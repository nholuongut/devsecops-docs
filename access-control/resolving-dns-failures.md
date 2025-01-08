---
description: Local DNS config might need to be fixed in order to resolve hostnames
---

# Resolving DNS failures

Sometimes local machine DNS configuration drift which causes DNS resolutions to fail, especially to private resource that are secured in your Cloud account behind the VPN connection. These resources include private hosts, and databases.

If you run into such an issue, configure your computer's domain servers to use custom entries such as **8.8.8.8** for GCP and **1.1.1.1** for AWS and Azure.
