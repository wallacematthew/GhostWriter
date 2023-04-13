---
layout: default
title: Troubleshooting
parent: APIs
nav_order: 4
---

# Errors and Troubleshooting
{: .no_toc }

This article provides an overview of the industry-standard API errors used by GhostWriter and offers suggestions for troubleshooting these errors. Understanding the various error codes and their meaning can help you quickly identify and resolve issues when integrating with the GhostWriter API.

## Table of contents
{: .no_toc }

- TOC
{:toc}

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