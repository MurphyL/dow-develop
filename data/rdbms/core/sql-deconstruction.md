## `SQL`解构

> `SQL`的语法顺序与执行顺序`SQL`语句的执行顺序跟其语句的语法顺序并不一致。

### SQL 语句的语法顺序是：

1. SELECT[DISTINCT]
2. FROM
3. JOIN ON 
4. WHERE
5. GROUP BY
6. HAVING
7. UNION
8. ORDER BY

### 其执行顺序为：

1. FROM
2. JOIN ON
3. WHERE
4. GROUP BY
5. HAVING
6. SELECT
7. DISTINCT
8. UNION
9. ORDER BY

### 需要注意的是：

1、`FROM`才是`SQL`语句执行的第一步。数据库在执行`SQL`语句的第一步是将数据从硬盘加载到数据缓冲区中，以便对这些数据进行操作。
2、`SELECT`是在大部分语句执行了之后才执行的，严格的说是在`FROM`和`GROUP BY`之后执行的。这就是你不能在`WHERE`中使用在`SELECT`中设定别名的字段作为判断条件的原因。
3、并非所有SQL都按照上述的顺序进行。

### 参考资料

- [学好SQL，数据分析就已经入门一半](https://zhuanlan.zhihu.com/p/92847419)