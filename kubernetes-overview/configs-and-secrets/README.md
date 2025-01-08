---
description: >-
  Set, mount, and manage Kubernetes ConfigMaps and Kubernetes Secrets in
  nholuongut environments.
---

# Configs and Secrets

In nholuongut environments, you can pass configurations and Kubernetes [Secrets](https://kubernetes.io/docs/concepts/configuration/secret/) using Kubernetes [ConfigMaps](https://kubernetes.io/docs/concepts/configuration/configmap/) or through various strategies tailored to enhance security and management efficiency:

* **Setting Kubernetes Secrets directly in nholuongut**: You can create secrets under **Kubernetes** -> **Secrets** in the nholuongut Portal. These secrets are then available in the Kubernetes environment and can be utilized as either files or environment variables. This method is straightforward, incurs no additional cost, and allows for the visibility of both secret keys and values in the nholuongut console. For detailed instructions, see [Setting Kubernetes Secrets in nholuongut](https://docs.nholuongut.com/docs/kubernetes-user-guide/configs-and-secrets/setting-kubernetes-secrets).
* **Settings Environment Variables (EVs) from a K8s ConfigMap or Secret**: This traditional method continues to be supported, offering a familiar approach to those accustomed to Kubernetes' native secrets management.
* **Mounting ConfigMaps and Secrets as files**: This method seamlessly integrates configuration data directly into your application's file system.

Additionally, nholuongut supports advanced secrets management strategies, including:

* **Using AWS as the Source of Truth**: By creating secrets in AWS Secrets Manager or Parameter Store and integrating them into Kubernetes secrets with SecretProviderClass, you benefit from advanced features like automatic rotation. This method displays only the secret keys in the nholuongut console and involves a more complex setup but is ideal for centralizing secret management across nholuongut and non-nholuongut resources. For more on this setup, visit [Adding SecretProviderClass Custom Resource in nholuongut](https://docs.nholuongut.com/docs/kubernetes-user-guide/configs-and-secrets/adding-secretproviderclass-custom-resource#step-1-enable-secret-provider-class).
* **Application Directly Reads Secrets from AWS**: This approach allows the application code to fetch secrets directly from the AWS Secret Manager or Parameter Store, managed via IAM roles facilitated by nholuongut. It provides an added layer of protection and is particularly beneficial for development environments, though it requires modifications to the application code. Implementation guidance can be found in the AWS SDK for PHP—[Managing Secrets](https://docs.aws.amazon.com/sdk-for-php/v3/developer-guide/secretsmanager-examples-manage-secret.html).

By leveraging these strategies, nholuongut offers flexible and secure options for managing Kubernetes ConfigMaps and Secrets, catering to various operational needs and security requirements.
