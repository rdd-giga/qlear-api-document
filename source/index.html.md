---
title: API Document for QLEAR (v2.0)

language_tabs:
  - ruby

search: true
---

# Introduction
> To access api, use the access token, assigned by QLEAR:

Welcome to the QLEAR API! You can use our API to access QLEAR API endpoints, which can get all informations about user, location, monitor and reading data etc.

# Access Token


```ruby
content = RestClient.get 'http://example.com/v2/ping',
  {params: {access_token: '12345'}}
```

> The above returns JSON structured like this:

```json
{
  "meta": {
    "code": 10000,
    "message": "Success"
  }
}
```

QLEAR uses access token to allow access to the API. you can contact QLEAR support to obtain the token.

QLEAR expects for the access token to be included in all API requests to the server in the query string.

# Localization

QLEAR API supports localization for error messages and other strings. Localization is defined in each request with query string 'locale'. Accepted values are currently:

* en    - English (default)
* zh-CN - Chinese

Numbers, currency and datetime don’t rely on localization so they will always be returned in standard format.

# User
## Sign Up


```ruby
require 'rest-client'

content = RestClient.post 'http://example.com/v2/users/sign_up',
  {params: {access_token: '12345', email: 'm2@giga.build', password: '11111111', user_name: 'Test User', last_name: '', first_name: ''}}
```

```json

{
  "data": {
    "id": 65,
    "email": "m2@giga.build",
    "first_name": null,
    "last_name": null,
    "auth_token": "0792f9d0-0b70-4747-93d2-17c6a243df6d",
    "user_name": "Test User",
    "mobile": null
  },
  "meta": {
    "code": 10000,
    "message": "Success"
  }
}
```

Create new account.

### HTTP Request

`POST http://example.com/v2/users/sign_up`

### Parameters

Parameter | Require| Default | Description
--------- | -------| ------- | -----------
access_token | true| | Access Token.
locale | false| en | Localization
email|true||Email
password|true||Password
user_name|true||User Name
mobile|false||Mobile


## Sign In

```ruby
require 'rest-client'

content = RestClient.post 'http://example.com/v2/users/sign_in',
  {params: {access_token: '12345', email: 'm2@giga.build', password: '11111111'}}
```

```json

{
  "data": {
    "id": 65,
    "email": "m2@giga.build",
    "first_name": null,
    "last_name": null,
    "auth_token": "d3248374-64cd-44ca-afcd-b7e2c55e40b2",
    "user_name": "Test User",
    "mobile": null
  },
  "meta": {
    "code": 10000,
    "message": "Success"
  }
}
```

Sign in with email and password

### HTTP Request

`POST http://example.com/v2/users/sign_in`

### Parameters

Parameter | Require| Default | Description
--------- | -------| ------- | -----------
access_token | true| | Access Token.
locale | false| en | Localization
email|true||Email
password|true||Password

## Get Profile

```ruby
require 'rest-client'

content = RestClient.get 'http://example.com/v2/users/profile',
  {params: {access_token: '12345', auth_token: 'd3248374-64cd-44ca-afcd-b7e2c55e40b2'}}
```

```json

{
  "data": {
    "id": 65,
    "email": "m2@giga.build",
    "first_name": null,
    "last_name": null,
    "auth_token": "d3248374-64cd-44ca-afcd-b7e2c55e40b2",
    "user_name": "Test User",
    "mobile": null
  },
  "meta": {
    "code": 10000,
    "message": "Success"
  }
}
```

Get user profile with the giving auth token, returned by server.

### HTTP Request

`GET http://example.com/v2/users/profile`

### Parameters

Parameter | Require| Default | Description
--------- | -------| ------- | -----------
access_token | true| | Access Token.
auth_token|true||Auth Token
locale | false| en | Localization

## Update Profile

```ruby
require 'rest-client'

content = RestClient.post 'http://example.com/v2/users/profile',
  {params: {access_token: '12345', auth_token: 'd3248374-64cd-44ca-afcd-b7e2c55e40b2', user_name: '', first_name: '', last_name: '', mobile: '', }}
```

