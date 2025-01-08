# Troubleshooting

## Failure to Login to ECR

Sometimes on Windows based agents will fail to login to ECR due to missing dependency of ECR credentials helper. Basically all aws api calls require certain headers. Dockers api for registries don't require these headers. Therefore ECR is not exactly a normal docker registry. This credentials helper just hooks into docker and adds those required aws headers to any request to ECR.

If the ECR login step of your pipeline has a failure that looks like:

> Error response from daemon: login attempt to https://\*\*\*\*\*\*.dkr.ecr.us-east-1.amazonaws.com/v2/ failed with status: 400 Bad Request

You can add a step to install the ECR Credenteials hellper, for example:

```sh
go install github.com/awslabs/amazon-ecr-credential-helper/ecr-login/cli/docker-credential-ecr-login@latest
```

More details on the ECR Credentials helper located [here](https://github.com/awslabs/amazon-ecr-credential-helper)

