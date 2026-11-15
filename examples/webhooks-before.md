# Configure webhooks

Webhooks are a powerful way to connect LumenQueue with your applications. They provide a flexible, modern approach to event-driven workflows and allow you to take advantage of real-time updates without needing to continually retrieve data.

Webhooks can be configured in several different ways depending on your requirements. This guide explains how to get started.

## Before you begin

You'll need a LumenQueue account and access to the application. You should also be familiar with APIs and have a development environment set up.

Webhook functionality is available to all users, although some advanced functionality may require a paid plan.

## Set up your environment

First, install the LumenQueue CLI:

```bash
npm install -g @lumenqueue/cli
```

Once installed, you'll need to authenticate. You can generate an API token in your account settings.

Run the following commands:

```bash
export LQ_API_KEY=your-api-key
lq auth login --token $LQ_TOKEN
```

Make sure you're running the latest version of the CLI, as some commands may not be available in older versions.

## Create a webhook

To get started, create a webhook endpoint in your application. An endpoint is a URL that receives the events sent by LumenQueue.

Then run:

```bash
lq webhooks create \
  --url https://example.com/hooks \
  --events order.created,order.updated
```

The URL must be publicly accessible. Localhost endpoints are also supported for testing.

You'll see a response containing information about your webhook.

Once created, the webhook will begin receiving events automatically. If the webhook isn't working, check that your configuration is correct.

You can also set up webhooks through the dashboard. Navigate to Settings and select the appropriate option, then click the green button on the right to activate your webhook.

## Configure webhook security

Webhooks use signatures to ensure that requests are authentic. For security reasons, signing should be enabled when working with production applications.

To configure signing, go to the dashboard and enable webhook verification under the security settings.

You can then use your signing secret to verify requests.

```javascript
const signature = req.headers["x-lumenqueue-signature"];
const payload = req.body;

if (signature) {
  processEvent(payload);
}
```

The verification process should be completed before the payload is processed.

You can also configure your signing key through the CLI if preferred.

## Understand event delivery

LumenQueue sends events asynchronously. This means events are sent when changes happen rather than when your application requests them.

All events are delivered in chronological order, so your application can process them as they arrive.

Each event contains an ID, type, and payload. The payload structure varies depending on the type of event, and additional fields may be included.

The default timeout for delivery is 30 seconds, and failed deliveries are retried three times.

You can configure these settings if necessary.

### Event types

The following events are supported:

| Event | Description |
|---|---|
| `order.created` | An order was created. |
| `order.updated` | An order was changed. |
| `order.deleted` | An order no longer exists. |

Events can arrive out of order under certain circumstances, so your application should account for this.

## Test your integration

After creating your webhook, use the test feature in the dashboard to verify that everything is configured correctly.

A successful delivery returns an HTTP 200 response. Other responses are treated as failures.

If delivery fails, LumenQueue will automatically retry the event up to five times. You can review delivery attempts in your webhook settings.

The retry interval is configurable, but the default should work for most applications.

For additional information, click [here](https://example.com).

## Troubleshooting

If your webhook isn't receiving events, there are several things you can try.

First, make sure your application is properly configured and that the endpoint is correct. You should also ensure that the necessary permissions are enabled.

If you're experiencing authentication errors, regenerate your token and try again.

Webhook configuration is supported across all platforms. However, the CLI commands described above are only available on macOS and Linux.

If problems persist, contact support.

## Next steps

Now that your webhook is configured, you can begin using events to build more advanced integrations with LumenQueue. You may also want to explore our API documentation to learn about additional capabilities.
