# Version 0

这个是遗留的一个接口，只针对以下老的设备有效，其他设备不使用此接口

* Env Monitor
* Fluke

## 数据

### 上报数据


#### 接口

```
POST /v0/readings
```


#### 参数


* 如果是 Env Monitor

Parameter | Require| Default | Description
--------- | -------| ------- | -----------
EnvMonitorID | true| | 设备编号
Location_Name|true||场所名称
CreatingTime | false|  | 数据产生时间
PM2p5|false||PM 2.5
AT|false||Temperature
RHi|false||Humidity

* 如果是 Fluke

Parameter | Require| Default | Description
--------- | -------| ------- | -----------
device_identifier | true| | 设备编号
reading_time | false|  | 数据产生时间
pm2p5|false||PM 2.5
temperature|false||Temperature
humidity|false||Humidity
co2|false||CO2
co|false||CO
tvoc|false||Total VOC
hcho|false||HCHO

#### 返回

返回 QLEAR 转换之后的标准格式

* Env Monitor

```json
[
  {
    "reading_time": "",
    "pm2p5": "",
    "temperature": "",
    "humidity": ""
  }
]
```

* Fluke

```json
[
  {
    "reading_time": "",
    "pm2p5": "",
    "temperature": "",
    "humidity": "",
    "co2": "",
    "co": "",
    "tvoc": "",
    "hcho": ""
  }
]
```