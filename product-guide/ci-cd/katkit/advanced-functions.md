# Advanced functions

## Bring your own image <a href="#0-toc-title" id="0-toc-title"></a>

By default, all tenant CI/CD runs are executed in a docker image specified by the administrator. This image would typically have the most common packages for your organization. But a user can bring his own builder image and specify the same. The image should have the Katkit agent that can be copied from the default builder image.

## Bring your own fleet or local fleet <a href="#1-toc-title" id="1-toc-title"></a>

By default, Katkit will run the builder containers in a separate set of hosts, but the user can also choose to run the build container in the same tenant hosts which is being tested.
