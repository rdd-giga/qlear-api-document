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
content = RestClient.get 'https://example.com/v2/ping',
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


content = RestClient.post 'https://example.com/v2/users/sign_up',
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

`POST https://example.com/v2/users/sign_up`

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


content = RestClient.post 'https://example.com/v2/users/sign_in',
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

`POST https://example.com/v2/users/sign_in`

### Parameters

Parameter | Require| Default | Description
--------- | -------| ------- | -----------
access_token | true| | Access Token.
locale | false| en | Localization
email|true||Email
password|true||Password

## Get Profile

```ruby


content = RestClient.get 'https://example.com/v2/users/profile',
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

`GET https://example.com/v2/users/profile`

### Parameters

Parameter | Require| Default | Description
--------- | -------| ------- | -----------
access_token | true| | Access Token.
auth_token|true||Auth Token
locale | false| en | Localization

## Update Profile

```ruby


content = RestClient.post 'https://example.com/v2/users/profile',
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

`POST https://example.com/v2/users/profile`

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


content = RestClient.post 'https://example.com/v2/users/password',
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

Update password

### HTTP Request

`POST https://example.com/v2/users/password`

### Parameters

Parameter | Require| Default | Description
--------- | -------| ------- | -----------
access_token | true| | Access Token.
auth_token|true||Auth Token
locale | false| en | Localization
old_password|true||Previous Password
new_password|true||New Password


## Get Dashboard


```ruby


content = RestClient.get 'https://example.com/v2/users/dashboard',
  {params: {access_token: '', auth_token: ''}}
```

```json

{
  "data": [
    {
      "id": 102,
      "name": "上海美国领事馆/U.S. Consulate SH ",
      "city_id": 800,
      "city_name": "Shanghai",
      "station_name": "Shanghai U.S. Consulate",
      "theme": null,
      "category": "outdoor",
      "status": "sensitive",
      "reading": {
        "pm2p5": 77,
        "bto": null
      }
    },
    {
      "id": 10152,
      "name": "Cicero Outdoor",
      "city_id": 3250,
      "city_name": "Chicago",
      "station_name": "AirNow 00514",
      "theme": "https://dn-reset.qbox.me/uploads/location/theme/thumb_ee6a0f68-8ac0-4b8d-a2f5-52ad2e819c19.jpg",
      "category": "outdoor",
      "status": "good",
      "reading": {
        "bto": null
      }
    },
    {
      "id": 99,
      "name": "北京美国使馆PM 2.5/BJ US Embassy PM2.5 ",
      "city_id": 2,
      "city_name": "Beijing",
      "station_name": "美国使馆PM 2.5/US Embassy PM2.5",
      "theme": null,
      "category": "outdoor",
      "status": "moderate",
      "reading": {
        "pm2p5": 64,
        "bto": null
      }
    },
    {
      "id": 10165,
      "name": "J.D. Power",
      "city_id": 2,
      "city_name": "Beijing",
      "station_name": "Office",
      "theme": "https://dn-reset.qbox.me/uploads/location/theme/thumb_c8826704-366f-4a79-b973-0c0e3d7abd56.jpg",
      "category": "indoor",
      "status": "good",
      "reading": {
        "pm2p5": 16,
        "bto": "4.0"
      }
    }
  ],
  "meta": {
    "code": 10000,
    "message": "Success",
    "access_token": "100001",
    "auth_token": "a53a1328-dc4e-4322-85a0-f0a05f932d1a"
  }
}
```

Create new account.

### HTTP Request

`GET https://example.com/v2/users/dashboard`

### Parameters

Parameter | Require| Default | Description
--------- | -------| ------- | -----------
access_token | true| | Access Token.
auth_token|true||Auth Token
locale | false| en | Localization


# Cities

## Get All Cities


```ruby


content = RestClient.get 'https://example.com/v2/cities',
  {params: {access_token: '12345'}}
```


```shell
curl "https://example.com/v2/cities?access_token=12345"
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

`GET https://example.com/v2/cities`

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


content = RestClient.get 'https://example.com/v2/cities/activity',
  {params: {access_token: '12345'}}
```

```shell
curl "https://example.com/v2/cities/activity?access_token=12345"
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

`GET https://example.com/v2/cities/activity`

### Parameters

Parameter | Require| Default | Description
--------- | -------| ------- | -----------
access_token|true |  | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization


# Location

## Get All Locations

```ruby


content = RestClient.get 'https://example.com/v2/locations',
  {params: {access_token: '12345', per: 2, page: 2}}
```


```shell
curl "https://example.com/v2/locations?access_token=12345&per=2&page=2"
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

`GET https://example.com/v2/locations`

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
content = RestClient.get 'https://example.com/v2/location/45'
```

```shell
curl "https://example.com/v2/locations/45"
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
    "status": "stale",
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

`GET https://example.com/v2/locations/45`


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


