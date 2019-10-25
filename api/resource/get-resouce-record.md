

#  获取资源的内容审核记录

**请求方式 GET https://api.ucloud.cn**

**请求参数(拼在Url后面)**

| 字段名 | 字段类型 | 说明 | 是否必须 |
| ------ | -------- | ---- | -------- |
| Action | String | 固定值：GetUAICensorResourceRecordInfo | 是 |
| PublicKey | String | 私钥 | 是 |
| Signature | String | 签名 | 签名参照https://docs.ucloud.cn/api/summary/signature |
| Region      | String  | 地域信息,可选地域：cn-bj2               | 是     |
| ProjectId   | String  | 项目ID。不填写则为默认项目                 | 否     |
| ResourceId  | String  | 资源ID, 若不提供则给出当前账号下所有资源的请求记录信息  | 否     |
| BeginTime   | Int     | 开始查询时间（unix时间戳）                | 是     |
| EndTime     | Int     | 结束查询时间（unix时间戳）                | 是     |
| Limit       | Int     | 查询限制条数，默认无限制                   | 否     |
| Offset      | Int     | 查询起始偏移量，默认为0                   | 否     |

**响应参数（JSON）**

| 字段名 | 字段类型 | 说明 |
| ------ | -------- | ---- |
| Action | String | 操作名称， GetUAICensorResourceRecordInfo |
| RetCode | Int | 返回码 |
| Message | String | 返回信息 |
| TotalRecordCount | Int | 资源请求记录总数 |
| TotalCensorCount | Int | 记录的审查请求总数 |
| DataSet | Array of UAICensorResourceRecordInfo | 资源请求记录的具体信息 |

**UAICensorResourceRecordInfo**

| 字段名 | 字段类型 | 说明 |
| ------ | -------- | ---- |
| ResourceId        | String  | 资源ID                 |
| Status            | String  | 资源状态                 |
| CensorCount       | Int     | 审查请求数                |
| LatestRecordTime  | Int     | 最新请求记录创建时间（unix时间戳）  |