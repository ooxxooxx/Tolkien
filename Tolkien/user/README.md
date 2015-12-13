
[<<](../README.md)

##用户模块接口

* <span id="catalog">[目录](#10) </span>
    * [手机注册步骤](#1) 
    * [手机注册接口](#2) 
    * [手机登录接口](#3) 
    * [发送验证码接口](#4)
    * [取得用户详情接口](#5)

###<h2 id="1">手机注册步骤</h2>

* 手机号注册分两步：

* 1.调用[`发送验证码接口`](#4)接口发送验证码
    
    `POST : /actions/sms`
    
```javascript
{
    "tel":{
        "dialCode":86,    // Int类型
        "number":13699851562  // Long类型
    },
    "action":"signup"
}
```

* 2.调用[`手机注册接口`](#2)完成手机注册
    
    `POST: /users`
  
```javascript
{
    "tel":{
        "dialCode":86,
        "number":13699851561
    },
    "password":"909123",
    "captcha":"909"
}
```
* 注意：
    * 手机号的dialCode和number都是Number类型
    * 由于当前验证码平台未达到上线要求，所以每个手机号每天只能请求三次
    * 由于有请求限制，所以设置了`909`为万能验证码。可以直接输入909通过验证码的验证。
    
[返回目录](#10)

###<h2 id="2">手机注册接口</h2>

* 说明:手机注册

* 请求方法:`POST`

* 请求URL：`/users`

* 返回说明：用户信息

* 返回示例：

```javascript
{
    "userId": 100015,
    "nickName": "小时候用户100015",
    "tel": {
      "dialCode": 86,
      "number": 13699851568
    },
    "avatar": null,
    "gender": "none",
    "signature": null
}
```

* 字段说明
    * userId: 用户ID
    * nickName : 用户昵称
    * tel : 手机号
    * avatar：用户头像
    * gender: none-未设置，m-女，f-男
    * signature ： 用户签名，例如：“今天心情不好...”
    
* 异常校验

* 1.如果输入的手机号已经在app中注册了，返回：

```javascript
{
  "timestamp": 1449949634821,
  "code": 403,
  "error": "用户已存在。"
}
```
* 2.如果输入的密码中包含特殊字符，比如中文的括号，返回:

```javascript
{
  "timestamp": 1449949634821,
  "code": 403,
  "error": "请去除密码中的特殊字符。"
}
```
* 3.如果验证码错误，返回:

```javascript
{
  "timestamp": 1449949634821,
  "code": 403,
  "error": "验证码错误，请重新输入。"
}
```
[返回目录](#10)

###<h2 id="3">手机登录接口</h2>

* 说明:手机登录

* 请求方法:`POST`

* 请求URL：`/users/signin`

* 返回说明：用户信息

* 返回示例：

```javascript
{
    "userId": 100015,
    "nickName": "小时候用户100015",
    "tel": {
      "dialCode": 86,
      "number": 13699851568
    },
    "avatar": null,
    "gender": "none",
    "signature": null
}
```

* 字段说明
    * userId: 用户ID
    * nickName : 用户昵称
    * tel : 手机号
    * avatar：用户头像
    * gender: none-未设置，m-女，f-男
    * signature ： 用户签名，例如：“今天心情不好...”
    
* 异常校验

* 1.如果用户不存在或密码错误，返回：

```javascript
{
  "timestamp": 1449949634821,
  "code": 403,
  "error": "用户不存在或密码错误。"
}
```

[返回目录](#10)

###<h2 id="4">发送验证码接口</h2>

* 说明:发送验证码

* 请求方法:`POST`

* 请求URL：`/actions/sms`

* 返回说明：发送验证码

* 返回示例：

```javascript
{
    "tel":{
        "dialCode":86,
        "number":13699851562
    },
    "action":"signup"
}
```

* 字段说明
    * tel : 手机号
    * action：发送验证码分三种场景
        * signup ：注册
        * resetPassword ：忘记密码
        * resetPhone ：绑定手机号
    
* 异常校验

* 1.如果注册时，手机号已经注册了，返回：

```javascript
{
  "timestamp": 1449949634821,
  "code": 403,
  "error": "您的手机号码已被注册了。"
}
```
* 2.如果忘记密码或绑定手机时，手机号没有注册过，返回：

```javascript
{
  "timestamp": 1449949634821,
  "code": 403,
  "error": "用户不存在。"
}
```

[返回目录](#10)

###<h2 id="5">取得用户详情接口</h2>

* 说明:用户查看自己的详细信息

* 请求方法:`GET`

* 请求URL：`/users/:userId`

* 请求参数： userId-用户ID 

* 返回说明：用户自己的详细信息

* 返回示例：

```javascript
{
    "userId": 100011,
    "nickName": "小时候用户100011",
    "tel": {
      "dialCode": 86,
      "number": 13699851562
    },
    "avatar": null,
    "gender": "none",
    "signature": null
  }
```

* 字段说明 [参照手机注册接口](#2)
    
* 异常校验

* 1.如果用户不存在，返回：

```javascript
{
  "timestamp": 1449949634821,
  "code": 404,
  "error": "用户不存在"
}
```
[返回目录](#10)