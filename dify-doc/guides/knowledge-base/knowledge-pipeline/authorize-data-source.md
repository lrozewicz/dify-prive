# Authorize Data Source

Dify supports connections to various external data sources. To ensure data security and access control, different data sources require appropriate authorization configurations. Dify provides two main authorization methods: **API Key** and **OAuth**.

## Accessing Data Source Authorization

In Dify, you can access data source authorization through the following two methods:

### I. Knowledge Pipeline Orchestration

When orchestrating a knowledge pipeline, select the data source node that requires authorization. Click **Connect** on the right panel.

<img src="https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-1.PNG?fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=e85d0e180bc24a78429b3ec16598a558" alt="Knowledge Pipeline Authorization" data-og-width="1280" width="1280" data-og-height="435" height="435" data-path="images/knowledge-base/authorize-data-1.PNG" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-1.PNG?w=280&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=f750da60b7aab1e04f87dcc62f4b15cd 280w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-1.PNG?w=560&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=9088ce99d6c192ea6a3b57825f2f6f5b 560w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-1.PNG?w=840&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=1a162505515a45a6cbc79ddee1d5a65d 840w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-1.PNG?w=1100&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=7a9c24f4b5ae680f42eedf3cfa5817e7 1100w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-1.PNG?w=1650&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=ab78b73f773db5835950222d0bae2912 1650w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-1.PNG?w=2500&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=2417ea54bceaf862184cb8f3e9aeff10 2500w" />

### II. Settings

Click your avatar in the upper right corner and select **Settings**. Navigate to **Data Sources** and find the data source you wish to authorize.

<img src="https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-2.PNG?fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=10fc039d69de4ae216fd99182e20aaca" alt="Settings Authorization" data-og-width="1280" width="1280" data-og-height="619" height="619" data-path="images/knowledge-base/authorize-data-2.PNG" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-2.PNG?w=280&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=4d68ca80fc0d088b9b073f323b33c905 280w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-2.PNG?w=560&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=9ae1286c5e2721a470b1636f535cb4db 560w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-2.PNG?w=840&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=0b8c9810cfb6080b69ebba7cb4e447de 840w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-2.PNG?w=1100&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=4651d826c0d5604d96bf6de037721d8d 1100w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-2.PNG?w=1650&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=75edbc153eb766500fb2162ee81030fc 1650w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-2.PNG?w=2500&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=b48985490cba8fcd8bc095801e1a1f6f 2500w" />

## Supported Data Source Authorization

| Data Source  | API Key | OAuth |
| ------------ | ------- | ----- |
| Notion       | ✅       | ✅     |
| Jina Reader  | ✅       |       |
| Firecrawl    | ✅       |       |
| Google Drive |         | ✅     |
| Dropbox      |         | ✅     |
| OneDrive     |         | ✅     |

## Authorization Processes

### API Key Authorization

API Key authorization is a key-based authentication method suitable for enterprise-level services and developer tools. You need to generate API Keys from the corresponding service providers and configure them in Dify.

#### Process

1. On the **Data Source** page, navigate to the corresponding data source. Click **Configure** and then **Add API Key**.

   <img src="https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-3.PNG?fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=0d6e202e0e1b86bb29934182085469b4" alt="Add API Key" data-og-width="1381" width="1381" data-og-height="256" height="256" data-path="images/knowledge-base/authorize-data-3.PNG" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-3.PNG?w=280&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=6bedce69b4aff401e24e21afc15eb9ed 280w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-3.PNG?w=560&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=1cda7ad19dd8780c14675a8512615394 560w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-3.PNG?w=840&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=e0daa14751aea5e8e63063795ee56f53 840w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-3.PNG?w=1100&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=c58e7d1a46107d862d0fa3b377b73443 1100w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-3.PNG?w=1650&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=b47abe864763c33496fc02c1b7d62517 1650w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-3.PNG?w=2500&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=fcf002f7d91f9b6674bc7e1285dd976c 2500w" />

