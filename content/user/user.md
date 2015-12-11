#用户相关接口

##用户注册
@(说明)

 用户注册分三步：
* 手机注册
* 发送验证码
* 手机注册验证
	 
###1.手机注册
* 方法：`POST`
* 链接：`/users`
* 参数：无
* Body：
```javascript
  {
    "loginName" : "13699851562"
    "password" : "123456"
  }
```
* 返回：
```python
  {
    "orderId" : "ogh87yuS87y87y",
    ……
  }
```