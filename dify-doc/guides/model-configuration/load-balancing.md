# Configure Load Balancing

## Introduction

<Info>
  Load balancing is a paid feature. You can enable it through [a paid SaaS subscription or an Enterprise license](https://dify.ai/pricing).
</Info>

Model providers typically enforce rate limits on API access within a specific timeframe to ensure stability and fair use. For enterprise applications, a high volume of concurrent requests from a single credential can easily trigger these limits, disrupting user access.

An effective solution is load balancing, which distributes request traffic across multiple model credentials. This prevents rate limit issues and single points of failure, ensuring business continuity and faster response times for all users.

Dify employs a round-robin strategy for load balancing, sequentially routing model requests to each credential in the load balancing pool. If a credential hits a rate limit, it is temporarily removed from rotation for one minute to avoid futile retries.

## Procedure

To configure load balancing for a model, follow these steps:

1. In the model list, find the target model, click the corresponding **Config**, and select **Load balancing**.

2. In the load balancing pool, click **Add credential** to select from existing credentials or add a new one.

<Info>
  **Default Config** refers to the default credential currently specified for that model.
</Info>

<Tip>
  If a credential has a higher quota or better performance, you can add it multiple times to increase its weight in the load balancing rotation, allowing it to handle a larger share of the request load.
</Tip>

<img src="https://mintcdn.com/dify-6c0370d8/7Ipos5aBzrNU-g5O/images/add_load_balancing_credential.png?fit=max&auto=format&n=7Ipos5aBzrNU-g5O&q=85&s=e689bbc418d53cce8344b7c44c0fe694" alt="Add credentials for load balancing" data-og-width="1194" width="1194" data-og-height="872" height="872" data-path="images/add_load_balancing_credential.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/7Ipos5aBzrNU-g5O/images/add_load_balancing_credential.png?w=280&fit=max&auto=format&n=7Ipos5aBzrNU-g5O&q=85&s=d7f48a7820d0af3bcc9ad7f24b051710 280w, https://mintcdn.com/dify-6c0370d8/7Ipos5aBzrNU-g5O/images/add_load_balancing_credential.png?w=560&fit=max&auto=format&n=7Ipos5aBzrNU-g5O&q=85&s=01d5e8e1250b99b3b33e0e813982abe8 560w, https://mintcdn.com/dify-6c0370d8/7Ipos5aBzrNU-g5O/images/add_load_balancing_credential.png?w=840&fit=max&auto=format&n=7Ipos5aBzrNU-g5O&q=85&s=3c29b6eec529e8a245606fff1f4d7b1c 840w, https://mintcdn.com/dify-6c0370d8/7Ipos5aBzrNU-g5O/images/add_load_balancing_credential.png?w=1100&fit=max&auto=format&n=7Ipos5aBzrNU-g5O&q=85&s=a18953c51ac9f524b43c07d6ee2b247d 1100w, https://mintcdn.com/dify-6c0370d8/7Ipos5aBzrNU-g5O/images/add_load_balancing_credential.png?w=1650&fit=max&auto=format&n=7Ipos5aBzrNU-g5O&q=85&s=60a649b3d7b36df42f253311bb4e4427 1650w, https://mintcdn.com/dify-6c0370d8/7Ipos5aBzrNU-g5O/images/add_load_balancing_credential.png?w=2500&fit=max&auto=format&n=7Ipos5aBzrNU-g5O&q=85&s=f8a87b70255870ad3328a3ce1aeda830 2500w" />

3. Enable at least two credentials in the load balancing pool, then click **Save**. Models with load balancing enabled will be marked with a special icon.

<img src="https://mintcdn.com/dify-6c0370d8/-0brHWfkawXPDZZK/images/load_balancing_icon.png?fit=max&auto=format&n=-0brHWfkawXPDZZK&q=85&s=ada7457cf9fcf9c66ddd73eb80214340" alt="Load balancing icon" data-og-width="1564" width="1564" data-og-height="358" height="358" data-path="images/load_balancing_icon.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/-0brHWfkawXPDZZK/images/load_balancing_icon.png?w=280&fit=max&auto=format&n=-0brHWfkawXPDZZK&q=85&s=1dc66baca22603f71122be8c035529a7 280w, https://mintcdn.com/dify-6c0370d8/-0brHWfkawXPDZZK/images/load_balancing_icon.png?w=560&fit=max&auto=format&n=-0brHWfkawXPDZZK&q=85&s=ed00102c0fd6613d65031ab927df0943 560w, https://mintcdn.com/dify-6c0370d8/-0brHWfkawXPDZZK/images/load_balancing_icon.png?w=840&fit=max&auto=format&n=-0brHWfkawXPDZZK&q=85&s=03fd46af96e266d14d20f57918470357 840w, https://mintcdn.com/dify-6c0370d8/-0brHWfkawXPDZZK/images/load_balancing_icon.png?w=1100&fit=max&auto=format&n=-0brHWfkawXPDZZK&q=85&s=be9ee3016591508a1e7c2c52ce877238 1100w, https://mintcdn.com/dify-6c0370d8/-0brHWfkawXPDZZK/images/load_balancing_icon.png?w=1650&fit=max&auto=format&n=-0brHWfkawXPDZZK&q=85&s=dafb37402661847f74b7ae12498eb423 1650w, https://mintcdn.com/dify-6c0370d8/-0brHWfkawXPDZZK/images/load_balancing_icon.png?w=2500&fit=max&auto=format&n=-0brHWfkawXPDZZK&q=85&s=b1604c6726c7f649fb8f99fecd45331f 2500w" />

<Info>
  When you switch from load-balancing mode back to the default single-credential mode, your load-balancing configuration is preserved for future use.
</Info>

***

[Edit this page](https://github.com/langgenius/dify-docs/edit/main/en/guides/model-configuration/load-balancing.mdx) | [Report an issue](https://github.com/langgenius/dify-docs/issues/new?template=docs.yml)