## Update Location


```ruby


content = RestClient.patch 'https://example.com/v2/locations/45',
  {params: {access_token: '', auth_token: ''}}
```


> Success

```json
{
  "meta": {
    "code": 10000,
    "message": "Success",
    "access_token": "30834411-f7db-486a-840b-21eb66b2699e",
    "auth_token": "348f5965-34c8-429e-a6ed-1c10e7d56d5b"
  }
}
```


Update Location

### HTTP Request

`PATCH https://example.com/v2/locations/45`

### Parameters

Parameter | Require|  Default | Description
--------- | ------- | ------- | -----------
access_token|true | false | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization
location_id|true|  | Location ID
tab|true|basic| basic, advanced, monitor, permission, certification
active|false|true|
client_id|true||Workspace, Owner or Client
name|true||Location Name
category|true|indoor| indoor or outdoor
city_id|true||City ID
time_zone|false||TimeZone
outdoor_location_id|false||Compared Outdoor ID
theme|false||Location Theme
logo|false||Location Logo
primary_indicator|false|pm2p5|See indicators
tvoc_unit|false|μg/m³|μg/m³ or ppm
privacy|false|false| true or false, true for lock, otherwise public
password|false||set password if location is locked
active_hours|false|false|check if need set active hours
active_hours_day_in_week|false|| Array, 0 for Sunday, 1 for Monday, and so on. [0, 1, 2, 3, 4, 5, 6]
active_hours_begin_time|false||Array, default ['0:00', '0:00', '0:00', '0:00', '0:00', '0:00', '0:00']
active_hours_end_time|false||Array, default ['23:59', '23:59', '23:59', '23:59', '23:59', '23:59', '23:59']
active_hours_enable|false|true|Array, default [true, true, true, true, true, true, true]
active_hours_close_message_en|false||message when non-acive, en
active_hours_close_message_zh|false||message when non-acive, zh-CN
average_indicator|false||Array
average_active|false|true| true for show, else hide| Visibility
monitor_id|false||Array, Monitor ID
monitor_name|false||Array
monitor_indicator|false||Array of Array, see indicators
monitor_active|false|true|true for monitor enabled, else false
permission_internal_access|false||1 for Regular, 2 for Only Admins
permission_user_id|false||Array
permission_role|false||Array, member or admin
certification_id|false||Array


## Location Staffs


```ruby


content = RestClient.get 'https://example.com/v2/locations/45/staffs',
  {params: {access_token: '', auth_token: ''}}
```


> Success

```json
{
  "data": [
    {
      "id": 7,
      "email": "indah@purelivingchina.com",
      "name": "indah@purelivingchina.com"
    }
  ],
  "meta": {
    "code": 10000,
    "message": "Success",
    "access_token": "30834411-f7db-486a-840b-21eb66b2699e",
    "auth_token": null
  }
}
```


Get staffs

### HTTP Request

`GET https://example.com/v2/locations/45/staffs`

### Parameters

Parameter | Require|  Default | Description
--------- | ------- | ------- | -----------
access_token|true | false | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization
location_id|true|  | Location ID


## Location Certifications


```ruby


content = RestClient.get 'https://example.com/v2/locations/45/certifications',
  {params: {access_token: '', auth_token: ''}}
```


> Success

```json
{
  "data": [
    {
      "id": 1,
      "name": "Reset",
      "logo": "https://dn-reset.qbox.me/uploads/certification/logo/584a8923-0372-468f-9e42-1884ce41a3b5.png"
    }
  ],
  "meta": {
    "code": 10000,
    "message": "Success",
    "access_token": "30834411-f7db-486a-840b-21eb66b2699e",
    "auth_token": null
  }
}
```


Get certifications

### HTTP Request

`GET https://example.com/v2/locations/45/certifications`

### Parameters

Parameter | Require|  Default | Description
--------- | ------- | ------- | -----------
access_token|true | false | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization
location_id|true|  | Location ID

## Add Following


```ruby


content = RestClient.post 'https://example.com/v2/followings',
  {params: {access_token: '', auth_token: '', location_id: ''}}
```


> Success

```json
{
  "meta": {
    "code": 10000,
    "message": "Success",
    "access_token": "30834411-f7db-486a-840b-21eb66b2699e",
    "auth_token": "348f5965-34c8-429e-a6ed-1c10e7d56d5b"
  }
}
```


Follow

### HTTP Request

`POST https://example.com/v2/followings`

### Parameters

Parameter | Require|  Default | Description
--------- | ------- | ------- | -----------
access_token|true | false | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization
location_id|true|  | Location ID


## Destroy Following


```ruby


content = RestClient.delete 'https://example.com/v2/followings/{location_id}',
  {params: {access_token: '', auth_token: '', location_id: ''}}
```


> Success

