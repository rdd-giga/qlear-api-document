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


## Create Location


```ruby


content = RestClient.post 'https://example.com/v2/locations',
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

`POST https://example.com/v2/locations`

### Parameters

Parameter | Require|  Default | Description
--------- | ------- | ------- | -----------
access_token|true | false | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization
active|false|true|
client_id|true||Workspace, Owner or Client
name|true||Location Name
category|true|indoor| indoor or outdoor
city_id|true||City ID
time_zone|false||TimeZone
outdoor_location_id|false||Compared Outdoor ID
theme|false||Location Theme
logo|false||Location Logo


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
  "meta": {
    "code": 10000,
    "message": "Success",
    "access_token": "30834411-f7db-486a-840b-21eb66b2699e",
    "auth_token": "348f5965-34c8-429e-a6ed-1c10e7d56d5b"
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
  "meta": {
    "code": 10000,
    "message": "Success",
    "access_token": "30834411-f7db-486a-840b-21eb66b2699e",
    "auth_token": "348f5965-34c8-429e-a6ed-1c10e7d56d5b"
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