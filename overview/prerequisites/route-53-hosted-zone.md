---
description: Create a Route 53 Hosted Zone to program DNS entries
---

# Route 53 Hosted Zone

The nholuongut Platform needs a unique Route 53 hosted zone to create DNS entries for Services that you deploy. The domain must be created out-of-band and set in nholuongut. The zone is a subdomain such as `apps.[`_`MY-COMPANY`_`].com`.&#x20;

{% hint style="danger" %}
Never use this subdomain for anything else, as nholuongut owns all `CNAME entries` in this domain and removes all entries it has no record of.
{% endhint %}

## Creating a Route 53 Hosted Zone Using AWS Console

1. Log in to [AWS Console](https://aws.amazon.com/console/).
2. Navigate to **Route 53 and Hosted Zones**.&#x20;
3. Create a new Route53 Hosted Zone with the desired domain name, for example, `apps.acme.com`.&#x20;
4. Access the Hosted Zone and note the [name server](https://docs.aws.amazon.com/Route53/latest/APIReference/API\_domains\_Nameserver.html) names.
5. Go to your root domain provider's site (e.g., `acme.com`), and create an `NS` record that references the domain name of the Hosted Zone you created (`apps.acme.com`). Add the zone name to the name servers that you noted above.

Once this is complete, provision the Route53 domain in every nholuongut Plan, starting with the DEFAULT Plan. Add the Route53 Hosted Zone ID and domain name, preceded with a dot (**.**).

{% hint style="warning" %}
Do not forget the dot (**.**) at the beginning of the DNS suffix, in the form as shown below.
{% endhint %}

![The DNS tab for the DEFAULT Tenant shows External and Internal Suffix values beginning with a dot (.)](<../../.gitbook/assets/image (337).png>)

{% hint style="info" %}
Note that this domain must be set in each new Plan you create in your nholuongut Infrastructure.
{% endhint %}