```json
{
  "meta": {
    "code": 10000,
    "message": "Success",
    "access_token": "30834411-f7db-486a-840b-21eb66b2699e",
    "auth_token": "348f5965-34c8-429e-a6ed-1c10e7d56d5b"
  }
}
```


Unfollow

### HTTP Request

`DELETE https://example.com/v2/followings/{location_id}`

### Parameters

Parameter | Require|  Default | Description
--------- | ------- | ------- | -----------
access_token|true | false | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization
location_id|true|  | Location ID

## Get All Monitor

```ruby


content = RestClient.get 'https://example.com/v2/locations/48/monitors',
  {params: {access_token: '12345'}}
```

```json
{
  "data": [
    {
      "id": 2848,
      "name": "3rd Floor",
      "identifier": "IPM251546036",
      "label": "3rd Floor ",
      "logo": null,
      "device_type": "air_assure",
      "status": "ok",
      "follow": false,
      "indicator": [
        "pm2p5"
      ],
      "last_reading_time": "2016-04-12 11:20:31",
      "last_received_at": "2016-04-12 11:20:31",
      "reading": [
        {
          "indicator": "pm2p5",
          "name": "PM 2.5",
          "unit": "μg/m³",
          "value": 9,
          "level": "good"
        }
      ]
    },
    {
      "id": 2847,
      "name": "4th Floor",
      "identifier": "IPM251546018",
      "label": "4th Floor ",
      "logo": null,
      "device_type": "air_assure",
      "status": "ok",
      "follow": false,
      "indicator": [
        "pm2p5"
      ],
      "last_reading_time": "2016-04-12 11:20:33",
      "last_received_at": "2016-04-12 11:20:33",
      "reading": [
        {
          "indicator": "pm2p5",
          "name": "PM 2.5",
          "unit": "μg/m³",
          "value": 16,
          "level": "good"
        }
      ]
    },
    {
      "id": 2849,
      "name": "7th Floor",
      "identifier": "IPM251546040",
      "label": "7th Floor ",
      "logo": null,
      "device_type": "air_assure",
      "status": "ok",
      "follow": false,
      "indicator": [
        "pm2p5"
      ],
      "last_reading_time": "2016-04-12 11:23:51",
      "last_received_at": "2016-04-12 11:23:52",
      "reading": [
        {
          "indicator": "pm2p5",
          "name": "PM 2.5",
          "unit": "μg/m³",
          "value": 16,
          "level": "good"
        }
      ]
    }
  ],
  "meta": {
    "code": 10000,
    "message": "Success",
    "access_token": "eb98298f-fc85-49b9-ae6c-322bab7ad7b4"
  }
}
```

Get all monitors of the current location
### HTTP Request

`GET https://example.com/v2/locations/45/monitors`

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


## Get Monitor's Detail

```ruby


content = RestClient.get 'https://example.com/v2/locations',
  {params: {access_token: '12345', location_id: 45, monitor_id: 28}}
```


```shell
curl "https://example.com/v2/locations/45/monitors/28?access_token=12345"
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
    "status": "stale",
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

`GET https://example.com/v2/locations/45/monitors/28`

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


content = RestClient.post 'https://example.com/v2/locations/45/unlock',
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
    "status": "stale",
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

`POST https://example.com/v2/locations/45/unlock`

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

## Get Sharings


```ruby


content = RestClient.get 'https://example.com/v2/locations/28/sharings',
  {params: {access_token: '12345'}}
```


```json
{
  "data": [
    {
      "id": 2,
      "client_id": 11,
      "client_name": "This is Test Client, Test Again",
      "permission": "read_only"
    },
    {
      "id": 3,
      "client_id": 12,
      "client_name": "This is Test Client, Test Again1",
      "permission": "read_only"
    },
    {
      "id": 4,
      "client_id": 7,
      "client_name": "111",
      "permission": "full_access"
    }
  ],
  "meta": {
    "code": 10000,
    "message": "Success",
    "access_token": "30834411-f7db-486a-840b-21eb66b2699e",
    "auth_token": "348f5965-34c8-429e-a6ed-1c10e7d56d5b"
  }
}
```

Get shared locations

### HTTP Request

`GET https://example.com/v2/locations/28/sharings`

<aside class="notice">
* You must replace <code>28</code> with your location ID.
</aside>

### Parameters

Parameter | Require|  Default | Description
--------- | ------- | ------- | -----------
access_token|true | false | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization
location_id|true|  | Location ID

## Add Sharing


```ruby


content = RestClient.post 'https://example.com/v2/locations/28/sharings',
  {params: {access_token: '12345', auth_token: '', code: 'TITCTA-6H3J02D0', permission: 'read_only'}}
```


> Success

```json
{
  "meta": {
    "code": 10000,
    "message": "Success",
    "access_token": "30834411-f7db-486a-840b-21eb66b2699e",
    "auth_token": "348f5965-34c8-429e-a6ed-1c10e7d56d5b"
  }
}
```
> Or failure


