# Cities

## Get All Cities


```ruby


content = RestClient.get 'https://example.com/v2/cities',
  {params: {access_token: '12345'}}
```


```shell
curl "https://example.com/v2/cities?access_token=12345"
```

```json

{
  "data": [
    {
      "id": 2,
      "name": "Beijing",
      "image": null
    },
    {
      "id": 800,
      "name": "Shanghai",
      "image": "https://dn-reset.qbox.me/uploads/city/theme/thumb_beb52b19-3f34-4cac-b093-95709cfedc59.jpg"
    },
    {
      "id": 864,
      "name": "Suzhou",
      "image": null
    }
  ],
  "meta": {
    "total_count": 3,
    "total_pages": 1,
    "current_page": 1,
    "last_page": true
  }
}
```

This endpoint retrieves all available cities.

### HTTP Request

`GET https://example.com/v2/cities`

### Parameters

Parameter | Require| Default | Description
--------- | -------| ------- | -----------
access_token | true| | Access Token.
auth_token|true||Auth Token
locale | false| en | Localization
page|false|1|Page number
size|false|20|Size per page


## Get Activity Cities

```ruby


content = RestClient.get 'https://example.com/v2/cities/activity',
  {params: {access_token: '12345'}}
```

```shell
curl "https://example.com/v2/cities/activity?access_token=12345"
```

```json
{
  "data": {
    "china": [
      {
        "id": 2,
        "name": "Beijing",
        "image": null
      },
      {
        "id": 800,
        "name": "Shanghai",
        "image": "https://dn-reset.qbox.me/uploads/city/theme/thumb_beb52b19-3f34-4cac-b093-95709cfedc59.jpg"
      },
      {
        "id": 864,
        "name": "Suzhou",
        "image": null
      }
    ],
    "global": [
      {
        "id": 3238,
        "name": "Xianggang",
        "image": null
      }
    ]
  }
}

```

Get all activity cities, grouping by country.

### HTTP Request

`GET https://example.com/v2/cities/activity`

### Parameters

Parameter | Require| Default | Description
--------- | -------| ------- | -----------
access_token|true |  | Access Token.
auth_token|true||Auth Token
locale |false| en | Localization