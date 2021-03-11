---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - python
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true

code_clipboard: true
---

# Introduction

Welcome to the Elastic personas API! You can use our API to access Elastic personas API endpoints,

We have language bindings in Shell, Ruby, Python, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This example API documentation page was created with [Slate](https://github.com/slatedocs/slate). Feel free to edit it and use it as a base for your own API's documentation.

# Authentication

> Authentication is handled by  `JWT token`.

Elastic personas uses JWT token keys to allow access to the API.

Elastic personas expects for the JWT token to be included in all API requests to the server in a header that looks like the following:

`Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImp0aSI6IjVlOWRlOGVmNWJiNGVlM2U4MGE1ODI4M2ZiMTgyYmMyM2YyZWExZDc0M2Q2N2E5OTQ2NjNkMzMzMjZlNjQzMzdiY2ZhYzZjNmM0MWI2ODRhIn0.eyJhdWQiOiIxIiwianRpIjoiNWU5Z`

<aside class="notice">
You must login to get <code>Bearer token</code> to access for API.
</aside>

# Accounts

## Login

```ruby
require "uri"
require "net/http"

url = URI("https://app.elasticpersonas.ai/en/api/v1/accounts/login")

http = Net::HTTP.new(url.host, url.port);
request = Net::HTTP::Post.new(url)
request["Content-Type"] = "application/json"
request.body = "{\"account\": {\"email\": \"ajith@techversantinfo.com\", \"password\": \"ajithking\"}}"

response = http.request(request)
puts response.read_body
```

```python
import http.client

conn = http.client.HTTPSConnection("localhost", undefined)
payload = "{\"account\": {\"email\": \"ajith@techversantinfo.com\", \"password\": \"ajithking\"}}"
headers = {
  'Content-Type': 'application/json',
}
conn.request("POST", "/en/api/v1/accounts/login", payload, headers)
res = conn.getresponse()
data = res.read()
print(data.decode("utf-8"))
```

```shell
curl --location --request POST 'https://app.elasticpersonas.ai/en/api/v1/accounts/login' \
--header 'Content-Type: application/json' \
--data-raw '{"account": {"email": "ajith@techversantinfo.com", "password": "ajithking"}}'
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Content-Type", "application/json");

var raw = JSON.stringify({"account":{"email":"ajith@techversantinfo.com","password":"ajithking"}});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://app.elasticpersonas.ai/en/api/v1/accounts/login", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> The above command returns JSON structured like this:

```json
{
    "status": {
        "success": "Login sucessfully."
    }
}
```

This endpoint login the client and generate jwt token for Api access.

### HTTP Request

`POST https://app.elasticpersonas.ai/en/api/v1/accounts/login`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
email | - | client email.
password | - | client password


<aside class="success">
Remember — You can get the JWT token from the response header!
</aside>

## Update account

```ruby
require "uri"
require "net/http"

url = URI("https://app.elasticpersonas.ai/en/api/v1/accounts")

http = Net::HTTP.new(url.host, url.port);
request = Net::HTTP::Put.new(url)
request["Content-Type"] = "application/json"
request.body = "{\"account\": {\"your_name\": \"Ajithk\", \"email\": \"ajithbuddy.kumar@gmail.com\", \"current_password\": \"ajithking\"}}"

response = http.request(request)
puts response.read_body

```

```python
import http.client

conn = http.client.HTTPSConnection("localhost", undefined)
payload = "{\"account\": {\"your_name\": \"Ajithk\", \"email\": \"ajithbuddy.kumar@gmail.com\", \"current_password\": \"ajithking\"}}"
headers = {
  'Content-Type': 'application/json',
}
conn.request("PUT", "/en/api/v1/accounts", payload, headers)
res = conn.getresponse()
data = res.read()
print(data.decode("utf-8"))
```

```shell
curl --location --request PUT 'https://app.elasticpersonas.ai/en/api/v1/accounts' \
--header 'Content-Type: application/json' \
--data-raw '{"account": {"your_name": "Ajithk", "email": "ajithbuddy.kumar@gmail.com", "current_password": "ajithking"}}'
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Content-Type", "application/json");

var raw = JSON.stringify({"account":{"your_name":"Ajithk","email":"ajithbuddy.kumar@gmail.com","current_password":"ajithking"}});

var requestOptions = {
  method: 'PUT',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://app.elasticpersonas.ai/en/api/v1/accounts", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> The above command returns JSON structured like this:

```json
{
    "status": {
        "success": "Updated sucessfully."
    }
}
```

This endpoint Updates a account.

<!-- <aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside> -->

### HTTP Request

`PUT https://app.elasticpersonas.ai/en/api/v1/accounts`

### URL Parameters

Parameter | Description
--------- | -----------
your_name | User name
email     | User email
current_password | Password for authentication


# Dashboard

## List all surveys in dashboard

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.elasticpersonas.ai/en/api/v1/dashboard")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)
request["cache-control"] = 'no-cache'

response = http.request(request)
puts response.read_body
```

```python
import http.client

conn = http.client.HTTPConnection("https://app.elasticpersonas.ai")

headers = {
    'cache-control': "no-cache"
    }

conn.request("GET", "/en/api/v1/dashboard", headers=headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
curl --request GET \
  --url https://app.elasticpersonas.ai/en/api/v1/dashboard \
  --header 'cache-control: no-cache'
```

```javascript
var data = null;

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("GET", "https://app.elasticpersonas.ai/en/api/v1/dashboard");
xhr.setRequestHeader("cache-control", "no-cache");

xhr.send(data);
```

> The above command returns JSON structured like this:

```json
{
    "dashboard_surveys_count": 127,
    "surveys_count": 127,
    "active": 0,
    "draft": 33,
    "finished": 94,
    "surveys": [
        {
            "id": 347,
            "title": "Atom",
            "group": "new grops3",
            "group_id": 3,
            "group_image": "no-img-reports.png",
            "status": "Created",
            "created_at": "Mar 04, 2021"
        },
        {
            "id": 346,
            "title": "Atom",
            "group": "testing new group",
            "group_id": 18,
            "group_image": "no-img-reports.png",
            "status": "Created",
            "created_at": "Mar 04, 2021"
        },
        {
            "id": 345,
            "title": "Atom",
            "group": "testing new group",
            "group_id": 18,
            "group_image": "no-img-reports.png",
            "status": "Created",
            "created_at": "Mar 04, 2021"
        },
        {
            "id": 344,
            "title": "Atom",
            "group": "testing new group",
            "group_id": 18,
            "group_image": "no-img-reports.png",
            "status": "Created",
            "created_at": "Mar 04, 2021"
        },
        {
            "id": 343,
            "title": "Atom",
            "group": "testing new group",
            "group_id": 18,
            "group_image": "no-img-reports.png",
            "status": "Created",
            "created_at": "Mar 04, 2021"
        },
        {
            "id": 342,
            "title": "Atom",
            "group": "testing new group",
            "group_id": 18,
            "group_image": "no-img-reports.png",
            "status": "Created",
            "created_at": "Mar 04, 2021"
        },
        {
            "id": 341,
            "title": "Atom",
            "group": "new grops10",
            "group_id": 10,
            "group_image": "https://app.elasticpersonas.ai/rails/active_storage/blobs/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBDQT09IiwiZXhwIjpudWxsLCJwdXIiOiJibG9iX2lkIn19--999d136eedf75488dd260f4d031b674e9dbf88f7/output.png?locale=en",
            "status": "Created",
            "created_at": "Mar 03, 2021"
        },
        {
            "id": 340,
            "title": "Atom",
            "group": "new grops10",
            "group_id": 10,
            "group_image": "https://app.elasticpersonas.ai/rails/active_storage/blobs/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBDQT09IiwiZXhwIjpudWxsLCJwdXIiOiJibG9iX2lkIn19--999d136eedf75488dd260f4d031b674e9dbf88f7/output.png?locale=en",
            "status": "Created",
            "created_at": "Mar 03, 2021"
        },
        {
            "id": 339,
            "title": "Atom",
            "group": "new grops10",
            "group_id": 10,
            "group_image": "https://app.elasticpersonas.ai/rails/active_storage/blobs/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBDQT09IiwiZXhwIjpudWxsLCJwdXIiOiJibG9iX2lkIn19--999d136eedf75488dd260f4d031b674e9dbf88f7/output.png?locale=en",
            "recipients": 2,
            "respondents": 0,
            "status": "Finished"
        },
        {
            "id": 338,
            "title": "Atom",
            "group": "new grops10",
            "group_id": 10,
            "group_image": "https://app.elasticpersonas.ai/rails/active_storage/blobs/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBDQT09IiwiZXhwIjpudWxsLCJwdXIiOiJibG9iX2lkIn19--999d136eedf75488dd260f4d031b674e9dbf88f7/output.png?locale=en",
            "status": "Created",
            "created_at": "Mar 03, 2021"
        }
    ]
}
```

This endpoint List all surveys in dashboard.

<!-- <aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside> -->

### HTTP Request

`GET https://app.elasticpersonas.ai/en/api/v1/dashboard?page=3`

### URL Parameters

Not needed.

## List active surveys in dashboard

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.elasticpersonas.ai/en/api/v1/dashboard/active")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)
request["cache-control"] = 'no-cache'

response = http.request(request)
puts response.read_body
```

```python
import http.client

conn = http.client.HTTPConnection("https://app.elasticpersonas.ai")

headers = {
    'cache-control': "no-cache"
    }

conn.request("GET", "/en/api/v1/dashboard/active", headers=headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
curl --request GET \
  --url https://app.elasticpersonas.ai/en/api/v1/dashboard/active
```

```javascript
var data = null;

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("GET", "https://app.elasticpersonas.ai/en/api/v1/dashboard/active");
xhr.setRequestHeader("cache-control", "no-cache");

xhr.send(data);
```

> The above command returns JSON structured like this:

```json
{
    "dashboard_surveys_count": 127,
    "surveys_count": 127,
    "active": 0,
    "draft": 33,
    "finished": 94,
    "surveys": []
}
```

This endpoint List active surveys in dashboard.

### HTTP Request

`GET https://app.elasticpersonas.ai/en/api/v1/dashboard/active`

### URL Parameters

Not needed.

## List draft surveys in dashboard

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.elasticpersonas.ai/en/api/v1/dashboard/draft")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)
request["cache-control"] = 'no-cache'

response = http.request(request)
puts response.read_body
```

```python
import http.client

conn = http.client.HTTPConnection("https://app.elasticpersonas.ai")

headers = {
    'cache-control': "no-cache"
    }

conn.request("GET", "/en/api/v1/dashboard/draft", headers=headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
curl --request GET \
  --url https://app.elasticpersonas.ai/en/api/v1/dashboard/draft \
  --header 'cache-control: no-cache'
```

```javascript
var data = null;

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("GET", "https://app.elasticpersonas.ai/en/api/v1/dashboard/draft");
xhr.setRequestHeader("cache-control", "no-cache");

xhr.send(data);
```

> The above command returns JSON structured like this:

```json
{
    "dashboard_surveys_count": 127,
    "surveys_count": 127,
    "active": 0,
    "draft": 33,
    "finished": 94,
    "surveys": [
        {
            "id": 347,
            "title": "Atom",
            "group": "new grops3",
            "group_id": 3,
            "group_image": "no-img-reports.png",
            "status": "Created",
            "created_at": "Mar 04, 2021"
        },
        {
            "id": 346,
            "title": "Atom",
            "group": "testing new group",
            "group_id": 18,
            "group_image": "no-img-reports.png",
            "status": "Created",
            "created_at": "Mar 04, 2021"
        },
        {
            "id": 345,
            "title": "Atom",
            "group": "testing new group",
            "group_id": 18,
            "group_image": "no-img-reports.png",
            "status": "Created",
            "created_at": "Mar 04, 2021"
        },
        {
            "id": 344,
            "title": "Atom",
            "group": "testing new group",
            "group_id": 18,
            "group_image": "no-img-reports.png",
            "status": "Created",
            "created_at": "Mar 04, 2021"
        },
        {
            "id": 343,
            "title": "Atom",
            "group": "testing new group",
            "group_id": 18,
            "group_image": "no-img-reports.png",
            "status": "Created",
            "created_at": "Mar 04, 2021"
        },
        {
            "id": 342,
            "title": "Atom",
            "group": "testing new group",
            "group_id": 18,
            "group_image": "no-img-reports.png",
            "status": "Created",
            "created_at": "Mar 04, 2021"
        },
        {
            "id": 341,
            "title": "Atom",
            "group": "new grops10",
            "group_id": 10,
            "group_image": "https://app.elasticpersonas.ai/rails/active_storage/blobs/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBDQT09IiwiZXhwIjpudWxsLCJwdXIiOiJibG9iX2lkIn19--999d136eedf75488dd260f4d031b674e9dbf88f7/output.png?locale=en",
            "status": "Created",
            "created_at": "Mar 03, 2021"
        },
        {
            "id": 340,
            "title": "Atom",
            "group": "new grops10",
            "group_id": 10,
            "group_image": "https://app.elasticpersonas.ai/rails/active_storage/blobs/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBDQT09IiwiZXhwIjpudWxsLCJwdXIiOiJibG9iX2lkIn19--999d136eedf75488dd260f4d031b674e9dbf88f7/output.png?locale=en",
            "status": "Created",
            "created_at": "Mar 03, 2021"
        },
        {
            "id": 338,
            "title": "Atom",
            "group": "new grops10",
            "group_id": 10,
            "group_image": "https://app.elasticpersonas.ai/rails/active_storage/blobs/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBDQT09IiwiZXhwIjpudWxsLCJwdXIiOiJibG9iX2lkIn19--999d136eedf75488dd260f4d031b674e9dbf88f7/output.png?locale=en",
            "status": "Created",
            "created_at": "Mar 03, 2021"
        },
        {
            "id": 337,
            "title": "BMW INTERIOR",
            "group": "testing new group",
            "group_id": 18,
            "group_image": "no-img-reports.png",
            "status": "Created",
            "created_at": "Mar 02, 2021"
        }
    ]
}
```

This endpoint List draft surveys in dashboard.

### HTTP Request

`GET https://app.elasticpersonas.ai/en/api/v1/dashboard/draft`

### URL Parameters

Not needed.

## List finished surveys in dashboard

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.elasticpersonas.ai/en/api/v1/dashboard/finished")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)
request["cache-control"] = 'no-cache'

response = http.request(request)
puts response.read_body
```

```python
import http.client

conn = http.client.HTTPConnection("https://app.elasticpersonas.ai")

headers = {
    'cache-control': "no-cache"
    }

conn.request("GET", "/en/api/v1/dashboard/finished", headers=headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
curl --request GET \
  --url https://app.elasticpersonas.ai/en/api/v1/dashboard/finished \
  --header 'cache-control: no-cache'
```

```javascript
var data = null;

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("GET", "https://app.elasticpersonas.ai/en/api/v1/dashboard/finished");
xhr.setRequestHeader("cache-control", "no-cache");

xhr.send(data);
```

> The above command returns JSON structured like this:

```json
{
    "dashboard_surveys_count": 127,
    "surveys_count": 127,
    "active": 0,
    "draft": 33,
    "finished": 94,
    "surveys": [
        {
            "id": 339,
            "title": "Atom",
            "group": "new grops10",
            "group_id": 10,
            "group_image": "https://app.elasticpersonas.ai/rails/active_storage/blobs/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBDQT09IiwiZXhwIjpudWxsLCJwdXIiOiJibG9iX2lkIn19--999d136eedf75488dd260f4d031b674e9dbf88f7/output.png?locale=en",
            "recipients": 2,
            "respondents": 0,
            "status": "Finished"
        },
        {
            "id": 332,
            "title": "Atom",
            "group": "asdsdas",
            "group_id": 17,
            "group_image": "no-img-reports.png",
            "recipients": 1,
            "respondents": 0,
            "status": "Finished"
        },
        {
            "id": 331,
            "title": "BMW INTERIOR",
            "group": "testing new group",
            "group_id": 18,
            "group_image": "no-img-reports.png",
            "recipients": 0,
            "respondents": 0,
            "status": "Finished"
        },
        {
            "id": 330,
            "title": "Atom",
            "group": "new grops",
            "group_id": 13,
            "group_image": "no-img-reports.png",
            "recipients": 0,
            "respondents": 0,
            "status": "Finished"
        },
        {
            "id": 329,
            "title": "Survey with template 2 (2) (1)",
            "group": "new gropss",
            "group_id": 1,
            "group_image": "no-img-reports.png",
            "recipients": 1,
            "respondents": 0,
            "status": "Finished"
        },
        {
            "id": 328,
            "title": "Survey with template 2 (2)",
            "group": "new gropss",
            "group_id": 1,
            "group_image": "no-img-reports.png",
            "recipients": 1,
            "respondents": 0,
            "status": "Finished"
        },
        {
            "id": 327,
            "title": "other multiple check (2) (2)",
            "group": "new grops",
            "group_id": 13,
            "group_image": "no-img-reports.png",
            "recipients": 0,
            "respondents": 0,
            "status": "Finished"
        },
        {
            "id": 325,
            "title": "Survey with template 2 (1)",
            "group": "new gropss",
            "group_id": 1,
            "group_image": "no-img-reports.png",
            "recipients": 0,
            "respondents": 0,
            "status": "Finished"
        },
        {
            "id": 323,
            "title": "BMW INTERIOR (2) (1) (1)",
            "group": "new gropsddd",
            "group_id": 16,
            "group_image": "no-img-reports.png",
            "recipients": 1,
            "respondents": 1,
            "status": "Finished"
        },
        {
            "id": 321,
            "title": "BMW INTERIOR (2)",
            "group": "new gropsddd",
            "group_id": 16,
            "group_image": "no-img-reports.png",
            "recipients": 2,
            "respondents": 2,
            "status": "Finished"
        }
    ]
}
```

This endpoint List finished surveys in dashboard.

### HTTP Request

`GET https://app.elasticpersonas.ai/en/api/v1/dashboard/finished`

### URL Parameters

Not needed.

<!-- ## Delete a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2" \
  -X DELETE \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

 -->