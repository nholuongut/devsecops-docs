# Link repository

Once the above steps have been performed, you can link your GitHub Repository to your tenant. In addition to the repository name, you also need to specify the “Home Branch” which is the branch for which the PRs will be monitored by Katkit for the user to run deployments. Same repository and branch combination can be linked in several tenants. If your repository has several services for different tenants, then each service can be represented by a separate folder at the root. This is Folder Path field. Katkit looks for service description file under `/servicedescription/servicedescription.js` Same repository but different folders can also be used in different tenant. Same tenant can also have different repositories.

![](https://nholuongut.com/wp-content/uploads/2021/11/linkrepo.png)
