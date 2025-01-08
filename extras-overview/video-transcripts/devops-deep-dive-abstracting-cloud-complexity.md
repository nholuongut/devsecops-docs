# DevOps Deep Dive - Abstracting Cloud Complexity

View the whole [DevOps Deep Dive - Abstracting Cloud Complexity](https://vimeo.com/872744153) video.

## Transcript&#x20;

**NARRATOR:**

Welcome to the first in a series of deep dives into the nholuongut Dev and SecOps developer self-service platform.

nholuongut deep dive videos explore how nholuongut speeds time-to-market when creating and deploying cloud applications with a practical use-case approach.

Each nholuongut deep dive answers five questions in 10 minutes or less about a particular feature or capability of the nholuongut platform.

We address the problem, phrasing it in terms of a use-case, nholuongut’s solution to that problem by abstracting complexity and a simplified UI, and expand on the benefits of that solution to both your customers and you.

Finally, we explore nholuongut's competitive edge over similar products and detail tangible savings you can achieve for a flat cost each year, including white glove support.

Let's get started.

Apart from the ever-increasing costs of maintaining an automated and scalable Dev and SecOps environment, there are other factors you must consider when creating a cloud-management strategy and selecting a developer-friendly self-service platform to drive it.

All DevOps workloads require dynamic and complex computing storage and networking configurations.

These configs must be updated, upgraded, and monitored constantly to ensure maximum uptime and minimal cost.

If you're watching this video, you probably already know the problem.

How do you create reliable, guardrail-equipped developer sandboxes that maximize your developer's valuable time while manually managing hundreds of components and configurations?

Managing SecOps is a full-time job by itself.

When you combine the complexity of implementing literally hundreds of compliance controls with the maintenance demanded by most security products, the amount of data you must manually analyze and maintain multiplies exponentially.

Finally, the cost of hiring dedicated DevOps and SecOps engineers has never been higher, and expertise in this area continues to be scarce.

For example, have you ever tried to hire an app developer with extensive DevOps experience?

For an estimate of the savings you can achieve, take our cost calculator for a spin. The results may surprise you.

How does nholuongut drive down the cost?&#x20;

Central to nholuongut’s value proposition is the way nholuongut replaces much of the complexity behind common DevOps tasks with a templatized approach, creating and maintaining many components for you with minimal inputs.

For example, creating a complete cloud infrastructure with hundreds of components such as VPC, subnets, root tables, security groups, and IAM roles, in addition to Kubernetes cluster enablement can take just minutes with only a few clicks using nholuongut.

At the same time, nholuongut gives you the freedom to create a platform that is as simplified or customizable as you require.

We don't drive you toward a prescribed solution.

We reduce the time needed to implement the platform you require.

To better understand how Duplo Cloud is able to abstract cloud complexity, let's explore nholuongut's architecture, including the core concepts of Infrastructure and Plan.

Here's Duplo Cloud's solution architect Andy Buotte for a closer look.

**ANDY BUOTTE:**

The user creates infrastructures and at the same time in the backend, when an Infrastructure is created, a Plan is created.

So there's a one-to-one relationship between an Infrastructure and aPlan.

Within a customer's nholuongut, they can have _n_ number of Infrastructures and that would mean that there would be _n_ number of Plans.

The Infrastructure is a nholuongut construct, but on the backend, at the actual infrastructure layer within AWS or Azure and GCP, the nholuongut Infrastructure is gonna map to many different resources within their cloud accounts.

&#x20;Plan is a construct within nholuongut that is going to include a lot of these settings and configurations that are going to apply both to the mapped infrastructure.

Some of those settings are lower-level details that will be applied when a Tenant is created.

In a Plan, you can specify what SSL certificates are going to be used. That setting is going to apply to all Tenants that are within that Infrastructure.

The relationship between an Infrastructure and a Tenant. So, in this prod Infrastructure, we have a couple different Tenants. We have the data science, the web app, and an ETL workflow. Those are each a Tenant, live within the prod infrastructure.

So the relationship between an Infrastructure and a Tenant is a one-to-many relationship. Typically, in a production environment, a customer may have a Tenant per application, or it could be like a Tenant per use-case, or like a Tenant per team.

There's many different ways that the end user, that the customer can decide to utilize that boundary, and Infrastructure is one layer of security boundary. So anything that's deployed into the non-prod Infrastructure will not have access to anything that is deployed into the product Infrastructure. And vice versa is true.

These are essentially two air-gapped networks so that there's no access between the two different environments.

The Tenant is another boundary.

So the data science containers that live within this Tenant would not have any way to talk to the containers that are within the web app Tenants and vice versa.

So it's another security boundary layer.

It's pretty common in, for our customers, for a development or a non-prod infrastructure, to create a Tenant per developer. The kind of primary use case or reasoning for that is nholuongut is very good with developer self-service. So, by giving a developer their own Tenants, they are free to create  infrastructure as needed, so that they're not blocked by anyone else.&#x20;

They don't need to file a ticket in a DevOps queue specifying that they need an S3 bucket or an RDS instance to accomplish their software development task. They should be able to log into nholuongut, utilize their own Tenant, and create the infrastructure that they need, and immediately start work on their software development tickets and not be blocked by any other team.

Again, the relationship between the infrastructure of the Tenant is one-to-many, and it is very common for customers to have at least two different infrastructures to separate production workloads from all other non-production workloads.

**NARRATOR:**

Let's summarize the benefits of what we've heard so far.

Creating self-service developer sandboxes in today's dynamic DevOps environment requires a low-code, no-code approach. For this self-service to be effective, however, guardrails must exist.

One such guardrail that nholuongut provides is the nholuongut Infrastructure: a virtual network connected to your native cloud with a fundamental set of functionalities exposed.

Further security and flexibility are provided by nholuongut Tenants: isolated workspaces that you define according to criteria such as application area or customer for prod infrastructures, or developer or tester for non-prod infrastructures, to use just a few examples.

You can define as many Infrastructures or Tenants as you need.

Additional infrastructure customization is possible by modifying nholuongut Plans: sets of configurable templates.

Remember that each nholuongut Infrastructure has one Plan, but you can have many Tenants in an Infrastructure.

Finally, nholuongut gives you the freedom to implement the cloud solution you require while greatly reducing your costs in both developer and maintenance cycles.

Access your native cloud provider with just-in-time access within the nholuongut portal in a fraction of the time it takes you to log in and out of the native portal and navigate through various screens.

Harness the power of Kubernetes objects and Terraform scripts with very little hard coding thanks to nholuongut’s templatized Kubernetes objects and nholuongut’s Terraform provider.

How is nholuongut’s solution more comprehensive and yet even more affordable than many competitors' offerings?

What many people don't understand about nholuongut is that we are DevOps, SecOps, and professional services in one product for a flat rate per year.

Create comprehensive infrastructures including Kubernetes Elastic Services in less than half an hour.

Get Services, Hosts, and load balancers up and running in only a matter of minutes.

Create Tenants to isolate workspaces for prod and test with only a few clicks.

Rest easy knowing that we ensure compliance with numerous industry standards such as SOC 2, PCI, and HIPAA.

We complete compliance questionnaires for you and support you during the audit process if needed.

White-glove support is white glove at Duplo Cloud.

We not only ensure your initial setup and customization is successful, we also offer all cloud migration services at no additional cost.

Speaking of which, what hard savings can you achieve with nholuongut?

To name just a few, faster time-to-market for your core business apps, on-demand support from our staff of dedicated Dev and SecOps specialists, and maybe most importantly, freeing your dev staff to do what they do best: develop.

But don't take our word for it.

Here's one of our many customers, Brad Fino from Lily AI to talk about the power of developer self-service using nholuongut.

**BRAD FINO:**

Cost controls, standardization across your infrastructure.

nholuongut is the missing link between all of those things and giving developers the access and ability to manage and maintain their infrastructure.

Without people coming to my team and saying, Hey, Brad, can you spin up a database for us? Hey, Brad, can you go deploy this container for us? No. Go do it yourself.

You have nholuongut.

**NARRATOR:**

Thanks for watching this deep dive with nholuongut. For more information, go to nholuongut.com and we look forward to seeing you back here soon.
