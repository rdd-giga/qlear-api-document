# Download

## Get All Prepared Downloads

```ruby

content = RestClient.post 'https://example.com/v2/downloads',
  {params: {access_token: '', auth_token: ''}}
```

```json
{
  "data": [
    {
      "id": 18,
      "name": "test",
      "count": 2,
      "begin_time": "2016-04-27 10:58:24",
      "end_time": "2016-04-27 10:58:25",
      "category": "hour",
      "conditions": {
        "model": "search",
        "tab": "hour",
        "client_id": "",
        "reporting_device_id": "64",
        "reading_time_begin": "2015-04-01",
        "reading_time_end": "2015-04-30",
        "controller": "readings",
        "action": "index",
        "sort_field": "reading_time",
        "locale": "en"
      }
    }
  ],
  "meta": {
    "total_count": 1,
    "total_pages": 1,
    "current_page": 1,
    "last_page": true,
    "code": 10000,
    "message": "Success",
    "access_token": "30834411-f7db-486a-840b-21eb66b2699e",
    "auth_token": "348f5965-34c8-429e-a6ed-1c10e7d56d5b"
  }
}
```

Get all prepared downloads of current user.
### HTTP Request

`GET https://example.com/v2/downloads`

### Parameters

Parameter | Require|  Default | Description
--------- | ------- | ------- | -----------
access_token|true | false | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization
page|false|1|Page number
size|false|20|Size per page

## Create Download

```ruby

content = RestClient.post 'https://example.com/v2/downloads',
  {params: {access_token: '', auth_token: ''}}
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

Create download
### HTTP Request

`POST https://example.com/v2/downloads`

### Parameters

Parameter | Require|  Default | Description
--------- | ------- | ------- | -----------
access_token|true | false | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization
name|true||Name of the download
monitor_id|true||Monitor ID
begi_time|true||Begin time for readings
end_time|true||End time for readings
category|true||raw, hour, day, minute_30 or minute_15




## Download File

```ruby

content = RestClient.get 'https://example.com/v2/downloads/{download_id}',
  {params: {access_token: '', auth_token: ''}}
```

```
Binary
```

Download file
### HTTP Request

`GET https://example.com/v2/downloads/1`

<aside class="notice">
* You must replace <code>1</code> with your download ID.
</aside>

### Parameters

Parameter | Require|  Default | Description
--------- | ------- | ------- | -----------
access_token|true | false | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization
download_id|true||Download ID


## Destroy Download

```ruby

content = RestClient.delete 'https://example.com/v2/downloads/1',
  {params: {access_token: '', auth_token: ''}}
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

Destroy download
### HTTP Request

`DELETE https://example.com/v2/downloads/1`


<aside class="notice">
* You must replace <code>1</code> with your download ID.
</aside>

### Parameters

Parameter | Require|  Default | Description
--------- | ------- | ------- | -----------
access_token|true | false | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization
download_id|true||Download ID

