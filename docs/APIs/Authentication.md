---
layout: default
title: Authentication API
parent: APIs
nav_order: 1
---

# Authentication API
{: .no_toc }

The Authentication API manages the authentication and authorization of users and third-party applications, allowing secure access to the platform's features and data.

## Table of contents
{: .no_toc }

- TOC
{:toc}

## Endpoint

```POST /api/v1/auth/token```


## Parameters

| Parameter    | Type   | Description                                                          | Required |
|--------------|--------|----------------------------------------------------------------------|----------|
| `grant_type` | string | The type of grant being requested. Accepted values: `password`.      | Yes      |
| `username`   | string | The user's email address or username.                                | Yes      |
| `password`   | string | The user's password.                                                 | Yes      |

## Sample Request

```bash
curl -X POST "https://ghostwriter.example.com/api/v1/auth/token" \
     -H "Content-Type: application/x-www-form-urlencoded" \
     -d "grant_type=password&username=user@example.com&password=my_password"
```
This request sends a POST request to the endpoint `/api/v1/auth/token` on the domain `ghostwriter.example.com`, with the Content-Type header set to `application/x-www-form-urlencoded`. The request data includes the grant type (password), the user's email address or username, and the user's password.

## Sample Response

```json
{
  "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "token_type": "Bearer",
  "expires_in": 3600,
  "refresh_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "scope": "read write"
}
```

## Error Response

```json
{
  "error": "invalid_grant",
  "error_description": "Invalid username and password combination."
}
```
