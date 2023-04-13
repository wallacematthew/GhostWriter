---
layout: default
title: Rate Limits
parent: APIs
nav_order: 3
---

# Rate Limits
{: .no_toc }

GhostWriter implements API rate limiting to ensure fair usage and maintain service stability for all users. Rate limiting controls the number of API requests a user or application can make within a specified time period. This article provides an overview of the rate limits in place for GhostWriter's API and guidance on handling rate-limited requests.

## Table of contents
{: .no_toc }

- TOC
{:toc}

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