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
page|false|1|Page number
size|false|20|Size per page
name|true||Name
contact|false||Contact
mobile|false||Mobile

## Get Client Details


```ruby


content = RestClient.get 'https://example.com/v2/clients/1',
  {params: {access_token: '12345', auth_token: '', client_id: ''}}
```

```json
{
  "data": {
    "id": 1,
    "code": null,
    "name": "Test Client",
    "description": "Hello guys!",
    "contact": "Martin",
    "tel": "021-50891119",
    "mobile": "15921367849",
    "email": "martin.xus@gmail.com",
    "address": "Shanghai"
  },
  "meta": {
    "code": 10000,
    "message": "Success",
    "access_token": "30834411-f7db-486a-840b-21eb66b2699e",
    "auth_token": null
  }
}
```

Get client details.

### HTTP Request

`GET https://example.com/v2/clients/1`

### Parameters

Parameter | Require| Default | Description
--------- | -------| ------- | -----------
access_token | true| | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization
client_id |true|  | Client ID

## Create Client


```ruby


content = RestClient.post 'https://example.com/v2/clients',
  {params: {access_token: '', auth_token: ''}}
```

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

Create new client.

### HTTP Request

`POST https://example.com/v2/clients`

### Parameters

Parameter | Require| Default | Description
--------- | -------| ------- | -----------
access_token | true| | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization
name|true||Name
description|false||Description
contact|false||Contact
mobile|false||Mobile
email|false||Email
tel|false||Tel
address|false||Address
active_time|false||Active Time


## Update Client


```ruby


content = RestClient.patch 'https://example.com/v2/clients/1',
  {params: {access_token: '', auth_token: ''}}
```

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

Update client

### HTTP Request

`PATCH https://example.com/v2/clients/1`

### Parameters

Parameter | Require| Default | Description
--------- | -------| ------- | -----------
access_token | true| | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization
client_id |true|  | Client ID
name|true||Name
description|false||Description
contact|false||Contact
mobile|false||Mobile
email|false||Email
tel|false||Tel
address|false||Address
active_time|false||Active Time

## Destroy Client


```ruby


content = RestClient.delete 'https://example.com/v2/clients/1',
  {params: {access_token: '', auth_token: ''}}
```

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

Destroy client

### HTTP Request

`DELETE https://example.com/v2/clients/1`

### Parameters

Parameter | Require| Default | Description
--------- | -------| ------- | -----------
access_token | true| | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization
client_id |true|  | Client ID


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