# 场景

## 场所列表

```json
{
  "data": [
    {
      "id": 1,
      "city_id": 800,
      "category": "indoor",
      "time_zone": "Asia/Shanghai",
      "address": null,
      "created_at": "2019-09-24T15:17:51.000+08:00",
      "name": "Testing Location",
      "city_name": "Shanghai",
      "workspace_id": 2,
      "workspace_name": "GIGA",
      "outdoor": {
        "id": 2,
        "name": "Shanghai U.S. Consulate"
      },
      "collections": [
        {
          "id": 1,
          "code": "C-00020211",
          "name": "22F-东"
        }
      ],
      "average": {
        "performance": "good",
        "status": "online",
        "stale": false,
        "last_reading_time": "2019-09-26T12:00:00.000+08:00",
        "readings": [
          {
            "data_channel": "pm2p5",
            "name": "PM 2.5",
            "type": "air",
            "unit": "μg/m³",
            "value": 11,
            "level": "good"
          },
          {
            "data_channel": "co2",
            "name": "CO₂",
            "type": "air",
            "unit": "ppm",
            "value": 623,
            "level": "good"
          },
          {
            "data_channel": "tvoc",
            "name": "Total VOC",
            "type": "air",
            "unit": "mg/m³",
            "value": 0.17,
            "level": "good"
          },
          {
            "data_channel": "temperature",
            "name": "Temperature",
            "type": "air",
            "unit": "°C",
            "value": 26,
            "level": null
          },
          {
            "data_channel": "humidity",
            "name": "Humidity",
            "type": "air",
            "unit": "%RH",
            "value": 43.58,
            "level": null
          }
        ]
      }
    }
  ],
  "meta": {
    "total_count": 2096,
    "total_pages": 2096,
    "current_page": 1,
    "last_page": false,
    "code": 10000,
    "message": "Success"
  }
}
```

接口描述 ...

### 接口

GET /v3/locations

### 参数

| 参数         | 类型   | 必须 | 默认 | 说明                    |
| ------------ | ------ | ---- | ---- | ----------------------- |
| access_token | String | 是   |      | 授权 Token              |
| version      | Number | 否   | 3.1  | 请求版本                |
| page         | Number | 否   | 1    | 当前请求页数            |
| page_size    | Number | 否   | 25   | 每页请求数量，不超过 50 |
| sign         | String | 是   |      | 签名                    |

## 场所明细

```json
{
  "data": {
    "id": 1,
    "city_id": 800,
    "category": "indoor",
    "time_zone": "Asia/Shanghai",
    "address": null,
    "created_at": "2019-09-24T15:17:51.000+08:00",
    "name": "0924teseting",
    "city_name": "Shanghai",
    "workspace_id": 2,
    "workspace_name": "GIGA",
    "outdoor": {
      "id": 2,
      "name": "Shanghai U.S. Consulate"
    },
    "collections": [
      {
        "id": 1,
        "code": "C-00020211",
        "name": "22F-东",
        "readings": [
          {
            "indicator_id": 1,
            "data_channel": "pm2p5",
            "name": "PM 2.5",
            "type": "air",
            "unit": "μg/m³",
            "value": 11,
            "level": "good",
            "time": "2019-09-26T12:00:00.000+08:00"
          },
          {
            "indicator_id": 2,
            "data_channel": "co2",
            "name": "CO₂",
            "type": "air",
            "unit": "ppm",
            "value": 623,
            "level": "good",
            "time": "2019-09-26T12:00:00.000+08:00"
          },
          {
            "indicator_id": 3,
            "data_channel": "tvoc",
            "name": "Total VOC",
            "type": "air",
            "unit": "mg/m³",
            "value": 0.17,
            "level": "good",
            "time": "2019-09-26T12:00:00.000+08:00"
          },
          {
            "indicator_id": 4,
            "data_channel": "temperature",
            "name": "Temperature",
            "type": "air",
            "unit": "°C",
            "value": 26,
            "level": null,
            "time": "2019-09-26T12:00:00.000+08:00"
          },
          {
            "indicator_id": 5,
            "data_channel": "humidity",
            "name": "Humidity",
            "type": "air",
            "unit": "%RH",
            "value": 43.58,
            "level": null,
            "time": "2019-09-26T12:00:00.000+08:00"
          }
        ],
        "performance": "good",
        "status": "online",
        "stale": false,
        "last_reading_time": "2019-09-26T12:00:00.000+08:00"
      }
    ],
    "average": {
      "performance": "good",
      "status": "online",
      "stale": false,
      "last_reading_time": "2019-09-26T12:00:00.000+08:00",
      "readings": [
        {
          "data_channel": "pm2p5",
          "name": "PM 2.5",
          "type": "air",
          "unit": "μg/m³",
          "value": 11,
          "level": "good"
        },
        {
          "data_channel": "co2",
          "name": "CO₂",
          "type": "air",
          "unit": "ppm",
          "value": 621,
          "level": "good"
        },
        {
          "data_channel": "tvoc",
          "name": "Total VOC",
          "type": "air",
          "unit": "mg/m³",
          "value": 0.17,
          "level": "good"
        },
        {
          "data_channel": "temperature",
          "name": "Temperature",
          "type": "air",
          "unit": "°C",
          "value": 26,
          "level": null
        },
        {
          "data_channel": "humidity",
          "name": "Humidity",
          "type": "air",
          "unit": "%RH",
          "value": 43.54,
          "level": null
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

GET /v3/locations/{location_id}

### 参数

| 参数         | 类型   | 必须 | 默认 | 说明       |
| ------------ | ------ | ---- | ---- | ---------- |
| access_token | String | 是   |      | 授权 Token |
| version      | Number | 否   | 3.1  | 请求版本   |
| sign         | String | 是   |      | 签名       |
