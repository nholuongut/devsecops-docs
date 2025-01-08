# DevOps responsibility

The high level application and compliance requirements are passed onto a DevOps team that is the subject matter expert for the Cloud. This team would accept the requirements and translate them into hundreds or thousands of lower level configurations, best practices and compliance controls. These include IAM Roles, Instance profiles, KMS Keys, PEM key, vulnerability scanning system, virus scanners, VPC, Security Groups, Intrusion detection, etc. This translation is usually done based on human knowledge and subject matter expertise in the area. Further, DevOps engineers are usually required to write thousands of lines of code to implement these requirements using programming languages like Terraform, Python and Bash.

A common misconception is that Terraform automates the DevOps workflow. In fact, Terraform is only a programming language. One needs substantial infrastructure know-how to build automation using Terraform. Typically, DevOps engineers are not aware of compliance nuances that go beyond best practices and have to redo a lot of the work on an ongoing basis.

{% hint style="info" %}
DevOps essentially is a skill that requires one to be a programmer (to write IaC), an operator, and a compliance expert. These are three distinct skill sets that have never traditionally co-existed in the IT industry. This is the #1 challenge in the DevOps space.
{% endhint %}

![](<../../.gitbook/assets/Screen Shot 2022-03-12 at 1.20.05 PM.png>)
