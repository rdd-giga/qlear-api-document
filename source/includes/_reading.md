# Readings

## Get All Data


```ruby


content = RestClient.get 'https://example.com/v2/readings',
  {params: {access_token: '12345', location_id: '70', monitor_id: '12,25', begin_time: '2016-03-29 15:00:00', end_time: '2016-03-30 15:00:00'}}
```

```json
{
  "data": [
    {
      "reading_time": "2015-04-29 15:00:00",
      "pm2p5": 32,
      "tvoc": null,
      "co2": null,
      "humidity": 26
    }
  ],
  "meta": {
    "total_count": 5,
    "total_pages": 5,
    "current_page": 1,
    "last_page": false,
    "code": 10000,
    "message": "Success",
    "access_token": "30834411-f7db-486a-840b-21eb66b2699e",
    "auth_token": "348f5965-34c8-429e-a6ed-1c10e7d56d5b"
  }
}
```

Retrieves all the data of specific location or monitor.

### HTTP Request

`GET https://example.com/v2/readings`

### Parameters

Parameter | Require| Default | Description
--------- | -------| ------- | -----------
access_token | true| | Access Token.
auth_token|true||Auth Token
location_id | false|  | Location id
monitor_id|false||Monitor id
begin_time|false||Begin time for query
end_time|false||End time for query
tab|false|hour|Data type. Available Tab: hour, raw
page|false|1|Page number
size|false|20|Size per page


## Get Graph Data


```ruby


content = RestClient.get 'https://example.com/v2/readings/graph',
  {params: {access_token: '12345', location_id: '70', monitor_id: '12,25', begin_time: '2016-03-29 15:00:00', end_time: '2016-03-30 15:00:00'}}
```

```json
{
  "data": {
    "times": [
      "03/29 16:00",
      "03/29 17:00",
      "03/29 18:00",
      "03/29 19:00",
      "03/29 20:00",
      "03/29 21:00",
      "03/29 22:00",
      "03/29 23:00",
      "03/30 00:00",
      "03/30 01:00",
      "03/30 02:00",
      "03/30 03:00",
      "03/30 04:00",
      "03/30 05:00",
      "03/30 06:00",
      "03/30 07:00",
      "03/30 08:00",
      "03/30 09:00",
      "03/30 10:00",
      "03/30 11:00",
      "03/30 12:00",
      "03/30 13:00",
      "03/30 14:00",
      "03/30 15:00"
    ],
    "readings": [
      {
        "name": "RESET Testing",
        "ref_id": 70,
        "ref_name": "RESET Testing",
        "data": [
          "5.0",
          "5.0",
          "5.0",
          "6.0",
          "8.0",
          "8.0",
          "10.0",
          "8.0",
          "8.0",
          "8.0",
          "10.0",
          "10.0",
          "9.0",
          "10.0",
          "10.0",
          "8.0",
          "6.0",
          "6.0",
          "11.0",
          "8.0",
          "8.0",
          "9.0",
          "8.0",
          "8.0"
        ],
        "type": "location"
      },
      {
        "name": "上海美国领事馆/U.S. Consulate SH ",
        "ref_id": 102,
        "ref_name": "上海美国领事馆/U.S. Consulate SH ",
        "data": [
          "61.0",
          "60.0",
          "52.0",
          "56.0",
          "65.0",
          "66.0",
          "71.0",
          "71.0",
          "80.0",
          "100.0",
          "104.0",
          "103.0",
          "100.0",
          "94.0",
          "82.0",
          "66.0",
          "60.0",
          "63.0",
          "62.0",
          "65.0",
          "67.0",
          "66.0",
          "67.0",
          "67.0"
        ],
        "type": "outdoor_location"
      },
      {
        "name": "Particulate Matter",
        "ref_id": "12",
        "ref_name": "30227",
        "data": [
          "43.0",
          "43.0",
          "42.0",
          "43.0",
          "44.0",
          "47.0",
          "47.0",
          "46.0",
          "43.0",
          "40.0",
          "36.0",
          "33.0",
          "30.0",
          "28.0",
          "27.0",
          "28.0",
          "29.0",
          "38.0",
          "44.0",
          "37.0",
          "34.0",
          "38.0",
          "38.0",
          "37.0"
        ],
        "type": "monitor"
      },
      {
        "name": "Year 1 Indoor Play Area",
        "ref_id": "25",
        "ref_name": "ACCF232C4754",
        "data": [
          "9.0",
          "8.0",
          "8.0",
          "8.0",
          "35.0",
          "9.0",
          "15.0",
          "17.0",
          "17.0",
          "16.0",
          "16.0",
          "16.0",
          "16.0",
          "15.0",
          "14.0",
          "14.0",
          "55.0",
          "20.0",
          "15.0",
          "13.0",
          "13.0",
          "13.0",
          "13.0",
          "12.0"
        ],
        "type": "monitor"
      }
    ]
  },
  "meta": {
    "location_id": "70",
    "monitor_id": [
      "12",
      "25"
    ],
    "begin_time": "2016-03-29T15:33:07.627+08:00",
    "end_time": "2016-03-30T15:00:00.000+08:00",
    "indicator": "pm2p5"
  }
}
```

Retrieves all the average readings of specific location or monitor for graph.

### HTTP Request

`GET https://example.com/v2/readings/graph`

### Parameters

Parameter | Require| Default | Description
--------- | -------| ------- | -----------
access_token | true| | Access Token.
auth_token|true||Auth Token
location_id | false|  | Location id
monitor_id|false||Monitor id, use comma if more than one, eg: 12,25
indicator|false|pm2p5|Available indicators: pm2p5, pm10, co2, co, tvoc, hcho, humidity, temperature. Use comma if more than one.
begin_time|false|Time.now - 1.day|Begin time for query
end_time|false|Time.now|End time for query