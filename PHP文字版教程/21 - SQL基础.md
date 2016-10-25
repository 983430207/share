# 前言

想对数据库进行任何操作，必须通过SQL语句，它就好像命令一样。

> SQL是一种语言，原本是通用的，但每种数据库都会在基础SQL上添加自己的特色。

# 术语

- 增，向数据库写入数据
- 删，删除已有数据
- 改，修改数据
- 查，从数据库读取数据

# 学习资料

[https://www.sodevel.com/mysql](https://www.sodevel.com/mysql)

# 准备工作

```
创建数据表：users
```

id(自增主键) | username | password
------------|------------|------------
1|波比|123456
2|张三|123456

# SQL 的基本概念

SQL 其实就是有格式的字符串，数据库来解析这个字符串，确认你的命令。

SQL语句的顺序很重要，不要随便调换！！

# 增

> 向数据库中写入数据

**语句**

```
insert into users (`username`,`password`) values ('name','passwd')
```

```insert into``` 关键字，表示插入数据

```users``` 目标数据表

```(username,password)``` 目标字段

```values``` 关键字

```('name','passwd')``` 每个字段对应的值

**在PHP中执行**

```
$sql = "insert into users (`username`,`password`) values ('name','12345')";
$is = $db->query($sql);

if( $is == true ){
    echo "插入成功";
}else{
    echo "插入失败";
}
```

```$db``` 是上文连接成功后得到的对象，还记得吗？

# 删

**语法**

```
delete from users WHERE id='3'
```

```delete``` 关键字，表示删除数据

```from users``` 目标数据表

```WHERE``` 筛选目标数据，没有它就会删除所有数据

```id='3'``` 只删除 ID= 3 的数据。

**在PHP中执行**

参考 写数据 的方法，就不重复介绍了。

# 改


```
update set users username='新值', password='新值' WHERE id=3
```

```update``` 关键字，表示插入数据

```set users``` 目标数据表

```username='新值', password='新密码'``` 要修改的字段值

```WHERE id=3``` 筛选目标数据

# 查

> 从数据库中取数据，比增删改要多一步。

**基本语法**

```
select * from users where id>1 order by id desc limit 0,2
```

```select``` 关键字，表示要取数据

```*``` 取出哪些字段的值？*号代表所有，也可以使用 id,username这样的格式

```from users``` 目标数据表

---

> 这些都是可有可无的，但是顺序不能颠倒！！

```where id>1``` 筛选目标数据，否则取出所有数据

```order by id``` 根据ID进行排序，没有的话使用默认排序

```desc``` 倒序，对应的是 asc 是正序。

```limit 0,2``` 对结果数量进行限制，0,2表示只要前两条数据。

**使用PHP获取数据**

> 代码较多，涉及多个知识点，请注意！

```
$mysqli_result = $db->query("select * from users");

$rows = array();
while( $row = $mysqli_result->fetch_array( MYSQLI_ASSOC ) ){
    $rows[] = $row;
}
var_dump( $rows );
```

```$mysqli_result``` 如果 ```$db->query()``` 执行的是 SELECT的语句，就会返回系统类```mysqli_result```的实例化对象。其他的是 true/false ）

mysqli_result 手册地址：[http://php.net/manual/zh/class.mysqli-result.php](http://php.net/manual/zh/class.mysqli-result.php)

```$rows``` 定义数组，用于保存取出来的数据

---

```while(){}``` 使用循环结构遍历数据。

```$row = $mysqli_result->fetch_array()``` 每调用一次fetch_array，就会取出一条数据，直到所有数据都显示完毕，我们将它保存在 $row 变量。

```MYSQLI_ASSOC``` （可选）内置常量，表示需要一个关联数组地。

```$rows[] = $row``` 将每次取出的数据，都保存在 $rows 这个二维数组里。

```var_dump($rows)``` 看看你的数据，标准的二维数组，之后你可以用对付数组的任何方法来处理它。

# WHERE 过滤

SQL的一部分，用于过滤数据，支持从简单到复杂的各种查询。

```
//给大家演示一些常见语法

WHERE id = 3
where id = 3 and name = '张三'
where id > 3 and name <> '张三' or password = '12345'
where ...
```

# 总结

SQL语法千变万化，本文介绍的只是最基础的一些操作，一定要多用多学多思考。

