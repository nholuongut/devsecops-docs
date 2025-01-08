# Phases

Each CI/CD run comprises of one or more phases. There are two types of phases – execution and deployment. In execution phase Katkit will invoke ci.sh file from the repository. The difference between two execution phases is in ENV variables based on which user code in ci.sh can operate differently. There can be only one deployment phase in each run. Katkit does not run ci.sh in deployment phase but it looks for the `servicdescription.js` file (details below), replaces the docker image tag \<hubtag> and replaces it with the git commit sha. It is assumed that the user, before invoking the deployment phase, has gone through a prior phase where they build a docker image which was tagged with the git commit sha. The sha is available as an ENV variable in every phase.

![](https://nholuongut.com/wp-content/uploads/2021/11/phases.png)
