---
title: API Document for QLEAR (v2.0)

language_tabs:
  - shell
  - ruby

search: true
---

# Introduction
> To access api, use the access token, assigned by QLEAR:

Welcome to the QLEAR API! You can use our API to access QLEAR API endpoints, which can get all informations about user, location, monitor and reading data etc.

# Access Token


```ruby
#You can use any other gem to replace rest-client
require 'rest-client'

content = RestClient.get 'http://example.com/ping',
  {params: {access_token: '12345'}}
```


```shell
# With shell, you can just pass the correct query with each request

curl "http://example.com/ping?access_token=12345"
```

> The above returns JSON structured like this:

```json

{
  "status": "pong",
  "code": 200
}
```

QLEAR uses access token to allow access to the API. you can contact QLEAR support to obtain the token.

QLEAR expects for the access token to be included in all API requests to the server in the query that looks like the following:

`http://example.com/ping?access_token=12345`

<aside class="notice">
* You must replace <code>12345</code> with your personal access token.
</aside>

# Localization

QLEAR API supports localization for error messages and other strings. Localization is defined in each request with query string 'locale'. Accepted values are currently:

* en    - English (default)
* zh-CN - Chinese

Numbers, currency and datetime don’t rely on localization so they will always be returned in standard format.

# Cities

## Get All Cities


```ruby
require 'rest-client'

content = RestClient.get 'http://example.com/v2/cities',
  {params: {access_token: '12345'}}
```


```shell
curl "http://example.com/v2/cities?access_token=12345"
```

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

Parameter | Require| Default | Description
--------- | -------| ------- | -----------
access_token | true| | Access Token.
locale | false| en | Localization
page|false|1|Page number
size|false|20|Size per page


## Get Activity Cities

```ruby
require 'rest-client'

content = RestClient.get 'http://example.com/v2/cities/activity',
  {params: {access_token: '12345'}}
```

```shell
curl "http://example.com/v2/cities/activity?access_token=12345"
```

```json
{
  "data": {
    "china": [
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
    "global": [
      {
        "id": 3238,
        "name": "Xianggang",
        "image": null
      }
    ]
  }
}

```

Get all activity cities, grouping by country.

### HTTP Request

`GET http://example.com/v2/cities/activity`

### Query Parameters

Parameter | Require| Default | Description
--------- | -------| ------- | -----------
access_token|true |  | Access Token.
locale |false| en | Localization


# Location

## Get All Locations

```ruby
require 'rest-client'

content = RestClient.get 'http://example.com/v2/locations',
  {params: {access_token: '12345', per: 2, page: 2}}
```


```shell
curl "http://example.com/v2/locations?access_token=12345&per=2&page=2"
```

```json

{
  "data": [
    {
      "id": 41,
      "name": "Canadian International School of Beijing",
      "city_id": 800,
      "city_name": "Shanghai",
      "station_name": null,
      "theme": "https://dn-reset.qbox.me//uploads/location/theme/thumb_66c95d6d-fe28-4e46-a66f-bb4286d572d4.jpg",
      "category": "indoor",
      "locked": false,
      "status": "good",
      "reading": {
        "pm2p5": 13,
        "bto": "--"
      }
    },
    {
      "id": 33,
      "name": "YCIS Beijing",
      "city_id": 800,
      "city_name": "Shanghai",
      "station_name": null,
      "theme": "https://dn-reset.qbox.me//uploads/location/theme/thumb_2916045d-f8b4-4dff-9244-5c6dfad3ca2e.jpg",
      "category": "indoor",
      "locked": false,
      "status": "good",
      "reading": {
        "pm2p5": 11,
        "bto": "--"
      }
    }
  ],
  "meta": {
    "total_count": 35,
    "total_pages": 18,
    "current_page": 2,
    "last_page": false
  }
}
```

Get all locations, can be filtered by city id and location name
### HTTP Request

`GET http://example.com/v2/locations`

### Query Parameters

Parameter | Require|  Default | Description
--------- | ------- | ------- | -----------
access_token|true | false | Access Token.
locale |false| en | Localization
city_id|false|  | City ID
name|falase|| Location name (support fuzzy query, SFQ)
page|false|1|Page number
size|false|20|Size per page


## Get Location Details

```ruby
content = RestClient.get 'http://example.com/v2/location/45'
```

```shell
curl "http://example.com/v2/locations/45"
```

```json

{
  "data": {
    "id": 24,
    "name": "Glumac",
    "desc": "",
    "city_id": 800,
    "city_name": "Shanghai",
    "station_name": null,
    "logo": "https://dn-reset.qbox.me/uploads/location/logo/dc7f364a-448e-4ec0-8996-dda793b938c8.png",
    "theme": "https://dn-reset.qbox.me/uploads/location/theme/0abd7419-9667-43de-bd10-9fa95add6db9.jpg",
    "category": "indoor",
    "stale": false,
    "follow": false,
    "primary_indicator": "pm2p5",
    "last_updated_at": "2016-03-23 17:00:00",
    "indoor_reading": [
      {
        "indicator": "pm2p5",
        "name": "PM 2.5",
        "unit": "μg/m³",
        "value": 13,
        "level": "good"
      },
      {
        "indicator": "co2",
        "name": "CO2",
        "unit": "ppm",
        "value": 360,
        "level": "good"
      },
      {
        "indicator": "tvoc",
        "name": "Total VOC",
        "unit": "mg/m³",
        "value": 0.04,
        "level": "good"
      },
      {
        "indicator": "temperature",
        "name": "Temperature",
        "unit": "°C",
        "value": 23,
        "level": null
      },
      {
        "indicator": "humidity",
        "name": "Humidity",
        "unit": "%RH",
        "value": 36.73,
        "level": "good"
      }
    ],
    "outdoor_reading": [
      {
        "indicator": "pm2p5",
        "name": "PM 2.5",
        "unit": "μg/m³",
        "value": 37,
        "level": "moderate"
      },
      {
        "indicator": "temperature",
        "name": "Temperature",
        "unit": "°C",
        "value": null,
        "level": null
      },
      {
        "indicator": "humidity",
        "name": "Humidity",
        "unit": "%RH",
        "value": null,
        "level": null
      }
    ],
    "bto": "2.8",
    "monitors": [
      "PM 2.5"
    ],
    "certifications": [
      {
        "name": "RESET Certified",
        "logo": "https://dn-reset.qbox.me/uploads/certification/logo/7f9180e3-916f-465d-9a62-3b7e3a86b279.png",
        "desc": "RESET"
      },
      {
        "name": "WELL Certified",
        "logo": "https://dn-reset.qbox.me/uploads/certification/logo/0e283e52-6a29-427e-ad1b-dbfc75440df0.png",
        "desc": ""
      },
      {
        "name": "LEED Certified",
        "logo": "https://dn-reset.qbox.me/uploads/certification/logo/a4c9c016-ee81-413c-a48a-47e5d3bcda5a.png",
        "desc": ""
      },
      {
        "name": "LBC Certified",
        "logo": "https://dn-reset.qbox.me/uploads/certification/logo/c3b0c543-c194-45ff-80ed-e9a1f2cf30bb.png",
        "desc": ""
      }
    ]
  }
}
```

Get location details by ID
### HTTP Request

`GET http://example.com/v2/locations/45`


<aside class="notice">
* You must replace <code>24</code> with your location ID.
</aside>

### Query Parameters

Parameter |Require| Default | Description
--------- | ------- | ------- | -----------
access_token |true|  | Access Token.
locale |false| en | Localization
