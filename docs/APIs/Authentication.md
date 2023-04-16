---
layout: default
title: Authentication API
parent: APIs
nav_order: 1
---

# Authentication API
{: .no_toc }

The GhostWriter API requires authentication using an API key. You can obtain an API key by signing up for a GhostWriter account and navigating to your account settings.

## Authentication Endpoint

The authentication endpoint is used to obtain an access token, which must be included in subsequent API requests. The endpoint is:


## Table of contents
{: .no_toc }

- TOC
{:toc}

## Endpoint

GET `/api/v1/auth/token`

## Parameters

The following parameters must be included in the request:

| Parameter   | Description                                                      |
|-------------|------------------------------------------------------------------|
| `email`     | Your GhostWriter account email address.                          |
| `password`  | Your GhostWriter account password.                               |
| `grant_type`| The OAuth 2.0 grant type. For the GhostWriter API, this should always be set to "password". |
| `client_id` | Your GhostWriter API client ID.                                  |
| `client_secret` | Your GhostWriter API client secret.                           |

## Sample Requests

Here are some sample requests in cURL and popular programming languages:

### cURL

```zsh
curl --location --request POST 'https://api.ghostwriter.com/auth'
--header 'Content-Type: application/x-www-form-urlencoded'
--data-urlencode 'email=YOUR_EMAIL'
--data-urlencode 'password=YOUR_PASSWORD'
--data-urlencode 'grant_type=password'
--data-urlencode 'client_id=YOUR_CLIENT_ID'
--data-urlencode 'client_secret=YOUR_CLIENT_SECRET'
```
This request sends a POST request to the endpoint `/api/v1/auth/token` on the domain `ghostwriter.example.com`, with the Content-Type header set to `application/x-www-form-urlencoded`. The request data includes the grant type (password), the user's email address or username, and the user's password.

### Python

```python
import requests

url = "https://api.ghostwriter.com/auth"
payload = {
    "email": "YOUR_EMAIL",
    "password": "YOUR_PASSWORD",
    "grant_type": "password",
    "client_id": "YOUR_CLIENT_ID",
    "client_secret": "YOUR_CLIENT_SECRET"
}
headers = {
    "Content-Type": "application/x-www-form-urlencoded"
}

response = requests.post(url, headers=headers, data=payload)
print(response.json())
```

### JavaScript (Node.js)

```js
const https = require('https');
const querystring = require('querystring');

const data = querystring.stringify({
    "email": "YOUR_EMAIL",
    "password": "YOUR_PASSWORD",
    "grant_type": "password",
    "client_id": "YOUR_CLIENT_ID",
    "client_secret": "YOUR_CLIENT_SECRET"
});

const options = {
    hostname: 'api.ghostwriter.com',
    path: '/auth',
    method: 'POST',
    headers: {
        'Content-Type': 'application/x-www-form-urlencoded',
        'Content-Length': data.length
    }
};

const req = https.request(options, (res) => {
    let data = '';
    res.on('data', (chunk) => {
        data += chunk;
    });
    res.on('end', () => {
        console.log(JSON.parse(data));
    });
});

req.on('error', (error) => {
    console.error(error);
});

req.write(data);
req.end();
```

### Ruby

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.ghostwriter.com/auth")

https = Net::HTTP.new(url.host, url.port)
https.use_ssl = true

request = Net::HTTP::Post.new(url)
request['Content-Type'] = 'application/x-www-form-urlencoded'
request.body = "email=YOUR_EMAIL&password=YOUR_PASSWORD&grant_type=password&client_id=YOUR_CLIENT_ID&client_secret=YOUR_CLIENT_SECRET"

response = https.request(request)
puts response.read_body
```


## Sample Response
```json
{
    "access_token": "ACCESS_TOKEN",
    "token_type": "bearer",
    "expires_in": 3600,
    "refresh_token": "REFRESH_TOKEN",
    "scope": "read write"
}
```