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

url = URI("localhost:3000/en/api/v1/accounts/login")

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
curl --location --request POST 'localhost:3000/en/api/v1/accounts/login' \
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

fetch("localhost:3000/en/api/v1/accounts/login", requestOptions)
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

`POST http://localhost:3000/en/api/v1/accounts/login`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
email | - | client email.
password | - | client password


<aside class="success">
Remember — You can get the JWT token from the response header!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten

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

