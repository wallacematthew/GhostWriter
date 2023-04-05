---
layout: default
title: Content Export API
parent: APIs
nav_order: 2
---

# Content Export API

The Content Export API allows you to export the generated content in various formats, such as PDF, HTML, or Markdown. It enables users to easily share and distribute their documentation across different channels and platforms.

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

```
http
POST /api/v1/content/export HTTP/1.1
Host: ghostwriter.example.com
Content-Type: application/json
Authorization: Bearer <your_access_token>

{
  "project_id": "12345",
  "format": "pdf",
  "filename": "my-documentation",
  "destination": "https://example.com/exports/"
}

HTTP/1.1 200 OK
Content-Type: application/json
```

## Sample Response

```
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

```
HTTP/1.1 400 Bad Request
Content-Type: application/json

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