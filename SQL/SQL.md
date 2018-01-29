E![Screen Shot 2018-01-27 at 9.29.36 PM](/Users/chenm/Desktop/Screen Shot 2018-01-27 at 9.29.36 PM.png)

## SQL 语句

| 语句                                       | 语法                                       |
| ---------------------------------------- | ---------------------------------------- |
| AND / OR                                 | SELECT column_name(s)FROM table_nameWHERE conditionAND\|OR condition |
| ALTER TABLE (add column)                 | ALTER TABLE table_name ADD column_name datatype |
| ALTER TABLE (drop column)                | ALTER TABLE table_name DROP COLUMN column_name |
| AS (alias for column)                    | SELECT column_name AS column_aliasFROM table_name |
| AS (alias for table)                     | SELECT column_nameFROM table_name  AS table_alias |
| BETWEEN                                  | SELECT column_name(s)FROM table_nameWHERE column_nameBETWEEN value1 AND value2 |
| CREATE DATABASE                          | CREATE DATABASE database_name            |
| CREATE INDEX                             | CREATE INDEX index_nameON table_name (column_name) |
| CREATE TABLE                             | CREATE TABLE table_name(column_name1 data_type,column_name2 data_type,.......) |
| CREATE UNIQUE INDEX                      | CREATE UNIQUE INDEX index_nameON table_name (column_name) |
| CREATE VIEW                              | CREATE VIEW view_name ASSELECT column_name(s)FROM table_nameWHERE condition |
| DELETE FROM                              | DELETE FROM table_name (**Note: **Deletes the entire table!!)*or*DELETE FROM table_nameWHERE condition |
| DROP DATABASE                            | DROP DATABASE database_name              |
| DROP INDEX                               | DROP INDEX table_name.index_name         |
| DROP TABLE                               | DROP TABLE table_name                    |
| GROUP BY                                 | SELECT column_name1,SUM(column_name2)FROM table_nameGROUP BY column_name1 |
| HAVING                                   | SELECT column_name1,SUM(column_name2)FROM table_nameGROUP BY column_name1HAVING SUM(column_name2) condition value |
| IN                                       | SELECT column_name(s)FROM table_nameWHERE column_nameIN (value1,value2,..) |
| INSERT INTO                              | INSERT INTO table_nameVALUES (value1, value2,....)*or*INSERT INTO table_name(column_name1, column_name2,...)VALUES (value1, value2,....) |
| LIKE                                     | SELECT column_name(s)FROM table_nameWHERE column_nameLIKE pattern |
| ORDER BY                                 | SELECT column_name(s)FROM table_nameORDER BY column_name [ASC\|DESC] |
| SELECT                                   | SELECT column_name(s)FROM table_name     |
| SELECT *                                 | SELECT *FROM table_name                  |
| SELECT DISTINCT                          | SELECT DISTINCT column_name(s)FROM table_name |
| SELECT INTO(used to create backup copies of tables) | SELECT *INTO new_table_nameFROM original_table_name*or*SELECT column_name(s)INTO new_table_nameFROM original_table_name |
| TRUNCATE TABLE(deletes only the data inside the table) | TRUNCATE TABLE table_name                |
| UPDATE                                   | UPDATE table_nameSET column_name=new_value[, column_name=new_value]WHERE column_name=some_value |
| WHERE                                    | SELECT column_name(s)FROM table_nameWHERE condition |

## To use SQL in your website

要创建发布数据库中数据的网站，您需要以下要素：

- RDBMS 数据库程序（比如 MS Access, SQL Server, MySQL）
- 服务器端脚本语言（比如 PHP 或 ASP）
- SQL
- HTML / CSS



## RDBMS

RDBMS 指的是关系型数据库管理系统。

RDBMS 是 SQL 的基础，同样也是所有现代数据库系统的基础，比如 MS SQL Server, IBM DB2, Oracle, MySQL 以及 Microsoft Access。

RDBMS 中的数据存储在被称为表（tables）的数据库对象中。

表是相关的数据项的集合，它由列和行组成

## 数据库表

一个数据库通常包含一个或多个表。每个表由一个名字标识（例如“客户”或者“订单”）。表包含带有数据的记录（行）。

下面的例子是一个名为 "Persons" 的表：

