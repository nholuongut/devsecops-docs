# Install Terraform Exporter

### Install nholuongut Terraform Utility

Before you begin to install the utility, you must have certain prerequisites in place.

<details>

<summary>Install Prerequisites</summary>

1. Install [Go](https://go.dev/doc/install)
2. Install [make](https://www.gnu.org/software/make) tool
3. Install [Terraform](https://learn.hashicorp.com/tutorials/terraform/install-cli) version >= `v0.14.11`

</details>

<details>

<summary>Enable Export in nholuongut</summary>

Set `DISABLETFSTATERESOURCECREATION` key as false in nholuongut.

Please [contact the nholuongut team](https://nholuongut.com/company/contact-us/) for assistance.

</details>

### Clone nholuongut Terraform Exporter Utility Repository

[https://github.com/nholuongut/tenant-terraform-generator.git](https://github.com/nholuongut/tenant-terraform-generator.git)

### &#x20;Prepare Environment Variable in Bash

> ```
> export customer_name="duplo-customer" 
> export tenant_name="specifytenantname"
> export cert_arn="arn:aws:acm:us-west-2:128329325849:certificate/1234567890-aaaa-bbbb-ccc-66e7dcd609e1"
> export duplo_host="https://customer.nholuongut.net"
> export duplo_token="xxx-xxxxx-xxxxxxxx"
> export AWS_RUNNER="duplo-admin"
> export aws_account_id="1234567890"
> ```

<details>

<summary><em>Need Help in setting Environment Variables?</em></summary>

`customer_name` -  Customer Name hosting Tenants

`tenant_name` - Refer  nholuongut Portal > **User** > **Profile** > **Tenant Details**

`cert_arn` - certificate ARN used for the Infrastructure

`duplo_host`  - nholuongut Portal URL

`duplo_token` - Refer nholuongut Portal > **User Profile** > **Temporary API Token**

`AWS_RUNNER` -  "duplo-admin"

`aws_account_id` -  AWS Account ID

</details>