```json

{
  "data": {
    "id": 65,
    "email": "m2@giga.build",
    "first_name": null,
    "last_name": null,
    "auth_token": "d3248374-64cd-44ca-afcd-b7e2c55e40b2",
    "user_name": "Test User",
    "mobile": null
  },
  "meta": {
    "code": 10000,
    "message": "Success"
  }
}
```

Update profile

### HTTP Request

`POST http://example.com/v2/users/profile`

### Parameters

Parameter | Require| Default | Description
--------- | -------| ------- | -----------
access_token | true| | Access Token.
auth_token|true||Auth Token
locale | false| en | Localization
user_name|false||User Name
first_name|false||First Name
last_name|false|| Last Name
mobile|false||Mobile

## Update Password

```ruby
require 'rest-client'

content = RestClient.post 'http://example.com/v2/users/password',
  {params: {access_token: '12345', auth_token: 'd3248374-64cd-44ca-afcd-b7e2c55e40b2', old_password: '', new_password: ''}}
```

```json
{
  "meta": {
    "code": 10000,
    "message": "Success"
  }
}
```

Update profile

### HTTP Request

`POST http://example.com/v2/users/password`

### Parameters

Parameter | Require| Default | Description
--------- | -------| ------- | -----------
access_token | true| | Access Token.
auth_token|true||Auth Token
locale | false| en | Localization
old_password|true||Previous Password
new_password|true||New Password

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

### Parameters

Parameter | Require| Default | Description
--------- | -------| ------- | -----------
access_token | true| | Access Token.
auth_token|true||Auth Token
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

### Parameters

Parameter | Require| Default | Description
--------- | -------| ------- | -----------
access_token|true |  | Access Token.
auth_token|true||Auth Token
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

### Parameters

Parameter | Require|  Default | Description
--------- | ------- | ------- | -----------
access_token|true | false | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization
city_id|false|  | City ID
name|falase|| Location name (support fuzzy query, SFQ)
page|false|1|Page number
size|false|20|Size per page

## Get Location's Details

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
* You must replace <code>45</code> with your location ID.
</aside>

### Parameters

Parameter |Require| Default | Description
--------- | ------- | ------- | -----------
access_token |true|  | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization
unlock_token|false||Unlock Token


## Get Monitor's Detail

```ruby
require 'rest-client'

content = RestClient.get 'http://example.com/v2/locations',
  {params: {access_token: '12345', location_id: 45, monitor_id: 28}}
```


```shell
curl "http://example.com/v2/locations/45/monitors/28?access_token=12345"
```

```json

{
  "data": {
    "id": 64,
    "name": "Particulate Matter ",
    "identifier": "30245",
    "label": "Particulate Matter ",
    "logo": null,
    "device_type": "air_advice",
    "stale": true,
    "follow": false,
    "indicator": [
      "humidity",
      "co2",
      "tvoc",
      "pm2p5"
    ],
    "last_reading_time": null,
    "last_received_at": "2015-04-08 23:33:50",
    "reading": [
      {
        "indicator": "pm2p5",
        "name": "PM 2.5",
        "unit": "μg/m³",
        "value": 32,
        "level": "good"
      },
      {
        "indicator": "co2",
        "name": "CO2",
        "unit": "ppm",
        "value": null,
        "level": null
      },
      {
        "indicator": "tvoc",
        "name": "Total VOC",
        "unit": "μg/m³",
        "value": null,
        "level": null
      },
      {
        "indicator": "humidity",
        "name": "Humidity",
        "unit": "%RH",
        "value": 26,
        "level": "good"
      }
    ]
  },
  "meta": {
    "code": 10000,
    "message": "Success"
  }
}
```

Get monitor's detail, which binding the specific location
### HTTP Request

`GET http://example.com/v2/locations/45/monitors/28`

<aside class="notice">
* You must replace <code>45</code> with your location ID, <code>28</code> with your monitor ID.
</aside>

### Parameters

Parameter | Require|  Default | Description
--------- | ------- | ------- | -----------
access_token|true | false | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization
location_id|true|  | Location ID
monitor_id|true|| Monitor ID

## Unlock Location

```ruby
require 'rest-client'

content = RestClient.post 'http://example.com/v2/locations/45/unlock',
  {params: {access_token: '12345', password: '123456'}}
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
  },
  "meta": {
    "code":10000,
    "message":"Success",
    "access_token":"30834411-f7db-486a-840b-21eb66b2699e",
    "unlock_token":"rvanyAZ0OQk13fWHL0X6cyY3gF8tuxIRx+2y20DXgto="
  }
}
```

