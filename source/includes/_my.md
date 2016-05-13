# My

## Get All Locations

```ruby


content = RestClient.get 'https://example.com/v2/locations',
  {params: {access_token: '12345', per: 2, page: 2}}
```


```shell
curl "https://example.com/v2/locations?access_token=12345&per=2&page=2"
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

Get all locations, can be filtered by city id and location name
### HTTP Request

`GET https://example.com/v2/locations`

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