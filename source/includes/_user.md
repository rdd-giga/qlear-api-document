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

Get dashboard

### HTTP Request

`GET https://example.com/v2/users/dashboard`

### Parameters

Parameter | Require| Default | Description
--------- | -------| ------- | -----------
access_token | true| | Access Token.
auth_token|true||Auth Token
locale | false| en | Localization