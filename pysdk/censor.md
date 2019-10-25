

# 内容审核

## 1. 视频内容审核

### 使用说明

  python censor_tool.py video {create,query} ...

### 参数说明

| 参数名称 | 参数类型 | 参数说明 |
| -------- | -------- | -------- |
| public\_key | string | 用户的公钥 |
| resource\_id | string | 资源ID|
| timestamp | int64 | 时间戳信息|
| url | string | 视频路径 |
| signature | string | 签名信息 |
| type | string | 视频审查任务类型，可选项{sync,async}|
| scenes | string | 视频审查场景，若有多个，用","分隔，可选项{porn, politician, terror}|
| interval | int | 截帧间隔 |
| callback | string | 视频审查结果回调地址 |

#### 1.1 创建视频审查任务

  python censor_tool.py video create		--signature SIGNATURE \
  						--public_key PUBLIC_KEY \
  						--resource_id RESOURCE_ID \
                                      		--timestamp TIMESTAMP 
                                      		--type {sync,async} \
                                   		--scenes SCENES \
                                   		--url URL \
                                   		[--interval INTERVAL] \
                                   		[--callback CALLBACK]


#### 1.2 查看视频审查任务

  python censor_tool.py video query		--signature SIGNATURE \
  						--public_key PUBLIC_KEY \
  						--resource_id RESOURCE_ID \
                                      		--timestamp TIMESTAMP \
                                      		--job_id JOB_ID


## 2. 图片内容审核

### 使用说明

  python censor_tool.py image {create} ...


### 参数说明

| 参数名称 | 参数类型 | 参数说明 |
| -------- | -------- | -------- |
| public\_key | string | 用户的公钥 |
| resource\_id | string | 资源ID|
| timestamp | int64 | 时间戳信息|
| url | string | 图片路径 |
| signature | string | 签名信息 |
| method | string | 图片审查任务数据输入方法，可选项{url,file}|
| scenes | string | 图片审查场景，若有多个，用","分隔，可选项{porn, politician, terror}|
| image | []byte | 图片内容 |
| url | string | 图片地址 |

#### 2.1 图片内容审核

  python censor_tool.py image create  	--signature SIGNATURE \
  					--public_key PUBLIC_KEY \
  					--resource_id RESOURCE_ID \
  					--timestamp TIMESTAMP \
  					--method {url, file} \
  					--scenes SCENES \
  					--url URL \
  					[--image IMAGE] \
  					[--url URL]