| Id   | LastName | FirstName | Address        | City     |
| ---- | -------- | --------- | -------------- | -------- |
| 1    | Adams    | John      | Oxford Street  | London   |
| 2    | Bush     | George    | Fifth Avenue   | New York |
| 3    | Carter   | Thomas    | Changan Street | Beijing  |

上面的表包含三条记录（每一条对应一个人）和五个列（Id、姓、名、地址和城市）。

您需要在数据库上执行的大部分工作都由 SQL 语句完成。

下面的语句从表中选取 LastName 列的数据：

```
SELECT LastName FROM Persons
```

*SQL 对大小写不敏感*！

## SQL DML 和 DDL

可以把 SQL 分为两个部分：数据操作语言 (DML) 和 数据定义语言 (DDL)。

SQL (结构化查询语言)是用于执行查询的语法。但是 SQL 语言也包含用于更新、插入和删除记录的语法。

查询和更新指令构成了 SQL 的 DML 部分：

- *SELECT* - 从数据库表中获取数据
- *UPDATE* - 更新数据库表中的数据
- *DELETE* - 从数据库表中删除数据
- *INSERT INTO* - 向数据库表中插入数据

SQL 的数据定义语言 (DDL) 部分使我们有能力创建或删除表格。我们也可以定义索引（键），规定表之间的链接，以及施加表间的约束。

SQL 中最重要的 DDL 语句:

- *CREATE DATABASE* - 创建新数据库
- *ALTER DATABASE* - 修改数据库
- *CREATE TABLE* - 创建新表
- *ALTER TABLE* - 变更（改变）数据库表
- *DROP TABLE* - 删除表
- *CREATE INDEX* - 创建索引（搜索键）
- *DROP INDEX* - 删除索引

#### SELECT DISTINCT

选取唯一不同值

```
SELECT DISTINCT Company FROM Orders 
```

#### SELECT … WHERE

按条件选取

```
SELECT * FROM Persons WHERE City='Beijing'
```

###### 引号使用

请注意，我们在例子中的条件值周围使用的是单引号。

SQL 使用单引号来环绕*文本值*（大部分数据库系统也接受双引号）。如果是*数值*，请不要使用引号

###### 文本值：

```
这是正确的：
SELECT * FROM Persons WHERE FirstName='Bush'

这是错误的：
SELECT * FROM Persons WHERE FirstName=Bush

```

###### 数值：

```
这是正确的：
SELECT * FROM Persons WHERE Year>1965

这是错误的：
SELECT * FROM Persons WHERE Year>'1965'
```

#### AND / OR

```SELECT * FROM Persons WHERE firstname=&#39;Thomas&#39; OR lastname=&#39;Carter&#39;
SELECT * FROM Persons WHERE FirstName='Thomas' AND LastName='Carter'
```

```
SELECT * FROM Persons WHERE firstname='Thomas' OR lastname='Carter'
```

```
SELECT * FROM Persons WHERE (FirstName='Thomas' OR FirstName='William')
AND LastName='Carter'
```

#### ORDER BY 

语句用于根据指定的列对结果集进行排序。默认按照升序对记录进行排序

```
SELECT Company, OrderNumber FROM Orders ORDER BY Company
```

以逆字母顺序显示公司名称，并以数字顺序显示顺序号：

```
SELECT Company, OrderNumber FROM Orders ORDER BY Company DESC, OrderNumber ASC
```

—>

| Company  | OrderNumber |
| -------- | ----------- |
| W3School | 2356        |
| W3School | 6953        |
| IBM      | 3532        |
| Apple    | 4698        |

注意：在以上的结果中有两个相等的公司名称 (W3School)。只有这一次，在第一列中有相同的值时，第二列是以升序排列的。如果第一列中有些值为 nulls 时，情况也是这样的。

```
INSERT INTO 表名称 VALUES (值1, 值2,....)
```

我们也可以指定所要插入数据的列：

```
INSERT INTO table_name (列1, 列2,...) VALUES (值1, 值2,....)
```

#### UPDATE

```
UPDATE 表名称 SET 列名称 = 新值 WHERE 列名称 = 某值
UPDATE Person SET FirstName = 'Fred' WHERE LastName = 'Wilson' 
```

#### DELETE

