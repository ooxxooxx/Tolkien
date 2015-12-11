* [./](./content/README.md)

##综述

###文档说明
* 本文是XSH后台API接口文档
* 接口版本0.1.0

###统一规格

####1.Header设置
* 说明:app端在请求后端接口时，需要按如下要求设置Header值

* 完整示例：
    * UserId  ："100001"
    * Platform ："Android4.5"
    * Version : "0.1.0"
    * Accept : "application/vnd.xiao10hou.v1+json"
    * ChannelId : "baidu"
    * Content-Type："application/json;charset=utf-8"

* 参数说明：
    * UserId：注册用户的用户ID，若用户未注册，就不设置UserId
    * Platform: 平台及版本，标识调用是Android还是IOS，以及系统的版本
    * Version：标识App的发行版本号
    * Accept：标识后台API的版本
    * ChannelId：Android的渠道号，IOS不设置
    * Content-Type：MIME类型
    
####2.接口返回数据格式
* 说明：接口的返回数据，采用Json格式

* 完整示例：
```javascript
  {
    "timestamp": 1449832944040,
    "code": 0,
    "result": {
                "userId": 100001，
                "nickName":"小时候"，
                "fridens":[100002,100003]
        }
 }
```

* 字段说明
    * timestamp:服务器时间戳，数据类型：long
    * code：返回状态码，数据类型：int
    * result：具体接口的返回值