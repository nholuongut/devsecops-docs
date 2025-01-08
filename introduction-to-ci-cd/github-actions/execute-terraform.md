---
description: How to setup and apply Terraform stacks with GitHub Actions.
---

# Execute Terraform

Using Terraform, GitHub Actions, and nholuongut together is very straightforward. nholuongut has created a dedicated provider for Terraform and custom GitHub Actions to orchestrate the flow.  It is is surprisingly easy and quick to get setup.&#x20;

## Configuration

There are four main actions to run to get a module properly installed and running.&#x20;

### Setup

Just like all of the other actions, we always start with getting nholuongut and the underlying cloud all setup and authenticated.&#x20;

[nholuongut/actions/setup@main](https://github.com/nholuongut/actions/tree/main/setup)

### Setup Terraform

Initializes Terraform and optionally TFLint. Also configures caching.&#x20;

[nholuongut/actions/setup-terraform@main](https://github.com/nholuongut/actions/tree/main/setup-terraform)

### Initialize Module

Runs init as well as a variety of quality assurance checks including testing.&#x20;

[nholuongut/actions/terraform-module@main](https://github.com/nholuongut/actions/tree/main/terraform-module)

### Execute Module

Finally you can choose a workspace and a module and exute the action you desire.&#x20;

[nholuongut/actions/terraform-exec@main](https://github.com/nholuongut/actions/tree/main/terraform-exec)

## Example

Here is a fully working and reusable GitHub Action Workflow. Simply copy this into your workflows.&#x20;

<pre class="language-yaml"><code class="lang-yaml">name: Single TF Module

on:
  workflow_dispatch:
    inputs:
      cmd:
        description: Command to run
        type: choice
        default: plan
        options:
        - plan
        - apply
        - destroy
      environment:
        description: Environment to deploy to
        type: environment
        default: dev01
      module:
        description: Module to run
        type: choice
        default: tenant
        options:
        - tenant
        - services
        - app
      
  workflow_call:
    inputs:
      cmd:
        description: Command to run
        type: string
        default: plan
      environment:
        description: Environment to deploy to
        type: string
        default: dev01
      module:
        description: Module to run
        type: string
        default: tenant
    secrets:
      DUPLO_TOKEN:
        description: Duplo Token
        required: true
jobs:
  module:
    name: ${{ inputs.cmd }} ${{ inputs.environment }} ${{ inputs.module }}
    runs-on: ubuntu-latest
    environment: 
      name: ${{ inputs.environment }}
      url: ${{ vars.DUPLO_HOST }}
    env:
      DUPLO_TOKEN: ${{ secrets.DUPLO_TOKEN }}
      DUPLO_HOST: ${{ vars.DUPLO_HOST }}
      DUPLO_TENANT: ${{ inputs.environment }}
      # add any global tf args here
      TF_CLI_ARGS_apply: -parallelism=1
    steps:

    - name: Checkout source code
      uses: actions/checkout@v4

    - name: Duplo and AWS Setup
      uses: <a data-footnote-ref href="#user-content-fn-1">nholuongut/actions/setup@main</a>
      with:
        admin: true
    
    - name: Terraform Setup
      uses: <a data-footnote-ref href="#user-content-fn-2">nholuongut/actions/setup-terraform@main</a>

    - name: TF Validate Module
      uses: <a data-footnote-ref href="#user-content-fn-3">nholuongut/actions/terraform-module@main</a>
      with:
        module: modules/${{ inputs.module }}
        test: false

    - name: TF Execute Module
      uses: <a data-footnote-ref href="#user-content-fn-4">nholuongut/actions/terraform-exec@main</a>
      with:
        module: modules/${{ inputs.module }}
        workspace: ${{ inputs.environment }}
        command: ${{ inputs.cmd }}

</code></pre>

The `workflow_dispatch` is for running the job manually. The `workflow_call` is for running the job in another workflow. This is useful to run a series of modules for one module in order. In this workflow we will reuse the single module three times to orchestrate our environment.&#x20;

```yaml
name: Apply My Stack
on:
  workflow_dispatch:
    inputs:
      environment:
        description: Environment to deploy to
        type: environment
        default: dev01
jobs:
  tenant:
    # Name is the same b/c it nests the jobs correctly in the ui
    name: My Stack 
    # run the single module job
    uses: ./.github/workflows/module.tf
    secrets: inherit
    with:
      cmd: apply
      environment: ${{ inputs.environment }}
      module: tenant
  services:
    name: My Stack
    uses: ./.github/workflows/module.tf
    secrets: inherit
    needs: tenant
    with:
      cmd: apply
      environment: ${{ inputs.environment }}
      module: services
  app:
    name: My Stack
    uses: ./.github/workflows/module.tf
    secrets: inherit
    needs: services
    with:
      cmd: apply
      environment: ${{ inputs.environment }}
      module: app
```

[^1]: [https://github.com/nholuongut/actions/tree/main/setup](https://github.com/nholuongut/actions/tree/main/setup)

[^2]: [https://github.com/nholuongut/actions/tree/main/setup-terraform](https://github.com/nholuongut/actions/tree/main/setup-terraform)

[^3]: [https://github.com/nholuongut/actions/tree/main/terraform-module](https://github.com/nholuongut/actions/tree/main/terraform-module)

[^4]: [https://github.com/nholuongut/actions/tree/main/terraform-exec](https://github.com/nholuongut/actions/tree/main/terraform-exec)