```json
{
  "meta": {
    "code": 10024,
    "message": "Already shared",
    "access_token": "30834411-f7db-486a-840b-21eb66b2699e",
    "auth_token": "348f5965-34c8-429e-a6ed-1c10e7d56d5b"
  }
}
```

Share location to other client.

### HTTP Request

`POST https://example.com/v2/locations/28/sharings`

<aside class="notice">
* You must replace <code>28</code> with your location ID.
</aside>

### Parameters

Parameter | Require|  Default | Description
--------- | ------- | ------- | -----------
access_token|true | false | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization
location_id|true|  | Location ID
code|true||Workspace(Client) Code
permission|true||read_only for full_access

## Destroy Sharing


```ruby

content = RestClient.delete 'https://example.com/v2/locations/28/sharings/{id}',
  {params: {access_token: '12345', auth_token: '', id: ''}}
```


> Success

```json
{
  "meta": {
    "code": 10000,
    "message": "Success",
    "access_token": "30834411-f7db-486a-840b-21eb66b2699e",
    "auth_token": "348f5965-34c8-429e-a6ed-1c10e7d56d5b"
  }
}
```

Destroy the shared location

### HTTP Request

`DELETE https://example.com/v2/locations/28/sharings/{id}`

<aside class="notice">
* You must replace <code>28</code> with your location ID.
</aside>

### Parameters

Parameter | Require|  Default | Description
--------- | ------- | ------- | -----------
access_token|true | false | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization
location_id|true|  | Location ID
id|true||Shared Location Id


## Get Notifications


```ruby

content = RestClient.get 'https://example.com/v2/locations/28/notifications',
  {params: {access_token: '12345', auth_token: ''}}
```


> Success

```json
{
  "data": {
    "stale_check": false,
    "over_repeat_check": false,
    "frequency": 3,
    "limit_rules": [
      {
        "indicator": "pm2p5",
        "type": "min",
        "value": 100
      },
      {
        "indicator": "hcho",
        "type": "max",
        "value": 200
      }
    ],
    "compare_rules": [
      {
        "indicator": "pm2p5",
        "value": 90,
        "min_value": 5
      },
      {
        "indicator": "hcho",
        "value": 85,
        "min_value": 40
      }
    ]
  },
  "meta": {
    "code": 10000,
    "message": "Success",
    "access_token": "30834411-f7db-486a-840b-21eb66b2699e",
    "auth_token": "348f5965-34c8-429e-a6ed-1c10e7d56d5b"
  }
}
```

GET notifications

### HTTP Request

`GET https://example.com/v2/locations/28/notifications`

<aside class="notice">
* You must replace <code>28</code> with your location ID.
</aside>

### Parameters

Parameter | Require|  Default | Description
--------- | ------- | ------- | -----------
access_token|true | false | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization
location_id|true|  | Location ID


## Create/Update Notifications


```ruby

content = RestClient.post 'https://example.com/v2/locations/28/notifications',
  {params: {access_token: '12345', auth_token: ''}}
```


> Success

```json
{
  "meta": {
    "code": 10000,
    "message": "Success",
    "access_token": "30834411-f7db-486a-840b-21eb66b2699e",
    "auth_token": "348f5965-34c8-429e-a6ed-1c10e7d56d5b"
  }
}
```

Create or update notifications

### HTTP Request

`POST https://example.com/v2/locations/28/notifications`

<aside class="notice">
* You must replace <code>28</code> with your location ID.
</aside>

### Parameters

Parameter | Require|  Default | Description
--------- | ------- | ------- | -----------
access_token|true | false | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization
location_id|true|  | Location ID
stale_check|false|| true or false
over_repeat_check|false||true or false
frequency|false||1 for Every Hour, 2 for Every 6 Hours, 3 for Every Day
limit_value|false||Array
limit_type|false||Array
limit_indicator|false||Array
compare_value|false||Array
compare_min_value|false||Array
compare_indicator|false||Array



# Monitor
## Get Monitor's Detail

```ruby


content = RestClient.get 'https://example.com/v2/monitors/28',
  {params: {access_token: '12345'}}
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
    "status": "stale",
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

`GET https://example.com/v2/monitors/28`

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


## Update Monitor

```ruby
content = RestClient.post 'https://example.com/v2/monitors/28',
  {params: {access_token: '12345'}}
```

> Success

```json
{
  "meta": {
    "code": 10000,
    "message": "Success",
    "access_token": "30834411-f7db-486a-840b-21eb66b2699e",
    "auth_token": "27148262-96bd-4608-8d7d-8afb8de7ffb2"
  }
}
```

> Or failure


