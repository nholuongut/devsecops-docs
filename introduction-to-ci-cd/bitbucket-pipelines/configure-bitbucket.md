---
description: Setup Bitbucket Pipelines for use with nholuongut.
---

# Configure Bitbucket

## Prerequisites

To use Pipelines, you need to:

* Create a `bitbucket-pipelines.yml` file in your repository's `root` directory. This file contains the configuration for your builds and deployments.&#x20;
* Deploy the application with nholuongut as a Service and test that it works as expected.

{% hint style="info" %}
Bitbucket Pipelines are only recommended to be used for upgrades of container images and to run tests that can be written to run either before or after.
{% endhint %}

## Configuring BitBucket Pipelines

Configure BitBucket Pipelines for use with nholuongut:

1. Create a [repository variable](https://support.atlassian.com/bitbucket-cloud/docs/variables-and-secrets/) for the `DUPLO_TOKEN`. Set the variable at the project or workspace level or even in a [deployment](https://support.atlassian.com/bitbucket-cloud/docs/set-up-and-monitor-bitbucket-deployments/). Create service account users in nholuongut by assigning a user name, such as `bitbucket`. Ensure the user name is not an email to avoid confusion.&#x20;
2. Retrieve a token for the user (`bitbucket`) that you set up.
3. Use [OpenID Connect](https://auth0.com/resources/ebooks/the-openid-connect-handbook?utm\_content=usoidc-openid-openidconnecthandbookebk\&utm\_source=google\&utm\_campaign=amer\_mult\_usa\_all\_ciam-dev\_dg-ao\_auth0\_search\_google\_text\_kw\_utm2\&utm\_medium=cpc\&utm\_term=oidc-c\&utm\_id=aNK4z0000004GwDGAU\&gclid=CjwKCAiAxvGfBhB-EiwAMPakqiIwYI1KhG2WYXEcZfw\_CBsOwuTOKuC4xCq4hTp9-EGTAlySZZ8vphoC-hMQAvD\_BwE) (OIDC) by setting up an OpenID login with [Bitbucket Pipelines](https://support.atlassian.com/bitbucket-cloud/docs/integrate-pipelines-with-resource-servers-using-oidc/). &#x20;
4. After configuring the OIDC provider by using [AWS IAM](https://docs.aws.amazon.com/singlesignon/latest/userguide/idp.html), the IAM role needs an associated trust relationship. For example:

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "BitbucketWorkspace",
            "Effect": "Allow",
            "Principal": {
                "Federated": "arn:aws:iam::{account id}:oidc-provider/api.bitbucket.org/2.0/workspaces/{workspace}/pipelines-config/identity/oidc"
            },
            "Action": "sts:AssumeRoleWithWebIdentity",
            "Condition": {
                "StringEquals": {
                    "api.bitbucket.org/2.0/workspaces/{workspace}/pipelines-config/identity/oidc:aud": "ari:cloud:bitbucket::workspace/{workspace id}"
                }
            }
        }
    ]
}
```