Unlock location with the giving password
### HTTP Request

`POST http://example.com/v2/locations/45/unlock`

<aside class="notice">
* You must replace <code>45</code> with your location ID.
</aside>

### Parameters

Parameter | Require|  Default | Description
--------- | ------- | ------- | -----------
access_token|true | false | Access Token.
auth_token|false||Auth Token
locale |false| en | Localization
location_id|true|  | Location ID
password|true||Password

# Monitor
## Get Monitor's Detail

```ruby
require 'rest-client'

content = RestClient.get 'http://example.com/v2/locations',
  {params: {access_token: '12345', monitor_id: 28}}
```


```shell
curl "http://example.com/v2/monitors/28?access_token=12345"
```

```json

{
  "data": {
    "id": 64,
    "name": "Particulate Matter ",
    "identifier": "30245",
    "label": "Particulate Matter ",
    "logo": null,
    "device_type": "air_advice",
    "stale": true,
    "follow": false,
    "indicator": [
      "humidity",
      "co2",
      "tvoc",
      "pm2p5"
    ],
    "last_reading_time": null,
    "last_received_at": "2015-04-08 23:33:50",
    "reading": [
      {
        "indicator": "pm2p5",
        "name": "PM 2.5",
        "unit": "μg/m³",
        "value": 32,
        "level": "good"
      },
      {
        "indicator": "co2",
        "name": "CO2",
        "unit": "ppm",
        "value": null,
        "level": null
      },
      {
        "indicator": "tvoc",
        "name": "Total VOC",
        "unit": "μg/m³",
        "value": null,
        "level": null
      },
      {
        "indicator": "humidity",
        "name": "Humidity",
        "unit": "%RH",
        "value": 26,
        "level": "good"
      }
    ]
  },
  "meta": {
    "code": 10000,
    "message": "Success"
  }
}
```

Get monitor's detail
### HTTP Request

`GET http://example.com/v2/monitors/28`

<aside class="notice">
* You must replace <code>28</code> with your monitor ID.
</aside>

### Parameters

Parameter | Require|  Default | Description
--------- | ------- | ------- | -----------
access_token|true | false | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization
location_id|true|  | Location ID
monitor_id|true|| Monitor ID


# Readings

## Get All Data


```ruby
require 'rest-client'

content = RestClient.get 'http://example.com/v2/readings',
  {params: {access_token: '12345', location_id: '70', monitor_id: '12,25', begin_time: '2016-03-29 15:00:00', end_time: '2016-03-30 15:00:00'}}
```

```json
{
  "data": [
    {
      "reading_time": "2015-04-29 15:00:00",
      "pm2p5": 32,
      "tvoc": null,
      "co2": null,
      "humidity": 26
    }
  ],
  "meta": {
    "total_count": 5,
    "total_pages": 5,
    "current_page": 1,
    "last_page": false,
    "code": 10000,
    "message": "Success",
    "access_token": "30834411-f7db-486a-840b-21eb66b2699e",
    "auth_token": "348f5965-34c8-429e-a6ed-1c10e7d56d5b"
  }
}
```

Retrieves all the data of specific location or monitor.

### HTTP Request

`GET http://example.com/v2/readings`

### Parameters

Parameter | Require| Default | Description
--------- | -------| ------- | -----------
access_token | true| | Access Token.
auth_token|true||Auth Token
location_id | false|  | Location id
monitor_id|false||Monitor id
begin_time|false||Begin time for query
end_time|false||End time for query
tab|false|hour|Data type. Available Tab: hour, raw


## Get Graph Data


```ruby
require 'rest-client'

content = RestClient.get 'http://example.com/v2/readings/graph',
  {params: {access_token: '12345', location_id: '70', monitor_id: '12,25', begin_time: '2016-03-29 15:00:00', end_time: '2016-03-30 15:00:00'}}
```

