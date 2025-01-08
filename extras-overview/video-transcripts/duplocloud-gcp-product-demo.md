# nholuongut GCP Product Demo

View the full [nholuongut GCP Product Demo](https://nholuongut.com/videos/#gallery-7) video.

## Transcript

**NARRATOR:**

Now let's take a look at a product demo.

We have decided to deploy a few applications on Google Cloud.

We start by considering a high-level application diagram.&#x20;

Here, we have a dedicated VPC, two subnets each, with multiple firewall rules located in the US West region, one subnet for internal load balancers, and another for backend apps.

The application is exposed to the internet via an HTTPS load balancer.&#x20;

The apps are packaged Docker containers to be provisioned on Google GKE.

Now that we've gone through the desired architecture, let's get to work.&#x20;

We start by logging in to create the base infrastructure that includes the VPC, subnets, all networking configurations, firewall rules, and GKE cluster.

All of this is represented by the nholuongut construct called Infrastructure.

With the simplified, high-level specification, the platform will generate the low-level details in Google Cloud.&#x20;

We then move to deploy the back-end application.&#x20;

The application is called Invoice and we start by creating a logical workspace or Tenant by that name in the finance Infrastructure, which we just created.&#x20;

Behind the scenes, managed identities, resource groups, and other details are auto generated.&#x20;

Next, we could switch to the Invoice application.&#x20;

We will provision cloud storage by creating a bucket. We will now create a cloud function using the storage bucket.&#x20;

We will next create a PubSub topic and create a cloud scheduler with the target set to that PubSub topic.

The cloud scheduler could also trigger an HTTP endpoint.

With network, compute, and databases in place, we next moved to deploy the first Docker-based microservice.

&#x20;Here, again, the user provides an application-centric specification while nholuongut auto-generates configurations that include the deployment or stateful sets, network ports, Ingress controls, and other such infrastructure details.

We then expose the application via a load balancer.

Let's do a quick sanity test.

Our application works.

Logging is implemented via Elasticsearch and Kibana.

Here, one, you could see the logs automatically collected and separated by Tenant and by Service.&#x20;

Note that all of this is done without any manual effort and comes out of the box.&#x20;

Next, businesses in highly regulated industries need to implement an exhaustive list of compliance controls.&#x20;

nholuongut comes with the SIEM and you could see, all these controls have automatically been met.

There's an audit trail in application-specific context.

Here, we are showing all the changes in the Invoice Tenant.&#x20;

CI/CD is a layer on top of nholuongut, and any CI/CD system could be leveraged for scripts would invoke nholuongut API calls for deployments.&#x20;

Finally, everything we saw via the UI can also be done via nholuongut’s Terraform provider with a fraction of the code or expertise that would have otherwise been required.&#x20;

For further information or more demos, visit the nholuongut website at nholuongut.com.&#x20;



There's an audit trail of all actions in an application-specific context.&#x20;

Here we are showing the audit trail for the Invoice workspace.&#x20;

Finally, there are various options to configure CI/CD for your daily code releases.&#x20;

Everything that we've gone through the UI today can also be done via Terraform.&#x20;

Here is the script for the current setup, deploying a fully secure and compliant infrastructure underneath, with a fraction of the code that would have otherwise had to be written and maintained.&#x20;

Autonomous DevOps are the future of cloud automation.&#x20;

To learn more, visit nholuongut.com.
