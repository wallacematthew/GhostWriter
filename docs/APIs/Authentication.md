---
layout: default
title: Authentication API
parent: APIs
nav_order: 1
---

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
