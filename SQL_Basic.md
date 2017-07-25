## Hive SQL调优小tips

1. 尽量使用left join  或者  right join，join可能会导致两表关联后记录数变多；

使用on而不是where作为连接条件；

错误的SQL

```sql
SELECT * FROM fracture_act JOIN fracture_ads  
WHERE fracture_act.planner_id = fracture_ads.planner_id;  
```

正确的SQL

```sql
SELECT * 
FROM fracture_act JOIN fracture_ads  
ON  fracture_act.planner_id = fracture_ads.planner_id; 
```



2. join前先通过限定分区查询出子表，再join子表，具体实例如下：

错误的SQL

```sql
SELECT b.pt,a.phone
FROM pbs_dw.ods_r_survey_result a
LEFT JOIN dj_dw.dw_pag_portrait b
ON to_date(a.busi_date)=b.pt
AND a.phone=b.mob
WHERE a.bu_id='6'and a.is_driver='0'and b.pt>='{start_date}'and [b.pt](http://b.pt/)<='{end_date}'
AND concat_ws('-', a.year, a.month, a.day) >= '${start_date}'
AND concat_ws('-', a.year, a.month, a.day) <= '${end_date}'
```

正确的SQL

```sql
SELECT b.pt,a.phone
FROM 
(SELECT phone,bu_id,is_driver,busi_date
FROM pbs_dw.ods_r_survey_result
WHERE concat_ws('-', year, month, day)>= '2017-07-01'
AND concat_ws('-', year, month, day) <= '2017-07-05') a
LEFT JOIN 
(SELECT pt,mob
FROM dj_dw.dw_pag_portrait
WHERE pt>='2017-07-01'
AND pt<='2017-07-05') b
ON (to_date(a.busi_date)=b.pt AND a.phone=b.mob)
WHERE a.bu_id='6'and a.is_driver='0'

```



3. order by后需要加limit

错误的SQL

```sql
SELECT driver_id
FROM gulfstream_dw.dw_v_driver_base
WHERE concat_ws('-',year,month,day)='2016-09-08  order by  driver_id 
```

正确的SQL

```sql
SELECT driver_id
FROM gulfstream_dw.dw_v_driver_base
WHERE concat_ws('-',year,month,day)='2016-09-08  order by  driver_id   limit 1000
```





## SQL_Basic

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
###增
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
###删
```
 - delete 删除行
 - drop 删除索引、表、数据库
 - alter add（drop） 增加、删除列

```
###查
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
###改 
```
update
```
###算
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



