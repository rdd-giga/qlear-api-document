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