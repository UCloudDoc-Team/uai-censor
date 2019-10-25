

# 接入流程

- **登录UCloud控制台，进入UAI内容审核产品页**

 UCloud控制台地址： https://console.ucloud.cn/dashboard，用户在登录前需要先完成账号的注册。

 进入控制台页面后，点击左上角的“全部产品”选项，选择“人工智能”下的“AI内容审核”，进入UAI内容审核产品页面。

 {{ :ai:uai-censor:access:0.png?nolink |}}

- **创建UAI内容审核资源**

 点击UAI内容审核页面的“创建应用”选项。

 {{ :ai:uai-censor:access:1.png?nolink |}}

 按需填写所需信息，点击“确认”选项，创建资源。
 {{ :ai:uai-censor:access:2.png?nolink |}}

 资源成功创建后，页面会弹出新创建资源的信息，包括应用名称以及应用ID。
 {{ :ai:uai-censor:access:3.jpg?nolink |}} 

- **快速上手UAI内容审核**

 控制台页面为用户提供了“快速上手”的功能，方便用户更快地接入UAI内容审核。使用方法如下：

 在UAI内容审核产品页面选择“快速上手”的选项卡，进入快速上手页面。
 {{ :ai:uai-censor:access:4.jpg?nolink |}} 

 若之前已经创建过内容审核的资源，可跳过第一步。填写第二步中所需的信息，点击“验证“选项。
 {{ :ai:uai-censor:access:5.jpg?nolink |}} 

 请求成功后会在页面右半部分显示请求体和返回体的详细信息。

 - 请求**非正常**返回时，"Response"的信息中"RetCode"字段不为0，"Meesage"字段会简单说明错误原因。

 {{ :ai:uai-censor:access:6.png?nolink |}} 

 - 请求**正常**返回时，"Response"的信息中"RetCode"字段为0，测试图片会显示供用户确认审核结果是否符合预期。

 {{ :ai:uai-censor:access:7.jpg?nolink |}} 

- **开始文件内容审核**

 内容审核服务提供两种调用方式，具体信息如下：

 - [[ai:uai-censor:api:censor|Restful API]]
 - [[ai:uai-censor:pysdk:censor|Python SDK]]

 

