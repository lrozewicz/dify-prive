# Integration with TrueFoundry AI Gateway

TrueFoundry provides an enterprise-ready [AI Gateway](https://www.truefoundry.com/ai-gateway) and integrates seamlessly with Dify, providing enterprise-grade AI features including cost tracking, security guardrails, and access controls.

TrueFoundry's AI Gateway routes all LLM calls through the Gateway to ensure your AI applications are secure, compliant, and cost-effective.

## Prerequisites

Before integrating Dify with TrueFoundry, ensure you have:

1. **TrueFoundry Account**: Create a [Truefoundry account](https://www.truefoundry.com/register) and follow the instructions in our [Gateway Quick Start Guide](https://docs.truefoundry.com/gateway/quick-start)
2. **Dify Installation**: Set up Dify using either the [cloud version](https://dify.ai/) or [self-hosted deployment](https://github.com/langgenius/dify) with Docker

## Integration Steps

This guide assumes you have Dify installed and running, and have obtained your TrueFoundry AI Gateway base URL and authentication token.

### Step 1: Access Dify Model Provider Settings

1. Log into your Dify workspace (cloud or self-hosted).

2. Navigate to **Settings** and go to **Model Provider**:

<Frame>
  <img src="https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/model%20provider%20select%20diffy.png?fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=7a07f137e9ee9b8cccbad4419b14bd61" data-og-width="2940" width="2940" data-og-height="1678" height="1678" data-path="images/model provider select diffy.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/model%20provider%20select%20diffy.png?w=280&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=441158fe91546d4bf8fe1a147f6593f2 280w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/model%20provider%20select%20diffy.png?w=560&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=43e7e16b731116bf9ce839af11d7e2fa 560w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/model%20provider%20select%20diffy.png?w=840&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=b20b0bb9dccc4e19e4671c13dba64da9 840w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/model%20provider%20select%20diffy.png?w=1100&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=c3ae9385fd0bb05ff044e27e6325e275 1100w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/model%20provider%20select%20diffy.png?w=1650&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=ae5aa10d378529fcff8c3a67a0bc8fa4 1650w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/model%20provider%20select%20diffy.png?w=2500&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=437b625f9997750fd4de1feaa9037322 2500w" />
</Frame>

### Step 2: Install OpenAI-API-Compatible Provider

1. In the Model Provider section, look for **OpenAI-API-compatible** and click **Install**.

2. Configure the OpenAI-API-compatible provider with your TrueFoundry details:

<Frame>
  <img src="https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/open%20api%20diffy.png?fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=45f47a27b71ccaccee60c644ed8ebb2c" data-og-width="1246" width="1246" data-og-height="1292" height="1292" data-path="images/open api diffy.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/open%20api%20diffy.png?w=280&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=204e76f550d37c0092d5d5b81c25065b 280w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/open%20api%20diffy.png?w=560&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=c04093d8f0b30c93a6d2d97ca92216a8 560w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/open%20api%20diffy.png?w=840&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=a2db996f1ed8925d23de6c19b250070e 840w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/open%20api%20diffy.png?w=1100&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=7ee03107c9113ed308b639d0522ea847 1100w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/open%20api%20diffy.png?w=1650&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=333d8f0d3d1cd827d3216ffc70b9ddf9 1650w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/open%20api%20diffy.png?w=2500&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=4c58d5911b3216ad410344488128086c 2500w" />
</Frame>

Fill in the following configuration:

* **Model Name**: Enter your TrueFoundry model ID (e.g., `openai-main/gpt-4o`)
* **Model display name**: Enter a display name (e.g., `Gpt-4o`)
* **API Key**: Enter your TrueFoundry API Key
* **API endpoint URL**: Enter your TrueFoundry Gateway base URL (e.g., `https://internal.devtest.truefoundry.tech/api/llm/api/inference/openai`)
* **model name for API endpoint**: Enter the endpoint model name (e.g., `openai-main/gpt-4o`)

<Frame>
  <img src="https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/new-code-snippet.png?fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=fee6d1b13c16aea461a772d3fa254da2" data-og-width="2940" width="2940" data-og-height="1664" height="1664" data-path="images/new-code-snippet.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/new-code-snippet.png?w=280&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=ba152fc95dc120c1c7325971f3e83b3b 280w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/new-code-snippet.png?w=560&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=c6f92a911e453d877a0ab9c8f27c24eb 560w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/new-code-snippet.png?w=840&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=895136a986f47062e182b5dae9d415bf 840w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/new-code-snippet.png?w=1100&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=0ec5416096bdf66ae781f2731376e992 1100w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/new-code-snippet.png?w=1650&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=510d40cfe2d02f30531093add91a8e45 1650w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/new-code-snippet.png?w=2500&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=daf6f84f404fb1118e03b65fdabb665b 2500w" />
</Frame>

### Step 3: Save and Test Your Configuration

1. Click **Save** to apply your configuration in Dify.

2. Create a new application or workflow to test the integration:

3. Test the integration by creating a simple LLM workflow to verify that Dify is successfully communicating with TrueFoundry's AI Gateway.

<Frame>
  <img src="https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/result%20diffy.png?fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=63cfcd63a8fef49e46cece78b665293e" data-og-width="2502" width="2502" data-og-height="1532" height="1532" data-path="images/result diffy.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/result%20diffy.png?w=280&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=f4297a789fffcac62eb17491c8d6ef07 280w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/result%20diffy.png?w=560&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=d86f5772162cf42c16f173908e9d6bf6 560w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/result%20diffy.png?w=840&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=593860648e1f454d86291e252daa8957 840w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/result%20diffy.png?w=1100&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=bd3481139c946edc9394f37c75379c11 1100w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/result%20diffy.png?w=1650&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=1f321a971d5d68e23558fe030cb9fcf1 1650w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/result%20diffy.png?w=2500&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=d4eddc2a34609ada220658122d21e1de 2500w" />
</Frame>

Your Dify workspace is now integrated with TrueFoundry's AI Gateway and ready for building AI applications, workflows, and agents.

***

[Edit this page](https://github.com/langgenius/dify-docs/edit/main/en/development/models-integration/truefoundry.mdx) | [Report an issue](https://github.com/langgenius/dify-docs/issues/new?template=docs.yml)
