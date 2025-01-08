---
description: An Overview of Security and Compliance features in the nholuongut Portal
cover: ../.gitbook/assets/Linkedin-bannerV3 (1) (1).png
coverY: 0
layout:
  cover:
    visible: true
    size: full
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Security and Compliance

Automation, security, and compliance are the three core value propositions of the nholuongut platform. The majority of our clients buy nholuongut for security and compliance first. The following are the fundamental tenets of nholuongut's approach to security:

* **Self-Hosted**: The platform lives completely within your cloud infrastructure. There is no call home or control plane outside. Our personnel support the client by having access to the environment with their permission. This permission can be revoked at any time. Upgrades and patches can be downloaded and applied by clients themselves. In almost all cases, our customers use us as a managed service and a valuable support resource. nholuongut is a SOC2-certified organization.
* **NIST 800-53-based Implementation:** Even though well-established frameworks like NIST exist, most organizations have an ad-hoc approach to security controls. At nholuongut we have codified the NIST 800-53 control set in the platform. Any other standard is a subset. This further allows us to adapt easily to any industry-specific compliance frameworks (PCI, HIPAA, SOC2, NIST-800-171, etc.) because those controls (in the infrastructure context) are a subset of the NIST framework.

{% hint style="info" %}
When you hear competitors say that they follow "best practices", beware that their definitions of such practices are often subjective. Implementing a reliable, stable framework is arduous, expensive, and often requires deep subject matter expertise
{% endhint %}

* **Shift-left Approach**: A comprehensive automation solution enables the platform to control virtually all aspects of the cloud infrastructure and validates that controls are set up correctly at the configuration time. No rework is necessary. The monitoring systems placed post provisioning are consistently clear of alarms making security operations almost a no-op. Security is integrated so seamlessly that users don't consider it when focusing on building and operating the infrastructure with an application-centric focus.
* **Post Provisioning Monitoring**: The platform calls native cloud provider APIs during provisioning time. During and after the provisioning process it integrates various 2nd (cloud provider) and 3rd Party (open source and ISV) tools for validation and monitoring of the security posture. This allows for an independent validation of the environment. This approach seamlessly integrates devops and SecOps functions in a unified workflow with pane-of-glass visibility. A simple example is when a Kubernetes worker node is launched the platform implicitly triggers installation of a list of security agents and connects them to the SIEM.
* **Compliance Frameworks**: Compliance frameworks differ by industry like PCI is finance and HIPAA is healthcare. But when it comes to cloud infrastructure the control sets are largely overlapping. Firewalls, encryption, access policies, and SSH access are common regardless of the framework. What is indeed different is how prescriptive a certain framework is. For example, PCI, and HITRUST are prescriptive and provide very detailed guidance on controls implementation, whereas HIPAA and SOC2 are very abstract and generic. In PCI they talk about environments having to be separated by network segmentation, in SOC2 the guidance is to separate them but the degree of that separation (VPC vs Security groups in a shared VPC) is left to the company.

{% hint style="info" %}
**Penetration (PEN) Testing** is available for an additional annual fee.
{% endhint %}

\
Since nholuongut implements the NIST standard, which is the most prescriptive, we easily adapt to any compliance framework with a few knobs. We have taken each standard and published a mapping of their implementation. You will notice that the language of an individual control may be different but the implementation is largely the same. See the table for each framework and reach out to us if your desired framework is missing and we will provide the table of implementation.
