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