```json
{
  "meta": {
    "code": 10050,
    "message": "Identifier has already been taken",
    "access_token": "30834411-f7db-486a-840b-21eb66b2699e",
    "auth_token": "27148262-96bd-4608-8d7d-8afb8de7ffb2"
  }
}
```

Update monitor

### HTTP Request

`POST https://example.com/v2/monitors/28`

<aside class="notice">
* You must replace <code>28</code> with your monitor ID.
</aside>

### Parameters

Parameter | Require|  Default | Description
--------- | ------- | ------- | -----------
access_token|true | false | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization
monitor_id|true|| Monitor ID
identifier|false||Identifier
label|false||Label
device_type|false||Device Type
status|false||1 or 0, 1 for active
client_id|false||Only available for QLEAR staff
lat|false||Latitude
lng|false||Longitude
note|false||Only available for QLEAR staff
logo|false||Image for monitor
batch_reading|false|false|Only for oxford

## Add Following


```ruby


content = RestClient.post 'https://example.com/v2/followings',
  {params: {access_token: '', auth_token: '', location_id: '', monitor_id: ''}}
```


> Success

```json
{
  "meta": {
    "code": 10000,
    "message": "Success",
    "access_token": "30834411-f7db-486a-840b-21eb66b2699e",
    "auth_token": "348f5965-34c8-429e-a6ed-1c10e7d56d5b"
  }
}
```


Follow

### HTTP Request

`POST https://example.com/v2/followings`

### Parameters

Parameter | Require|  Default | Description
--------- | ------- | ------- | -----------
access_token|true | false | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization
location_id|true|  | Location ID
monitor_id|true||Monitor ID


## Destroy Following


```ruby


content = RestClient.delete 'https://example.com/v2/followings/{location_id}',
  {params: {access_token: '', auth_token: '', location_id: '', monitor_id: ''}}
```


> Success

```json
{
  "meta": {
    "code": 10000,
    "message": "Success",
    "access_token": "30834411-f7db-486a-840b-21eb66b2699e",
    "auth_token": "348f5965-34c8-429e-a6ed-1c10e7d56d5b"
  }
}
```


Unfollow

### HTTP Request

`DELETE https://example.com/v2/followings/{location_id}`

### Parameters

Parameter | Require|  Default | Description
--------- | ------- | ------- | -----------
access_token|true | false | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization
location_id|true|  | Location ID
monitor_id|true||Monitor ID


## Get Calibrations

```ruby
content = RestClient.get 'https://example.com/v2/monitors/28/calibrations',
  {params: {access_token: '12345', auth_token: ''}}
```

> Success

```json
{
  "data": [
    {
      "indicator": "hcho",
      "calibration": {
        "formula": "y = a*(x**5) + b*(x**4) + c*(x**3) + d*(x**2) + e*x + f",
        "calibration_id": 292,
        "factors": [
          {
            "factor_id": 303,
            "start_value": 1,
            "end_value": 20,
            "config": "a:1.0,  b:1.0,  c:1.0,  d:1.0,  e:1.0,  f:0.0"
          }
        ]
      }
    },
    {
      "indicator": "co2",
      "calibration": {
        "formula": "y = a*x + b",
        "calibration_id": 293,
        "factors": [
          {
            "factor_id": 304,
            "start_value": 1,
            "end_value": 4,
            "config": "a:1.0,  b:0.0"
          }
        ]
      }
    },
    {
      "indicator": "tvoc",
      "calibration": null
    },
    {
      "indicator": "pm2p5",
      "calibration": null
    },
    {
      "indicator": "pm10",
      "calibration": null
    },
    {
      "indicator": "temperature",
      "calibration": {
        "formula": "y = a*x + b",
        "calibration_id": 290,
        "factors": [
          {
            "factor_id": 301,
            "start_value": -1,
            "end_value": -1,
            "config": "a:1.0,  b:-0.35"
          }
        ]
      }
    },
    {
      "indicator": "humidity",
      "calibration": {
        "formula": "y = a*x + b",
        "calibration_id": 291,
        "factors": [
          {
            "factor_id": 302,
            "start_value": -1,
            "end_value": -1,
            "config": "a:1.0,  b:1.0"
          }
        ]
      }
    }
  ],
  "meta": {
    "code": 10000,
    "message": "Success",
    "access_token": "30834411-f7db-486a-840b-21eb66b2699e",
    "auth_token": "348f5965-34c8-429e-a6ed-1c10e7d56d5b"
  }
}
```

Get all calibrations for specific monitor

### HTTP Request

`GET https://example.com/v2/monitors/28/calibrations`

<aside class="notice">
* You must replace <code>28</code> with your monitor ID.
</aside>

### Parameters

Parameter | Require|  Default | Description
--------- | ------- | ------- | -----------
access_token|true | false | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization
monitor_id|true|| Monitor ID


## Update Calibration

