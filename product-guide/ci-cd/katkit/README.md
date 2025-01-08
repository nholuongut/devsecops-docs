# Katkit CI/CD

nholuongut provides a CI/CD framework that allows you to build, test and deploy your application from GitHub commits and PRs. We call it Katkit. Katkit is a arbitrary code execution engine which allows the user to run arbitrary code before and after deployment. Katkit follows the same notion of a “Tenant” or environment. Thus, tying together CI and CD. In other words, the tests are run against the application in same underlying AWS topology where one’s code is running as against running them in a separate fleet of servers which does not capture the interactions of the application with the AWS infrastructure like IAM, Security groups ELB etc.

At a high level, Katkit functions as follows:

* A repository is linked to a Tenant.
* User chooses a Git commit to run test and deploy
* Katkit deploys a service in the same tenant with the docker image provided by nholuongut, which is essentially like a jenkins worker and had the Katkit agent in it.
* Katkit agent in the CI container checks out the code at that commit inside the container. It then executes ci.sh from the checked-out code. Essentially each build is a short-lived service that is removed once the ci.sh execution is over.
* User can put any arbitrary code in ci.sh
* Katkit allows, for a given run of a commit, the user to execute code in “phases” where in each phase Katkit repeats the above steps with a difference in the ENV variables that are set in each phase. The code inside ci.sh is to read the env variables and perform different actions corresponding to each phase
* Katkit has a special phase called “deployment” where it does not run ci.sh but it looks for the servicdescription.js file (details below), replaces the docker image tag and replaces it with the git commit sha. It is assumed that the user, before invoking the deployment phase, has gone through a prior phase where he build a docker image which was tagged with the git commit sha. The sha is available as an ENV variable in every phase.
