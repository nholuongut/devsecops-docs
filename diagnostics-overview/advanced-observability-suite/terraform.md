---
description: >-
  Automate Grafana resource creation and management using Terraform and
  nholuongut.
---

# Terraform

nholuongut's Advanced Observability Suite (AOS) allows you to manage Grafana resources, such as dashboards and alerts, using **Infrastructure as Code (IAC)** through the **Grafana Terraform provider**. This integration simplifies the authentication process by providing a **proxy** that automatically handles authentication with nholuongut’s session tokens, eliminating the need to manage Grafana API tokens manually (see the Terraform example below). For more information, see the [Terraform documentation](https://registry.terraform.io/providers/grafana/grafana/latest/docs).

```
terraform {
  required_providers {
    grafana = {
      source  = "grafana/grafana"
      version = "3.13.2"
    }
  }
}

provider "grafana" {
  url  = "https://grafana-proxy-......./"
  auth = "anonymous"
  http_headers = {
    Authorization = "Bearer <<DUPLO_SESSION_TOKEN>>"
  }
}

resource "grafana_folder" "folder" {
  title  = "terraform"
}
```