```json
{
  "data": {
    "times": [
      "03/29 16:00",
      "03/29 17:00",
      "03/29 18:00",
      "03/29 19:00",
      "03/29 20:00",
      "03/29 21:00",
      "03/29 22:00",
      "03/29 23:00",
      "03/30 00:00",
      "03/30 01:00",
      "03/30 02:00",
      "03/30 03:00",
      "03/30 04:00",
      "03/30 05:00",
      "03/30 06:00",
      "03/30 07:00",
      "03/30 08:00",
      "03/30 09:00",
      "03/30 10:00",
      "03/30 11:00",
      "03/30 12:00",
      "03/30 13:00",
      "03/30 14:00",
      "03/30 15:00"
    ],
    "readings": [
      {
        "name": "RESET Testing",
        "ref_id": 70,
        "ref_name": "RESET Testing",
        "data": [
          "5.0",
          "5.0",
          "5.0",
          "6.0",
          "8.0",
          "8.0",
          "10.0",
          "8.0",
          "8.0",
          "8.0",
          "10.0",
          "10.0",
          "9.0",
          "10.0",
          "10.0",
          "8.0",
          "6.0",
          "6.0",
          "11.0",
          "8.0",
          "8.0",
          "9.0",
          "8.0",
          "8.0"
        ],
        "type": "location"
      },
      {
        "name": "上海美国领事馆/U.S. Consulate SH ",
        "ref_id": 102,
        "ref_name": "上海美国领事馆/U.S. Consulate SH ",
        "data": [
          "61.0",
          "60.0",
          "52.0",
          "56.0",
          "65.0",
          "66.0",
          "71.0",
          "71.0",
          "80.0",
          "100.0",
          "104.0",
          "103.0",
          "100.0",
          "94.0",
          "82.0",
          "66.0",
          "60.0",
          "63.0",
          "62.0",
          "65.0",
          "67.0",
          "66.0",
          "67.0",
          "67.0"
        ],
        "type": "outdoor_location"
      },
      {
        "name": "Particulate Matter",
        "ref_id": "12",
        "ref_name": "30227",
        "data": [
          "43.0",
          "43.0",
          "42.0",
          "43.0",
          "44.0",
          "47.0",
          "47.0",
          "46.0",
          "43.0",
          "40.0",
          "36.0",
          "33.0",
          "30.0",
          "28.0",
          "27.0",
          "28.0",
          "29.0",
          "38.0",
          "44.0",
          "37.0",
          "34.0",
          "38.0",
          "38.0",
          "37.0"
        ],
        "type": "monitor"
      },
      {
        "name": "Year 1 Indoor Play Area",
        "ref_id": "25",
        "ref_name": "ACCF232C4754",
        "data": [
          "9.0",
          "8.0",
          "8.0",
          "8.0",
          "35.0",
          "9.0",
          "15.0",
          "17.0",
          "17.0",
          "16.0",
          "16.0",
          "16.0",
          "16.0",
          "15.0",
          "14.0",
          "14.0",
          "55.0",
          "20.0",
          "15.0",
          "13.0",
          "13.0",
          "13.0",
          "13.0",
          "12.0"
        ],
        "type": "monitor"
      }
    ]
  },
  "meta": {
    "location_id": "70",
    "monitor_id": [
      "12",
      "25"
    ],
    "begin_time": "2016-03-29T15:33:07.627+08:00",
    "end_time": "2016-03-30T15:00:00.000+08:00",
    "indicator": "pm2p5"
  }
}
```

Retrieves all the average readings of specific location or monitor for graph.

### HTTP Request

`GET http://example.com/v2/readings/graph`

### Parameters

Parameter | Require| Default | Description
--------- | -------| ------- | -----------
access_token | true| | Access Token.
auth_token|true||Auth Token
location_id | false|  | Location id
monitor_id|false||Monitor id, use comma if more than one, eg: 12,25
indicator|false|pm2p5|Available indicators: pm2p5, pm10, co2, co, tvoc, hcho, humidity, temperature. Use comma if more than one.
begin_time|false|Time.now - 1.day|Begin time for query
end_time|false|Time.now|End time for query

# Changelog

## 2016-04-11
Status|Api|Content|
 -------| ------- | -----------
Updated|/v2/locations/{location_id}|new parameter for unlock_token
Added|/v2/locations/{location_id}/unlock|new api for unlocking location
Added|/v2/readings|new api for all readings

