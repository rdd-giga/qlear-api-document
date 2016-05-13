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