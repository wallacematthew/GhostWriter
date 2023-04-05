---
layout: default
title: Customization
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

# Authentication API

The Authentication API manages the authentication and authorization of users and third-party applications, allowing secure access to the platform's features and data.

## Endpoint

```POST /api/v1/auth/token```


## Parameters

| Parameter    | Type   | Description                                                          | Required |
|--------------|--------|----------------------------------------------------------------------|----------|
| `grant_type` | string | The type of grant being requested. Accepted values: `password`.      | Yes      |
| `username`   | string | The user's email address or username.                                | Yes      |
| `password`   | string | The user's password.                                                 | Yes      |

## Sample Request

```
http
POST /api/v1/auth/token HTTP/1.1
Host: ghostwriter.example.com
Content-Type: application/x-www-form-urlencoded

grant_type=password&username=user@example.com&password=my_password
```

## Sample Response

```
HTTP/1.1 200 OK
Content-Type: application/json

{
  "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "token_type": "Bearer",
  "expires_in": 3600,
  "refresh_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "scope": "read write"
}
```

## Error Response

```
HTTP/1.1 400 Bad Request
Content-Type: application/json

{
  "error": "invalid_grant",
  "error_description": "Invalid username and password combination."
}
```

# GhostWriter API Rate Limiting

GhostWriter implements API rate limiting to ensure fair usage and maintain service stability for all users. Rate limiting controls the number of API requests a user or application can make within a specified time period. This article provides an overview of the rate limits in place for GhostWriter's API and guidance on handling rate-limited requests.

## Rate Limits

GhostWriter uses industry-standard rate limits, which are as follows:

- **Free tier users:** 60 requests per minute (RPM) and 1,000 requests per day (RPD)
- **Basic tier users:** 300 RPM and 10,000 RPD
- **Pro tier users:** 1,000 RPM and 50,000 RPD
- **Enterprise tier users:** Custom rate limits, depending on the agreement

Please note that these limits are subject to change, and it's always a good idea to check the latest documentation for updates.

## Handling Rate-Limited Requests

When a rate limit is exceeded, the API will respond with a `429 Too Many Requests` HTTP status code. The response headers will provide information about the rate limits and the time at which the limit will be reset.

### Rate Limit Headers

- `X-RateLimit-Limit`: The maximum number of requests allowed within the specified time window
- `X-RateLimit-Remaining`: The number of requests remaining in the current time window
- `X-RateLimit-Reset`: The time at which the rate limit will be reset, provided as a Unix timestamp

### Sample Rate-Limited Response

```http
HTTP/1.1 429 Too Many Requests
Content-Type: application/json
X-RateLimit-Limit: 60
X-RateLimit-Remaining: 0
X-RateLimit-Reset: 1620419320

{
  "status": "error",
  "message": "API rate limit exceeded. Please try again later."
}
```

## Best Practices for Handling Rate Limits

1. **Implement Retry Logic:** If your application receives a `429 Too Many Requests` response, implement retry logic with exponential backoff to avoid overwhelming the API further.
2. **Monitor Rate Limit Headers:** Monitor the `X-RateLimit-Remaining` and `X-RateLimit-Reset` headers in API responses to anticipate when the limit will be reached and adjust your request rate accordingly.
3. **Optimize API Usage:** Limit the number of API calls by optimizing your application's logic, batching requests, and using caching where appropriate.
4. **Upgrade Your Plan:** If your application consistently exceeds the rate limits, consider upgrading to a higher tier or reaching out to the GhostWriter team to discuss custom rate limits for your specific use case.

# GhostWriter API Errors and Troubleshooting

This article provides an overview of the industry-standard API errors used by GhostWriter and offers suggestions for troubleshooting these errors. Understanding the various error codes and their meaning can help you quickly identify and resolve issues when integrating with the GhostWriter API.

## Common API Errors

| HTTP Status Code | Error Code     | Description                                                                 |
|------------------|----------------|-----------------------------------------------------------------------------|
| 400              | Bad Request    | The request was malformed or invalid. Check the request parameters.         |
| 401              | Unauthorized   | The request requires authentication. Check your API access token.           |
| 403              | Forbidden      | The request is not allowed. Check your permissions or access token scope.   |
| 404              | Not Found      | The requested resource could not be found. Check the provided URL or ID.    |
| 405              | Method Not Allowed | The HTTP method used is not allowed for the specified endpoint.          |
| 429              | Too Many Requests | The request rate limit has been exceeded. See the rate limiting article.   |
| 500              | Internal Server Error | An error occurred on the server. Contact support if the issue persists. |

## Troubleshooting Suggestions

1. **Double-check the API request:** Ensure that the API request is formatted correctly, and all required parameters are included. Refer to the API documentation for specific endpoint requirements.

2. **Verify the API access token:** Make sure you are using a valid API access token and that it has the necessary permissions (scopes) for the requested operation.

3. **Check the requested resource:** Confirm that the resource you are trying to access exists and that the provided URL or ID is correct.

4. **Review your API usage:** If you are encountering rate limit errors, review the API rate limiting article for guidance on how to handle and avoid these issues.

5. **Examine the API response:** Analyze the API response for additional information about the error, such as specific parameters that may be causing the issue or a more detailed error message.

6. **Test with different parameters:** If possible, try different combinations of parameters to determine if a specific parameter is causing the error.

7. **Check for known issues:** Refer to the GhostWriter API documentation and any relevant release notes to see if there are any known issues or updates that may affect your integration.

8. **Contact support:** If you are unable to resolve the issue after following the above steps, reach out to GhostWriter support for further assistance.