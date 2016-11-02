# 前言

HTTP协议是无状态协议，请求之后会销毁所有数据，并且两个请求之间不能共享数据，而 COOKIE 和 SESSION 主要就解决了这个问题。

# COOKIE解决了什么问题

> 最常见的用户登录功能的实现，基本都是基于 COOKIE 和 SESSION 的。

为什么每次我都把 COOKIE 和 SESSION 放在一起说？

因为他们用来解决相同的问题，只不过方法不同而已。

# 学习资料

[http://php.net/manual/zh/reserved.variables.cookies.php](http://php.net/manual/zh/reserved.variables.cookies.php)

# 基础语法

> $_COOKIE说到底就是个数组，它是预定义变量，和普通数组的唯一区别就是：能够跨网页读写数据，并且关闭网页后，数据还在。

**创建 cookie**

```
setcookie( 'name', 'value', time()+3600, '/' );
```

```
setcookie() 系统函数，直接用就行
name 是 COOKIE的名字
value 是对应的值
time()+3600 表示有效期为当前时间 + 3600秒（1小时）
/ 表示在域名下所有文件夹都生效
... 还有更多参数，可自行阅读手册
```

**获取 COOKIE**

```
//同域名下，任何代码文件均可获取
echo $_COOKIE['name'];
```

$_COOKIE 是PHP预定义的超全局变量，和 $_GET $_POST 雷同。

**销毁COOKIE**

```
//清空值，并且赋予一个历史时间，使其立刻过期
setcookie(name,null, time()-1000)
```

# COOKIE 的原理

1. setcookie() 这个系统函数，会向客户端浏览器写入一个键值对。
2. 之后，浏览器每次请求网址，都会携带cookie。
3. php 通过 $_COOKIE 接收客户端的数据，用于识别是哪台客户端。

# 总结

COOKIE 和 SESSION 对于新人来说，颇有难度，一定要配合实战，本章只是做基本的语法讲解。

答疑微信：pmtt9121