---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - python
  - javascript

toc_footers:
  # - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Orange Power Ltd</a>

includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the Kittn API
---

# Introduction

Welcome to the Orange Power Connect API! You can use our API to access different devices API endpoints, which can get information, or give access to different control mechanisms.

We have language bindings in Shell, Ruby, Python, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

# BMW

## Get Tokens

```ruby
require "uri"
require "json"
require "net/http"

url = URI("http://localhost:3000/api/bmw/oauth-token")

http = Net::HTTP.new(url.host, url.port);
request = Net::HTTP::Post.new(url)
request["Content-Type"] = "application/json"
request.body = JSON.dump({
  "email": "georgebatts1@outlook.com",
  "password": "Myenergi123&",
  "payload": {
    "email": "test@test.com"
  }
})

response = http.request(request)
puts response.read_body
```

```python
import requests
import json

url = "http://localhost:3000/api/bmw/oauth-token"

payload = json.dumps({
  "email": "georgebatts1@outlook.com",
  "password": "Myenergi123&",
  "payload": {
    "email": "test@test.com"
  }
})
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

```shell
curl --location --request POST 'http://localhost:3000/api/bmw/oauth-token' \
--header 'Content-Type: application/json' \
--data-raw '{
 "email":"georgebatts1@outlook.com",
 "password":"Myenergi123&",
 "payload":{
     "email":"test@test.com"
 }
}'
```

```javascript
var axios = require('axios');
var data = JSON.stringify({
  "email": "georgebatts1@outlook.com",
  "password": "Myenergi123&",
  "payload": {
    "email": "test@test.com"
  }
});

var config = {
  method: 'post',
  url: 'http://localhost:3000/api/bmw/oauth-token',
  headers: { 
    'Content-Type': 'application/json'
  },
  maxRedirects: 0,
  data : data
};

axios(config)
.then(function (response) {
  console.log(JSON.stringify(response.data));
})
.catch(function (error) {
  console.log(error);
});
```
> Request body:

```json
{
 "email":"demo@outlook.com",
 "password":"demopass",
 "payload":{
     "email":"test@test.com"
 }
}
```

> Response:

```json
{
    "access_token": "YKJUUwmBXcQThWx7XzU7ddd4pyMZkd3tgWM",
    "token_type": "Bearer",
    "expires_in": 28800,
    "refresh_token": "mRlcF34pWzkfHxOauwpVe7B3GSMxCSFdfeRIPA3G9ilkHSGacnkUUo",
    "scope": "smacc vehicle_data vehicle_list perseus svds dlm cesim mini_connected remote_services authenticate_user fupo"
}
```

This endpoint returns access token.

### HTTP Request

`POST https://www.connect.orangepower.co.uk/api/bmw/oauth-token`

<!-- <aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside> -->

## Get vehicle info

```ruby
require "uri"
require "json"
require "net/http"

url = URI("https://www.connect.orangepower.co.uk/api/get-user-devices")

https = Net::HTTP.new(url.host, url.port)
https.use_ssl = true

request = Net::HTTP::Post.new(url)
request["Authorization"] = "Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJlbWFpbCI6InRyYW5zcG9ydGVyQGdtYWlsLmNvbSIsInBhc3N3b3JkIjoidHJhbnNwb3J0ZXIiLCJpYXQiOjE2NDQwNzQ0OTgsImV4cCI6MTY0NDA3ODA5OH0"
request["Content-Type"] = "application/json"
request.body = JSON.dump({
  "email": "test@test.com",
  "password": "testing123"
})

response = https.request(request)
puts response.read_body

```

```python
import requests
import json

url = "https://www.connect.orangepower.co.uk/api/get-user-devices"

payload = json.dumps({
  "email": "test@test.com",
  "password": "testing123"
})
headers = {
  'Authorization': 'Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJlbWFpbCI6InRyYW5zcG9ydGVyQGdtYWlsLmNvbSIsInBhc3N3b3JkIjoidHJhbnNwb3J0ZXIiLCJpYXQiOjE2NDQwNzQ0OTgsImV4cCI6MTY0NDA3ODA5OH0',
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

```shell
curl --location --request POST 'https://www.connect.orangepower.co.uk/api/get-user-devices' \
--header 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJlbWFpbCI6InRyYW5zcG9ydGVyQGdtYWlsLmNvbSIsInBhc3N3b3JkIjoidHJhbnNwb3J0ZXIiLCJpYXQiOjE2NDQwNzQ0OTgsImV4cCI6MTY0NDA3ODA5OH0' \
--header 'Content-Type: application/json' \
--data-raw '{
    "email":"test@test.com",
    "password":"testing123"
}'
```

```javascript
var axios = require('axios');
var data = JSON.stringify({
  "email": "test@test.com",
  "password": "testing123"
});

var config = {
  method: 'post',
  url: 'https://www.connect.orangepower.co.uk/api/get-user-devices',
  headers: { 
    'Authorization': 'Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJlbWFpbCI6InRyYW5zcG9ydGVyQGdtYWlsLmNvbSIsInBhc3N3b3JkIjoidHJhbnNwb3J0ZXIiLCJpYXQiOjE2NDQwNzQ0OTgsImV4cCI6MTY0NDA3ODA5OH0', 
    'Content-Type': 'application/json'
  },
  maxRedirects: 0,
  data : data
};

axios(config)
.then(function (response) {
  console.log(JSON.stringify(response.data));
})
.catch(function (error) {
  console.log(error);
});

```
> Request body:

```json
{
  "email": "demo@hotmail.com",
  "password": "password"
}
```

> Response:

```json
    {
        "_id": "62137c48e075b1442f0c955c",
        "electric_range": {
            "distance": {
                "value": 121,
                "units": "KILOMETERS"
            }
        },
        "device_type": "bmw",
        "user_id": "61b1d1a2d5df13f67657dbf2",
        "device_id": "WBY7ZddD802daf16",
        "id": "916ba1b2eeba4b4881ce9d829852d70e",
        "model": "i3s 94 REX",
        "year": 2018,
        "brand": "BMW",
        "charging_state": {
            "charge_percentage": "82",
            "state": "NOT_CHARGING",
            "type": "CONDUCTIVE",
            "is_charger_connected": false
        },
        "__v": 0
    }
```

This endpoint retrieves all the details related to your BMW car

### HTTP Request

`POST https://www.connect.orangepower.co.uk/api/get-user-devices`

### Authorization Parameters

Bearer `<token>`

