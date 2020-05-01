### 数据类型遵循原则：

1. 符合应用要求，尽量使用短的数据类型    能有效节省存储空寂，有效提升数据的计算性能
2. 数据类型越简单越好，能用int绝不用char   连接查询效率更高
3. 尽量采用精确小数类型   保证数据计算的准确度，节省存储空间
4. 尽量避免null字段，推荐使用0或者其他字段代替null。 因为null很难进行SQL语句优化查询。



### 数据库操作

1. 建表

   create table '表名' ();

2. 删表

   drop table '表名';   删除后，表不存在

3. 修改表结构

   alter table 表名 {alter column 字段名 数据类型 | add 新字段名 数据类型 [约束性] | drop column 字段名} 

   e.g: 表名：student 

4. 插入语句

   insert  into 表名(字段值1，字段值2, ..., 字段值n) value(n1, n2, ..., n)

   更新语句：

   update 表名 set 字段名 <条件表达式> where<条件判断>

5. 删除语句

   delete from 表名 where <条件判断>

6. 清空表结构

​      truncate table 表名  注：只是清空表里面数据，表存在



### SQL数据查询功能

#### 单表查询

select （*|字段名）from 表名；有显示重复信息

select distinct  (*|字段名）from 表名;   不显示重复信息

空值查询：用IS， 不能用=