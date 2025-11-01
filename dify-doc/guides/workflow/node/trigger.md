# Trigger

## Introduction

<Info>
  Triggers are available for workflow applications only.
</Info>

A trigger is a type of Start node that enables your workflow to run automatically—on a schedule or in response to events from external systems (e.g., GitHub, Gmail, or your own internal systems)—rather than waiting for active initiation from a user or an API call.

Triggers are ideal for automating repetitive tasks or integrating your workflow with third-party applications to achieve automatic data synchronization and processing.

A workflow can have multiple triggers running in parallel. You can also build several independent workflows on the same canvas, each starting with its own triggers.

The trigger source for each workflow execution is displayed in the **Logs** section.

<img src="https://mintcdn.com/dify-6c0370d8/HVQw7qIn2dg_iQmO/images/trigger.png?fit=max&auto=format&n=HVQw7qIn2dg_iQmO&q=85&s=1d51cd27b4d1d08449e9250c9d22bd9b" alt="Trigger" width="450" data-og-width="784" data-og-height="778" data-path="images/trigger.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/HVQw7qIn2dg_iQmO/images/trigger.png?w=280&fit=max&auto=format&n=HVQw7qIn2dg_iQmO&q=85&s=edb6ab00a452abb2ea1e8df310ce4b71 280w, https://mintcdn.com/dify-6c0370d8/HVQw7qIn2dg_iQmO/images/trigger.png?w=560&fit=max&auto=format&n=HVQw7qIn2dg_iQmO&q=85&s=396a472057ae7e2083662e7be40edc70 560w, https://mintcdn.com/dify-6c0370d8/HVQw7qIn2dg_iQmO/images/trigger.png?w=840&fit=max&auto=format&n=HVQw7qIn2dg_iQmO&q=85&s=697383714b43d792aface581e6aea5ba 840w, https://mintcdn.com/dify-6c0370d8/HVQw7qIn2dg_iQmO/images/trigger.png?w=1100&fit=max&auto=format&n=HVQw7qIn2dg_iQmO&q=85&s=2ba154647b4b8b791783c55468598ef8 1100w, https://mintcdn.com/dify-6c0370d8/HVQw7qIn2dg_iQmO/images/trigger.png?w=1650&fit=max&auto=format&n=HVQw7qIn2dg_iQmO&q=85&s=2eb91ae52f1e6972b25c249fe91e74db 1650w, https://mintcdn.com/dify-6c0370d8/HVQw7qIn2dg_iQmO/images/trigger.png?w=2500&fit=max&auto=format&n=HVQw7qIn2dg_iQmO&q=85&s=75379d2a31f480baf02b993b4da3afb2 2500w" />

## Trigger Types

* [Schedule Trigger](/en/guides/workflow/node/schedule-trigger)

  * Runs your workflow at specified times or intervals.

  * Example: Automatically generate a daily sales report every morning at 9 AM and email it to your team.

* [Plugin Trigger](/en/guides/workflow/node/plugin-trigger)

  * Runs your workflow when a specific event occurs in an external system, via an event subscription through a trigger plugin.

  * Example: Automatically analyze and archive new messages in a specific Slack channel via a subscription to the `New Message in Channel` event through a Slack trigger plugin.

* [Webhook Trigger](/en/guides/workflow/node/webhook-trigger)

  * Runs your workflow when a specific event occurs in an external system via a custom webhook.

  * Example: Automatically process new orders in response to an HTTP request containing the order details from your e-commerce platform.

<Tip>
  Both plugin triggers and webhook triggers make your workflow *event-driven*. Here's how to choose:

  1. Use a **plugin trigger** when a trigger plugin is available for your target external system. You can simply subscribe to the supported events.

  2. Use a **webhook trigger** when no corresponding plugin exists or when you need to capture events not supported by existing plugins. In such cases, you'll need to set up custom webhooks in the external system.
</Tip>

## Enable or Disable Triggers

In the **Quick Settings** side menu, you can enable or disable published triggers. Disabled triggers do not initiate workflow execution.

<Info>
  Only published triggers appear in **Quick Settings**. If you don't see an added trigger listed, ensure it has been published first.
</Info>

<img src="https://mintcdn.com/dify-6c0370d8/ssHaNZ_xFtdKDTtH/images/enable_disable_added_trigger.png?fit=max&auto=format&n=ssHaNZ_xFtdKDTtH&q=85&s=e1d86a3da60d7c842d38c0f80e0bb7b4" alt="Enable or Disable Published Triggers" width="500" data-og-width="822" data-og-height="916" data-path="images/enable_disable_added_trigger.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/ssHaNZ_xFtdKDTtH/images/enable_disable_added_trigger.png?w=280&fit=max&auto=format&n=ssHaNZ_xFtdKDTtH&q=85&s=9304b991518338d763e71dabb1fd4032 280w, https://mintcdn.com/dify-6c0370d8/ssHaNZ_xFtdKDTtH/images/enable_disable_added_trigger.png?w=560&fit=max&auto=format&n=ssHaNZ_xFtdKDTtH&q=85&s=bcbc4847151f0e7cac73c7976efe5f0f 560w, https://mintcdn.com/dify-6c0370d8/ssHaNZ_xFtdKDTtH/images/enable_disable_added_trigger.png?w=840&fit=max&auto=format&n=ssHaNZ_xFtdKDTtH&q=85&s=61e1c3b325e9f4eeaa4ea88c2818b7b6 840w, https://mintcdn.com/dify-6c0370d8/ssHaNZ_xFtdKDTtH/images/enable_disable_added_trigger.png?w=1100&fit=max&auto=format&n=ssHaNZ_xFtdKDTtH&q=85&s=9065fc6954be00122c698bb66264a875 1100w, https://mintcdn.com/dify-6c0370d8/ssHaNZ_xFtdKDTtH/images/enable_disable_added_trigger.png?w=1650&fit=max&auto=format&n=ssHaNZ_xFtdKDTtH&q=85&s=fc5b719627a1194450357486fdefb6aa 1650w, https://mintcdn.com/dify-6c0370d8/ssHaNZ_xFtdKDTtH/images/enable_disable_added_trigger.png?w=2500&fit=max&auto=format&n=ssHaNZ_xFtdKDTtH&q=85&s=057549117ddd812eb0a37d61a3c7f5e0 2500w" />

## Test Multiple Triggers

When a workflow has multiple triggers, you can click **Test Run** > **Run all triggers** to test them at once. The first trigger that activates will initiate the workflow, and the others will then be ignored.

After you click **Run all triggers**:

* Schedule triggers will run at the next scheduled execution time.

* Plugin triggers will listen for subscribed events.

* Webhook triggers will listen for external HTTP requests.

***

[Edit this page](https://github.com/langgenius/dify-docs/edit/main/en/guides/workflow/node/trigger.mdx) | [Report an issue](https://github.com/langgenius/dify-docs/issues/new?template=docs.yml)
