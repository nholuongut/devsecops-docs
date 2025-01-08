---
description: Use SCPs with nholuongut to add guardrails to AWS organizational units
---

# Setting up SCPs (Service Control Policies) for nholuongut

If you use AWS organizations, you likely use SCPs as guardrails to restrict specific user actions for each organization. You typically set up policy statements in an SCP to add security to restrict specific user actions.

Create a separate organizational unit for your nholuongut accounts and use the Full Access SCP with no restrictions as a base JSON template, as shown below, and then add policy statements such as the ones described in the [AWS Documentation for general SCP examples](https://docs.aws.amazon.com/organizations/latest/userguide/orgs\_manage\_policies\_scps\_examples\_general.html#example-scp-deny-region) and those linked in the following list:

* [Prevent Root access](https://docs.aws.amazon.com/organizations/latest/userguide/orgs\_manage\_policies\_scps\_examples\_general.html#example-scp-root-user)
* [Prevent users from disabling an AWS configuration or changing configuration rules](https://docs.aws.amazon.com/organizations/latest/userguide/orgs\_manage\_policies\_scps\_examples\_config.html#example\_config\_1)
* [Prevent users from disabling CloudWatch or changing its configuration](https://docs.aws.amazon.com/organizations/latest/userguide/orgs\_manage\_policies\_scps\_examples\_cloudwatch.html#example\_cloudwatch\_1)&#x20;

```json
{
    "Version": "2012-10-17",
    "Statement": {
        "Effect": "Allow",
        "Action": [
          "*:*"
        ],
        "Resource": "*"
    }
}
```
