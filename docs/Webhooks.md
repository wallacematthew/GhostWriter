---
layout: default
title: Webhooks
nav_order: 8
has_children: false
has_toc: true
---

# Content Export Webhook
{: .no_toc }

The Content Export Webhook allows you to receive generated content asynchronously, providing a more efficient and scalable solution for exporting large amounts of content or handling high volumes of export requests. Instead of waiting for a synchronous API call to complete, GhostWriter sends an HTTP request to a specified webhook URL with the exported content in the request payload.

This article provides an overview of the Content Export Webhook, including how to register a webhook URL, configure the export request, and handle the webhook payload.

## Table of contents
{: .no_toc }

- TOC
{:toc}

## Registering a Webhook URL

To use the Content Export Webhook, you'll need to register a webhook URL in your GhostWriter account settings. Follow these steps:

1. Log in to your GhostWriter account.
1. Go to the **Projects** page and select a project.
2. Go to the **Webhooks** section.
3. Click **Add Webhook.**
4. Enter a name for your webhook and provide the webhook URL where GhostWriter should send the exported content.
5. Select **Content Export** as the webhook event type.
6. Click **Save** to register the webhook.

## Configuring the Export Request

To initiate a content export request, use the GhostWriter API or the UI. When using the API, include the `webhook` parameter in your export request payload, and set its value to the registered webhook's ID. The export request should also include any other necessary parameters, such as `projectId`, `outputFormat`, and `language`.

```json
{
  **projectId**: **your_project_id**,
  **outputFormat**: **pdf**,
  **language**: **en**,
  **webhook**: **your_webhook_id**
}
```

## Handling the Webhook Payload

When GhostWriter completes the content export, it sends an HTTP POST request to the registered webhook URL. The request payload contains the exported content and metadata about the export request.

## Sample Webhook Payload

```json
{
  **event**: **content_export**,
  **timestamp**: 1620421315,
  **data**: {
    **projectId**: **your_project_id**,
    **outputFormat**: **pdf**,
    **language**: **en**,
    **file**: {
      **filename**: **exported_content.pdf**,
      **content**: **base64_encoded_exported_content**
    }
  }
}
```

Upon receiving the webhook request, your server or application should process the content accordingly. This may involve decoding the base64-encoded content, saving the file, distributing it to team members, or publishing it on a website.