{{indexmenu_n>20}}

# 查询异步视频任务执行结果

**GET http://api.uai.ucloud.cn/v1/video/asyncscan**

**Signature使用参数**

- JobId
- ResourceId
- PublicKey
- Timestamp


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

**请求参数（拼在Url后面）**

| 字段名 | 字段类型 | 说明 | 是否必须 |
| ------ | -------- | ---- | -------- |
| JobId | String | 任务ID | 是 |

**返回结果（JSON）**

| 字段名 | 字段类型 | 说明 |
| ------ | -------- | ---- |
| RetCode      | Int           | 返回码                                                                          |
| Message      | String        | 返回信息                                                                         |
| Status       | String        | 任务执行状态： Unknown-未知, Waiting-等待中, Running-执行中, Success-成功, Fail-失败, Abort-中止  |
| Url          | String        | 视频源地址                                                                        |
| StartTime    | Int           | 任务开始时间unix时间戳                                                                |
| EndTime      | Int           | 任务结束时间unix时间戳                                                                |
| ExpiredTime  | Int           | 鉴别结果保存失效时间unix时间戳                                                            |
| Timestamp    | Int           | 当前unix时间戳                                                                    |
| Result       | CensorResult  | 鉴别结果                                                                         |

**CensorResult**

| 字段名 | 字段类型 | 说明 |
| ------ | -------- | ---- |
| Porn        | CensorInfo  | 涉黄审查结果  |
| Terror      | CensorInfo  | 涉恐审查结果  |
| Politician  | CensorInfo  | 涉政审查结果  |

**CensorInfo**

| 字段名 | 字段类型 | 说明 |
| ------ | -------- | ---- |
| Frames      | Array of FrameInfo  | 涉黄/涉恐/涉政的帧信息                               |
| Suggestion  | String              | 结果建议，pass - 放行， forbid - 封禁， check - 人工审核  |

**FrameInfo**

| 字段名 | 字段类型 | 说明 |
| ------ | -------- | ---- |
| FrameId | Int | 图像帧号， 视频第一帧图像帧号为0 |
| Score | Float | 得分， 范围[0, 1]， 分数越高，置信度越高 |