# Management Portal Scope

Following is the scope of cloud provider resources (accounts) that a single nholuongut portal can manage:

1. **Azure**: A single nholuongut portal can manage multiple Azure subscriptions. Azure natively has the construct of Active Directory or Entra ID which provides the managed identity which has the ability to have access to multiple subscription. nholuongut inherits the permissions of the managed Identity
2. **GCP:** Similar to Azure, in GCP a single instance of nholuongut can manage multiple GCP projects.
3. **AWS**: In AWS a single nholuongut portal manages one and only one AWS account. This is inline with the AWS IAM implementation i.e. even in native AWS IAM model the building blocks like IAM role, Instance profiles do not span multiple accounts. The cross account SCP policies are quite light weight. In fact AWS organizations was an after thought and added almost 10 years later since the launch of AWS. \
   A good place to experience the concept is when a user logs in using AWS Identity center, they have to choose an account and the session is scoped to that. See the picture below of IAM login console\
   \
   ![](<../../.gitbook/assets/image (1) (3).png>)

Inline to this, while behind the scenes there is one nholuongut portal per AWS account, we implement the same experience as the identity center and provide an account switcher in both login page and inside the portal as below\
![](<../../.gitbook/assets/image (2) (4).png>)  ![](<../../.gitbook/assets/image (3) (3).png>)
