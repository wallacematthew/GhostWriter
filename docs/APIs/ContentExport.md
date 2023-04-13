---
layout: default
title: Content Export API
parent: APIs
nav_order: 2
---

# Content Export API
{: .no_toc }

The Content Export API allows you to export the generated content in various formats, such as PDF, HTML, or Markdown. It enables users to easily share and distribute their documentation across different channels and platforms.

## Table of contents
{: .no_toc }

- TOC
{:toc}

## Endpoint

```GET /api/v1/content/export```

## Parameters

| Parameter     | Type   | Description                                                                                                 | Required |
|---------------|--------|-------------------------------------------------------------------------------------------------------------|----------|
| `project_id`  | string | The unique identifier of the project for which the content is being exported.                               | Yes      |
| `format`      | string | The desired output format for the exported content. Accepted values: `pdf`, `html`, `markdown`.             | Yes      |
| `filename`    | string | The desired filename for the exported content.                                                              | No       |
| `destination` | string | The destination URL or path where the exported content should be stored.                                    | No       |
| `access_token`| string | The authentication token for the user or application making the request.                                   | Yes      |

## Sample Request

```bash
curl -X POST "https://ghostwriter.example.com/api/v1/content/export" \
     -H "Content-Type: application/json" \
     -H "Authorization: Bearer <your_access_token>" \
     -d '{
           "project_id": "12345",
           "format": "pdf",
           "filename": "my-documentation",
           "destination": "https://example.com/exports/"
         }'
```
This request sends a POST request to the `/api/v1/content/export` endpoint on the domain `ghostwriter.example.com`, with the `Content-Type` header set to `application/json` and the `Authorization` header set to `Bearer <your_access_token>`. The request data includes the project_id, format, filename, and destination for the exported content.

## Sample Response

```json
{
  "status": "success",
  "message": "Content exported successfully.",
  "data": {
    "project_id": "12345",
    "format": "pdf",
    "filename": "my-documentation",
    "destination": "https://example.com/
```

## Error Response

```json
{
  "status": "error",
  "message": "Invalid format specified.",
  "errors": [
    {
      "parameter": "format",
      "message": "Accepted values are 'pdf', 'html', 'markdown'."
    }
  ]
}
```