2. In the pop-up window, fill in the **Authorization Name** and **API Key**. Click **Save** to complete the setup.

   <img src="https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-4.png?fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=3c38c6e7cac17a43ac1cd82e2eaf76dd" alt="API Key Configuration" data-og-width="1280" width="1280" data-og-height="720" height="720" data-path="images/knowledge-base/authorize-data-4.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-4.png?w=280&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=49ef1c68a7b52824d0782d0bc64dcc5b 280w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-4.png?w=560&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=5f4e201693c0a451dd02773e5d44a227 560w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-4.png?w=840&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=739716927bbe51637d5e0bbb2b76bd3e 840w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-4.png?w=1100&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=efd7b3170a8229e9ca6f9e475fb47c58 1100w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-4.png?w=1650&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=9d5f7264781b1ff43f37896e03ba9c88 1650w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-4.png?w=2500&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=ad79d04e03e215f4d6fdcc796133ad4e 2500w" />

The API key will be securely encrypted. Once completed, you can start using the data source (e.g., Jina Reader) for knowledge pipeline orchestration.

<img src="https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-6.png?fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=9920807bc2169b7d8324fc4a15018c8a" alt="API Key Complete" data-og-width="1328" width="1328" data-og-height="256" height="256" data-path="images/knowledge-base/authorize-data-6.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-6.png?w=280&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=585fe44755aacc04cb40e7d6df5daee2 280w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-6.png?w=560&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=53500d3b6fa06ac8c86bf2c1f4d8b5ce 560w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-6.png?w=840&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=16a8044287b7746517bc5c855cc711a3 840w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-6.png?w=1100&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=6c0eb12357133f3e6b2a40734c4c48a6 1100w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-6.png?w=1650&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=5553409362cbd45339b49b3924d8329d 1650w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-6.png?w=2500&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=9e6c72c3e2afafb931e9d2c22f771e6d 2500w" />

### OAuth Authorization

OAuth is an open standard authorization protocol that allows users to authorize third-party applications to access their resources on specific service providers without exposing passwords.

#### Process

1. On the **Data Source** page, select an OAuth-supported data source. Click **Configure** and then **Add OAuth**.

   <img src="https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-7.png?fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=7ed7d760fd45ddddab5cb0c696e78046" alt="Add OAuth" data-og-width="1280" width="1280" data-og-height="305" height="305" data-path="images/knowledge-base/authorize-data-7.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-7.png?w=280&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=cddb729ecbdf5ebe3adba1f682d1b551 280w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-7.png?w=560&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=65f06ea9393f7f36c9e32c6cc1ae2a6f 560w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-7.png?w=840&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=820f0fbed0f52e641cea0c54f7d9e8cb 840w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-7.png?w=1100&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=361cc758591c70d6901634d857b4e66d 1100w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-7.png?w=1650&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=77d03208a4b1d9fe59c30ce0998f77fc 1650w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-7.png?w=2500&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=6b768342eab2530f5f7172ee8b510199 2500w" />

2. Review the permission scope and click **Allow Access**.

<div style={{display: 'flex', flexWrap: 'wrap', gap: '30px'}}>
  <div style={{flex: 1, minWidth: '300px'}}>
        <img src="https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-8.png?fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=aa178ea168624ce8e56c668ed7f0d06e" alt="OAuth Permissions" data-og-width="1242" width="1242" data-og-height="1242" height="1242" data-path="images/knowledge-base/authorize-data-8.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-8.png?w=280&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=03bad7e84a85fd94147439dd6475d5cc 280w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-8.png?w=560&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=3c200696d0c3173ba3b3c236254beff8 560w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-8.png?w=840&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=903bd7184a2e6d5d343611432c314ea2 840w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-8.png?w=1100&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=e03559faea937e7bb48606a28c68d072 1100w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-8.png?w=1650&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=34f3aaba8444fa96f8de04ba6e2c13b5 1650w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-8.png?w=2500&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=741fffcff84d4713d17ec067b61cffd0 2500w" />
  </div>

  <div style={{flex: 1, minWidth: '300px'}}>
        <img src="https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-9.png?fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=1cdde896b888e6135c5cccd587b15a46" alt="OAuth Allow" data-og-width="1280" width="1280" data-og-height="1280" height="1280" data-path="images/knowledge-base/authorize-data-9.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-9.png?w=280&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=240c72e6dccb5db1d1e0f80a5bcf04b3 280w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-9.png?w=560&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=27dd4d01e4df62b21b928df36fae2b81 560w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-9.png?w=840&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=bf1825c53ace6a60ac056d94b3385817 840w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-9.png?w=1100&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=880c967b1306fe45eeab85b19e8de3e2 1100w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-9.png?w=1650&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=44383a796d0ce46022c41ee0a8b2c709 1650w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-9.png?w=2500&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=b4f66cbb58ddb512d5c704ee0ad22887 2500w" />
  </div>
