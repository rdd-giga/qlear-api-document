# Account

## Get All Accounts

```ruby

content = RestClient.get 'https://example.com/v2/accounts',
  {params: {access_token: '', auth_token: ''}}
```

```json
{
  "data": [
    {
      "id": 1,
      "email": "demo@gmail.com",
      "name": "josh",
      "category": "client"
    }
  ],
  "meta": {
    "total_count": 55,
    "total_pages": 3,
    "current_page": 1,
    "last_page": false,
    "code": 10000,
    "message": "Success",
    "access_token": "30834411-f7db-486a-840b-21eb66b2699e",
    "auth_token": "348f5965-34c8-429e-a6ed-1c10e7d56d5b"
  }
}
```

Get all accounts
### HTTP Request

`GET https://example.com/v2/accounts`

### Parameters

Parameter | Require|  Default | Description
--------- | ------- | ------- | -----------
access_token|true | false | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization
all|false||Set true, if you want to load all accounts
client_id|false||Client ID
email|false||Email
category|false||User Type, manager, client or user
page|false|1|Page number
size|false|20|Size per page


## Account Detail

```ruby

content = RestClient.get 'https://example.com/v2/accounts/{account_id}',
  {params: {access_token: '', auth_token: '', account_id: ''}}
```

```
{
  "data": {
    "id": 1,
    "email": "joshuaballoch@gmail.com",
    "first_name": "Joshua",
    "last_name": "Balloch",
    "auth_token": "d2cf538d-38f1-4514-a9b3-2cacae3fae74",
    "user_name": "josh",
    "mobile": null,
    "category": "client",
    "client_id": null,
    "sign_in_count": 77,
    "current_sign_in_at": "2014-11-14 03:37:39",
    "last_sign_in_at": "2014-11-04 11:19:55",
    "current_sign_in_ip": "74.71.179.183",
    "last_sign_in_ip": "74.71.179.183",
    "timezone": "Asia/Shanghai",
    "created_at": "2014-04-27 12:10:14"
  },
  "meta": {
    "code": 10000,
    "message": "Success",
    "access_token": "30834411-f7db-486a-840b-21eb66b2699e",
    "auth_token": "348f5965-34c8-429e-a6ed-1c10e7d56d5b"
  }
}
```

Account detail
### HTTP Request

`GET https://example.com/v2/accounts/1`

<aside class="notice">
* You must replace <code>1</code> with your account ID.
</aside>

### Parameters

Parameter | Require|  Default | Description
--------- | ------- | ------- | -----------
access_token|true | false | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization
account_id|true||Account ID


## Create Account

```ruby

content = RestClient.post 'https://example.com/v2/accounts/',
  {params: {access_token: '', auth_token: '', email: '', ...}}
```

```
{
  "meta": {
    "code": 10000,
    "message": "Success",
    "access_token": "30834411-f7db-486a-840b-21eb66b2699e",
    "auth_token": "348f5965-34c8-429e-a6ed-1c10e7d56d5b"
  }
}
```

Create new account
### HTTP Request

`POST https://example.com/v2/accounts`

### Parameters

Parameter | Require|  Default | Description
--------- | ------- | ------- | -----------
access_token|true | false | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization
client_id|false||Need it if qlear staff else ignore
email|true||Email
username|true||User Name
mobile|false||Mobile
first_name|false||First Name
last_name|false||Last Name
password|true||Password
category|true||User type, manager, client, user


## Update Account

```ruby

content = RestClient.patch 'https://example.com/v2/accounts/{account_id}',
  {params: {access_token: '', auth_token: '', email: '', ...}}
```

```
{
  "meta": {
    "code": 10000,
    "message": "Success",
    "access_token": "30834411-f7db-486a-840b-21eb66b2699e",
    "auth_token": "348f5965-34c8-429e-a6ed-1c10e7d56d5b"
  }
}
```

Update account
### HTTP Request

`PATCH https://example.com/v2/accounts/1`

<aside class="notice">
* You must replace <code>1</code> with your account ID.
</aside>

### Parameters

Parameter | Require|  Default | Description
--------- | ------- | ------- | -----------
access_token|true | false | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization
account_id|true||Account ID
client_id|false||Need it if qlear staff else ignore
email|true||Email
username|true||User Name
mobile|false||Mobile
first_name|false||First Name
last_name|false||Last Name
password|true||Password
category|true||User type, manager, client, user


## Destroy Account

```ruby

content = RestClient.delete 'https://example.com/v2/accounts/{account_id}',
  {params: {access_token: '', auth_token: '', email: '', ...}}
```

```
{
  "meta": {
    "code": 10000,
    "message": "Success",
    "access_token": "30834411-f7db-486a-840b-21eb66b2699e",
    "auth_token": "348f5965-34c8-429e-a6ed-1c10e7d56d5b"
  }
}
```

Destroy account
### HTTP Request

`DELETE https://example.com/v2/accounts/1`

<aside class="notice">
* You must replace <code>1</code> with your account ID.
</aside>

### Parameters

Parameter | Require|  Default | Description
--------- | ------- | ------- | -----------
access_token|true | false | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization
account_id|true||Account ID
