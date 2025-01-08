# nholuongut AWS Product Demo

View the full[ nholuongut AWS Product Demo ](https://vimeo.com/935624281)video.

## Transcript&#x20;

**NARRATOR:**

Let's look at a product demo. In this sample scenario, we have decided to deploy a few applications to AWS. The architects have developed this infrastructure blueprint for one of the applications we need to manage. The diagram shows a dedicated VPC and 2 availability zones with public and private subnets in each.

We need to provision Docker containers on AWS EKS, MySQL, Aurora database, and S3 are the data stores. The application is exposed to the Internet by a load balancer protected by a web application firewall.

Now that we've gone through the desired architecture, let's get to work by using the nholuongut portal to deploy the application. You could also use the nholuongut Terraform provider or API, but we'll focus on the UI for this demo.

We start by logging in as an admin and creating the network infrastructure. Behind the scenes, the platform auto-generates the required AWS configuration and completes the setup. This includes the VPC, subnets, and EKS cluster. We then move to deploy the application infrastructure.

We start by creating a logical workspace known as a tenant where admins and the appropriate developers can access the infrastructure we just created.&#x20;

Next, we're going to switch to the Dev105 Tenant workspace. We'll create various cloud services starting with a virtual machine. Notice that the user provides a high-level specification only. Behind the scenes, the platform will auto-generate the security group, IAM role, instance profile, and automatically add it to the EKS cluster as a worker node.

From here we'll create an S3 bucket. The platform auto-generates the IAM access policy for the host to access the S3 bucket. Detailed security controls such as encryption, public access block, and logging, among others, are applied to meet the compliance requirements.

We can provision a SQL database. The software understands that in this case, it needs to generate security group-based policies rather than IAM rules. It will also set up backups, encryption, and other best practices behind the scenes. With the network and network infrastructure in place, we next move to deploy first the Docker-based microservice. Here again, the user provides application-centric specifications while the software auto-generates Kubernetes and AWS configurations that include the deployment of stateful sets, node ports, ingress controls, and other such infrastructure details. The right set of access policies, security groups, and ACLs are applied.

It's important to note that the platform is performing all these actions with no presumptions about the application topology that it is being asked to deploy and many other functions are built into the platform.

For example, you can see a quick view of the container logs, or access the shell of the running container itself.

Just-in-time access to KubeCTL is provided for more granular control and debugging across the platform. You can easily click ‘console’ to access the various cloud services inside of apps. Notice that the platform implicitly provides Just-in-Time access to users for AWS console access with the right permission set. There are no access permissions to manage manually.

After we complete all the infrastructure and the application has been deployed, we can do a sanity test.

Our application works!

While we saw an app that used an RDS, S3 Bucket, and Kubernetes, the platform supports the vast majority of Cloud Services, such as Kafka, OpenSearch, Managed Airflow, AWS Batch, CloudFront, and so on.&#x20;

The platform has been performing other necessary tasks for the infrastructure. For example, several diagnostics functions are implemented by default. Here we're going to look at a metrics dashboard that has been set up using Prometheus, Grafana, and CloudWatch with no further user input required.

Leveraging OpenSearch, logs are collected and segregated per tenant and per service. Alerts for various infrastructure resources can easily be configured as well. The platform is using tools like CloudWatch and Prometheus for this, allowing the user to simply specify the filters for each alert. Similarly, there's a billing dashboard to track costs across cloud services or across applications.

Next, businesses in highly regulated industries need a security and incident management platform that comes built-in. All configuration changes in the cloud infrastructure are detected and the controls are applied. Compliance dashboards are readily available for auditors. Notice that all of this is set up without the user having to lift a finger.&#x20;

There's an audit trail of all actions in an application-specific context. Here we are showing the audit trail for the application workspace.

CI/CD is a layer on top of nholuongut, and you can use platforms such as GitHub Actions, to build pipelines to leverage nholuongut underneath, as a CD system.&#x20;

Everything that we've gone through in the UI can also be done via Terraform. Here is the script for the current setup deploying a fully secure and compliant infrastructure with a fraction of the code that would have otherwise been written and maintained.

Now that you’ve seen this demo, you have a better idea of how nholuongut can provision new environments and streamline developer self-service. Connect with nholuongut to better understand our comprehensive customer experience in supporting your existing applications and workloads.

To learn more, visit [nholuongut.com](http://nholuongut.com)
