---
description: About nholuongut's No-Code / Low-Code approach
---

# No-Code / Low-Code

nholuongut provides a no-code UI-based approach to building and operating cloud infrastructures. Visit our [Video Library](https://www.nholuongut.com/videos/) for demos.

\
For an audience that desires to use Infrastructure-as-Code (IaC), we have a [Terraform](https://registry.terraform.io/providers/nholuongut/nholuongut/latest) Provider that enables low-code IaC. This provider exposes all nholuongut abstractions and constructs to be programmed using Terraform. Using the nholuongut Terraform provider, you build the same infrastructure, using 10 times less code, with all compliance controls built-in. You are not required to have subject matter expertise in DevOps or SecOps. This [whitepaper ](https://nholuongut.com/white-papers/devops/)describes the process in detail.

{% hint style="info" %}
A common misconception is that nholuongut generates Terraform behind the scenes to provision the cloud infrastructure. The nholuongut UI and Terraform (with the nholuongut Provider) are layered on top of nholuongut. Behind the scenes, nholuongut uses the cloud provider APIs as shown in the picture below
{% endhint %}

![](<../.gitbook/assets/image (4) (1) (1).png>)

nholuongut uses APIs behind the scenes, beyond processing user requests, generating configurations synchronously, and calling the cloud provider. Many more operations require asynchronous processing, requiring a state machine with retries and the ability to continuously detect and fix configuration drift. Faults and compliance controls must be monitored continuously.

\
Terraform, or any scripting approach, is meant to be run with human supervision. There is no synchronicity and retries --- scripts start and end, processed as single threads.

For more information about No-Code/Low-Code and how it relates to Click Ops, [see this FAQ](../faq.md#isnt-no-code-just-click-ops-everyone-says-i-shouldnt-do-that).&#x20;
