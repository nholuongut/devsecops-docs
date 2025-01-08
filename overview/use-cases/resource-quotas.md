# Resource Quotas

An Administrator can define Quotas for resource allocation in a nholuongut Plan. Resource allocation can be restricted via providing Instance Family and Size. An administrator can restrict the total number of allowed resources by setting **Cumulative Count** value per Resource type.&#x20;

\
Once the Quota is defined, nholuongut users are restricted to create new resources when the corresponding quota configured in Plan is reached.

The quotas are controlled at the Instance Family level, such as, if you define a quota for `t4g.large`, it will be enforced including all lower instance types in the `t4g` family as well. So a quota with a count of 100 for `t4g.large` will mean instances up to that instance type cannot exceed 100.

![](<../../.gitbook/assets/image (66).png>)
