---
title: API Reference

language_tabs:
  - shell
  - ruby
  - javascript

toc_footers:
  - <a href='http://www.qlear.build' target="_blank">API Document for QLEAR</a>

<!-- includes:
  - errors -->

search: true
---

# Introduction

Welcome to the QLEAR API! You can use our API to access QLEAR API endpoints, which can get all informations about user, location, monitor and reading data etc.

# Authentication

> To authorize, use the access token, assigned by QLEAR:

```javascript
fetch('http://example.com/path_of_api?access_token=12345')
  .then(function(response) {
    return response.json()
  }).then(function(json) {
    console.log(json)
  }).catch(function(ex) {
    console.log('parsing failed', ex)
  })
```

```ruby
#You can use any other gem to replace rest-client
require 'rest-client'

content = RestClient.get 'http://example.com', {params: {access_token: '12345'}}
```


```shell
# With shell, you can just pass the correct query with each request

curl "http://example.com?access_token=12345&[other_params]"
```

> Make sure to replace `12345` with your access token.

QLEAR uses access token to allow access to the API. you can contact QLEAR support to obtain the token.

QLEAR expects for the access token to be included in all API requests to the server in the query that looks like the following:

`http://example.com?access_token=12345`

<aside class="notice">
* You must replace <code>12345</code> with your personal access token.
</aside>

<aside class="notice">
* You must replace <code>http://example.com</code> with the correct service url.
</aside>

# Cities

## Get All Cities

```javascript
fetch('http://example.com/v2/cities?access_token=12345')
  .then(function(response) {
    return response.json()
  }).then(function(json) {
    console.log(json)
  }).catch(function(ex) {
    console.log('parsing failed', ex)
  })
```

```ruby
require 'rest-client'

content = RestClient.get http://example.com/v2/cities, {params: {access_token: '12345'}}
```


```shell
curl "http://example.com/v2/cities?access_token=12345"
```

> The above command returns JSON structured like this:

```json

{
  "data": [
    {
      "id": 2,
      "name": "Beijing",
      "image": null
    },
    {
      "id": 800,
      "name": "Shanghai",
      "image": "https://dn-reset.qbox.me/uploads/city/theme/thumb_beb52b19-3f34-4cac-b093-95709cfedc59.jpg"
    },
    {
      "id": 864,
      "name": "Suzhou",
      "image": null
    }
  ],
  "meta": {
    "total_count": 3,
    "total_pages": 1,
    "current_page": 1,
    "last_page": true
  }
}
```

This endpoint retrieves all available cities.

### HTTP Request

`GET http://example.com/v2/cities`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
access_token | false | Access Token.
locale | en | If set to en, will return english name for city.
page|1|Page number
size|20|Size per page


Available values for locale:

* en
* zh-CN