</div>

#### OAuth Client Settings

Dify provides two OAuth client configuration methods: **Default** and **Custom**.

<img src="https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-10.png?fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=6fa847da415eafdd3bd4553567b005a1" alt="OAuth Client Settings" data-og-width="1034" width="1034" data-og-height="580" height="580" data-path="images/knowledge-base/authorize-data-10.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-10.png?w=280&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=4a13a3c7b459ce6cca871ae77a287cac 280w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-10.png?w=560&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=d70fcd6282cc8ea75266d2b76a39539b 560w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-10.png?w=840&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=969a406b82789bba4bbc98648311b25a 840w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-10.png?w=1100&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=321395e8121ee1c938ff4790b7fdcd83 1100w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-10.png?w=1650&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=060c63d675be142768e8579c36a2cff2 1650w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-10.png?w=2500&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=82a85ffda647d49b40e946f1ac4ecfdf 2500w" />

<Tabs>
  <Tab title="Default">
    The default client is primarily supported in the SaaS version, using OAuth client parameters that are pre-configured and maintained by Dify. Users can add OAuth credentials with one click without additional configuration.
  </Tab>

  <Tab title="Custom">
    Custom client is supported across all versions of Dify. Users need to register OAuth applications on third-party platforms and obtain client parameters themselves. This is mainly suitable for data sources that don't have default configuration in the SaaS version, or when enterprises have special security compliance requirements.
  </Tab>
</Tabs>

**Process for Custom OAuth**

1. On the **Data Source** page, select an OAuth-supported data source. Click **Configure** and then the **Setting icon** on the right side of **Add OAuth**.

   <img src="https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-11.png?fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=8329ee62c4fee7be6b446dc132077d6f" alt="Custom OAuth Settings" data-og-width="1280" width="1280" data-og-height="364" height="364" data-path="images/knowledge-base/authorize-data-11.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-11.png?w=280&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=a288cd988477e41e1905c8dd26c7a490 280w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-11.png?w=560&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=6a26cc0f0884e63375b6749fd25eb98c 560w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-11.png?w=840&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=94bf10b24554a94ec780425ad5721f29 840w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-11.png?w=1100&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=1e4df5d0a38845e71d37d0b0bfbdd580 1100w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-11.png?w=1650&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=5f0c8dbcc772dcd241932827bbd84be9 1650w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-11.png?w=2500&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=3cc8711cf5120f47c6a2ea5f631d83bb 2500w" />

2. Choose **Custom**, enter the **Client ID** and **Client Secret**. Click **Save and Authorize** to complete the authorization.

   <img src="https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-12.png?fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=b96222b52fdb37964b82658fdd149313" alt="Custom OAuth Configuration" data-og-width="1198" width="1198" data-og-height="1240" height="1240" data-path="images/knowledge-base/authorize-data-12.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-12.png?w=280&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=fa5089b33623b6f5fbe3371868bcc103 280w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-12.png?w=560&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=9b175b7d4736a32427e682a0dfb91ade 560w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-12.png?w=840&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=cc2c0a8cd6ee6705d9fec61ca6792de4 840w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-12.png?w=1100&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=bc123bf74918d924391d055dd3cd3046 1100w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-12.png?w=1650&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=2c996f82e9e9f9f1a0857919119ebf6c 1650w, https://mintcdn.com/dify-6c0370d8/zkT6R8Ak-WmNYVSe/images/knowledge-base/authorize-data-12.png?w=2500&fit=max&auto=format&n=zkT6R8Ak-WmNYVSe&q=85&s=e839be5616a12078756af1b1be866fc7 2500w" />

***

[Edit this page](https://github.com/langgenius/dify-docs/edit/main/en/guides/knowledge-base/knowledge-pipeline/authorize-data-source.mdx) | [Report an issue](https://github.com/langgenius/dify-docs/issues/new?template=docs.yml)
