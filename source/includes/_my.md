# My

## Get All Locations

```ruby


content = RestClient.get 'https://example.com/v2/my/locations',
  {params: {access_token: '', auth_token: '', per: 2, page: 2}}
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

Get all locations
### HTTP Request

`GET https://example.com/v2/my/locations`

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


## Get All Monitor

```ruby


content = RestClient.get 'https://example.com/v2/my/monitors',
  {params: {access_token: '', auth_token: ''}}
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

Get all monitors
### HTTP Request

`GET https://example.com/v2/my/monitors`

### Parameters

Parameter | Require|  Default | Description
--------- | ------- | ------- | -----------
access_token|true | false | Access Token.
auth_token|false||Auth Token
locale |false| en | Localization


## Get Display Settings

```ruby


content = RestClient.get 'https://example.com/v2/my/settings',
  {params: {access_token: '', auth_token: ''}}
```

```json
{
  "data": {
    "user_id": 15,
    "pm2p5_display": "aqi",
    "temp_unit": "f"
  },
  "meta": {
    "code": 10000,
    "message": "Success",
    "access_token": "30834411-f7db-486a-840b-21eb66b2699e",
    "auth_token": "348f5965-34c8-429e-a6ed-1c10e7d56d5b"
  }
}
```

Get display settings of current_user
### HTTP Request

`GET https://example.com/v2/my/settings`

### Parameters

Parameter | Require|  Default | Description
--------- | ------- | ------- | -----------
access_token|true | false | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization


## Update Display Settings

```ruby


content = RestClient.post 'https://example.com/v2/my/settings',
  {params: {access_token: '', auth_token: '', pm2p5_display: '', temp_unit: ''}}
```

```json
{
  "data": {
    "user_id": 15,
    "pm2p5_display": "aqi",
    "temp_unit": "f"
  },
  "meta": {
    "code": 10000,
    "message": "Success",
    "access_token": "30834411-f7db-486a-840b-21eb66b2699e",
    "auth_token": "348f5965-34c8-429e-a6ed-1c10e7d56d5b"
  }
}
```

Get display settings of current_user
### HTTP Request

`POST https://example.com/v2/my/settings`

### Parameters

Parameter | Require|  Default | Description
--------- | ------- | ------- | -----------
access_token|true | false | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization
pm2p5_display|false|con| con for Concentration, aqi for AQI
temp_unit|false|c| c for °C, f for °F
