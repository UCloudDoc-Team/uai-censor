{{indexmenu_n>1}}

#  创建图片任务

**POST http://api.uai.ucloud.cn/v1/image/scan**

**Signature使用参数**

- Url: 请求参数Url, 若请求参数无Url,则不加入此参数
- ResourceId: header参数ResourceId
- PublicKey： header参数PublicKey
- Timestamp： header参数Timestamp


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

**请求参数（Multipart/Form-data）**

| 字段名 | 字段类型 | 说明 | 是否必须 |
| ------ | -------- | ---- | -------- |
| Scenes  | String  | 场景，场景之间逗号隔开，可选场景： porn - 鉴黄               | 是     |
| Method  | String  | 请求方式，可选方式： url - 传入图片url, file - 传入图片二进制  | 是     |
| Url     | String  | 图片url                                     | 否     |
| Image   | Binary  | 图片文件                                      | 否     |

**响应参数（JSON）**

| 字段名 | 字段类型 | 说明 |
| ------ | -------- | ---- |
| RetCode | Int | 返回码 |
| Message | String | 返回信息 |
| Timestamp | Int | 当前unix时间戳 |
| JobId | String | 任务ID |
| StartTime | Int | 任务开始时间unix时间戳 |
| EndTime | Int | 任务结束时间unix时间戳 |
| ExpiredTime | Int | 鉴别结果保存失效时间unix时间戳 |
| Result | CensorResult | 鉴别结果 |

**CensorResult**

| 字段名 | 字段类型 | 说明 |
| ------ | -------- | ---- |
| Porn        | ImageResultInfo  | 涉黄审查结果  |
| Terror      | ImageResultInfo  | 涉恐审查结果  |
| Politician  | ImageResultInfo  | 涉政审查结果  |

**ImageResultInfo**

| 字段名 | 字段类型 | 说明 |
| ------ | -------- | ---- |
| Score | Float | 得分，范围[0, 1], 得分越高，置信度越高 |
| Suggestion | String | 建议， pass-放行， forbid-封禁， check-人工审核 |