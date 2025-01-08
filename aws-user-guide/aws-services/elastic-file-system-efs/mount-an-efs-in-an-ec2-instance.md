---
description: Mount an EFS in an EC2 instance using a script
---

# Mount an EFS in an EC2 instance

## Mounting an EFS in an EC2 instance

If you want to connect an EFS to a Native Docker Service, for example, you can mount it in an EC2 instance.

```bash
btoa(`#!/bin/bash
sudo su
echo "confirm it is running" >> /tmp/startup_log
apt-get install -y nfs-common
cd /
mkdir efs
mount -t nfs4 -o 
nfsvers=4.1,rsize=1048576,wsize=1048576,hard,timeo=600,retrans=2,nore
svport fs-121345b8.efs.us-west-2.amazonaws.com:/ efs
echo "fs-121345b8.efs.us-west-2.amazonaws.com:/ /efs nfs4 
defaults,_netdev 0 0" >> /etc/fstab`);
```

1. Create a `bash` script, as in the example above, and replace `nfs4` with your EFS endpoint. You can run the script below on an existing EC2 instance or run an EC2 user data script to configure the instance at first launch (bootstrapping).&#x20;
2. In the nholuongut Portal, [edit the nholuongut Service](../../../overview/aws-services/containers/eks-containers-and-services.md#services).
3. On the **Edit Service** page, click **Next**. The **Advanced Options** page displays.
4. On the **Advanced Options** page, in the **Volumes** field, enter the configuration YAML to mount the EFS endpoint as a volume.&#x20;