```ruby
content = RestClient.post 'https://example.com/v2/monitors/28',
  {params: {access_token: '12345', indicator: 'pm2p5', start_value: [-1, 20], end_value: [20, 50], factors: ['a:1, b:2', 'a:1, b:3']}}
```

> Success

```json
{
  "meta": {
    "code": 10000,
    "message": "Success",
    "access_token": "30834411-f7db-486a-840b-21eb66b2699e",
    "auth_token": "27148262-96bd-4608-8d7d-8afb8de7ffb2"
  }
}
```

Update monitor

### HTTP Request

`POST https://example.com/v2/monitors/28/calibrations`

<aside class="notice">
* You must replace <code>28</code> with your monitor ID.
</aside>

### Parameters

Parameter | Require|  Default | Description
--------- | ------- | ------- | -----------
access_token|true | false | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization
monitor_id|true|| Monitor ID
formula|true||Formula
indicator|true||Indicator
start_value|true||Array
end_value|true||Array
factors|true||Array


## Destory Calibration

```ruby
content = RestClient.delete 'https://example.com/v2/monitors/28/calibrations/{factor_id}',
  {params: {access_token: '12345', calibration_id: ''}}
```

> Success

```json
{
  "meta": {
    "code": 10000,
    "message": "Success",
    "access_token": "30834411-f7db-486a-840b-21eb66b2699e",
    "auth_token": "27148262-96bd-4608-8d7d-8afb8de7ffb2"
  }
}
```



Update monitor

### HTTP Request

`DELETE https://example.com/v2/monitors/28/calibrations/{factor_id}`

<aside class="notice">
* You must replace <code>28</code> with your monitor ID.
</aside>

### Parameters

Parameter | Require|  Default | Description
--------- | ------- | ------- | -----------
access_token|true | false | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization
monitor_id|true|| Monitor ID
calibration_id|true||Calibration ID
factor_id|true||Factor ID


# Readings

## Get All Data


```ruby


content = RestClient.get 'https://example.com/v2/readings',
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

`GET https://example.com/v2/readings`

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
page|false|1|Page number
size|false|20|Size per page


## Get Graph Data


```ruby


content = RestClient.get 'https://example.com/v2/readings/graph',
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

`GET https://example.com/v2/readings/graph`

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

# History

## Get All Histories


```ruby


content = RestClient.get 'https://example.com/v2/histories',
  {params: {access_token: '12345', location_id: '70', monitor_id: '12'}}
```

```json
{
  "data": [
    {
      "user_name": "Martin Xu",
      "created_at": "2015-08-11 11:02:51",
      "target": "certification",
      "event": "create",
      "changes": "{:id=>[\"1\"], :name=>[\"Reset\"]}"
    },
    ...
  ],
  "meta": {
    "total_count": 70,
    "total_pages": 4,
    "current_page": 1,
    "last_page": false,
    "code": 10000,
    "message": "Success",
    "access_token": "30834411-f7db-486a-840b-21eb66b2699e"
  }
}
```

Get histories of location or monitor.

### HTTP Request

`GET https://example.com/v2/histories`

### Parameters

Parameter | Require| Default | Description
--------- | -------| ------- | -----------
access_token | true| | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization
location_id | true|  | Location id
monitor_id|false||Monitor id
begin_time|false||Begin time for query
end_time|false||End time for query
page|false|1|Page number
size|false|20|Size per page

# Client

## Get All Clients


```ruby


content = RestClient.get 'https://example.com/v2/clients',
  {params: {access_token: '12345', auth_token: ''}}
```

```json
{
  "data": [
    {
      "id": 1,
      "code": "TC-R1RA",
      "name": "Test Client",
      "description": "Hello guys!",
      "contact": "Martin",
      "tel": "021-50891119",
      "mobile": "15921367849",
      "email": "test@gmail.com",
      "address": "Shanghai",
      "logo": null
    }
  ],
  "meta": {
    "code": 10000,
    "message": "Success",
    "access_token": "30834411-f7db-486a-840b-21eb66b2699e",
    "auth_token": ""
  }
}
```

Get all clients.

### HTTP Request

`GET https://example.com/v2/clients`

### Parameters

Parameter | Require| Default | Description
--------- | -------| ------- | -----------
access_token | true| | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization

## Get Users


```ruby


content = RestClient.get 'https://example.com/v2/clients/{client_id}/users',
  {params: {access_token: '12345', auth_token: ''}}
```

```json
{
  "data": [
    {
      "id": 15,
      "email": "test@gigabase.org",
      "name": "Martin Xu"
    }
  ],
  "meta": {
    "code": 10000,
    "message": "Success",
    "access_token": "30834411-f7db-486a-840b-21eb66b2699e",
    "auth_token": null
  }
}
```

Get all clients.

### HTTP Request

`GET https://example.com/v2/clients/{client_id}/users`

### Parameters

Parameter | Require| Default | Description
--------- | -------| ------- | -----------
access_token | true| | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization
client_id |true|  | Client ID


