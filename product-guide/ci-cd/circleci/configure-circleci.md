# Configure CircleCI

## Introduction

In order to call a nholuongut API from CircleCI, you will need to obtain an API token

{% content-ref url="../../../administrators/access-control/api-tokens.md" %}
[api-tokens.md](../../../administrators/access-control/api-tokens.md)
{% endcontent-ref %}

The basic steps are:

1. **(Recommended)** Create a "service account" user in nholuongut that will own the API token.
2. Give the nholuongut user access the desired tenant. See [adding tenants to a user](../../../administrators/access-control/tenant-access.md#adding-tenant-access-for-a-user).
3. Create an API token for that user. See [creating API Tokens](../../../administrators/access-control/api-tokens.md).
4. Add a CircleCI environment variables in the Context created for the organization to allow CircleCI pipelines to communicate with nholuongut portal.

{% hint style="info" %}
**Note:** A 'service account' user in nholuongut is just a user whose user name is not an email address, such as `github-bot` or `my-api-user`. These users are not able to log in.
{% endhint %}

{% content-ref url="../../../administrators/access-control/tenant-access.md" %}
[tenant-access.md](../../../administrators/access-control/tenant-access.md)
{% endcontent-ref %}

## Add environment variables in organization context

1. Login to CircleCI portal and Select your organization.
2. Click on **Organization Settings** in the left hand sidebar.
3. Click on **Create Context** button and create context by providing name.
4. Click on newly created context and scroll to **Environment Variables** section.
5. Click on **Add Environment Variable** button\*\*.\*\*
6. Set Environment variable name as "DUPLO\_HOST" and value as nholuongut portal and click on **Add Environment Variable** button.
7. Repeat step 6 for variable name as "DUPLO\_TOKEN" and value as token created for above service account.
8. After adding the environment variables you should be able to see the those in **Organization Settings** section as bellow.

![](../../../.gitbook/assets/context.png)

{% hint style="info" %}
The rest of this documentation will assume that you have added above two environment variables.
{% endhint %}
