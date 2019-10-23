## 设备列表

```json
{
  "data": [
    {
      "id": 1,
      "name": null,
      "identifier": "US-Embassy-Shanghai",
      "brand_id": 2,
      "brand_name": "US Embassy & Consulates",
      "brand": "US Embassy & Consulates",
      "model_id": 6,
      "model_name": "Default Monitor",
      "model": "Default Monitor",
      "status": "online",
      "parameters": ["air"],
      "created_at": "2014-09-25T09:06:11.000+08:00"
    }
  ],
  "meta": {
    "total_count": 7011,
    "total_pages": 7011,
    "current_page": 1,
    "last_page": false,
    "code": 10000,
    "message": "Success"
  }
}
```

接口描述 ...

### 接口

GET /v3/data_sources

### 参数

| 参数         | 类型   | 必须 | 默认 | 说明                    |
| ------------ | ------ | ---- | ---- | ----------------------- |
| access_token | String | 是   |      | 授权 Token              |
| version      | Number | 否   | 3.1  | 请求版本                |
| page         | Number | 否   | 1    | 当前请求页数            |
| page_size    | Number | 否   | 25   | 每页请求数量，不超过 50 |
| sign         | String | 是   |      | 签名                    |

## 设备明细

```json
{
  "data": {
    "id": 1,
    "name": null,
    "identifier": "US-Embassy-Shanghai",
    "brand_id": 2,
    "brand_name": "US Embassy & Consulates",
    "brand": "US Embassy & Consulates",
    "model_id": 6,
    "model_name": "Default Monitor",
    "model": "Default Monitor",
    "status": "online",
    "parameters": ["air"],
    "created_at": "2016-08-23T16:09:04.000+08:00",
    "last_received_time": "2019-09-26T12:55:32.000+08:00",
    "last_reading_time": "2019-09-26T12:55:32.000+08:00",
    "reading": {
      "co": 828,
      "o3": 0,
      "co2": 444,
      "no2": 159,
      "so2": 0,
      "hcho": 0,
      "pm10": 0,
      "tvoc": 230,
      "pm2p5": 0,
      "humidity": 305,
      "temperature": 266,
      "enqueue_time": "2019-09-26T12:55:32.292+08:00",
      "reading_time": "2019-09-26T12:55:32.290+08:00"
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

GET /v3/data_sources/{data_source_id}

### 参数

| 参数         | 类型   | 必须 | 默认 | 说明       |
| ------------ | ------ | ---- | ---- | ---------- |
| access_token | String | 是   |      | 授权 Token |
| type        |  String| 否 | id| 可选 identifier|
| version      | Number | 否   | 3.1  | 请求版本   |
| sign         | String | 是   |      | 签名       |
