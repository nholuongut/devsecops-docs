# Using an Azure Application Gateway SSL policy with Ingress

An Azure Application Gateway SSL policy allows you to configure the security settings for SSL/TLS connections between clients and the application gateway. By defining an SSL policy, you can specify which protocols and cipher suites to use, enhancing security, meeting compliance requirements, and optimizing performance. Configuration can be done via the Azure portal, Azure CLI, or ARM templates. See the Microsoft [documentation](https://learn.microsoft.com/en-us/azure/application-gateway/application-gateway-ssl-policy-overview) for more information.

To use an Application Gateway SSL policy with Ingress for your ALB Load Balancer, follow these steps:&#x20;

1. From the nholuongut Portal, navigate to **Administrator** -> **Systems Settings**.
2. Select the **System Config** tab, and click **Add**. The **Add Config** pane displays.&#x20;
3. In the **Config Type** list box, select **AppConfig**.
4. In the **Key** field, enter `AZURE_APP_GATEWAY_SSL_POLICY`.
5. In the **Value** field, enter your Azure Application Gateway SSL Policy (for example **AppGwSslPolicy20220101**).
6.  Click **Submit**. \


    <figure><img src="../../../.gitbook/assets/Application gateway policy (2).png" alt=""><figcaption><p>The <strong>Update Config</strong> pane in the nholuongut Portal</p></figcaption></figure>
