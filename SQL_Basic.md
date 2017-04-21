# SQL_Basic

```
Select[ALL|DISTINCT|DISTINCTROW|TOP] 
{*|talbe.*|[table.]field1[AS alias1][,[table.]field2[AS alias2][,…]]} 
FROM tableexpression[,…][IN externaldatabase] 
[join...]
[Where…] [and/or][like]
[GROUP BY…] 
[HAVING…] 
[ORDER BY…] [DESC]
[WITH OWNERACCESS OPTION] 

Union
...

```



---
##增
```
 - insert
 - select into 列
 - alter add（drop） 增加、删除列
 - create DB
 - creat table
            CREATE TABLE 表名称
            (
            列名称1 数据类型,
            列名称2 数据类型,
            列名称3 数据类型,
            ....
            )

 - 列属性
    - Not Null 不为空属性
    - Unique 唯一属性，primary·key具有unique属性
    - Primary Key
    - Foreign Key
    - Check 限定列为特定范围内的值
    - default 设置列的默认项
    
  - 辅助手段  
    （Index）用于查询加速
     (AUTO_INCREMENT)自动增加序列
     View结果集可视化的表
     数据类型
        -Date
         Nulls



```
##删
```
 - delete 删除行
 - drop 删除索引、表、数据库
 - alter add（drop） 增加、删除列

```
##查
```
 - select
 - select top
 - seletc distinct
 - select where (in) (between and)
 - select order by
 - where like pattern  正则匹配
 - select as 列改名
 - 
 - Join(Inner join), left join, right join, full join
        SELECT Persons.LastName, Persons.FirstName, Orders.OrderNo
        FROM Persons
        LEFT JOIN Orders
        ON Persons.Id_P=Orders.Id_P
        ORDER BY Persons.LastName
        
- 辅助手段
    - create index 有助于快速查询
 - 
```
##改 
```
update
```
##算
```
平均数 avg()
行计数 count()
访问第一个元素 fisrt（）
访问最后一个元素 last（）
最小数 min（）
最大数 max（）
求和 sum（）
分组+分组条件 Group by + Having
字母大写 ucase
字母小写 lcase
提取字符 mid
字符串长度 len
四舍五入 round
格式化 format

```



