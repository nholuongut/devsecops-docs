---
description: In Transit encryption support in nholuongut
---

# In Transit encryption

Except in AWS, users generate SSL certificates out-of-band either from the cloud provider ACM or issue and upload them to the cloud provider ACM. A reference to these certificates can be added using the **Administrator** -> **Plan** -> **Certificates** menu. During the creation of cloud resources like load balancers, Ingress, Cloudfront, and API gateway, one of these certificates can be selected and the platform applies them to the resources.

In AWS, nholuongut automatically generates a wildcard certificate in ACM for each DNS domain that the platform manages and adds it to the nholuongut Plan. Users can add more certificates at any time.

