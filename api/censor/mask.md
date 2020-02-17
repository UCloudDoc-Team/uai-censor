

#  创建口罩检测任务

**POST http://api.uai.ucloud.cn/v1/mask**

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
| Method  | String  | 请求方式，可选方式： url - 传入图片url, file - 传入图片二进制  | 是     |
| Url     | String  | 图片url                                     | 否     |
| Image   | Binary  | 图片文件                                      | 否     |

**响应参数（JSON）**

| 字段名 | 字段类型 | 说明 |
| ------ | -------- | ---- |
| RetCode | Int | 返回码 |
| Message | String | 返回信息 |
| Timestamp | Int | 当前unix时间戳 |
| Results | []MaskMResult  | 检测结果, 未检测到人脸数组长度为0 |

**MaskMResult**

| 字段名 | 字段类型 | 说明 |
| ------ | -------- | ---- |
| Rect        | []int  | 涉黄审查结果, 人脸框位置[x0, y0, w, h], (x0,y0) 人脸框左上角位置, w、h 人脸框宽、高 |
| Type      | int  | 0:未戴口罩; 1:口罩佩戴不规范; 2:正确佩戴口罩 |
| Color  | string  | 口罩颜色, 范围:white,black,blue,other  |
| Uncovered  | []string  | 口罩未覆盖的位置,范围:nose,mouth  |
