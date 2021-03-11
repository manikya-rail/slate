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

`GET https://app.elasticpersonas.ai/en/api/v1/dashboard`

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


# Surveys

## Generate PDF of Respondents

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.elasticpersonas.ai/en/api/v1/reports/16/surveys/323/export_pdf?submission_ids=198")

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

conn.request("GET", "/en/api/v1/reports/16/surveys/323/export_pdf?submission_ids=198", headers=headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
curl --request GET \
  --url 'https://app.elasticpersonas.ai/en/api/v1/reports/16/surveys/323/export_pdf?submission_ids=198' \
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

xhr.open("GET", "https://app.elasticpersonas.ai/en/api/v1/reports/16/surveys/323/export_pdf?submission_ids=198");
xhr.setRequestHeader("cache-control", "no-cache");

xhr.send(data);
```

> The above command returns PDF file.

This endpoint Generate PDF of Respondents.

### HTTP Request

`GET https://app.elasticpersonas.ai/en/api/v1/reports/16/surveys/323/export_pdf?submission_ids=198`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the survey
report_id | The ID of the report
submission_ids | The submission ids of the survey

## Generate PDF of General

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.elasticpersonas.ai/en/api/v1/reports/16/surveys/323/export_summary_pdf")

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

conn.request("GET", "/en/api/v1/reports/16/surveys/323/export_summary_pdf", headers=headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
curl --request GET \
  --url https://app.elasticpersonas.ai/en/api/v1/reports/16/surveys/323/export_summary_pdf \
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

xhr.open("GET", "https://app.elasticpersonas.ai/en/api/v1/reports/16/surveys/323/export_summary_pdf");
xhr.setRequestHeader("cache-control", "no-cache");

xhr.send(data);
```

> The above command returns PDF file.

This endpoint Generate PDF of General.

<!-- <aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside> -->

### HTTP Request

`GET https://app.elasticpersonas.ai/en/api/v1/reports/16/surveys/323/export_summary_pdf`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the survey
report_id | The ID of the report

## Shows Template in Create Survey

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.elasticpersonas.ai/en/api/v1/groups/choose_template")

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

conn.request("GET", "/en/api/v1/groups/choose_template", headers=headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
curl --request GET \
  --url https://app.elasticpersonas.ai/en/api/v1/groups/choose_template \
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

xhr.open("GET", "https://app.elasticpersonas.ai/en/api/v1/groups/choose_template");
xhr.setRequestHeader("cache-control", "no-cache");

xhr.send(data);
```

> The above command returns JSON structured like this:

```json
{
    "themes": {
        "industries": [
            {
                "id": 1,
                "title": "abc industry",
                "t_count": 2,
                "description": "company lmited",
                "survey_themes": [
                    {
                        "id": 1,
                        "title": "Atom"
                    },
                    {
                        "id": 2,
                        "title": "BMW INTERIOR"
                    }
                ]
            },
            {
                "id": 3,
                "title": "Accounting\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 4,
                "title": "Airlines/Aviation\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 5,
                "title": "Alternative Dispute Resolution\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 6,
                "title": "Alternative Medicine\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 7,
                "title": "Animation\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 8,
                "title": "Apparel & Fashion\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 2,
                "title": "Architecture",
                "t_count": 0,
                "description": "arch",
                "survey_themes": []
            },
            {
                "id": 9,
                "title": "Architecture & Planning\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 10,
                "title": "Arts & Crafts\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 11,
                "title": "Automotive\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 12,
                "title": "Aviation & Aerospace\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 13,
                "title": "Banking\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 14,
                "title": "Biotechnology\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 15,
                "title": "Broadcast Media\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 16,
                "title": "Building Materials\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 17,
                "title": "Business Supplies & Equipment\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 18,
                "title": "Capital Markets\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 19,
                "title": "Chemicals\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 20,
                "title": "Civic & Social Organization\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 21,
                "title": "Civil Engineering\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 22,
                "title": "Commercial Real Estate\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 24,
                "title": "Computer Games\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 25,
                "title": "Computer Hardware\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 26,
                "title": "Computer Networking\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 23,
                "title": "Computer & Network Security\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 27,
                "title": "Computer Software\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 28,
                "title": "Construction\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 29,
                "title": "Consumer Electronics\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 30,
                "title": "Consumer Goods\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 31,
                "title": "Consumer Services\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 32,
                "title": "Cosmetics\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 33,
                "title": "Dairy\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 34,
                "title": "Defense & Space\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 35,
                "title": "Design\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 36,
                "title": "Education Management\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 37,
                "title": "E-learning\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 38,
                "title": "Electrical & Electronic Manufacturing\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 39,
                "title": "Entertainment\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 40,
                "title": "Environmental Services\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 41,
                "title": "Events Services\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 42,
                "title": "Executive Office\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 124,
                "title": "Facilities & Services\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 43,
                "title": "Facilities Services\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 44,
                "title": "Farming\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 45,
                "title": "Financial Services\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 46,
                "title": "Fine Art\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 47,
                "title": "Fishery\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 48,
                "title": "Food & Beverages\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 49,
                "title": "Food Production\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 50,
                "title": "Fundraising\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 51,
                "title": "Furniture\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 52,
                "title": "Gambling & Casinos\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 53,
                "title": "Glass, Ceramics & Concrete\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 54,
                "title": "Government Administration\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 55,
                "title": "Government Relations\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 56,
                "title": "Graphic Design\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 57,
                "title": "Health, Wellness & Fitness\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 58,
                "title": "Higher Education\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 59,
                "title": "Hospital & Health Care\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 60,
                "title": "Hospitality\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 61,
                "title": "Human Resources\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 62,
                "title": "Import & Export\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 63,
                "title": "Individual & Family Services\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 64,
                "title": "Industrial Automation\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 65,
                "title": "Information Services\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 66,
                "title": "Information Technology & Services\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 67,
                "title": "Insurance\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 68,
                "title": "International Affairs\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 69,
                "title": "International Trade & Development\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 70,
                "title": "Internet\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 71,
                "title": "Investment Banking/Venture\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 72,
                "title": "Investment Management\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 73,
                "title": "Judiciary\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 74,
                "title": "Law Enforcement\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 75,
                "title": "Law Practice\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 76,
                "title": "Legal Services\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 77,
                "title": "Legislative Office\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 78,
                "title": "Leisure & Travel\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 79,
                "title": "Libraries\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 80,
                "title": "Logistics & Supply Chain\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 81,
                "title": "Luxury Goods & Jewelry\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 82,
                "title": "Machinery\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 83,
                "title": "Management Consulting\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 84,
                "title": "Maritime\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 85,
                "title": "Marketing & Advertising\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 86,
                "title": "Market Research\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 87,
                "title": "Mechanical or Industrial Engineering\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 88,
                "title": "Media Production\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 89,
                "title": "Medical Device\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 90,
                "title": "Medical Practice\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 91,
                "title": "Mental Health Care\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 92,
                "title": "Military\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 93,
                "title": "Mining & Metals\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 94,
                "title": "Motion Pictures & Film\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 95,
                "title": "Museums & Institutions\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 96,
                "title": "Music\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 97,
                "title": "Nanotechnology\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 98,
                "title": "Newspapers\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 99,
                "title": "Nonprofit Organization Management\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 100,
                "title": "Oil & Energy\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 101,
                "title": "Online Publishing\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 102,
                "title": "Outsourcing/Offshoring\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 103,
                "title": "Package/Freight Delivery\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 104,
                "title": "Packaging & Containers\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 105,
                "title": "Paper & Forest Products\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 106,
                "title": "Performing Arts\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 107,
                "title": "Pharmaceuticals\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 108,
                "title": "Philanthropy\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 109,
                "title": "Photography\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 110,
                "title": "Plastics\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 111,
                "title": "Political Organization\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 112,
                "title": "Primary/Secondary Education\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 113,
                "title": "Printing\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 114,
                "title": "Professional Training\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 115,
                "title": "Program Development\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 116,
                "title": "Public Policy\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 117,
                "title": "Public Relations\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 118,
                "title": "Public Safety\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 119,
                "title": "Publishing\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 120,
                "title": "Railroad Manufacture\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 121,
                "title": "Ranching\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 122,
                "title": "Real Estate\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 123,
                "title": "Recreational\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 125,
                "title": "Religious Institutions\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 126,
                "title": "Renewables & Environment\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 127,
                "title": "Research\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 128,
                "title": "Restaurants\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 129,
                "title": "Retail\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 130,
                "title": "Security & Investigations\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 131,
                "title": "Semiconductors\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 132,
                "title": "Shipbuilding\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 133,
                "title": "Sporting Goods\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 134,
                "title": "Sports\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 135,
                "title": "Staffing & Recruiting\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 136,
                "title": "Supermarkets\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 137,
                "title": "Telecommunications\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 138,
                "title": "Textiles\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 139,
                "title": "Think Tanks\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 140,
                "title": "Tobacco\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 141,
                "title": "Translation & Localization\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 142,
                "title": "Transportation/Trucking/Railroad\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 143,
                "title": "Utilities\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 144,
                "title": "Venture Capital\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 145,
                "title": "Veterinary\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 146,
                "title": "Warehousing\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 147,
                "title": "Wholesale\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 148,
                "title": "Wine & Spirits\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 149,
                "title": "Wireless\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 150,
                "title": "Writing & Editing",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            }
        ]
    },
    "my_templates": {
        "industries": [
            {
                "id": 1,
                "title": "abc industry",
                "t_count": 9,
                "description": "company lmited",
                "survey_themes": [
                    {
                        "id": 7,
                        "title": "New cech"
                    },
                    {
                        "id": 4,
                        "title": "New IMage"
                    },
                    {
                        "id": 6,
                        "title": "New IMagesss"
                    },
                    {
                        "id": 13,
                        "title": "New Indus check template"
                    },
                    {
                        "id": 5,
                        "title": "New teplate"
                    },
                    {
                        "id": 14,
                        "title": "new test for template"
                    },
                    {
                        "id": 10,
                        "title": "newtesting"
                    },
                    {
                        "id": 9,
                        "title": "newtezt"
                    },
                    {
                        "id": 8,
                        "title": "Newwwwwwwq"
                    }
                ]
            },
            {
                "id": 2,
                "title": "Architecture",
                "t_count": 2,
                "description": "arch",
                "survey_themes": [
                    {
                        "id": 13,
                        "title": "New Indus check template"
                    },
                    {
                        "id": 15,
                        "title": "newtestingss"
                    }
                ]
            },
            {
                "id": 3,
                "title": "Accounting\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 4,
                "title": "Airlines/Aviation\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 5,
                "title": "Alternative Dispute Resolution\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 6,
                "title": "Alternative Medicine\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 7,
                "title": "Animation\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 8,
                "title": "Apparel & Fashion\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 9,
                "title": "Architecture & Planning\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 10,
                "title": "Arts & Crafts\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 11,
                "title": "Automotive\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 12,
                "title": "Aviation & Aerospace\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 13,
                "title": "Banking\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 14,
                "title": "Biotechnology\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 15,
                "title": "Broadcast Media\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 16,
                "title": "Building Materials\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 17,
                "title": "Business Supplies & Equipment\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 18,
                "title": "Capital Markets\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 19,
                "title": "Chemicals\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 20,
                "title": "Civic & Social Organization\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 21,
                "title": "Civil Engineering\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 22,
                "title": "Commercial Real Estate\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 24,
                "title": "Computer Games\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 25,
                "title": "Computer Hardware\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 26,
                "title": "Computer Networking\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 23,
                "title": "Computer & Network Security\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 27,
                "title": "Computer Software\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 28,
                "title": "Construction\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 29,
                "title": "Consumer Electronics\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 30,
                "title": "Consumer Goods\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 31,
                "title": "Consumer Services\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 32,
                "title": "Cosmetics\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 33,
                "title": "Dairy\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 34,
                "title": "Defense & Space\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 35,
                "title": "Design\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 36,
                "title": "Education Management\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 37,
                "title": "E-learning\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 38,
                "title": "Electrical & Electronic Manufacturing\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 39,
                "title": "Entertainment\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 40,
                "title": "Environmental Services\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 41,
                "title": "Events Services\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 42,
                "title": "Executive Office\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 124,
                "title": "Facilities & Services\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 43,
                "title": "Facilities Services\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 44,
                "title": "Farming\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 45,
                "title": "Financial Services\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 46,
                "title": "Fine Art\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 47,
                "title": "Fishery\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 48,
                "title": "Food & Beverages\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 49,
                "title": "Food Production\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 50,
                "title": "Fundraising\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 51,
                "title": "Furniture\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 52,
                "title": "Gambling & Casinos\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 53,
                "title": "Glass, Ceramics & Concrete\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 54,
                "title": "Government Administration\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 55,
                "title": "Government Relations\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 56,
                "title": "Graphic Design\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 57,
                "title": "Health, Wellness & Fitness\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 58,
                "title": "Higher Education\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 59,
                "title": "Hospital & Health Care\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 60,
                "title": "Hospitality\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 61,
                "title": "Human Resources\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 62,
                "title": "Import & Export\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 63,
                "title": "Individual & Family Services\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 64,
                "title": "Industrial Automation\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 65,
                "title": "Information Services\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 66,
                "title": "Information Technology & Services\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 67,
                "title": "Insurance\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 68,
                "title": "International Affairs\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 69,
                "title": "International Trade & Development\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 70,
                "title": "Internet\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 71,
                "title": "Investment Banking/Venture\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 72,
                "title": "Investment Management\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 73,
                "title": "Judiciary\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 74,
                "title": "Law Enforcement\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 75,
                "title": "Law Practice\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 76,
                "title": "Legal Services\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 77,
                "title": "Legislative Office\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 78,
                "title": "Leisure & Travel\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 79,
                "title": "Libraries\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 80,
                "title": "Logistics & Supply Chain\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 81,
                "title": "Luxury Goods & Jewelry\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 82,
                "title": "Machinery\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 83,
                "title": "Management Consulting\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 84,
                "title": "Maritime\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 85,
                "title": "Marketing & Advertising\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 86,
                "title": "Market Research\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 87,
                "title": "Mechanical or Industrial Engineering\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 88,
                "title": "Media Production\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 89,
                "title": "Medical Device\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 90,
                "title": "Medical Practice\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 91,
                "title": "Mental Health Care\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 92,
                "title": "Military\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 93,
                "title": "Mining & Metals\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 94,
                "title": "Motion Pictures & Film\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 95,
                "title": "Museums & Institutions\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 96,
                "title": "Music\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 97,
                "title": "Nanotechnology\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 98,
                "title": "Newspapers\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 99,
                "title": "Nonprofit Organization Management\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 100,
                "title": "Oil & Energy\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 101,
                "title": "Online Publishing\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 102,
                "title": "Outsourcing/Offshoring\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 103,
                "title": "Package/Freight Delivery\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 104,
                "title": "Packaging & Containers\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 105,
                "title": "Paper & Forest Products\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 106,
                "title": "Performing Arts\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 107,
                "title": "Pharmaceuticals\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 108,
                "title": "Philanthropy\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 109,
                "title": "Photography\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 110,
                "title": "Plastics\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 111,
                "title": "Political Organization\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 112,
                "title": "Primary/Secondary Education\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 113,
                "title": "Printing\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 114,
                "title": "Professional Training\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 115,
                "title": "Program Development\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 116,
                "title": "Public Policy\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 117,
                "title": "Public Relations\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 118,
                "title": "Public Safety\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 119,
                "title": "Publishing\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 120,
                "title": "Railroad Manufacture\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 121,
                "title": "Ranching\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 122,
                "title": "Real Estate\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 123,
                "title": "Recreational\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 125,
                "title": "Religious Institutions\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 126,
                "title": "Renewables & Environment\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 127,
                "title": "Research\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 128,
                "title": "Restaurants\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 129,
                "title": "Retail\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 130,
                "title": "Security & Investigations\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 131,
                "title": "Semiconductors\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 132,
                "title": "Shipbuilding\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 133,
                "title": "Sporting Goods\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 134,
                "title": "Sports\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 135,
                "title": "Staffing & Recruiting\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 136,
                "title": "Supermarkets\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 137,
                "title": "Telecommunications\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 138,
                "title": "Textiles\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 139,
                "title": "Think Tanks\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 140,
                "title": "Tobacco\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 141,
                "title": "Translation & Localization\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 142,
                "title": "Transportation/Trucking/Railroad\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 143,
                "title": "Utilities\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 144,
                "title": "Venture Capital\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 145,
                "title": "Veterinary\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 146,
                "title": "Warehousing\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 147,
                "title": "Wholesale\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 148,
                "title": "Wine & Spirits\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 149,
                "title": "Wireless\n",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            },
            {
                "id": 150,
                "title": "Writing & Editing",
                "t_count": 0,
                "description": null,
                "survey_themes": []
            }
        ]
    }
}
```

This endpoint Shows Template in Create Survey.

### HTTP Request

`GET https://app.elasticpersonas.ai/en/api/v1/groups/choose_template`

### URL Parameters

Not needed.

## Shows Themes in Create Survey

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.elasticpersonas.ai/en/api/v1/groups/industry_themes?id=1&type=account")

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

conn.request("GET", "/en/api/v1/groups/industry_themes?id=1&type=account", headers=headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
curl --request GET \
  --url 'https://app.elasticpersonas.ai/en/api/v1/groups/industry_themes?id=1&type=account' \
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

xhr.open("GET", "https://app.elasticpersonas.ai/en/api/v1/groups/industry_themes?id=1&type=account");
xhr.setRequestHeader("cache-control", "no-cache");

xhr.send(data);
```

> The above command returns JSON structured like this:

```json
{
    "survey_themes": [
        {
            "id": 7,
            "title": "New cech"
        },
        {
            "id": 4,
            "title": "New IMage"
        },
        {
            "id": 6,
            "title": "New IMagesss"
        },
        {
            "id": 13,
            "title": "New Indus check template"
        },
        {
            "id": 5,
            "title": "New teplate"
        },
        {
            "id": 14,
            "title": "new test for template"
        },
        {
            "id": 10,
            "title": "newtesting"
        },
        {
            "id": 9,
            "title": "newtezt"
        },
        {
            "id": 8,
            "title": "Newwwwwwwq"
        }
    ]
}
```

This endpoint Shows Themes in Create Survey.

### HTTP Request

`GET https://app.elasticpersonas.ai/en/api/v1/groups/industry_themes?id=1&type=account`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the industry
type | Type of the theme

## Duplicate a Question in a Block

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.elasticpersonas.ai/en/api/v1/surveys/346/categories_surveys/duplicate_question?question_id=9540")

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

conn.request("GET", "/en/api/v1/surveys/346/categories_surveys/duplicate_question?question_id=9540", headers=headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
curl --request GET \
  --url 'https://app.elasticpersonas.ai/en/api/v1/surveys/346/categories_surveys/duplicate_question?question_id=9540' \
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

xhr.open("GET", "https://app.elasticpersonas.ai/en/api/v1/surveys/346/categories_surveys/duplicate_question?question_id=9540");
xhr.setRequestHeader("cache-control", "no-cache");

xhr.send(data);
```

> The above command returns JSON structured like this:

```json
{
    "success": "Item was duplicated successfully."
}
```

This endpoint Duplicate a Question in a Block.

### HTTP Request

`GET https://app.elasticpersonas.ai/en/api/v1/surveys/346/categories_surveys/duplicate_question?question_id=9540`

### URL Parameters

Parameter | Description
--------- | -----------
survey_id | The ID of the survey
question_id | The ID of the question

# Reports

## View list of Reports

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.elasticpersonas.ai/en/api/v1/reports")

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

conn.request("GET", "/en/api/v1/reports", headers=headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
curl --request GET \
  --url https://app.elasticpersonas.ai/en/api/v1/reports \
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

xhr.open("GET", "https://app.elasticpersonas.ai/en/api/v1/reports");
xhr.setRequestHeader("cache-control", "no-cache");

xhr.send(data);
```

> The above command returns JSON structured like this:

```json
{
    "groups": [
        {
            "id": 18,
            "title": "testing new group",
            "creator_name": "Ajith",
            "created_at": "Nov 19, 2020",
            "created_by_id": 3,
            "archived": false,
            "custom_personas_count": 0,
            "reports_count": 1
        },
        {
            "id": 17,
            "title": "asdsdas",
            "creator_name": "Ajith",
            "created_at": "Oct 21, 2020",
            "created_by_id": 3,
            "archived": false,
            "custom_personas_count": 0,
            "reports_count": 1
        },
        {
            "id": 16,
            "title": "new gropsddd",
            "creator_name": "Ajith",
            "created_at": "Oct 14, 2020",
            "created_by_id": 3,
            "archived": false,
            "custom_personas_count": 0,
            "reports_count": 3
        },
        {
            "id": 13,
            "title": "new grops",
            "creator_name": "Ajith",
            "created_at": "Aug 26, 2020",
            "created_by_id": 3,
            "archived": false,
            "custom_personas_count": 20,
            "reports_count": 13
        },
        {
            "id": 10,
            "title": "new grops10",
            "creator_name": "Ajith",
            "created_at": "Jul 27, 2020",
            "created_by_id": 3,
            "archived": false,
            "custom_personas_count": 0,
            "reports_count": 5,
            "image_url": "https://app.elasticpersonas.ai/rails/active_storage/blobs/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBDQT09IiwiZXhwIjpudWxsLCJwdXIiOiJibG9iX2lkIn19--999d136eedf75488dd260f4d031b674e9dbf88f7/output.png?locale=en"
        },
        {
            "id": 9,
            "title": "new grops9",
            "creator_name": "Ajith",
            "created_at": "Jul 27, 2020",
            "created_by_id": 3,
            "archived": false,
            "custom_personas_count": 0,
            "reports_count": 2,
            "image_url": "https://app.elasticpersonas.ai/rails/active_storage/blobs/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBkUT09IiwiZXhwIjpudWxsLCJwdXIiOiJibG9iX2lkIn19--05e42a8ee3fa9cc01acffae046503395254234d8/output.png?locale=en"
        },
        {
            "id": 2,
            "title": "new grops22",
            "creator_name": "Ajith",
            "created_at": "Jul 23, 2020",
            "created_by_id": 3,
            "archived": false,
            "custom_personas_count": 3,
            "reports_count": 2
        },
        {
            "id": 1,
            "title": "new gropss",
            "creator_name": "Ajith",
            "created_at": "Mar 30, 2020",
            "created_by_id": 3,
            "archived": false,
            "custom_personas_count": 47,
            "reports_count": 67
        }
    ]
}
```

This endpoint View list of Reports.

### HTTP Request

`GET https://app.elasticpersonas.ai/en/api/v1/reports`

### URL Parameters

Not needed.

## List all surveys in Reports

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.elasticpersonas.ai/en/api/v1/reports/1/surveys/all")

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

conn.request("GET", "/en/api/v1/reports/1/surveys/all", headers=headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
curl --request GET \
  --url https://app.elasticpersonas.ai/en/api/v1/reports/1/surveys/all \
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

xhr.open("GET", "https://app.elasticpersonas.ai/en/api/v1/reports/1/surveys/all");
xhr.setRequestHeader("cache-control", "no-cache");

xhr.send(data);
```

> The above command returns JSON structured like this:

```json
{
    "surveys_count": 67,
    "active": 0,
    "draft": 0,
    "finished": 67,
    "surveys": [
        {
            "id": 329,
            "title": "Survey with template 2 (2) (1)",
            "customized_personas_count": 0,
            "recipients": 1,
            "respondents": 0,
            "status": "Finished",
            "created_at": "Dec 14, 2020"
        },
        {
            "id": 328,
            "title": "Survey with template 2 (2)",
            "customized_personas_count": 0,
            "recipients": 1,
            "respondents": 0,
            "status": "Finished",
            "created_at": "Dec 14, 2020"
        },
        {
            "id": 325,
            "title": "Survey with template 2 (1)",
            "customized_personas_count": 0,
            "recipients": 0,
            "respondents": 0,
            "status": "Finished",
            "created_at": "Dec 07, 2020"
        },
        {
            "id": 311,
            "title": "Survey with template 2",
            "customized_personas_count": 2,
            "recipients": 8,
            "respondents": 5,
            "status": "Finished",
            "created_at": "Oct 13, 2020"
        },
        {
            "id": 310,
            "title": "Survey with template 1",
            "customized_personas_count": 0,
            "recipients": 3,
            "respondents": 2,
            "status": "Finished",
            "created_at": "Oct 13, 2020"
        },
        {
            "id": 292,
            "title": "Survey template 1",
            "customized_personas_count": 0,
            "recipients": 1,
            "respondents": 1,
            "status": "Finished",
            "created_at": "Oct 04, 2020"
        },
        {
            "id": 283,
            "title": "BMW INTERIOR",
            "customized_personas_count": 0,
            "recipients": 0,
            "respondents": 0,
            "status": "Finished",
            "created_at": "Sep 16, 2020"
        },
        {
            "id": 274,
            "title": "BMW INTERIOR",
            "customized_personas_count": 0,
            "recipients": 0,
            "respondents": 0,
            "status": "Finished",
            "created_at": "Aug 25, 2020"
        },
        {
            "id": 273,
            "title": "BMW INTERIOR (52) (1) (1) (1) (1) (1)",
            "customized_personas_count": 0,
            "recipients": 1,
            "respondents": 1,
            "status": "Finished",
            "created_at": "Aug 25, 2020"
        },
        {
            "id": 272,
            "title": "BMW INTERIOR (61)",
            "customized_personas_count": 1,
            "recipients": 6,
            "respondents": 3,
            "status": "Finished",
            "created_at": "Aug 24, 2020"
        }
    ]
}
```

This endpoint List all surveys in Reports.

### HTTP Request

`GET https://app.elasticpersonas.ai/en/api/v1/reports/1/surveys/all`

### URL Parameters

Parameter | Description
--------- | -----------
report_id | The ID of the report

## List active surveys in Reports

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.elasticpersonas.ai/en/api/v1/reports/13/surveys/active")

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

conn.request("GET", "/en/api/v1/reports/13/surveys/active", headers=headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
curl --request GET \
  --url https://app.elasticpersonas.ai/en/api/v1/reports/13/surveys/active \
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

xhr.open("GET", "https://app.elasticpersonas.ai/en/api/v1/reports/13/surveys/active");
xhr.setRequestHeader("cache-control", "no-cache");

xhr.send(data);
```

> The above command returns JSON structured like this:

```json
{
    "surveys_count": 13,
    "active": 0,
    "draft": 0,
    "finished": 13,
    "surveys": []
}
```

This endpoint List active surveys in Reports.

### HTTP Request

`GET https://app.elasticpersonas.ai/en/api/v1/reports/13/surveys/active`

### URL Parameters

Parameter | Description
--------- | -----------
report_id | The ID of the report

## List finished surveys in Reports

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.elasticpersonas.ai/en/api/v1/reports/13/surveys/finished")

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

conn.request("GET", "/en/api/v1/reports/13/surveys/finished", headers=headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
curl --request GET \
  --url https://app.elasticpersonas.ai/en/api/v1/reports/13/surveys/finished \
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

xhr.open("GET", "https://app.elasticpersonas.ai/en/api/v1/reports/13/surveys/finished");
xhr.setRequestHeader("cache-control", "no-cache");

xhr.send(data);
```

> The above command returns JSON structured like this:

```json
{
    "surveys_count": 13,
    "active": 0,
    "draft": 0,
    "finished": 13,
    "surveys": [
        {
            "id": 330,
            "title": "Atom",
            "customized_personas_count": 0,
            "recipients": 0,
            "respondents": 0,
            "status": "Finished",
            "created_at": "Feb 24, 2021"
        },
        {
            "id": 327,
            "title": "other multiple check (2) (2)",
            "customized_personas_count": 0,
            "recipients": 0,
            "respondents": 0,
            "status": "Finished",
            "created_at": "Dec 07, 2020"
        },
        {
            "id": 319,
            "title": "other multiple check (2)",
            "customized_personas_count": 1,
            "recipients": 1,
            "respondents": 1,
            "status": "Finished",
            "created_at": "Dec 01, 2020"
        },
        {
            "id": 315,
            "title": "duplicate display type error (1) (1)",
            "customized_personas_count": 1,
            "recipients": 1,
            "respondents": 1,
            "status": "Finished",
            "created_at": "Oct 15, 2020"
        },
        {
            "id": 312,
            "title": "other multiple check (1)",
            "customized_personas_count": 0,
            "recipients": 3,
            "respondents": 1,
            "status": "Finished",
            "created_at": "Oct 14, 2020"
        },
        {
            "id": 309,
            "title": "duplicate display type error (1)",
            "customized_personas_count": 0,
            "recipients": 1,
            "respondents": 0,
            "status": "Finished",
            "created_at": "Oct 12, 2020"
        },
        {
            "id": 306,
            "title": "duplicate display type error",
            "customized_personas_count": 0,
            "recipients": 1,
            "respondents": 0,
            "status": "Finished",
            "created_at": "Oct 12, 2020"
        },
        {
            "id": 305,
            "title": "other multiple check",
            "customized_personas_count": 0,
            "recipients": 1,
            "respondents": 1,
            "status": "Finished",
            "created_at": "Oct 11, 2020"
        },
        {
            "id": 304,
            "title": "New testing set",
            "customized_personas_count": 2,
            "recipients": 2,
            "respondents": 2,
            "status": "Finished",
            "created_at": "Oct 08, 2020"
        },
        {
            "id": 293,
            "title": "survey template 2",
            "customized_personas_count": 2,
            "recipients": 3,
            "respondents": 3,
            "status": "Finished",
            "created_at": "Oct 04, 2020"
        }
    ]
}
```

This endpoint List finished surveys in Reports.

### HTTP Request

`GET https://app.elasticpersonas.ai/en/api/v1/reports/13/surveys/finished`

### URL Parameters

Parameter | Description
--------- | -----------
report_id | The ID of the report

# Groups

## Navigate to Groups

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.elasticpersonas.ai/en/api/v1/groups")

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

conn.request("GET", "/en/api/v1/groups", headers=headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
curl --request GET \
  --url https://app.elasticpersonas.ai/en/api/v1/groups \
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

xhr.open("GET", "https://app.elasticpersonas.ai/en/api/v1/groups");
xhr.setRequestHeader("cache-control", "no-cache");

xhr.send(data);
```

> The above command returns JSON structured like this:

```json
{
    "group_count": 14,
    "groups": [
        {
            "id": 22,
            "title": "New test group",
            "created_at": "2021-03-05T03:22:46.848-05:00",
            "created_by_id": 3,
            "archived": false,
            "survey_count": 0,
            "active_count": "0"
        },
        {
            "id": 18,
            "title": "testing new group",
            "created_at": "2020-11-19T05:56:03.311-05:00",
            "created_by_id": 3,
            "archived": false,
            "survey_count": 7,
            "active_count": "0"
        },
        {
            "id": 17,
            "title": "asdsdas",
            "created_at": "2020-10-21T22:44:50.394-04:00",
            "created_by_id": 3,
            "archived": false,
            "survey_count": 5,
            "active_count": "0"
        },
        {
            "id": 16,
            "title": "new gropsddd",
            "created_at": "2020-10-14T17:00:39.094-04:00",
            "created_by_id": 3,
            "archived": false,
            "survey_count": 3,
            "active_count": "0"
        },
        {
            "id": 15,
            "title": "new gropsdd",
            "created_at": "2020-10-14T17:00:22.366-04:00",
            "created_by_id": 3,
            "archived": false,
            "survey_count": 0,
            "active_count": "0"
        },
        {
            "id": 13,
            "title": "new grops",
            "created_at": "2020-08-26T21:59:09.039-04:00",
            "created_by_id": 3,
            "archived": false,
            "survey_count": 13,
            "active_count": "0"
        },
        {
            "id": 10,
            "title": "new grops10",
            "created_at": "2020-07-27T23:51:19.398-04:00",
            "created_by_id": 3,
            "archived": false,
            "image_url": "https://app.elasticpersonas.ai/rails/active_storage/blobs/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBDQT09IiwiZXhwIjpudWxsLCJwdXIiOiJibG9iX2lkIn19--999d136eedf75488dd260f4d031b674e9dbf88f7/output.png?locale=en",
            "survey_count": 8,
            "active_count": "0"
        },
        {
            "id": 9,
            "title": "new grops9",
            "created_at": "2020-07-27T23:51:10.830-04:00",
            "created_by_id": 3,
            "archived": false,
            "image_url": "https://app.elasticpersonas.ai/rails/active_storage/blobs/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBkUT09IiwiZXhwIjpudWxsLCJwdXIiOiJibG9iX2lkIn19--05e42a8ee3fa9cc01acffae046503395254234d8/output.png?locale=en",
            "survey_count": 4,
            "active_count": "0"
        },
        {
            "id": 7,
            "title": "new group7",
            "created_at": "2020-07-27T23:50:44.089-04:00",
            "created_by_id": 3,
            "archived": false,
            "survey_count": 0,
            "active_count": "0"
        },
        {
            "id": 6,
            "title": "new grops6",
            "created_at": "2020-07-27T23:50:33.045-04:00",
            "created_by_id": 3,
            "archived": false,
            "survey_count": 0,
            "active_count": "0"
        }
    ]
}
```

This endpoint Navigate to Groups.

### HTTP Request

`GET https://app.elasticpersonas.ai/en/api/v1/groups`

### URL Parameters

Not needed.

## List all surveys in Group

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.elasticpersonas.ai/en/api/v1/groups/1/surveys/all")

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

conn.request("GET", "/en/api/v1/groups/1/surveys/all", headers=headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
curl --request GET \
  --url https://app.elasticpersonas.ai/en/api/v1/groups/1/surveys/all \
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

xhr.open("GET", "https://app.elasticpersonas.ai/en/api/v1/groups/1/surveys/all");
xhr.setRequestHeader("cache-control", "no-cache");

xhr.send(data);
```

> The above command returns JSON structured like this:

```json
{
    "surveys_count": 75,
    "active": 0,
    "draft": 8,
    "finished": 67,
    "surveys": [
        {
            "id": 329,
            "title": "Survey with template 2 (2) (1)",
            "group": "new gropss",
            "group_image": "no-img-reports.png",
            "recipients": 1,
            "respondents": 0,
            "status": "Finished",
            "created_at": "Dec 14, 2020",
            "created_by": "Ajith"
        },
        {
            "id": 328,
            "title": "Survey with template 2 (2)",
            "group": "new gropss",
            "group_image": "no-img-reports.png",
            "recipients": 1,
            "respondents": 0,
            "status": "Finished",
            "created_at": "Dec 14, 2020",
            "created_by": "Ajith"
        },
        {
            "id": 325,
            "title": "Survey with template 2 (1)",
            "group": "new gropss",
            "group_image": "no-img-reports.png",
            "recipients": 0,
            "respondents": 0,
            "status": "Finished",
            "created_at": "Dec 07, 2020",
            "created_by": "Ajith"
        },
        {
            "id": 311,
            "title": "Survey with template 2",
            "group": "new gropss",
            "group_image": "no-img-reports.png",
            "recipients": 8,
            "respondents": 5,
            "status": "Finished",
            "created_at": "Oct 13, 2020",
            "created_by": "Ajith"
        },
        {
            "id": 310,
            "title": "Survey with template 1",
            "group": "new gropss",
            "group_image": "no-img-reports.png",
            "recipients": 3,
            "respondents": 2,
            "status": "Finished",
            "created_at": "Oct 13, 2020",
            "created_by": "Ajith"
        },
        {
            "id": 292,
            "title": "Survey template 1",
            "group": "new gropss",
            "group_image": "no-img-reports.png",
            "recipients": 1,
            "respondents": 1,
            "status": "Finished",
            "created_at": "Oct 04, 2020",
            "created_by": "Ajith"
        },
        {
            "id": 285,
            "title": "Survey without branching",
            "group": "new gropss",
            "group_image": "no-img-reports.png",
            "status": "Created",
            "created_at": "Sep 29, 2020",
            "created_by": "Ajith"
        },
        {
            "id": 283,
            "title": "BMW INTERIOR",
            "group": "new gropss",
            "group_image": "no-img-reports.png",
            "recipients": 0,
            "respondents": 0,
            "status": "Finished",
            "created_at": "Sep 16, 2020",
            "created_by": "Ajith"
        },
        {
            "id": 274,
            "title": "BMW INTERIOR",
            "group": "new gropss",
            "group_image": "no-img-reports.png",
            "recipients": 0,
            "respondents": 0,
            "status": "Finished",
            "created_at": "Aug 25, 2020",
            "created_by": "Ajith"
        },
        {
            "id": 273,
            "title": "BMW INTERIOR (52) (1) (1) (1) (1) (1)",
            "group": "new gropss",
            "group_image": "no-img-reports.png",
            "recipients": 1,
            "respondents": 1,
            "status": "Finished",
            "created_at": "Aug 25, 2020",
            "created_by": "Ajith"
        }
    ]
}
```

This endpoint List all surveys in Group.

### HTTP Request

`GET https://app.elasticpersonas.ai/en/api/v1/groups/1/surveys/all`

### URL Parameters

Parameter | Description
--------- | -----------
group_id | The ID of the group

## List active surveys in Group

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.elasticpersonas.ai/en/api/v1/groups/1/surveys/active")

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

conn.request("GET", "/en/api/v1/groups/1/surveys/active", headers=headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
curl --request GET \
  --url https://app.elasticpersonas.ai/en/api/v1/groups/1/surveys/active \
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

xhr.open("GET", "https://app.elasticpersonas.ai/en/api/v1/groups/1/surveys/active");
xhr.setRequestHeader("cache-control", "no-cache");

xhr.send(data);
```

> The above command returns JSON structured like this:

```json
{
    "surveys_count": 75,
    "active": 0,
    "draft": 8,
    "finished": 67,
    "surveys": []
}
```

This endpoint List active surveys in Group.

### HTTP Request

`GET https://app.elasticpersonas.ai/en/api/v1/groups/1/surveys/active`

### URL Parameters

Parameter | Description
--------- | -----------
group_id | The ID of the group

## List finished surveys in Group

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.elasticpersonas.ai/en/api/v1/groups/1/surveys/finished")

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

conn.request("GET", "/en/api/v1/groups/1/surveys/finished", headers=headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
curl --request GET \
  --url https://app.elasticpersonas.ai/en/api/v1/groups/1/surveys/finished \
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

xhr.open("GET", "https://app.elasticpersonas.ai/en/api/v1/groups/1/surveys/finished");
xhr.setRequestHeader("cache-control", "no-cache");

xhr.send(data);
```

> The above command returns JSON structured like this:

```json
{
    "surveys_count": 75,
    "active": 0,
    "draft": 8,
    "finished": 67,
    "surveys": [
        {
            "id": 329,
            "title": "Survey with template 2 (2) (1)",
            "group": "new gropss",
            "group_image": "no-img-reports.png",
            "recipients": 1,
            "respondents": 0,
            "status": "Finished",
            "created_at": "Dec 14, 2020",
            "created_by": "Ajith"
        },
        {
            "id": 328,
            "title": "Survey with template 2 (2)",
            "group": "new gropss",
            "group_image": "no-img-reports.png",
            "recipients": 1,
            "respondents": 0,
            "status": "Finished",
            "created_at": "Dec 14, 2020",
            "created_by": "Ajith"
        },
        {
            "id": 325,
            "title": "Survey with template 2 (1)",
            "group": "new gropss",
            "group_image": "no-img-reports.png",
            "recipients": 0,
            "respondents": 0,
            "status": "Finished",
            "created_at": "Dec 07, 2020",
            "created_by": "Ajith"
        },
        {
            "id": 311,
            "title": "Survey with template 2",
            "group": "new gropss",
            "group_image": "no-img-reports.png",
            "recipients": 8,
            "respondents": 5,
            "status": "Finished",
            "created_at": "Oct 13, 2020",
            "created_by": "Ajith"
        },
        {
            "id": 310,
            "title": "Survey with template 1",
            "group": "new gropss",
            "group_image": "no-img-reports.png",
            "recipients": 3,
            "respondents": 2,
            "status": "Finished",
            "created_at": "Oct 13, 2020",
            "created_by": "Ajith"
        },
        {
            "id": 292,
            "title": "Survey template 1",
            "group": "new gropss",
            "group_image": "no-img-reports.png",
            "recipients": 1,
            "respondents": 1,
            "status": "Finished",
            "created_at": "Oct 04, 2020",
            "created_by": "Ajith"
        },
        {
            "id": 283,
            "title": "BMW INTERIOR",
            "group": "new gropss",
            "group_image": "no-img-reports.png",
            "recipients": 0,
            "respondents": 0,
            "status": "Finished",
            "created_at": "Sep 16, 2020",
            "created_by": "Ajith"
        },
        {
            "id": 274,
            "title": "BMW INTERIOR",
            "group": "new gropss",
            "group_image": "no-img-reports.png",
            "recipients": 0,
            "respondents": 0,
            "status": "Finished",
            "created_at": "Aug 25, 2020",
            "created_by": "Ajith"
        },
        {
            "id": 273,
            "title": "BMW INTERIOR (52) (1) (1) (1) (1) (1)",
            "group": "new gropss",
            "group_image": "no-img-reports.png",
            "recipients": 1,
            "respondents": 1,
            "status": "Finished",
            "created_at": "Aug 25, 2020",
            "created_by": "Ajith"
        },
        {
            "id": 272,
            "title": "BMW INTERIOR (61)",
            "group": "new gropss",
            "group_image": "no-img-reports.png",
            "recipients": 6,
            "respondents": 3,
            "status": "Finished",
            "created_at": "Aug 24, 2020",
            "created_by": "Ajith"
        }
    ]
}
```

This endpoint List finished surveys in Group.

### HTTP Request

`GET https://app.elasticpersonas.ai/en/api/v1/groups/1/surveys/finished`

### URL Parameters

Parameter | Description
--------- | -----------
group_id | The ID of the group

## List draft surveys in Group

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.elasticpersonas.ai/en/api/v1/groups/1/surveys/draft")

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

conn.request("GET", "/en/api/v1/groups/1/surveys/draft", headers=headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
curl --request GET \
  --url https://app.elasticpersonas.ai/en/api/v1/groups/1/surveys/draft \
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

xhr.open("GET", "https://app.elasticpersonas.ai/en/api/v1/groups/1/surveys/draft");
xhr.setRequestHeader("cache-control", "no-cache");

xhr.send(data);
```

> The above command returns JSON structured like this:

```json
{
    "surveys_count": 75,
    "active": 0,
    "draft": 8,
    "finished": 67,
    "surveys": [
        {
            "id": 285,
            "title": "Survey without branching",
            "group": "new gropss",
            "group_image": "no-img-reports.png",
            "status": "Draft",
            "created_at": "Sep 29, 2020",
            "created_by": "Ajith"
        },
        {
            "id": 270,
            "title": "Branching 1",
            "group": "new gropss",
            "group_image": "no-img-reports.png",
            "status": "Draft",
            "created_at": "Aug 24, 2020",
            "created_by": "Ajith"
        },
        {
            "id": 248,
            "title": "Normal survey 1",
            "group": "new gropss",
            "group_image": "no-img-reports.png",
            "status": "Draft",
            "created_at": "Jul 28, 2020",
            "created_by": "Ajith"
        },
        {
            "id": 227,
            "title": "BMW INTERIOR (1) (1) (1) (1) (1)",
            "group": "new gropss",
            "group_image": "no-img-reports.png",
            "status": "Draft",
            "created_at": "Jul 26, 2020",
            "created_by": "Ajith"
        },
        {
            "id": 224,
            "title": "BMW INTERIOR (1) (1) (1) (1)",
            "group": "new gropss",
            "group_image": "no-img-reports.png",
            "status": "Draft",
            "created_at": "Jul 26, 2020",
            "created_by": "Ajith"
        },
        {
            "id": 164,
            "title": "BMW INTERIOR (1) (1) (1)",
            "group": "new gropss",
            "group_image": "no-img-reports.png",
            "status": "Draft",
            "created_at": "Jul 23, 2020",
            "created_by": "Ajith"
        },
        {
            "id": 57,
            "title": "BMW INTERIOR (47)",
            "group": "new gropss",
            "group_image": "no-img-reports.png",
            "status": "Draft",
            "created_at": "Jul 19, 2020",
            "created_by": "Ajith"
        },
        {
            "id": 8,
            "title": "BMW INTERIOR",
            "group": "new gropss",
            "group_image": "no-img-reports.png",
            "status": "Draft",
            "created_at": "Apr 01, 2020",
            "created_by": "Ajith"
        }
    ]
}
```

This endpoint List draft surveys in Group.

### HTTP Request

`GET https://app.elasticpersonas.ai/en/api/v1/groups/1/surveys/draft`

### URL Parameters

Parameter | Description
--------- | -----------
group_id | The ID of the group

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