```
DELETE FROM 表名称 WHERE 列名称 = 值
DELETE FROM Person WHERE LastName = 'Wilson' 
```

#### TOP

```
SELECT TOP number|percent column_name(s)
FROM table_name
```

###### MySQL 和 Oracle 中的 SQL SELECT TOP 是等价的

```
SELECT *
FROM Persons
LIMIT 5
```

#### LIKE

```
SELECT column_name(s)
FROM table_name
WHERE column_name LIKE pattern
```

从 "Persons" 表中选取居住在包含 "lon" 的城市里的人

```
SELECT * FROM Persons
WHERE City LIKE '%lon%'
```

##### SQL 通配符

在搜索数据库中的数据时，SQL 通配符可以替代一个或多个字符。

SQL 通配符必须与 LIKE 运算符一起使用。

在 SQL 中，可使用以下通配符

| 通配符                      | 描述            |
| ------------------------ | ------------- |
| %                        | 替代一个或多个字符     |
| _                        | 仅替代一个字符       |
| [charlist]               | 字符列中的任何单一字符   |
| [^charlist]或者[!charlist] | 不在字符列中的任何单一字符 |

现在，我们希望从上面的 "Persons" 表中选取居住的城市以 "A" 或 "L" 或 "N" 开头的人：

我们可以使用下面的 SELECT 语句：

```
SELECT * FROM Persons
WHERE City LIKE '[ALN]%'
```

#### SELECT IN 允许我们在 WHERE 子句中规定多个值。

```
SELECT column_name(s)
FROM table_name
WHERE column_name IN (value1,value2,...)
```

#### SELECT BETWEEN 操作符在 WHERE 子句中使用，作用是选取介于两个值之间的数据范围

```
SELECT column_name(s)
FROM table_name
WHERE column_name
BETWEEN value1 AND value2
```

###### **重要事项：不同的数据库对 BETWEEN...AND 操作符的处理方式是有差异的。某些数据库会列出介于 "Adams" 和 "Carter" 之间的人，但不包括 "Adams" 和 "Carter" ；某些数据库会列出介于 "Adams" 和 "Carter" 之间并包括 "Adams" 和 "Carter" 的人；而另一些数据库会列出介于 "Adams" 和 "Carter" 之间的人，包括 "Adams" ，但不包括 "Carter" 。所以，请检查你的数据库是如何处理 BETWEEN....AND 操作符的！**

##### 表的 SQL Alias 语法

```
SELECT column_name(s)
FROM table_name
AS alias_name
```

##### 列的 SQL Alias 语法

```
SELECT column_name AS alias_name
FROM table_name
```

e.g.

```
SELECT po.OrderID, p.LastName, p.FirstName
FROM Persons AS p, Product_Orders AS po
WHERE p.LastName='Adams' AND p.FirstName='John'
```

#### SELECT JOIN

##### Join 和 Key

有时为了得到完整的结果，我们需要从两个或更多的表中获取结果。我们就需要执行 join。

数据库中的表可通过键将彼此联系起来。主键（Primary Key）是一个列，在这个列中的每一行的值都是唯一的。在表中，每个主键的值都是唯一的。这样做的目的是在不重复每个表中的所有数据的情况下，把表间的数据交叉捆绑在一起。

| Id_P | LastName | FirstName | Address        | City     |
| ---- | -------- | --------- | -------------- | -------- |
| 1    | Adams    | John      | Oxford Street  | London   |
| 2    | Bush     | George    | Fifth Avenue   | New York |
| 3    | Carter   | Thomas    | Changan Street | Beijing  |

请注意，"Id_P" 列是 Persons 表中的的主键。这意味着没有两行能够拥有相同的 Id_P。即使两个人的姓名完全相同，Id_P 也可以区分他们。

接下来请看 "Orders" 表：

| Id_O | OrderNo | Id_P |
| ---- | ------- | ---- |
| 1    | 77895   | 3    |
| 2    | 44678   | 3    |
| 3    | 22456   | 1    |
| 4    | 24562   | 1    |
| 5    | 34764   | 65   |

请注意，"Id_O" 列是 Orders 表中的的主键，同时，"Orders" 表中的 "Id_P" 列用于引用 "Persons" 表中的人，而无需使用他们的确切姓名。

请留意，"Id_P" 列把上面的两个表联系了起来。