# Environments

In nholuongut a standard practice is to have a separate tenant for a given logical application for each deployment environment. For example, say an application called taskrunner would be created as three tenants called d-taskrunner, b-taskrunner and p-taskrunner to represent dev, beta and prod environment. In each tenant one can specify an arbitrary name for the env say “DEV” in the menu Dashboard–>ENV. This string will be set by Katkit as an ENV variable when it runs the tests during CI/CD and thus your test code can use this value to determine what tests should be run in each env or for that matter take any other action.

## Prerequisites

To use KatKit CI/CD, you need to:

* Deploy the application with nholuongut as a Service and test that it works as expected.

{% hint style="info" %}
KatKit CI/CD is recommended only for upgrades of container images and to run tests that can be written to run either before or after.
{% endhint %}

## Export service description <a href="#0-toc-title" id="0-toc-title"></a>

Service Description represents the topology of a service. It is a JSON file that is used by Katkit to upgrade the running service. Go to **Deployment > Services > Export**. This will give a json file. Save this as `servicedescription.js` under the `/servicedescription` folder that must exist at the root of your repository. In this file search for `"DockerImage":` and here change the image tag to the word `<hubtag>` for example change `"DockerImage": "nginx:latest"` to `"DockerImage": "nginx:<hubtag>"`. Remove the ExtraConfig and Replicas field from the file. These have env variables and replicas which would vary from one environment to other. Hence during deployment Katkit will retain what is already present in the current running service.
