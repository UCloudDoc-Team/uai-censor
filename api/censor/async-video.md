

#  创建异步视频任务

**请求方式 POST http://api.uai.ucloud.cn/v1/video/asyncscan**

**Signature使用参数**

- Timestamp: Header参数Timestamp
- ResourceId: Header参数ResourceId
- Url: 请求参数Url
- PublicKey: Header参数PublicKey

生成Signature签名算法流程包括四步：  
（1）将请求参数按照名进行升序排列；  
（2）构造被签名参数串；  
（3）计算签名；  
（4）使用签名组合HTTP请求。  

*具体内容请参考签名文档：https://docs.ucloud.cn/api/summary/signature*

**Header参数**

| 字段名 | 字段类型 | 说明 | 是否必须 |
| ------ | -------- | ---- | -------- |
| Signature | String | 签名 | 是 |
| PublicKey | String | 公钥 | 是 |
| ResourceId | String | 资源ID | 是 |
| Timestamp | Int | 当前unix时间戳 | 是 |

**请求参数（JSON）**

| 字段名 | 字段类型 | 说明 | 是否必须 |
| ------ | -------- | ---- | -------- |
| Scenes | Array of String | 场景，可选场景包括：鉴黄 - porn | 是 |
| Url | String | 视频文件地址 | 是 |
| Interval | Int | 抽帧间隔， 默认值25 | 是 |
| Callback | String | 鉴别结果通知回调（公网域名，任务完成后向callback post鉴别结果） | 否 |

**返回结果（JSON）**

| 字段名 | 字段类型 | 说明 |
| ------ | -------- | ---- |
| RetCode    | Int     | 返回码             |
| Message    | String  | 返回信息            |
| JobId      | String  | 任务ID，用于接收、查询结果  |
| Timestamp  | Int     | 当前unix时间戳       |

**Callback数据格式**

| 字段名 | 字段类型 | 说明 |
| ------ | -------- | ---- |
| JobId | String | 任务ID |
| Url | String | 视频源文件地址 |
| StartTime | Int | 任务开始时间unix时间戳 |
| EndTime | Int | 任务结束时间unix时间戳 |
| ExpiredTime | Int | 鉴别结果保存失效时间unix时间戳 |
| Result | CensorResult | 鉴别结果 |

**CensorResult**

| 字段名 | 字段类型 | 说明 |
| ------ | -------- | ---- |
| Porn | CensorInfo | 涉黄审查结果 |
| Terror | CensorInfo | 涉恐审查结果 |
| Politician | CensorInfo | 涉政审查结果 |

**CensorInfo**

| 字段名 | 字段类型 | 说明 |
| ------ | -------- | ---- |
| Frames | Array of FrameInfo | 涉黄/涉恐/涉政的帧信息 |
| Suggestion | String | 结果建议，pass - 放行， forbid - 封禁， check - 人工审核 |

**FrameInfo**

| 字段名 | 字段类型 | 说明 |
| ------ | -------- | ---- |
| FrameId | Int | 图像帧号， 视频第一帧图像帧号为0 |
| Score | Float | 得分， 范围[0, 1]， 分数越高，置信度越高 |

**用户成功接收callback信息，返回数据格式**

| 字段名 | 字段类型 | 说明 |
| ------ | -------- | ---- |
| RetCode | Int | 0 - 正确接收 |
| Message | String | 信息 |

