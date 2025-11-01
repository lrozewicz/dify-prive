# Plugin Trigger

## Introduction

<Info>
  Triggers are available for workflow applications only.
</Info>

A plugin trigger automatically initiates your workflow when a specific event occurs in an external system. All you need to do is subscribe to these events through a trigger plugin and add the corresponding plugin trigger to your workflow.

For example, suppose you have installed a GitHub trigger plugin. It provides a list of GitHub events you can subscribe to, including `Pull Request`, `Push`, and `Issue`. If you subscribe to the `Pull Request` event and add the `Pull Request` plugin trigger to your workflow, it will automatically run whenever someone opens a pull request in the specified repository.

## Add and Configure a Plugin Trigger

1. On the workflow canvas, right-click and select **Add Node** > **Start**, then choose from the available plugin triggers or search for more in [Dify Marketplace](https://marketplace.dify.ai/?language=en-US\&category=trigger).

   <Tip>
     * If there's no suitable trigger plugin for your target external system, you can [request one from the community](https://github.com/langgenius/dify-plugins/issues/new?template=plugin_request.yaml), [develop one yourself](/plugin-dev-en/0222-trigger-plugin), or use a [webhook trigger](/en/guides/workflow/node/webhook-trigger) instead.

     * A workflow can have multiple plugin triggers running in parallel. When the parallel branches contain identical consecutive nodes, you can add a [Variable Aggregator](/en/guides/workflow/node/variable-aggregator) node to merge the branches before the common section, without duplicating the same nodes across each branch.
   </Tip>

2. Select an existing subscription or [create a new one](#create-a-new-subscription).

   <Tip>
     You can view how many workflows is using a specific subscription from the plugin's details panel under **Plugins**.
   </Tip>

3. Configure any other required settings.

<Info>
  The output variables of a plugin trigger are defined by its trigger plugin and cannot be modified.
</Info>

## Create a New Subscription

<Note>
  A subscription cannot be modified once created. To make changes, delete the existing one and create a new subscription.
</Note>

<Info>
  A trigger plugin supports creating up to 10 subscriptions per workspace.
</Info>

Each subscription is built on a webhook. When you create a subscription, you're essentially setting up a webhook that listens for events from an external system.

<Accordion title="What is a webhook?">
  A webhook allows one system to automatically send real-time data to another. When a certain event occurs, the source system packages the event details into an HTTP request and sends it to a designated URL provided by the destination system.
</Accordion>

Dify supports the following two methods for creating subscriptions (webhooks), but the options available in each plugin depend on how that plugin was designed.

* **Automatic Creation**: You select the events you want to subscribe to, and Dify automatically creates the corresponding webhook in the external system. This requires prior authorization via **OAuth** or **API keys** so Dify can handle the webhook setup on your behalf.

* **Manual Creation**: You create the webhook yourself using the webhook callback URL provided by Dify. No authorization is needed.

<img src="https://mintcdn.com/dify-6c0370d8/ssHaNZ_xFtdKDTtH/images/create_subscription_method.png?fit=max&auto=format&n=ssHaNZ_xFtdKDTtH&q=85&s=133bd91fc9eb403ba846f10ae7f52893" alt="Ways to Create Subscriptions" width="563" data-og-width="770" data-og-height="626" data-path="images/create_subscription_method.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/ssHaNZ_xFtdKDTtH/images/create_subscription_method.png?w=280&fit=max&auto=format&n=ssHaNZ_xFtdKDTtH&q=85&s=395b1ee713bd4f4af22712b3c3185004 280w, https://mintcdn.com/dify-6c0370d8/ssHaNZ_xFtdKDTtH/images/create_subscription_method.png?w=560&fit=max&auto=format&n=ssHaNZ_xFtdKDTtH&q=85&s=c68473ac338d1b7d09995d4e2fa95c71 560w, https://mintcdn.com/dify-6c0370d8/ssHaNZ_xFtdKDTtH/images/create_subscription_method.png?w=840&fit=max&auto=format&n=ssHaNZ_xFtdKDTtH&q=85&s=cad71cd662536a0bd63ad7f833a6793d 840w, https://mintcdn.com/dify-6c0370d8/ssHaNZ_xFtdKDTtH/images/create_subscription_method.png?w=1100&fit=max&auto=format&n=ssHaNZ_xFtdKDTtH&q=85&s=abf5d36f2100f0b582cee99567759e82 1100w, https://mintcdn.com/dify-6c0370d8/ssHaNZ_xFtdKDTtH/images/create_subscription_method.png?w=1650&fit=max&auto=format&n=ssHaNZ_xFtdKDTtH&q=85&s=48fb80f9e4105e242008cd0ec1d06dec 1650w, https://mintcdn.com/dify-6c0370d8/ssHaNZ_xFtdKDTtH/images/create_subscription_method.png?w=2500&fit=max&auto=format&n=ssHaNZ_xFtdKDTtH&q=85&s=c6da7712d961b2505581bee8e137c117 2500w" />

<Tip>
  It's recommended to select all available events when creating a subscription.

  A plugin trigger works only when its corresponding event is included in the linked subscription. Selecting all available events ensures that any plugin trigger you add to the workflow later can use the same subscription, without creating another one.
</Tip>

<Tabs>
  <Tab title="Create with OAuth (Automatic)">
    On Dify Cloud, many popular trigger plugins are pre-configured with default OAuth clients so you can authorize Dify with a single click.

    In self-hosted environments, only the custom OAuth client option is available, meaning that you need to create the OAuth application yourself in the external system.

    <Tabs>
      <Tab title="Default OAuth Client">
        1. Select **Create with OAuth** > **Default** > **Save and Authorize**.

           <Info>
             **Save** means the selected option is set as the default OAuth method for future subscriptions.

             To switch methods later, click the **OAuth Client Settings** icon.

             <img src="https://mintcdn.com/dify-6c0370d8/08YnOTsXHUUWuwGW/images/oauth_client_settings_icon.png?fit=max&auto=format&n=08YnOTsXHUUWuwGW&q=85&s=faa5a5ee180dc478f089c5164fd526aa" alt="OAuth Client Settings Icon" width="300" data-og-width="640" data-og-height="80" data-path="images/oauth_client_settings_icon.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/08YnOTsXHUUWuwGW/images/oauth_client_settings_icon.png?w=280&fit=max&auto=format&n=08YnOTsXHUUWuwGW&q=85&s=7e96f09d1eef0c4423dd841b0b363fd3 280w, https://mintcdn.com/dify-6c0370d8/08YnOTsXHUUWuwGW/images/oauth_client_settings_icon.png?w=560&fit=max&auto=format&n=08YnOTsXHUUWuwGW&q=85&s=a6d6ff01c90ddd0caa5cff382a25b28a 560w, https://mintcdn.com/dify-6c0370d8/08YnOTsXHUUWuwGW/images/oauth_client_settings_icon.png?w=840&fit=max&auto=format&n=08YnOTsXHUUWuwGW&q=85&s=690c9618c945f1f44c5b86a69947b86b 840w, https://mintcdn.com/dify-6c0370d8/08YnOTsXHUUWuwGW/images/oauth_client_settings_icon.png?w=1100&fit=max&auto=format&n=08YnOTsXHUUWuwGW&q=85&s=107411780220e89533890151ca2181b0 1100w, https://mintcdn.com/dify-6c0370d8/08YnOTsXHUUWuwGW/images/oauth_client_settings_icon.png?w=1650&fit=max&auto=format&n=08YnOTsXHUUWuwGW&q=85&s=20e172e3b8999dd262d94a91415b5a81 1650w, https://mintcdn.com/dify-6c0370d8/08YnOTsXHUUWuwGW/images/oauth_client_settings_icon.png?w=2500&fit=max&auto=format&n=08YnOTsXHUUWuwGW&q=85&s=2c1421d995abe4f72dd283c06df6b08a 2500w" />
           </Info>

        2. On the external system's authorization page that pops up, click **Next** to grant Dify access.

        3. Specify the subscription name, select the events you want to subscribe to, and configure any other required settings.

           <Tip>
             We recommend selecting all available events.
           </Tip>

        4. Click **Create**.
      </Tab>

      <Tab title="Custom OAuth Client">
        1. Select **Create with OAuth** > **Custom**.

        2. In the external system, create an OAuth application using the callback URL provided by Dify.

        3. Back in Dify, enter the client ID and client secret of the newly created OAuth application, then click **Save and Authorize**.

           <Info>
             Once saved, the same client credentials can be reused for future subscriptions.
           </Info>

        4. Specify the subscription name, select the events you want to subscribe to, and configure any other required settings.
           <Tip>
             We recommend selecting all available events.
           </Tip>

        5. Click **Create**.
      </Tab>
    </Tabs>

    <Info>
      The **Callback URL** displayed on the subscription configuration page is used internally by Dify to create the webhook in the external system on your behalf.

      You don't need to take any action with this URL.
    </Info>
  </Tab>

  <Tab title="Create with API Key (Automatic)">
    1. Select **Create with API Key**.

    2. Enter the required authentication information, then click **Verify**.

    3. Specify the subscription name, select the events you want to subscribe to, and configure any other required settings.

       <Tip>
         We recommend selecting all available events.
       </Tip>

    4. Click **Create**.

    <Info>
      The **Callback URL** displayed on the subscription configuration page is used internally by Dify when it creates the webhook in the external system on your behalf.

      You don't need to take any action with this URL.
    </Info>
  </Tab>

  <Tab title="Paste URL to Create a New Subscription (Manual)">
    1. Select **Paste URL to create a new subscription**.

    2. Specify the subscription name and use the provided callback URL to manually create a webhook in the external system.

    3. (Optional) Test the created webhook.

       <Info>
         Most external systems automatically test a new webhook by sending a ping request to Dify upon creation.
       </Info>

       1. Trigger a subscribed event so the external system sends an HTTP request to the callback URL.

       2. Return to the **Manual Setup** page and check the **Request Logs** section at the bottom. If the webhook works properly, you'll see the received request and Dify's response.

          <img src="https://mintcdn.com/dify-6c0370d8/08YnOTsXHUUWuwGW/images/plugin_trigger_manual_setup_request_logs.png?fit=max&auto=format&n=08YnOTsXHUUWuwGW&q=85&s=1efc0b873f07aa5be9ff017e49a291cd" alt="Request Logs" width="563" data-og-width="1218" data-og-height="518" data-path="images/plugin_trigger_manual_setup_request_logs.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/08YnOTsXHUUWuwGW/images/plugin_trigger_manual_setup_request_logs.png?w=280&fit=max&auto=format&n=08YnOTsXHUUWuwGW&q=85&s=93bab440185383d47d9f39837f2f5c2f 280w, https://mintcdn.com/dify-6c0370d8/08YnOTsXHUUWuwGW/images/plugin_trigger_manual_setup_request_logs.png?w=560&fit=max&auto=format&n=08YnOTsXHUUWuwGW&q=85&s=b30a45323ee291bd1672453fc85c1a41 560w, https://mintcdn.com/dify-6c0370d8/08YnOTsXHUUWuwGW/images/plugin_trigger_manual_setup_request_logs.png?w=840&fit=max&auto=format&n=08YnOTsXHUUWuwGW&q=85&s=39b93ed008312277c4d7b0b908b97aff 840w, https://mintcdn.com/dify-6c0370d8/08YnOTsXHUUWuwGW/images/plugin_trigger_manual_setup_request_logs.png?w=1100&fit=max&auto=format&n=08YnOTsXHUUWuwGW&q=85&s=3c6ac7a64bf53770c26e2fd541814ead 1100w, https://mintcdn.com/dify-6c0370d8/08YnOTsXHUUWuwGW/images/plugin_trigger_manual_setup_request_logs.png?w=1650&fit=max&auto=format&n=08YnOTsXHUUWuwGW&q=85&s=556667716d758728adf5e90c819c853e 1650w, https://mintcdn.com/dify-6c0370d8/08YnOTsXHUUWuwGW/images/plugin_trigger_manual_setup_request_logs.png?w=2500&fit=max&auto=format&n=08YnOTsXHUUWuwGW&q=85&s=147d3d7762c57b8d687885f897c7e3fd 2500w" />

    4. Click **Create**.
  </Tab>
</Tabs>

## Test a Plugin Trigger

To test an unpublished plugin trigger, you must first click **Run this step** or test-run the entire workflow. This puts the trigger into a listening state so that it can monitor external events. Otherwise, the trigger will not capture subscribed events even when they occur.

***

[Edit this page](https://github.com/langgenius/dify-docs/edit/main/en/guides/workflow/node/plugin-trigger.mdx) | [Report an issue](https://github.com/langgenius/dify-docs/issues/new?template=docs.yml)
