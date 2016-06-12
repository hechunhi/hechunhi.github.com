---
title: JSON Web Token的使用
date: 2016-5-2 21:35:40
categories: javascript
tags: 
	- javascript 
	- JSON Web Token
---
### JWT是什么
JWT是基于token的api认证的解决方案，可替代Session。

### JWT与Session有什么不同
 Session的解决方案是通过一个sessionID写入到Cookie，同时在服务端以此sessionID为Key存储用户数据在服务端，因此需要在服务端维持用户状态。

 JWT则通过分配一个加密的token将用户数据在服务端加密后回传到客户端,客户每次请求api需将token发送到服务端,服务端拿到token后进行解密得到之前分配该token时的用户数据。token本身是包含用户数据的，所以服务端并不需要存放用户数据,**JWT是无状态的**。

### JWT的实现是怎样的
JWT包含`header`,`payload`,`signatrue`三个部分：

- header用来存放token本身的信息（类型、编码等）,通常使用base64编码。
```javascript
base64({
    type: 'JWT',
    alg: 'HS256'
});
```
- payload用于存放数据，比如用户信息、产品信息等。
```javascript
base64({
    name:'hugo',
    userid:'238843992'
});
```
- signatrue是包含`header`,`payload`,`secret_key`三个部分的混合体，secret_key作为解密的唯一凭证必须安全的存放在服务端。
```javascript
HMACSHA256(
base64(header),
base64(payload),
secret_key);
```

完整的Token字符串示例： 
```
//header.payload.signtrue
eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI1NTc4MzJkZjk0ZTFjN2YyMDJmYTVlNGUiLCJ1c2VybmFtZSI6InNhbmciLCJwYXNzd29yZCI6IjAwMDAwMCIsImF2YXRhciI6IiIsInBob25lX251bWJlciI6IiIsImFkZHJlc3MiOiIiLCJfX3YiOjB9.Wv5za6GpJSMi346o625_8FxfoM4dJ1cWNuezG10zQG4
```

### Node.js中使用JWT
[未完待续]




### 推荐阅读
[使用 AngularJS & NodeJS 实现基于 token 的认证应用](https://zhuanlan.zhihu.com/p/19920223)
[使用JSON Web Token](http://www.haomou.net/2014/08/13/2014_web_token/)
[【JWT】JWT+HA256加密 Token验证](http://www.cnblogs.com/anny0404/p/5318692.html)
[八幅漫画理解使用JSON Web Token设计单点登录系统](http://www.cnblogs.com/jianjialin/p/5328429.html)
[nodejs实现的jwt代码](http://github.com/auth0/node-jsonwebtoken)
