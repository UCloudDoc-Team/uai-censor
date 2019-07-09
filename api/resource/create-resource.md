{{indexmenu_n>10}}

### 创建资源

**请求方式 GET <https://api.ucloud.cn>**

**请求参数(拼在Url后面)**

|                |        |                                    |                                                  |
| -------------- | ------ | ---------------------------------- | ------------------------------------------------ |
| 字段名            | 字段类型   | 说明                                 | 是否必须                                             |
| Action         | String | 固定值：CreateUAICensorResource        | 是                                                |
| PublicKey      | String | 私钥                                 | 是                                                |
| Signature      | String | 签名                                 | 签名参照https://docs.ucloud.cn/api/summary/signature |
| Region         | String | 地域信息,可选地域：cn-bj2                   | 是                                                |
| ProjectId      | String | 项目ID。不填写则为默认项目                     | 否                                                |
| ResourceType.N | Int    | 安全审查类型,可选类型: 0 - 鉴黄                | 是                                                |
| ResourceName   | String | 资源名称, 默认资源名称AutoCensor-{timestamp} | 否                                                |
| ResourceMemo   | String | 资源备注信息，默认无备注信息                     | 否                                                |

**响应参数（JSON）**

|            |        |                               |
| ---------- | ------ | ----------------------------- |
| 字段名        | 字段类型   | 说明                            |
| Action     | String | 操作名称， CreateUAICensorResource |
| RetCode    | Int    | 返回码                           |
| Message    | String | 返回信息                          |
| ResourceId | String | 资源ID                          |
