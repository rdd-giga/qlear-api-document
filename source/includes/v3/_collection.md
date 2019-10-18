## 集合列表

```json
{
  "data": [
    {
      "id": 1,
      "code": "S-99002",
      "name": "Outdoor Monitor",
      "indicators": [
        {
          "id": 1,
          "name": "PM 2.5",
          "data_channel": "pm2p5",
          "data_channel_name": "PM 2.5",
          "data_source_id": 76,
          "data_source_identifier": "US-Embassy-Beijing"
        }
      ]
    }
  ],
  "meta": {
    "total_count": 2815,
    "total_pages": 2815,
    "current_page": 1,
    "last_page": false,
    "code": 10000,
    "message": "Success"
  }
}
```

接口描述 ...

### 接口

GET /v3/collections

### 参数

| 参数         | 类型   | 必须 | 默认 | 说明                    |
| ------------ | ------ | ---- | ---- | ----------------------- |
| access_token | String | 是   |      | 授权 Token              |
| version      | Number | 否   | 3.1  | 请求版本                |
| page         | Number | 否   | 1    | 当前请求页数            |
| page_size    | Number | 否   | 25   | 每页请求数量，不超过 50 |
| sign         | String | 是   |      | 签名                    |

## 集合明细

```json
{
  "data": {
    "id": 1,
    "code": "S-99002",
    "name": "Outdoor Monitor",
    "indicators": [
      {
        "id": 1,
        "name": "PM 2.5",
        "data_channel": "pm2p5",
        "data_channel_name": "PM 2.5",
        "data_source_id": 76,
        "data_source_identifier": "US-Embassy-Beijing"
      }
    ],
    "locations": [
      {
        "id": 1,
        "name": "Beijing U.S. Embassy",
        "category": "outdoor"
      }
    ],
    "reading": {
      "status": "moderate",
      "stale": false,
      "last_reading_time": "2019-09-26T12:00:00.000+08:00",
      "data_channels": [
        {
          "data_channel": "pm2p5",
          "name": "PM 2.5",
          "type": "air",
          "unit": "μg/m³",
          "value": 49,
          "level": "moderate"
        }
      ]
    }
  },
  "meta": {
    "code": 10000,
    "message": "Success"
  }
}
```

接口描述 ...

### 接口

GET /v3/collections/{collection_id}

### 参数

| 参数         | 类型   | 必须 | 默认 | 说明       |
| ------------ | ------ | ---- | ---- | ---------- |
| access_token | String | 是   |      | 授权 Token |
| version      | Number | 否   | 3.1  | 请求版本   |
| sign         | String | 是   |      | 签名       |