# Dictionary

## Certifications


```ruby
content = RestClient.get 'https://example.com/v2/dictionaries/certifications',
  {params: {access_token: '12345', auth_token: ''}}
```

> Success

```json
{
  "data": [
    {
      "id": 1,
      "name": "Reset",
      "logo": "https://dn-reset.qbox.me/uploads/certification/logo/584a8923-0372-468f-9e42-1884ce41a3b5.png"
    }
  ],
  "meta": {
    "code": 10000,
    "message": "Success",
    "access_token": "30834411-f7db-486a-840b-21eb66b2699e",
    "auth_token": null
  }
}

```

Get all certifications

### HTTP Request

`GET https://example.com/v2/dictionaries/certifications`

### Parameters

Parameter | Require|  Default | Description
--------- | ------- | ------- | -----------
access_token|true | false | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization

## Formulas

```ruby
content = RestClient.get 'https://example.com/v2/dictionaries/formulas',
  {params: {access_token: '12345', indicator: 'pm2p5'}}
```

> Success

```json
{
  "data": [
    "y = a*x + b",
    "y = a*(x+b) + c",
    "y = a*(x**5) + b*(x**4) + c*(x**3) + d*(x**2) + e*x + f"
  ],
  "meta": {
    "code": 10000,
    "message": "Success",
    "access_token": "30834411-f7db-486a-840b-21eb66b2699e",
    "auth_token": null
  }
}

```

Get all formulas for specifical indicator

### HTTP Request

`GET https://example.com/v2/dictionaries/formulas`

### Parameters

Parameter | Require|  Default | Description
--------- | ------- | ------- | -----------
access_token|true | false | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization
indicator|false|| Indicator


## Time Zones

```ruby
content = RestClient.get 'https://example.com/v2/dictionaries/time_zones',
  {params: {access_token: '12345'}}
```

> Success

```json
{
  "data": {
    "+0": [
      "Africa/Abidjan",
      "Africa/Accra",
    ],
    "+8": [
      "Antarctica/Casey",
      "Asia/Brunei",
      "Asia/Chita",
      "Asia/Choibalsan",
      "Asia/Hong_Kong",
      "Asia/Irkutsk",
      "Asia/Kuala_Lumpur",
      "Asia/Kuching",
      "Asia/Macau",
      "Asia/Makassar",
      "Asia/Manila",
      "Asia/Shanghai",
      "Asia/Singapore",
      "Asia/Taipei",
      "Asia/Ulaanbaatar",
      "Australia/Perth"
    ]
  },
  "meta": {
    "code": 10000,
    "message": "Success",
    "access_token": "30834411-f7db-486a-840b-21eb66b2699e",
    "auth_token": "27148262-96bd-4608-8d7d-8afb8de7ffb2"
  }
}

```

Get all time zones

### HTTP Request

`GET https://example.com/v2/dictionaries/time_zones`

### Parameters

Parameter | Require|  Default | Description
--------- | ------- | ------- | -----------
access_token|true | false | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization


## Indicators

```ruby
content = RestClient.get 'https://example.com/v2/dictionaries/indicators',
  {params: {access_token: '12345'}}
```

> Success

```json
{
  "data": {
    "pm2p5": "PM 2.5",
    "hcho": "HCHO",
    "co": "CO",
    "co2": "CO2",
    "tvoc": "Total VOC",
    "pm10": "PM 10",
    "temperature": "Temperature",
    "humidity": "Humidity"
  },
  "meta": {
    "code": 10000,
    "message": "Success",
    "access_token": "30834411-f7db-486a-840b-21eb66b2699e",
    "auth_token": null
  }
}

```

Get all indicators

### HTTP Request

`GET https://example.com/v2/dictionaries/indicators`

### Parameters

Parameter | Require|  Default | Description
--------- | ------- | ------- | -----------
access_token|true | false | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization



## Monitor Types

```ruby
content = RestClient.get 'https://example.com/v2/dictionaries/monitor_types',
  {params: {access_token: '12345'}}
```

> Success

```json
{
  "data": {
    "fluke": "Fluke",
    "air_advice": "Air advice",
    "us_embassy": "Us embassy",
    "env_monitor": "Env monitor",
    "particles_plus": "Particles plus",
    "china_government": "China government",
    "ion_science": "Ion science",
    "air_assure": "Air assure",
    "net_work": "Net work",
    "laser_egg": "Laser egg",
    "dst": "Dst",
    "tondy": "Tondy"
  },
  "meta": {
    "code": 10000,
    "message": "Success",
    "access_token": "30834411-f7db-486a-840b-21eb66b2699e",
    "auth_token": "27148262-96bd-4608-8d7d-8afb8de7ffb2"
  }
}
```

Get all types of monitor

### HTTP Request

