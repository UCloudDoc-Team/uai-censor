{{indexmenu_n>50}}

#  获取已创建资源列表

**请求方式 GET https://api.ucloud.cn**

**请求参数(拼在Url后面)**

| 字段名 | 字段类型 | 说明 | 是否必须 |
| ------ | -------- | ---- | -------- |
| Action | String | 固定值：GetUAICensorResourceList | 是 |
| PublicKey | String | 私钥 | 是 |
| Signature | String | 签名 | 签名参照https://docs.ucloud.cn/api/summary/signature |
| Region | String | 地域信息,可选地域：cn-bj2 | 是 |
| ProjectId | String | 项目ID。不填写则为默认项目 | 否 |
| Limit | Int | 查询限制条数，默认无限制 | 否 |
| Offset | Int | 查询起始偏移量，默认为0 | 否 |

**响应参数（JSON）**

| 字段名 | 字段类型 | 说明 |
| ------ | -------- | ---- |
| Action | String | 操作名称， GetUAICensorResourceList |
| RetCode | Int | 返回码 |
| Message | String | 返回信息 |
| TotalCount | Int | 返回资源总数 |
| DataSet | Array of UAICensorResourceInfo | UAI安全审查的资源信息 |

**UAICensorResourceInfo**

| 字段名 | 字段类型 | 说明 |
| ------ | -------- | ---- |
| ResourceId | String | 资源ID |
| ResourceName | String | 资源名称 |
| ResourceType | Array of String | 资源类型 |
| ResourceMemo | String | 资源备注 |
| Status | String| 资源状态 |
| CreateTime | Int | 资源创建时间 |