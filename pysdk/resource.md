{{indexmenu_n>10}}

### 资源管理

\#\#使用说明

    python censor_tool.py resource {create,delete,modifyname,modifymemo,modifyoss,list,listrecord,listtype} ...

\#\#参数说明

|                   |        |                    |
| ----------------- | ------ | ------------------ |
| 参数名称              | 参数类型   | 参数说明               |
| public\\\_key     | string | 用户的公钥              |
| private\\\_key    | string | 用户的私钥              |
| project\\\_id     | string | bitmap的具体含义        |
| region            | string | 地域信息，默认cn-bj2      |
| zone              | string | 可用区信息，默认cn-bj2     |
| resource\\\_types | string | 资源类型，若含多种资源，用","隔开 |
| resource\\\_name  | string | 资源名称               |
| resource\\\_memo  | string | 资源备注               |
| limit             | string | 查询记录总数             |
| offset            | string | 首条记录的偏移量           |

\#\#1. 创建资源

``` 
python censor_tool.py resource create --public_key PUBLIC_KEY \
                                      --private_key PRIVATE_KEY \
                                      [--project_id PROJECT_ID] \
                                      [--region REGION] \
                                      [--zone ZONE] \
                                      --resource_types RESOURCE_TYPES \
                                      [--resource_name RESOURCE_NAME] \
                                      [--resource_memo RESOURCE_MEMO]

```

\#\#2. 删除资源

``` 
python censor_tool.py resource delete --public_key PUBLIC_KEY \
                                      --private_key PRIVATE_KEY \
                                      [--project_id PROJECT_ID] \
                                      [--region REGION] \
                                      [--zone ZONE] \
                                      --resource_id RESOURCE_ID

```

\#\#3. 修改资源名称

    python censor_tool.py resource modifyname --public_key PUBLIC_KEY \
                                              --private_key PRIVATE_KEY \
                                              [--project_id PROJECT_ID] \
                                              [--region REGION] \
                                              [--zone ZONE] \
                                              --resource_id RESOURCE_ID \
                                              --resource_name RESOURCE_NAME

\#\#4. 修改资源备注

    python censor_tool.py resource modifymemo --public_key PUBLIC_KEY \
                                              --private_key PRIVATE_KEY \
                                              [--project_id PROJECT_ID] \
                                              [--region REGION] \
                                              [--zone ZONE] \
                                              --resource_id RESOURCE_ID \
                                              --resource_memo RESOURCE_MEMO

\#\#5. 获取已创建资源列表

``` 
python censor_tool.py resource list --public_key PUBLIC_KEY \
                                          --private_key PRIVATE_KEY \
                                          [--project_id PROJECT_ID] \
                                          [--region REGION] \
                                          [--zone ZONE] \
                                          [--limit LIMIT] \
                                          [--offset OFFSET] 
                                   
```

\#\#6. 获取资源使用记录

    python censor_tool.py resource listtype       --public_key PUBLIC_KEY \
                                                  --private_key PRIVATE_KEY \
                                                  [--project_id PROJECT_ID] \
                                                  [--region REGION] \
                                                  [--zone ZONE] \
                                                  --begin_time BEGIN_TIME \                                                       --end_time END_TIME \
                                                  [--resource_id RESOURCE_ID]
