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