`GET https://example.com/v2/dictionaries/monitor_types`

### Parameters

Parameter | Require|  Default | Description
--------- | ------- | ------- | -----------
access_token|true | false | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization

## Cities

```ruby
content = RestClient.get 'https://example.com/v2/dictionaries/cities',
  {params: {access_token: '12345'}}
```

> Success

```json
{
  "data": {
    "2": "北京",
    "800": "上海",
    "864": "苏州",
    "3238": "香港"
  },
  "meta": {
    "code": 10000,
    "message": "Success",
    "access_token": "30834411-f7db-486a-840b-21eb66b2699e",
    "auth_token": "27148262-96bd-4608-8d7d-8afb8de7ffb2"
  }
}

```

Get all cities

### HTTP Request

`GET https://example.com/v2/dictionaries/cities`

### Parameters

Parameter | Require|  Default | Description
--------- | ------- | ------- | -----------
access_token|true | false | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization



## Workspaces

```ruby
content = RestClient.get 'https://example.com/v2/dictionaries/workspaces',
  {params: {access_token: '12345', auth_token: '...'}}
```

> Success

```json
{
  "data": {
    "1": "Test Client",
    "2": "abc"
  },
  "meta": {
    "code": 10000,
    "message": "Success",
    "access_token": "30834411-f7db-486a-840b-21eb66b2699e",
    "auth_token": "27148262-96bd-4608-8d7d-8afb8de7ffb2"
  }
}

```

Get all workspaces

### HTTP Request

`GET https://example.com/v2/dictionaries/workspaces`

### Parameters

Parameter | Require|  Default | Description
--------- | ------- | ------- | -----------
access_token|true | false | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization


## Monitors

```ruby
content = RestClient.get 'https://example.com/v2/dictionaries/monitors',
  {params: {access_token: '12345', auth_token: '....'}}
```

> Success

```json
{
  "data": [
    "2": "10",
    "3": "12.34.56.92",
    "4": "12.34.56.93 (12.34.56.93)",
    "6": "30218 (PM 2.5)",
    "7": "30217 (30217)",
    "8": "30221 (Room D109)",
    "9": "30181 (30181)",
    "10": "30170 (Primary Library)",
    "11": "30233"
  ],
  "meta": {
    "code": 10000,
    "message": "Success",
    "access_token": "30834411-f7db-486a-840b-21eb66b2699e",
    "auth_token": null
  }
}

```

Get all monitors

### HTTP Request

`GET https://example.com/v2/dictionaries/monitors`

### Parameters

Parameter | Require|  Default | Description
--------- | ------- | ------- | -----------
access_token|true | false | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization



## Outdoors

```ruby
content = RestClient.get 'https://example.com/v2/dictionaries/outdoors',
  {params: {access_token: '12345', auth_token: '....'}}
```

> Success

```json
{
  "data": {
    "88": "Martin's Loction"
  },
  "meta": {
    "code": 10000,
    "message": "Success",
    "access_token": "30834411-f7db-486a-840b-21eb66b2699e",
    "auth_token": "27148262-96bd-4608-8d7d-8afb8de7ffb2"
  }
}

```

Get all outdoor locations

### HTTP Request

`GET https://example.com/v2/dictionaries/outdoors`

### Parameters

Parameter | Require|  Default | Description
--------- | ------- | ------- | -----------
access_token|true | false | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization



# Changelog

## 2016-05-05

Status|Api|Content|
 -------| ------- | -----------
Added|GET /v2/locations/{location_id}/staffs|Get staffs of location
Added|GET /v2/locations/{location_id}/certifications|Get certifications of location
Added|GET /v2/clients|Get clients
Added|GET /v2/clients/{client_id}/users|Get users of the specific client
Added|PATCH /v2/locations/{location_id}|Update location


## 2016-04-28

Status|Api|Content|
 -------| ------- | -----------
Added|/v2/followings|location and monitor following
Added|/v2/locations/{location_id}/sharings|location sharing
Added|/v2/locations/{location_id}/notifications|location notification
Added|/v2/monitors/{monitor_id}/calibrations|monitor calibration

## 2016-04-20
Status|Api|Content|
 -------| ------- | -----------
Added|/v2/monitors/{monitor_id}|new api for updating monitor
Added|/v2/dictionaries/*|bunche api for dictionary


## 2016-04-12
Status|Api|Content|
 -------| ------- | -----------
Updated|/v2/monitors/{monitor_id}|rename stale to status, returned by server
Added|/v2/locations/{location_id}/monitors|new api for getting all monitors of the location
Added|/v2/histories|new api for history

## 2016-04-11

Status|Api|Content|
 -------| ------- | -----------
Updated|/v2/locations/{location_id}|new parameter for unlock_token
Added|/v2/locations/{location_id}/unlock|new api for unlocking location
Added|/v2/readings|new api for all readings

