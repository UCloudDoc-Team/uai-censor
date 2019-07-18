{{indexmenu_n>10}}

==== 环境准备 ====

##1. 环境要求

- Python 2.7
- UAI-Censor SDK
    - git clone https://github.com/ucloud/uai-saas-sdk.git
    - sudo python setup.py install


##2. UAI-Censor 工具一览

| 命令子类       | 命令名称       | 命令说明            |
| resource   | create      | 创建UAI审查资源 |
|            | delete      | 删除UAI审查资源 |
|			   | modifyname  | 修改资源名称信息 |
| 			   | modifymemo  | 修改资源备注信息 |
|            | modifyoss   | 修改资源oss授权信息 |
|            | list        | 获取资源列表 |
|            | listtype    | 获取资源类型列表 |
|            | listrecord  | 获取资源请求记录 |
| video      | create      | 创建UAI视频审查任务 |
|            | query       | 查询UAI视频审查任务状态 |
| image      | create      | 创建UAI图片审查任务 |
|            | query       | 查询UAI图片审查任务状态|
| frame      | fullcut     | 创建UAI截帧任务, 获取完整视频的截图 |
|			   | snapshot    | 创建UAI截帧任务, 获取视频的首张图片 |
|            | query       | 查询UAI截帧任务状态 |
| signature  | gen         | 生成signature |

##3. 使用说明

  cd tools
  python censor_tool.py {resource,video,image,frame,signature} ...
  