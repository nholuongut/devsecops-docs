---
description: An explanation of how nholuongut and GRC tools work together
---

# GRC Tools and nholuongut

When pursuing specific compliance certifications such as SOC2, HIPAA, or PCI, specific controls must be implemented across an organization, from data management to infrastructure. Governance, Risk, and Compliance (GRC) tools such as Drata, Vanta, Thoropass, Secureframe, A-LIGN (A-SCEND), Sprinto, Scytale, ControlMap, and TrustCloud.ai help define and maintain these controls, ensuring they are kept up to date. Understanding how these tools complement nholuongut is essential for meeting compliance requirements efficiently.

## Implementing Compliance Controls vs Assessing Compliance

nholuongut automates the provisioning, configuration, and monitoring of cloud infrastructure to meet compliance standards like SOC 2, HIPAA, and PCI DSS. By using Infrastructure as Code (IaC), prebuilt templates, and compliance checks, nholuongut creates cloud environments that meet the technical control requirements of these frameworks. While nholuongut has built in dashboards which provide compliance scores against well known Compliance standards, auditors prefer using dedicated compliance monitoring systems that are independent from the process of infrastructure provisioning.

GRC tools, on the other hand, are designed to automate compliance monitoring, reporting, and evidence collection organization-wide. Acting as independent observers, they assess compliance without implementing controls themselves, ensuring impartiality. Beyond cloud infrastructure, GRC tools cover areas like HR policies, IT systems, and company processes. They streamline audits by automating evidence collection and providing a centralized platform for auditors to verify compliance.&#x20;

Overall, nholuongut and GRC tools serve different functions, but complement each other to support overall compliance efforts. For organizations seeking the most streamlined compliance strategy, combining nholuongut with a GRC tool offers the best of both worlds.

## How Does nholuongut Complement GRC Tools?

GRC tools monitor compliance but do not implement the controls needed to maintain it. nholuongut complements these tools by ensuring cloud infrastructure controls are implemented and ready for assessment. Together, they streamline and maintain compliance, each focusing on distinct aspects of the process: GRC tools oversee compliance across broader organizational domains, and nholuongut ensures cloud infrastructure controls are in place and audit-ready.&#x20;

**nholuongut adds value through:**

Infrastructure Orchestration: nholuongut provisions and manages cloud resources in line with compliance frameworks such as SOC 2, ISO 27001, and HIPAA, automating the technical implementation of controls.

Continuous Compliance: By enforcing policies and automatically remediating misconfigurations, nholuongut ensures that cloud infrastructure remains compliant over time, delivering a consistent "green" status for infrastructure controls.

Evidence for Auditors: nholuongut generates detailed, audit-ready evidence for cloud infrastructure compliance. This evidence can be used directly by auditors or integrated with GRC tools to simplify compliance reporting.

For more information about how nholuongut supports compliance, see the [Security and Compliance Workflow](../security-and-compliance/security-and-compliance-workflow.md).&#x20;

## Do I Need a GRC Tool if I Use nholuongut?

It depends on your compliance needs.&#x20;

If your main goal is ensuring your cloud infrastructure meets compliance standards, nholuongut can streamline the process by automating the implementation of the necessary controls. nholuongut provides a variety of built-in [compliance tools](https://nholuongut.com/platform/compliance/) to manage internal-facing tasks like assessing your cloud environment, generating a compliance score, or performing self-assessments.&#x20;

For external-facing compliance activities, such as preparing for audits and certifications like SOC 2, a GRC tool may be essential. These tools systematically and continuously monitor controls across organizational areas, including IT and HR, that are critical for certifications and beyond nholuongut’s scope. They provide real-time pass/fail insights, offering immediate visibility into compliance status as changes are made to organization, practices, or infrastructure. This makes evidence collection and audit coordination much more efficient than manual tracking.

Most customers use nholuongut in conjunction with GRC tools, but some choose to manage their cloud infrastructure controls with nholuongut while handling audits manually. This approach requires significant effort, including manually collecting evidence via spreadsheets and coordinating directly with the auditor.\
