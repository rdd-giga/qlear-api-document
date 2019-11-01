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

```typescript
{
  data:{
    assigned_data_channels: string[]; // 已关联的数据源
    brand: string; // 设备厂牌
    brand_id: number;
    brand_name: string;
    calibrated: boolean; // 是否被默认校准
    created_at: string;
    enable_status_notification: boolean;
    id: number;
    identifier: string; // 设备唯一标识
    image?: string;
    model: string; // 款式型号
    model_id: number;
    model_name: string;
    name?: string;
    parameters: string[]; // 支持的类型（空气、电 等等）
    search_time_enabled_at: string;
    status: string; // 当前状态
    unassigned_count: number; // 未关联的数据通道数量
  }[];
  meta: {
    ...
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

```typescript
{
  data: {
    assigned_data_channels: string[];
    brand: string;
    brand_id: number;
    brand_name: string;
    calibrated: boolean;
    channels?: { // 使用的数据通道信息
      channel: string;
      channel_name: string;
      data_source_id: number;
      id: number;
      indicator: string;
      name: string;
      unit: string;
      abbr?: string;
    }[];
    created_at: string;
    enable_status_notification: boolean; // 设备是否开启了状态通知
    flatline_limit?: number; // flatline状态 标准
    id: number;
    identifier: string;
    image?: string;
    last_averaged_at?: string;  // 系列时间
    last_calibrated_at?: string;
    last_consumed_time?: string;
    last_reading_time?: string;
    last_received_time?: string;
    model: string;
    model_id: number;
    model_name: string;
    name: string;
    offline_limit?: number; // offline 状态标准
    parameters: string[];
    reading?: { // 最新一条数据信息
      ... // 各种接收到的数据信息（不同型号的设备发送的数据各不相同）
      reading_time: string;
      enqueue_time: string;
      source: string;
      type: string;
    };
    search_time_enabled_at: string;
    status: string;
    unassigned_count: number;
  };
  meta: {
    ...
  }
}
```

[数据源的含义](https://qlear.io/web/knowledge/58)

### 接口

GET /v3/data_sources/{data_source_id}

### 参数

| 参数         | 类型   | 必须 | 默认 | 说明       |
| ------------ | ------ | ---- | ---- | ---------- |
| access_token | String | 是   |      | 授权 Token |
| type        |  String| 否 | id| 可选 identifier|
| version      | Number | 否   | 3.1  | 请求版本   |
| sign         | String | 是   |      | 签名       |


