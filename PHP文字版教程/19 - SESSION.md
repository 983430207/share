# 前言

HTTP协议是无状态协议，请求之后会销毁所有数据，并且两个请求之间不能共享数据，而 SESSION 和 COOKIE 主要就解决了这个问题。

# 学习资料

[http://php.net/manual/zh/reserved.variables.session.php](http://php.net/manual/zh/reserved.variables.session.php)

# SESSION 和 COOKIE 有什么不同

> 注意：默认情况下，SESSION内部也是向客户端添加了一个COOKIE的，只不过我们不知道而已。

**数据存储方式**

SESSION 将值 存在服务器端。

COOKIE 将值 存在客户端。

**有效期**

COOKIE 通过设置有效期可以长时间留存。

SESSION 默认关闭网页数据就清空。

**其他**

就不是新手需要关注的了。

# 基础语法

> SESSION说到底就是个数组，它是预定义变量，和普通数组的唯一区别就是：能够跨网页读写数据。

**设置SESSION**

```
session_start();
$_SESSION['键'] = '值';

session_start() 是系统函数，必须先调用该函数，才能使用session。
$_SESSION 就是一个数组，完全可以像操作数组一样用它。
```

**获取SESSION中的值**

```
//设置SESSION后，同域名下代码文件均可获取。
session_start();

echo $_SESSION['键'];
```

# 总结

SESSION 和 COOKIE 是关联性很强的知识，很多时候我们二选一的用就行了。

记住学习重点：他们能够跨网页读写数据，并且关闭网页后数据可以留存。