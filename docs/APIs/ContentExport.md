---
layout: default
title: Content Generation API
parent: APIs
nav_order: 2
---

# Content Export API
{: .no_toc }

GhostWriter's content generation API allows developers to programmatically generate a variety of help and support content, such as release notes, executive summaries, how-to guides, overviews, tutorials, and get started guides. The API provides a flexible and powerful way to generate high-quality content that meets your specific needs. In this guide, we'll walk through the various parameters that can be used with the GhostWriter content generation API.

## Table of contents
{: .no_toc }

- TOC
{:toc}

## API Endpoints
The GhostWriter content generation API has the following endpoints:

GET `/api/v1/content`: generates content based on the specified parameters.

## Parameters

| Parameter     | Description                                                                                                 |
|---------------|-------------------------------------------------------------------------------------------------------------|
| `article_type` | Specifies the type of article to generate. Possible values include "release_note", "executive_summary", "how_to_guide", "overview", "tutorial", "get_started_guide", and more. |
| `length`       | Specifies the desired length of the generated content in words or characters.                             |
| `topic`        | Specifies the topic or subject matter of the generated content.                                            |
| `style`        | Specifies the style or tone of the generated content, such as formal, informal, technical, or humorous.  |
| `language`     | Specifies the language of the generated content, such as English, Spanish, or French.                     |
| `format`       | Specifies the format of the generated content, such as HTML, Markdown, or plain text.                     |
| `template`     | Specifies a pre-built template to use for the generated content, such as a blog post template, email template, or landing page template. |
| `data_source`  | Specifies the data sources to use when generating the content, such as Jira tickets, pull requests, product specs, and more. |
| `audience`     | Specifies the target audience for the generated content, such as developers, end-users, or executives.   |


## Sample Requests and Response

Here's a sample request (in cURL) to generate a release note with a length of 500 words, a formal style, and data sources from Jira tickets and product specs:

### cURL
```zsh
curl --location --request GET 'https://api.ghostwriter.com/content?article_type=release_note&length=500&style=formal&data_source=jira_tickets,product_specs' \
--header 'Authorization: Bearer API_KEY'
```
### Python
```python
import requests

url = "https://api.ghostwriter.com/content"
querystring = {
    "article_type": "release_note",
    "length": "500",
    "style": "formal",
    "data_source": "jira_tickets,product_specs"
}
headers = {
    "Authorization": "Bearer API_KEY"
}

response = requests.request("GET", url, headers=headers, params=querystring)
print(response.json())
```

### JavaScript (Node.js)
```js
const https = require('https');
const options = {
    hostname: 'api.ghostwriter.com',
    path: '/content?article_type=release_note&length=500&style=formal&data_source=jira_tickets,product_specs',
    headers: {
        'Authorization': 'Bearer API_KEY'
    }
};

https.get(options, (res) => {
    let data = '';
    res.on('data', (chunk) => {
        data += chunk;
    });
    res.on('end', () => {
        console.log(JSON.parse(data));
    });
}).on('error', (err) => {
    console.log(err);
});
```

### Ruby
```ruby
require 'uri'
require 'net/http'
require 'openssl'

url = URI("https://api.ghostwriter.com/content?article_type=release_note&length=500&style=formal&data_source=jira_tickets,product_specs")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Get.new(url)
request["Authorization"] = 'Bearer API_KEY'

response = http.request(request)
puts response.read_body
```

## Sample Response

And here's a sample response (in JSON) for the above requests:

```json
{
   "title": "Release Notes: Version 1.2.3",
   "content": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Praesent non feugiat turpis, eget elementum nibh. Vestibulum auctor nibh eget luctus scelerisque. Nunc congue lacus in turpis luctus malesuada. Quisque convallis vehicula metus, eu fringilla mauris pretium at. Duis auctor turpis vitae diam rhoncus pretium. Integer condimentum ultricies nisl. Vestibulum vel interdum odio. Sed sit amet faucibus velit. Nullam mattis urna vel ullamcorper malesuada."
}
```
