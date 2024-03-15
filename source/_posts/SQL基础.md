---
title: SQL基础
date: 2023-04-11 18:20:57
categories: 大数据
comments: true
cover: 'https://s2.loli.net/2024/03/15/2FsIWTqfuboHtEy.png'
tags:
  - SQL
  - 数据库
  - 数据操作
abbrlink: SQLba
---


## 一、数据库概述

### 1、数据库介绍

数据库就是存储数据的仓库，其本质是一个文件系统，按照特定的格式将数据存储起来，用户可以对数据库中的数据进行增加，修改，删除及查询操作。

随着互联网的高速发展，大量的数据在不断的产生，伴随而来的是如何高效安全的存储数据和处理数据，而这一问题成为了信息时代的一个非常大的问题，而使用数据库可以高效的有条理的储存数据。

- 可以结构化存储大量的数据；
- 可以有效的保持数据的一致性、完整性；
- 读写效率极高。

### 2、数据库分类

数据库又分为关系型数据库和非关系型数据库

#### 关系型数据库RDBMS

关系型数据库：指采用了关系模型来组织数据的数据库。

关系模型指的就是二维表格模型，而一个关系型数据库就是由二维表及其之间的联系所组成的一个数据组织。

#### 非关系型数据库NoSQL

非关系型数据库：又被称为NoSQL（Not Only SQL )，意为不仅仅是SQL，对NoSQL 最普遍的定义是“非关联型的”，强调 Key-Value 的方式存储数据。

Key-Value结构存储： Key-value数据库是一种以键值对存储数据的一种数据库，类似Java中的map。可以将整个数据库理解为一个大的map，每个键都会对应一个唯一的值。

![mysql图1.png](https://s2.loli.net/2024/03/15/ASPFqNxer8mgMa9.png)

关系型数据库（RDBMS）和非关系型数据库（NoSQL）是两种不同类型的数据库管理系统，用于存储和管理数据的方式不同，它们之间的一些主要区别如下：

1. 数据结构：关系型数据库使用表格（表）来组织数据，每个表都有固定的列和行。表之间可以建立关系，通过键（键值对）进行连接。而非关系型数据库则没有固定的表结构，数据可以以文档、键值对、列族或者图等形式存储。
2. 可扩展性：非关系型数据库通常具有更好的可扩展性，可以更容易地处理大规模和高并发的数据。关系型数据库在处理大量数据和高并发请求时可能会面临性能瓶颈。
3. 数据一致性：关系型数据库通常具有强一致性，即数据在数据库中的状态是一致的。而非关系型数据库则可能具有弱一致性或最终一致性，即在某一时刻数据在不同节点之间可能存在不一致，但最终会达到一致状态。
4. 灵活性：非关系型数据库通常更加灵活，可以在不需要事先定义数据结构的情况下存储和处理各种不同类型的数据。而关系型数据库需要事先定义表结构，并在存储数据之前进行严格的模式设计。
5. 查询语言：关系型数据库通常使用结构化查询语言（SQL）来查询和操作数据。而非关系型数据库使用不同的查询语言，例如键值对数据库使用键（key）来查询数据，文档数据库使用类似于JSON的查询语法，列族数据库使用列族和列来查询数据。
6. 数据库设计：关系型数据库通常适用于复杂的事务性应用，需要保持数据的一致性和完整性，如金融系统、人力资源管理系统等。而非关系型数据库通常适用于需要处理大量半结构化或非结构化数据、需要高度可扩展性和灵活性的应用，如社交媒体、物联网应用、日志数据等。

### 3、常见数据库介绍

####  关系型数据库

| **数据库**    | **介绍**                                                     |
| ------------- | ------------------------------------------------------------ |
| **MySQL**     | 开源免费的中型数据库,已经被Oracle收购.MySQL6.x版本也开始收费。 |
| **Oracle**    | 收费的大型数据库，Oracle公司的产品。Oracle收购SUN公司，收购MYSQL。 |
| **DB2**       | IBM公司的数据库产品,收费的。常应用在银行系统中.              |
| **SQLserver** | MicroSoft 公司收费的中型的数据库。C#、.net等语言常使用。     |
| **SQLite**    | 嵌入式的小型数据库，应用在手机端。                           |

#### 非关系型数据库

| **数据库**  | **介绍**                                                     |
| ----------- | ------------------------------------------------------------ |
| **Redis**   | 是一个小而美的数据库，主要用在key-value的内存缓存，读写性能极佳 |
| **HBase**   | HBase是列式数据库，目标是高效存储大量数据                    |
| **MongoDB** | MongoDB是文档型数据库，非常接近关系型数据库的。              |

## 二、MySQL数据库

### 1、MySQL介绍

MySQL是一个关系型数据库管理系统，在 WEB 应用方面，MySQL是最好的 RDBMS (Relational Database Management System，关系数据库管理系统) 应用软件，它是由瑞典MySQL AB 公司开发，目前属于 Oracle 旗下产品，MySQL 是最流行的关系型数据库管理系统中的一个。

### 2、MySQL特点

1.MySQL支持大型的数据库。可以处理拥有上千万条记录的大型数据库。
        2.MySQL使用标准的SQL数据语言形式。
        3.MySQL可以安装在不同的操作系统，并且提供多种编程语言的操作接口。这些编程语言包括C、C++、Python、Java、Ruby等等。

### 3、MySQL版本

MySQL Community Server：社区版本，开源免费，但不提供官方技术支持。

MySQL Enterprise Edition：企业版本，需付费，可以试用30天。

MySQL Cluster：集群版，开源免费。可将几个MySQL Server封装成一个Server。

MySQL Cluster CGE：高级集群版，需付费。

MySQL Workbench（GUITOOL）：一款专为MySQL设计的ER/数据库建模工具。它是著名的数据库设计工具DBDesigner4的继任者。MySQL Workbench又分为两个版本，分别是社区版（MySQL Workbench OSS）、商用版（MySQL WorkbenchSE）。

## 三、Linux系统MySQL使用

### 1、登陆MySQL数据库

MySQL是一个需要账户名密码登录的数据库，登陆后使用，它提供了一个默认的root账号，使用安装时设置的密码即可登录，目前有两种登录场景：

####  本地登录

```
# mysql -uroot –p 回车  
password：输入密码
```

-u 后面是登录的用户名
        -p 后面是登录密码, 如果不填写, 回车之后会提示输入密码

#### 远程登录

```
# mysql -h 远程服务器IP地址 -P 端口号 -u用户名 -p 回车
password：输入密码
```

#### 退出

```
mysql> exit

mysql> quit

快捷键Ctrl + d
```

### 2.DataGrip使用

### 创建工程

点击File->New->Project新建DataGrip工程

输入项目名称，点击确定。

选择新项目打开方式：This Windows（在本窗口中打开），New Windows（在新窗口中打开）， Attach（附加模式）

### 连接数据库

选择Database下的➕，点击DataSource菜单下的MySQL。
       填写对应的参数，连接数据库：连接名，IP，用户名，密码等，点击OK完成连接。
       如果是第一次使用，需要下载mysql驱动文件。



设置数据库时区：

1. 点击Advanced按钮；
2. 在VM options后面写入`-Duser.timezone=Asia/Shanghai



设置完成后，单击Apply（应用），单击OK，连接完成

### 选择要使用的数据库

点击连接名称之后的按钮可以选择所要使用的数据库：![mysql图2.png](https://s2.loli.net/2024/03/15/UgTEJmiSWzwtKH6.png)

### DataGrip软件设置

####  设置字体大小

设置文字大小： File--->settings--->Editor---->Font，可以设置文字尺寸Size和行高Line height

#### 设置关键字大写

设置关键字大写： File--->settings--->Editor---->Code Style--->SQL--->MySql(需要设置的数据库)--->Case

![mysql图3.png](https://s2.loli.net/2024/03/15/l85hCm9oiXQzfIN.png)

#### 自动排版

自动排版布局： File--->settings--->Editor---->Code Style--->SQL--->MySql(需要设置的数据库)--->Queries
自动排版快捷键：Ctrl+ Alt + L![mysql图4.png](https://s2.loli.net/2024/03/15/gecvOzLyQsxPmjR.png)

## 四、SQL语句

### 1、连接数据库

结构化查询语言(Structured Query Language)简称SQL，是关系型数据库管理系统都需要遵循的规范，是数据库认识的语句。不同的数据库生产厂商都支持SQL语句，但都有特有内容。

**举例：**

普通话：各数据库厂商都遵循的ISO标准

方言：数据库特有的关键字

### 2、SQL语句分类

#### DDL

DDL（Data Definition Language）用于定义和管理数据库中的数据结构，包括表、视图、索引、触发器、存储过程、用户等。

DDL通常包括以下几种常见的语句：

1. CREATE：用于创建数据库中的各种对象，如创建表、视图、索引、触发器、存储过程等。例如，CREATE TABLE用于创建表，CREATE VIEW用于创建视图。
2. ALTER：用于修改数据库中已存在的对象，如修改表结构、修改视图定义等。例如，ALTER TABLE用于修改表结构，ALTER VIEW用于修改视图定义。
3. DROP：用于删除数据库中的对象，如删除表、删除视图等。例如，DROP TABLE用于删除表，DROP VIEW用于删除视图。
4. TRUNCATE：用于删除表中的所有数据，并且保留表结构和属性。例如，TRUNCATE TABLE用于删除表中的所有数据。
5. RENAME：用于修改数据库中对象的名称，如修改表名、修改视图名等。例如，RENAME TABLE用于修改表名，RENAME VIEW用于修改视图名。
6. GRANT和REVOKE：用于授权和撤销数据库对象的权限，如授权用户对表进行增、删、改、查操作等。例如，GRANT SELECT, INSERT, UPDATE, DELETE ON table_name TO user_name用于授权用户对表进行查询、插入、更新、删除操作。

DDL语句通常由数据库管理员或具有相应权限的用户执行，用于定义数据库的结构和元数据，对数据库的整体架构进行管理和控制。

#### DML

DML（Data Manipulation Language）用于对数据库中的数据进行操作，包括查询、插入、更新、删除等操作。

DML通常包括以下几种常见的语句：

1. SELECT：用于查询数据库中的数据，包括单表查询、多表查询、嵌套查询、聚合查询、排序、分组等操作。例如，SELECT * FROM table_name用于查询表中的所有数据，SELECT column1, column2 FROM table_name用于查询表中指定列的数据。
2. INSERT：用于向数据库中插入新数据，包括单行插入和多行插入。例如，INSERT INTO table_name (column1, column2) VALUES (value1, value2)用于向表中插入一行数据。
3. UPDATE：用于更新数据库中的数据，可以更新单表或多表中的数据。例如，UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition用于更新表中符合条件的数据。
4. DELETE：用于删除数据库中的数据，可以删除单表或多表中的数据。例如，DELETE FROM table_name WHERE condition用于删除表中符合条件的数据。

DML语句用于对数据库中的数据进行增、删、改、查等操作，由应用程序或数据库用户执行，用于操作数据库中的具体数据记录。DML操作可以通过执行DML语句来实现对数据库中数据的增加、删除、修改和查询。

#### DQL

DQL（Data Query Language）用于查询数据库中的数据，即实现从数据库中获取数据的操作。

DQL通常包括以下几种常见的语句：

1. SELECT：用于查询数据库中的数据，包括单表查询、多表查询、嵌套查询、聚合查询、排序、分组等操作。SELECT语句可以通过指定要查询的表、列、条件、排序方式等来获取数据。例如，SELECT * FROM table_name用于查询表中的所有数据，SELECT column1, column2 FROM table_name用于查询表中指定列的数据。
2. FROM：用于指定要查询的表名，可以查询单个表或多个表的数据。例如，SELECT * FROM table1, table2用于从table1和table2两个表中获取数据。
3. WHERE：用于指定查询的条件，可以使用逻辑运算符、比较运算符、通配符等来定义查询条件。例如，SELECT * FROM table_name WHERE column1 = 'value'用于查询column1等于特定值的数据。
4. ORDER BY：用于指定查询结果的排序方式，可以按照一个或多个列进行升序或降序排序。例如，SELECT * FROM table_name ORDER BY column1 ASC用于按照column1列的升序排序。
5. GROUP BY：用于将查询结果按照一个或多个列进行分组，并对每个分组进行聚合计算。例如，SELECT column1, SUM(column2) FROM table_name GROUP BY column1用于按照column1列的值进行分组，并计算每个分组中column2列的和。
6. JOIN：用于连接多个表的数据，可以通过不同的连接方式（如内连接、外连接、自连接等）来获取联接后的结果。例如，SELECT * FROM table1 INNER JOIN table2 ON table1.id = table2.id用于执行内连接操作，连接两个表的id列相等的记录。

DQL语句用于查询数据库中的数据，并通过结果集返回查询结果。DQL语句可以通过执行查询操作来实现从数据库中获取数据，并支持丰富的查询功能，用于满足应用程序或用户对数据库中数据的查询需求。

#### DCL

DCL（Data Control Language用于控制数据库中的数据访问和权限管理。

DCL主要包括以下两种常见的语句：

1. GRANT：用于授权用户或角色对数据库对象（如表、视图、存储过程等）进行特定的操作权限。GRANT语句可以授权用户或角色执行SELECT、INSERT、UPDATE、DELETE等数据库操作，也可以授权用户或角色对特定的数据库对象进行操作。例如，GRANT SELECT, INSERT ON table_name TO user_name或GRANT UPDATE ON table_name TO role_name用于授权用户或角色对表进行SELECT、INSERT或UPDATE操作。
2. REVOKE：用于撤销用户或角色对数据库对象的操作权限。REVOKE语句可以撤销之前通过GRANT语句授权的权限。例如，REVOKE SELECT ON table_name FROM user_name或REVOKE INSERT ON table_name FROM role_name用于撤销用户或角色对表的SELECT或INSERT权限。

DCL语句用于对数据库中的数据访问进行控制，包括授权用户或角色对数据库对象的操作权限，以及撤销之前授权的权限。通过DCL语句，数据库管理员可以灵活地管理用户或角色对数据库的操作权限，确保数据库的安全性和数据的合法性。

#### 要点

① SQL语句可以单行或多行书写，以分号结尾

② 可使用空格和缩进来增强语句的可读性

③ MySQL数据库的SQL语句不区分大小写，关键字建议使用大写

④ 可以使用单行与多行注释（#和/*）

## 五、DDL数据库操作

### 1、MySQL的组成结构

![mysql图5.png](https://s2.loli.net/2024/03/15/6tPWEkzJH4G9Soh.png)

一个MySQL DBMS可以同时存放多个数据库，理论上一个项目就对应一个数据库

一个数据库中还可以同时包含多个数据表，而数据表才是真正用于存放数据的位置。（类似Office软件中的Excel表格），理论上一个功能就对应一个数据表。如博客系统中的用户管理功能，就需要一个user数据表、博客中的文章就需要一个article数据表、博客中的评论就需要一个message数据表

一个数据表又可以拆分为多个字段，每个字段就是一个属性

一个数据表除了字段以外，还有很多行，每一行都是一条完整的数据（记录）

### 2、数据库的基本操作

#### ① 创建数据库

create database 数据库名称(字母+数字+下划线组成，以字母开头，不能出现中文以及特殊字符，不能重名)

```powershell
mysql> create database 数据库名称 [设置编码格式];
create database if not exists db_itheima default character set utf8 指定默认字符集设置编码格式
```

国内汉字无法通过256个字符进行描述，所以国内开发了自己的编码格式gb2312，升级gbk

中国台湾业开发了一套自己的编码格式big5

很多项目并不仅仅只在本地使用，也可能支持多国语言，标准化组织开发了一套通用编码utf8，后来5.6版本以后又进行了升级utf8mb4

> 编写SQL语句是一个比较细致工作，不建议直接在终端中输入SQL语句，可以先把要写的SQL语句写入一个记事本中，然后拷贝执行。

#### ② 查询数据库

基本语法：显示所有数据库

```powershell
mysql> show databases;
```

#### ③ 删除数据库

基本语法：

```powershell
mysql> drop database 数据库名称;
```

#### ④ 选择数据库

从数据库列表中查找需要使用的数据库 格式：

```mysql
mysql> use datab;
```

查看正在使用的数据库（8.0以后版本需要基于select查询来获取当前数据库）

```powershell
mysql> select database();
```

## 六、DDL数据表操作

特别注意：创建数据表必须有一个前提，首先要明确选择某一个数据库。

### 1、数据表的基本操作

####  数据表的创建

基本语法：

```powershell
mysql> create table 数据表名称(
	字段1 字段类型 [字段约束],
	字段2 字段类型 [字段约束],
	...
); 
```

> use在MySQL中的含义代表选择，use 数据库名称相当于选择指定的数据库。而且use比较特殊，其选择结束后，其尾部可以不加分号；但是强烈建议所有的SQL语句都要加分号，养成一个好习惯。

```powershell
mysql> create table aa(
	id tinyint,
    username varchar(20),
    password char(32)
) engine=innodb default charset=utf8;
```

> tinyint ：微整型，范围-128 ~ 127，无符号型，则表示0 ~ 255

> 表示字符串类型可以使用char与varchar，char代表固定长度的字段，varchar代表变化长度的字段。

创建一个article文章表，拥有4个字段（编号、标题、作者、内容）

```powershell
mysql> use datab;
mysql> create table article(
	id int,
	title varchar(50),
	author varchar(20),
	content text
) engine=innodb default charset=utf8;
```

> text ：文本类型，一般情况下，用varchar存储不了的字符串信息，都建议使用text文本进行处理。

> varchar存储的最大长度，理论值65535个字符。但是实际上，有几个字符是用于存放内容的长度的，所以真正可以使用的不足65535个字符，另外varchar类型存储的字符长度还和编码格式有关。1个GBK格式的占用2个字节长度，1个UTF8格式的字符占用3个字节长度。GBK = 65532~65533/2，UTF8 = 65532~65533/3



####  查询已创建数据表

显示所有数据表（当前数据库）

```powershell
mysql> use 数据库名称;
mysql> show tables;
```

显示数据表的（编码格式、字段等信息）

```powershell
mysql> desc 数据表名称;
```

####  修改数据表信息

##### ① 数据表字段添加

```powershell
mysql> alter table 数据表名称 add 新字段名称 字段类型 first|after 其他字段名称;
选项说明：
first：把新添加字段放在第一位
after 字段名称：把新添加字段放在指定字段的后面
```

案例：在tb_article文章表中添加一个addtime字段，类型为date(年-月-日)

```powershell
mysql> alter table tb_article add addtime date after content;
mysql> desc tb_article;
```

##### ② 修改字段名称或字段类型

修改字段名称与字段类型（也可以只修改名称）

```powershell
mysql> alter table tb_admin change username user varchar(40);
mysql> desc tb_admin;
```

仅修改字段的类型

```powershell
mysql> alter table tb_admin modify user varchar(20
mysql> desc tb_admin;
```

##### ③ 删除某个字段

```powershell
mysql> alter table tb_article drop 字段名称;
mysql> desc tb_article;
```

##### ④ 修改数据表名称

```powershell
rename table 旧名称 to 新名称;
```

####  删除数据表

```powershell
mysql> drop table IF EXISTS 数据表名称;
```

### 2、字段类型详解

① 整数类型

| **分类**     | **类型名称**   | **说明**                 |
| ------------ | -------------- | ------------------------ |
| tinyint      | 很小的整数     | -128 ~ 127               |
| smallint     | 小的整数       | -32768 ~ 32767           |
| mediumint    | 中等大小的整数 | -8388608 ~ 8388607       |
| int(integer) | 普通大小的整数 | -2147483648 ~ 2147483647 |

② 浮点类型

浮点类型（精度失真情况）和定点类型（推荐使用定点类型）

| 分类         | 类型名称              |
| ------------ | --------------------- |
| float        | 单精度浮点数          |
| double       | 双精度浮点数          |
| decimal(m,d) | 定点数，decimal(10,2) |

> decimal(10,2) ：代表这个数的总长度为10 = 整数长度 + 小数长度，2代表保留2位小数

③ 日期类型

| 分类      | 类型名称                                                     |
| --------- | ------------------------------------------------------------ |
| year      | YYYY 1901~2155                                               |
| time      | HH:MM:SS -838:59:59~838:59:59                                |
| date      | YYYY-MM-DD  1000-01-01~9999-12-3                             |
| datetime  | YYYY-MM-DD  HH:MM:SS 1000-01-01 00:00:00~ 9999-12-31 23:59:59 |
| timestamp | YYYY-MM-DD  HH:MM:SS 1970~01~01 00:00:01  UTC~2038-01-19 03:14:07UTC |

④ 文本

| **类型名称** | **说明**                             |
| ------------ | ------------------------------------ |
| char(m)      | m为0~255之间的整数定长（固定长度）   |
| varchar(m)   | m为0~65535之间的整数变长（变化长度） |
| text         | 允许长度0~65535字节                  |
| mediumtext   | 允许长度0~167772150字节              |
| longtext     | 允许长度0~4294967295字节             |

## 七、DML数据操作语言

### 1、DML的SQL语句

insert插入、update更新、delete删除

### 2、数据的增删改

#### 数据的增加操作

```powershell
mysql> insert into 数据表名称([字段1,字段2,字段3...]) values (字段1的值,字段2的值,字段3的值...);
```

> 特别注意：在SQL语句中，除了数字，其他类型的值，都需要使用引号引起来，否则插入时会报错。

第一步：准备一个数据表

```powershell
mysql> use aa;
mysql> create table tb_user(
	id int,
	username varchar(20),
	age tinyint unsigned,
	gender enum('男','女','保密'),
	address varchar(255)
) engine=innodb default charset=utf8;
```

> unsigned代表无符号型，只有0到正数。tinyint unsigned无符号型，范围0 ~ 255

> enum枚举类型，多选一。只能从给定的值中选择一个

第二步：使用insert语句插入数据

```powershell
mysql> insert into tb_user values (1,'刘备',34,'男','广州市天河区');
mysql> insert into tb_user(id,username,age) values (2,'关羽',33);
```

第三步：批量插入多条数据

```powershell
mysql> insert into tb_user values (3,'大乔',19,'女','上海市浦东新区'),(4,'小乔',18,'女','上海市浦东新区'),(5,'马超',26,'男','北京市昌平区');

INSERT INTO aaa(name)VALUES ('heheh');                               #单独插入一个数据
INSERT INTO aaa(name,gender,age)VALUES ('hehe','male',18);           #插入多个列出数据
INSERT INTO aaa VALUES ('hehe1','male',18);                          #插入一条完整数据
INSERT INTO aaa VALUES ('hehe2','male',18),('hehehe','female',18);   #插入多条完整数据
INSERT INTO aaa(name,gender)VALUES ('hehe3','male'),('hehe4','male');#插入多条列出数据
```

#### 数据的修改操作

```powershell
mysql> update 数据表名称 set 字段1=更新后的值,字段2=更新后的值,... where 更新条件;
```

> 特别说明：如果在更新数据时，不指定更新条件，则其会把这个数据表的所有记录全部更新一遍。

案例：修改username='马鹏'这条记录，将其性别更新为男，家庭住址更新为广东省深圳市

```powershell
mysql> update tb_user set gender='男',address='广东省深圳市' where username='马鹏';
```

案例：今年是2020年，假设到了2021年，现在存储的学生年龄都差1岁，整体进行一次更新

```powershell
mysql> update tb_user set age=age+1;
```

#### 数据的删除操作

```powershell
mysql> delete from 数据表名称 [where 删除条件];
```

删除tb_user表中，id=1的用户信息

```powershell
mysql> delete from tb_user where id=1;
```



delete from与truncate清空数据表操作

```powershell
mysql> delete from 数据表;
或
mysql> truncate 数据表;
```



delete from与truncate区别

- delete：删除数据记录
  - 数据操作语言（DML）
  - 删除大量记录速度慢，只删除数据，主键自增序列不清零，100 => 新插入 => 101
  - 可以带条件删除
- truncate：删除所有数据记录
  - 数据定义语言（DDL）
  - 清里大量数据速度快，主键自增序列清零, 100 => 新插入 => 1
  - 不能带条件删除

## 八、SQL约束

### 1、主键约束

1、PRIMARY KEY 约束唯一标识数据库表中的每条记录。
        2、主键必须包含唯一的值。
        3、主键列不能包含 NULL 值。
        4、每个表都应该有一个主键，并且每个表只能有一个主键。

遵循原则：

1）主键应当是对用户没有意义的
        2）永远也不要更新主键。
        3）主键不应包含动态变化的数据，如时间戳、创建时间列、修改时间列等。
        4） 主键应当由计算机自动生成。

创建主键约束：创建表时，在字段描述处，声明指定字段为主键

![mysql图6.png](https://s2.loli.net/2024/03/15/TiFnpNmeAYq8dPQ.png)

如：创建一个学生信息表tb_students，包含编号id、学生姓名name、年龄age、性别gender以及家庭住址address等字段，然后将id设置为主键。

```sql
create table tb_students(
	id int primary key,
    name varchar(20),
    age tinyint unsigned,
    gender enum('男', '女'),
    address varchar(255)
) engine=innodb default charset=utf8;
```

删除主键约束：如需撤销 PRIMARY KEY 约束，请使用下面的 SQL

```powershell
alter table persons2 drop primary key;
```

删除tb_students数据表的主键

```sql
alter table tb_students drop primary key;
```



> 自动增长

我们通常希望在每次插入新记录时，数据库自动生成字段的值。

我们可以在表中使用 auto_increment（自动增长列）关键字，自动增长列类型必须是整型，自动增长列必须为键(一般是主键)。

**下列 SQL 语句把 "Persons" 表中的 "Id" 列定义为** **auto_increment** **主键**

```powershell
create table persons3(
	id int primary key auto_increment,
	first_name varchar(255),
	last_name varchar(255),
	address varchar(255),
	city varchar(255)
) default charset=utf8;
```

向persons添加数据时，可以不为Id字段设置值，也可以设置成null，数据库将自动维护主键值：

```powershell
insert into persons3(first_name,last_name) values('Bill','Gates');
insert into persons3(id,first_name,last_name) values(null,'Bill','Gates');
```



如：创建一个学生信息表tb_students，包含编号id、学生姓名name、年龄age、性别gender以及家庭住址address等字段，然后将id设置为主键自动增长列。

```sql
drop table tb_students;

create table tb_students(
	id int auto_increment primary key,
    name varchar(20),
    age tinyint unsigned,
    gender enum('男', '女'),
    address varchar(255)
) engine=innodb default charset=utf8;
或
create table tb_students(
	id int auto_increment,
    name varchar(20),
    age tinyint unsigned,
    gender enum('男', '女'),
    address varchar(255),
    primary key(id)
) engine=innodb default charset=utf8;

-- 插入测试数据
insert into tb_students values (null, '吕布', 30, '男', '内蒙古包头市');
insert into tb_students values (null, '貂蝉', 19, '女', '山西忻州市');

-- 删除auto_increment
alter table 表名 change 列名 列名 类型; 

ALTER TABLE 表名 CHANGE 列名 列名 类型;
ALTER TABLE 表名 DROP PRIMARY KEY ;#删除主键自增的值需要先更改主键类型
```

### 2、非空约束

NOT NULL 约束强制列不接受 NULL 值。
NOT NULL 约束强制字段始终包含值。这意味着，如果不向字段添加值，就无法插入新记录或者更新记录。
下面的 SQL 语句强制 "id" 列和 "last_name" 列不接受 NULL 值：

![mysql图7.png](https://s2.loli.net/2024/03/15/LH4D1AqFgcWaktz.png)

创建一个tb_news新闻表，包含id主键列、title新闻标题、description描述、content新闻内容以及addtime添加时间，要求为title字段添加非空约束。

```sql
create table tb_news(
	id int auto_increment,
    title varchar(80) not null,
    description varchar(255),
    content text,
    addtime datetime,
    primary key(id)
) engine=innodb default charset=utf8;
```

### 3、唯一约束

UNIQUE 约束唯一标识数据库表中的每条记录。
UNIQUE 和 PRIMARY KEY 约束均为列或列集合提供了唯一性的保证。
PRIMARY KEY 拥有自动定义的 UNIQUE 约束。

请注意：
每个表可以有多个 UNIQUE 约束，但是每个表只能有一个 PRIMARY KEY 约束。

![mysql图8.png](https://s2.loli.net/2024/03/15/xoFvkLelYCJquzr.png)

创建一个tb_member会员表 ，包含字段有id主键、username用户名、password密码（密码必须使用密文保存，长度为固定的32位），由于用户名不允许出现重复的情况，所以请为username添加唯一约束。

```sql
create table tb_member(
	id int auto_increment,
    username varchar(20) unique,
    password char(32),
    primary key(id)
) engine=innodb default charset=utf8;
```

### 4、默认值约束

关键字：default

用来指定某列的默认值。在表中插入一条新记录时，如果没有为这个字段赋值，系统就会自动为这个字段插入默认值。

创建一个tb_department部门表，包含字段id主键、name部门名称以及location部门位置。由于我们的部门位置位于北京的较多，所以部门位置就可以默认为“Beijing”。

```sql
create table tb_department(
	id int auto_increment,
    name varchar(20),
    location varchar(50) default 'Beijing',
    primary key(id)
) engine=innodb default charset=utf8;
```

### 5、外键约束

外键约束：关键字foreign key（主要用于多表关联使用）

用于保持不同表之间的数据一致性和完整性。它是一种规定，用于确保在一个表中的外键（Foreign Key）值必须存在于另一个表中的主键（Primary Key）中。

外键约束的主要目的是建立表之间的关联关系，以确保表之间的数据一致性。外键约束可以在数据库设计时定义，并且可以由数据库管理系统（DBMS）自动执行，以防止不符合约束条件的数据插入或更新操作。

比如：有两张数据表，这两个数据表之间有联系，通过了某个字段可以建立连接，这个字段在其中一个表中是主键，在另外一张表中，我们就把其称之为==外键==。

![mysql图9.png](https://s2.loli.net/2024/03/15/tLpQDuqBj8JPAU4.png)

外键约束可以有以下特性：

1. 引用完整性：外键约束可以确保表之间的关联关系是有效的，即在外键列中的值必须在主键列中存在。这可以防止插入或更新数据时出现无效的外键值，从而保持数据的完整性。
2. 数据一致性：外键约束可以确保在关联表之间的数据一致性，因为它要求外键值与主键值相匹配。这可以防止在不同表中出现不一致的数据，从而保持数据的一致性。
3. 数据操作控制：外键约束可以限制对外键列的插入、更新和删除操作，从而控制对关联表的数据操作。这可以帮助防止不正确的数据操作，从而提高数据的质量和准确性。

外键约束可能会对数据库的性能和灵活性产生影响，因为它会增加对数据的检查和验证操作。在设计数据库时，需要仔细考虑外键约束的使用，并根据具体情况进行权衡。

### 6、小结

① 主键约束：唯一标示，不能重复，不能为空。
1）主键应当是对用户没有意义的
2）永远也不要更新主键。
3）主键不应包含动态变化的数据，如时间戳、创建时间列、修改时间列等。
4） 主键应当由计算机自动生成。

自动增长：
我们可以在表中使用 auto_increment（自动增长列）关键字，自动增长列类型必须是整型，自动增长列必须为键(一般是主键)。

② 非空约束：
NOT NULL 约束强制列不接受 NULL 值。

③ 唯一约束：
UNIQUE 约束唯一标识数据库表中的每条记录。
UNIQUE 和 PRIMARY KEY 约束均为列或列集合提供了唯一性的保证。
PRIMARY KEY 拥有自动定义的 UNIQUE 约束。

④ 默认值约束

default 默认值

用来指定某列的默认值。在表中插入一条新记录时，如果没有为这个字段赋值，系统就会自动为这个字段插入默认值。

⑤ 外键约束

主要用于指定两张表之间的关联关系。

## 九、DQL数据查询语言

### 1、数据集准备

```mysql
CREATE TABLE product
(
    pid         INT PRIMARY KEY,
    pname       VARCHAR(20),
    price       DOUBLE,
    category_id VARCHAR(32)
);
```

插入数据：

```mysql
INSERT INTO product VALUES (1,'联想',5000,'c001');
INSERT INTO product VALUES (2,'海尔',3000,'c001');
INSERT INTO product VALUES (3,'雷神',5000,'c001');
INSERT INTO product VALUES (4,'杰克琼斯',800,'c002');
INSERT INTO product VALUES (5,'真维斯',200,'c002');
INSERT INTO product VALUES (6,'花花公子',440,'c002');
INSERT INTO product VALUES (7,'劲霸',2000,'c002');
INSERT INTO product VALUES (8,'香奈儿',800,'c003');
INSERT INTO product VALUES (9,'相宜本草',200,'c003');
INSERT INTO product VALUES (10,'面霸',5,'c003');
INSERT INTO product VALUES (11,'好想你枣',56,'c004');
INSERT INTO product VALUES (12,'香飘飘奶茶',1,'c005');
INSERT INTO product VALUES (13,'海澜之家',1,'c002');
```

### 2、select查询

基础查询：

```powershell
# 根据某些条件从某个表中查询指定字段的内容
格式：select [distinct]*| 列名,列名 from 表 where 条件
```

高级查询：SQL查询五子句

```sql
select */列名,列名 from 数据表 where 子句 group by 子句 having 子句 order by 子句 limit 子句;

① where子句
② group by子句
③ having子句
④ order by子句
⑤ limit子句
```

### 3、简单查询

```mysql
# 1.查询所有的商品.  
select *  from product;
# 2.查询商品名和商品价格. 
select pname,price from product;
# 3.查询结果是表达式（运算查询）：将所有商品的价格+10元进行显示.
select pname,price+10 from product;
```

### 4、条件查询

![mysql图10.png](https://s2.loli.net/2024/03/15/sWaSuJbvqHVidmw.png)

####  比较查询

```powershell
# 查询商品名称为“花花公子”的商品所有信息：
SELECT * FROM product WHERE pname = '花花公子';
# 查询价格为800商品
SELECT * FROM product WHERE price = 800;
# 查询价格不是800的所有商品
SELECT * FROM product WHERE price != 800;
SELECT * FROM product WHERE price <> 800;
# 查询商品价格大于60元的所有商品信息
SELECT * FROM product WHERE price > 60;
# 查询商品价格小于等于800元的所有商品信息
SELECT * FROM product WHERE price <= 800;
```

####  范围查询

```powershell
# 查询商品价格在200到1000之间所有商品
SELECT * FROM product WHERE price BETWEEN 200 AND 1000;
# 查询商品价格是200或800的所有商品
SELECT * FROM product WHERE price IN (200,800);
```

####  逻辑查询

```powershell
# 查询商品价格在200到1000之间所有商品
SELECT * FROM product WHERE price >= 200 AND price <=1000;
# 查询商品价格是200或800的所有商品
SELECT * FROM product WHERE price = 200 OR price = 800;
# 查询价格不是800的所有商品
SELECT * FROM product WHERE NOT(price = 800);
```

####  模糊查询

```powershell
# 查询以'香'开头的所有商品
SELECT * FROM product WHERE pname LIKE '香%';
# 查询第二个字为'想'的所有商品
SELECT * FROM product WHERE pname LIKE '_想%';
```

####  非空查询

```powershell
# 查询没有分类的商品
SELECT * FROM product WHERE category_id IS NULL;
# 查询有分类的商品
SELECT * FROM product WHERE category_id IS NOT NULL;
```

### 5、排序查询

```powershell
# 通过order by语句，可以将查询出的结果进行排序。暂时放置在select语句的最后。
格式：SELECT * FROM 表名 ORDER BY 排序字段 ASC|DESC;
ASC 升序 (默认)
DESC 降序

# 1.使用价格排序(降序)
SELECT * FROM product ORDER BY price DESC;
# 2.在价格排序(降序)的基础上，以分类排序(降序)
SELECT * FROM product ORDER BY price DESC,category_id DESC;
```

### 6、聚合查询

之前我们做的查询都是横向查询，它们都是根据条件一行一行的进行判断，而使用聚合函数查询是纵向查询，它是对一列的值进行计算，然后返回一个单一的值；另外聚合函数会忽略空值。

今天我们学习如下五个聚合函数：

| **聚合函数** | **作用**                                                     |
| ------------ | ------------------------------------------------------------ |
| count()      | 统计指定列不为NULL的记录行数；                               |
| sum()        | 计算指定列的数值和，如果指定列类型不是数值类型，则计算结果为0 |
| max()        | 计算指定列的最大值，如果指定列是字符串类型，使用字符串排序运算； |
| min()        | 计算指定列的最小值，如果指定列是字符串类型，使用字符串排序运算； |
| avg()        | 计算指定列的平均值，如果指定列类型不是数值类型，则计算结果为0 |

演示：

```powershell
# 1、查询商品的总条数
SELECT COUNT(*) FROM product;
# 2、查询价格大于200商品的总条数
SELECT COUNT(*) FROM product WHERE price > 200;
# 3、查询分类为'c001'的所有商品的总和
SELECT SUM(price) FROM product WHERE category_id = 'c001';
# 4、查询分类为'c002'所有商品的平均价格
SELECT AVG(price) FROM product WHERE categ ory_id = 'c002';
# 5、查询商品的最大价格和最小价格
SELECT MAX(price),MIN(price) FROM product;
```

### 7、分组查询与having子句

####  分组查询介绍

分组查询就是将查询结果按照指定字段进行分组，字段中数据相等的分为一组。

**分组查询基本的语法格式如下：**

GROUP BY 列名 [HAVING 条件表达式] [WITH ROLLUP]

**说明:**

- 列名: 是指按照指定字段的值进行分组。
- HAVING 条件表达式: 用来过滤分组后的数据。
- WITH ROLLUP：在所有记录的最后加上一条记录，显示select查询时聚合函数的统计和计算结果

####  group by的使用

创建数据集

```sql
create table students(
	id int auto_increment,
	name varchar(20),
	age tinyint unsigned,
	gender enum('male', 'female'),
	height float(5,2),
	primary key(id)
) engine=innodb default charset=utf8;

insert into students values (null,'郭靖',33,'male',1.80);
insert into students values (null,'黄蓉',19,'female',1.65);
insert into students values (null,'柯镇恶',45,'male',1.61);
insert into students values (null,'黄药师',50,'male',1.72);
insert into students values (null,'华筝',18,'female',1.60);
```



group by可用于单个字段分组，也可用于多个字段分组

```sql
-- 根据gender字段来分组
select gender from students group by gender;
-- 根据name和gender字段进行分组
select name, gender from students group by name, gender;
```

① group by可以实现去重操作

② group by的作用是为了实现分组统计（group by + 聚合函数）

####  group by + 聚合函数的使用

```sql
-- 统计不同性别的人的平均年龄
select gender,avg(age) from students group by gender;
-- 统计不同性别的人的个数
select gender,count(*) from students group by gender;
```

执行原理图

![mysql图11.png](https://s2.loli.net/2024/03/15/H4dDUatMegwfKYn.png)

####  group by + having的使用

having作用和where类似都是过滤数据的，但having是过滤分组数据的，只能用于group by

```sql
-- 根据gender字段进行分组，统计分组条数大于2的
select gender,count(*) from students group by gender having count(*)>2;
```



```powershell
#1 统计各个分类商品的个数
SELECT category_id ,COUNT(*) FROM product GROUP BY category_id ;

#2 统计各个分类商品的个数,且只显示个数大于1的信息
SELECT category_id ,COUNT(*) FROM product GROUP BY category_id HAVING COUNT(*) > 1;
```

### 8、limit分页查询

作用：限制数据的查询数量

基本语法：

```sql
select * from 数据表 limit 查询数量;
```

案例：查询学生表中，身高最高的3名同学信息

```sql
select * from students order by height desc limit 3;
```



limit除了可以限制查询数量以外，其还可以指定从哪条数据开始查起，limit完整语法：

```sql
select * from students limit offset,count;

offset：索引，默认从0开始
count：查询总数量
```

如：查询学生表中，身高第2、3高的同学信息

```sql
select * from students order by height desc limit 1,2;
```



limit子句典型应用场景：

分页查询在项目开发中常见，由于数据量很大，显示屏长度有限，因此对数据需要采取分页显示方式。例如数据共有30条，每页显示5条，第一页显示1-5条，第二页显示6-10条。

 格式：

```powershell
SELECT 字段1，字段2... FROM 表名 LIMIT M,N
M: 整数，表示从第几条索引开始，计算方式 （当前页-1）* 每页显示条数
N: 整数，表示查询多少条数据
SELECT 字段1，字段2... FROM 表名 LIMIT 0,5
SELECT 字段1，字段2... FROM 表名 LIMIT 5,5
```

### 9、小结

```powershell
SQL查询五子句：
select * from 表名 where子句 group by子句 having子句 order by子句 limit子句;
特别注意：查询五子句中，五子句的顺序一定要严格按照以上格式。

条件查询：SELECT *|字段名 FROM 表名 WHERE 条件；
排序查询：SELECT * FROM 表名 ORDER BY 排序字段 ASC|DESC;
聚合查询函数：count()，sum()，max()，min()，avg()。
分组查询：SELECT 字段1,字段2… FROM 表名 GROUP BY 分组字段 HAVING 分组条件;
分页查询：
SELECT 字段1，字段2... FROM 表名 LIMIT M,N
M: 整数，表示从第几条索引开始，计算方式 （当前页-1）*每页显示条数
N: 整数，表示查询多少条数据
```

## 十、多表查询

### 数据集准备

classes班级表

```sql
create table classes(
	cls_id tinyint auto_increment,
    cls_name varchar(20),
    primary key(cls_id)
) engine=innodb default charset=utf8;

-- 插入测试数据
insert into classes values (null, 'ui');
insert into classes values (null, 'java');
insert into classes values (null, 'python');
```

students学生表

```sql
create table students(
	id int auto_increment,
    name varchar(20),
    age tinyint unsigned,
    gender enum('male','female'),
    score float(5,1),
	cls_id tinyint,
    primary key(id)
) engine=innodb default charset=utf8;

-- 插入测试数据
insert into students values (null,'刘备',34,'male',90.0,2);
insert into students values (null,'貂蝉',18,'female',75.0,1);
insert into students values (null,'赵云',28,'male',95.0,3);
insert into students values (null,'关羽',32,'male',98.0,3);
insert into students values (null,'大乔',19,'female',80.0,1);
```



### 交叉连接

是所有连接的基础。其功能就是将表1和表2中的每一条数据进行连接。

结果：

字段数 = 表1字段 + 表2的字段

记录数 = 表1中的总数量 * 表2中的总数量（笛卡尔积）

```powershell
select * from students cross join classes;
或
select * from students, classes;
```



### 1、内连接

####  连接查询的介绍

连接查询可以实现多个表的查询，当查询的字段数据来自不同的表就可以使用连接查询来完成。

连接查询可以分为:

1. 内连接查询
2. 左外连接查询
3. 右外连接查询

####  内连接查询

查询两个表中符合条件的共有记录

![mysql图12](/upload/2023/04/mysql图12.png)

**内连接查询语法格式:**

```sql
select 字段 from 表1 inner join 表2 on 表1.字段1 = 表2.字段2
```

**说明:**

- inner join 就是内连接查询关键字
- on 就是连接查询条件

**例1：使用内连接查询学生表与班级表:**

```sql
select * from students as s inner join classes as c on s.cls_id = c.id;
```

####  小结

- 内连接使用inner join .. on .., on 表示两个表的连接查询条件
- 内连接根据连接查询条件取出两个表的 “交集”

### 2、左外连接

#### 左连接查询

以左表为主根据条件查询右表数据，如果根据条件查询右表数据不存在使用null值填充

![mysql图12.png](https://s2.loli.net/2024/03/15/xDXCSlnTcuWrsL4.png)

**左连接查询语法格式:**

```sql
select 字段 from 表1 left join 表2 on 表1.字段1 = 表2.字段2
```

**说明:**

- left join 就是左连接查询关键字
- on 就是连接查询条件
- 表1 是左表
- 表2 是右表

**例1：使用左连接查询学生表与班级表:**

```sql
select * from students as s left join classes as c on s.cls_id = c.id;
```

**例2：查询学生表中每一位学生（包括没有对应班级的学生）所属的班级信息**

前提：

在students学生表中，插入一条测试数据

```sql
insert into students values (null,'林黛玉',19,'female',96.0,99);
```

执行左外连接查询：

```sql
select * from students as s left join classes as c on s.cls_id = c.id;
```

####  小结

- 左连接使用left join .. on .., on 表示两个表的连接查询条件
- 左连接以左表为主根据条件查询右表数据，右表数据不存在使用null值填充。

### 3、右外连接

####  右连接查询

以右表为主根据条件查询左表数据，如果根据条件查询左表数据不存在使用null值填充

![mysql图13.png](https://s2.loli.net/2024/03/15/tFMayxRQZh9pYLW.png)

**右连接查询语法格式:**

```sql
select 字段 from 表1 right join 表2 on 表1.字段1 = 表2.字段2
```

**说明:**

- right join 就是右连接查询关键字
- on 就是连接查询条件
- 表1 是左表
- 表2 是右表

**例1：使用右连接查询学生表与班级表:**

```sql
select * from students as s right join classes as c on s.cls_id = c.id;
```

####  小结

- 右连接使用right join .. on .., on 表示两个表的连接查询条件
- 右连接以右表为主根据条件查询左表数据，左表数据不存在使用null值填充。

## 十一、子查询

### 1、子查询（嵌套查询）的介绍

在一个 select 语句中,嵌入了另外一个 select 语句, 那么被嵌入的 select 语句称之为子查询语句，外部那个select语句则称为主查询.

**主查询和子查询的关系:**

1. 子查询是嵌入到主查询中
2. 子查询是辅助主查询的,要么充当条件,要么充当数据源(数据表)
3. 子查询是可以独立存在的语句,是一条完整的 select 语句

### 2、子查询的使用

**例1. 查询学生表中大于平均年龄的所有学生:**

需求：查询年龄 > 平均年龄的所有学生

前提：① 获取所有学生的平均年龄

​	   ② 查询表中的所有记录，判断哪个同学 > 平均年龄值

第一步：写子查询

```powershell
select avg(age) from students;
```

第二步：写主查询

```powershell
select * from students where age > (平均值);
```

第三步：第一步和第二步进行合并

```powershell
select * from students where age > (select avg(age) from students);
```



**例2. 查询学生在班的所有班级名字:**

需求：显示所有有学生的班级名称

前提：① 先获取所有学员都属于那些班级

​	         ② 查询班级表中的所有记录，判断是否出现在①结果中，如果在，则显示，不在，则忽略。

第一步：编写子查询

```powershell
select distinct cls_id from students is not null;
```

第二步：编写主查询

```powershell
select * from classes where cls_id in (1, 2, 3);
```

第三步：把主查询和子查询合并

```sql
select * from classes where cls_id in (select distinct cls_id from students where cls_id is not null);
```



**例3. 查找年龄最小,成绩最低的学生:**

第一步：获取年龄最小值和成绩最小值

```powershell
select min(age), min(score) from student;
```

第二步：查询所有学员信息（主查询）

```sql
select * from students where (age, score) = (最小年龄, 最少成绩);
```

第三步：把第一步和第二步合并

```powershell
select * from students where (age, score) = (select min(age), min(score) from students);
```

![SQL基础内容](/upload/2023/04/SQL基础内容.png)

## 十二、练习部分

练习使用 微软的Northwind数据集, 零售业务，包含了客户，供应商和订单数据。原始数据集可以在 [微软GitHub 仓库](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)下载。当前使用数据库数据在原始数据基础上做了微调，放在了文末。

基于此份数据，通过SQL来创建数据报表，满足业务需求。

本项目中一共用到7张表

1. `employees` 员工表 记录了Northwind所有员工信息.
2. `customers` 客户表，记录了客户相关信息.
3. `products` 记录了商品信息.
4. `categories` 记录了商品类别信息.
5. `suppliers` 记录了商品供应商信息.
6. `orders` 记录了Northwind的顾客下的订单.
7. `order_items` 记录了订单中的每一件商品明细.

**数据表结构及表关系**

![mysql图14.png](https://s2.loli.net/2024/03/15/dk5Le8RXhZT1FaW.png)

![mysql图15.png](https://s2.loli.net/2024/03/15/UbNQkfIhJSlVE53.png)

### 1.1 员工表(employees)

![mysql图16.png](https://s2.loli.net/2024/03/15/WN8c5ydk9uDBVwl.png)

- 保存员工基本信息：
  - 唯一ID (`employee_id`).
  - 姓，名(`first_name` and `last_name`).
  - 职务 (`title`).
- 需要注意的是 `reports_to`这一列, 保存的是员工所对应的直属领导的员工ID (也在这张表中保存) ，此外还有其它列包括入职时间，生日... ...

#### 练习1

- 选中`employees` 表的所有数据

```sql
select * from employees
```

![mysql图17.png](https://s2.loli.net/2024/03/15/6rq1TGNiyuvngja.png)

### 1.2 顾客表(customers)

- 每一个顾客都有唯一ID`customer_id`, 顾客的ID是公司全名的缩写，用5个字母表示

- 公司全名在 `company_name` 列中保存

- `contact_name` 和 `contact_title` 两列代表了客户公司的联系人信息（名字和职务）

  除此之外还保存了顾客的地址信息和联系方式`city`, `region`, `postal_code`, `country`, `fax`

#### 练习2

- 查询每个客户的 `ID`, `company name`, `contact name`, `contact title`, `city`, 和 `country`.并按照国家名字排序

```sql
select customer_id,
  company_name,
  contact_name,
  contact_title,
  city,
  country from customers
  order by country
```

![mysql图18.png](https://s2.loli.net/2024/03/15/FzSiLJ3yK4DAhGV.png)

### 1.3 商品(products)和商品类别(categories)表

- 商品表中保存了在Northwind商店中出售的商品信息
  - 每一种商品都有唯一的 `product_id` 和商品名字`product_name`.
  - 每一种商品都有一个供应商 (`supplier_id`) 
  - 每一种商品都有一个商品类别 (`category_id`).
  - 每一种商品都有确定的单价 `unit_price`. 
  - 字段 `discontinued` 代表商品是否缺货， `false` (有货)   `true` (缺货) 
- 商品类别表 `categories` ，保存了所有商品的类别
  - 每个类别都有唯一的id
  - 每个类别都有自己的名称 `category_name`
  - 字段`description` 存储了类别的简短描述信息
- 商品表中包含了  `category_id` 字段，所以可以使用join 将商品表中的信息与商品类别表中的信息进行关联查询

#### 练习3

- 查询每一个商品的`product_name`，`category_name`，`quantity_per_unit`，`unit_price`，`units_in_stock` 并且通过 `unit_price` 字段排序

```sql
SELECT
  product_name,
  category_name,
  quantity_per_unit,
  unit_price,
  units_in_stock
FROM products
JOIN categories
  ON products.category_id = categories.category_id
ORDER BY unit_price;
```

![mysql图19.png](https://s2.loli.net/2024/03/15/vl9HDzPXf4yh5AQ.png)

### 1.4 供应商表（supplier）

- 供应商表与用户表类似
- 每个供应商都有唯一ID `supplier_id` 
- 每个供应商都有公司名字`company_name`
- 表中还记录了供应商的地址信息 `address`，`city`，`region`，`postal_code`，`country`

#### 练习4

- 列出所有提供了4种以上不同商品的供应商列表
- 所需字段：`supplier_id`, `company_name`, and `products_count` (提供的商品种类数量).

```sql
SELECT
  s.supplier_id, 
  s.company_name, 
  COUNT(*) AS products_count
FROM products p
JOIN suppliers s 
  ON p.supplier_id = s.supplier_id
GROUP BY s.supplier_id,
  s.company_name
HAVING COUNT(*) > 4;
```

![mysql图20.png](https://s2.loli.net/2024/03/15/NSHhZDv5rALW9O2.png)

### 1.5 订单和订单明细表

- 订单表 `orders` 中的每一条数据包含了一个订单的基本信息：
  - 订单ID `order_id`，顾客ID `customer_id`, 销售员的员工ID `employee_id` 
  - 订单相关的时间信息  (下单日期`order_date` 和配送日期 `shipped_date`) 和其他配送相关信息
    - ship_via 运输方式
    - freight   运费
    - ship_address  收货地址
    - ship_city   收货城市
    - ship_region 收货地区
    - ship_postal_code 收货地址邮编
    - ship_country 收货国家

#### 练习5

- 提取订单编号为10250的订单详情，显示如下信息：

  `product_name`, `quantity`, `unit_price` （ `order_items` 表)`discount` ，`order_date` ,按商品名字排序

```sql
SELECT
  product_name,
  quantity,
  order_items.unit_price,
  discount,
  order_date
FROM order_items
JOIN products
  ON order_items.product_id = products.product_id
JOIN orders
  ON orders.order_id = order_items.order_id
WHERE orders.order_id = 10250
ORDER BY product_name;
```

### 2.1 详细报告

- 将一个或者多个业务对象的详细信息汇总到一张表中是一种比较常见的报表形式
- 我们需要的信息可能分散在多张表中，在写SQL时可以通过一个或者多个`JOIN`子句将信息进行汇总

```sql
SELECT
  c.company_name AS customer_company_name, 
  e.first_name AS employee_first_name, 
  e.last_name AS employee_last_name,
  o.order_date,
  o.shipped_date,
  o.ship_country
FROM orders o
JOIN employees e
  ON o.employee_id = e.employee_id
JOIN customers c
  ON o.customer_id = c.customer_id
WHERE o.ship_country = 'France';
```

- 在上面的SQL查询中，我们想收集运输到法国的订单的相关信息，包括订单涉及的顾客和员工信息，下单和发货日期等
- 由于相关数据保存在不同的表中，所以需要将`orders` 表， `employees` 表和 `customers` 表连接在一起
- 注意在写SQL时，我们可以为每一张表都起了一个别名，可以减少输入的字符数

#### 练习6

- 需求：提供订单编号为10248的相关信息，包括**product name**,  **unit price** (在 `order_items` 表中),  **quantity（数量）**,**company_name**（供应商公司名字 ，起别名 `supplier_name`).

```sql
SELECT
  product_name,
  oi.unit_price,
  oi.quantity,
  company_name AS supplier_name
FROM order_items oi
JOIN products p 
  ON oi.product_id = p.product_id
JOIN suppliers s
  ON s.supplier_id = p.supplier_id
WHERE oi.order_id = 10248;
```

#### 练习7

- 需求：提取每件商品的详细信息，包括  商品名称（`product_name`）, 供应商的公司名称  (`company_name`，在 `suppliers` 表中), 类别名称 `category_name`, 商品单价`unit_price`, 和每单位商品数量`quantity per unit`

```sql
SELECT 
  p.product_name,
  s.company_name,
  c.category_name,
  p.unit_price,
  p.quantity_per_unit
FROM products p
JOIN suppliers s
  ON p.supplier_id = s.supplier_id
JOIN categories c
  ON c.category_id = p.category_id;
```

### 2.2 带时间限制的报表

- 另一种常见的报表需求是查询某段时间内的业务指标

```sql
SELECT
  COUNT(*)
FROM orders
WHERE order_date >= '2016-07-01' AND  order_date < '2016-08-01';
```

- 在上面的查询中，我们统计了2016年7月的订单数量，
- 需要注意SQL中的日期总是放在单引号内，格式通常为“ YYYY-MM-DD”（年-月-日）

#### 练习8

- 统计2013年入职的员工数量，统计字段起别名 `number_of_employees`

```sql
SELECT
  COUNT(*) AS number_of_employees
FROM employees
WHERE hire_date >= '2013-01-01' AND hire_date < '2014-01-01';
```

### 2.3 计算多个对象

- 在业务报表中，我们通常希望同时计算多个业务对象的某些指标。

```sql
SELECT
    order_id,
    COUNT(*) AS order_items_count
FROM
    order_items
WHERE
    order_id BETWEEN 10200 AND 10300
GROUP BY
    order_id;
```

- 在上面的查询中，我们统计了指定范围内的`order_id`，计算每个订单中的商品数量
  - 通过连接`orders` 和`order_items`表，在同一行显示单个订单商品及其父订单的信息
  - 按照父顺序对所有行进行分组
  - 使用`COUNT（*）`统计每个订单的商品数量

#### 练习9

- 需求：统计每个供应商供应的商品总数量
  - 结果返回供应商ID`supplier_id` ，公司名字`company_name` ，商品种类数量（起别名`products_count` )
  - 使用 `products` 和 `suppliers` 表.

```sql
SELECT
  s.supplier_id,
  company_name,
  COUNT(*) AS products_count
FROM products p
JOIN suppliers s
  ON p.supplier_id = s.supplier_id 
GROUP BY s.supplier_id,company_name;
```

需求：统计每个供应商分别供应每类商品的数量

```sql
SELECT
    count(*) AS `products_count`,
    s.supplier_id,
    s.company_name,
    category_id
FROM
    products AS p
        INNER JOIN suppliers AS s ON p.supplier_id = s.supplier_id
GROUP BY
    s.supplier_id, s.company_name, category_id ;
```



### 2.4 总订单金额

- 在销售报表中,我们经常需要计算订单的总付款额。

```sql
SELECT
    sum(unit_price * quantity) AS total_price
FROM
    order_items
WHERE
    order_id = 10250;
```

- 我们要查找ID为10250的订单的总价（折扣前），`SUM(unit_price * quantity)`

#### 练习10

- Northwind商店某些产品会不定期做打折促销
- 每个商品的折扣都存储在 `order_items` 表的`discount` 列中
- 例如，“ 0.20”折扣意味着客户支付原始价格的“ 1-0.2 = 0.8”
- 在下面的代码中添加第二个名为`total_price_after_discount`的列，计算打折后的商品价格

```sql
SELECT
  SUM(unit_price * quantity) AS total_price
FROM orders o
JOIN order_items oi 
  ON o.order_id = oi.order_id
WHERE o.order_id = 10250;
```



```sql
SELECT
    SUM(unit_price * quantity) AS total_price,
    SUM(unit_price * quantity * (1 - discount)) AS total_price_after_discount
FROM
    order_items
WHERE
        order_id = 10250
```

### 2.5 计算多个订单的订单金额

- 上面的案例中我们计算了单个订单的订单总金额，接下来我们统计多个订单的总金额

```sql
SELECT
  o.order_id,
  c.company_name AS customer_company_name, 
  SUM(unit_price * quantity) AS total_price
FROM orders o
JOIN customers c
  ON o.customer_id = c.customer_id
JOIN order_items oi
  ON o.order_id = oi.order_id
WHERE o.ship_country = 'France'
GROUP BY o.order_id, c.company_name;
```

- 我们想计算运输到法国的所有订单的总订单金额
- 在结果中，我们想保留订单ID和订单公司名字，可以通过`GROUP BY` 实现
- 注意：通过`GROUP BY`  我们只需要对 `order_id` 进行分组就可以了，但MySQL 5.7之后要求，在使用`GROUP BY`分组时，SELECT 后的字段，如果没有在聚合函数中使用，就必须在GROUP BY 后出现

#### 练习11

- 统计每个员工处理的订单总数
- 结果包含员工ID`employee_id`，姓名`first_name` 和 `last_name`，处理的订单总数(别名 `orders_count`)

```sql
SELECT
  e.employee_id,
  e.first_name,
  e.last_name,
  COUNT(*) AS orders_count
FROM orders o
JOIN employees e
  ON e.employee_id = o.employee_id
GROUP BY e.employee_id,
  e.first_name,
  e.last_name;
```

### 2.6 不同类别商品的库存

- 统计每个类别中的库存产品值多少钱？ 
  - 显示三列：`category_id`, `category_name`, 和 `category_total_value`
  - 如何计算库存商品总价：`SUM(unit_price * units_in_stock)`。

```sql
SELECT
  c.category_id,
  c.category_name,
  SUM(unit_price * units_in_stock) AS category_total_value
FROM products p
JOIN categories c
  ON p.category_id = c.category_id
GROUP BY c.category_id,
  c.category_name;
```

### 2.7 Group by分组

- 接下来，我们来了解每个员工的业绩：计算每个员工的订单数量
- 看下面的SQL是否有问题

```sql
SELECT
  e.first_name,
  e.last_name,
  COUNT(*) AS orders_count
FROM orders o
JOIN employees e
  ON o.employee_id = e.employee_id
GROUP BY e.first_name,
  e.last_name;
```

- 上面的SQL貌似正确，但是没有考虑到员工重名的问题，所以需要做一个小调整：

```sql
SELECT
  e.employee_id,
  e.first_name,
  e.last_name,
  COUNT(*) AS orders_count
FROM orders o
JOIN employees e
  ON o.employee_id = e.employee_id
GROUP BY e.employee_id,
  e.first_name,
  e.last_name;
```

- 在`SELECT` 和 `GROUP BY` 中添加了 员工ID `employee_id`字段后,重名的问题就可以解决了
- 注意，在使用GROUP BY进行分组聚合统计时，需要考虑分组字段中的相同值的业务含义是否相同

#### 练习12

- 需求：计算每个客户的下订单数
- 结果包含：用户id、用户公司名称、订单数量（`customer_id`, `company_name`,  `orders_count` ）

```sql
SELECT
  c.customer_id,
  c.company_name,
  COUNT(*) AS orders_count
FROM orders o
JOIN customers c
  ON o.customer_id = c.customer_id
GROUP BY c.customer_id,
  c.company_name;
```

### 2.8 选择显示部分信息

- 再看一下上面的例子

```sql
SELECT
  e.employee_id,
  e.first_name,
  e.last_name,
  COUNT(*) AS orders_count
FROM orders o
JOIN employees e
  ON o.employee_id = e.employee_id
GROUP BY e.employee_id,
  e.first_name,
  e.last_name;
```

- 我们通过 `employee_id`进行分组, 但是`GROUP BY`中的字段，不一定在`SELECT`中出现，例如下面的SQL：

```sql
SELECT
  e.first_name,
  e.last_name,
  COUNT(*) AS orders_count
FROM orders o
JOIN employees e
  ON o.employee_id = e.employee_id
GROUP BY e.employee_id,
  e.first_name,
  e.last_name;
```

- 之前我们强调过，`SELECT` 中的字段，如果没在聚合函数中使用，就一定更要在`GROUP BY` 子句中出现
- 但是，`GROUPY BY`子句中的字段，可以不用都出现在`SELECT`中

#### 练习13

- 需求：统计2016年6月到2016年7月底用户的总下单金额并按金额从高到低排序
- 结果包含：顾客公司名称`company_name` 和总下单金额（折后实付金额）`total_paid`
- 提示：
  - 计算实际总付款金额： SUM(unit_price * quantity * (1 - discount)) 
  - 日期过滤 `WHERE order_date >= '2016-06-01' AND order_date < '2016-08-01'`

```sql
SELECT
  c.company_name, 
  SUM(unit_price * quantity * (1 - discount)) AS total_paid
FROM orders o
JOIN order_items oi
  ON o.order_id = oi.order_id
JOIN customers c
  ON o.customer_id = c.customer_id
WHERE order_date >= '2016-06-01' AND order_date < '2016-08-01'
GROUP BY c.customer_id,
  c.company_name
ORDER BY total_paid DESC;
```

### 2.9 COUNT()函数回顾

- 当创建业务报表的时候，需要注意 `COUNT(*)` 和 `COUNT(列名)` 之间的区别
- 假设我们要统计发货到不同国家/地区的订单数量以及已经发货的订单数量

```sql
SELECT
  ship_country,
  COUNT(*) AS all_orders,
  COUNT(shipped_date) AS shipped_orders
FROM orders
GROUP BY ship_country;
```

- `COUNT（*）`将计算ship_country中的所有订单
- `COUNT（shipped_date）`将仅计算shipped_date列值不为NULL的行
- 在我们的数据库中，` shipped_date` 列中的`NULL`表示尚未发货，COUNT（shipped_date）` 仅计算已经发货的订单。

#### 练习14

- 需求：统计客户总数和带有传真号码的客户数量
- 需要字段：`all_customers_count` 和 `customers_with_fax_count`

```sql
SELECT
  COUNT(*) AS all_customers_count, 
  COUNT(fax) AS customers_with_fax_count
FROM customers;
```

### 3.1 使用CASE WHEN自定义分组

- 需求：我们要在报表中显示每种产品的库存量，但我们不想简单地将“ units_in_stock”列放在报表中。报表中只需要一个总体级别，例如低，高：

```sql
SELECT
  product_id,
  product_name,
  units_in_stock,
  CASE
    WHEN units_in_stock > 100 THEN 'high'
    WHEN units_in_stock > 50 THEN 'moderate'
    WHEN units_in_stock > 0 THEN 'low'
    WHEN units_in_stock = 0 THEN 'none'
  END AS availability
FROM products;
```

- 上面的SQL查询结果中，我们创建了一个新列`availability`， 通过 `CASE WHEN` 语句来对这一列赋值
- `CASE WHEN` 语法回顾
- 上面的查询中，通过  `units_in_stock` 列的值来判断库存的可用性
  - 库存大于100 的可用性为高(high)
  - 50到100的可用性为中等(moderate)
  - 小于50的为低(low)
  - 零库存 为 (none)

#### 练习15

运行上面的SQL，比较`units_in_stock` 和 `availability`两列的结果

#### 练习16

- 需求： 创建一个报表，统计员工的经验水平
- 显示字段：`first_name`, `last_name`, `hire_date`, 和 `experience` 
- 经验字段（`experience` ）：
  - `'junior'`  2014年1月1日以后雇用的员工
  - `'middle'` 在2013年1月1日之后至2014年1月1日之前雇用的员工
  - `'senior'` 2013年1月1日或之前雇用的员工

```sql
SELECT
  first_name,
  last_name,
  hire_date,
  CASE
    WHEN hire_date > '2014-01-01' THEN 'junior'
    WHEN hire_date > '2013-01-01' THEN 'middle'
    WHEN hire_date <= '2013-01-01' THEN 'senior'
  END AS experience
FROM employees;
```

### 3.2 CASE WHEN中ELSE的使用

- 我们的商店要针对北美地区的用户做促销活动：任何运送到北美地区（美国，加拿大) 的包裹免运费。 
- 创建报表，查询订单编号为10720~10730 活动后的运费价格

```sql
SELECT 
  order_id,
  customer_id,
  ship_country,
  CASE
    WHEN ship_country = 'USA' OR ship_country = 'Canada' THEN 0.0
  END AS shipping_cost
FROM orders
WHERE order_id BETWEEN 10720 AND 10730;
```

- 上面的SQL中，只定义了美国和加拿大的运费，并没有处理其他目的地的运费信息

#### 练习17

- 运行上面的SQL 观察 `ship_country` 和 `shipping_cost` 列，除了美国和加拿大之外，其他行的 `shipping_cost`  的值为NULL

- 在上面的案例中，除了北美地区的以外的订单，运费统计为NULL, 如果将其他地区的运费设置为10美元，那么可以用如下方式处理：

  ```
  SELECT 
    order_id,
    customer_id,
    ship_country,
    CASE
      WHEN ship_country = 'USA' OR ship_country = 'Canada' THEN 0.0
      ELSE 10.0
    END AS shipping_cost
  FROM orders
  WHERE order_id BETWEEN 10720 AND 10730;
  ```

  - 我们在`CASE WHEN`结构中添加了`ELSE`
  - 如果不满足其他条件，则执行`ELSE`。 因此，所有其他国家/地区的 `shipping_cost`都将变为“ 10.0”，而不是`NULL`。

#### 练习18

- 需求：创建客户基本信息报表
- 包含字段：
  - 客户id `customer_id`
  - 公司名字 `company_name`
  - 所在国家 `country`
  - 使用语言`language`
- 使用语言`language` 的取值按如下规则
  - Germany, Switzerland, and Austria 语言为德语 `'German'` 
  - UK, Canada, the USA, and Ireland 语言为英语 `'English'` 
  - 其他所有国家 `'Other'` 

```sql
SELECT 
  customer_id,
  company_name,
  country,
  CASE
    WHEN country IN ('Germany', 'Switzerland', 'Austria') THEN 'German'
    WHEN country IN ('UK', 'Canada', 'USA', 'Ireland') THEN 'English'
    ELSE 'Other'
  END AS language
FROM customers;
```

#### 练习19

- 需求：创建报表将所有产品划分为素食和非素食两类
- 报表中包含如下字段：
  - 产品名字 `product_name`
  - 类别名称 `category_name`
  - 膳食类型 `diet_type`:
    - 非素食 `'Non-vegetarian'`  商品类别字段的值为 `'Meat/Poultry'` 和 `'Seafood'`.
    - 素食

```sql
SELECT
  product_name,
  category_name,
  CASE
    WHEN category_name IN ('Meat/Poultry', 'Seafood') THEN 'Non-vegetarian'
    ELSE 'Vegetarian'
  END AS diet_type
FROM categories c
JOIN products p
  ON c.category_id = p.category_id;
```

### 3.3 在GROUP BY中使用CASE WHEN

- 在引入北美地区免运费的促销策略时，我们也想知道运送到北美地区和其它国家地区的订单数量

```sql
SELECT 
  CASE
    WHEN ship_country = 'USA' OR ship_country = 'Canada' THEN 0.0
    ELSE 10.0
  END AS shipping_cost,
  COUNT(*) AS order_count
FROM orders
GROUP BY
  CASE
    WHEN ship_country = 'USA' OR ship_country = 'Canada' THEN 0.0
    ELSE 10.0
  END;
```

- 在`SELECT`子句和`GROUP BY`子句中，有相同的`CASE WHEN`出现在`GROUP BY`子句中
- 这里并没有使用别名`shipping_cost`。 虽然在SELECT子句中指定了别名（shipping_cost），但标准SQL不允许在GROUP BY子句中引用别名，所以这里`CASE WHEN` 写了两次
- MySQL允许 在`GROUP BY`中使用列别名，在本案例中两种写法都可以
- 注意：CASE WHEN` 语句在 `GROUP BY` 和 `SELECT` 子句中，写法必须相同

#### 练习20

- 需求：创建报表统计供应商来自那个大洲
- 报表中包含两个字段：供应商来自哪个大洲（`supplier_continent` ）和 供应产品种类数量（`product_count`）
- 供应商来自哪个大洲（`supplier_continent` ）包含如下取值：
  - `'North America'` （供应商来自 `'USA'` 和 `'Canada'`.）
  - `'Asia'` （供应商来自 `'Japan'` 和 `'Singapore'`)
  - `'Other'` (其它国家)

```sql
SELECT 
  CASE
    WHEN country IN ('USA', 'Canada') THEN 'North America'
    WHEN country IN ('Japan', 'Singapore') THEN 'Asia'
    ELSE 'Other'
  END AS supplier_continent,
  COUNT(*) AS product_count
FROM products p
JOIN suppliers s
  ON p.supplier_id = s.supplier_id
GROUP BY
  CASE
    WHEN country IN ('USA', 'Canada') THEN 'North America'
    WHEN country IN ('Japan', 'Singapore') THEN 'Asia'
    ELSE 'Other'
  END;
```

#### 练习21

- 需求：创建一个简单的报表来统计员工的年龄情况
- 报表中包含如下字段
  - 年龄（ `age` ）：生日大于1980年1月1日 `'young'` ，其余`'old'` 
  - 员工数量 （ `employee_count`）

```sql
SELECT
  CASE
    WHEN birth_date > '1980-01-01' THEN 'young'
    ELSE 'old'
  END AS age,
  COUNT(*) AS employee_count
FROM employees
GROUP BY
  CASE
    WHEN birth_date > '1980-01-01' THEN 'young'
    ELSE 'old'
  END;
```

### 3.4 CASE WHEN 和 COUNT

- 可以将 `CASE WHEN` 和 `COUNT` 结合使用，自定义分组并统计每组数据数量

```sql
SELECT 
  COUNT(CASE 
    WHEN ship_country = 'USA' OR ship_country = 'Canada' THEN order_id 
  END) AS free_shipping,
  COUNT(CASE
    WHEN ship_country != 'USA' AND ship_country != 'Canada' THEN order_id
  END) AS paid_shipping
FROM orders;
```

在上面的查询中，在`COUNT（）`函数中包含了一个`CASE WHEN`子句。

- 对于每一行，`CASE WHEN`子句会检查`ship_country`中的值。 如果是“ USA”或“ Canada”，则将order_id传递给`COUNT（）`并进行计数。 
- 如果`ship_country`中的值不同，则`CASE WHEN`将返回`NULL`, `COUNT（）`不会统计`NULL`值。 `free_shipping`列将**仅计算运往美国或加拿大的订单”**
- ` paid_shipping`列的构建方式与上述方式类似

#### 练习22

- 需求：统计客户的contact_title 字段值为 ’Owner' 的客户数量
- 查询结果有两个字段：`represented_by_owner` 和 `not_represented_by_owner`

```sql
SELECT 
  COUNT(CASE
    WHEN contact_title = 'Owner' THEN customer_id
  END) AS represented_by_owner,
  COUNT(CASE
    WHEN contact_title != 'Owner' THEN customer_id
  END) AS not_represented_by_owner
FROM customers;
```

#### 练习23

- 需求：Washington (WA) 是 Northwind的主要运营地区，统计有多少订单是由华盛顿地区的员工处理的，多少订单是有其它地区的员工处理的
- 结果字段： `orders_wa_employees` 和 `orders_not_wa_employees`

```sql
SELECT 
  COUNT(CASE
    WHEN region = 'WA' THEN order_id
  END) AS orders_wa_employees,
  COUNT(CASE
    WHEN region != 'WA' THEN order_id
  END) AS orders_not_wa_employees
FROM employees e
JOIN orders o
  ON e.employee_id = o.employee_id;
```

### 3.5 GROUP BY 和 CASE WHEN组合使用

```sql
SELECT 
  ship_country,
  COUNT(CASE
    WHEN freight < 40.0 THEN order_id
  END) AS low_freight,
  COUNT(CASE
    WHEN freight >= 40.0 AND freight < 80.0 THEN order_id
  END) AS avg_freight,
  COUNT(CASE
    WHEN freight >= 80.0 THEN order_id
  END) AS high_freight
FROM orders
GROUP BY ship_country;
```

- 将`COUNT(CASE WHEN...)` 和 `GROUP BY` 组合使用，可以创建更复杂的报表，在报表中，我们将运输到不同国家的订单根据运费高低进一步分成三组，并统计每组数量

#### 练习24

- 需求：创建报表，统计不同类别产品的库存量，将库存量分成两类 >30 和 <=30 两档,分别统计这两档的商品数量
- 报表包含三个字段
  - 类别名称  `category_name`,
  - 库存充足  `high_availability` 
  - 库存紧张 `low_availability` 

```sql
SELECT 
  c.category_name,
  COUNT(CASE
    WHEN units_in_stock > 30 THEN product_id
  END) AS high_availability,
  COUNT(CASE
    WHEN units_in_stock <= 30 THEN product_id
  END) AS low_availability
FROM products p
JOIN categories c
  ON p.category_id = c.category_id
GROUP BY c.category_id,
  c.category_name;
```

### 3.6 SUM中使用CASE WHEN

- 上面通过我们通过  `COUNT()` 函数 和`CASE WHEN`子句联合使用来创建的报表，也可以通过  `SUM()` 来替代 `COUNT()`

```sql
SELECT 
  SUM(CASE
    WHEN ship_country = 'USA' OR ship_country = 'Canada' THEN 1
  END) AS free_shipping,
  SUM(CASE
    WHEN ship_country != 'USA' AND ship_country != 'Canada' THEN 1
  END) AS paid_shipping
FROM orders;
```

- 在上面的查询中，我们将`SUM（）`与`CASE WHEN`一起使用，结果与使用 `COUNT()`相同

#### 练习25

```sql
SELECT 
  COUNT(CASE
    WHEN region = 'WA' THEN order_id
  END) AS orders_wa_employees,
  COUNT(CASE
    WHEN region != 'WA' THEN order_id
  END) AS orders_not_wa_employees
FROM employees e
JOIN orders o
  ON e.employee_id = o.employee_id;
```

- 将上面的SQL修改成用 SUM（） 函数实现

```sql
SELECT 
  SUM(CASE
    WHEN region = 'WA' THEN 1
  END) AS orders_wa_employees,
  SUM(CASE
    WHEN region != 'WA' THEN 1
  END) AS orders_not_wa_employees
FROM employees e
JOIN orders o
  ON e.employee_id = o.employee_id;
```

#### 练习26

- 需求：创建报表统计运输到法国的的订单中，打折和未打折订单的总数量
- 结果包含两个字段：`full_price` （原价）和 `discounted_price`（打折）

```sql
SELECT
  SUM(CASE
    WHEN discount = 0 THEN 1
  END) AS full_price,
  SUM(CASE
    WHEN discount != 0 THEN 1
  END) AS discounted_price
FROM orders o
JOIN order_items oi
  ON o.order_id = oi.order_id
WHERE ship_country = 'France';
```

### 3.7 SUM中使用CASE WHEN进行复杂计算

- 我们现在要统计每个订单的总付款额以及非素食产品的总付款额。

> 注: 非素食产品的产品ID （ `category_id`） 是 6 和 8

```sql
SELECT
  o.order_id,
  SUM(oi.quantity * oi.unit_price * (1 - oi.discount)) AS total_price,
  SUM(CASE
    WHEN p.category_id in (6, 8) THEN oi.quantity * oi.unit_price * (1 - oi.discount)
    ELSE 0
  END) AS non_vegetarian_price
FROM orders o
JOIN order_items oi
  ON o.order_id = oi.order_id
JOIN products p
  ON p.product_id = oi.product_id
GROUP BY o.order_id;
```

- 之前的场景中，我们可以通过`SUM(CASE WHEN...)` 来替换`COUNT(CASE WHEN...)` ，但在上面的例子中，我们只能使用`SUM(CASE WHEN...)` ，因为涉及到不同值的累加，不能通过COUNT计数替代

#### 练习27

- 需求：输出报表，统计不同供应商供应商品的总库存量，以及高价值商品的库存量（单价超过40定义为高价值）
- 结果显示四列：
  - 供应商ID `supplier_id`
  - 供应商公司名 `company_name`
  - 由该供应商提供的总库存 `all_units` 
  - 由该供应商提供的高价值商品库存 `expensive_units` 

```sql
SELECT 
  s.supplier_id,
  s.company_name,
  SUM(units_in_stock) AS all_units,
  SUM(CASE
    WHEN unit_price > 40.0 THEN units_in_stock
    ELSE 0
  END) AS expensive_units
FROM products p
JOIN suppliers s
  ON p.supplier_id = s.supplier_id
GROUP BY s.supplier_id,
  s.company_name;
```

### 小结

1. CASE WHEN语句检查一个或多个条件，并在找到第一个匹配条件时返回一个值。 如果没有`ELSE`子句并且没有匹配条件，则`CASE WHEN`返回`NULL`。

   ```sql
   CASE
     WHEN condition_1 THEN result_1
     WHEN condition_2 THEN result_2
     ...
     ELSE result
   END
   ```

2. 要添加新列，从而对业务数据进行**自定义分组**，可以在`SELECT`子句中使用`CASE WHEN`：

   ```sql
   SELECT 
     CASE
       WHEN ... THEN ...
     END AS sample_column
   FROM table;
   ```

3. 可以在“ GROUP BY”子句中使用“ CASE WHEN”来创建自己的分组。 同样的`CASE WHEN`子句也必须出现在`SELECT`子句中：

   ```sql
   SELECT 
     CASE
       WHEN ... THEN ...
     END AS sample_column,
     COUNT(*) AS sample_count
   FROM table
     ...
   GROUP BY
     CASE WHEN ... THEN ...
     END;
   ```

4. 可以在`COUNT()`或`SUM()`函数内使用`CASE WHEN`来创建业务对象的自定义计数：

   ```sql
   SELECT 
     COUNT(CASE
       WHEN ... THEN column_name
     END) AS count_column
   FROM table;
   ```

   ```sql
   SELECT 
     SUM(CASE
       WHEN ... THEN 1
     END) AS count_column
   FROM table;
   ```

#### 练习28

- 需求：创建报表来为每种商品添加价格标签，贵、中等、便宜
- 结果包含如下字段：`product_id`, `product_name`, `unit_price`, 和 `price_level`
- 价格等级`price_level`的取值说明：
  - `'expensive'`  单价高于100的产品
  - `'average'`  单价高于40但不超过100的产品
  - `'cheap'`  其他产品

```sql
SELECT 
  product_id,
  product_name,
  unit_price,
  CASE
    WHEN unit_price > 100 THEN 'expensive'
    WHEN unit_price > 40 THEN 'average'
    ELSE 'cheap'
  END AS price_level
FROM products;
```

#### 练习29

- 需求：制作报表统计所有订单的总价（不计任何折扣）对它们进行分类。
- 包含一下字段：
  - `order_id`
  - `total_price`（折扣前）
  - `price_group`
- 字段 price_group 取值说明：
  - 总价超过2000美元
  - `'average'`，总价在$ 600到$ 2,000之间，包括两端
  - `'low'` 总价低于$ 600

```sql
SELECT
  order_id,
  SUM(unit_price * quantity) AS total_price,
  CASE
    WHEN SUM(unit_price * quantity) > 2000 THEN 'high'
    WHEN SUM(unit_price * quantity) > 600 THEN 'average'
    ELSE 'low'
  END AS price_group
FROM order_items
GROUP BY order_id;
```

#### 练习30

- 需求：统计所有订单的运费，将运费高低分为三档
- 报表中包含三个字段
  - `low_freight` `freight`值小于“ 40.0”的订单数
  - `avg_freight`  `freight`值大于或等于“ 40.0”但小于“ 80.0”的订单数
  - `high_freight `  `freight`值大于或等于“ 80.0”的订单数

```sql
SELECT
  COUNT(CASE
    WHEN freight >= 80.0 THEN order_id
  END) AS high_freight,
  COUNT(CASE
    WHEN freight < 40.0 THEN order_id
  END) AS low_freight,
  COUNT(CASE
    WHEN freight >= 40.0 AND freight < 80.0 THEN order_id
  END) AS avg_freight
FROM orders;
```







数据

```
/*
 Navicat Premium Data Transfer

 Source Server         : localhost
 Source Server Type    : MySQL
 Source Server Version : 80022
 Source Host           : localhost:3306
 Source Schema         : test

 Target Server Type    : MySQL
 Target Server Version : 80022
 File Encoding         : 65001

 Date: 27/04/2021 19:38:18
*/

SET NAMES utf8mb4;
SET FOREIGN_KEY_CHECKS = 0;

-- ----------------------------
-- Table structure for categories
-- ----------------------------
DROP TABLE IF EXISTS `categories`;
CREATE TABLE `categories` (
  `category_id` int NOT NULL,
  `category_name` varchar(15) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL,
  `description` text CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci,
  PRIMARY KEY (`category_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

-- ----------------------------
-- Records of categories
-- ----------------------------
BEGIN;
INSERT INTO `categories` VALUES (1, 'Beverages', 'Soft drinks, coffees, teas, beers, and ales');
INSERT INTO `categories` VALUES (2, 'Condiments', 'Sweet and savory sauces, relishes, spreads, and seasonings');
INSERT INTO `categories` VALUES (3, 'Confections', 'Desserts, candies, and sweet breads');
INSERT INTO `categories` VALUES (4, 'Dairy Products', 'Cheeses');
INSERT INTO `categories` VALUES (5, 'Grains/Cereals', 'Breads, crackers, pasta, and cereal');
INSERT INTO `categories` VALUES (6, 'Meat/Poultry', 'Prepared meats');
INSERT INTO `categories` VALUES (7, 'Produce', 'Dried fruit and bean curd');
INSERT INTO `categories` VALUES (8, 'Seafood', 'Seaweed and fish');
COMMIT;

-- ----------------------------
-- Table structure for customers
-- ----------------------------
DROP TABLE IF EXISTS `customers`;
CREATE TABLE `customers` (
  `customer_id` varchar(5) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci NOT NULL,
  `company_name` varchar(40) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL,
  `contact_name` varchar(30) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL,
  `contact_title` varchar(30) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL,
  `address` varchar(60) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL,
  `city` varchar(15) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL,
  `region` varchar(15) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL,
  `postal_code` varchar(10) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL,
  `country` varchar(15) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL,
  `fax` varchar(24) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL,
  PRIMARY KEY (`customer_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

-- ----------------------------
-- Records of customers
-- ----------------------------
BEGIN;
INSERT INTO `customers` VALUES ('ALFKI', 'Alfreds Futterkiste', 'Maria Anders', 'Sales Representative', 'Obere Str. 57', 'Berlin', NULL, '12209', 'Germany', '030-0076545');
INSERT INTO `customers` VALUES ('ANATR', 'Ana Trujillo Emparedados y helados', 'Ana Trujillo', 'Owner', 'Avda. de la Constitución 2222', 'México D.F.', NULL, '5021', 'Mexico', '(5) 555-3745');
INSERT INTO `customers` VALUES ('ANTON', 'Antonio Moreno Taquería', 'Antonio Moreno', 'Owner', 'Mataderos 2312', 'México D.F.', NULL, '5023', 'Mexico', NULL);
INSERT INTO `customers` VALUES ('AROUT', 'Around the Horn', 'Thomas Hardy', 'Sales Representative', '120 Hanover Sq.', 'London', NULL, 'WA1 1DP', 'UK', '(171) 555-6750');
INSERT INTO `customers` VALUES ('BERGS', 'Berglunds snabbköp', 'Christina Berglund', 'Order Administrator', 'Berguvsvägen 8', 'Luleå', NULL, 'S-958 22', 'Sweden', '0921-12 34 67');
INSERT INTO `customers` VALUES ('BLAUS', 'Blauer See Delikatessen', 'Hanna Moos', 'Sales Representative', 'Forsterstr. 57', 'Mannheim', NULL, '68306', 'Germany', '0621-08924');
INSERT INTO `customers` VALUES ('BLONP', 'Blondesddsl père et fils', 'Frédérique Citeaux', 'Marketing Manager', '24, place Kléber', 'Strasbourg', NULL, '67000', 'France', '88.60.15.32');
INSERT INTO `customers` VALUES ('BOLID', 'Bólido Comidas preparadas', 'Martín Sommer', 'Owner', 'C/ Araquil, 67', 'Madrid', NULL, '28023', 'Spain', '(91) 555 91 99');
INSERT INTO `customers` VALUES ('BONAP', 'Bon app\'', 'Laurence Lebihan', 'Owner', '12, rue des Bouchers', 'Marseille', NULL, '13008', 'France', '91.24.45.41');
INSERT INTO `customers` VALUES ('BOTTM', 'Bottom-Dollar Markets', 'Elizabeth Lincoln', 'Accounting Manager', '23 Tsawassen Blvd.', 'Tsawassen', 'BC', 'T2F 8M4', 'Canada', '(604) 555-3745');
INSERT INTO `customers` VALUES ('BSBEV', 'B\'s Beverages', 'Victoria Ashworth', 'Sales Representative', 'Fauntleroy Circus', 'London', NULL, 'EC2 5NT', 'UK', NULL);
INSERT INTO `customers` VALUES ('CACTU', 'Cactus Comidas para llevar', 'Patricio Simpson', 'Sales Agent', 'Cerrito 333', 'Buenos Aires', NULL, '1010', 'Argentina', '(1) 135-4892');
INSERT INTO `customers` VALUES ('CENTC', 'Centro comercial Moctezuma', 'Francisco Chang', 'Marketing Manager', 'Sierras de Granada 9993', 'México D.F.', NULL, '5022', 'Mexico', '(5) 555-7293');
INSERT INTO `customers` VALUES ('CHOPS', 'Chop-suey Chinese', 'Yang Wang', 'Owner', 'Hauptstr. 29', 'Bern', NULL, '3012', 'Switzerland', NULL);
INSERT INTO `customers` VALUES ('COMMI', 'Comércio Mineiro', 'Pedro Afonso', 'Sales Associate', 'Av. dos Lusíadas, 23', 'Sao Paulo', 'SP', '05432-043', 'Brazil', NULL);
INSERT INTO `customers` VALUES ('CONSH', 'Consolidated Holdings', 'Elizabeth Brown', 'Sales Representative', 'Berkeley Gardens 12 Brewery', 'London', NULL, 'WX1 6LT', 'UK', '(171) 555-9199');
INSERT INTO `customers` VALUES ('DRACD', 'Drachenblut Delikatessen', 'Sven Ottlieb', 'Order Administrator', 'Walserweg 21', 'Aachen', NULL, '52066', 'Germany', '0241-059428');
INSERT INTO `customers` VALUES ('DUMON', 'Du monde entier', 'Janine Labrune', 'Owner', '67, rue des Cinquante Otages', 'Nantes', NULL, '44000', 'France', '40.67.89.89');
INSERT INTO `customers` VALUES ('EASTC', 'Eastern Connection', 'Ann Devon', 'Sales Agent', '35 King George', 'London', NULL, 'WX3 6FW', 'UK', '(171) 555-3373');
INSERT INTO `customers` VALUES ('ERNSH', 'Ernst Handel', 'Roland Mendel', 'Sales Manager', 'Kirchgasse 6', 'Graz', NULL, '8010', 'Austria', '7675-3426');
INSERT INTO `customers` VALUES ('FAMIA', 'Familia Arquibaldo', 'Aria Cruz', 'Marketing Assistant', 'Rua Orós, 92', 'Sao Paulo', 'SP', '05442-030', 'Brazil', NULL);
INSERT INTO `customers` VALUES ('FISSA', 'FISSA Fabrica Inter. Salchichas S.A.', 'Diego Roel', 'Accounting Manager', 'C/ Moralzarzal, 86', 'Madrid', NULL, '28034', 'Spain', '(91) 555 55 93');
INSERT INTO `customers` VALUES ('FOLIG', 'Folies gourmandes', 'Martine Rancé', 'Assistant Sales Agent', '184, chaussée de Tournai', 'Lille', NULL, '59000', 'France', '20.16.10.17');
INSERT INTO `customers` VALUES ('FOLKO', 'Folk och fä HB', 'Maria Larsson', 'Owner', 'Åkergatan 24', 'Bräcke', NULL, 'S-844 67', 'Sweden', NULL);
INSERT INTO `customers` VALUES ('FRANK', 'Frankenversand', 'Peter Franken', 'Marketing Manager', 'Berliner Platz 43', 'München', NULL, '80805', 'Germany', '089-0877451');
INSERT INTO `customers` VALUES ('FRANR', 'France restauration', 'Carine Schmitt', 'Marketing Manager', '54, rue Royale', 'Nantes', NULL, '44000', 'France', '40.32.21.20');
INSERT INTO `customers` VALUES ('FRANS', 'Franchi S.p.A.', 'Paolo Accorti', 'Sales Representative', 'Via Monte Bianco 34', 'Torino', NULL, '10100', 'Italy', '011-4988261');
INSERT INTO `customers` VALUES ('FURIB', 'Furia Bacalhau e Frutos do Mar', 'Lino Rodriguez', 'Sales Manager', 'Jardim das rosas n. 32', 'Lisboa', NULL, '1675', 'Portugal', '(1) 354-2535');
INSERT INTO `customers` VALUES ('GALED', 'Galería del gastrónomo', 'Eduardo Saavedra', 'Marketing Manager', 'Rambla de Cataluña, 23', 'Barcelona', NULL, '8022', 'Spain', '(93) 203 4561');
INSERT INTO `customers` VALUES ('GODOS', 'Godos Cocina Típica', 'José Pedro Freyre', 'Sales Manager', 'C/ Romero, 33', 'Sevilla', NULL, '41101', 'Spain', NULL);
INSERT INTO `customers` VALUES ('GOURL', 'Gourmet Lanchonetes', 'André Fonseca', 'Sales Associate', 'Av. Brasil, 442', 'Campinas', 'SP', '04876-786', 'Brazil', NULL);
INSERT INTO `customers` VALUES ('GREAL', 'Great Lakes Food Market', 'Howard Snyder', 'Marketing Manager', '2732 Baker Blvd.', 'Eugene', 'OR', '97403', 'USA', NULL);
INSERT INTO `customers` VALUES ('GROSR', 'GROSELLA-Restaurante', 'Manuel Pereira', 'Owner', '5ª Ave. Los Palos Grandes', 'Caracas', 'DF', '1081', 'Venezuela', '(2) 283-3397');
INSERT INTO `customers` VALUES ('HANAR', 'Hanari Carnes', 'Mario Pontes', 'Accounting Manager', 'Rua do Paço, 67', 'Rio de Janeiro', 'RJ', '05454-876', 'Brazil', '(21) 555-8765');
INSERT INTO `customers` VALUES ('HILAA', 'HILARION-Abastos', 'Carlos Hernández', 'Sales Representative', 'Carrera 22 con Ave. Carlos Soublette #8-35', 'San Cristóbal', 'Táchira', '5022', 'Venezuela', '(5) 555-1948');
INSERT INTO `customers` VALUES ('HUNGC', 'Hungry Coyote Import Store', 'Yoshi Latimer', 'Sales Representative', 'City Center Plaza 516 Main St.', 'Elgin', 'OR', '97827', 'USA', '(503) 555-2376');
INSERT INTO `customers` VALUES ('HUNGO', 'Hungry Owl All-Night Grocers', 'Patricia McKenna', 'Sales Associate', '8 Johnstown Road', 'Cork', 'Co. Cork', 'null', 'Ireland', '2967 3333');
INSERT INTO `customers` VALUES ('ISLAT', 'Island Trading', 'Helen Bennett', 'Marketing Manager', 'Garden House Crowther Way', 'Cowes', 'Isle of Wight', 'PO31 7PJ', 'UK', NULL);
INSERT INTO `customers` VALUES ('KOENE', 'Königlich Essen', 'Philip Cramer', 'Sales Associate', 'Maubelstr. 90', 'Brandenburg', NULL, '14776', 'Germany', NULL);
INSERT INTO `customers` VALUES ('LACOR', 'La corne d\'abondance', 'Daniel Tonini', 'Sales Representative', '67, avenue de l\'Europe', 'Versailles', NULL, '78000', 'France', '30.59.85.11');
INSERT INTO `customers` VALUES ('LAMAI', 'La maison d\'Asie', 'Annette Roulet', 'Sales Manager', '1 rue Alsace-Lorraine', 'Toulouse', NULL, '31000', 'France', '61.77.61.11');
INSERT INTO `customers` VALUES ('LAUGB', 'Laughing Bacchus Wine Cellars', 'Yoshi Tannamuri', 'Marketing Assistant', '1900 Oak St.', 'Vancouver', 'BC', 'V3F 2K1', 'Canada', '(604) 555-7293');
INSERT INTO `customers` VALUES ('LAZYK', 'Lazy K Kountry Store', 'John Steel', 'Marketing Manager', '12 Orchestra Terrace', 'Walla Walla', 'WA', '99362', 'USA', '(509) 555-6221');
INSERT INTO `customers` VALUES ('LEHMS', 'Lehmanns Marktstand', 'Renate Messner', 'Sales Representative', 'Magazinweg 7', 'Frankfurt a.M.', NULL, '60528', 'Germany', '069-0245874');
INSERT INTO `customers` VALUES ('LETSS', 'Let\'s Stop N Shop', 'Jaime Yorres', 'Owner', '87 Polk St. Suite 5', 'San Francisco', 'CA', '94117', 'USA', NULL);
INSERT INTO `customers` VALUES ('LILAS', 'LILA-Supermercado', 'Carlos González', 'Accounting Manager', 'Carrera 52 con Ave. Bolívar #65-98 Llano Largo', 'Barquisimeto', 'Lara', '3508', 'Venezuela', '(9) 331-7256');
INSERT INTO `customers` VALUES ('LINOD', 'LINO-Delicateses', 'Felipe Izquierdo', 'Owner', 'Ave. 5 de Mayo Porlamar', 'I. de Margarita', 'Nueva Esparta', '4980', 'Venezuela', '(8) 34-93-93');
INSERT INTO `customers` VALUES ('LONEP', 'Lonesome Pine Restaurant', 'Fran Wilson', 'Sales Manager', '89 Chiaroscuro Rd.', 'Portland', 'OR', '97219', 'USA', '(503) 555-9646');
INSERT INTO `customers` VALUES ('MAGAA', 'Magazzini Alimentari Riuniti', 'Giovanni Rovelli', 'Marketing Manager', 'Via Ludovico il Moro 22', 'Bergamo', NULL, '24100', 'Italy', '035-640231');
INSERT INTO `customers` VALUES ('MAISD', 'Maison Dewey', 'Catherine Dewey', 'Sales Agent', 'Rue Joseph-Bens 532', 'Bruxelles', NULL, 'B-1180', 'Belgium', '(02) 201 24 68');
INSERT INTO `customers` VALUES ('MEREP', 'Mère Paillarde', 'Jean Fresnière', 'Marketing Assistant', '43 rue St. Laurent', 'Montréal', 'Québec', 'H1J 1C3', 'Canada', '(514) 555-8055');
INSERT INTO `customers` VALUES ('MORGK', 'Morgenstern Gesundkost', 'Alexander Feuer', 'Marketing Assistant', 'Heerstr. 22', 'Leipzig', NULL, '4179', 'Germany', NULL);
INSERT INTO `customers` VALUES ('NORTS', 'North/South', 'Simon Crowther', 'Sales Associate', 'South House 300 Queensbridge', 'London', NULL, 'SW7 1RZ', 'UK', '(171) 555-2530');
INSERT INTO `customers` VALUES ('OCEAN', 'Océano Atlántico Ltda.', 'Yvonne Moncada', 'Sales Agent', 'Ing. Gustavo Moncada 8585 Piso 20-A', 'Buenos Aires', NULL, '1010', 'Argentina', '(1) 135-5535');
INSERT INTO `customers` VALUES ('OLDWO', 'Old World Delicatessen', 'Rene Phillips', 'Sales Representative', '2743 Bering St.', 'Anchorage', 'AK', '99508', 'USA', '(907) 555-2880');
INSERT INTO `customers` VALUES ('OTTIK', 'Ottilies Käseladen', 'Henriette Pfalzheim', 'Owner', 'Mehrheimerstr. 369', 'Köln', NULL, '50739', 'Germany', '0221-0765721');
INSERT INTO `customers` VALUES ('PARIS', 'Paris spécialités', 'Marie Bertrand', 'Owner', '265, boulevard Charonne', 'Paris', NULL, '75012', 'France', '(1) 42.34.22.77');
INSERT INTO `customers` VALUES ('PERIC', 'Pericles Comidas clásicas', 'Guillermo Fernández', 'Sales Representative', 'Calle Dr. Jorge Cash 321', 'México D.F.', NULL, '5033', 'Mexico', '(5) 545-3745');
INSERT INTO `customers` VALUES ('PICCO', 'Piccolo und mehr', 'Georg Pipps', 'Sales Manager', 'Geislweg 14', 'Salzburg', NULL, '5020', 'Austria', '6562-9723');
INSERT INTO `customers` VALUES ('PRINI', 'Princesa Isabel Vinhos', 'Isabel de Castro', 'Sales Representative', 'Estrada da saúde n. 58', 'Lisboa', NULL, '1756', 'Portugal', NULL);
INSERT INTO `customers` VALUES ('QUEDE', 'Que Delícia', 'Bernardo Batista', 'Accounting Manager', 'Rua da Panificadora, 12', 'Rio de Janeiro', 'RJ', '02389-673', 'Brazil', '(21) 555-4545');
INSERT INTO `customers` VALUES ('QUEEN', 'Queen Cozinha', 'Lúcia Carvalho', 'Marketing Assistant', 'Alameda dos Canàrios, 891', 'Sao Paulo', 'SP', '05487-020', 'Brazil', NULL);
INSERT INTO `customers` VALUES ('QUICK', 'QUICK-Stop', 'Horst Kloss', 'Accounting Manager', 'Taucherstraße 10', 'Cunewalde', NULL, '1307', 'Germany', NULL);
INSERT INTO `customers` VALUES ('RANCH', 'Rancho grande', 'Sergio Gutiérrez', 'Sales Representative', 'Av. del Libertador 900', 'Buenos Aires', NULL, '1010', 'Argentina', '(1) 123-5556');
INSERT INTO `customers` VALUES ('RATTC', 'Rattlesnake Canyon Grocery', 'Paula Wilson', 'Assistant Sales Representative', '2817 Milton Dr.', 'Albuquerque', 'NM', '87110', 'USA', '(505) 555-3620');
INSERT INTO `customers` VALUES ('REGGC', 'Reggiani Caseifici', 'Maurizio Moroni', 'Sales Associate', 'Strada Provinciale 124', 'Reggio Emilia', NULL, '42100', 'Italy', '0522-556722');
INSERT INTO `customers` VALUES ('RICAR', 'Ricardo Adocicados', 'Janete Limeira', 'Assistant Sales Agent', 'Av. Copacabana, 267', 'Rio de Janeiro', 'RJ', '02389-890', 'Brazil', NULL);
INSERT INTO `customers` VALUES ('RICSU', 'Richter Supermarkt', 'Michael Holz', 'Sales Manager', 'Grenzacherweg 237', 'Genève', NULL, '1203', 'Switzerland', NULL);
INSERT INTO `customers` VALUES ('ROMEY', 'Romero y tomillo', 'Alejandra Camino', 'Accounting Manager', 'Gran Vía, 1', 'Madrid', NULL, '28001', 'Spain', '(91) 745 6210');
INSERT INTO `customers` VALUES ('SANTG', 'Santé Gourmet', 'Jonas Bergulfsen', 'Owner', 'Erling Skakkes gate 78', 'Stavern', NULL, '4110', 'Norway', '07-98 92 47');
INSERT INTO `customers` VALUES ('SAVEA', 'Save-a-lot Markets', 'Jose Pavarotti', 'Sales Representative', '187 Suffolk Ln.', 'Boise', 'ID', '83720', 'USA', NULL);
INSERT INTO `customers` VALUES ('SEVES', 'Seven Seas Imports', 'Hari Kumar', 'Sales Manager', '90 Wadhurst Rd.', 'London', NULL, 'OX15 4NB', 'UK', '(171) 555-5646');
INSERT INTO `customers` VALUES ('SIMOB', 'Simons bistro', 'Jytte Petersen', 'Owner', 'Vinbæltet 34', 'Kobenhavn', NULL, '1734', 'Denmark', '31 13 35 57');
INSERT INTO `customers` VALUES ('SPECD', 'Spécialités du monde', 'Dominique Perrier', 'Marketing Manager', '25, rue Lauriston', 'Paris', NULL, '75016', 'France', '(1) 47.55.60.20');
INSERT INTO `customers` VALUES ('SPLIR', 'Split Rail Beer & Ale', 'Art Braunschweiger', 'Sales Manager', 'P.O. Box 555', 'Lander', 'WY', '82520', 'USA', '(307) 555-6525');
INSERT INTO `customers` VALUES ('SUPRD', 'Suprêmes délices', 'Pascale Cartrain', 'Accounting Manager', 'Boulevard Tirou, 255', 'Charleroi', NULL, 'B-6000', 'Belgium', '(071) 23 67 22 21');
INSERT INTO `customers` VALUES ('THEBI', 'The Big Cheese', 'Liz Nixon', 'Marketing Manager', '89 Jefferson Way Suite 2', 'Portland', 'OR', '97201', 'USA', NULL);
INSERT INTO `customers` VALUES ('THECR', 'The Cracker Box', 'Liu Wong', 'Marketing Assistant', '55 Grizzly Peak Rd.', 'Butte', 'MT', '59801', 'USA', '(406) 555-8083');
INSERT INTO `customers` VALUES ('TOMSP', 'Toms Spezialitäten', 'Karin Josephs', 'Marketing Manager', 'Luisenstr. 48', 'Münster', NULL, '44087', 'Germany', '0251-035695');
INSERT INTO `customers` VALUES ('TORTU', 'Tortuga Restaurante', 'Miguel Angel Paolino', 'Owner', 'Avda. Azteca 123', 'México D.F.', NULL, '5033', 'Mexico', NULL);
INSERT INTO `customers` VALUES ('TRADH', 'Tradição Hipermercados', 'Anabela Domingues', 'Sales Representative', 'Av. Inês de Castro, 414', 'Sao Paulo', 'SP', '05634-030', 'Brazil', '(11) 555-2168');
INSERT INTO `customers` VALUES ('TRAIH', 'Trail\'s Head Gourmet Provisioners', 'Helvetius Nagy', 'Sales Associate', '722 DaVinci Blvd.', 'Kirkland', 'WA', '98034', 'USA', '(206) 555-2174');
INSERT INTO `customers` VALUES ('VAFFE', 'Vaffeljernet', 'Palle Ibsen', 'Sales Manager', 'Smagsloget 45', 'Århus', NULL, '8200', 'Denmark', '86 22 33 44');
INSERT INTO `customers` VALUES ('VICTE', 'Victuailles en stock', 'Mary Saveley', 'Sales Agent', '2, rue du Commerce', 'Lyon', NULL, '69004', 'France', '78.32.54.87');
INSERT INTO `customers` VALUES ('VINET', 'Vins et alcools Chevalier', 'Paul Henriot', 'Accounting Manager', '59 rue de l\'Abbaye', 'Reims', NULL, '51100', 'France', '26.47.15.11');
INSERT INTO `customers` VALUES ('WANDK', 'Die Wandernde Kuh', 'Rita Müller', 'Sales Representative', 'Adenauerallee 900', 'Stuttgart', NULL, '70563', 'Germany', '0711-035428');
INSERT INTO `customers` VALUES ('WARTH', 'Wartian Herkku', 'Pirkko Koskitalo', 'Accounting Manager', 'Torikatu 38', 'Oulu', NULL, '90110', 'Finland', '981-443655');
INSERT INTO `customers` VALUES ('WELLI', 'Wellington Importadora', 'Paula Parente', 'Sales Manager', 'Rua do Mercado, 12', 'Resende', 'SP', '08737-363', 'Brazil', NULL);
INSERT INTO `customers` VALUES ('WHITC', 'White Clover Markets', 'Karl Jablonski', 'Owner', '305 - 14th Ave. S. Suite 3B', 'Seattle', 'WA', '98128', 'USA', '(206) 555-4115');
INSERT INTO `customers` VALUES ('WILMK', 'Wilman Kala', 'Matti Karttunen', 'Owner/Marketing Assistant', 'Keskuskatu 45', 'Helsinki', NULL, '21240', 'Finland', '90-224 8858');
INSERT INTO `customers` VALUES ('WOLZA', 'Wolski Zajazd', 'Zbyszek Piestrzeniewicz', 'Owner', 'ul. Filtrowa 68', 'Warszawa', NULL, '01-012', 'Poland', '(26) 642-7012');
COMMIT;

-- ----------------------------
-- Table structure for employees
-- ----------------------------
DROP TABLE IF EXISTS `employees`;
CREATE TABLE `employees` (
  `employee_id` int NOT NULL,
  `last_name` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL,
  `first_name` varchar(10) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL,
  `title` varchar(30) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL,
  `birth_date` datetime DEFAULT NULL,
  `hire_date` datetime DEFAULT NULL,
  `address` varchar(60) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL,
  `city` varchar(15) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL,
  `region` varchar(15) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL,
  `postal_code` varchar(10) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL,
  `country` varchar(15) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL,
  `reports_to` varchar(10) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL,
  PRIMARY KEY (`employee_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

-- ----------------------------
-- Records of employees
-- ----------------------------
BEGIN;
INSERT INTO `employees` VALUES (1, 'Davolio', 'Nancy', 'Sales Representative', '1968-12-08 00:00:00', '2012-05-01 00:00:00', '507 - 20th Ave. E. Apt. 2A', 'Seattle', 'WA', '98122', 'USA', '2');
INSERT INTO `employees` VALUES (2, 'Fuller', 'Andrew', 'Vice President, Sales', '1972-02-19 00:00:00', '2012-08-14 00:00:00', '908 W. Capital Way', 'Tacoma', 'WA', '98401', 'USA', NULL);
INSERT INTO `employees` VALUES (3, 'Smith', 'John', 'Sales Representative', '1983-08-30 00:00:00', '2012-04-01 00:00:00', '722 Moss Bay Blvd.', 'Kirkland', 'WA', '98033', 'USA', '2');
INSERT INTO `employees` VALUES (4, 'Peacock', 'Margaret', 'Sales Representative', '1957-09-19 00:00:00', '2013-05-03 00:00:00', '4110 Old Redmond Rd.', 'Redmond', 'WA', '98052', 'USA', '2');
INSERT INTO `employees` VALUES (5, 'Buchanan', 'Steven', 'Sales Manager', '1975-03-04 00:00:00', '2013-10-17 00:00:00', '14 Garrett Hill', 'London', 'null', 'SW1 8JR', 'UK', '2');
INSERT INTO `employees` VALUES (6, 'Suyama', 'Michael', 'Sales Representative', '1983-07-02 00:00:00', '2013-10-17 00:00:00', 'Coventry House Miner Rd.', 'London', 'null', 'EC2 7JR', 'UK', '5');
INSERT INTO `employees` VALUES (7, 'King', 'Robert', 'Sales Representative', '1980-05-29 00:00:00', '2014-01-02 00:00:00', 'Edgeham Hollow Winchester Way', 'London', 'null', 'RG1 9SP', 'UK', '5');
INSERT INTO `employees` VALUES (8, 'Callahan', 'Laura', 'Inside Sales Coordinator', '1978-01-09 00:00:00', '2014-03-05 00:00:00', '4726 - 11th Ave. N.E.', 'Seattle', 'WA', '98105', 'USA', '2');
INSERT INTO `employees` VALUES (9, 'Dodsworth', 'Anne', 'Sales Representative', '1986-01-27 00:00:00', '2014-11-15 00:00:00', '7 Houndstooth Rd.', 'London', 'null', 'WG2 7LT', 'UK', '5');
INSERT INTO `employees` VALUES (10, 'Smith', 'John', 'Sales Representative', '1994-08-30 00:00:00', '2017-03-21 00:00:00', '22 Abbey Rd', 'London', 'null', 'NW6 5JG', 'UK', '2');
COMMIT;

-- ----------------------------
-- Table structure for order_items
-- ----------------------------
DROP TABLE IF EXISTS `order_items`;
CREATE TABLE `order_items` (
  `order_id` int NOT NULL,
  `product_id` int NOT NULL,
  `unit_price` decimal(10,2) DEFAULT NULL,
  `quantity` smallint DEFAULT NULL,
  `discount` double(24,2) DEFAULT NULL,
  PRIMARY KEY (`order_id`,`product_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

-- ----------------------------
-- Records of order_items
-- ----------------------------
BEGIN;
INSERT INTO `order_items` VALUES (10248, 11, 14.00, 12, 0.00);
INSERT INTO `order_items` VALUES (10248, 42, 9.80, 10, 0.00);
INSERT INTO `order_items` VALUES (10248, 72, 34.80, 5, 0.00);
INSERT INTO `order_items` VALUES (10249, 14, 18.60, 9, 0.00);
INSERT INTO `order_items` VALUES (10249, 51, 42.40, 40, 0.00);
INSERT INTO `order_items` VALUES (10250, 41, 7.70, 10, 0.00);
INSERT INTO `order_items` VALUES (10250, 51, 42.40, 35, 0.15);
INSERT INTO `order_items` VALUES (10250, 65, 16.80, 15, 0.15);
INSERT INTO `order_items` VALUES (10251, 22, 16.80, 6, 0.05);
INSERT INTO `order_items` VALUES (10251, 57, 15.60, 15, 0.05);
INSERT INTO `order_items` VALUES (10251, 65, 16.80, 20, 0.00);
INSERT INTO `order_items` VALUES (10252, 20, 64.80, 40, 0.05);
INSERT INTO `order_items` VALUES (10252, 33, 2.00, 25, 0.05);
INSERT INTO `order_items` VALUES (10252, 60, 27.20, 40, 0.00);
INSERT INTO `order_items` VALUES (10253, 31, 10.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10253, 39, 14.40, 42, 0.00);
INSERT INTO `order_items` VALUES (10253, 49, 16.00, 40, 0.00);
INSERT INTO `order_items` VALUES (10254, 24, 3.60, 15, 0.15);
INSERT INTO `order_items` VALUES (10254, 55, 19.20, 21, 0.15);
INSERT INTO `order_items` VALUES (10254, 74, 8.00, 21, 0.00);
INSERT INTO `order_items` VALUES (10255, 2, 15.20, 20, 0.00);
INSERT INTO `order_items` VALUES (10255, 16, 13.90, 35, 0.00);
INSERT INTO `order_items` VALUES (10255, 36, 15.20, 25, 0.00);
INSERT INTO `order_items` VALUES (10255, 59, 44.00, 30, 0.00);
INSERT INTO `order_items` VALUES (10256, 53, 26.20, 15, 0.00);
INSERT INTO `order_items` VALUES (10256, 77, 10.40, 12, 0.00);
INSERT INTO `order_items` VALUES (10257, 27, 35.10, 25, 0.00);
INSERT INTO `order_items` VALUES (10257, 39, 14.40, 6, 0.00);
INSERT INTO `order_items` VALUES (10257, 77, 10.40, 15, 0.00);
INSERT INTO `order_items` VALUES (10258, 2, 15.20, 50, 0.20);
INSERT INTO `order_items` VALUES (10258, 5, 17.00, 65, 0.20);
INSERT INTO `order_items` VALUES (10258, 32, 25.60, 6, 0.20);
INSERT INTO `order_items` VALUES (10259, 21, 8.00, 10, 0.00);
INSERT INTO `order_items` VALUES (10259, 37, 20.80, 1, 0.00);
INSERT INTO `order_items` VALUES (10260, 41, 7.70, 16, 0.25);
INSERT INTO `order_items` VALUES (10260, 57, 15.60, 50, 0.00);
INSERT INTO `order_items` VALUES (10260, 62, 39.40, 15, 0.25);
INSERT INTO `order_items` VALUES (10260, 70, 12.00, 21, 0.25);
INSERT INTO `order_items` VALUES (10261, 21, 8.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10261, 35, 14.40, 20, 0.00);
INSERT INTO `order_items` VALUES (10262, 5, 17.00, 12, 0.20);
INSERT INTO `order_items` VALUES (10262, 7, 24.00, 15, 0.00);
INSERT INTO `order_items` VALUES (10262, 56, 30.40, 2, 0.00);
INSERT INTO `order_items` VALUES (10263, 16, 13.90, 60, 0.25);
INSERT INTO `order_items` VALUES (10263, 24, 3.60, 28, 0.00);
INSERT INTO `order_items` VALUES (10263, 30, 20.70, 60, 0.25);
INSERT INTO `order_items` VALUES (10263, 74, 8.00, 36, 0.25);
INSERT INTO `order_items` VALUES (10264, 2, 15.20, 35, 0.00);
INSERT INTO `order_items` VALUES (10264, 41, 7.70, 25, 0.15);
INSERT INTO `order_items` VALUES (10265, 17, 31.20, 30, 0.00);
INSERT INTO `order_items` VALUES (10265, 70, 12.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10266, 12, 30.40, 12, 0.05);
INSERT INTO `order_items` VALUES (10267, 40, 14.70, 50, 0.00);
INSERT INTO `order_items` VALUES (10267, 59, 44.00, 70, 0.15);
INSERT INTO `order_items` VALUES (10267, 76, 14.40, 15, 0.15);
INSERT INTO `order_items` VALUES (10268, 29, 99.00, 10, 0.00);
INSERT INTO `order_items` VALUES (10268, 72, 27.80, 4, 0.00);
INSERT INTO `order_items` VALUES (10269, 33, 2.00, 60, 0.05);
INSERT INTO `order_items` VALUES (10269, 72, 27.80, 20, 0.05);
INSERT INTO `order_items` VALUES (10270, 36, 15.20, 30, 0.00);
INSERT INTO `order_items` VALUES (10270, 43, 36.80, 25, 0.00);
INSERT INTO `order_items` VALUES (10271, 33, 2.00, 24, 0.00);
INSERT INTO `order_items` VALUES (10272, 20, 64.80, 6, 0.00);
INSERT INTO `order_items` VALUES (10272, 31, 10.00, 40, 0.00);
INSERT INTO `order_items` VALUES (10272, 72, 27.80, 24, 0.00);
INSERT INTO `order_items` VALUES (10273, 10, 24.80, 24, 0.05);
INSERT INTO `order_items` VALUES (10273, 31, 10.00, 15, 0.05);
INSERT INTO `order_items` VALUES (10273, 33, 2.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10273, 40, 14.70, 60, 0.05);
INSERT INTO `order_items` VALUES (10273, 76, 14.40, 33, 0.05);
INSERT INTO `order_items` VALUES (10274, 71, 17.20, 20, 0.00);
INSERT INTO `order_items` VALUES (10274, 72, 27.80, 7, 0.00);
INSERT INTO `order_items` VALUES (10275, 24, 3.60, 12, 0.05);
INSERT INTO `order_items` VALUES (10275, 59, 44.00, 6, 0.05);
INSERT INTO `order_items` VALUES (10276, 10, 24.80, 15, 0.00);
INSERT INTO `order_items` VALUES (10276, 13, 4.80, 10, 0.00);
INSERT INTO `order_items` VALUES (10277, 28, 36.40, 20, 0.00);
INSERT INTO `order_items` VALUES (10277, 62, 39.40, 12, 0.00);
INSERT INTO `order_items` VALUES (10278, 44, 15.50, 16, 0.00);
INSERT INTO `order_items` VALUES (10278, 59, 44.00, 15, 0.00);
INSERT INTO `order_items` VALUES (10278, 63, 35.10, 8, 0.00);
INSERT INTO `order_items` VALUES (10278, 73, 12.00, 25, 0.00);
INSERT INTO `order_items` VALUES (10279, 17, 31.20, 15, 0.25);
INSERT INTO `order_items` VALUES (10280, 24, 3.60, 12, 0.00);
INSERT INTO `order_items` VALUES (10280, 55, 19.20, 20, 0.00);
INSERT INTO `order_items` VALUES (10280, 75, 6.20, 30, 0.00);
INSERT INTO `order_items` VALUES (10281, 19, 7.30, 1, 0.00);
INSERT INTO `order_items` VALUES (10281, 24, 3.60, 6, 0.00);
INSERT INTO `order_items` VALUES (10281, 35, 14.40, 4, 0.00);
INSERT INTO `order_items` VALUES (10282, 30, 20.70, 6, 0.00);
INSERT INTO `order_items` VALUES (10282, 57, 15.60, 2, 0.00);
INSERT INTO `order_items` VALUES (10283, 15, 12.40, 20, 0.00);
INSERT INTO `order_items` VALUES (10283, 19, 7.30, 18, 0.00);
INSERT INTO `order_items` VALUES (10283, 60, 27.20, 35, 0.00);
INSERT INTO `order_items` VALUES (10283, 72, 27.80, 3, 0.00);
INSERT INTO `order_items` VALUES (10284, 27, 35.10, 15, 0.25);
INSERT INTO `order_items` VALUES (10284, 44, 15.50, 21, 0.00);
INSERT INTO `order_items` VALUES (10284, 60, 27.20, 20, 0.25);
INSERT INTO `order_items` VALUES (10284, 67, 11.20, 5, 0.25);
INSERT INTO `order_items` VALUES (10285, 1, 14.40, 45, 0.20);
INSERT INTO `order_items` VALUES (10285, 40, 14.70, 40, 0.20);
INSERT INTO `order_items` VALUES (10285, 53, 26.20, 36, 0.20);
INSERT INTO `order_items` VALUES (10286, 35, 14.40, 100, 0.00);
INSERT INTO `order_items` VALUES (10286, 62, 39.40, 40, 0.00);
INSERT INTO `order_items` VALUES (10287, 16, 13.90, 40, 0.15);
INSERT INTO `order_items` VALUES (10287, 34, 11.20, 20, 0.00);
INSERT INTO `order_items` VALUES (10287, 46, 9.60, 15, 0.15);
INSERT INTO `order_items` VALUES (10288, 54, 5.90, 10, 0.10);
INSERT INTO `order_items` VALUES (10288, 68, 10.00, 3, 0.10);
INSERT INTO `order_items` VALUES (10289, 3, 8.00, 30, 0.00);
INSERT INTO `order_items` VALUES (10289, 64, 26.60, 9, 0.00);
INSERT INTO `order_items` VALUES (10290, 5, 17.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10290, 29, 99.00, 15, 0.00);
INSERT INTO `order_items` VALUES (10290, 49, 16.00, 15, 0.00);
INSERT INTO `order_items` VALUES (10290, 77, 10.40, 10, 0.00);
INSERT INTO `order_items` VALUES (10291, 13, 4.80, 20, 0.10);
INSERT INTO `order_items` VALUES (10291, 44, 15.50, 24, 0.10);
INSERT INTO `order_items` VALUES (10291, 51, 42.40, 2, 0.10);
INSERT INTO `order_items` VALUES (10292, 20, 64.80, 20, 0.00);
INSERT INTO `order_items` VALUES (10293, 18, 50.00, 12, 0.00);
INSERT INTO `order_items` VALUES (10293, 24, 3.60, 10, 0.00);
INSERT INTO `order_items` VALUES (10293, 63, 35.10, 5, 0.00);
INSERT INTO `order_items` VALUES (10293, 75, 6.20, 6, 0.00);
INSERT INTO `order_items` VALUES (10294, 1, 14.40, 18, 0.00);
INSERT INTO `order_items` VALUES (10294, 17, 31.20, 15, 0.00);
INSERT INTO `order_items` VALUES (10294, 43, 36.80, 15, 0.00);
INSERT INTO `order_items` VALUES (10294, 60, 27.20, 21, 0.00);
INSERT INTO `order_items` VALUES (10294, 75, 6.20, 6, 0.00);
INSERT INTO `order_items` VALUES (10295, 56, 30.40, 4, 0.00);
INSERT INTO `order_items` VALUES (10296, 11, 16.80, 12, 0.00);
INSERT INTO `order_items` VALUES (10296, 16, 13.90, 30, 0.00);
INSERT INTO `order_items` VALUES (10296, 69, 28.80, 15, 0.00);
INSERT INTO `order_items` VALUES (10297, 39, 14.40, 60, 0.00);
INSERT INTO `order_items` VALUES (10297, 72, 27.80, 20, 0.00);
INSERT INTO `order_items` VALUES (10298, 2, 15.20, 40, 0.00);
INSERT INTO `order_items` VALUES (10298, 36, 15.20, 40, 0.25);
INSERT INTO `order_items` VALUES (10298, 59, 44.00, 30, 0.25);
INSERT INTO `order_items` VALUES (10298, 62, 39.40, 15, 0.00);
INSERT INTO `order_items` VALUES (10299, 19, 7.30, 15, 0.00);
INSERT INTO `order_items` VALUES (10299, 70, 12.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10300, 66, 13.60, 30, 0.00);
INSERT INTO `order_items` VALUES (10300, 68, 10.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10301, 40, 14.70, 10, 0.00);
INSERT INTO `order_items` VALUES (10301, 56, 30.40, 20, 0.00);
INSERT INTO `order_items` VALUES (10302, 17, 31.20, 40, 0.00);
INSERT INTO `order_items` VALUES (10302, 28, 36.40, 28, 0.00);
INSERT INTO `order_items` VALUES (10302, 43, 36.80, 12, 0.00);
INSERT INTO `order_items` VALUES (10303, 40, 14.70, 40, 0.10);
INSERT INTO `order_items` VALUES (10303, 65, 16.80, 30, 0.10);
INSERT INTO `order_items` VALUES (10303, 68, 10.00, 15, 0.10);
INSERT INTO `order_items` VALUES (10304, 49, 16.00, 30, 0.00);
INSERT INTO `order_items` VALUES (10304, 59, 44.00, 10, 0.00);
INSERT INTO `order_items` VALUES (10304, 71, 17.20, 2, 0.00);
INSERT INTO `order_items` VALUES (10305, 18, 50.00, 25, 0.10);
INSERT INTO `order_items` VALUES (10305, 29, 99.00, 25, 0.10);
INSERT INTO `order_items` VALUES (10305, 39, 14.40, 30, 0.10);
INSERT INTO `order_items` VALUES (10306, 30, 20.70, 10, 0.00);
INSERT INTO `order_items` VALUES (10306, 53, 26.20, 10, 0.00);
INSERT INTO `order_items` VALUES (10306, 54, 5.90, 5, 0.00);
INSERT INTO `order_items` VALUES (10307, 62, 39.40, 10, 0.00);
INSERT INTO `order_items` VALUES (10307, 68, 10.00, 3, 0.00);
INSERT INTO `order_items` VALUES (10308, 69, 28.80, 1, 0.00);
INSERT INTO `order_items` VALUES (10308, 70, 12.00, 5, 0.00);
INSERT INTO `order_items` VALUES (10309, 4, 17.60, 20, 0.00);
INSERT INTO `order_items` VALUES (10309, 6, 20.00, 30, 0.00);
INSERT INTO `order_items` VALUES (10309, 42, 11.20, 2, 0.00);
INSERT INTO `order_items` VALUES (10309, 43, 36.80, 20, 0.00);
INSERT INTO `order_items` VALUES (10309, 71, 17.20, 3, 0.00);
INSERT INTO `order_items` VALUES (10310, 16, 13.90, 10, 0.00);
INSERT INTO `order_items` VALUES (10310, 62, 39.40, 5, 0.00);
INSERT INTO `order_items` VALUES (10311, 42, 11.20, 6, 0.00);
INSERT INTO `order_items` VALUES (10311, 69, 28.80, 7, 0.00);
INSERT INTO `order_items` VALUES (10312, 28, 36.40, 4, 0.00);
INSERT INTO `order_items` VALUES (10312, 43, 36.80, 24, 0.00);
INSERT INTO `order_items` VALUES (10312, 53, 26.20, 20, 0.00);
INSERT INTO `order_items` VALUES (10312, 75, 6.20, 10, 0.00);
INSERT INTO `order_items` VALUES (10313, 36, 15.20, 12, 0.00);
INSERT INTO `order_items` VALUES (10314, 32, 25.60, 40, 0.10);
INSERT INTO `order_items` VALUES (10314, 58, 10.60, 30, 0.10);
INSERT INTO `order_items` VALUES (10314, 62, 39.40, 25, 0.10);
INSERT INTO `order_items` VALUES (10315, 34, 11.20, 14, 0.00);
INSERT INTO `order_items` VALUES (10315, 70, 12.00, 30, 0.00);
INSERT INTO `order_items` VALUES (10316, 41, 7.70, 10, 0.00);
INSERT INTO `order_items` VALUES (10316, 62, 39.40, 70, 0.00);
INSERT INTO `order_items` VALUES (10317, 1, 14.40, 20, 0.00);
INSERT INTO `order_items` VALUES (10318, 41, 7.70, 20, 0.00);
INSERT INTO `order_items` VALUES (10318, 76, 14.40, 6, 0.00);
INSERT INTO `order_items` VALUES (10319, 17, 31.20, 8, 0.00);
INSERT INTO `order_items` VALUES (10319, 28, 36.40, 14, 0.00);
INSERT INTO `order_items` VALUES (10319, 76, 14.40, 30, 0.00);
INSERT INTO `order_items` VALUES (10320, 71, 17.20, 30, 0.00);
INSERT INTO `order_items` VALUES (10321, 35, 14.40, 10, 0.00);
INSERT INTO `order_items` VALUES (10322, 52, 5.60, 20, 0.00);
INSERT INTO `order_items` VALUES (10323, 15, 12.40, 5, 0.00);
INSERT INTO `order_items` VALUES (10323, 25, 11.20, 4, 0.00);
INSERT INTO `order_items` VALUES (10323, 39, 14.40, 4, 0.00);
INSERT INTO `order_items` VALUES (10324, 16, 13.90, 21, 0.15);
INSERT INTO `order_items` VALUES (10324, 35, 14.40, 70, 0.15);
INSERT INTO `order_items` VALUES (10324, 46, 9.60, 30, 0.00);
INSERT INTO `order_items` VALUES (10324, 59, 44.00, 40, 0.15);
INSERT INTO `order_items` VALUES (10324, 63, 35.10, 80, 0.15);
INSERT INTO `order_items` VALUES (10325, 6, 20.00, 6, 0.00);
INSERT INTO `order_items` VALUES (10325, 13, 4.80, 12, 0.00);
INSERT INTO `order_items` VALUES (10325, 14, 18.60, 9, 0.00);
INSERT INTO `order_items` VALUES (10325, 31, 10.00, 4, 0.00);
INSERT INTO `order_items` VALUES (10325, 72, 27.80, 40, 0.00);
INSERT INTO `order_items` VALUES (10326, 4, 17.60, 24, 0.00);
INSERT INTO `order_items` VALUES (10326, 57, 15.60, 16, 0.00);
INSERT INTO `order_items` VALUES (10326, 75, 6.20, 50, 0.00);
INSERT INTO `order_items` VALUES (10327, 2, 15.20, 25, 0.20);
INSERT INTO `order_items` VALUES (10327, 11, 16.80, 50, 0.20);
INSERT INTO `order_items` VALUES (10327, 30, 20.70, 35, 0.20);
INSERT INTO `order_items` VALUES (10327, 58, 10.60, 30, 0.20);
INSERT INTO `order_items` VALUES (10328, 59, 44.00, 9, 0.00);
INSERT INTO `order_items` VALUES (10328, 65, 16.80, 40, 0.00);
INSERT INTO `order_items` VALUES (10328, 68, 10.00, 10, 0.00);
INSERT INTO `order_items` VALUES (10329, 19, 7.30, 10, 0.05);
INSERT INTO `order_items` VALUES (10329, 30, 20.70, 8, 0.05);
INSERT INTO `order_items` VALUES (10329, 38, 210.80, 20, 0.05);
INSERT INTO `order_items` VALUES (10329, 56, 30.40, 12, 0.05);
INSERT INTO `order_items` VALUES (10330, 26, 24.90, 50, 0.15);
INSERT INTO `order_items` VALUES (10330, 72, 27.80, 25, 0.15);
INSERT INTO `order_items` VALUES (10331, 54, 5.90, 15, 0.00);
INSERT INTO `order_items` VALUES (10332, 18, 50.00, 40, 0.20);
INSERT INTO `order_items` VALUES (10332, 42, 11.20, 10, 0.20);
INSERT INTO `order_items` VALUES (10332, 47, 7.60, 16, 0.20);
INSERT INTO `order_items` VALUES (10333, 14, 18.60, 10, 0.00);
INSERT INTO `order_items` VALUES (10333, 21, 8.00, 10, 0.10);
INSERT INTO `order_items` VALUES (10333, 71, 17.20, 40, 0.10);
INSERT INTO `order_items` VALUES (10334, 52, 5.60, 8, 0.00);
INSERT INTO `order_items` VALUES (10334, 68, 10.00, 10, 0.00);
INSERT INTO `order_items` VALUES (10335, 2, 15.20, 7, 0.20);
INSERT INTO `order_items` VALUES (10335, 31, 10.00, 25, 0.20);
INSERT INTO `order_items` VALUES (10335, 32, 25.60, 6, 0.20);
INSERT INTO `order_items` VALUES (10335, 51, 42.40, 48, 0.20);
INSERT INTO `order_items` VALUES (10336, 4, 17.60, 18, 0.10);
INSERT INTO `order_items` VALUES (10337, 23, 7.20, 40, 0.00);
INSERT INTO `order_items` VALUES (10337, 26, 24.90, 24, 0.00);
INSERT INTO `order_items` VALUES (10337, 36, 15.20, 20, 0.00);
INSERT INTO `order_items` VALUES (10337, 37, 20.80, 28, 0.00);
INSERT INTO `order_items` VALUES (10337, 72, 27.80, 25, 0.00);
INSERT INTO `order_items` VALUES (10338, 17, 31.20, 20, 0.00);
INSERT INTO `order_items` VALUES (10338, 30, 20.70, 15, 0.00);
INSERT INTO `order_items` VALUES (10339, 4, 17.60, 10, 0.00);
INSERT INTO `order_items` VALUES (10339, 17, 31.20, 70, 0.05);
INSERT INTO `order_items` VALUES (10339, 62, 39.40, 28, 0.00);
INSERT INTO `order_items` VALUES (10340, 18, 50.00, 20, 0.05);
INSERT INTO `order_items` VALUES (10340, 41, 7.70, 12, 0.05);
INSERT INTO `order_items` VALUES (10340, 43, 36.80, 40, 0.05);
INSERT INTO `order_items` VALUES (10341, 33, 2.00, 8, 0.00);
INSERT INTO `order_items` VALUES (10341, 59, 44.00, 9, 0.15);
INSERT INTO `order_items` VALUES (10342, 2, 15.20, 24, 0.20);
INSERT INTO `order_items` VALUES (10342, 31, 10.00, 56, 0.20);
INSERT INTO `order_items` VALUES (10342, 36, 15.20, 40, 0.20);
INSERT INTO `order_items` VALUES (10342, 55, 19.20, 40, 0.20);
INSERT INTO `order_items` VALUES (10343, 64, 26.60, 50, 0.00);
INSERT INTO `order_items` VALUES (10343, 68, 10.00, 4, 0.05);
INSERT INTO `order_items` VALUES (10343, 76, 14.40, 15, 0.00);
INSERT INTO `order_items` VALUES (10344, 4, 17.60, 35, 0.00);
INSERT INTO `order_items` VALUES (10344, 8, 32.00, 70, 0.25);
INSERT INTO `order_items` VALUES (10345, 8, 32.00, 70, 0.00);
INSERT INTO `order_items` VALUES (10345, 19, 7.30, 80, 0.00);
INSERT INTO `order_items` VALUES (10345, 42, 11.20, 9, 0.00);
INSERT INTO `order_items` VALUES (10346, 17, 31.20, 36, 0.10);
INSERT INTO `order_items` VALUES (10346, 56, 30.40, 20, 0.00);
INSERT INTO `order_items` VALUES (10347, 25, 11.20, 10, 0.00);
INSERT INTO `order_items` VALUES (10347, 39, 14.40, 50, 0.15);
INSERT INTO `order_items` VALUES (10347, 40, 14.70, 4, 0.00);
INSERT INTO `order_items` VALUES (10347, 75, 6.20, 6, 0.15);
INSERT INTO `order_items` VALUES (10348, 1, 14.40, 15, 0.15);
INSERT INTO `order_items` VALUES (10348, 23, 7.20, 25, 0.00);
INSERT INTO `order_items` VALUES (10349, 54, 5.90, 24, 0.00);
INSERT INTO `order_items` VALUES (10350, 50, 13.00, 15, 0.10);
INSERT INTO `order_items` VALUES (10350, 69, 28.80, 18, 0.10);
INSERT INTO `order_items` VALUES (10351, 38, 210.80, 20, 0.05);
INSERT INTO `order_items` VALUES (10351, 41, 7.70, 13, 0.00);
INSERT INTO `order_items` VALUES (10351, 44, 15.50, 77, 0.05);
INSERT INTO `order_items` VALUES (10351, 65, 16.80, 10, 0.05);
INSERT INTO `order_items` VALUES (10352, 24, 3.60, 10, 0.00);
INSERT INTO `order_items` VALUES (10352, 54, 5.90, 20, 0.15);
INSERT INTO `order_items` VALUES (10353, 11, 16.80, 12, 0.20);
INSERT INTO `order_items` VALUES (10353, 38, 210.80, 50, 0.20);
INSERT INTO `order_items` VALUES (10354, 1, 14.40, 12, 0.00);
INSERT INTO `order_items` VALUES (10354, 29, 99.00, 4, 0.00);
INSERT INTO `order_items` VALUES (10355, 24, 3.60, 25, 0.00);
INSERT INTO `order_items` VALUES (10355, 57, 15.60, 25, 0.00);
INSERT INTO `order_items` VALUES (10356, 31, 10.00, 30, 0.00);
INSERT INTO `order_items` VALUES (10356, 55, 19.20, 12, 0.00);
INSERT INTO `order_items` VALUES (10356, 69, 28.80, 20, 0.00);
INSERT INTO `order_items` VALUES (10357, 10, 24.80, 30, 0.20);
INSERT INTO `order_items` VALUES (10357, 26, 24.90, 16, 0.00);
INSERT INTO `order_items` VALUES (10357, 60, 27.20, 8, 0.20);
INSERT INTO `order_items` VALUES (10358, 24, 3.60, 10, 0.05);
INSERT INTO `order_items` VALUES (10358, 34, 11.20, 10, 0.05);
INSERT INTO `order_items` VALUES (10358, 36, 15.20, 20, 0.05);
INSERT INTO `order_items` VALUES (10359, 16, 13.90, 56, 0.05);
INSERT INTO `order_items` VALUES (10359, 31, 10.00, 70, 0.05);
INSERT INTO `order_items` VALUES (10359, 60, 27.20, 80, 0.05);
INSERT INTO `order_items` VALUES (10360, 28, 36.40, 30, 0.00);
INSERT INTO `order_items` VALUES (10360, 29, 99.00, 35, 0.00);
INSERT INTO `order_items` VALUES (10360, 38, 210.80, 10, 0.00);
INSERT INTO `order_items` VALUES (10360, 49, 16.00, 35, 0.00);
INSERT INTO `order_items` VALUES (10360, 54, 5.90, 28, 0.00);
INSERT INTO `order_items` VALUES (10361, 39, 14.40, 54, 0.10);
INSERT INTO `order_items` VALUES (10361, 60, 27.20, 55, 0.10);
INSERT INTO `order_items` VALUES (10362, 25, 11.20, 50, 0.00);
INSERT INTO `order_items` VALUES (10362, 51, 42.40, 20, 0.00);
INSERT INTO `order_items` VALUES (10362, 54, 5.90, 24, 0.00);
INSERT INTO `order_items` VALUES (10363, 31, 10.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10363, 75, 6.20, 12, 0.00);
INSERT INTO `order_items` VALUES (10363, 76, 14.40, 12, 0.00);
INSERT INTO `order_items` VALUES (10364, 69, 28.80, 30, 0.00);
INSERT INTO `order_items` VALUES (10364, 71, 17.20, 5, 0.00);
INSERT INTO `order_items` VALUES (10365, 11, 16.80, 24, 0.00);
INSERT INTO `order_items` VALUES (10366, 65, 16.80, 5, 0.00);
INSERT INTO `order_items` VALUES (10366, 77, 10.40, 5, 0.00);
INSERT INTO `order_items` VALUES (10367, 34, 11.20, 36, 0.00);
INSERT INTO `order_items` VALUES (10367, 54, 5.90, 18, 0.00);
INSERT INTO `order_items` VALUES (10367, 65, 16.80, 15, 0.00);
INSERT INTO `order_items` VALUES (10367, 77, 10.40, 7, 0.00);
INSERT INTO `order_items` VALUES (10368, 21, 8.00, 5, 0.10);
INSERT INTO `order_items` VALUES (10368, 28, 36.40, 13, 0.10);
INSERT INTO `order_items` VALUES (10368, 57, 15.60, 25, 0.00);
INSERT INTO `order_items` VALUES (10368, 64, 26.60, 35, 0.10);
INSERT INTO `order_items` VALUES (10369, 29, 99.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10369, 56, 30.40, 18, 0.25);
INSERT INTO `order_items` VALUES (10370, 1, 14.40, 15, 0.15);
INSERT INTO `order_items` VALUES (10370, 64, 26.60, 30, 0.00);
INSERT INTO `order_items` VALUES (10370, 74, 8.00, 20, 0.15);
INSERT INTO `order_items` VALUES (10371, 36, 15.20, 6, 0.20);
INSERT INTO `order_items` VALUES (10372, 20, 64.80, 12, 0.25);
INSERT INTO `order_items` VALUES (10372, 38, 210.80, 40, 0.25);
INSERT INTO `order_items` VALUES (10372, 60, 27.20, 70, 0.25);
INSERT INTO `order_items` VALUES (10372, 72, 27.80, 42, 0.25);
INSERT INTO `order_items` VALUES (10373, 58, 10.60, 80, 0.20);
INSERT INTO `order_items` VALUES (10373, 71, 17.20, 50, 0.20);
INSERT INTO `order_items` VALUES (10374, 31, 10.00, 30, 0.00);
INSERT INTO `order_items` VALUES (10374, 58, 10.60, 15, 0.00);
INSERT INTO `order_items` VALUES (10375, 14, 18.60, 15, 0.00);
INSERT INTO `order_items` VALUES (10375, 54, 5.90, 10, 0.00);
INSERT INTO `order_items` VALUES (10376, 31, 10.00, 42, 0.05);
INSERT INTO `order_items` VALUES (10377, 28, 36.40, 20, 0.15);
INSERT INTO `order_items` VALUES (10377, 39, 14.40, 20, 0.15);
INSERT INTO `order_items` VALUES (10378, 71, 17.20, 6, 0.00);
INSERT INTO `order_items` VALUES (10379, 41, 7.70, 8, 0.10);
INSERT INTO `order_items` VALUES (10379, 63, 35.10, 16, 0.10);
INSERT INTO `order_items` VALUES (10379, 65, 16.80, 20, 0.10);
INSERT INTO `order_items` VALUES (10380, 30, 20.70, 18, 0.10);
INSERT INTO `order_items` VALUES (10380, 53, 26.20, 20, 0.10);
INSERT INTO `order_items` VALUES (10380, 60, 27.20, 6, 0.10);
INSERT INTO `order_items` VALUES (10380, 70, 12.00, 30, 0.00);
INSERT INTO `order_items` VALUES (10381, 74, 8.00, 14, 0.00);
INSERT INTO `order_items` VALUES (10382, 5, 17.00, 32, 0.00);
INSERT INTO `order_items` VALUES (10382, 18, 50.00, 9, 0.00);
INSERT INTO `order_items` VALUES (10382, 29, 99.00, 14, 0.00);
INSERT INTO `order_items` VALUES (10382, 33, 2.00, 60, 0.00);
INSERT INTO `order_items` VALUES (10382, 74, 8.00, 50, 0.00);
INSERT INTO `order_items` VALUES (10383, 13, 4.80, 20, 0.00);
INSERT INTO `order_items` VALUES (10383, 50, 13.00, 15, 0.00);
INSERT INTO `order_items` VALUES (10383, 56, 30.40, 20, 0.00);
INSERT INTO `order_items` VALUES (10384, 20, 64.80, 28, 0.00);
INSERT INTO `order_items` VALUES (10384, 60, 27.20, 15, 0.00);
INSERT INTO `order_items` VALUES (10385, 7, 24.00, 10, 0.20);
INSERT INTO `order_items` VALUES (10385, 60, 27.20, 20, 0.20);
INSERT INTO `order_items` VALUES (10385, 68, 10.00, 8, 0.20);
INSERT INTO `order_items` VALUES (10386, 24, 3.60, 15, 0.00);
INSERT INTO `order_items` VALUES (10386, 34, 11.20, 10, 0.00);
INSERT INTO `order_items` VALUES (10387, 24, 3.60, 15, 0.00);
INSERT INTO `order_items` VALUES (10387, 28, 36.40, 6, 0.00);
INSERT INTO `order_items` VALUES (10387, 59, 44.00, 12, 0.00);
INSERT INTO `order_items` VALUES (10387, 71, 17.20, 15, 0.00);
INSERT INTO `order_items` VALUES (10388, 45, 7.60, 15, 0.20);
INSERT INTO `order_items` VALUES (10388, 52, 5.60, 20, 0.20);
INSERT INTO `order_items` VALUES (10388, 53, 26.20, 40, 0.00);
INSERT INTO `order_items` VALUES (10389, 10, 24.80, 16, 0.00);
INSERT INTO `order_items` VALUES (10389, 55, 19.20, 15, 0.00);
INSERT INTO `order_items` VALUES (10389, 62, 39.40, 20, 0.00);
INSERT INTO `order_items` VALUES (10389, 70, 12.00, 30, 0.00);
INSERT INTO `order_items` VALUES (10390, 31, 10.00, 60, 0.10);
INSERT INTO `order_items` VALUES (10390, 35, 14.40, 40, 0.10);
INSERT INTO `order_items` VALUES (10390, 46, 9.60, 45, 0.00);
INSERT INTO `order_items` VALUES (10390, 72, 27.80, 24, 0.10);
INSERT INTO `order_items` VALUES (10391, 13, 4.80, 18, 0.00);
INSERT INTO `order_items` VALUES (10392, 69, 28.80, 50, 0.00);
INSERT INTO `order_items` VALUES (10393, 2, 15.20, 25, 0.25);
INSERT INTO `order_items` VALUES (10393, 14, 18.60, 42, 0.25);
INSERT INTO `order_items` VALUES (10393, 25, 11.20, 7, 0.25);
INSERT INTO `order_items` VALUES (10393, 26, 24.90, 70, 0.25);
INSERT INTO `order_items` VALUES (10393, 31, 10.00, 32, 0.00);
INSERT INTO `order_items` VALUES (10394, 13, 4.80, 10, 0.00);
INSERT INTO `order_items` VALUES (10394, 62, 39.40, 10, 0.00);
INSERT INTO `order_items` VALUES (10395, 46, 9.60, 28, 0.10);
INSERT INTO `order_items` VALUES (10395, 53, 26.20, 70, 0.10);
INSERT INTO `order_items` VALUES (10395, 69, 28.80, 8, 0.00);
INSERT INTO `order_items` VALUES (10396, 23, 7.20, 40, 0.00);
INSERT INTO `order_items` VALUES (10396, 71, 17.20, 60, 0.00);
INSERT INTO `order_items` VALUES (10396, 72, 27.80, 21, 0.00);
INSERT INTO `order_items` VALUES (10397, 21, 8.00, 10, 0.15);
INSERT INTO `order_items` VALUES (10397, 51, 42.40, 18, 0.15);
INSERT INTO `order_items` VALUES (10398, 35, 14.40, 30, 0.00);
INSERT INTO `order_items` VALUES (10398, 55, 19.20, 120, 0.10);
INSERT INTO `order_items` VALUES (10399, 68, 10.00, 60, 0.00);
INSERT INTO `order_items` VALUES (10399, 71, 17.20, 30, 0.00);
INSERT INTO `order_items` VALUES (10399, 76, 14.40, 35, 0.00);
INSERT INTO `order_items` VALUES (10399, 77, 10.40, 14, 0.00);
INSERT INTO `order_items` VALUES (10400, 29, 99.00, 21, 0.00);
INSERT INTO `order_items` VALUES (10400, 35, 14.40, 35, 0.00);
INSERT INTO `order_items` VALUES (10400, 49, 16.00, 30, 0.00);
INSERT INTO `order_items` VALUES (10401, 30, 20.70, 18, 0.00);
INSERT INTO `order_items` VALUES (10401, 56, 30.40, 70, 0.00);
INSERT INTO `order_items` VALUES (10401, 65, 16.80, 20, 0.00);
INSERT INTO `order_items` VALUES (10401, 71, 17.20, 60, 0.00);
INSERT INTO `order_items` VALUES (10402, 23, 7.20, 60, 0.00);
INSERT INTO `order_items` VALUES (10402, 63, 35.10, 65, 0.00);
INSERT INTO `order_items` VALUES (10403, 16, 13.90, 21, 0.15);
INSERT INTO `order_items` VALUES (10403, 48, 10.20, 70, 0.15);
INSERT INTO `order_items` VALUES (10404, 26, 24.90, 30, 0.05);
INSERT INTO `order_items` VALUES (10404, 42, 11.20, 40, 0.05);
INSERT INTO `order_items` VALUES (10404, 49, 16.00, 30, 0.05);
INSERT INTO `order_items` VALUES (10405, 3, 8.00, 50, 0.00);
INSERT INTO `order_items` VALUES (10406, 1, 14.40, 10, 0.00);
INSERT INTO `order_items` VALUES (10406, 21, 8.00, 30, 0.10);
INSERT INTO `order_items` VALUES (10406, 28, 36.40, 42, 0.10);
INSERT INTO `order_items` VALUES (10406, 36, 15.20, 5, 0.10);
INSERT INTO `order_items` VALUES (10406, 40, 14.70, 2, 0.10);
INSERT INTO `order_items` VALUES (10407, 11, 16.80, 30, 0.00);
INSERT INTO `order_items` VALUES (10407, 69, 28.80, 15, 0.00);
INSERT INTO `order_items` VALUES (10407, 71, 17.20, 15, 0.00);
INSERT INTO `order_items` VALUES (10408, 37, 20.80, 10, 0.00);
INSERT INTO `order_items` VALUES (10408, 54, 5.90, 6, 0.00);
INSERT INTO `order_items` VALUES (10408, 62, 39.40, 35, 0.00);
INSERT INTO `order_items` VALUES (10409, 14, 18.60, 12, 0.00);
INSERT INTO `order_items` VALUES (10409, 21, 8.00, 12, 0.00);
INSERT INTO `order_items` VALUES (10410, 33, 2.00, 49, 0.00);
INSERT INTO `order_items` VALUES (10410, 59, 44.00, 16, 0.00);
INSERT INTO `order_items` VALUES (10411, 41, 7.70, 25, 0.20);
INSERT INTO `order_items` VALUES (10411, 44, 15.50, 40, 0.20);
INSERT INTO `order_items` VALUES (10411, 59, 44.00, 9, 0.20);
INSERT INTO `order_items` VALUES (10412, 14, 18.60, 20, 0.10);
INSERT INTO `order_items` VALUES (10413, 1, 14.40, 24, 0.00);
INSERT INTO `order_items` VALUES (10413, 62, 39.40, 40, 0.00);
INSERT INTO `order_items` VALUES (10413, 76, 14.40, 14, 0.00);
INSERT INTO `order_items` VALUES (10414, 19, 7.30, 18, 0.05);
INSERT INTO `order_items` VALUES (10414, 33, 2.00, 50, 0.00);
INSERT INTO `order_items` VALUES (10415, 17, 31.20, 2, 0.00);
INSERT INTO `order_items` VALUES (10415, 33, 2.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10416, 19, 7.30, 20, 0.00);
INSERT INTO `order_items` VALUES (10416, 53, 26.20, 10, 0.00);
INSERT INTO `order_items` VALUES (10416, 57, 15.60, 20, 0.00);
INSERT INTO `order_items` VALUES (10417, 38, 210.80, 50, 0.00);
INSERT INTO `order_items` VALUES (10417, 46, 9.60, 2, 0.25);
INSERT INTO `order_items` VALUES (10417, 68, 10.00, 36, 0.25);
INSERT INTO `order_items` VALUES (10417, 77, 10.40, 35, 0.00);
INSERT INTO `order_items` VALUES (10418, 2, 15.20, 60, 0.00);
INSERT INTO `order_items` VALUES (10418, 47, 7.60, 55, 0.00);
INSERT INTO `order_items` VALUES (10418, 61, 22.80, 16, 0.00);
INSERT INTO `order_items` VALUES (10418, 74, 8.00, 15, 0.00);
INSERT INTO `order_items` VALUES (10419, 60, 27.20, 60, 0.05);
INSERT INTO `order_items` VALUES (10419, 69, 28.80, 20, 0.05);
INSERT INTO `order_items` VALUES (10420, 9, 77.60, 20, 0.10);
INSERT INTO `order_items` VALUES (10420, 13, 4.80, 2, 0.10);
INSERT INTO `order_items` VALUES (10420, 70, 12.00, 8, 0.10);
INSERT INTO `order_items` VALUES (10420, 73, 12.00, 20, 0.10);
INSERT INTO `order_items` VALUES (10421, 19, 7.30, 4, 0.15);
INSERT INTO `order_items` VALUES (10421, 26, 24.90, 30, 0.00);
INSERT INTO `order_items` VALUES (10421, 53, 26.20, 15, 0.15);
INSERT INTO `order_items` VALUES (10421, 77, 10.40, 10, 0.15);
INSERT INTO `order_items` VALUES (10422, 26, 24.90, 2, 0.00);
INSERT INTO `order_items` VALUES (10423, 31, 10.00, 14, 0.00);
INSERT INTO `order_items` VALUES (10423, 59, 44.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10424, 35, 14.40, 60, 0.20);
INSERT INTO `order_items` VALUES (10424, 38, 210.80, 49, 0.20);
INSERT INTO `order_items` VALUES (10424, 68, 10.00, 30, 0.20);
INSERT INTO `order_items` VALUES (10425, 55, 19.20, 10, 0.25);
INSERT INTO `order_items` VALUES (10425, 76, 14.40, 20, 0.25);
INSERT INTO `order_items` VALUES (10426, 56, 30.40, 5, 0.00);
INSERT INTO `order_items` VALUES (10426, 64, 26.60, 7, 0.00);
INSERT INTO `order_items` VALUES (10427, 14, 18.60, 35, 0.00);
INSERT INTO `order_items` VALUES (10428, 46, 9.60, 20, 0.00);
INSERT INTO `order_items` VALUES (10429, 50, 13.00, 40, 0.00);
INSERT INTO `order_items` VALUES (10429, 63, 35.10, 35, 0.25);
INSERT INTO `order_items` VALUES (10430, 17, 31.20, 45, 0.20);
INSERT INTO `order_items` VALUES (10430, 21, 8.00, 50, 0.00);
INSERT INTO `order_items` VALUES (10430, 56, 30.40, 30, 0.00);
INSERT INTO `order_items` VALUES (10430, 59, 44.00, 70, 0.20);
INSERT INTO `order_items` VALUES (10431, 17, 31.20, 50, 0.25);
INSERT INTO `order_items` VALUES (10431, 40, 14.70, 50, 0.25);
INSERT INTO `order_items` VALUES (10431, 47, 7.60, 30, 0.25);
INSERT INTO `order_items` VALUES (10432, 26, 24.90, 10, 0.00);
INSERT INTO `order_items` VALUES (10432, 54, 5.90, 40, 0.00);
INSERT INTO `order_items` VALUES (10433, 56, 30.40, 28, 0.00);
INSERT INTO `order_items` VALUES (10434, 11, 16.80, 6, 0.00);
INSERT INTO `order_items` VALUES (10434, 76, 14.40, 18, 0.15);
INSERT INTO `order_items` VALUES (10435, 2, 15.20, 10, 0.00);
INSERT INTO `order_items` VALUES (10435, 22, 16.80, 12, 0.00);
INSERT INTO `order_items` VALUES (10435, 72, 27.80, 10, 0.00);
INSERT INTO `order_items` VALUES (10436, 46, 9.60, 5, 0.00);
INSERT INTO `order_items` VALUES (10436, 56, 30.40, 40, 0.10);
INSERT INTO `order_items` VALUES (10436, 64, 26.60, 30, 0.10);
INSERT INTO `order_items` VALUES (10436, 75, 6.20, 24, 0.10);
INSERT INTO `order_items` VALUES (10437, 53, 26.20, 15, 0.00);
INSERT INTO `order_items` VALUES (10438, 19, 7.30, 15, 0.20);
INSERT INTO `order_items` VALUES (10438, 34, 11.20, 20, 0.20);
INSERT INTO `order_items` VALUES (10438, 57, 15.60, 15, 0.20);
INSERT INTO `order_items` VALUES (10439, 12, 30.40, 15, 0.00);
INSERT INTO `order_items` VALUES (10439, 16, 13.90, 16, 0.00);
INSERT INTO `order_items` VALUES (10439, 64, 26.60, 6, 0.00);
INSERT INTO `order_items` VALUES (10439, 74, 8.00, 30, 0.00);
INSERT INTO `order_items` VALUES (10440, 2, 15.20, 45, 0.15);
INSERT INTO `order_items` VALUES (10440, 16, 13.90, 49, 0.15);
INSERT INTO `order_items` VALUES (10440, 29, 99.00, 24, 0.15);
INSERT INTO `order_items` VALUES (10440, 61, 22.80, 90, 0.15);
INSERT INTO `order_items` VALUES (10441, 27, 35.10, 50, 0.00);
INSERT INTO `order_items` VALUES (10442, 11, 16.80, 30, 0.00);
INSERT INTO `order_items` VALUES (10442, 54, 5.90, 80, 0.00);
INSERT INTO `order_items` VALUES (10442, 66, 13.60, 60, 0.00);
INSERT INTO `order_items` VALUES (10443, 11, 16.80, 6, 0.20);
INSERT INTO `order_items` VALUES (10443, 28, 36.40, 12, 0.00);
INSERT INTO `order_items` VALUES (10444, 17, 31.20, 10, 0.00);
INSERT INTO `order_items` VALUES (10444, 26, 24.90, 15, 0.00);
INSERT INTO `order_items` VALUES (10444, 35, 14.40, 8, 0.00);
INSERT INTO `order_items` VALUES (10444, 41, 7.70, 30, 0.00);
INSERT INTO `order_items` VALUES (10445, 39, 14.40, 6, 0.00);
INSERT INTO `order_items` VALUES (10445, 54, 5.90, 15, 0.00);
INSERT INTO `order_items` VALUES (10446, 19, 7.30, 12, 0.10);
INSERT INTO `order_items` VALUES (10446, 24, 3.60, 20, 0.10);
INSERT INTO `order_items` VALUES (10446, 31, 10.00, 3, 0.10);
INSERT INTO `order_items` VALUES (10446, 52, 5.60, 15, 0.10);
INSERT INTO `order_items` VALUES (10447, 19, 7.30, 40, 0.00);
INSERT INTO `order_items` VALUES (10447, 65, 16.80, 35, 0.00);
INSERT INTO `order_items` VALUES (10447, 71, 17.20, 2, 0.00);
INSERT INTO `order_items` VALUES (10448, 26, 24.90, 6, 0.00);
INSERT INTO `order_items` VALUES (10448, 40, 14.70, 20, 0.00);
INSERT INTO `order_items` VALUES (10449, 10, 24.80, 14, 0.00);
INSERT INTO `order_items` VALUES (10449, 52, 5.60, 20, 0.00);
INSERT INTO `order_items` VALUES (10449, 62, 39.40, 35, 0.00);
INSERT INTO `order_items` VALUES (10450, 10, 24.80, 20, 0.20);
INSERT INTO `order_items` VALUES (10450, 54, 5.90, 6, 0.20);
INSERT INTO `order_items` VALUES (10451, 55, 19.20, 120, 0.10);
INSERT INTO `order_items` VALUES (10451, 64, 26.60, 35, 0.10);
INSERT INTO `order_items` VALUES (10451, 65, 16.80, 28, 0.10);
INSERT INTO `order_items` VALUES (10451, 77, 10.40, 55, 0.10);
INSERT INTO `order_items` VALUES (10452, 28, 36.40, 15, 0.00);
INSERT INTO `order_items` VALUES (10452, 44, 15.50, 100, 0.05);
INSERT INTO `order_items` VALUES (10453, 48, 10.20, 15, 0.10);
INSERT INTO `order_items` VALUES (10453, 70, 12.00, 25, 0.10);
INSERT INTO `order_items` VALUES (10454, 16, 13.90, 20, 0.20);
INSERT INTO `order_items` VALUES (10454, 33, 2.00, 20, 0.20);
INSERT INTO `order_items` VALUES (10454, 46, 9.60, 10, 0.20);
INSERT INTO `order_items` VALUES (10455, 39, 14.40, 20, 0.00);
INSERT INTO `order_items` VALUES (10455, 53, 26.20, 50, 0.00);
INSERT INTO `order_items` VALUES (10455, 61, 22.80, 25, 0.00);
INSERT INTO `order_items` VALUES (10455, 71, 17.20, 30, 0.00);
INSERT INTO `order_items` VALUES (10456, 21, 8.00, 40, 0.15);
INSERT INTO `order_items` VALUES (10456, 49, 16.00, 21, 0.15);
INSERT INTO `order_items` VALUES (10457, 59, 44.00, 36, 0.00);
INSERT INTO `order_items` VALUES (10458, 26, 24.90, 30, 0.00);
INSERT INTO `order_items` VALUES (10458, 28, 36.40, 30, 0.00);
INSERT INTO `order_items` VALUES (10458, 43, 36.80, 20, 0.00);
INSERT INTO `order_items` VALUES (10458, 56, 30.40, 15, 0.00);
INSERT INTO `order_items` VALUES (10458, 71, 17.20, 50, 0.00);
INSERT INTO `order_items` VALUES (10459, 7, 24.00, 16, 0.05);
INSERT INTO `order_items` VALUES (10459, 46, 9.60, 20, 0.05);
INSERT INTO `order_items` VALUES (10459, 72, 27.80, 40, 0.00);
INSERT INTO `order_items` VALUES (10460, 68, 10.00, 21, 0.25);
INSERT INTO `order_items` VALUES (10460, 75, 6.20, 4, 0.25);
INSERT INTO `order_items` VALUES (10461, 21, 8.00, 40, 0.25);
INSERT INTO `order_items` VALUES (10461, 30, 20.70, 28, 0.25);
INSERT INTO `order_items` VALUES (10461, 55, 19.20, 60, 0.25);
INSERT INTO `order_items` VALUES (10462, 13, 4.80, 1, 0.00);
INSERT INTO `order_items` VALUES (10462, 23, 7.20, 21, 0.00);
INSERT INTO `order_items` VALUES (10463, 19, 7.30, 21, 0.00);
INSERT INTO `order_items` VALUES (10463, 42, 11.20, 50, 0.00);
INSERT INTO `order_items` VALUES (10464, 4, 17.60, 16, 0.20);
INSERT INTO `order_items` VALUES (10464, 43, 36.80, 3, 0.00);
INSERT INTO `order_items` VALUES (10464, 56, 30.40, 30, 0.20);
INSERT INTO `order_items` VALUES (10464, 60, 27.20, 20, 0.00);
INSERT INTO `order_items` VALUES (10465, 24, 3.60, 25, 0.00);
INSERT INTO `order_items` VALUES (10465, 29, 99.00, 18, 0.10);
INSERT INTO `order_items` VALUES (10465, 40, 14.70, 20, 0.00);
INSERT INTO `order_items` VALUES (10465, 45, 7.60, 30, 0.10);
INSERT INTO `order_items` VALUES (10465, 50, 13.00, 25, 0.00);
INSERT INTO `order_items` VALUES (10466, 11, 16.80, 10, 0.00);
INSERT INTO `order_items` VALUES (10466, 46, 9.60, 5, 0.00);
INSERT INTO `order_items` VALUES (10467, 24, 3.60, 28, 0.00);
INSERT INTO `order_items` VALUES (10467, 25, 11.20, 12, 0.00);
INSERT INTO `order_items` VALUES (10468, 30, 20.70, 8, 0.00);
INSERT INTO `order_items` VALUES (10468, 43, 36.80, 15, 0.00);
INSERT INTO `order_items` VALUES (10469, 2, 15.20, 40, 0.15);
INSERT INTO `order_items` VALUES (10469, 16, 13.90, 35, 0.15);
INSERT INTO `order_items` VALUES (10469, 44, 15.50, 2, 0.15);
INSERT INTO `order_items` VALUES (10470, 18, 50.00, 30, 0.00);
INSERT INTO `order_items` VALUES (10470, 23, 7.20, 15, 0.00);
INSERT INTO `order_items` VALUES (10470, 64, 26.60, 8, 0.00);
INSERT INTO `order_items` VALUES (10471, 7, 24.00, 30, 0.00);
INSERT INTO `order_items` VALUES (10471, 56, 30.40, 20, 0.00);
INSERT INTO `order_items` VALUES (10472, 24, 3.60, 80, 0.05);
INSERT INTO `order_items` VALUES (10472, 51, 42.40, 18, 0.00);
INSERT INTO `order_items` VALUES (10473, 33, 2.00, 12, 0.00);
INSERT INTO `order_items` VALUES (10473, 71, 17.20, 12, 0.00);
INSERT INTO `order_items` VALUES (10474, 14, 18.60, 12, 0.00);
INSERT INTO `order_items` VALUES (10474, 28, 36.40, 18, 0.00);
INSERT INTO `order_items` VALUES (10474, 40, 14.70, 21, 0.00);
INSERT INTO `order_items` VALUES (10474, 75, 6.20, 10, 0.00);
INSERT INTO `order_items` VALUES (10475, 31, 10.00, 35, 0.15);
INSERT INTO `order_items` VALUES (10475, 66, 13.60, 60, 0.15);
INSERT INTO `order_items` VALUES (10475, 76, 14.40, 42, 0.15);
INSERT INTO `order_items` VALUES (10476, 55, 19.20, 2, 0.05);
INSERT INTO `order_items` VALUES (10476, 70, 12.00, 12, 0.00);
INSERT INTO `order_items` VALUES (10477, 1, 14.40, 15, 0.00);
INSERT INTO `order_items` VALUES (10477, 21, 8.00, 21, 0.25);
INSERT INTO `order_items` VALUES (10477, 39, 14.40, 20, 0.25);
INSERT INTO `order_items` VALUES (10478, 10, 24.80, 20, 0.05);
INSERT INTO `order_items` VALUES (10479, 38, 210.80, 30, 0.00);
INSERT INTO `order_items` VALUES (10479, 53, 26.20, 28, 0.00);
INSERT INTO `order_items` VALUES (10479, 59, 44.00, 60, 0.00);
INSERT INTO `order_items` VALUES (10479, 64, 26.60, 30, 0.00);
INSERT INTO `order_items` VALUES (10480, 47, 7.60, 30, 0.00);
INSERT INTO `order_items` VALUES (10480, 59, 44.00, 12, 0.00);
INSERT INTO `order_items` VALUES (10481, 49, 16.00, 24, 0.00);
INSERT INTO `order_items` VALUES (10481, 60, 27.20, 40, 0.00);
INSERT INTO `order_items` VALUES (10482, 40, 14.70, 10, 0.00);
INSERT INTO `order_items` VALUES (10483, 34, 11.20, 35, 0.05);
INSERT INTO `order_items` VALUES (10483, 77, 10.40, 30, 0.05);
INSERT INTO `order_items` VALUES (10484, 21, 8.00, 14, 0.00);
INSERT INTO `order_items` VALUES (10484, 40, 14.70, 10, 0.00);
INSERT INTO `order_items` VALUES (10484, 51, 42.40, 3, 0.00);
INSERT INTO `order_items` VALUES (10485, 2, 15.20, 20, 0.10);
INSERT INTO `order_items` VALUES (10485, 3, 8.00, 20, 0.10);
INSERT INTO `order_items` VALUES (10485, 55, 19.20, 30, 0.10);
INSERT INTO `order_items` VALUES (10485, 70, 12.00, 60, 0.10);
INSERT INTO `order_items` VALUES (10486, 11, 16.80, 5, 0.00);
INSERT INTO `order_items` VALUES (10486, 51, 42.40, 25, 0.00);
INSERT INTO `order_items` VALUES (10486, 74, 8.00, 16, 0.00);
INSERT INTO `order_items` VALUES (10487, 19, 7.30, 5, 0.00);
INSERT INTO `order_items` VALUES (10487, 26, 24.90, 30, 0.00);
INSERT INTO `order_items` VALUES (10487, 54, 5.90, 24, 0.25);
INSERT INTO `order_items` VALUES (10488, 59, 44.00, 30, 0.00);
INSERT INTO `order_items` VALUES (10488, 73, 12.00, 20, 0.20);
INSERT INTO `order_items` VALUES (10489, 11, 16.80, 15, 0.25);
INSERT INTO `order_items` VALUES (10489, 16, 13.90, 18, 0.00);
INSERT INTO `order_items` VALUES (10490, 59, 44.00, 60, 0.00);
INSERT INTO `order_items` VALUES (10490, 68, 10.00, 30, 0.00);
INSERT INTO `order_items` VALUES (10490, 75, 6.20, 36, 0.00);
INSERT INTO `order_items` VALUES (10491, 44, 15.50, 15, 0.15);
INSERT INTO `order_items` VALUES (10491, 77, 10.40, 7, 0.15);
INSERT INTO `order_items` VALUES (10492, 25, 11.20, 60, 0.05);
INSERT INTO `order_items` VALUES (10492, 42, 11.20, 20, 0.05);
INSERT INTO `order_items` VALUES (10493, 65, 16.80, 15, 0.10);
INSERT INTO `order_items` VALUES (10493, 66, 13.60, 10, 0.10);
INSERT INTO `order_items` VALUES (10493, 69, 28.80, 10, 0.10);
INSERT INTO `order_items` VALUES (10494, 56, 30.40, 30, 0.00);
INSERT INTO `order_items` VALUES (10495, 23, 7.20, 10, 0.00);
INSERT INTO `order_items` VALUES (10495, 41, 7.70, 20, 0.00);
INSERT INTO `order_items` VALUES (10495, 77, 10.40, 5, 0.00);
INSERT INTO `order_items` VALUES (10496, 31, 10.00, 20, 0.05);
INSERT INTO `order_items` VALUES (10497, 56, 30.40, 14, 0.00);
INSERT INTO `order_items` VALUES (10497, 72, 27.80, 25, 0.00);
INSERT INTO `order_items` VALUES (10497, 77, 10.40, 25, 0.00);
INSERT INTO `order_items` VALUES (10498, 24, 4.50, 14, 0.00);
INSERT INTO `order_items` VALUES (10498, 40, 18.40, 5, 0.00);
INSERT INTO `order_items` VALUES (10498, 42, 14.00, 30, 0.00);
INSERT INTO `order_items` VALUES (10499, 28, 45.60, 20, 0.00);
INSERT INTO `order_items` VALUES (10499, 49, 20.00, 25, 0.00);
INSERT INTO `order_items` VALUES (10500, 15, 15.50, 12, 0.05);
INSERT INTO `order_items` VALUES (10500, 28, 45.60, 8, 0.05);
INSERT INTO `order_items` VALUES (10501, 54, 7.45, 20, 0.00);
INSERT INTO `order_items` VALUES (10502, 45, 9.50, 21, 0.00);
INSERT INTO `order_items` VALUES (10502, 53, 32.80, 6, 0.00);
INSERT INTO `order_items` VALUES (10502, 67, 14.00, 30, 0.00);
INSERT INTO `order_items` VALUES (10503, 14, 23.25, 70, 0.00);
INSERT INTO `order_items` VALUES (10503, 65, 21.05, 20, 0.00);
INSERT INTO `order_items` VALUES (10504, 2, 19.00, 12, 0.00);
INSERT INTO `order_items` VALUES (10504, 21, 10.00, 12, 0.00);
INSERT INTO `order_items` VALUES (10504, 53, 32.80, 10, 0.00);
INSERT INTO `order_items` VALUES (10504, 61, 28.50, 25, 0.00);
INSERT INTO `order_items` VALUES (10505, 62, 49.30, 3, 0.00);
INSERT INTO `order_items` VALUES (10506, 25, 14.00, 18, 0.10);
INSERT INTO `order_items` VALUES (10506, 70, 15.00, 14, 0.10);
INSERT INTO `order_items` VALUES (10507, 43, 46.00, 15, 0.15);
INSERT INTO `order_items` VALUES (10507, 48, 12.75, 15, 0.15);
INSERT INTO `order_items` VALUES (10508, 13, 6.00, 10, 0.00);
INSERT INTO `order_items` VALUES (10508, 39, 18.00, 10, 0.00);
INSERT INTO `order_items` VALUES (10509, 28, 45.60, 3, 0.00);
INSERT INTO `order_items` VALUES (10510, 29, 123.79, 36, 0.00);
INSERT INTO `order_items` VALUES (10510, 75, 7.75, 36, 0.10);
INSERT INTO `order_items` VALUES (10511, 4, 22.00, 50, 0.15);
INSERT INTO `order_items` VALUES (10511, 7, 30.00, 50, 0.15);
INSERT INTO `order_items` VALUES (10511, 8, 40.00, 10, 0.15);
INSERT INTO `order_items` VALUES (10512, 24, 4.50, 10, 0.15);
INSERT INTO `order_items` VALUES (10512, 46, 12.00, 9, 0.15);
INSERT INTO `order_items` VALUES (10512, 47, 9.50, 6, 0.15);
INSERT INTO `order_items` VALUES (10512, 60, 34.00, 12, 0.15);
INSERT INTO `order_items` VALUES (10513, 21, 10.00, 40, 0.20);
INSERT INTO `order_items` VALUES (10513, 32, 32.00, 50, 0.20);
INSERT INTO `order_items` VALUES (10513, 61, 28.50, 15, 0.20);
INSERT INTO `order_items` VALUES (10514, 20, 81.00, 39, 0.00);
INSERT INTO `order_items` VALUES (10514, 28, 45.60, 35, 0.00);
INSERT INTO `order_items` VALUES (10514, 56, 38.00, 70, 0.00);
INSERT INTO `order_items` VALUES (10514, 65, 21.05, 39, 0.00);
INSERT INTO `order_items` VALUES (10514, 75, 7.75, 50, 0.00);
INSERT INTO `order_items` VALUES (10515, 9, 97.00, 16, 0.15);
INSERT INTO `order_items` VALUES (10515, 16, 17.45, 50, 0.00);
INSERT INTO `order_items` VALUES (10515, 27, 43.90, 120, 0.00);
INSERT INTO `order_items` VALUES (10515, 33, 2.50, 16, 0.15);
INSERT INTO `order_items` VALUES (10515, 60, 34.00, 84, 0.15);
INSERT INTO `order_items` VALUES (10516, 18, 62.50, 25, 0.10);
INSERT INTO `order_items` VALUES (10516, 41, 9.65, 80, 0.10);
INSERT INTO `order_items` VALUES (10516, 42, 14.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10517, 52, 7.00, 6, 0.00);
INSERT INTO `order_items` VALUES (10517, 59, 55.00, 4, 0.00);
INSERT INTO `order_items` VALUES (10517, 70, 15.00, 6, 0.00);
INSERT INTO `order_items` VALUES (10518, 24, 4.50, 5, 0.00);
INSERT INTO `order_items` VALUES (10518, 38, 263.50, 15, 0.00);
INSERT INTO `order_items` VALUES (10518, 44, 19.45, 9, 0.00);
INSERT INTO `order_items` VALUES (10519, 10, 31.00, 16, 0.05);
INSERT INTO `order_items` VALUES (10519, 56, 38.00, 40, 0.00);
INSERT INTO `order_items` VALUES (10519, 60, 34.00, 10, 0.05);
INSERT INTO `order_items` VALUES (10520, 24, 4.50, 8, 0.00);
INSERT INTO `order_items` VALUES (10520, 53, 32.80, 5, 0.00);
INSERT INTO `order_items` VALUES (10521, 35, 18.00, 3, 0.00);
INSERT INTO `order_items` VALUES (10521, 41, 9.65, 10, 0.00);
INSERT INTO `order_items` VALUES (10521, 68, 12.50, 6, 0.00);
INSERT INTO `order_items` VALUES (10522, 1, 18.00, 40, 0.20);
INSERT INTO `order_items` VALUES (10522, 8, 40.00, 24, 0.00);
INSERT INTO `order_items` VALUES (10522, 30, 25.89, 20, 0.20);
INSERT INTO `order_items` VALUES (10522, 40, 18.40, 25, 0.20);
INSERT INTO `order_items` VALUES (10523, 17, 39.00, 25, 0.10);
INSERT INTO `order_items` VALUES (10523, 20, 81.00, 15, 0.10);
INSERT INTO `order_items` VALUES (10523, 37, 26.00, 18, 0.10);
INSERT INTO `order_items` VALUES (10523, 41, 9.65, 6, 0.10);
INSERT INTO `order_items` VALUES (10524, 10, 31.00, 2, 0.00);
INSERT INTO `order_items` VALUES (10524, 30, 25.89, 10, 0.00);
INSERT INTO `order_items` VALUES (10524, 43, 46.00, 60, 0.00);
INSERT INTO `order_items` VALUES (10524, 54, 7.45, 15, 0.00);
INSERT INTO `order_items` VALUES (10525, 36, 19.00, 30, 0.00);
INSERT INTO `order_items` VALUES (10525, 40, 18.40, 15, 0.10);
INSERT INTO `order_items` VALUES (10526, 1, 18.00, 8, 0.15);
INSERT INTO `order_items` VALUES (10526, 13, 6.00, 10, 0.00);
INSERT INTO `order_items` VALUES (10526, 56, 38.00, 30, 0.15);
INSERT INTO `order_items` VALUES (10527, 4, 22.00, 50, 0.10);
INSERT INTO `order_items` VALUES (10527, 36, 19.00, 30, 0.10);
INSERT INTO `order_items` VALUES (10528, 11, 21.00, 3, 0.00);
INSERT INTO `order_items` VALUES (10528, 33, 2.50, 8, 0.20);
INSERT INTO `order_items` VALUES (10528, 72, 34.80, 9, 0.00);
INSERT INTO `order_items` VALUES (10529, 55, 24.00, 14, 0.00);
INSERT INTO `order_items` VALUES (10529, 68, 12.50, 20, 0.00);
INSERT INTO `order_items` VALUES (10529, 69, 36.00, 10, 0.00);
INSERT INTO `order_items` VALUES (10530, 17, 39.00, 40, 0.00);
INSERT INTO `order_items` VALUES (10530, 43, 46.00, 25, 0.00);
INSERT INTO `order_items` VALUES (10530, 61, 28.50, 20, 0.00);
INSERT INTO `order_items` VALUES (10530, 76, 18.00, 50, 0.00);
INSERT INTO `order_items` VALUES (10531, 59, 55.00, 2, 0.00);
INSERT INTO `order_items` VALUES (10532, 30, 25.89, 15, 0.00);
INSERT INTO `order_items` VALUES (10532, 66, 17.00, 24, 0.00);
INSERT INTO `order_items` VALUES (10533, 4, 22.00, 50, 0.05);
INSERT INTO `order_items` VALUES (10533, 72, 34.80, 24, 0.00);
INSERT INTO `order_items` VALUES (10533, 73, 15.00, 24, 0.05);
INSERT INTO `order_items` VALUES (10534, 30, 25.89, 10, 0.00);
INSERT INTO `order_items` VALUES (10534, 40, 18.40, 10, 0.20);
INSERT INTO `order_items` VALUES (10534, 54, 7.45, 10, 0.20);
INSERT INTO `order_items` VALUES (10535, 11, 21.00, 50, 0.10);
INSERT INTO `order_items` VALUES (10535, 40, 18.40, 10, 0.10);
INSERT INTO `order_items` VALUES (10535, 57, 19.50, 5, 0.10);
INSERT INTO `order_items` VALUES (10535, 59, 55.00, 15, 0.10);
INSERT INTO `order_items` VALUES (10536, 12, 38.00, 15, 0.25);
INSERT INTO `order_items` VALUES (10536, 31, 12.50, 20, 0.00);
INSERT INTO `order_items` VALUES (10536, 33, 2.50, 30, 0.00);
INSERT INTO `order_items` VALUES (10536, 60, 34.00, 35, 0.25);
INSERT INTO `order_items` VALUES (10537, 31, 12.50, 30, 0.00);
INSERT INTO `order_items` VALUES (10537, 51, 53.00, 6, 0.00);
INSERT INTO `order_items` VALUES (10537, 58, 13.25, 20, 0.00);
INSERT INTO `order_items` VALUES (10537, 72, 34.80, 21, 0.00);
INSERT INTO `order_items` VALUES (10537, 73, 15.00, 9, 0.00);
INSERT INTO `order_items` VALUES (10538, 70, 15.00, 7, 0.00);
INSERT INTO `order_items` VALUES (10538, 72, 34.80, 1, 0.00);
INSERT INTO `order_items` VALUES (10539, 13, 6.00, 8, 0.00);
INSERT INTO `order_items` VALUES (10539, 21, 10.00, 15, 0.00);
INSERT INTO `order_items` VALUES (10539, 33, 2.50, 15, 0.00);
INSERT INTO `order_items` VALUES (10539, 49, 20.00, 6, 0.00);
INSERT INTO `order_items` VALUES (10540, 3, 10.00, 60, 0.00);
INSERT INTO `order_items` VALUES (10540, 26, 31.23, 40, 0.00);
INSERT INTO `order_items` VALUES (10540, 38, 263.50, 30, 0.00);
INSERT INTO `order_items` VALUES (10540, 68, 12.50, 35, 0.00);
INSERT INTO `order_items` VALUES (10541, 24, 4.50, 35, 0.10);
INSERT INTO `order_items` VALUES (10541, 38, 263.50, 4, 0.10);
INSERT INTO `order_items` VALUES (10541, 65, 21.05, 36, 0.10);
INSERT INTO `order_items` VALUES (10541, 71, 21.50, 9, 0.10);
INSERT INTO `order_items` VALUES (10542, 11, 21.00, 15, 0.05);
INSERT INTO `order_items` VALUES (10542, 54, 7.45, 24, 0.05);
INSERT INTO `order_items` VALUES (10543, 12, 38.00, 30, 0.15);
INSERT INTO `order_items` VALUES (10543, 23, 9.00, 70, 0.15);
INSERT INTO `order_items` VALUES (10544, 28, 45.60, 7, 0.00);
INSERT INTO `order_items` VALUES (10544, 67, 14.00, 7, 0.00);
INSERT INTO `order_items` VALUES (10545, 11, 21.00, 10, 0.00);
INSERT INTO `order_items` VALUES (10546, 7, 30.00, 10, 0.00);
INSERT INTO `order_items` VALUES (10546, 35, 18.00, 30, 0.00);
INSERT INTO `order_items` VALUES (10546, 62, 49.30, 40, 0.00);
INSERT INTO `order_items` VALUES (10547, 32, 32.00, 24, 0.15);
INSERT INTO `order_items` VALUES (10547, 36, 19.00, 60, 0.00);
INSERT INTO `order_items` VALUES (10548, 34, 14.00, 10, 0.25);
INSERT INTO `order_items` VALUES (10548, 41, 9.65, 14, 0.00);
INSERT INTO `order_items` VALUES (10549, 31, 12.50, 55, 0.15);
INSERT INTO `order_items` VALUES (10549, 45, 9.50, 100, 0.15);
INSERT INTO `order_items` VALUES (10549, 51, 53.00, 48, 0.15);
INSERT INTO `order_items` VALUES (10550, 17, 39.00, 8, 0.10);
INSERT INTO `order_items` VALUES (10550, 19, 9.20, 10, 0.00);
INSERT INTO `order_items` VALUES (10550, 21, 10.00, 6, 0.10);
INSERT INTO `order_items` VALUES (10550, 61, 28.50, 10, 0.10);
INSERT INTO `order_items` VALUES (10551, 16, 17.45, 40, 0.15);
INSERT INTO `order_items` VALUES (10551, 35, 18.00, 20, 0.15);
INSERT INTO `order_items` VALUES (10551, 44, 19.45, 40, 0.00);
INSERT INTO `order_items` VALUES (10552, 69, 36.00, 18, 0.00);
INSERT INTO `order_items` VALUES (10552, 75, 7.75, 30, 0.00);
INSERT INTO `order_items` VALUES (10553, 11, 21.00, 15, 0.00);
INSERT INTO `order_items` VALUES (10553, 16, 17.45, 14, 0.00);
INSERT INTO `order_items` VALUES (10553, 22, 21.00, 24, 0.00);
INSERT INTO `order_items` VALUES (10553, 31, 12.50, 30, 0.00);
INSERT INTO `order_items` VALUES (10553, 35, 18.00, 6, 0.00);
INSERT INTO `order_items` VALUES (10554, 16, 17.45, 30, 0.05);
INSERT INTO `order_items` VALUES (10554, 23, 9.00, 20, 0.05);
INSERT INTO `order_items` VALUES (10554, 62, 49.30, 20, 0.05);
INSERT INTO `order_items` VALUES (10554, 77, 13.00, 10, 0.05);
INSERT INTO `order_items` VALUES (10555, 14, 23.25, 30, 0.20);
INSERT INTO `order_items` VALUES (10555, 19, 9.20, 35, 0.20);
INSERT INTO `order_items` VALUES (10555, 24, 4.50, 18, 0.20);
INSERT INTO `order_items` VALUES (10555, 51, 53.00, 20, 0.20);
INSERT INTO `order_items` VALUES (10555, 56, 38.00, 40, 0.20);
INSERT INTO `order_items` VALUES (10556, 72, 34.80, 24, 0.00);
INSERT INTO `order_items` VALUES (10557, 64, 33.25, 30, 0.00);
INSERT INTO `order_items` VALUES (10557, 75, 7.75, 20, 0.00);
INSERT INTO `order_items` VALUES (10558, 47, 9.50, 25, 0.00);
INSERT INTO `order_items` VALUES (10558, 51, 53.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10558, 52, 7.00, 30, 0.00);
INSERT INTO `order_items` VALUES (10558, 53, 32.80, 18, 0.00);
INSERT INTO `order_items` VALUES (10558, 73, 15.00, 3, 0.00);
INSERT INTO `order_items` VALUES (10559, 41, 9.65, 12, 0.05);
INSERT INTO `order_items` VALUES (10559, 55, 24.00, 18, 0.05);
INSERT INTO `order_items` VALUES (10560, 30, 25.89, 20, 0.00);
INSERT INTO `order_items` VALUES (10560, 62, 49.30, 15, 0.25);
INSERT INTO `order_items` VALUES (10561, 44, 19.45, 10, 0.00);
INSERT INTO `order_items` VALUES (10561, 51, 53.00, 50, 0.00);
INSERT INTO `order_items` VALUES (10562, 33, 2.50, 20, 0.10);
INSERT INTO `order_items` VALUES (10562, 62, 49.30, 10, 0.10);
INSERT INTO `order_items` VALUES (10563, 36, 19.00, 25, 0.00);
INSERT INTO `order_items` VALUES (10563, 52, 7.00, 70, 0.00);
INSERT INTO `order_items` VALUES (10564, 17, 39.00, 16, 0.05);
INSERT INTO `order_items` VALUES (10564, 31, 12.50, 6, 0.05);
INSERT INTO `order_items` VALUES (10564, 55, 24.00, 25, 0.05);
INSERT INTO `order_items` VALUES (10565, 24, 4.50, 25, 0.10);
INSERT INTO `order_items` VALUES (10565, 64, 33.25, 18, 0.10);
INSERT INTO `order_items` VALUES (10566, 11, 21.00, 35, 0.15);
INSERT INTO `order_items` VALUES (10566, 18, 62.50, 18, 0.15);
INSERT INTO `order_items` VALUES (10566, 76, 18.00, 10, 0.00);
INSERT INTO `order_items` VALUES (10567, 31, 12.50, 60, 0.20);
INSERT INTO `order_items` VALUES (10567, 51, 53.00, 3, 0.00);
INSERT INTO `order_items` VALUES (10567, 59, 55.00, 40, 0.20);
INSERT INTO `order_items` VALUES (10568, 10, 31.00, 5, 0.00);
INSERT INTO `order_items` VALUES (10569, 31, 12.50, 35, 0.20);
INSERT INTO `order_items` VALUES (10569, 76, 18.00, 30, 0.00);
INSERT INTO `order_items` VALUES (10570, 11, 21.00, 15, 0.05);
INSERT INTO `order_items` VALUES (10570, 56, 38.00, 60, 0.05);
INSERT INTO `order_items` VALUES (10571, 14, 23.25, 11, 0.15);
INSERT INTO `order_items` VALUES (10571, 42, 14.00, 28, 0.15);
INSERT INTO `order_items` VALUES (10572, 16, 17.45, 12, 0.10);
INSERT INTO `order_items` VALUES (10572, 32, 32.00, 10, 0.10);
INSERT INTO `order_items` VALUES (10572, 40, 18.40, 50, 0.00);
INSERT INTO `order_items` VALUES (10572, 75, 7.75, 15, 0.10);
INSERT INTO `order_items` VALUES (10573, 17, 39.00, 18, 0.00);
INSERT INTO `order_items` VALUES (10573, 34, 14.00, 40, 0.00);
INSERT INTO `order_items` VALUES (10573, 53, 32.80, 25, 0.00);
INSERT INTO `order_items` VALUES (10574, 33, 2.50, 14, 0.00);
INSERT INTO `order_items` VALUES (10574, 40, 18.40, 2, 0.00);
INSERT INTO `order_items` VALUES (10574, 62, 49.30, 10, 0.00);
INSERT INTO `order_items` VALUES (10574, 64, 33.25, 6, 0.00);
INSERT INTO `order_items` VALUES (10575, 59, 55.00, 12, 0.00);
INSERT INTO `order_items` VALUES (10575, 63, 43.90, 6, 0.00);
INSERT INTO `order_items` VALUES (10575, 72, 34.80, 30, 0.00);
INSERT INTO `order_items` VALUES (10575, 76, 18.00, 10, 0.00);
INSERT INTO `order_items` VALUES (10576, 1, 18.00, 10, 0.00);
INSERT INTO `order_items` VALUES (10576, 31, 12.50, 20, 0.00);
INSERT INTO `order_items` VALUES (10576, 44, 19.45, 21, 0.00);
INSERT INTO `order_items` VALUES (10577, 39, 18.00, 10, 0.00);
INSERT INTO `order_items` VALUES (10577, 75, 7.75, 20, 0.00);
INSERT INTO `order_items` VALUES (10577, 77, 13.00, 18, 0.00);
INSERT INTO `order_items` VALUES (10578, 35, 18.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10578, 57, 19.50, 6, 0.00);
INSERT INTO `order_items` VALUES (10579, 15, 15.50, 10, 0.00);
INSERT INTO `order_items` VALUES (10579, 75, 7.75, 21, 0.00);
INSERT INTO `order_items` VALUES (10580, 14, 23.25, 15, 0.05);
INSERT INTO `order_items` VALUES (10580, 41, 9.65, 9, 0.05);
INSERT INTO `order_items` VALUES (10580, 65, 21.05, 30, 0.05);
INSERT INTO `order_items` VALUES (10581, 75, 7.75, 50, 0.20);
INSERT INTO `order_items` VALUES (10582, 57, 19.50, 4, 0.00);
INSERT INTO `order_items` VALUES (10582, 76, 18.00, 14, 0.00);
INSERT INTO `order_items` VALUES (10583, 29, 123.79, 10, 0.00);
INSERT INTO `order_items` VALUES (10583, 60, 34.00, 24, 0.15);
INSERT INTO `order_items` VALUES (10583, 69, 36.00, 10, 0.15);
INSERT INTO `order_items` VALUES (10584, 31, 12.50, 50, 0.05);
INSERT INTO `order_items` VALUES (10585, 47, 9.50, 15, 0.00);
INSERT INTO `order_items` VALUES (10586, 52, 7.00, 4, 0.15);
INSERT INTO `order_items` VALUES (10587, 26, 31.23, 6, 0.00);
INSERT INTO `order_items` VALUES (10587, 35, 18.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10587, 77, 13.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10588, 18, 62.50, 40, 0.20);
INSERT INTO `order_items` VALUES (10588, 42, 14.00, 100, 0.20);
INSERT INTO `order_items` VALUES (10589, 35, 18.00, 4, 0.00);
INSERT INTO `order_items` VALUES (10590, 1, 18.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10590, 77, 13.00, 60, 0.05);
INSERT INTO `order_items` VALUES (10591, 3, 10.00, 14, 0.00);
INSERT INTO `order_items` VALUES (10591, 7, 30.00, 10, 0.00);
INSERT INTO `order_items` VALUES (10591, 54, 7.45, 50, 0.00);
INSERT INTO `order_items` VALUES (10592, 15, 15.50, 25, 0.05);
INSERT INTO `order_items` VALUES (10592, 26, 31.23, 5, 0.05);
INSERT INTO `order_items` VALUES (10593, 20, 81.00, 21, 0.20);
INSERT INTO `order_items` VALUES (10593, 69, 36.00, 20, 0.20);
INSERT INTO `order_items` VALUES (10593, 76, 18.00, 4, 0.20);
INSERT INTO `order_items` VALUES (10594, 52, 7.00, 24, 0.00);
INSERT INTO `order_items` VALUES (10594, 58, 13.25, 30, 0.00);
INSERT INTO `order_items` VALUES (10595, 35, 18.00, 30, 0.25);
INSERT INTO `order_items` VALUES (10595, 61, 28.50, 120, 0.25);
INSERT INTO `order_items` VALUES (10595, 69, 36.00, 65, 0.25);
INSERT INTO `order_items` VALUES (10596, 56, 38.00, 5, 0.20);
INSERT INTO `order_items` VALUES (10596, 63, 43.90, 24, 0.20);
INSERT INTO `order_items` VALUES (10596, 75, 7.75, 30, 0.20);
INSERT INTO `order_items` VALUES (10597, 24, 4.50, 35, 0.20);
INSERT INTO `order_items` VALUES (10597, 57, 19.50, 20, 0.00);
INSERT INTO `order_items` VALUES (10597, 65, 21.05, 12, 0.20);
INSERT INTO `order_items` VALUES (10598, 27, 43.90, 50, 0.00);
INSERT INTO `order_items` VALUES (10598, 71, 21.50, 9, 0.00);
INSERT INTO `order_items` VALUES (10599, 62, 49.30, 10, 0.00);
INSERT INTO `order_items` VALUES (10600, 54, 7.45, 4, 0.00);
INSERT INTO `order_items` VALUES (10600, 73, 15.00, 30, 0.00);
INSERT INTO `order_items` VALUES (10601, 13, 6.00, 60, 0.00);
INSERT INTO `order_items` VALUES (10601, 59, 55.00, 35, 0.00);
INSERT INTO `order_items` VALUES (10602, 77, 13.00, 5, 0.25);
INSERT INTO `order_items` VALUES (10603, 22, 21.00, 48, 0.00);
INSERT INTO `order_items` VALUES (10603, 49, 20.00, 25, 0.05);
INSERT INTO `order_items` VALUES (10604, 48, 12.75, 6, 0.10);
INSERT INTO `order_items` VALUES (10604, 76, 18.00, 10, 0.10);
INSERT INTO `order_items` VALUES (10605, 16, 17.45, 30, 0.05);
INSERT INTO `order_items` VALUES (10605, 59, 55.00, 20, 0.05);
INSERT INTO `order_items` VALUES (10605, 60, 34.00, 70, 0.05);
INSERT INTO `order_items` VALUES (10605, 71, 21.50, 15, 0.05);
INSERT INTO `order_items` VALUES (10606, 4, 22.00, 20, 0.20);
INSERT INTO `order_items` VALUES (10606, 55, 24.00, 20, 0.20);
INSERT INTO `order_items` VALUES (10606, 62, 49.30, 10, 0.20);
INSERT INTO `order_items` VALUES (10607, 7, 30.00, 45, 0.00);
INSERT INTO `order_items` VALUES (10607, 17, 39.00, 100, 0.00);
INSERT INTO `order_items` VALUES (10607, 33, 2.50, 14, 0.00);
INSERT INTO `order_items` VALUES (10607, 40, 18.40, 42, 0.00);
INSERT INTO `order_items` VALUES (10607, 72, 34.80, 12, 0.00);
INSERT INTO `order_items` VALUES (10608, 56, 38.00, 28, 0.00);
INSERT INTO `order_items` VALUES (10609, 1, 18.00, 3, 0.00);
INSERT INTO `order_items` VALUES (10609, 10, 31.00, 10, 0.00);
INSERT INTO `order_items` VALUES (10609, 21, 10.00, 6, 0.00);
INSERT INTO `order_items` VALUES (10610, 36, 19.00, 21, 0.25);
INSERT INTO `order_items` VALUES (10611, 1, 18.00, 6, 0.00);
INSERT INTO `order_items` VALUES (10611, 2, 19.00, 10, 0.00);
INSERT INTO `order_items` VALUES (10611, 60, 34.00, 15, 0.00);
INSERT INTO `order_items` VALUES (10612, 10, 31.00, 70, 0.00);
INSERT INTO `order_items` VALUES (10612, 36, 19.00, 55, 0.00);
INSERT INTO `order_items` VALUES (10612, 49, 20.00, 18, 0.00);
INSERT INTO `order_items` VALUES (10612, 60, 34.00, 40, 0.00);
INSERT INTO `order_items` VALUES (10612, 76, 18.00, 80, 0.00);
INSERT INTO `order_items` VALUES (10613, 13, 6.00, 8, 0.10);
INSERT INTO `order_items` VALUES (10613, 75, 7.75, 40, 0.00);
INSERT INTO `order_items` VALUES (10614, 11, 21.00, 14, 0.00);
INSERT INTO `order_items` VALUES (10614, 21, 10.00, 8, 0.00);
INSERT INTO `order_items` VALUES (10614, 39, 18.00, 5, 0.00);
INSERT INTO `order_items` VALUES (10615, 55, 24.00, 5, 0.00);
INSERT INTO `order_items` VALUES (10616, 38, 263.50, 15, 0.05);
INSERT INTO `order_items` VALUES (10616, 56, 38.00, 14, 0.00);
INSERT INTO `order_items` VALUES (10616, 70, 15.00, 15, 0.05);
INSERT INTO `order_items` VALUES (10616, 71, 21.50, 15, 0.05);
INSERT INTO `order_items` VALUES (10617, 59, 55.00, 30, 0.15);
INSERT INTO `order_items` VALUES (10618, 6, 25.00, 70, 0.00);
INSERT INTO `order_items` VALUES (10618, 56, 38.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10618, 68, 12.50, 15, 0.00);
INSERT INTO `order_items` VALUES (10619, 21, 10.00, 42, 0.00);
INSERT INTO `order_items` VALUES (10619, 22, 21.00, 40, 0.00);
INSERT INTO `order_items` VALUES (10620, 24, 4.50, 5, 0.00);
INSERT INTO `order_items` VALUES (10620, 52, 7.00, 5, 0.00);
INSERT INTO `order_items` VALUES (10621, 19, 9.20, 5, 0.00);
INSERT INTO `order_items` VALUES (10621, 23, 9.00, 10, 0.00);
INSERT INTO `order_items` VALUES (10621, 70, 15.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10621, 71, 21.50, 15, 0.00);
INSERT INTO `order_items` VALUES (10622, 2, 19.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10622, 68, 12.50, 18, 0.20);
INSERT INTO `order_items` VALUES (10623, 14, 23.25, 21, 0.00);
INSERT INTO `order_items` VALUES (10623, 19, 9.20, 15, 0.10);
INSERT INTO `order_items` VALUES (10623, 21, 10.00, 25, 0.10);
INSERT INTO `order_items` VALUES (10623, 24, 4.50, 3, 0.00);
INSERT INTO `order_items` VALUES (10623, 35, 18.00, 30, 0.10);
INSERT INTO `order_items` VALUES (10624, 28, 45.60, 10, 0.00);
INSERT INTO `order_items` VALUES (10624, 29, 123.79, 6, 0.00);
INSERT INTO `order_items` VALUES (10624, 44, 19.45, 10, 0.00);
INSERT INTO `order_items` VALUES (10625, 14, 23.25, 3, 0.00);
INSERT INTO `order_items` VALUES (10625, 42, 14.00, 5, 0.00);
INSERT INTO `order_items` VALUES (10625, 60, 34.00, 10, 0.00);
INSERT INTO `order_items` VALUES (10626, 53, 32.80, 12, 0.00);
INSERT INTO `order_items` VALUES (10626, 60, 34.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10626, 71, 21.50, 20, 0.00);
INSERT INTO `order_items` VALUES (10627, 62, 49.30, 15, 0.00);
INSERT INTO `order_items` VALUES (10627, 73, 15.00, 35, 0.15);
INSERT INTO `order_items` VALUES (10628, 1, 18.00, 25, 0.00);
INSERT INTO `order_items` VALUES (10629, 29, 123.79, 20, 0.00);
INSERT INTO `order_items` VALUES (10629, 64, 33.25, 9, 0.00);
INSERT INTO `order_items` VALUES (10630, 55, 24.00, 12, 0.05);
INSERT INTO `order_items` VALUES (10630, 76, 18.00, 35, 0.00);
INSERT INTO `order_items` VALUES (10631, 75, 7.75, 8, 0.10);
INSERT INTO `order_items` VALUES (10632, 2, 19.00, 30, 0.05);
INSERT INTO `order_items` VALUES (10632, 33, 2.50, 20, 0.05);
INSERT INTO `order_items` VALUES (10633, 12, 38.00, 36, 0.15);
INSERT INTO `order_items` VALUES (10633, 13, 6.00, 13, 0.15);
INSERT INTO `order_items` VALUES (10633, 26, 31.23, 35, 0.15);
INSERT INTO `order_items` VALUES (10633, 62, 49.30, 80, 0.15);
INSERT INTO `order_items` VALUES (10634, 7, 30.00, 35, 0.00);
INSERT INTO `order_items` VALUES (10634, 18, 62.50, 50, 0.00);
INSERT INTO `order_items` VALUES (10634, 51, 53.00, 15, 0.00);
INSERT INTO `order_items` VALUES (10634, 75, 7.75, 2, 0.00);
INSERT INTO `order_items` VALUES (10635, 4, 22.00, 10, 0.10);
INSERT INTO `order_items` VALUES (10635, 5, 21.35, 15, 0.10);
INSERT INTO `order_items` VALUES (10635, 22, 21.00, 40, 0.00);
INSERT INTO `order_items` VALUES (10636, 4, 22.00, 25, 0.00);
INSERT INTO `order_items` VALUES (10636, 58, 13.25, 6, 0.00);
INSERT INTO `order_items` VALUES (10637, 11, 21.00, 10, 0.00);
INSERT INTO `order_items` VALUES (10637, 50, 16.25, 25, 0.05);
INSERT INTO `order_items` VALUES (10637, 56, 38.00, 60, 0.05);
INSERT INTO `order_items` VALUES (10638, 45, 9.50, 20, 0.00);
INSERT INTO `order_items` VALUES (10638, 65, 21.05, 21, 0.00);
INSERT INTO `order_items` VALUES (10638, 72, 34.80, 60, 0.00);
INSERT INTO `order_items` VALUES (10639, 18, 62.50, 8, 0.00);
INSERT INTO `order_items` VALUES (10640, 69, 36.00, 20, 0.25);
INSERT INTO `order_items` VALUES (10640, 70, 15.00, 15, 0.25);
INSERT INTO `order_items` VALUES (10641, 2, 19.00, 50, 0.00);
INSERT INTO `order_items` VALUES (10641, 40, 18.40, 60, 0.00);
INSERT INTO `order_items` VALUES (10642, 21, 10.00, 30, 0.20);
INSERT INTO `order_items` VALUES (10642, 61, 28.50, 20, 0.20);
INSERT INTO `order_items` VALUES (10643, 28, 45.60, 15, 0.25);
INSERT INTO `order_items` VALUES (10643, 39, 18.00, 21, 0.25);
INSERT INTO `order_items` VALUES (10643, 46, 12.00, 2, 0.25);
INSERT INTO `order_items` VALUES (10644, 18, 62.50, 4, 0.10);
INSERT INTO `order_items` VALUES (10644, 43, 46.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10644, 46, 12.00, 21, 0.10);
INSERT INTO `order_items` VALUES (10645, 18, 62.50, 20, 0.00);
INSERT INTO `order_items` VALUES (10645, 36, 19.00, 15, 0.00);
INSERT INTO `order_items` VALUES (10646, 1, 18.00, 15, 0.25);
INSERT INTO `order_items` VALUES (10646, 10, 31.00, 18, 0.25);
INSERT INTO `order_items` VALUES (10646, 71, 21.50, 30, 0.25);
INSERT INTO `order_items` VALUES (10646, 77, 13.00, 35, 0.25);
INSERT INTO `order_items` VALUES (10647, 19, 9.20, 30, 0.00);
INSERT INTO `order_items` VALUES (10647, 39, 18.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10648, 22, 21.00, 15, 0.00);
INSERT INTO `order_items` VALUES (10648, 24, 4.50, 15, 0.15);
INSERT INTO `order_items` VALUES (10649, 28, 45.60, 20, 0.00);
INSERT INTO `order_items` VALUES (10649, 72, 34.80, 15, 0.00);
INSERT INTO `order_items` VALUES (10650, 30, 25.89, 30, 0.00);
INSERT INTO `order_items` VALUES (10650, 53, 32.80, 25, 0.05);
INSERT INTO `order_items` VALUES (10650, 54, 7.45, 30, 0.00);
INSERT INTO `order_items` VALUES (10651, 19, 9.20, 12, 0.25);
INSERT INTO `order_items` VALUES (10651, 22, 21.00, 20, 0.25);
INSERT INTO `order_items` VALUES (10652, 30, 25.89, 2, 0.25);
INSERT INTO `order_items` VALUES (10652, 42, 14.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10653, 16, 17.45, 30, 0.10);
INSERT INTO `order_items` VALUES (10653, 60, 34.00, 20, 0.10);
INSERT INTO `order_items` VALUES (10654, 4, 22.00, 12, 0.10);
INSERT INTO `order_items` VALUES (10654, 39, 18.00, 20, 0.10);
INSERT INTO `order_items` VALUES (10654, 54, 7.45, 6, 0.10);
INSERT INTO `order_items` VALUES (10655, 41, 9.65, 20, 0.20);
INSERT INTO `order_items` VALUES (10656, 14, 23.25, 3, 0.10);
INSERT INTO `order_items` VALUES (10656, 44, 19.45, 28, 0.10);
INSERT INTO `order_items` VALUES (10656, 47, 9.50, 6, 0.10);
INSERT INTO `order_items` VALUES (10657, 15, 15.50, 50, 0.00);
INSERT INTO `order_items` VALUES (10657, 41, 9.65, 24, 0.00);
INSERT INTO `order_items` VALUES (10657, 46, 12.00, 45, 0.00);
INSERT INTO `order_items` VALUES (10657, 47, 9.50, 10, 0.00);
INSERT INTO `order_items` VALUES (10657, 56, 38.00, 45, 0.00);
INSERT INTO `order_items` VALUES (10657, 60, 34.00, 30, 0.00);
INSERT INTO `order_items` VALUES (10658, 21, 10.00, 60, 0.00);
INSERT INTO `order_items` VALUES (10658, 40, 18.40, 70, 0.05);
INSERT INTO `order_items` VALUES (10658, 60, 34.00, 55, 0.05);
INSERT INTO `order_items` VALUES (10658, 77, 13.00, 70, 0.05);
INSERT INTO `order_items` VALUES (10659, 31, 12.50, 20, 0.05);
INSERT INTO `order_items` VALUES (10659, 40, 18.40, 24, 0.05);
INSERT INTO `order_items` VALUES (10659, 70, 15.00, 40, 0.05);
INSERT INTO `order_items` VALUES (10660, 20, 81.00, 21, 0.00);
INSERT INTO `order_items` VALUES (10661, 39, 18.00, 3, 0.20);
INSERT INTO `order_items` VALUES (10661, 58, 13.25, 49, 0.20);
INSERT INTO `order_items` VALUES (10662, 68, 12.50, 10, 0.00);
INSERT INTO `order_items` VALUES (10663, 40, 18.40, 30, 0.05);
INSERT INTO `order_items` VALUES (10663, 42, 14.00, 30, 0.05);
INSERT INTO `order_items` VALUES (10663, 51, 53.00, 20, 0.05);
INSERT INTO `order_items` VALUES (10664, 10, 31.00, 24, 0.15);
INSERT INTO `order_items` VALUES (10664, 56, 38.00, 12, 0.15);
INSERT INTO `order_items` VALUES (10664, 65, 21.05, 15, 0.15);
INSERT INTO `order_items` VALUES (10665, 51, 53.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10665, 59, 55.00, 1, 0.00);
INSERT INTO `order_items` VALUES (10665, 76, 18.00, 10, 0.00);
INSERT INTO `order_items` VALUES (10666, 29, 123.79, 36, 0.00);
INSERT INTO `order_items` VALUES (10666, 65, 21.05, 10, 0.00);
INSERT INTO `order_items` VALUES (10667, 69, 36.00, 45, 0.20);
INSERT INTO `order_items` VALUES (10667, 71, 21.50, 14, 0.20);
INSERT INTO `order_items` VALUES (10668, 31, 12.50, 8, 0.10);
INSERT INTO `order_items` VALUES (10668, 55, 24.00, 4, 0.10);
INSERT INTO `order_items` VALUES (10668, 64, 33.25, 15, 0.10);
INSERT INTO `order_items` VALUES (10669, 36, 19.00, 30, 0.00);
INSERT INTO `order_items` VALUES (10670, 23, 9.00, 32, 0.00);
INSERT INTO `order_items` VALUES (10670, 46, 12.00, 60, 0.00);
INSERT INTO `order_items` VALUES (10670, 67, 14.00, 25, 0.00);
INSERT INTO `order_items` VALUES (10670, 73, 15.00, 50, 0.00);
INSERT INTO `order_items` VALUES (10670, 75, 7.75, 25, 0.00);
INSERT INTO `order_items` VALUES (10671, 16, 17.45, 10, 0.00);
INSERT INTO `order_items` VALUES (10671, 62, 49.30, 10, 0.00);
INSERT INTO `order_items` VALUES (10671, 65, 21.05, 12, 0.00);
INSERT INTO `order_items` VALUES (10672, 38, 263.50, 15, 0.10);
INSERT INTO `order_items` VALUES (10672, 71, 21.50, 12, 0.00);
INSERT INTO `order_items` VALUES (10673, 16, 17.45, 3, 0.00);
INSERT INTO `order_items` VALUES (10673, 42, 14.00, 6, 0.00);
INSERT INTO `order_items` VALUES (10673, 43, 46.00, 6, 0.00);
INSERT INTO `order_items` VALUES (10674, 23, 9.00, 5, 0.00);
INSERT INTO `order_items` VALUES (10675, 14, 23.25, 30, 0.00);
INSERT INTO `order_items` VALUES (10675, 53, 32.80, 10, 0.00);
INSERT INTO `order_items` VALUES (10675, 58, 13.25, 30, 0.00);
INSERT INTO `order_items` VALUES (10676, 10, 31.00, 2, 0.00);
INSERT INTO `order_items` VALUES (10676, 19, 9.20, 7, 0.00);
INSERT INTO `order_items` VALUES (10676, 44, 19.45, 21, 0.00);
INSERT INTO `order_items` VALUES (10677, 26, 31.23, 30, 0.15);
INSERT INTO `order_items` VALUES (10677, 33, 2.50, 8, 0.15);
INSERT INTO `order_items` VALUES (10678, 12, 38.00, 100, 0.00);
INSERT INTO `order_items` VALUES (10678, 33, 2.50, 30, 0.00);
INSERT INTO `order_items` VALUES (10678, 41, 9.65, 120, 0.00);
INSERT INTO `order_items` VALUES (10678, 54, 7.45, 30, 0.00);
INSERT INTO `order_items` VALUES (10679, 59, 55.00, 12, 0.00);
INSERT INTO `order_items` VALUES (10680, 16, 17.45, 50, 0.25);
INSERT INTO `order_items` VALUES (10680, 31, 12.50, 20, 0.25);
INSERT INTO `order_items` VALUES (10680, 42, 14.00, 40, 0.25);
INSERT INTO `order_items` VALUES (10681, 19, 9.20, 30, 0.10);
INSERT INTO `order_items` VALUES (10681, 21, 10.00, 12, 0.10);
INSERT INTO `order_items` VALUES (10681, 64, 33.25, 28, 0.00);
INSERT INTO `order_items` VALUES (10682, 33, 2.50, 30, 0.00);
INSERT INTO `order_items` VALUES (10682, 66, 17.00, 4, 0.00);
INSERT INTO `order_items` VALUES (10682, 75, 7.75, 30, 0.00);
INSERT INTO `order_items` VALUES (10683, 52, 7.00, 9, 0.00);
INSERT INTO `order_items` VALUES (10684, 40, 18.40, 20, 0.00);
INSERT INTO `order_items` VALUES (10684, 47, 9.50, 40, 0.00);
INSERT INTO `order_items` VALUES (10684, 60, 34.00, 30, 0.00);
INSERT INTO `order_items` VALUES (10685, 10, 31.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10685, 41, 9.65, 4, 0.00);
INSERT INTO `order_items` VALUES (10685, 47, 9.50, 15, 0.00);
INSERT INTO `order_items` VALUES (10686, 17, 39.00, 30, 0.20);
INSERT INTO `order_items` VALUES (10686, 26, 31.23, 15, 0.00);
INSERT INTO `order_items` VALUES (10687, 9, 97.00, 50, 0.25);
INSERT INTO `order_items` VALUES (10687, 29, 123.79, 10, 0.00);
INSERT INTO `order_items` VALUES (10687, 36, 19.00, 6, 0.25);
INSERT INTO `order_items` VALUES (10688, 10, 31.00, 18, 0.10);
INSERT INTO `order_items` VALUES (10688, 28, 45.60, 60, 0.10);
INSERT INTO `order_items` VALUES (10688, 34, 14.00, 14, 0.00);
INSERT INTO `order_items` VALUES (10689, 1, 18.00, 35, 0.25);
INSERT INTO `order_items` VALUES (10690, 56, 38.00, 20, 0.25);
INSERT INTO `order_items` VALUES (10690, 77, 13.00, 30, 0.25);
INSERT INTO `order_items` VALUES (10691, 1, 18.00, 30, 0.00);
INSERT INTO `order_items` VALUES (10691, 29, 123.79, 40, 0.00);
INSERT INTO `order_items` VALUES (10691, 43, 46.00, 40, 0.00);
INSERT INTO `order_items` VALUES (10691, 44, 19.45, 24, 0.00);
INSERT INTO `order_items` VALUES (10691, 62, 49.30, 48, 0.00);
INSERT INTO `order_items` VALUES (10692, 63, 43.90, 20, 0.00);
INSERT INTO `order_items` VALUES (10693, 9, 97.00, 6, 0.00);
INSERT INTO `order_items` VALUES (10693, 54, 7.45, 60, 0.15);
INSERT INTO `order_items` VALUES (10693, 69, 36.00, 30, 0.15);
INSERT INTO `order_items` VALUES (10693, 73, 15.00, 15, 0.15);
INSERT INTO `order_items` VALUES (10694, 7, 30.00, 90, 0.00);
INSERT INTO `order_items` VALUES (10694, 59, 55.00, 25, 0.00);
INSERT INTO `order_items` VALUES (10694, 70, 15.00, 50, 0.00);
INSERT INTO `order_items` VALUES (10695, 8, 40.00, 10, 0.00);
INSERT INTO `order_items` VALUES (10695, 12, 38.00, 4, 0.00);
INSERT INTO `order_items` VALUES (10695, 24, 4.50, 20, 0.00);
INSERT INTO `order_items` VALUES (10696, 17, 39.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10696, 46, 12.00, 18, 0.00);
INSERT INTO `order_items` VALUES (10697, 19, 9.20, 7, 0.25);
INSERT INTO `order_items` VALUES (10697, 35, 18.00, 9, 0.25);
INSERT INTO `order_items` VALUES (10697, 58, 13.25, 30, 0.25);
INSERT INTO `order_items` VALUES (10697, 70, 15.00, 30, 0.25);
INSERT INTO `order_items` VALUES (10698, 11, 21.00, 15, 0.00);
INSERT INTO `order_items` VALUES (10698, 17, 39.00, 8, 0.05);
INSERT INTO `order_items` VALUES (10698, 29, 123.79, 12, 0.05);
INSERT INTO `order_items` VALUES (10698, 65, 21.05, 65, 0.05);
INSERT INTO `order_items` VALUES (10698, 70, 15.00, 8, 0.05);
INSERT INTO `order_items` VALUES (10699, 47, 9.50, 12, 0.00);
INSERT INTO `order_items` VALUES (10700, 1, 18.00, 5, 0.20);
INSERT INTO `order_items` VALUES (10700, 34, 14.00, 12, 0.20);
INSERT INTO `order_items` VALUES (10700, 68, 12.50, 40, 0.20);
INSERT INTO `order_items` VALUES (10700, 71, 21.50, 60, 0.20);
INSERT INTO `order_items` VALUES (10701, 59, 55.00, 42, 0.15);
INSERT INTO `order_items` VALUES (10701, 71, 21.50, 20, 0.15);
INSERT INTO `order_items` VALUES (10701, 76, 18.00, 35, 0.15);
INSERT INTO `order_items` VALUES (10702, 3, 10.00, 6, 0.00);
INSERT INTO `order_items` VALUES (10702, 76, 18.00, 15, 0.00);
INSERT INTO `order_items` VALUES (10703, 2, 19.00, 5, 0.00);
INSERT INTO `order_items` VALUES (10703, 59, 55.00, 35, 0.00);
INSERT INTO `order_items` VALUES (10703, 73, 15.00, 35, 0.00);
INSERT INTO `order_items` VALUES (10704, 4, 22.00, 6, 0.00);
INSERT INTO `order_items` VALUES (10704, 24, 4.50, 35, 0.00);
INSERT INTO `order_items` VALUES (10704, 48, 12.75, 24, 0.00);
INSERT INTO `order_items` VALUES (10705, 31, 12.50, 20, 0.00);
INSERT INTO `order_items` VALUES (10705, 32, 32.00, 4, 0.00);
INSERT INTO `order_items` VALUES (10706, 16, 17.45, 20, 0.00);
INSERT INTO `order_items` VALUES (10706, 43, 46.00, 24, 0.00);
INSERT INTO `order_items` VALUES (10706, 59, 55.00, 8, 0.00);
INSERT INTO `order_items` VALUES (10707, 55, 24.00, 21, 0.00);
INSERT INTO `order_items` VALUES (10707, 57, 19.50, 40, 0.00);
INSERT INTO `order_items` VALUES (10707, 70, 15.00, 28, 0.15);
INSERT INTO `order_items` VALUES (10708, 5, 21.35, 4, 0.00);
INSERT INTO `order_items` VALUES (10708, 36, 19.00, 5, 0.00);
INSERT INTO `order_items` VALUES (10709, 8, 40.00, 40, 0.00);
INSERT INTO `order_items` VALUES (10709, 51, 53.00, 28, 0.00);
INSERT INTO `order_items` VALUES (10709, 60, 34.00, 10, 0.00);
INSERT INTO `order_items` VALUES (10710, 19, 9.20, 5, 0.00);
INSERT INTO `order_items` VALUES (10710, 47, 9.50, 5, 0.00);
INSERT INTO `order_items` VALUES (10711, 19, 9.20, 12, 0.00);
INSERT INTO `order_items` VALUES (10711, 41, 9.65, 42, 0.00);
INSERT INTO `order_items` VALUES (10711, 53, 32.80, 120, 0.00);
INSERT INTO `order_items` VALUES (10712, 53, 32.80, 3, 0.05);
INSERT INTO `order_items` VALUES (10712, 56, 38.00, 30, 0.00);
INSERT INTO `order_items` VALUES (10713, 10, 31.00, 18, 0.00);
INSERT INTO `order_items` VALUES (10713, 26, 31.23, 30, 0.00);
INSERT INTO `order_items` VALUES (10713, 45, 9.50, 110, 0.00);
INSERT INTO `order_items` VALUES (10713, 46, 12.00, 24, 0.00);
INSERT INTO `order_items` VALUES (10714, 2, 19.00, 30, 0.25);
INSERT INTO `order_items` VALUES (10714, 17, 39.00, 27, 0.25);
INSERT INTO `order_items` VALUES (10714, 47, 9.50, 50, 0.25);
INSERT INTO `order_items` VALUES (10714, 56, 38.00, 18, 0.25);
INSERT INTO `order_items` VALUES (10714, 58, 13.25, 12, 0.25);
INSERT INTO `order_items` VALUES (10715, 10, 31.00, 21, 0.00);
INSERT INTO `order_items` VALUES (10715, 71, 21.50, 30, 0.00);
INSERT INTO `order_items` VALUES (10716, 21, 10.00, 5, 0.00);
INSERT INTO `order_items` VALUES (10716, 51, 53.00, 7, 0.00);
INSERT INTO `order_items` VALUES (10716, 61, 28.50, 10, 0.00);
INSERT INTO `order_items` VALUES (10717, 21, 10.00, 32, 0.05);
INSERT INTO `order_items` VALUES (10717, 54, 7.45, 15, 0.00);
INSERT INTO `order_items` VALUES (10717, 69, 36.00, 25, 0.05);
INSERT INTO `order_items` VALUES (10718, 12, 38.00, 36, 0.00);
INSERT INTO `order_items` VALUES (10718, 16, 17.45, 20, 0.00);
INSERT INTO `order_items` VALUES (10718, 36, 19.00, 40, 0.00);
INSERT INTO `order_items` VALUES (10718, 62, 49.30, 20, 0.00);
INSERT INTO `order_items` VALUES (10719, 18, 62.50, 12, 0.25);
INSERT INTO `order_items` VALUES (10719, 30, 25.89, 3, 0.25);
INSERT INTO `order_items` VALUES (10719, 54, 7.45, 40, 0.25);
INSERT INTO `order_items` VALUES (10720, 35, 18.00, 21, 0.00);
INSERT INTO `order_items` VALUES (10720, 71, 21.50, 8, 0.00);
INSERT INTO `order_items` VALUES (10721, 44, 19.45, 50, 0.05);
INSERT INTO `order_items` VALUES (10722, 2, 19.00, 3, 0.00);
INSERT INTO `order_items` VALUES (10722, 31, 12.50, 50, 0.00);
INSERT INTO `order_items` VALUES (10722, 68, 12.50, 45, 0.00);
INSERT INTO `order_items` VALUES (10722, 75, 7.75, 42, 0.00);
INSERT INTO `order_items` VALUES (10723, 26, 31.23, 15, 0.00);
INSERT INTO `order_items` VALUES (10724, 10, 31.00, 16, 0.00);
INSERT INTO `order_items` VALUES (10724, 61, 28.50, 5, 0.00);
INSERT INTO `order_items` VALUES (10725, 41, 9.65, 12, 0.00);
INSERT INTO `order_items` VALUES (10725, 52, 7.00, 4, 0.00);
INSERT INTO `order_items` VALUES (10725, 55, 24.00, 6, 0.00);
INSERT INTO `order_items` VALUES (10726, 4, 22.00, 25, 0.00);
INSERT INTO `order_items` VALUES (10726, 11, 21.00, 5, 0.00);
INSERT INTO `order_items` VALUES (10727, 17, 39.00, 20, 0.05);
INSERT INTO `order_items` VALUES (10727, 56, 38.00, 10, 0.05);
INSERT INTO `order_items` VALUES (10727, 59, 55.00, 10, 0.05);
INSERT INTO `order_items` VALUES (10728, 30, 25.89, 15, 0.00);
INSERT INTO `order_items` VALUES (10728, 40, 18.40, 6, 0.00);
INSERT INTO `order_items` VALUES (10728, 55, 24.00, 12, 0.00);
INSERT INTO `order_items` VALUES (10728, 60, 34.00, 15, 0.00);
INSERT INTO `order_items` VALUES (10729, 1, 18.00, 50, 0.00);
INSERT INTO `order_items` VALUES (10729, 21, 10.00, 30, 0.00);
INSERT INTO `order_items` VALUES (10729, 50, 16.25, 40, 0.00);
INSERT INTO `order_items` VALUES (10730, 16, 17.45, 15, 0.05);
INSERT INTO `order_items` VALUES (10730, 31, 12.50, 3, 0.05);
INSERT INTO `order_items` VALUES (10730, 65, 21.05, 10, 0.05);
INSERT INTO `order_items` VALUES (10731, 21, 10.00, 40, 0.05);
INSERT INTO `order_items` VALUES (10731, 51, 53.00, 30, 0.05);
INSERT INTO `order_items` VALUES (10732, 76, 18.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10733, 14, 23.25, 16, 0.00);
INSERT INTO `order_items` VALUES (10733, 28, 45.60, 20, 0.00);
INSERT INTO `order_items` VALUES (10733, 52, 7.00, 25, 0.00);
INSERT INTO `order_items` VALUES (10734, 6, 25.00, 30, 0.00);
INSERT INTO `order_items` VALUES (10734, 30, 25.89, 15, 0.00);
INSERT INTO `order_items` VALUES (10734, 76, 18.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10735, 61, 28.50, 20, 0.10);
INSERT INTO `order_items` VALUES (10735, 77, 13.00, 2, 0.10);
INSERT INTO `order_items` VALUES (10736, 65, 21.05, 40, 0.00);
INSERT INTO `order_items` VALUES (10736, 75, 7.75, 20, 0.00);
INSERT INTO `order_items` VALUES (10737, 13, 6.00, 4, 0.00);
INSERT INTO `order_items` VALUES (10737, 41, 9.65, 12, 0.00);
INSERT INTO `order_items` VALUES (10738, 16, 17.45, 3, 0.00);
INSERT INTO `order_items` VALUES (10739, 36, 19.00, 6, 0.00);
INSERT INTO `order_items` VALUES (10739, 52, 7.00, 18, 0.00);
INSERT INTO `order_items` VALUES (10740, 28, 45.60, 5, 0.20);
INSERT INTO `order_items` VALUES (10740, 35, 18.00, 35, 0.20);
INSERT INTO `order_items` VALUES (10740, 45, 9.50, 40, 0.20);
INSERT INTO `order_items` VALUES (10740, 56, 38.00, 14, 0.20);
INSERT INTO `order_items` VALUES (10741, 2, 19.00, 15, 0.20);
INSERT INTO `order_items` VALUES (10742, 3, 10.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10742, 60, 34.00, 50, 0.00);
INSERT INTO `order_items` VALUES (10742, 72, 34.80, 35, 0.00);
INSERT INTO `order_items` VALUES (10743, 46, 12.00, 28, 0.05);
INSERT INTO `order_items` VALUES (10744, 40, 18.40, 50, 0.20);
INSERT INTO `order_items` VALUES (10745, 18, 62.50, 24, 0.00);
INSERT INTO `order_items` VALUES (10745, 44, 19.45, 16, 0.00);
INSERT INTO `order_items` VALUES (10745, 59, 55.00, 45, 0.00);
INSERT INTO `order_items` VALUES (10745, 72, 34.80, 7, 0.00);
INSERT INTO `order_items` VALUES (10746, 13, 6.00, 6, 0.00);
INSERT INTO `order_items` VALUES (10746, 42, 14.00, 28, 0.00);
INSERT INTO `order_items` VALUES (10746, 62, 49.30, 9, 0.00);
INSERT INTO `order_items` VALUES (10746, 69, 36.00, 40, 0.00);
INSERT INTO `order_items` VALUES (10747, 31, 12.50, 8, 0.00);
INSERT INTO `order_items` VALUES (10747, 41, 9.65, 35, 0.00);
INSERT INTO `order_items` VALUES (10747, 63, 43.90, 9, 0.00);
INSERT INTO `order_items` VALUES (10747, 69, 36.00, 30, 0.00);
INSERT INTO `order_items` VALUES (10748, 23, 9.00, 44, 0.00);
INSERT INTO `order_items` VALUES (10748, 40, 18.40, 40, 0.00);
INSERT INTO `order_items` VALUES (10748, 56, 38.00, 28, 0.00);
INSERT INTO `order_items` VALUES (10749, 56, 38.00, 15, 0.00);
INSERT INTO `order_items` VALUES (10749, 59, 55.00, 6, 0.00);
INSERT INTO `order_items` VALUES (10749, 76, 18.00, 10, 0.00);
INSERT INTO `order_items` VALUES (10750, 14, 23.25, 5, 0.15);
INSERT INTO `order_items` VALUES (10750, 45, 9.50, 40, 0.15);
INSERT INTO `order_items` VALUES (10750, 59, 55.00, 25, 0.15);
INSERT INTO `order_items` VALUES (10751, 26, 31.23, 12, 0.10);
INSERT INTO `order_items` VALUES (10751, 30, 25.89, 30, 0.00);
INSERT INTO `order_items` VALUES (10751, 50, 16.25, 20, 0.10);
INSERT INTO `order_items` VALUES (10751, 73, 15.00, 15, 0.00);
INSERT INTO `order_items` VALUES (10752, 1, 18.00, 8, 0.00);
INSERT INTO `order_items` VALUES (10752, 69, 36.00, 3, 0.00);
INSERT INTO `order_items` VALUES (10753, 45, 9.50, 4, 0.00);
INSERT INTO `order_items` VALUES (10753, 74, 10.00, 5, 0.00);
INSERT INTO `order_items` VALUES (10754, 40, 18.40, 3, 0.00);
INSERT INTO `order_items` VALUES (10755, 47, 9.50, 30, 0.25);
INSERT INTO `order_items` VALUES (10755, 56, 38.00, 30, 0.25);
INSERT INTO `order_items` VALUES (10755, 57, 19.50, 14, 0.25);
INSERT INTO `order_items` VALUES (10755, 69, 36.00, 25, 0.25);
INSERT INTO `order_items` VALUES (10756, 18, 62.50, 21, 0.20);
INSERT INTO `order_items` VALUES (10756, 36, 19.00, 20, 0.20);
INSERT INTO `order_items` VALUES (10756, 68, 12.50, 6, 0.20);
INSERT INTO `order_items` VALUES (10756, 69, 36.00, 20, 0.20);
INSERT INTO `order_items` VALUES (10757, 34, 14.00, 30, 0.00);
INSERT INTO `order_items` VALUES (10757, 59, 55.00, 7, 0.00);
INSERT INTO `order_items` VALUES (10757, 62, 49.30, 30, 0.00);
INSERT INTO `order_items` VALUES (10757, 64, 33.25, 24, 0.00);
INSERT INTO `order_items` VALUES (10758, 26, 31.23, 20, 0.00);
INSERT INTO `order_items` VALUES (10758, 52, 7.00, 60, 0.00);
INSERT INTO `order_items` VALUES (10758, 70, 15.00, 40, 0.00);
INSERT INTO `order_items` VALUES (10759, 32, 32.00, 10, 0.00);
INSERT INTO `order_items` VALUES (10760, 25, 14.00, 12, 0.25);
INSERT INTO `order_items` VALUES (10760, 27, 43.90, 40, 0.00);
INSERT INTO `order_items` VALUES (10760, 43, 46.00, 30, 0.25);
INSERT INTO `order_items` VALUES (10761, 25, 14.00, 35, 0.25);
INSERT INTO `order_items` VALUES (10761, 75, 7.75, 18, 0.00);
INSERT INTO `order_items` VALUES (10762, 39, 18.00, 16, 0.00);
INSERT INTO `order_items` VALUES (10762, 47, 9.50, 30, 0.00);
INSERT INTO `order_items` VALUES (10762, 51, 53.00, 28, 0.00);
INSERT INTO `order_items` VALUES (10762, 56, 38.00, 60, 0.00);
INSERT INTO `order_items` VALUES (10763, 21, 10.00, 40, 0.00);
INSERT INTO `order_items` VALUES (10763, 22, 21.00, 6, 0.00);
INSERT INTO `order_items` VALUES (10763, 24, 4.50, 20, 0.00);
INSERT INTO `order_items` VALUES (10764, 3, 10.00, 20, 0.10);
INSERT INTO `order_items` VALUES (10764, 39, 18.00, 130, 0.10);
INSERT INTO `order_items` VALUES (10765, 65, 21.05, 80, 0.10);
INSERT INTO `order_items` VALUES (10766, 2, 19.00, 40, 0.00);
INSERT INTO `order_items` VALUES (10766, 7, 30.00, 35, 0.00);
INSERT INTO `order_items` VALUES (10766, 68, 12.50, 40, 0.00);
INSERT INTO `order_items` VALUES (10767, 42, 14.00, 2, 0.00);
INSERT INTO `order_items` VALUES (10768, 22, 21.00, 4, 0.00);
INSERT INTO `order_items` VALUES (10768, 31, 12.50, 50, 0.00);
INSERT INTO `order_items` VALUES (10768, 60, 34.00, 15, 0.00);
INSERT INTO `order_items` VALUES (10768, 71, 21.50, 12, 0.00);
INSERT INTO `order_items` VALUES (10769, 41, 9.65, 30, 0.05);
INSERT INTO `order_items` VALUES (10769, 52, 7.00, 15, 0.05);
INSERT INTO `order_items` VALUES (10769, 61, 28.50, 20, 0.00);
INSERT INTO `order_items` VALUES (10769, 62, 49.30, 15, 0.00);
INSERT INTO `order_items` VALUES (10770, 11, 21.00, 15, 0.25);
INSERT INTO `order_items` VALUES (10771, 71, 21.50, 16, 0.00);
INSERT INTO `order_items` VALUES (10772, 29, 123.79, 18, 0.00);
INSERT INTO `order_items` VALUES (10772, 59, 55.00, 25, 0.00);
INSERT INTO `order_items` VALUES (10773, 17, 39.00, 33, 0.00);
INSERT INTO `order_items` VALUES (10773, 31, 12.50, 70, 0.20);
INSERT INTO `order_items` VALUES (10773, 75, 7.75, 7, 0.20);
INSERT INTO `order_items` VALUES (10774, 31, 12.50, 2, 0.25);
INSERT INTO `order_items` VALUES (10774, 66, 17.00, 50, 0.00);
INSERT INTO `order_items` VALUES (10775, 10, 31.00, 6, 0.00);
INSERT INTO `order_items` VALUES (10775, 67, 14.00, 3, 0.00);
INSERT INTO `order_items` VALUES (10776, 31, 12.50, 16, 0.05);
INSERT INTO `order_items` VALUES (10776, 42, 14.00, 12, 0.05);
INSERT INTO `order_items` VALUES (10776, 45, 9.50, 27, 0.05);
INSERT INTO `order_items` VALUES (10776, 51, 53.00, 120, 0.05);
INSERT INTO `order_items` VALUES (10777, 42, 14.00, 20, 0.20);
INSERT INTO `order_items` VALUES (10778, 41, 9.65, 10, 0.00);
INSERT INTO `order_items` VALUES (10779, 16, 17.45, 20, 0.00);
INSERT INTO `order_items` VALUES (10779, 62, 49.30, 20, 0.00);
INSERT INTO `order_items` VALUES (10780, 70, 15.00, 35, 0.00);
INSERT INTO `order_items` VALUES (10780, 77, 13.00, 15, 0.00);
INSERT INTO `order_items` VALUES (10781, 54, 7.45, 3, 0.20);
INSERT INTO `order_items` VALUES (10781, 56, 38.00, 20, 0.20);
INSERT INTO `order_items` VALUES (10781, 74, 10.00, 35, 0.00);
INSERT INTO `order_items` VALUES (10782, 31, 12.50, 1, 0.00);
INSERT INTO `order_items` VALUES (10783, 31, 12.50, 10, 0.00);
INSERT INTO `order_items` VALUES (10783, 38, 263.50, 5, 0.00);
INSERT INTO `order_items` VALUES (10784, 36, 19.00, 30, 0.00);
INSERT INTO `order_items` VALUES (10784, 39, 18.00, 2, 0.15);
INSERT INTO `order_items` VALUES (10784, 72, 34.80, 30, 0.15);
INSERT INTO `order_items` VALUES (10785, 10, 31.00, 10, 0.00);
INSERT INTO `order_items` VALUES (10785, 75, 7.75, 10, 0.00);
INSERT INTO `order_items` VALUES (10786, 8, 40.00, 30, 0.20);
INSERT INTO `order_items` VALUES (10786, 30, 25.89, 15, 0.20);
INSERT INTO `order_items` VALUES (10786, 75, 7.75, 42, 0.20);
INSERT INTO `order_items` VALUES (10787, 2, 19.00, 15, 0.05);
INSERT INTO `order_items` VALUES (10787, 29, 123.79, 20, 0.05);
INSERT INTO `order_items` VALUES (10788, 19, 9.20, 50, 0.05);
INSERT INTO `order_items` VALUES (10788, 75, 7.75, 40, 0.05);
INSERT INTO `order_items` VALUES (10789, 18, 62.50, 30, 0.00);
INSERT INTO `order_items` VALUES (10789, 35, 18.00, 15, 0.00);
INSERT INTO `order_items` VALUES (10789, 63, 43.90, 30, 0.00);
INSERT INTO `order_items` VALUES (10789, 68, 12.50, 18, 0.00);
INSERT INTO `order_items` VALUES (10790, 7, 30.00, 3, 0.15);
INSERT INTO `order_items` VALUES (10790, 56, 38.00, 20, 0.15);
INSERT INTO `order_items` VALUES (10791, 29, 123.79, 14, 0.05);
INSERT INTO `order_items` VALUES (10791, 41, 9.65, 20, 0.05);
INSERT INTO `order_items` VALUES (10792, 2, 19.00, 10, 0.00);
INSERT INTO `order_items` VALUES (10792, 54, 7.45, 3, 0.00);
INSERT INTO `order_items` VALUES (10792, 68, 12.50, 15, 0.00);
INSERT INTO `order_items` VALUES (10793, 41, 9.65, 14, 0.00);
INSERT INTO `order_items` VALUES (10793, 52, 7.00, 8, 0.00);
INSERT INTO `order_items` VALUES (10794, 14, 23.25, 15, 0.20);
INSERT INTO `order_items` VALUES (10794, 54, 7.45, 6, 0.20);
INSERT INTO `order_items` VALUES (10795, 16, 17.45, 65, 0.00);
INSERT INTO `order_items` VALUES (10795, 17, 39.00, 35, 0.25);
INSERT INTO `order_items` VALUES (10796, 26, 31.23, 21, 0.20);
INSERT INTO `order_items` VALUES (10796, 44, 19.45, 10, 0.00);
INSERT INTO `order_items` VALUES (10796, 64, 33.25, 35, 0.20);
INSERT INTO `order_items` VALUES (10796, 69, 36.00, 24, 0.20);
INSERT INTO `order_items` VALUES (10797, 11, 21.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10798, 62, 49.30, 2, 0.00);
INSERT INTO `order_items` VALUES (10798, 72, 34.80, 10, 0.00);
INSERT INTO `order_items` VALUES (10799, 13, 6.00, 20, 0.15);
INSERT INTO `order_items` VALUES (10799, 24, 4.50, 20, 0.15);
INSERT INTO `order_items` VALUES (10799, 59, 55.00, 25, 0.00);
INSERT INTO `order_items` VALUES (10800, 11, 21.00, 50, 0.10);
INSERT INTO `order_items` VALUES (10800, 51, 53.00, 10, 0.10);
INSERT INTO `order_items` VALUES (10800, 54, 7.45, 7, 0.10);
INSERT INTO `order_items` VALUES (10801, 17, 39.00, 40, 0.25);
INSERT INTO `order_items` VALUES (10801, 29, 123.79, 20, 0.25);
INSERT INTO `order_items` VALUES (10802, 30, 25.89, 25, 0.25);
INSERT INTO `order_items` VALUES (10802, 51, 53.00, 30, 0.25);
INSERT INTO `order_items` VALUES (10802, 55, 24.00, 60, 0.25);
INSERT INTO `order_items` VALUES (10802, 62, 49.30, 5, 0.25);
INSERT INTO `order_items` VALUES (10803, 19, 9.20, 24, 0.05);
INSERT INTO `order_items` VALUES (10803, 25, 14.00, 15, 0.05);
INSERT INTO `order_items` VALUES (10803, 59, 55.00, 15, 0.05);
INSERT INTO `order_items` VALUES (10804, 10, 31.00, 36, 0.00);
INSERT INTO `order_items` VALUES (10804, 28, 45.60, 24, 0.00);
INSERT INTO `order_items` VALUES (10804, 49, 20.00, 4, 0.15);
INSERT INTO `order_items` VALUES (10805, 34, 14.00, 10, 0.00);
INSERT INTO `order_items` VALUES (10805, 38, 263.50, 10, 0.00);
INSERT INTO `order_items` VALUES (10806, 2, 19.00, 20, 0.25);
INSERT INTO `order_items` VALUES (10806, 65, 21.05, 2, 0.00);
INSERT INTO `order_items` VALUES (10806, 74, 10.00, 15, 0.25);
INSERT INTO `order_items` VALUES (10807, 40, 18.40, 1, 0.00);
INSERT INTO `order_items` VALUES (10808, 56, 38.00, 20, 0.15);
INSERT INTO `order_items` VALUES (10808, 76, 18.00, 50, 0.15);
INSERT INTO `order_items` VALUES (10809, 52, 7.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10810, 13, 6.00, 7, 0.00);
INSERT INTO `order_items` VALUES (10810, 25, 14.00, 5, 0.00);
INSERT INTO `order_items` VALUES (10810, 70, 15.00, 5, 0.00);
INSERT INTO `order_items` VALUES (10811, 19, 9.20, 15, 0.00);
INSERT INTO `order_items` VALUES (10811, 23, 9.00, 18, 0.00);
INSERT INTO `order_items` VALUES (10811, 40, 18.40, 30, 0.00);
INSERT INTO `order_items` VALUES (10812, 31, 12.50, 16, 0.10);
INSERT INTO `order_items` VALUES (10812, 72, 34.80, 40, 0.10);
INSERT INTO `order_items` VALUES (10812, 77, 13.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10813, 2, 19.00, 12, 0.20);
INSERT INTO `order_items` VALUES (10813, 46, 12.00, 35, 0.00);
INSERT INTO `order_items` VALUES (10814, 41, 9.65, 20, 0.00);
INSERT INTO `order_items` VALUES (10814, 43, 46.00, 20, 0.15);
INSERT INTO `order_items` VALUES (10814, 48, 12.75, 8, 0.15);
INSERT INTO `order_items` VALUES (10814, 61, 28.50, 30, 0.15);
INSERT INTO `order_items` VALUES (10815, 33, 2.50, 16, 0.00);
INSERT INTO `order_items` VALUES (10816, 38, 263.50, 30, 0.05);
INSERT INTO `order_items` VALUES (10816, 62, 49.30, 20, 0.05);
INSERT INTO `order_items` VALUES (10817, 26, 31.23, 40, 0.15);
INSERT INTO `order_items` VALUES (10817, 38, 263.50, 30, 0.00);
INSERT INTO `order_items` VALUES (10817, 40, 18.40, 60, 0.15);
INSERT INTO `order_items` VALUES (10817, 62, 49.30, 25, 0.15);
INSERT INTO `order_items` VALUES (10818, 32, 32.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10818, 41, 9.65, 20, 0.00);
INSERT INTO `order_items` VALUES (10819, 43, 46.00, 7, 0.00);
INSERT INTO `order_items` VALUES (10819, 75, 7.75, 20, 0.00);
INSERT INTO `order_items` VALUES (10820, 56, 38.00, 30, 0.00);
INSERT INTO `order_items` VALUES (10821, 35, 18.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10821, 51, 53.00, 6, 0.00);
INSERT INTO `order_items` VALUES (10822, 62, 49.30, 3, 0.00);
INSERT INTO `order_items` VALUES (10822, 70, 15.00, 6, 0.00);
INSERT INTO `order_items` VALUES (10823, 11, 21.00, 20, 0.10);
INSERT INTO `order_items` VALUES (10823, 57, 19.50, 15, 0.00);
INSERT INTO `order_items` VALUES (10823, 59, 55.00, 40, 0.10);
INSERT INTO `order_items` VALUES (10823, 77, 13.00, 15, 0.10);
INSERT INTO `order_items` VALUES (10824, 41, 9.65, 12, 0.00);
INSERT INTO `order_items` VALUES (10824, 70, 15.00, 9, 0.00);
INSERT INTO `order_items` VALUES (10825, 26, 31.23, 12, 0.00);
INSERT INTO `order_items` VALUES (10825, 53, 32.80, 20, 0.00);
INSERT INTO `order_items` VALUES (10826, 31, 12.50, 35, 0.00);
INSERT INTO `order_items` VALUES (10826, 57, 19.50, 15, 0.00);
INSERT INTO `order_items` VALUES (10827, 10, 31.00, 15, 0.00);
INSERT INTO `order_items` VALUES (10827, 39, 18.00, 21, 0.00);
INSERT INTO `order_items` VALUES (10828, 20, 81.00, 5, 0.00);
INSERT INTO `order_items` VALUES (10828, 38, 263.50, 2, 0.00);
INSERT INTO `order_items` VALUES (10829, 2, 19.00, 10, 0.00);
INSERT INTO `order_items` VALUES (10829, 8, 40.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10829, 13, 6.00, 10, 0.00);
INSERT INTO `order_items` VALUES (10829, 60, 34.00, 21, 0.00);
INSERT INTO `order_items` VALUES (10830, 6, 25.00, 6, 0.00);
INSERT INTO `order_items` VALUES (10830, 39, 18.00, 28, 0.00);
INSERT INTO `order_items` VALUES (10830, 60, 34.00, 30, 0.00);
INSERT INTO `order_items` VALUES (10830, 68, 12.50, 24, 0.00);
INSERT INTO `order_items` VALUES (10831, 19, 9.20, 2, 0.00);
INSERT INTO `order_items` VALUES (10831, 35, 18.00, 8, 0.00);
INSERT INTO `order_items` VALUES (10831, 38, 263.50, 8, 0.00);
INSERT INTO `order_items` VALUES (10831, 43, 46.00, 9, 0.00);
INSERT INTO `order_items` VALUES (10832, 13, 6.00, 3, 0.20);
INSERT INTO `order_items` VALUES (10832, 25, 14.00, 10, 0.20);
INSERT INTO `order_items` VALUES (10832, 44, 19.45, 16, 0.20);
INSERT INTO `order_items` VALUES (10832, 64, 33.25, 3, 0.00);
INSERT INTO `order_items` VALUES (10833, 7, 30.00, 20, 0.10);
INSERT INTO `order_items` VALUES (10833, 31, 12.50, 9, 0.10);
INSERT INTO `order_items` VALUES (10833, 53, 32.80, 9, 0.10);
INSERT INTO `order_items` VALUES (10834, 29, 123.79, 8, 0.05);
INSERT INTO `order_items` VALUES (10834, 30, 25.89, 20, 0.05);
INSERT INTO `order_items` VALUES (10835, 59, 55.00, 15, 0.00);
INSERT INTO `order_items` VALUES (10835, 77, 13.00, 2, 0.20);
INSERT INTO `order_items` VALUES (10836, 22, 21.00, 52, 0.00);
INSERT INTO `order_items` VALUES (10836, 35, 18.00, 6, 0.00);
INSERT INTO `order_items` VALUES (10836, 57, 19.50, 24, 0.00);
INSERT INTO `order_items` VALUES (10836, 60, 34.00, 60, 0.00);
INSERT INTO `order_items` VALUES (10836, 64, 33.25, 30, 0.00);
INSERT INTO `order_items` VALUES (10837, 13, 6.00, 6, 0.00);
INSERT INTO `order_items` VALUES (10837, 40, 18.40, 25, 0.00);
INSERT INTO `order_items` VALUES (10837, 47, 9.50, 40, 0.25);
INSERT INTO `order_items` VALUES (10837, 76, 18.00, 21, 0.25);
INSERT INTO `order_items` VALUES (10838, 1, 18.00, 4, 0.25);
INSERT INTO `order_items` VALUES (10838, 18, 62.50, 25, 0.25);
INSERT INTO `order_items` VALUES (10838, 36, 19.00, 50, 0.25);
INSERT INTO `order_items` VALUES (10839, 58, 13.25, 30, 0.10);
INSERT INTO `order_items` VALUES (10839, 72, 34.80, 15, 0.10);
INSERT INTO `order_items` VALUES (10840, 25, 14.00, 6, 0.20);
INSERT INTO `order_items` VALUES (10840, 39, 18.00, 10, 0.20);
INSERT INTO `order_items` VALUES (10841, 10, 31.00, 16, 0.00);
INSERT INTO `order_items` VALUES (10841, 56, 38.00, 30, 0.00);
INSERT INTO `order_items` VALUES (10841, 59, 55.00, 50, 0.00);
INSERT INTO `order_items` VALUES (10841, 77, 13.00, 15, 0.00);
INSERT INTO `order_items` VALUES (10842, 11, 21.00, 15, 0.00);
INSERT INTO `order_items` VALUES (10842, 43, 46.00, 5, 0.00);
INSERT INTO `order_items` VALUES (10842, 68, 12.50, 20, 0.00);
INSERT INTO `order_items` VALUES (10842, 70, 15.00, 12, 0.00);
INSERT INTO `order_items` VALUES (10843, 51, 53.00, 4, 0.25);
INSERT INTO `order_items` VALUES (10844, 22, 21.00, 35, 0.00);
INSERT INTO `order_items` VALUES (10845, 23, 9.00, 70, 0.10);
INSERT INTO `order_items` VALUES (10845, 35, 18.00, 25, 0.10);
INSERT INTO `order_items` VALUES (10845, 42, 14.00, 42, 0.10);
INSERT INTO `order_items` VALUES (10845, 58, 13.25, 60, 0.10);
INSERT INTO `order_items` VALUES (10845, 64, 33.25, 48, 0.00);
INSERT INTO `order_items` VALUES (10846, 4, 22.00, 21, 0.00);
INSERT INTO `order_items` VALUES (10846, 70, 15.00, 30, 0.00);
INSERT INTO `order_items` VALUES (10846, 74, 10.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10847, 1, 18.00, 80, 0.20);
INSERT INTO `order_items` VALUES (10847, 19, 9.20, 12, 0.20);
INSERT INTO `order_items` VALUES (10847, 37, 26.00, 60, 0.20);
INSERT INTO `order_items` VALUES (10847, 45, 9.50, 36, 0.20);
INSERT INTO `order_items` VALUES (10847, 60, 34.00, 45, 0.20);
INSERT INTO `order_items` VALUES (10847, 71, 21.50, 55, 0.20);
INSERT INTO `order_items` VALUES (10848, 5, 21.35, 30, 0.00);
INSERT INTO `order_items` VALUES (10848, 9, 97.00, 3, 0.00);
INSERT INTO `order_items` VALUES (10849, 3, 10.00, 49, 0.00);
INSERT INTO `order_items` VALUES (10849, 26, 31.23, 18, 0.15);
INSERT INTO `order_items` VALUES (10850, 25, 14.00, 20, 0.15);
INSERT INTO `order_items` VALUES (10850, 33, 2.50, 4, 0.15);
INSERT INTO `order_items` VALUES (10850, 70, 15.00, 30, 0.15);
INSERT INTO `order_items` VALUES (10851, 2, 19.00, 5, 0.05);
INSERT INTO `order_items` VALUES (10851, 25, 14.00, 10, 0.05);
INSERT INTO `order_items` VALUES (10851, 57, 19.50, 10, 0.05);
INSERT INTO `order_items` VALUES (10851, 59, 55.00, 42, 0.05);
INSERT INTO `order_items` VALUES (10852, 2, 19.00, 15, 0.00);
INSERT INTO `order_items` VALUES (10852, 17, 39.00, 6, 0.00);
INSERT INTO `order_items` VALUES (10852, 62, 49.30, 50, 0.00);
INSERT INTO `order_items` VALUES (10853, 18, 62.50, 10, 0.00);
INSERT INTO `order_items` VALUES (10854, 10, 31.00, 100, 0.15);
INSERT INTO `order_items` VALUES (10854, 13, 6.00, 65, 0.15);
INSERT INTO `order_items` VALUES (10855, 16, 17.45, 50, 0.00);
INSERT INTO `order_items` VALUES (10855, 31, 12.50, 14, 0.00);
INSERT INTO `order_items` VALUES (10855, 56, 38.00, 24, 0.00);
INSERT INTO `order_items` VALUES (10855, 65, 21.05, 15, 0.15);
INSERT INTO `order_items` VALUES (10856, 2, 19.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10856, 42, 14.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10857, 3, 10.00, 30, 0.00);
INSERT INTO `order_items` VALUES (10857, 26, 31.23, 35, 0.25);
INSERT INTO `order_items` VALUES (10857, 29, 123.79, 10, 0.25);
INSERT INTO `order_items` VALUES (10858, 7, 30.00, 5, 0.00);
INSERT INTO `order_items` VALUES (10858, 27, 43.90, 10, 0.00);
INSERT INTO `order_items` VALUES (10858, 70, 15.00, 4, 0.00);
INSERT INTO `order_items` VALUES (10859, 24, 4.50, 40, 0.25);
INSERT INTO `order_items` VALUES (10859, 54, 7.45, 35, 0.25);
INSERT INTO `order_items` VALUES (10859, 64, 33.25, 30, 0.25);
INSERT INTO `order_items` VALUES (10860, 51, 53.00, 3, 0.00);
INSERT INTO `order_items` VALUES (10860, 76, 18.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10861, 17, 39.00, 42, 0.00);
INSERT INTO `order_items` VALUES (10861, 18, 62.50, 20, 0.00);
INSERT INTO `order_items` VALUES (10861, 21, 10.00, 40, 0.00);
INSERT INTO `order_items` VALUES (10861, 33, 2.50, 35, 0.00);
INSERT INTO `order_items` VALUES (10861, 62, 49.30, 3, 0.00);
INSERT INTO `order_items` VALUES (10862, 11, 21.00, 25, 0.00);
INSERT INTO `order_items` VALUES (10862, 52, 7.00, 8, 0.00);
INSERT INTO `order_items` VALUES (10863, 1, 18.00, 20, 0.15);
INSERT INTO `order_items` VALUES (10863, 58, 13.25, 12, 0.15);
INSERT INTO `order_items` VALUES (10864, 35, 18.00, 4, 0.00);
INSERT INTO `order_items` VALUES (10864, 67, 14.00, 15, 0.00);
INSERT INTO `order_items` VALUES (10865, 38, 263.50, 60, 0.05);
INSERT INTO `order_items` VALUES (10865, 39, 18.00, 80, 0.05);
INSERT INTO `order_items` VALUES (10866, 2, 19.00, 21, 0.25);
INSERT INTO `order_items` VALUES (10866, 24, 4.50, 6, 0.25);
INSERT INTO `order_items` VALUES (10866, 30, 25.89, 40, 0.25);
INSERT INTO `order_items` VALUES (10867, 53, 32.80, 3, 0.00);
INSERT INTO `order_items` VALUES (10868, 26, 31.23, 20, 0.00);
INSERT INTO `order_items` VALUES (10868, 35, 18.00, 30, 0.00);
INSERT INTO `order_items` VALUES (10868, 49, 20.00, 42, 0.10);
INSERT INTO `order_items` VALUES (10869, 1, 18.00, 40, 0.00);
INSERT INTO `order_items` VALUES (10869, 11, 21.00, 10, 0.00);
INSERT INTO `order_items` VALUES (10869, 23, 9.00, 50, 0.00);
INSERT INTO `order_items` VALUES (10869, 68, 12.50, 20, 0.00);
INSERT INTO `order_items` VALUES (10870, 35, 18.00, 3, 0.00);
INSERT INTO `order_items` VALUES (10870, 51, 53.00, 2, 0.00);
INSERT INTO `order_items` VALUES (10871, 6, 25.00, 50, 0.05);
INSERT INTO `order_items` VALUES (10871, 16, 17.45, 12, 0.05);
INSERT INTO `order_items` VALUES (10871, 17, 39.00, 16, 0.05);
INSERT INTO `order_items` VALUES (10872, 55, 24.00, 10, 0.05);
INSERT INTO `order_items` VALUES (10872, 62, 49.30, 20, 0.05);
INSERT INTO `order_items` VALUES (10872, 64, 33.25, 15, 0.05);
INSERT INTO `order_items` VALUES (10872, 65, 21.05, 21, 0.05);
INSERT INTO `order_items` VALUES (10873, 21, 10.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10873, 28, 45.60, 3, 0.00);
INSERT INTO `order_items` VALUES (10874, 10, 31.00, 10, 0.00);
INSERT INTO `order_items` VALUES (10875, 19, 9.20, 25, 0.00);
INSERT INTO `order_items` VALUES (10875, 47, 9.50, 21, 0.10);
INSERT INTO `order_items` VALUES (10875, 49, 20.00, 15, 0.00);
INSERT INTO `order_items` VALUES (10876, 46, 12.00, 21, 0.00);
INSERT INTO `order_items` VALUES (10876, 64, 33.25, 20, 0.00);
INSERT INTO `order_items` VALUES (10877, 16, 17.45, 30, 0.25);
INSERT INTO `order_items` VALUES (10877, 18, 62.50, 25, 0.00);
INSERT INTO `order_items` VALUES (10878, 20, 81.00, 20, 0.05);
INSERT INTO `order_items` VALUES (10879, 40, 18.40, 12, 0.00);
INSERT INTO `order_items` VALUES (10879, 65, 21.05, 10, 0.00);
INSERT INTO `order_items` VALUES (10879, 76, 18.00, 10, 0.00);
INSERT INTO `order_items` VALUES (10880, 23, 9.00, 30, 0.20);
INSERT INTO `order_items` VALUES (10880, 61, 28.50, 30, 0.20);
INSERT INTO `order_items` VALUES (10880, 70, 15.00, 50, 0.20);
INSERT INTO `order_items` VALUES (10881, 73, 15.00, 10, 0.00);
INSERT INTO `order_items` VALUES (10882, 42, 14.00, 25, 0.00);
INSERT INTO `order_items` VALUES (10882, 49, 20.00, 20, 0.15);
INSERT INTO `order_items` VALUES (10882, 54, 7.45, 32, 0.15);
INSERT INTO `order_items` VALUES (10883, 24, 4.50, 8, 0.00);
INSERT INTO `order_items` VALUES (10884, 21, 10.00, 40, 0.05);
INSERT INTO `order_items` VALUES (10884, 56, 38.00, 21, 0.05);
INSERT INTO `order_items` VALUES (10884, 65, 21.05, 12, 0.05);
INSERT INTO `order_items` VALUES (10885, 2, 19.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10885, 24, 4.50, 12, 0.00);
INSERT INTO `order_items` VALUES (10885, 70, 15.00, 30, 0.00);
INSERT INTO `order_items` VALUES (10885, 77, 13.00, 25, 0.00);
INSERT INTO `order_items` VALUES (10886, 10, 31.00, 70, 0.00);
INSERT INTO `order_items` VALUES (10886, 31, 12.50, 35, 0.00);
INSERT INTO `order_items` VALUES (10886, 77, 13.00, 40, 0.00);
INSERT INTO `order_items` VALUES (10887, 25, 14.00, 5, 0.00);
INSERT INTO `order_items` VALUES (10888, 2, 19.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10888, 68, 12.50, 18, 0.00);
INSERT INTO `order_items` VALUES (10889, 11, 21.00, 40, 0.00);
INSERT INTO `order_items` VALUES (10889, 38, 263.50, 40, 0.00);
INSERT INTO `order_items` VALUES (10890, 17, 39.00, 15, 0.00);
INSERT INTO `order_items` VALUES (10890, 34, 14.00, 10, 0.00);
INSERT INTO `order_items` VALUES (10890, 41, 9.65, 14, 0.00);
INSERT INTO `order_items` VALUES (10891, 30, 25.89, 15, 0.05);
INSERT INTO `order_items` VALUES (10892, 59, 55.00, 40, 0.05);
INSERT INTO `order_items` VALUES (10893, 8, 40.00, 30, 0.00);
INSERT INTO `order_items` VALUES (10893, 24, 4.50, 10, 0.00);
INSERT INTO `order_items` VALUES (10893, 29, 123.79, 24, 0.00);
INSERT INTO `order_items` VALUES (10893, 30, 25.89, 35, 0.00);
INSERT INTO `order_items` VALUES (10893, 36, 19.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10894, 13, 6.00, 28, 0.05);
INSERT INTO `order_items` VALUES (10894, 69, 36.00, 50, 0.05);
INSERT INTO `order_items` VALUES (10894, 75, 7.75, 120, 0.05);
INSERT INTO `order_items` VALUES (10895, 24, 4.50, 110, 0.00);
INSERT INTO `order_items` VALUES (10895, 39, 18.00, 45, 0.00);
INSERT INTO `order_items` VALUES (10895, 40, 18.40, 91, 0.00);
INSERT INTO `order_items` VALUES (10895, 60, 34.00, 100, 0.00);
INSERT INTO `order_items` VALUES (10896, 45, 9.50, 15, 0.00);
INSERT INTO `order_items` VALUES (10896, 56, 38.00, 16, 0.00);
INSERT INTO `order_items` VALUES (10897, 29, 123.79, 80, 0.00);
INSERT INTO `order_items` VALUES (10897, 30, 25.89, 36, 0.00);
INSERT INTO `order_items` VALUES (10898, 13, 6.00, 5, 0.00);
INSERT INTO `order_items` VALUES (10899, 39, 18.00, 8, 0.15);
INSERT INTO `order_items` VALUES (10900, 70, 15.00, 3, 0.25);
INSERT INTO `order_items` VALUES (10901, 41, 9.65, 30, 0.00);
INSERT INTO `order_items` VALUES (10901, 71, 21.50, 30, 0.00);
INSERT INTO `order_items` VALUES (10902, 55, 24.00, 30, 0.15);
INSERT INTO `order_items` VALUES (10902, 62, 49.30, 6, 0.15);
INSERT INTO `order_items` VALUES (10903, 13, 6.00, 40, 0.00);
INSERT INTO `order_items` VALUES (10903, 65, 21.05, 21, 0.00);
INSERT INTO `order_items` VALUES (10903, 68, 12.50, 20, 0.00);
INSERT INTO `order_items` VALUES (10904, 58, 13.25, 15, 0.00);
INSERT INTO `order_items` VALUES (10904, 62, 49.30, 35, 0.00);
INSERT INTO `order_items` VALUES (10905, 1, 18.00, 20, 0.05);
INSERT INTO `order_items` VALUES (10906, 61, 28.50, 15, 0.00);
INSERT INTO `order_items` VALUES (10907, 75, 7.75, 14, 0.00);
INSERT INTO `order_items` VALUES (10908, 7, 30.00, 20, 0.05);
INSERT INTO `order_items` VALUES (10908, 52, 7.00, 14, 0.05);
INSERT INTO `order_items` VALUES (10909, 7, 30.00, 12, 0.00);
INSERT INTO `order_items` VALUES (10909, 16, 17.45, 15, 0.00);
INSERT INTO `order_items` VALUES (10909, 41, 9.65, 5, 0.00);
INSERT INTO `order_items` VALUES (10910, 19, 9.20, 12, 0.00);
INSERT INTO `order_items` VALUES (10910, 49, 20.00, 10, 0.00);
INSERT INTO `order_items` VALUES (10910, 61, 28.50, 5, 0.00);
INSERT INTO `order_items` VALUES (10911, 1, 18.00, 10, 0.00);
INSERT INTO `order_items` VALUES (10911, 17, 39.00, 12, 0.00);
INSERT INTO `order_items` VALUES (10911, 67, 14.00, 15, 0.00);
INSERT INTO `order_items` VALUES (10912, 11, 21.00, 40, 0.25);
INSERT INTO `order_items` VALUES (10912, 29, 123.79, 60, 0.25);
INSERT INTO `order_items` VALUES (10913, 4, 22.00, 30, 0.25);
INSERT INTO `order_items` VALUES (10913, 33, 2.50, 40, 0.25);
INSERT INTO `order_items` VALUES (10913, 58, 13.25, 15, 0.00);
INSERT INTO `order_items` VALUES (10914, 71, 21.50, 25, 0.00);
INSERT INTO `order_items` VALUES (10915, 17, 39.00, 10, 0.00);
INSERT INTO `order_items` VALUES (10915, 33, 2.50, 30, 0.00);
INSERT INTO `order_items` VALUES (10915, 54, 7.45, 10, 0.00);
INSERT INTO `order_items` VALUES (10916, 16, 17.45, 6, 0.00);
INSERT INTO `order_items` VALUES (10916, 32, 32.00, 6, 0.00);
INSERT INTO `order_items` VALUES (10916, 57, 19.50, 20, 0.00);
INSERT INTO `order_items` VALUES (10917, 30, 25.89, 1, 0.00);
INSERT INTO `order_items` VALUES (10917, 60, 34.00, 10, 0.00);
INSERT INTO `order_items` VALUES (10918, 1, 18.00, 60, 0.25);
INSERT INTO `order_items` VALUES (10918, 60, 34.00, 25, 0.25);
INSERT INTO `order_items` VALUES (10919, 16, 17.45, 24, 0.00);
INSERT INTO `order_items` VALUES (10919, 25, 14.00, 24, 0.00);
INSERT INTO `order_items` VALUES (10919, 40, 18.40, 20, 0.00);
INSERT INTO `order_items` VALUES (10920, 50, 16.25, 24, 0.00);
INSERT INTO `order_items` VALUES (10921, 35, 18.00, 10, 0.00);
INSERT INTO `order_items` VALUES (10921, 63, 43.90, 40, 0.00);
INSERT INTO `order_items` VALUES (10922, 17, 39.00, 15, 0.00);
INSERT INTO `order_items` VALUES (10922, 24, 4.50, 35, 0.00);
INSERT INTO `order_items` VALUES (10923, 42, 14.00, 10, 0.20);
INSERT INTO `order_items` VALUES (10923, 43, 46.00, 10, 0.20);
INSERT INTO `order_items` VALUES (10923, 67, 14.00, 24, 0.20);
INSERT INTO `order_items` VALUES (10924, 10, 31.00, 20, 0.10);
INSERT INTO `order_items` VALUES (10924, 28, 45.60, 30, 0.10);
INSERT INTO `order_items` VALUES (10924, 75, 7.75, 6, 0.00);
INSERT INTO `order_items` VALUES (10925, 36, 19.00, 25, 0.15);
INSERT INTO `order_items` VALUES (10925, 52, 7.00, 12, 0.15);
INSERT INTO `order_items` VALUES (10926, 11, 21.00, 2, 0.00);
INSERT INTO `order_items` VALUES (10926, 13, 6.00, 10, 0.00);
INSERT INTO `order_items` VALUES (10926, 19, 9.20, 7, 0.00);
INSERT INTO `order_items` VALUES (10926, 72, 34.80, 10, 0.00);
INSERT INTO `order_items` VALUES (10927, 20, 81.00, 5, 0.00);
INSERT INTO `order_items` VALUES (10927, 52, 7.00, 5, 0.00);
INSERT INTO `order_items` VALUES (10927, 76, 18.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10928, 47, 9.50, 5, 0.00);
INSERT INTO `order_items` VALUES (10928, 76, 18.00, 5, 0.00);
INSERT INTO `order_items` VALUES (10929, 21, 10.00, 60, 0.00);
INSERT INTO `order_items` VALUES (10929, 75, 7.75, 49, 0.00);
INSERT INTO `order_items` VALUES (10929, 77, 13.00, 15, 0.00);
INSERT INTO `order_items` VALUES (10930, 21, 10.00, 36, 0.00);
INSERT INTO `order_items` VALUES (10930, 27, 43.90, 25, 0.00);
INSERT INTO `order_items` VALUES (10930, 55, 24.00, 25, 0.20);
INSERT INTO `order_items` VALUES (10930, 58, 13.25, 30, 0.20);
INSERT INTO `order_items` VALUES (10931, 13, 6.00, 42, 0.15);
INSERT INTO `order_items` VALUES (10931, 57, 19.50, 30, 0.00);
INSERT INTO `order_items` VALUES (10932, 16, 17.45, 30, 0.10);
INSERT INTO `order_items` VALUES (10932, 62, 49.30, 14, 0.10);
INSERT INTO `order_items` VALUES (10932, 72, 34.80, 16, 0.00);
INSERT INTO `order_items` VALUES (10932, 75, 7.75, 20, 0.10);
INSERT INTO `order_items` VALUES (10933, 53, 32.80, 2, 0.00);
INSERT INTO `order_items` VALUES (10933, 61, 28.50, 30, 0.00);
INSERT INTO `order_items` VALUES (10934, 6, 25.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10935, 1, 18.00, 21, 0.00);
INSERT INTO `order_items` VALUES (10935, 18, 62.50, 4, 0.25);
INSERT INTO `order_items` VALUES (10935, 23, 9.00, 8, 0.25);
INSERT INTO `order_items` VALUES (10936, 36, 19.00, 30, 0.20);
INSERT INTO `order_items` VALUES (10937, 28, 45.60, 8, 0.00);
INSERT INTO `order_items` VALUES (10937, 34, 14.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10938, 13, 6.00, 20, 0.25);
INSERT INTO `order_items` VALUES (10938, 43, 46.00, 24, 0.25);
INSERT INTO `order_items` VALUES (10938, 60, 34.00, 49, 0.25);
INSERT INTO `order_items` VALUES (10938, 71, 21.50, 35, 0.25);
INSERT INTO `order_items` VALUES (10939, 2, 19.00, 10, 0.15);
INSERT INTO `order_items` VALUES (10939, 67, 14.00, 40, 0.15);
INSERT INTO `order_items` VALUES (10940, 7, 30.00, 8, 0.00);
INSERT INTO `order_items` VALUES (10940, 13, 6.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10941, 31, 12.50, 44, 0.25);
INSERT INTO `order_items` VALUES (10941, 62, 49.30, 30, 0.25);
INSERT INTO `order_items` VALUES (10941, 68, 12.50, 80, 0.25);
INSERT INTO `order_items` VALUES (10941, 72, 34.80, 50, 0.00);
INSERT INTO `order_items` VALUES (10942, 49, 20.00, 28, 0.00);
INSERT INTO `order_items` VALUES (10943, 13, 6.00, 15, 0.00);
INSERT INTO `order_items` VALUES (10943, 22, 21.00, 21, 0.00);
INSERT INTO `order_items` VALUES (10943, 46, 12.00, 15, 0.00);
INSERT INTO `order_items` VALUES (10944, 11, 21.00, 5, 0.25);
INSERT INTO `order_items` VALUES (10944, 44, 19.45, 18, 0.25);
INSERT INTO `order_items` VALUES (10944, 56, 38.00, 18, 0.00);
INSERT INTO `order_items` VALUES (10945, 13, 6.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10945, 31, 12.50, 10, 0.00);
INSERT INTO `order_items` VALUES (10946, 10, 31.00, 25, 0.00);
INSERT INTO `order_items` VALUES (10946, 24, 4.50, 25, 0.00);
INSERT INTO `order_items` VALUES (10946, 77, 13.00, 40, 0.00);
INSERT INTO `order_items` VALUES (10947, 59, 55.00, 4, 0.00);
INSERT INTO `order_items` VALUES (10948, 50, 16.25, 9, 0.00);
INSERT INTO `order_items` VALUES (10948, 51, 53.00, 40, 0.00);
INSERT INTO `order_items` VALUES (10948, 55, 24.00, 4, 0.00);
INSERT INTO `order_items` VALUES (10949, 6, 25.00, 12, 0.00);
INSERT INTO `order_items` VALUES (10949, 10, 31.00, 30, 0.00);
INSERT INTO `order_items` VALUES (10949, 17, 39.00, 6, 0.00);
INSERT INTO `order_items` VALUES (10949, 62, 49.30, 60, 0.00);
INSERT INTO `order_items` VALUES (10950, 4, 22.00, 5, 0.00);
INSERT INTO `order_items` VALUES (10951, 33, 2.50, 15, 0.05);
INSERT INTO `order_items` VALUES (10951, 41, 9.65, 6, 0.05);
INSERT INTO `order_items` VALUES (10951, 75, 7.75, 50, 0.05);
INSERT INTO `order_items` VALUES (10952, 6, 25.00, 16, 0.05);
INSERT INTO `order_items` VALUES (10952, 28, 45.60, 2, 0.00);
INSERT INTO `order_items` VALUES (10953, 20, 81.00, 50, 0.05);
INSERT INTO `order_items` VALUES (10953, 31, 12.50, 50, 0.05);
INSERT INTO `order_items` VALUES (10954, 16, 17.45, 28, 0.15);
INSERT INTO `order_items` VALUES (10954, 31, 12.50, 25, 0.15);
INSERT INTO `order_items` VALUES (10954, 45, 9.50, 30, 0.00);
INSERT INTO `order_items` VALUES (10954, 60, 34.00, 24, 0.15);
INSERT INTO `order_items` VALUES (10955, 75, 7.75, 12, 0.20);
INSERT INTO `order_items` VALUES (10956, 21, 10.00, 12, 0.00);
INSERT INTO `order_items` VALUES (10956, 47, 9.50, 14, 0.00);
INSERT INTO `order_items` VALUES (10956, 51, 53.00, 8, 0.00);
INSERT INTO `order_items` VALUES (10957, 30, 25.89, 30, 0.00);
INSERT INTO `order_items` VALUES (10957, 35, 18.00, 40, 0.00);
INSERT INTO `order_items` VALUES (10957, 64, 33.25, 8, 0.00);
INSERT INTO `order_items` VALUES (10958, 5, 21.35, 20, 0.00);
INSERT INTO `order_items` VALUES (10958, 7, 30.00, 6, 0.00);
INSERT INTO `order_items` VALUES (10958, 72, 34.80, 5, 0.00);
INSERT INTO `order_items` VALUES (10959, 75, 7.75, 20, 0.15);
INSERT INTO `order_items` VALUES (10960, 24, 4.50, 10, 0.25);
INSERT INTO `order_items` VALUES (10960, 41, 9.65, 24, 0.00);
INSERT INTO `order_items` VALUES (10961, 52, 7.00, 6, 0.05);
INSERT INTO `order_items` VALUES (10961, 76, 18.00, 60, 0.00);
INSERT INTO `order_items` VALUES (10962, 7, 30.00, 45, 0.00);
INSERT INTO `order_items` VALUES (10962, 13, 6.00, 77, 0.00);
INSERT INTO `order_items` VALUES (10962, 53, 32.80, 20, 0.00);
INSERT INTO `order_items` VALUES (10962, 69, 36.00, 9, 0.00);
INSERT INTO `order_items` VALUES (10962, 76, 18.00, 44, 0.00);
INSERT INTO `order_items` VALUES (10963, 60, 34.00, 2, 0.15);
INSERT INTO `order_items` VALUES (10964, 18, 62.50, 6, 0.00);
INSERT INTO `order_items` VALUES (10964, 38, 263.50, 5, 0.00);
INSERT INTO `order_items` VALUES (10964, 69, 36.00, 10, 0.00);
INSERT INTO `order_items` VALUES (10965, 51, 53.00, 16, 0.00);
INSERT INTO `order_items` VALUES (10966, 37, 26.00, 8, 0.00);
INSERT INTO `order_items` VALUES (10966, 56, 38.00, 12, 0.15);
INSERT INTO `order_items` VALUES (10966, 62, 49.30, 12, 0.15);
INSERT INTO `order_items` VALUES (10967, 19, 9.20, 12, 0.00);
INSERT INTO `order_items` VALUES (10967, 49, 20.00, 40, 0.00);
INSERT INTO `order_items` VALUES (10968, 12, 38.00, 30, 0.00);
INSERT INTO `order_items` VALUES (10968, 24, 4.50, 30, 0.00);
INSERT INTO `order_items` VALUES (10968, 64, 33.25, 4, 0.00);
INSERT INTO `order_items` VALUES (10969, 46, 12.00, 9, 0.00);
INSERT INTO `order_items` VALUES (10970, 52, 7.00, 40, 0.20);
INSERT INTO `order_items` VALUES (10971, 29, 123.79, 14, 0.00);
INSERT INTO `order_items` VALUES (10972, 17, 39.00, 6, 0.00);
INSERT INTO `order_items` VALUES (10972, 33, 2.50, 7, 0.00);
INSERT INTO `order_items` VALUES (10973, 26, 31.23, 5, 0.00);
INSERT INTO `order_items` VALUES (10973, 41, 9.65, 6, 0.00);
INSERT INTO `order_items` VALUES (10973, 75, 7.75, 10, 0.00);
INSERT INTO `order_items` VALUES (10974, 63, 43.90, 10, 0.00);
INSERT INTO `order_items` VALUES (10975, 8, 40.00, 16, 0.00);
INSERT INTO `order_items` VALUES (10975, 75, 7.75, 10, 0.00);
INSERT INTO `order_items` VALUES (10976, 28, 45.60, 20, 0.00);
INSERT INTO `order_items` VALUES (10977, 39, 18.00, 30, 0.00);
INSERT INTO `order_items` VALUES (10977, 47, 9.50, 30, 0.00);
INSERT INTO `order_items` VALUES (10977, 51, 53.00, 10, 0.00);
INSERT INTO `order_items` VALUES (10977, 63, 43.90, 20, 0.00);
INSERT INTO `order_items` VALUES (10978, 8, 40.00, 20, 0.15);
INSERT INTO `order_items` VALUES (10978, 21, 10.00, 40, 0.15);
INSERT INTO `order_items` VALUES (10978, 40, 18.40, 10, 0.00);
INSERT INTO `order_items` VALUES (10978, 44, 19.45, 6, 0.15);
INSERT INTO `order_items` VALUES (10979, 7, 30.00, 18, 0.00);
INSERT INTO `order_items` VALUES (10979, 12, 38.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10979, 24, 4.50, 80, 0.00);
INSERT INTO `order_items` VALUES (10979, 27, 43.90, 30, 0.00);
INSERT INTO `order_items` VALUES (10979, 31, 12.50, 24, 0.00);
INSERT INTO `order_items` VALUES (10979, 63, 43.90, 35, 0.00);
INSERT INTO `order_items` VALUES (10980, 75, 7.75, 40, 0.20);
INSERT INTO `order_items` VALUES (10981, 38, 263.50, 60, 0.00);
INSERT INTO `order_items` VALUES (10982, 7, 30.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10982, 43, 46.00, 9, 0.00);
INSERT INTO `order_items` VALUES (10983, 13, 6.00, 84, 0.15);
INSERT INTO `order_items` VALUES (10983, 57, 19.50, 15, 0.00);
INSERT INTO `order_items` VALUES (10984, 16, 17.45, 55, 0.00);
INSERT INTO `order_items` VALUES (10984, 24, 4.50, 20, 0.00);
INSERT INTO `order_items` VALUES (10984, 36, 19.00, 40, 0.00);
INSERT INTO `order_items` VALUES (10985, 16, 17.45, 36, 0.10);
INSERT INTO `order_items` VALUES (10985, 18, 62.50, 8, 0.10);
INSERT INTO `order_items` VALUES (10985, 32, 32.00, 35, 0.10);
INSERT INTO `order_items` VALUES (10986, 11, 21.00, 30, 0.00);
INSERT INTO `order_items` VALUES (10986, 20, 81.00, 15, 0.00);
INSERT INTO `order_items` VALUES (10986, 76, 18.00, 10, 0.00);
INSERT INTO `order_items` VALUES (10986, 77, 13.00, 15, 0.00);
INSERT INTO `order_items` VALUES (10987, 7, 30.00, 60, 0.00);
INSERT INTO `order_items` VALUES (10987, 43, 46.00, 6, 0.00);
INSERT INTO `order_items` VALUES (10987, 72, 34.80, 20, 0.00);
INSERT INTO `order_items` VALUES (10988, 7, 30.00, 60, 0.00);
INSERT INTO `order_items` VALUES (10988, 62, 49.30, 40, 0.10);
INSERT INTO `order_items` VALUES (10989, 6, 25.00, 40, 0.00);
INSERT INTO `order_items` VALUES (10989, 11, 21.00, 15, 0.00);
INSERT INTO `order_items` VALUES (10989, 41, 9.65, 4, 0.00);
INSERT INTO `order_items` VALUES (10990, 21, 10.00, 65, 0.00);
INSERT INTO `order_items` VALUES (10990, 34, 14.00, 60, 0.15);
INSERT INTO `order_items` VALUES (10990, 55, 24.00, 65, 0.15);
INSERT INTO `order_items` VALUES (10990, 61, 28.50, 66, 0.15);
INSERT INTO `order_items` VALUES (10991, 2, 19.00, 50, 0.20);
INSERT INTO `order_items` VALUES (10991, 70, 15.00, 20, 0.20);
INSERT INTO `order_items` VALUES (10991, 76, 18.00, 90, 0.20);
INSERT INTO `order_items` VALUES (10992, 72, 34.80, 2, 0.00);
INSERT INTO `order_items` VALUES (10993, 29, 123.79, 50, 0.25);
INSERT INTO `order_items` VALUES (10993, 41, 9.65, 35, 0.25);
INSERT INTO `order_items` VALUES (10994, 59, 55.00, 18, 0.05);
INSERT INTO `order_items` VALUES (10995, 51, 53.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10995, 60, 34.00, 4, 0.00);
INSERT INTO `order_items` VALUES (10996, 42, 14.00, 40, 0.00);
INSERT INTO `order_items` VALUES (10997, 32, 32.00, 50, 0.00);
INSERT INTO `order_items` VALUES (10997, 46, 12.00, 20, 0.25);
INSERT INTO `order_items` VALUES (10997, 52, 7.00, 20, 0.25);
INSERT INTO `order_items` VALUES (10998, 24, 4.50, 12, 0.00);
INSERT INTO `order_items` VALUES (10998, 61, 28.50, 7, 0.00);
INSERT INTO `order_items` VALUES (10998, 74, 10.00, 20, 0.00);
INSERT INTO `order_items` VALUES (10998, 75, 7.75, 30, 0.00);
INSERT INTO `order_items` VALUES (10999, 41, 9.65, 20, 0.05);
INSERT INTO `order_items` VALUES (10999, 51, 53.00, 15, 0.05);
INSERT INTO `order_items` VALUES (10999, 77, 13.00, 21, 0.05);
INSERT INTO `order_items` VALUES (11000, 4, 22.00, 25, 0.25);
INSERT INTO `order_items` VALUES (11000, 24, 4.50, 30, 0.25);
INSERT INTO `order_items` VALUES (11000, 77, 13.00, 30, 0.00);
INSERT INTO `order_items` VALUES (11001, 7, 30.00, 60, 0.00);
INSERT INTO `order_items` VALUES (11001, 22, 21.00, 25, 0.00);
INSERT INTO `order_items` VALUES (11001, 46, 12.00, 25, 0.00);
INSERT INTO `order_items` VALUES (11001, 55, 24.00, 6, 0.00);
INSERT INTO `order_items` VALUES (11002, 13, 6.00, 56, 0.00);
INSERT INTO `order_items` VALUES (11002, 35, 18.00, 15, 0.15);
INSERT INTO `order_items` VALUES (11002, 42, 14.00, 24, 0.15);
INSERT INTO `order_items` VALUES (11002, 55, 24.00, 40, 0.00);
INSERT INTO `order_items` VALUES (11003, 1, 18.00, 4, 0.00);
INSERT INTO `order_items` VALUES (11003, 40, 18.40, 10, 0.00);
INSERT INTO `order_items` VALUES (11003, 52, 7.00, 10, 0.00);
INSERT INTO `order_items` VALUES (11004, 26, 31.23, 6, 0.00);
INSERT INTO `order_items` VALUES (11004, 76, 18.00, 6, 0.00);
INSERT INTO `order_items` VALUES (11005, 1, 18.00, 2, 0.00);
INSERT INTO `order_items` VALUES (11005, 59, 55.00, 10, 0.00);
INSERT INTO `order_items` VALUES (11006, 1, 18.00, 8, 0.00);
INSERT INTO `order_items` VALUES (11006, 29, 123.79, 2, 0.25);
INSERT INTO `order_items` VALUES (11007, 8, 40.00, 30, 0.00);
INSERT INTO `order_items` VALUES (11007, 29, 123.79, 10, 0.00);
INSERT INTO `order_items` VALUES (11007, 42, 14.00, 14, 0.00);
INSERT INTO `order_items` VALUES (11008, 28, 45.60, 70, 0.05);
INSERT INTO `order_items` VALUES (11008, 34, 14.00, 90, 0.05);
INSERT INTO `order_items` VALUES (11008, 71, 21.50, 21, 0.00);
INSERT INTO `order_items` VALUES (11009, 24, 4.50, 12, 0.00);
INSERT INTO `order_items` VALUES (11009, 36, 19.00, 18, 0.25);
INSERT INTO `order_items` VALUES (11009, 60, 34.00, 9, 0.00);
INSERT INTO `order_items` VALUES (11010, 7, 30.00, 20, 0.00);
INSERT INTO `order_items` VALUES (11010, 24, 4.50, 10, 0.00);
INSERT INTO `order_items` VALUES (11011, 58, 13.25, 40, 0.05);
INSERT INTO `order_items` VALUES (11011, 71, 21.50, 20, 0.00);
INSERT INTO `order_items` VALUES (11012, 19, 9.20, 50, 0.05);
INSERT INTO `order_items` VALUES (11012, 60, 34.00, 36, 0.05);
INSERT INTO `order_items` VALUES (11012, 71, 21.50, 60, 0.05);
INSERT INTO `order_items` VALUES (11013, 23, 9.00, 10, 0.00);
INSERT INTO `order_items` VALUES (11013, 42, 14.00, 4, 0.00);
INSERT INTO `order_items` VALUES (11013, 45, 9.50, 20, 0.00);
INSERT INTO `order_items` VALUES (11013, 68, 12.50, 2, 0.00);
INSERT INTO `order_items` VALUES (11014, 41, 9.65, 28, 0.10);
INSERT INTO `order_items` VALUES (11015, 30, 25.89, 15, 0.00);
INSERT INTO `order_items` VALUES (11015, 77, 13.00, 18, 0.00);
INSERT INTO `order_items` VALUES (11016, 31, 12.50, 15, 0.00);
INSERT INTO `order_items` VALUES (11016, 36, 19.00, 16, 0.00);
INSERT INTO `order_items` VALUES (11017, 3, 10.00, 25, 0.00);
INSERT INTO `order_items` VALUES (11017, 59, 55.00, 110, 0.00);
INSERT INTO `order_items` VALUES (11017, 70, 15.00, 30, 0.00);
INSERT INTO `order_items` VALUES (11018, 12, 38.00, 20, 0.00);
INSERT INTO `order_items` VALUES (11018, 18, 62.50, 10, 0.00);
INSERT INTO `order_items` VALUES (11018, 56, 38.00, 5, 0.00);
INSERT INTO `order_items` VALUES (11019, 46, 12.00, 3, 0.00);
INSERT INTO `order_items` VALUES (11019, 49, 20.00, 2, 0.00);
INSERT INTO `order_items` VALUES (11020, 10, 31.00, 24, 0.15);
INSERT INTO `order_items` VALUES (11021, 2, 19.00, 11, 0.25);
INSERT INTO `order_items` VALUES (11021, 20, 81.00, 15, 0.00);
INSERT INTO `order_items` VALUES (11021, 26, 31.23, 63, 0.00);
INSERT INTO `order_items` VALUES (11021, 51, 53.00, 44, 0.25);
INSERT INTO `order_items` VALUES (11021, 72, 34.80, 35, 0.00);
INSERT INTO `order_items` VALUES (11022, 19, 9.20, 35, 0.00);
INSERT INTO `order_items` VALUES (11022, 69, 36.00, 30, 0.00);
INSERT INTO `order_items` VALUES (11023, 7, 30.00, 4, 0.00);
INSERT INTO `order_items` VALUES (11023, 43, 46.00, 30, 0.00);
INSERT INTO `order_items` VALUES (11024, 26, 31.23, 12, 0.00);
INSERT INTO `order_items` VALUES (11024, 33, 2.50, 30, 0.00);
INSERT INTO `order_items` VALUES (11024, 65, 21.05, 21, 0.00);
INSERT INTO `order_items` VALUES (11024, 71, 21.50, 50, 0.00);
INSERT INTO `order_items` VALUES (11025, 1, 18.00, 10, 0.10);
INSERT INTO `order_items` VALUES (11025, 13, 6.00, 20, 0.10);
INSERT INTO `order_items` VALUES (11026, 18, 62.50, 8, 0.00);
INSERT INTO `order_items` VALUES (11026, 51, 53.00, 10, 0.00);
INSERT INTO `order_items` VALUES (11027, 24, 4.50, 30, 0.25);
INSERT INTO `order_items` VALUES (11027, 62, 49.30, 21, 0.25);
INSERT INTO `order_items` VALUES (11028, 55, 24.00, 35, 0.00);
INSERT INTO `order_items` VALUES (11028, 59, 55.00, 24, 0.00);
INSERT INTO `order_items` VALUES (11029, 56, 38.00, 20, 0.00);
INSERT INTO `order_items` VALUES (11029, 63, 43.90, 12, 0.00);
INSERT INTO `order_items` VALUES (11030, 2, 19.00, 100, 0.25);
INSERT INTO `order_items` VALUES (11030, 5, 21.35, 70, 0.00);
INSERT INTO `order_items` VALUES (11030, 29, 123.79, 60, 0.25);
INSERT INTO `order_items` VALUES (11030, 59, 55.00, 100, 0.25);
INSERT INTO `order_items` VALUES (11031, 1, 18.00, 45, 0.00);
INSERT INTO `order_items` VALUES (11031, 13, 6.00, 80, 0.00);
INSERT INTO `order_items` VALUES (11031, 24, 4.50, 21, 0.00);
INSERT INTO `order_items` VALUES (11031, 64, 33.25, 20, 0.00);
INSERT INTO `order_items` VALUES (11031, 71, 21.50, 16, 0.00);
INSERT INTO `order_items` VALUES (11032, 36, 19.00, 35, 0.00);
INSERT INTO `order_items` VALUES (11032, 38, 263.50, 25, 0.00);
INSERT INTO `order_items` VALUES (11032, 59, 55.00, 30, 0.00);
INSERT INTO `order_items` VALUES (11033, 53, 32.80, 70, 0.10);
INSERT INTO `order_items` VALUES (11033, 69, 36.00, 36, 0.10);
INSERT INTO `order_items` VALUES (11034, 21, 10.00, 15, 0.10);
INSERT INTO `order_items` VALUES (11034, 44, 19.45, 12, 0.00);
INSERT INTO `order_items` VALUES (11034, 61, 28.50, 6, 0.00);
INSERT INTO `order_items` VALUES (11035, 1, 18.00, 10, 0.00);
INSERT INTO `order_items` VALUES (11035, 35, 18.00, 60, 0.00);
INSERT INTO `order_items` VALUES (11035, 42, 14.00, 30, 0.00);
INSERT INTO `order_items` VALUES (11035, 54, 7.45, 10, 0.00);
INSERT INTO `order_items` VALUES (11036, 13, 6.00, 7, 0.00);
INSERT INTO `order_items` VALUES (11036, 59, 55.00, 30, 0.00);
INSERT INTO `order_items` VALUES (11037, 70, 15.00, 4, 0.00);
INSERT INTO `order_items` VALUES (11038, 40, 18.40, 5, 0.20);
INSERT INTO `order_items` VALUES (11038, 52, 7.00, 2, 0.00);
INSERT INTO `order_items` VALUES (11038, 71, 21.50, 30, 0.00);
INSERT INTO `order_items` VALUES (11039, 28, 45.60, 20, 0.00);
INSERT INTO `order_items` VALUES (11039, 35, 18.00, 24, 0.00);
INSERT INTO `order_items` VALUES (11039, 49, 20.00, 60, 0.00);
INSERT INTO `order_items` VALUES (11039, 57, 19.50, 28, 0.00);
INSERT INTO `order_items` VALUES (11040, 21, 10.00, 20, 0.00);
INSERT INTO `order_items` VALUES (11041, 2, 19.00, 30, 0.20);
INSERT INTO `order_items` VALUES (11041, 63, 43.90, 30, 0.00);
INSERT INTO `order_items` VALUES (11042, 44, 19.45, 15, 0.00);
INSERT INTO `order_items` VALUES (11042, 61, 28.50, 4, 0.00);
INSERT INTO `order_items` VALUES (11043, 11, 21.00, 10, 0.00);
INSERT INTO `order_items` VALUES (11044, 62, 49.30, 12, 0.00);
INSERT INTO `order_items` VALUES (11045, 33, 2.50, 15, 0.00);
INSERT INTO `order_items` VALUES (11045, 51, 53.00, 24, 0.00);
INSERT INTO `order_items` VALUES (11046, 12, 38.00, 20, 0.05);
INSERT INTO `order_items` VALUES (11046, 32, 32.00, 15, 0.05);
INSERT INTO `order_items` VALUES (11046, 35, 18.00, 18, 0.05);
INSERT INTO `order_items` VALUES (11047, 1, 18.00, 25, 0.25);
INSERT INTO `order_items` VALUES (11047, 5, 21.35, 30, 0.25);
INSERT INTO `order_items` VALUES (11048, 68, 12.50, 42, 0.00);
INSERT INTO `order_items` VALUES (11049, 2, 19.00, 10, 0.20);
INSERT INTO `order_items` VALUES (11049, 12, 38.00, 4, 0.20);
INSERT INTO `order_items` VALUES (11050, 76, 18.00, 50, 0.10);
INSERT INTO `order_items` VALUES (11051, 24, 4.50, 10, 0.20);
INSERT INTO `order_items` VALUES (11052, 43, 46.00, 30, 0.20);
INSERT INTO `order_items` VALUES (11052, 61, 28.50, 10, 0.20);
INSERT INTO `order_items` VALUES (11053, 18, 62.50, 35, 0.20);
INSERT INTO `order_items` VALUES (11053, 32, 32.00, 20, 0.00);
INSERT INTO `order_items` VALUES (11053, 64, 33.25, 25, 0.20);
INSERT INTO `order_items` VALUES (11054, 33, 2.50, 10, 0.00);
INSERT INTO `order_items` VALUES (11054, 67, 14.00, 20, 0.00);
INSERT INTO `order_items` VALUES (11055, 24, 4.50, 15, 0.00);
INSERT INTO `order_items` VALUES (11055, 25, 14.00, 15, 0.00);
INSERT INTO `order_items` VALUES (11055, 51, 53.00, 20, 0.00);
INSERT INTO `order_items` VALUES (11055, 57, 19.50, 20, 0.00);
INSERT INTO `order_items` VALUES (11056, 7, 30.00, 40, 0.00);
INSERT INTO `order_items` VALUES (11056, 55, 24.00, 35, 0.00);
INSERT INTO `order_items` VALUES (11056, 60, 34.00, 50, 0.00);
INSERT INTO `order_items` VALUES (11057, 70, 15.00, 3, 0.00);
INSERT INTO `order_items` VALUES (11058, 21, 10.00, 3, 0.00);
INSERT INTO `order_items` VALUES (11058, 60, 34.00, 21, 0.00);
INSERT INTO `order_items` VALUES (11058, 61, 28.50, 4, 0.00);
INSERT INTO `order_items` VALUES (11059, 13, 6.00, 30, 0.00);
INSERT INTO `order_items` VALUES (11059, 17, 39.00, 12, 0.00);
INSERT INTO `order_items` VALUES (11059, 60, 34.00, 35, 0.00);
INSERT INTO `order_items` VALUES (11060, 60, 34.00, 4, 0.00);
INSERT INTO `order_items` VALUES (11060, 77, 13.00, 10, 0.00);
INSERT INTO `order_items` VALUES (11061, 60, 34.00, 15, 0.00);
INSERT INTO `order_items` VALUES (11062, 53, 32.80, 10, 0.20);
INSERT INTO `order_items` VALUES (11062, 70, 15.00, 12, 0.20);
INSERT INTO `order_items` VALUES (11063, 34, 14.00, 30, 0.00);
INSERT INTO `order_items` VALUES (11063, 40, 18.40, 40, 0.10);
INSERT INTO `order_items` VALUES (11063, 41, 9.65, 30, 0.10);
INSERT INTO `order_items` VALUES (11064, 17, 39.00, 77, 0.10);
INSERT INTO `order_items` VALUES (11064, 41, 9.65, 12, 0.00);
INSERT INTO `order_items` VALUES (11064, 53, 32.80, 25, 0.10);
INSERT INTO `order_items` VALUES (11064, 55, 24.00, 4, 0.10);
INSERT INTO `order_items` VALUES (11064, 68, 12.50, 55, 0.00);
INSERT INTO `order_items` VALUES (11065, 30, 25.89, 4, 0.25);
INSERT INTO `order_items` VALUES (11065, 54, 7.45, 20, 0.25);
INSERT INTO `order_items` VALUES (11066, 16, 17.45, 3, 0.00);
INSERT INTO `order_items` VALUES (11066, 19, 9.20, 42, 0.00);
INSERT INTO `order_items` VALUES (11066, 34, 14.00, 35, 0.00);
INSERT INTO `order_items` VALUES (11067, 41, 9.65, 9, 0.00);
INSERT INTO `order_items` VALUES (11068, 28, 45.60, 8, 0.15);
INSERT INTO `order_items` VALUES (11068, 43, 46.00, 36, 0.15);
INSERT INTO `order_items` VALUES (11068, 77, 13.00, 28, 0.15);
INSERT INTO `order_items` VALUES (11069, 39, 18.00, 20, 0.00);
INSERT INTO `order_items` VALUES (11070, 1, 18.00, 40, 0.15);
INSERT INTO `order_items` VALUES (11070, 2, 19.00, 20, 0.15);
INSERT INTO `order_items` VALUES (11070, 16, 17.45, 30, 0.15);
INSERT INTO `order_items` VALUES (11070, 31, 12.50, 20, 0.00);
INSERT INTO `order_items` VALUES (11071, 7, 30.00, 15, 0.05);
INSERT INTO `order_items` VALUES (11071, 13, 6.00, 10, 0.05);
INSERT INTO `order_items` VALUES (11072, 2, 19.00, 8, 0.00);
INSERT INTO `order_items` VALUES (11072, 41, 9.65, 40, 0.00);
INSERT INTO `order_items` VALUES (11072, 50, 16.25, 22, 0.00);
INSERT INTO `order_items` VALUES (11072, 64, 33.25, 130, 0.00);
INSERT INTO `order_items` VALUES (11073, 11, 21.00, 10, 0.00);
INSERT INTO `order_items` VALUES (11073, 24, 4.50, 20, 0.00);
INSERT INTO `order_items` VALUES (11074, 16, 17.45, 14, 0.05);
INSERT INTO `order_items` VALUES (11075, 2, 19.00, 10, 0.15);
INSERT INTO `order_items` VALUES (11075, 46, 12.00, 30, 0.15);
INSERT INTO `order_items` VALUES (11075, 76, 18.00, 2, 0.15);
INSERT INTO `order_items` VALUES (11076, 6, 25.00, 20, 0.25);
INSERT INTO `order_items` VALUES (11076, 14, 23.25, 20, 0.25);
INSERT INTO `order_items` VALUES (11076, 19, 9.20, 10, 0.25);
INSERT INTO `order_items` VALUES (11077, 2, 19.00, 24, 0.20);
INSERT INTO `order_items` VALUES (11077, 3, 10.00, 4, 0.00);
INSERT INTO `order_items` VALUES (11077, 4, 22.00, 1, 0.00);
INSERT INTO `order_items` VALUES (11077, 6, 25.00, 1, 0.02);
INSERT INTO `order_items` VALUES (11077, 7, 30.00, 1, 0.05);
INSERT INTO `order_items` VALUES (11077, 8, 40.00, 2, 0.10);
INSERT INTO `order_items` VALUES (11077, 10, 31.00, 1, 0.00);
INSERT INTO `order_items` VALUES (11077, 12, 38.00, 2, 0.05);
INSERT INTO `order_items` VALUES (11077, 13, 6.00, 4, 0.00);
INSERT INTO `order_items` VALUES (11077, 14, 23.25, 1, 0.03);
INSERT INTO `order_items` VALUES (11077, 16, 17.45, 2, 0.03);
INSERT INTO `order_items` VALUES (11077, 20, 81.00, 1, 0.04);
INSERT INTO `order_items` VALUES (11077, 23, 9.00, 2, 0.00);
INSERT INTO `order_items` VALUES (11077, 32, 32.00, 1, 0.00);
INSERT INTO `order_items` VALUES (11077, 39, 18.00, 2, 0.05);
INSERT INTO `order_items` VALUES (11077, 41, 9.65, 3, 0.00);
INSERT INTO `order_items` VALUES (11077, 46, 12.00, 3, 0.02);
INSERT INTO `order_items` VALUES (11077, 52, 7.00, 2, 0.00);
INSERT INTO `order_items` VALUES (11077, 55, 24.00, 2, 0.00);
INSERT INTO `order_items` VALUES (11077, 60, 34.00, 2, 0.06);
INSERT INTO `order_items` VALUES (11077, 64, 33.25, 2, 0.03);
INSERT INTO `order_items` VALUES (11077, 66, 17.00, 1, 0.00);
INSERT INTO `order_items` VALUES (11077, 73, 15.00, 2, 0.01);
INSERT INTO `order_items` VALUES (11077, 75, 7.75, 4, 0.00);
INSERT INTO `order_items` VALUES (11077, 77, 13.00, 2, 0.00);
COMMIT;

-- ----------------------------
-- Table structure for orders
-- ----------------------------
DROP TABLE IF EXISTS `orders`;
CREATE TABLE `orders` (
  `order_id` int NOT NULL,
  `customer_id` varchar(5) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL,
  `employee_id` int DEFAULT NULL,
  `order_date` datetime DEFAULT NULL,
  `shipped_date` datetime DEFAULT NULL,
  `ship_via` int DEFAULT NULL,
  `freight` decimal(10,2) DEFAULT NULL,
  `ship_address` varchar(60) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL,
  `ship_city` varchar(15) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL,
  `ship_region` varchar(15) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL,
  `ship_postal_code` varchar(10) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL,
  `ship_country` varchar(15) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL,
  PRIMARY KEY (`order_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

-- ----------------------------
-- Records of orders
-- ----------------------------
BEGIN;
INSERT INTO `orders` VALUES (10248, 'VINET', 5, '2016-07-04 00:00:00', '2016-07-16 00:00:00', 3, 32.38, '59 rue de l\'\'Abbaye', 'Reims', NULL, '51100', 'France');
INSERT INTO `orders` VALUES (10249, 'TOMSP', 6, '2016-07-05 00:00:00', '2016-07-10 00:00:00', 1, 11.61, 'Luisenstr. 48', 'Münster', NULL, '44087', 'Germany');
INSERT INTO `orders` VALUES (10250, 'HANAR', 4, '2016-07-08 00:00:00', '2016-07-12 00:00:00', 2, 65.83, 'Rua do Paço-67', 'Rio de Janeiro', 'RJ', '05454-876', 'Brazil');
INSERT INTO `orders` VALUES (10251, 'VICTE', 3, '2016-07-08 00:00:00', '2016-07-15 00:00:00', 1, 41.34, '2-rue du Commerce', 'Lyo', NULL, '69004', 'France');
INSERT INTO `orders` VALUES (10252, 'SUPRD', 4, '2016-07-09 00:00:00', '2016-07-11 00:00:00', 2, 51.30, 'Boulevard Tirou-255', 'Charleroi', NULL, 'B-6000', 'Belgium');
INSERT INTO `orders` VALUES (10253, 'HANAR', 3, '2016-07-10 00:00:00', '2016-07-16 00:00:00', 2, 58.17, 'Rua do Paço-67', 'Rio de Janeiro', 'RJ', '05454-876', 'Brazil');
INSERT INTO `orders` VALUES (10254, 'CHOPS', 5, '2016-07-11 00:00:00', '2016-07-23 00:00:00', 2, 22.98, 'Hauptstr. 31', 'Ber', NULL, '3012', 'Switzerland');
INSERT INTO `orders` VALUES (10255, 'RICSU', 9, '2016-07-12 00:00:00', '2016-07-15 00:00:00', 3, 148.33, 'Starenweg 5', 'Genève', NULL, '1204', 'Switzerland');
INSERT INTO `orders` VALUES (10256, 'WELLI', 3, '2016-07-15 00:00:00', '2016-07-17 00:00:00', 2, 13.97, 'Rua do Mercado-12', 'Resende', 'SP', '08737-363', 'Brazil');
INSERT INTO `orders` VALUES (10257, 'HILAA', 4, '2016-07-16 00:00:00', '2016-07-22 00:00:00', 3, 81.91, 'Carrera 22 con Ave. Carlos Soublette #8-35', 'San Cristóbal', 'Táchira', '5022', 'Venezuela');
INSERT INTO `orders` VALUES (10258, 'ERNSH', 1, '2016-07-17 00:00:00', '2016-07-23 00:00:00', 1, 140.51, 'Kirchgasse 6', 'Graz', NULL, '8010', 'Austria');
INSERT INTO `orders` VALUES (10259, 'CENTC', 4, '2016-07-18 00:00:00', '2016-07-25 00:00:00', 3, 3.25, 'Sierras de Granada 9993', 'México D.F.', NULL, '05022', 'Mexico');
INSERT INTO `orders` VALUES (10260, 'OTTIK', 4, '2016-07-19 00:00:00', '2016-07-29 00:00:00', 1, 55.09, 'Mehrheimerstr. 369', 'Köl', NULL, '50739', 'Germany');
INSERT INTO `orders` VALUES (10261, 'QUEDE', 10, '2016-07-19 00:00:00', '2016-07-30 00:00:00', 2, 3.05, 'Rua da Panificadora-12', 'Rio de Janeiro', 'RJ', '02389-673', 'Brazil');
INSERT INTO `orders` VALUES (10262, 'RATTC', 8, '2016-07-22 00:00:00', '2016-07-25 00:00:00', 3, 48.29, '2817 Milton Dr.', 'Albuquerque', 'NM', '87110', 'USA');
INSERT INTO `orders` VALUES (10263, 'ERNSH', 9, '2016-07-23 00:00:00', '2016-07-31 00:00:00', 3, 146.06, 'Kirchgasse 6', 'Graz', NULL, '8010', 'Austria');
INSERT INTO `orders` VALUES (10264, 'FOLKO', 6, '2016-07-24 00:00:00', '2016-08-23 00:00:00', 3, 3.67, 'Åkergatan 24', 'Bräcke', NULL, 'S-844 67', 'Sweden');
INSERT INTO `orders` VALUES (10265, 'BLONP', 2, '2016-07-25 00:00:00', '2016-08-12 00:00:00', 1, 55.28, '24-place Kléber', 'Strasbourg', NULL, '67000', 'France');
INSERT INTO `orders` VALUES (10266, 'WARTH', 3, '2016-07-26 00:00:00', '2016-07-31 00:00:00', 3, 25.73, 'Torikatu 38', 'Oulu', NULL, '90110', 'Finland');
INSERT INTO `orders` VALUES (10267, 'FRANK', 4, '2016-07-29 00:00:00', '2016-08-06 00:00:00', 1, 208.58, 'Berliner Platz 43', 'Münche', NULL, '80805', 'Germany');
INSERT INTO `orders` VALUES (10268, 'GROSR', 8, '2016-07-30 00:00:00', '2016-08-02 00:00:00', 3, 66.29, '5ª Ave. Los Palos Grandes', 'Caracas', 'DF', '1081', 'Venezuela');
INSERT INTO `orders` VALUES (10269, 'WHITC', 5, '2016-07-31 00:00:00', '2016-08-09 00:00:00', 1, 4.56, '1029 - 12th Ave. S.', 'Seattle', 'WA', '98124', 'USA');
INSERT INTO `orders` VALUES (10270, 'WARTH', 1, '2016-08-01 00:00:00', '2016-08-02 00:00:00', 1, 136.54, 'Torikatu 38', 'Oulu', NULL, '90110', 'Finland');
INSERT INTO `orders` VALUES (10271, 'SPLIR', 6, '2016-08-01 00:00:00', '2016-08-30 00:00:00', 2, 4.54, 'P.O. Box 555', 'Lander', 'WY', '82520', 'USA');
INSERT INTO `orders` VALUES (10272, 'RATTC', 6, '2016-08-02 00:00:00', '2016-08-06 00:00:00', 2, 98.03, '2817 Milton Dr.', 'Albuquerque', 'NM', '87110', 'USA');
INSERT INTO `orders` VALUES (10273, 'QUICK', 3, '2016-08-05 00:00:00', '2016-08-12 00:00:00', 3, 76.07, 'Taucherstraße 10', 'Cunewalde', NULL, '01307', 'Germany');
INSERT INTO `orders` VALUES (10274, 'VINET', 6, '2016-08-06 00:00:00', '2016-08-16 00:00:00', 1, 6.01, '59 rue de l\'\'Abbaye', 'Reims', NULL, '51100', 'France');
INSERT INTO `orders` VALUES (10275, 'MAGAA', 1, '2016-08-07 00:00:00', '2016-08-09 00:00:00', 1, 26.93, 'Via Ludovico il Moro 22', 'Bergamo', NULL, '24100', 'Italy');
INSERT INTO `orders` VALUES (10276, 'TORTU', 8, '2016-08-08 00:00:00', '2016-08-14 00:00:00', 3, 13.84, 'Avda. Azteca 123', 'México D.F.', NULL, '05033', 'Mexico');
INSERT INTO `orders` VALUES (10277, 'MORGK', 2, '2016-08-09 00:00:00', '2016-08-13 00:00:00', 3, 125.77, 'Heerstr. 22', 'Leipzig', NULL, '04179', 'Germany');
INSERT INTO `orders` VALUES (10278, 'BERGS', 8, '2016-08-12 00:00:00', '2016-08-16 00:00:00', 2, 92.69, 'Berguvsvägen  8', 'Luleå', NULL, 'S-958 22', 'Sweden');
INSERT INTO `orders` VALUES (10279, 'LEHMS', 8, '2016-08-13 00:00:00', '2016-08-16 00:00:00', 2, 25.83, 'Magazinweg 7', 'Frankfurt a.M.', NULL, '60528', 'Germany');
INSERT INTO `orders` VALUES (10280, 'BERGS', 2, '2016-08-14 00:00:00', '2016-09-12 00:00:00', 1, 8.98, 'Berguvsvägen  8', 'Luleå', NULL, 'S-958 22', 'Sweden');
INSERT INTO `orders` VALUES (10281, 'ROMEY', 4, '2016-08-14 00:00:00', '2016-08-21 00:00:00', 1, 2.94, 'Gran Vía-1', 'Madrid', NULL, '28001', 'Spain');
INSERT INTO `orders` VALUES (10282, 'ROMEY', 4, '2016-08-15 00:00:00', '2016-08-21 00:00:00', 1, 12.69, 'Gran Vía-1', 'Madrid', NULL, '28001', 'Spain');
INSERT INTO `orders` VALUES (10283, 'LILAS', 3, '2016-08-16 00:00:00', '2016-08-23 00:00:00', 3, 84.81, 'Carrera 52 con Ave. Bolívar #65-98 Llano Largo', 'Barquisimeto', 'Lara', '3508', 'Venezuela');
INSERT INTO `orders` VALUES (10284, 'LEHMS', 4, '2016-08-19 00:00:00', '2016-08-27 00:00:00', 1, 76.56, 'Magazinweg 7', 'Frankfurt a.M.', NULL, '60528', 'Germany');
INSERT INTO `orders` VALUES (10285, 'QUICK', 1, '2016-08-20 00:00:00', '2016-08-26 00:00:00', 2, 76.83, 'Taucherstraße 10', 'Cunewalde', NULL, '01307', 'Germany');
INSERT INTO `orders` VALUES (10286, 'QUICK', 8, '2016-08-21 00:00:00', '2016-08-30 00:00:00', 3, 229.24, 'Taucherstraße 10', 'Cunewalde', NULL, '01307', 'Germany');
INSERT INTO `orders` VALUES (10287, 'RICAR', 8, '2016-08-22 00:00:00', '2016-08-28 00:00:00', 3, 12.76, 'Av. Copacabana-267', 'Rio de Janeiro', 'RJ', '02389-890', 'Brazil');
INSERT INTO `orders` VALUES (10288, 'REGGC', 4, '2016-08-23 00:00:00', '2016-09-03 00:00:00', 1, 7.45, 'Strada Provinciale 124', 'Reggio Emilia', NULL, '42100', 'Italy');
INSERT INTO `orders` VALUES (10289, 'BSBEV', 7, '2016-08-26 00:00:00', '2016-08-28 00:00:00', 3, 22.77, 'Fauntleroy Circus', 'Londo', NULL, 'EC2 5NT', 'UK');
INSERT INTO `orders` VALUES (10290, 'COMMI', 8, '2016-08-27 00:00:00', '2016-09-03 00:00:00', 1, 79.70, 'Av. dos Lusíadas-23', 'Sao Paulo', 'SP', '05432-043', 'Brazil');
INSERT INTO `orders` VALUES (10291, 'QUEDE', 6, '2016-08-27 00:00:00', '2016-09-04 00:00:00', 2, 6.40, 'Rua da Panificadora-12', 'Rio de Janeiro', 'RJ', '02389-673', 'Brazil');
INSERT INTO `orders` VALUES (10292, 'TRADH', 1, '2016-08-28 00:00:00', '2016-09-02 00:00:00', 2, 1.35, 'Av. Inês de Castro-414', 'Sao Paulo', 'SP', '05634-030', 'Brazil');
INSERT INTO `orders` VALUES (10293, 'TORTU', 1, '2016-08-29 00:00:00', '2016-09-11 00:00:00', 3, 21.18, 'Avda. Azteca 123', 'México D.F.', NULL, '05033', 'Mexico');
INSERT INTO `orders` VALUES (10294, 'RATTC', 4, '2016-08-30 00:00:00', '2016-09-05 00:00:00', 2, 147.26, '2817 Milton Dr.', 'Albuquerque', 'NM', '87110', 'USA');
INSERT INTO `orders` VALUES (10295, 'VINET', 2, '2016-09-02 00:00:00', '2016-09-10 00:00:00', 2, 1.15, '59 rue de l\'\'Abbaye', 'Reims', NULL, '51100', 'France');
INSERT INTO `orders` VALUES (10296, 'LILAS', 6, '2016-09-03 00:00:00', '2016-09-11 00:00:00', 1, 0.12, 'Carrera 52 con Ave. Bolívar #65-98 Llano Largo', 'Barquisimeto', 'Lara', '3508', 'Venezuela');
INSERT INTO `orders` VALUES (10297, 'BLONP', 5, '2016-09-04 00:00:00', '2016-09-10 00:00:00', 2, 5.74, '24-place Kléber', 'Strasbourg', NULL, '67000', 'France');
INSERT INTO `orders` VALUES (10298, 'HUNGO', 6, '2016-09-05 00:00:00', '2016-09-11 00:00:00', 2, 168.22, '8 Johnstown Road', 'Cork', 'Co. Cork', NULL, 'Ireland');
INSERT INTO `orders` VALUES (10299, 'RICAR', 4, '2016-09-06 00:00:00', '2016-09-13 00:00:00', 2, 29.76, 'Av. Copacabana-267', 'Rio de Janeiro', 'RJ', '02389-890', 'Brazil');
INSERT INTO `orders` VALUES (10300, 'MAGAA', 2, '2016-09-09 00:00:00', '2016-09-18 00:00:00', 2, 17.68, 'Via Ludovico il Moro 22', 'Bergamo', NULL, '24100', 'Italy');
INSERT INTO `orders` VALUES (10301, 'WANDK', 8, '2016-09-09 00:00:00', '2016-09-17 00:00:00', 2, 45.08, 'Adenauerallee 900', 'Stuttgart', NULL, '70563', 'Germany');
INSERT INTO `orders` VALUES (10302, 'SUPRD', 4, '2016-09-10 00:00:00', '2016-10-09 00:00:00', 2, 6.27, 'Boulevard Tirou-255', 'Charleroi', NULL, 'B-6000', 'Belgium');
INSERT INTO `orders` VALUES (10303, 'GODOS', 7, '2016-09-11 00:00:00', '2016-09-18 00:00:00', 2, 107.83, 'C/ Romero-33', 'Sevilla', NULL, '41101', 'Spain');
INSERT INTO `orders` VALUES (10304, 'TORTU', 1, '2016-09-12 00:00:00', '2016-09-17 00:00:00', 2, 63.79, 'Avda. Azteca 123', 'México D.F.', NULL, '05033', 'Mexico');
INSERT INTO `orders` VALUES (10305, 'OLDWO', 8, '2016-09-13 00:00:00', '2016-10-09 00:00:00', 3, 257.62, '2743 Bering St.', 'Anchorage', 'AK', '99508', 'USA');
INSERT INTO `orders` VALUES (10306, 'ROMEY', 1, '2016-09-16 00:00:00', '2016-09-23 00:00:00', 3, 7.56, 'Gran Vía-1', 'Madrid', NULL, '28001', 'Spain');
INSERT INTO `orders` VALUES (10307, 'LONEP', 2, '2016-09-17 00:00:00', '2016-09-25 00:00:00', 2, 0.56, '89 Chiaroscuro Rd.', 'Portland', 'OR', '97219', 'USA');
INSERT INTO `orders` VALUES (10308, 'ANATR', 7, '2016-09-18 00:00:00', '2016-09-24 00:00:00', 3, 1.61, 'Avda. de la Constitución 2222', 'México D.F.', NULL, '05021', 'Mexico');
INSERT INTO `orders` VALUES (10309, 'HUNGO', 3, '2016-09-19 00:00:00', '2016-10-23 00:00:00', 1, 47.30, '8 Johnstown Road', 'Cork', 'Co. Cork', NULL, 'Ireland');
INSERT INTO `orders` VALUES (10310, 'THEBI', 8, '2016-09-20 00:00:00', '2016-09-27 00:00:00', 2, 17.52, '89 Jefferson Way Suite 2', 'Portland', 'OR', '97201', 'USA');
INSERT INTO `orders` VALUES (10311, 'DUMO', 1, '2016-09-20 00:00:00', '2016-09-26 00:00:00', 3, 24.69, '67-rue des Cinquante Otages', 'Nantes', NULL, '44000', 'France');
INSERT INTO `orders` VALUES (10312, 'WANDK', 2, '2016-09-23 00:00:00', '2016-10-03 00:00:00', 2, 40.26, 'Adenauerallee 900', 'Stuttgart', NULL, '70563', 'Germany');
INSERT INTO `orders` VALUES (10313, 'QUICK', 2, '2016-09-24 00:00:00', '2016-10-04 00:00:00', 2, 1.96, 'Taucherstraße 10', 'Cunewalde', NULL, '01307', 'Germany');
INSERT INTO `orders` VALUES (10314, 'RATTC', 1, '2016-09-25 00:00:00', '2016-10-04 00:00:00', 2, 74.16, '2817 Milton Dr.', 'Albuquerque', 'NM', '87110', 'USA');
INSERT INTO `orders` VALUES (10315, 'ISLAT', 4, '2016-09-26 00:00:00', '2016-10-03 00:00:00', 2, 41.76, 'Garden House Crowther Way', 'Cowes', 'Isle of Wight', 'PO31 7PJ', 'UK');
INSERT INTO `orders` VALUES (10316, 'RATTC', 1, '2016-09-27 00:00:00', '2016-10-08 00:00:00', 3, 150.15, '2817 Milton Dr.', 'Albuquerque', 'NM', '87110', 'USA');
INSERT INTO `orders` VALUES (10317, 'LONEP', 6, '2016-09-30 00:00:00', '2016-10-10 00:00:00', 1, 12.69, '89 Chiaroscuro Rd.', 'Portland', 'OR', '97219', 'USA');
INSERT INTO `orders` VALUES (10318, 'ISLAT', 8, '2016-10-01 00:00:00', '2016-10-04 00:00:00', 2, 4.73, 'Garden House Crowther Way', 'Cowes', 'Isle of Wight', 'PO31 7PJ', 'UK');
INSERT INTO `orders` VALUES (10319, 'TORTU', 7, '2016-10-02 00:00:00', '2016-10-11 00:00:00', 3, 64.50, 'Avda. Azteca 123', 'México D.F.', NULL, '05033', 'Mexico');
INSERT INTO `orders` VALUES (10320, 'WARTH', 5, '2016-10-03 00:00:00', '2016-10-18 00:00:00', 3, 34.57, 'Torikatu 38', 'Oulu', NULL, '90110', 'Finland');
INSERT INTO `orders` VALUES (10321, 'ISLAT', 3, '2016-10-03 00:00:00', '2016-10-11 00:00:00', 2, 3.43, 'Garden House Crowther Way', 'Cowes', 'Isle of Wight', 'PO31 7PJ', 'UK');
INSERT INTO `orders` VALUES (10322, 'PERIC', 7, '2016-10-04 00:00:00', '2016-10-23 00:00:00', 3, 0.40, 'Calle Dr. Jorge Cash 321', 'México D.F.', NULL, '05033', 'Mexico');
INSERT INTO `orders` VALUES (10323, 'KOENE', 4, '2016-10-07 00:00:00', '2016-10-14 00:00:00', 1, 4.88, 'Maubelstr. 90', 'Brandenburg', NULL, '14776', 'Germany');
INSERT INTO `orders` VALUES (10324, 'SAVEA', 9, '2016-10-08 00:00:00', '2016-10-10 00:00:00', 1, 214.27, '187 Suffolk Ln.', 'Boise', 'ID', '83720', 'USA');
INSERT INTO `orders` VALUES (10325, 'KOENE', 1, '2016-10-09 00:00:00', '2016-10-14 00:00:00', 3, 64.86, 'Maubelstr. 90', 'Brandenburg', NULL, '14776', 'Germany');
INSERT INTO `orders` VALUES (10326, 'BOLID', 4, '2016-10-10 00:00:00', '2016-10-14 00:00:00', 2, 77.92, 'C/ Araquil-67', 'Madrid', NULL, '28023', 'Spain');
INSERT INTO `orders` VALUES (10327, 'FOLKO', 2, '2016-10-11 00:00:00', '2016-10-14 00:00:00', 1, 63.36, 'Åkergatan 24', 'Bräcke', NULL, 'S-844 67', 'Sweden');
INSERT INTO `orders` VALUES (10328, 'FURIB', 4, '2016-10-14 00:00:00', '2016-10-17 00:00:00', 3, 87.03, 'Jardim das rosas n. 32', 'Lisboa', NULL, '1675', 'Portugal');
INSERT INTO `orders` VALUES (10329, 'SPLIR', 4, '2016-10-15 00:00:00', '2016-10-23 00:00:00', 2, 191.67, 'P.O. Box 555', 'Lander', 'WY', '82520', 'USA');
INSERT INTO `orders` VALUES (10330, 'LILAS', 3, '2016-10-16 00:00:00', '2016-10-28 00:00:00', 1, 12.75, 'Carrera 52 con Ave. Bolívar #65-98 Llano Largo', 'Barquisimeto', 'Lara', '3508', 'Venezuela');
INSERT INTO `orders` VALUES (10331, 'BONAP', 9, '2016-10-16 00:00:00', '2016-10-21 00:00:00', 1, 10.19, '12-rue des Bouchers', 'Marseille', NULL, '13008', 'France');
INSERT INTO `orders` VALUES (10332, 'MEREP', 3, '2016-10-17 00:00:00', '2016-10-21 00:00:00', 2, 52.84, '43 rue St. Laurent', 'Montréal', 'Québec', 'H1J 1C3', 'Canada');
INSERT INTO `orders` VALUES (10333, 'WARTH', 5, '2016-10-18 00:00:00', '2016-10-25 00:00:00', 3, 0.59, 'Torikatu 38', 'Oulu', NULL, '90110', 'Finland');
INSERT INTO `orders` VALUES (10334, 'VICTE', 8, '2016-10-21 00:00:00', '2016-10-28 00:00:00', 2, 8.56, '2-rue du Commerce', 'Lyo', NULL, '69004', 'France');
INSERT INTO `orders` VALUES (10335, 'HUNGO', 7, '2016-10-22 00:00:00', '2016-10-24 00:00:00', 2, 42.11, '8 Johnstown Road', 'Cork', 'Co. Cork', NULL, 'Ireland');
INSERT INTO `orders` VALUES (10336, 'PRINI', 7, '2016-10-23 00:00:00', '2016-10-25 00:00:00', 2, 15.51, 'Estrada da saúde n. 58', 'Lisboa', NULL, '1756', 'Portugal');
INSERT INTO `orders` VALUES (10337, 'FRANK', 4, '2016-10-24 00:00:00', '2016-10-29 00:00:00', 3, 108.26, 'Berliner Platz 43', 'Münche', NULL, '80805', 'Germany');
INSERT INTO `orders` VALUES (10338, 'OLDWO', 4, '2016-10-25 00:00:00', '2016-10-29 00:00:00', 3, 84.21, '2743 Bering St.', 'Anchorage', 'AK', '99508', 'USA');
INSERT INTO `orders` VALUES (10339, 'MEREP', 2, '2016-10-28 00:00:00', '2016-11-04 00:00:00', 2, 15.66, '43 rue St. Laurent', 'Montréal', 'Québec', 'H1J 1C3', 'Canada');
INSERT INTO `orders` VALUES (10340, 'BONAP', 1, '2016-10-29 00:00:00', '2016-11-08 00:00:00', 3, 166.31, '12-rue des Bouchers', 'Marseille', NULL, '13008', 'France');
INSERT INTO `orders` VALUES (10341, 'SIMOB', 7, '2016-10-29 00:00:00', '2016-11-05 00:00:00', 3, 26.78, 'Vinbæltet 34', 'Kobenhav', NULL, '1734', 'Denmark');
INSERT INTO `orders` VALUES (10342, 'FRANK', 4, '2016-10-30 00:00:00', '2016-11-04 00:00:00', 2, 54.83, 'Berliner Platz 43', 'Münche', NULL, '80805', 'Germany');
INSERT INTO `orders` VALUES (10343, 'LEHMS', 4, '2016-10-31 00:00:00', '2016-11-06 00:00:00', 1, 110.37, 'Magazinweg 7', 'Frankfurt a.M.', NULL, '60528', 'Germany');
INSERT INTO `orders` VALUES (10344, 'WHITC', 4, '2016-11-01 00:00:00', '2016-11-05 00:00:00', 2, 23.29, '1029 - 12th Ave. S.', 'Seattle', 'WA', '98124', 'USA');
INSERT INTO `orders` VALUES (10345, 'QUICK', 2, '2016-11-04 00:00:00', '2016-11-11 00:00:00', 2, 249.06, 'Taucherstraße 10', 'Cunewalde', NULL, '01307', 'Germany');
INSERT INTO `orders` VALUES (10346, 'RATTC', 3, '2016-11-05 00:00:00', '2016-11-08 00:00:00', 3, 142.08, '2817 Milton Dr.', 'Albuquerque', 'NM', '87110', 'USA');
INSERT INTO `orders` VALUES (10347, 'FAMIA', 4, '2016-11-06 00:00:00', '2016-11-08 00:00:00', 3, 3.10, 'Rua Orós-92', 'Sao Paulo', 'SP', '05442-030', 'Brazil');
INSERT INTO `orders` VALUES (10348, 'WANDK', 4, '2016-11-07 00:00:00', '2016-11-15 00:00:00', 2, 0.78, 'Adenauerallee 900', 'Stuttgart', NULL, '70563', 'Germany');
INSERT INTO `orders` VALUES (10349, 'SPLIR', 7, '2016-11-08 00:00:00', '2016-11-15 00:00:00', 1, 8.63, 'P.O. Box 555', 'Lander', 'WY', '82520', 'USA');
INSERT INTO `orders` VALUES (10350, 'LAMAI', 6, '2016-11-11 00:00:00', '2016-12-03 00:00:00', 2, 64.19, '1 rue Alsace-Lorraine', 'Toulouse', NULL, '31000', 'France');
INSERT INTO `orders` VALUES (10351, 'ERNSH', 1, '2016-11-11 00:00:00', '2016-11-20 00:00:00', 1, 162.33, 'Kirchgasse 6', 'Graz', NULL, '8010', 'Austria');
INSERT INTO `orders` VALUES (10352, 'FURIB', 3, '2016-11-12 00:00:00', '2016-11-18 00:00:00', 3, 1.30, 'Jardim das rosas n. 32', 'Lisboa', NULL, '1675', 'Portugal');
INSERT INTO `orders` VALUES (10353, 'PICCO', 7, '2016-11-13 00:00:00', '2016-11-25 00:00:00', 3, 360.63, 'Geislweg 14', 'Salzburg', NULL, '5020', 'Austria');
INSERT INTO `orders` VALUES (10354, 'PERIC', 8, '2016-11-14 00:00:00', '2016-11-20 00:00:00', 3, 53.80, 'Calle Dr. Jorge Cash 321', 'México D.F.', NULL, '05033', 'Mexico');
INSERT INTO `orders` VALUES (10355, 'AROUT', 6, '2016-11-15 00:00:00', '2016-11-20 00:00:00', 1, 41.95, 'Brook Farm Stratford St. Mary', 'Colchester', 'Essex', 'CO7 6JX', 'UK');
INSERT INTO `orders` VALUES (10356, 'WANDK', 6, '2016-11-18 00:00:00', '2016-11-27 00:00:00', 2, 36.71, 'Adenauerallee 900', 'Stuttgart', NULL, '70563', 'Germany');
INSERT INTO `orders` VALUES (10357, 'LILAS', 1, '2016-11-19 00:00:00', '2016-12-02 00:00:00', 3, 34.88, 'Carrera 52 con Ave. Bolívar #65-98 Llano Largo', 'Barquisimeto', 'Lara', '3508', 'Venezuela');
INSERT INTO `orders` VALUES (10358, 'LAMAI', 5, '2016-11-20 00:00:00', '2016-11-27 00:00:00', 1, 19.64, '1 rue Alsace-Lorraine', 'Toulouse', NULL, '31000', 'France');
INSERT INTO `orders` VALUES (10359, 'SEVES', 5, '2016-11-21 00:00:00', '2016-11-26 00:00:00', 3, 288.43, '90 Wadhurst Rd.', 'Londo', NULL, 'OX15 4NB', 'UK');
INSERT INTO `orders` VALUES (10360, 'BLONP', 4, '2016-11-22 00:00:00', '2016-12-02 00:00:00', 3, 131.70, '24-place Kléber', 'Strasbourg', NULL, '67000', 'France');
INSERT INTO `orders` VALUES (10361, 'QUICK', 1, '2016-11-22 00:00:00', '2016-12-03 00:00:00', 2, 183.17, 'Taucherstraße 10', 'Cunewalde', NULL, '01307', 'Germany');
INSERT INTO `orders` VALUES (10362, 'BONAP', 3, '2016-11-25 00:00:00', '2016-11-28 00:00:00', 1, 96.04, '12-rue des Bouchers', 'Marseille', NULL, '13008', 'France');
INSERT INTO `orders` VALUES (10363, 'DRACD', 4, '2016-11-26 00:00:00', '2016-12-04 00:00:00', 3, 30.54, 'Walserweg 21', 'Aache', NULL, '52066', 'Germany');
INSERT INTO `orders` VALUES (10364, 'EASTC', 1, '2016-11-26 00:00:00', '2016-12-04 00:00:00', 1, 71.97, '35 King George', 'Londo', NULL, 'WX3 6FW', 'UK');
INSERT INTO `orders` VALUES (10365, 'ANTO', 3, '2016-11-27 00:00:00', '2016-12-02 00:00:00', 2, 22.00, 'Mataderos  2312', 'México D.F.', NULL, '05023', 'Mexico');
INSERT INTO `orders` VALUES (10366, 'GALED', 8, '2016-11-28 00:00:00', '2016-12-30 00:00:00', 2, 10.14, 'Rambla de Cataluña-23', 'Barcelona', NULL, '8022', 'Spain');
INSERT INTO `orders` VALUES (10367, 'VAFFE', 7, '2016-11-28 00:00:00', '2016-12-02 00:00:00', 3, 13.55, 'Smagsloget 45', 'Århus', NULL, '8200', 'Denmark');
INSERT INTO `orders` VALUES (10368, 'ERNSH', 2, '2016-11-29 00:00:00', '2016-12-02 00:00:00', 2, 101.95, 'Kirchgasse 6', 'Graz', NULL, '8010', 'Austria');
INSERT INTO `orders` VALUES (10369, 'SPLIR', 8, '2016-12-02 00:00:00', '2016-12-09 00:00:00', 2, 195.68, 'P.O. Box 555', 'Lander', 'WY', '82520', 'USA');
INSERT INTO `orders` VALUES (10370, 'CHOPS', 6, '2016-12-03 00:00:00', '2016-12-27 00:00:00', 2, 1.17, 'Hauptstr. 31', 'Ber', NULL, '3012', 'Switzerland');
INSERT INTO `orders` VALUES (10371, 'LAMAI', 1, '2016-12-03 00:00:00', '2016-12-24 00:00:00', 1, 0.45, '1 rue Alsace-Lorraine', 'Toulouse', NULL, '31000', 'France');
INSERT INTO `orders` VALUES (10372, 'QUEE', 5, '2016-12-04 00:00:00', '2016-12-09 00:00:00', 2, 890.78, 'Alameda dos Canàrios-891', 'Sao Paulo', 'SP', '05487-020', 'Brazil');
INSERT INTO `orders` VALUES (10373, 'HUNGO', 4, '2016-12-05 00:00:00', '2016-12-11 00:00:00', 3, 124.12, '8 Johnstown Road', 'Cork', 'Co. Cork', NULL, 'Ireland');
INSERT INTO `orders` VALUES (10374, 'WOLZA', 1, '2016-12-05 00:00:00', '2016-12-09 00:00:00', 3, 3.94, 'ul. Filtrowa 68', 'Warszawa', NULL, '01-012', 'Poland');
INSERT INTO `orders` VALUES (10375, 'HUNGC', 3, '2016-12-06 00:00:00', '2016-12-09 00:00:00', 2, 20.12, 'City Center Plaza 516 Main St.', 'Elgi', 'OR', '97827', 'USA');
INSERT INTO `orders` VALUES (10376, 'MEREP', 1, '2016-12-09 00:00:00', '2016-12-13 00:00:00', 2, 20.39, '43 rue St. Laurent', 'Montréal', 'Québec', 'H1J 1C3', 'Canada');
INSERT INTO `orders` VALUES (10377, 'SEVES', 1, '2016-12-09 00:00:00', '2016-12-13 00:00:00', 3, 22.21, '90 Wadhurst Rd.', 'Londo', NULL, 'OX15 4NB', 'UK');
INSERT INTO `orders` VALUES (10378, 'FOLKO', 5, '2016-12-10 00:00:00', '2016-12-19 00:00:00', 3, 5.44, 'Åkergatan 24', 'Bräcke', NULL, 'S-844 67', 'Sweden');
INSERT INTO `orders` VALUES (10379, 'QUEDE', 2, '2016-12-11 00:00:00', '2016-12-13 00:00:00', 1, 45.03, 'Rua da Panificadora-12', 'Rio de Janeiro', 'RJ', '02389-673', 'Brazil');
INSERT INTO `orders` VALUES (10380, 'HUNGO', 8, '2016-12-12 00:00:00', '2017-01-16 00:00:00', 3, 35.03, '8 Johnstown Road', 'Cork', 'Co. Cork', NULL, 'Ireland');
INSERT INTO `orders` VALUES (10381, 'LILAS', 3, '2016-12-12 00:00:00', '2016-12-13 00:00:00', 3, 7.99, 'Carrera 52 con Ave. Bolívar #65-98 Llano Largo', 'Barquisimeto', 'Lara', '3508', 'Venezuela');
INSERT INTO `orders` VALUES (10382, 'ERNSH', 4, '2016-12-13 00:00:00', '2016-12-16 00:00:00', 1, 94.77, 'Kirchgasse 6', 'Graz', NULL, '8010', 'Austria');
INSERT INTO `orders` VALUES (10383, 'AROUT', 8, '2016-12-16 00:00:00', '2016-12-18 00:00:00', 3, 34.24, 'Brook Farm Stratford St. Mary', 'Colchester', 'Essex', 'CO7 6JX', 'UK');
INSERT INTO `orders` VALUES (10384, 'BERGS', 3, '2016-12-16 00:00:00', '2016-12-20 00:00:00', 3, 168.64, 'Berguvsvägen  8', 'Luleå', NULL, 'S-958 22', 'Sweden');
INSERT INTO `orders` VALUES (10385, 'SPLIR', 1, '2016-12-17 00:00:00', '2016-12-23 00:00:00', 2, 30.96, 'P.O. Box 555', 'Lander', 'WY', '82520', 'USA');
INSERT INTO `orders` VALUES (10386, 'FAMIA', 9, '2016-12-18 00:00:00', '2016-12-25 00:00:00', 3, 13.99, 'Rua Orós-92', 'Sao Paulo', 'SP', '05442-030', 'Brazil');
INSERT INTO `orders` VALUES (10387, 'SANTG', 1, '2016-12-18 00:00:00', '2016-12-20 00:00:00', 2, 93.63, 'Erling Skakkes gate 78', 'Staver', NULL, '4110', 'Norway');
INSERT INTO `orders` VALUES (10388, 'SEVES', 2, '2016-12-19 00:00:00', '2016-12-20 00:00:00', 1, 34.86, '90 Wadhurst Rd.', 'Londo', NULL, 'OX15 4NB', 'UK');
INSERT INTO `orders` VALUES (10389, 'BOTTM', 4, '2016-12-20 00:00:00', '2016-12-24 00:00:00', 2, 47.42, '23 Tsawassen Blvd.', 'Tsawasse', 'BC', 'T2F 8M4', 'Canada');
INSERT INTO `orders` VALUES (10390, 'ERNSH', 6, '2016-12-23 00:00:00', '2016-12-26 00:00:00', 1, 126.38, 'Kirchgasse 6', 'Graz', NULL, '8010', 'Austria');
INSERT INTO `orders` VALUES (10391, 'DRACD', 3, '2016-12-23 00:00:00', '2016-12-31 00:00:00', 3, 5.45, 'Walserweg 21', 'Aache', NULL, '52066', 'Germany');
INSERT INTO `orders` VALUES (10392, 'PICCO', 2, '2016-12-24 00:00:00', '2017-01-01 00:00:00', 3, 122.46, 'Geislweg 14', 'Salzburg', NULL, '5020', 'Austria');
INSERT INTO `orders` VALUES (10393, 'SAVEA', 1, '2016-12-25 00:00:00', '2017-01-03 00:00:00', 3, 126.56, '187 Suffolk Ln.', 'Boise', 'ID', '83720', 'USA');
INSERT INTO `orders` VALUES (10394, 'HUNGC', 1, '2016-12-25 00:00:00', '2017-01-03 00:00:00', 3, 30.34, 'City Center Plaza 516 Main St.', 'Elgi', 'OR', '97827', 'USA');
INSERT INTO `orders` VALUES (10395, 'HILAA', 6, '2016-12-26 00:00:00', '2017-01-03 00:00:00', 1, 184.41, 'Carrera 22 con Ave. Carlos Soublette #8-35', 'San Cristóbal', 'Táchira', '5022', 'Venezuela');
INSERT INTO `orders` VALUES (10396, 'FRANK', 1, '2016-12-27 00:00:00', '2017-01-06 00:00:00', 3, 135.35, 'Berliner Platz 43', 'Münche', NULL, '80805', 'Germany');
INSERT INTO `orders` VALUES (10397, 'PRINI', 5, '2016-12-27 00:00:00', '2017-01-02 00:00:00', 1, 60.26, 'Estrada da saúde n. 58', 'Lisboa', NULL, '1756', 'Portugal');
INSERT INTO `orders` VALUES (10398, 'SAVEA', 2, '2016-12-30 00:00:00', '2017-01-09 00:00:00', 3, 89.16, '187 Suffolk Ln.', 'Boise', 'ID', '83720', 'USA');
INSERT INTO `orders` VALUES (10399, 'VAFFE', 8, '2016-12-31 00:00:00', '2017-01-08 00:00:00', 3, 27.36, 'Smagsloget 45', 'Århus', NULL, '8200', 'Denmark');
INSERT INTO `orders` VALUES (10400, 'EASTC', 1, '2017-01-01 00:00:00', '2017-01-16 00:00:00', 3, 83.93, '35 King George', 'Londo', NULL, 'WX3 6FW', 'UK');
INSERT INTO `orders` VALUES (10401, 'RATTC', 1, '2017-01-01 00:00:00', '2017-01-10 00:00:00', 1, 12.51, '2817 Milton Dr.', 'Albuquerque', 'NM', '87110', 'USA');
INSERT INTO `orders` VALUES (10402, 'ERNSH', 8, '2017-01-02 00:00:00', '2017-01-10 00:00:00', 2, 67.88, 'Kirchgasse 6', 'Graz', NULL, '8010', 'Austria');
INSERT INTO `orders` VALUES (10403, 'ERNSH', 4, '2017-01-03 00:00:00', '2017-01-09 00:00:00', 3, 73.79, 'Kirchgasse 6', 'Graz', NULL, '8010', 'Austria');
INSERT INTO `orders` VALUES (10404, 'MAGAA', 2, '2017-01-03 00:00:00', '2017-01-08 00:00:00', 1, 155.97, 'Via Ludovico il Moro 22', 'Bergamo', NULL, '24100', 'Italy');
INSERT INTO `orders` VALUES (10405, 'LINOD', 1, '2017-01-06 00:00:00', '2017-01-22 00:00:00', 1, 34.82, 'Ave. 5 de Mayo Porlamar', 'I. de Margarita', 'Nueva Esparta', '4980', 'Venezuela');
INSERT INTO `orders` VALUES (10406, 'QUEE', 7, '2017-01-07 00:00:00', '2017-01-13 00:00:00', 1, 108.04, 'Alameda dos Canàrios-891', 'Sao Paulo', 'SP', '05487-020', 'Brazil');
INSERT INTO `orders` VALUES (10407, 'OTTIK', 2, '2017-01-07 00:00:00', '2017-01-30 00:00:00', 2, 91.48, 'Mehrheimerstr. 369', 'Köl', NULL, '50739', 'Germany');
INSERT INTO `orders` VALUES (10408, 'FOLIG', 8, '2017-01-08 00:00:00', '2017-01-14 00:00:00', 1, 11.26, '184-chaussée de Tournai', 'Lille', NULL, '59000', 'France');
INSERT INTO `orders` VALUES (10409, 'OCEA', 3, '2017-01-09 00:00:00', '2017-01-14 00:00:00', 1, 29.83, 'Ing. Gustavo Moncada 8585 Piso 20-A', 'Buenos Aires', NULL, '1010', 'Argentina');
INSERT INTO `orders` VALUES (10410, 'BOTTM', 3, '2017-01-10 00:00:00', '2017-01-15 00:00:00', 3, 2.40, '23 Tsawassen Blvd.', 'Tsawasse', 'BC', 'T2F 8M4', 'Canada');
INSERT INTO `orders` VALUES (10411, 'BOTTM', 9, '2017-01-10 00:00:00', '2017-01-21 00:00:00', 3, 23.65, '23 Tsawassen Blvd.', 'Tsawasse', 'BC', 'T2F 8M4', 'Canada');
INSERT INTO `orders` VALUES (10412, 'WARTH', 8, '2017-01-13 00:00:00', '2017-01-15 00:00:00', 2, 3.77, 'Torikatu 38', 'Oulu', NULL, '90110', 'Finland');
INSERT INTO `orders` VALUES (10413, 'LAMAI', 3, '2017-01-14 00:00:00', '2017-01-16 00:00:00', 2, 95.66, '1 rue Alsace-Lorraine', 'Toulouse', NULL, '31000', 'France');
INSERT INTO `orders` VALUES (10414, 'FAMIA', 2, '2017-01-14 00:00:00', '2017-01-17 00:00:00', 3, 21.48, 'Rua Orós-92', 'Sao Paulo', 'SP', '05442-030', 'Brazil');
INSERT INTO `orders` VALUES (10415, 'HUNGC', 3, '2017-01-15 00:00:00', '2017-01-24 00:00:00', 1, 0.20, 'City Center Plaza 516 Main St.', 'Elgi', 'OR', '97827', 'USA');
INSERT INTO `orders` VALUES (10416, 'WARTH', 8, '2017-01-16 00:00:00', '2017-01-27 00:00:00', 3, 22.72, 'Torikatu 38', 'Oulu', NULL, '90110', 'Finland');
INSERT INTO `orders` VALUES (10417, 'SIMOB', 4, '2017-01-16 00:00:00', '2017-01-28 00:00:00', 3, 70.29, 'Vinbæltet 34', 'Kobenhav', NULL, '1734', 'Denmark');
INSERT INTO `orders` VALUES (10418, 'QUICK', 4, '2017-01-17 00:00:00', '2017-01-24 00:00:00', 1, 17.55, 'Taucherstraße 10', 'Cunewalde', NULL, '01307', 'Germany');
INSERT INTO `orders` VALUES (10419, 'RICSU', 4, '2017-01-20 00:00:00', '2017-01-30 00:00:00', 2, 137.35, 'Starenweg 5', 'Genève', NULL, '1204', 'Switzerland');
INSERT INTO `orders` VALUES (10420, 'WELLI', 3, '2017-01-21 00:00:00', '2017-01-27 00:00:00', 1, 44.12, 'Rua do Mercado-12', 'Resende', 'SP', '08737-363', 'Brazil');
INSERT INTO `orders` VALUES (10421, 'QUEDE', 8, '2017-01-21 00:00:00', '2017-01-27 00:00:00', 1, 99.23, 'Rua da Panificadora-12', 'Rio de Janeiro', 'RJ', '02389-673', 'Brazil');
INSERT INTO `orders` VALUES (10422, 'FRANS', 2, '2017-01-22 00:00:00', '2017-01-31 00:00:00', 1, 3.02, 'Via Monte Bianco 34', 'Torino', NULL, '10100', 'Italy');
INSERT INTO `orders` VALUES (10423, 'GOURL', 6, '2017-01-23 00:00:00', '2017-02-24 00:00:00', 3, 24.50, 'Av. Brasil-442', 'Campinas', 'SP', '04876-786', 'Brazil');
INSERT INTO `orders` VALUES (10424, 'MEREP', 7, '2017-01-23 00:00:00', '2017-01-27 00:00:00', 2, 370.61, '43 rue St. Laurent', 'Montréal', 'Québec', 'H1J 1C3', 'Canada');
INSERT INTO `orders` VALUES (10425, 'LAMAI', 6, '2017-01-24 00:00:00', '2017-02-14 00:00:00', 2, 7.93, '1 rue Alsace-Lorraine', 'Toulouse', NULL, '31000', 'France');
INSERT INTO `orders` VALUES (10426, 'GALED', 4, '2017-01-27 00:00:00', '2017-02-06 00:00:00', 1, 18.69, 'Rambla de Cataluña-23', 'Barcelona', NULL, '8022', 'Spain');
INSERT INTO `orders` VALUES (10427, 'PICCO', 4, '2017-01-27 00:00:00', '2017-03-03 00:00:00', 2, 31.29, 'Geislweg 14', 'Salzburg', NULL, '5020', 'Austria');
INSERT INTO `orders` VALUES (10428, 'REGGC', 7, '2017-01-28 00:00:00', '2017-02-04 00:00:00', 1, 11.09, 'Strada Provinciale 124', 'Reggio Emilia', NULL, '42100', 'Italy');
INSERT INTO `orders` VALUES (10429, 'HUNGO', 3, '2017-01-29 00:00:00', '2017-02-07 00:00:00', 2, 56.63, '8 Johnstown Road', 'Cork', 'Co. Cork', NULL, 'Ireland');
INSERT INTO `orders` VALUES (10430, 'ERNSH', 4, '2017-01-30 00:00:00', '2017-02-03 00:00:00', 1, 458.78, 'Kirchgasse 6', 'Graz', NULL, '8010', 'Austria');
INSERT INTO `orders` VALUES (10431, 'BOTTM', 4, '2017-01-30 00:00:00', '2017-02-07 00:00:00', 2, 44.17, '23 Tsawassen Blvd.', 'Tsawasse', 'BC', 'T2F 8M4', 'Canada');
INSERT INTO `orders` VALUES (10432, 'SPLIR', 3, '2017-01-31 00:00:00', '2017-02-07 00:00:00', 2, 4.34, 'P.O. Box 555', 'Lander', 'WY', '82520', 'USA');
INSERT INTO `orders` VALUES (10433, 'PRINI', 3, '2017-02-03 00:00:00', '2017-03-04 00:00:00', 3, 73.83, 'Estrada da saúde n. 58', 'Lisboa', NULL, '1756', 'Portugal');
INSERT INTO `orders` VALUES (10434, 'FOLKO', 3, '2017-02-03 00:00:00', '2017-02-13 00:00:00', 2, 17.92, 'Åkergatan 24', 'Bräcke', NULL, 'S-844 67', 'Sweden');
INSERT INTO `orders` VALUES (10435, 'CONSH', 8, '2017-02-04 00:00:00', '2017-02-07 00:00:00', 2, 9.21, 'Berkeley Gardens 12  Brewery', 'Londo', NULL, 'WX1 6LT', 'UK');
INSERT INTO `orders` VALUES (10436, 'BLONP', 3, '2017-02-05 00:00:00', '2017-02-11 00:00:00', 2, 156.66, '24-place Kléber', 'Strasbourg', NULL, '67000', 'France');
INSERT INTO `orders` VALUES (10437, 'WARTH', 8, '2017-02-05 00:00:00', '2017-02-12 00:00:00', 1, 19.97, 'Torikatu 38', 'Oulu', NULL, '90110', 'Finland');
INSERT INTO `orders` VALUES (10438, 'TOMSP', 3, '2017-02-06 00:00:00', '2017-02-14 00:00:00', 2, 8.24, 'Luisenstr. 48', 'Münster', NULL, '44087', 'Germany');
INSERT INTO `orders` VALUES (10439, 'MEREP', 6, '2017-02-07 00:00:00', '2017-02-10 00:00:00', 3, 4.07, '43 rue St. Laurent', 'Montréal', 'Québec', 'H1J 1C3', 'Canada');
INSERT INTO `orders` VALUES (10440, 'SAVEA', 4, '2017-02-10 00:00:00', '2017-02-28 00:00:00', 2, 86.53, '187 Suffolk Ln.', 'Boise', 'ID', '83720', 'USA');
INSERT INTO `orders` VALUES (10441, 'OLDWO', 3, '2017-02-10 00:00:00', '2017-03-14 00:00:00', 2, 73.02, '2743 Bering St.', 'Anchorage', 'AK', '99508', 'USA');
INSERT INTO `orders` VALUES (10442, 'ERNSH', 3, '2017-02-11 00:00:00', '2017-02-18 00:00:00', 2, 47.94, 'Kirchgasse 6', 'Graz', NULL, '8010', 'Austria');
INSERT INTO `orders` VALUES (10443, 'REGGC', 8, '2017-02-12 00:00:00', '2017-02-14 00:00:00', 1, 13.95, 'Strada Provinciale 124', 'Reggio Emilia', NULL, '42100', 'Italy');
INSERT INTO `orders` VALUES (10444, 'BERGS', 3, '2017-02-12 00:00:00', '2017-02-21 00:00:00', 3, 3.50, 'Berguvsvägen  8', 'Luleå', NULL, 'S-958 22', 'Sweden');
INSERT INTO `orders` VALUES (10445, 'BERGS', 3, '2017-02-13 00:00:00', '2017-02-20 00:00:00', 1, 9.30, 'Berguvsvägen  8', 'Luleå', NULL, 'S-958 22', 'Sweden');
INSERT INTO `orders` VALUES (10446, 'TOMSP', 6, '2017-02-14 00:00:00', '2017-02-19 00:00:00', 1, 14.68, 'Luisenstr. 48', 'Münster', NULL, '44087', 'Germany');
INSERT INTO `orders` VALUES (10447, 'RICAR', 4, '2017-02-14 00:00:00', '2017-03-07 00:00:00', 2, 68.66, 'Av. Copacabana-267', 'Rio de Janeiro', 'RJ', '02389-890', 'Brazil');
INSERT INTO `orders` VALUES (10448, 'RANCH', 4, '2017-02-17 00:00:00', '2017-02-24 00:00:00', 2, 38.82, 'Av. del Libertador 900', 'Buenos Aires', NULL, '1010', 'Argentina');
INSERT INTO `orders` VALUES (10449, 'BLONP', 3, '2017-02-18 00:00:00', '2017-02-27 00:00:00', 2, 53.30, '24-place Kléber', 'Strasbourg', NULL, '67000', 'France');
INSERT INTO `orders` VALUES (10450, 'VICTE', 8, '2017-02-19 00:00:00', '2017-03-11 00:00:00', 2, 7.23, '2-rue du Commerce', 'Lyo', NULL, '69004', 'France');
INSERT INTO `orders` VALUES (10451, 'QUICK', 4, '2017-02-19 00:00:00', '2017-03-12 00:00:00', 3, 189.09, 'Taucherstraße 10', 'Cunewalde', NULL, '01307', 'Germany');
INSERT INTO `orders` VALUES (10452, 'SAVEA', 8, '2017-02-20 00:00:00', '2017-02-26 00:00:00', 1, 140.26, '187 Suffolk Ln.', 'Boise', 'ID', '83720', 'USA');
INSERT INTO `orders` VALUES (10453, 'AROUT', 1, '2017-02-21 00:00:00', '2017-02-26 00:00:00', 2, 25.36, 'Brook Farm Stratford St. Mary', 'Colchester', 'Essex', 'CO7 6JX', 'UK');
INSERT INTO `orders` VALUES (10454, 'LAMAI', 4, '2017-02-21 00:00:00', '2017-02-25 00:00:00', 3, 2.74, '1 rue Alsace-Lorraine', 'Toulouse', NULL, '31000', 'France');
INSERT INTO `orders` VALUES (10455, 'WARTH', 8, '2017-02-24 00:00:00', '2017-03-03 00:00:00', 2, 180.45, 'Torikatu 38', 'Oulu', NULL, '90110', 'Finland');
INSERT INTO `orders` VALUES (10456, 'KOENE', 8, '2017-02-25 00:00:00', '2017-02-28 00:00:00', 2, 8.12, 'Maubelstr. 90', 'Brandenburg', NULL, '14776', 'Germany');
INSERT INTO `orders` VALUES (10457, 'KOENE', 2, '2017-02-25 00:00:00', '2017-03-03 00:00:00', 1, 11.57, 'Maubelstr. 90', 'Brandenburg', NULL, '14776', 'Germany');
INSERT INTO `orders` VALUES (10458, 'SUPRD', 7, '2017-02-26 00:00:00', '2017-03-04 00:00:00', 3, 147.06, 'Boulevard Tirou-255', 'Charleroi', NULL, 'B-6000', 'Belgium');
INSERT INTO `orders` VALUES (10459, 'VICTE', 4, '2017-02-27 00:00:00', '2017-02-28 00:00:00', 2, 25.09, '2-rue du Commerce', 'Lyo', NULL, '69004', 'France');
INSERT INTO `orders` VALUES (10460, 'FOLKO', 8, '2017-02-28 00:00:00', '2017-03-03 00:00:00', 1, 16.27, 'Åkergatan 24', 'Bräcke', NULL, 'S-844 67', 'Sweden');
INSERT INTO `orders` VALUES (10461, 'LILAS', 1, '2017-02-28 00:00:00', '2017-03-05 00:00:00', 3, 148.61, 'Carrera 52 con Ave. Bolívar #65-98 Llano Largo', 'Barquisimeto', 'Lara', '3508', 'Venezuela');
INSERT INTO `orders` VALUES (10462, 'CONSH', 2, '2017-03-03 00:00:00', '2017-03-18 00:00:00', 1, 6.17, 'Berkeley Gardens 12  Brewery', 'Londo', NULL, 'WX1 6LT', 'UK');
INSERT INTO `orders` VALUES (10463, 'SUPRD', 5, '2017-03-04 00:00:00', '2017-03-06 00:00:00', 3, 14.78, 'Boulevard Tirou-255', 'Charleroi', NULL, 'B-6000', 'Belgium');
INSERT INTO `orders` VALUES (10464, 'FURIB', 4, '2017-03-04 00:00:00', '2017-03-14 00:00:00', 2, 89.00, 'Jardim das rosas n. 32', 'Lisboa', NULL, '1675', 'Portugal');
INSERT INTO `orders` VALUES (10465, 'VAFFE', 1, '2017-03-05 00:00:00', '2017-03-14 00:00:00', 3, 145.04, 'Smagsloget 45', 'Århus', NULL, '8200', 'Denmark');
INSERT INTO `orders` VALUES (10466, 'COMMI', 4, '2017-03-06 00:00:00', '2017-03-13 00:00:00', 1, 11.93, 'Av. dos Lusíadas-23', 'Sao Paulo', 'SP', '05432-043', 'Brazil');
INSERT INTO `orders` VALUES (10467, 'MAGAA', 8, '2017-03-06 00:00:00', '2017-03-11 00:00:00', 2, 4.93, 'Via Ludovico il Moro 22', 'Bergamo', NULL, '24100', 'Italy');
INSERT INTO `orders` VALUES (10468, 'KOENE', 3, '2017-03-07 00:00:00', '2017-03-12 00:00:00', 3, 44.12, 'Maubelstr. 90', 'Brandenburg', NULL, '14776', 'Germany');
INSERT INTO `orders` VALUES (10469, 'WHITC', 1, '2017-03-10 00:00:00', '2017-03-14 00:00:00', 1, 60.18, '1029 - 12th Ave. S.', 'Seattle', 'WA', '98124', 'USA');
INSERT INTO `orders` VALUES (10470, 'BONAP', 4, '2017-03-11 00:00:00', '2017-03-14 00:00:00', 2, 64.56, '12-rue des Bouchers', 'Marseille', NULL, '13008', 'France');
INSERT INTO `orders` VALUES (10471, 'BSBEV', 2, '2017-03-11 00:00:00', '2017-03-18 00:00:00', 3, 45.59, 'Fauntleroy Circus', 'Londo', NULL, 'EC2 5NT', 'UK');
INSERT INTO `orders` VALUES (10472, 'SEVES', 8, '2017-03-12 00:00:00', '2017-03-19 00:00:00', 1, 4.20, '90 Wadhurst Rd.', 'Londo', NULL, 'OX15 4NB', 'UK');
INSERT INTO `orders` VALUES (10473, 'ISLAT', 1, '2017-03-13 00:00:00', '2017-03-21 00:00:00', 3, 16.37, 'Garden House Crowther Way', 'Cowes', 'Isle of Wight', 'PO31 7PJ', 'UK');
INSERT INTO `orders` VALUES (10474, 'PERIC', 5, '2017-03-13 00:00:00', '2017-03-21 00:00:00', 2, 83.49, 'Calle Dr. Jorge Cash 321', 'México D.F.', NULL, '05033', 'Mexico');
INSERT INTO `orders` VALUES (10475, 'SUPRD', 9, '2017-03-14 00:00:00', '2017-04-04 00:00:00', 1, 68.52, 'Boulevard Tirou-255', 'Charleroi', NULL, 'B-6000', 'Belgium');
INSERT INTO `orders` VALUES (10476, 'HILAA', 8, '2017-03-17 00:00:00', '2017-03-24 00:00:00', 3, 4.41, 'Carrera 22 con Ave. Carlos Soublette #8-35', 'San Cristóbal', 'Táchira', '5022', 'Venezuela');
INSERT INTO `orders` VALUES (10477, 'PRINI', 5, '2017-03-17 00:00:00', '2017-03-25 00:00:00', 2, 13.02, 'Estrada da saúde n. 58', 'Lisboa', NULL, '1756', 'Portugal');
INSERT INTO `orders` VALUES (10478, 'VICTE', 2, '2017-03-18 00:00:00', '2017-03-26 00:00:00', 3, 4.81, '2-rue du Commerce', 'Lyo', NULL, '69004', 'France');
INSERT INTO `orders` VALUES (10479, 'RATTC', 3, '2017-03-19 00:00:00', '2017-03-21 00:00:00', 3, 708.95, '2817 Milton Dr.', 'Albuquerque', 'NM', '87110', 'USA');
INSERT INTO `orders` VALUES (10480, 'FOLIG', 6, '2017-03-20 00:00:00', '2017-03-24 00:00:00', 2, 1.35, '184-chaussée de Tournai', 'Lille', NULL, '59000', 'France');
INSERT INTO `orders` VALUES (10481, 'RICAR', 8, '2017-03-20 00:00:00', '2017-03-25 00:00:00', 2, 64.33, 'Av. Copacabana-267', 'Rio de Janeiro', 'RJ', '02389-890', 'Brazil');
INSERT INTO `orders` VALUES (10482, 'LAZYK', 1, '2017-03-21 00:00:00', '2017-04-10 00:00:00', 3, 7.48, '12 Orchestra Terrace', 'Walla Walla', 'WA', '99362', 'USA');
INSERT INTO `orders` VALUES (10483, 'WHITC', 7, '2017-03-24 00:00:00', '2017-04-25 00:00:00', 2, 15.28, '1029 - 12th Ave. S.', 'Seattle', 'WA', '98124', 'USA');
INSERT INTO `orders` VALUES (10484, 'BSBEV', 3, '2017-03-24 00:00:00', '2017-04-01 00:00:00', 3, 6.88, 'Fauntleroy Circus', 'Londo', NULL, 'EC2 5NT', 'UK');
INSERT INTO `orders` VALUES (10485, 'LINOD', 4, '2017-03-25 00:00:00', '2017-03-31 00:00:00', 2, 64.45, 'Ave. 5 de Mayo Porlamar', 'I. de Margarita', 'Nueva Esparta', '4980', 'Venezuela');
INSERT INTO `orders` VALUES (10486, 'HILAA', 1, '2017-03-26 00:00:00', '2017-04-02 00:00:00', 2, 30.53, 'Carrera 22 con Ave. Carlos Soublette #8-35', 'San Cristóbal', 'Táchira', '5022', 'Venezuela');
INSERT INTO `orders` VALUES (10487, 'QUEE', 2, '2017-03-26 00:00:00', '2017-03-28 00:00:00', 2, 71.07, 'Alameda dos Canàrios-891', 'Sao Paulo', 'SP', '05487-020', 'Brazil');
INSERT INTO `orders` VALUES (10488, 'FRANK', 8, '2017-03-27 00:00:00', '2017-04-02 00:00:00', 2, 4.93, 'Berliner Platz 43', 'Münche', NULL, '80805', 'Germany');
INSERT INTO `orders` VALUES (10489, 'PICCO', 6, '2017-03-28 00:00:00', '2017-04-09 00:00:00', 2, 5.29, 'Geislweg 14', 'Salzburg', NULL, '5020', 'Austria');
INSERT INTO `orders` VALUES (10490, 'HILAA', 7, '2017-03-31 00:00:00', '2017-04-03 00:00:00', 2, 210.19, 'Carrera 22 con Ave. Carlos Soublette #8-35', 'San Cristóbal', 'Táchira', '5022', 'Venezuela');
INSERT INTO `orders` VALUES (10491, 'FURIB', 8, '2017-03-31 00:00:00', '2017-04-08 00:00:00', 3, 16.96, 'Jardim das rosas n. 32', 'Lisboa', NULL, '1675', 'Portugal');
INSERT INTO `orders` VALUES (10492, 'BOTTM', 3, '2017-04-01 00:00:00', '2017-04-11 00:00:00', 1, 62.89, '23 Tsawassen Blvd.', 'Tsawasse', 'BC', 'T2F 8M4', 'Canada');
INSERT INTO `orders` VALUES (10493, 'LAMAI', 4, '2017-04-02 00:00:00', '2017-04-10 00:00:00', 3, 10.64, '1 rue Alsace-Lorraine', 'Toulouse', NULL, '31000', 'France');
INSERT INTO `orders` VALUES (10494, 'COMMI', 4, '2017-04-02 00:00:00', '2017-04-09 00:00:00', 2, 65.99, 'Av. dos Lusíadas-23', 'Sao Paulo', 'SP', '05432-043', 'Brazil');
INSERT INTO `orders` VALUES (10495, 'LAUGB', 3, '2017-04-03 00:00:00', '2017-04-11 00:00:00', 3, 4.65, '2319 Elm St.', 'Vancouver', 'BC', 'V3F 2K1', 'Canada');
INSERT INTO `orders` VALUES (10496, 'TRADH', 7, '2017-04-04 00:00:00', '2017-04-07 00:00:00', 2, 46.77, 'Av. Inês de Castro-414', 'Sao Paulo', 'SP', '05634-030', 'Brazil');
INSERT INTO `orders` VALUES (10497, 'LEHMS', 7, '2017-04-04 00:00:00', '2017-04-07 00:00:00', 1, 36.21, 'Magazinweg 7', 'Frankfurt a.M.', NULL, '60528', 'Germany');
INSERT INTO `orders` VALUES (10498, 'HILAA', 8, '2017-04-07 00:00:00', '2017-04-11 00:00:00', 2, 29.75, 'Carrera 22 con Ave. Carlos Soublette #8-35', 'San Cristóbal', 'Táchira', '5022', 'Venezuela');
INSERT INTO `orders` VALUES (10499, 'LILAS', 4, '2017-04-08 00:00:00', '2017-04-16 00:00:00', 2, 102.02, 'Carrera 52 con Ave. Bolívar #65-98 Llano Largo', 'Barquisimeto', 'Lara', '3508', 'Venezuela');
INSERT INTO `orders` VALUES (10500, 'LAMAI', 6, '2017-04-09 00:00:00', '2017-04-17 00:00:00', 1, 42.68, '1 rue Alsace-Lorraine', 'Toulouse', NULL, '31000', 'France');
INSERT INTO `orders` VALUES (10501, 'BLAUS', 9, '2017-04-09 00:00:00', '2017-04-16 00:00:00', 3, 8.85, 'Forsterstr. 57', 'Mannheim', NULL, '68306', 'Germany');
INSERT INTO `orders` VALUES (10502, 'PERIC', 2, '2017-04-10 00:00:00', '2017-04-29 00:00:00', 1, 69.32, 'Calle Dr. Jorge Cash 321', 'México D.F.', NULL, '05033', 'Mexico');
INSERT INTO `orders` VALUES (10503, 'HUNGO', 6, '2017-04-11 00:00:00', '2017-04-16 00:00:00', 2, 16.74, '8 Johnstown Road', 'Cork', 'Co. Cork', NULL, 'Ireland');
INSERT INTO `orders` VALUES (10504, 'WHITC', 4, '2017-04-11 00:00:00', '2017-04-18 00:00:00', 3, 59.13, '1029 - 12th Ave. S.', 'Seattle', 'WA', '98124', 'USA');
INSERT INTO `orders` VALUES (10505, 'MEREP', 3, '2017-04-14 00:00:00', '2017-04-21 00:00:00', 3, 7.13, '43 rue St. Laurent', 'Montréal', 'Québec', 'H1J 1C3', 'Canada');
INSERT INTO `orders` VALUES (10506, 'KOENE', 9, '2017-04-15 00:00:00', '2017-05-02 00:00:00', 2, 21.19, 'Maubelstr. 90', 'Brandenburg', NULL, '14776', 'Germany');
INSERT INTO `orders` VALUES (10507, 'ANTO', 7, '2017-04-15 00:00:00', '2017-04-22 00:00:00', 1, 47.45, 'Mataderos  2312', 'México D.F.', NULL, '05023', 'Mexico');
INSERT INTO `orders` VALUES (10508, 'OTTIK', 1, '2017-04-16 00:00:00', '2017-05-13 00:00:00', 2, 4.99, 'Mehrheimerstr. 369', 'Köl', NULL, '50739', 'Germany');
INSERT INTO `orders` VALUES (10509, 'BLAUS', 4, '2017-04-17 00:00:00', '2017-04-29 00:00:00', 1, 0.15, 'Forsterstr. 57', 'Mannheim', NULL, '68306', 'Germany');
INSERT INTO `orders` VALUES (10510, 'SAVEA', 6, '2017-04-18 00:00:00', '2017-04-28 00:00:00', 3, 367.63, '187 Suffolk Ln.', 'Boise', 'ID', '83720', 'USA');
INSERT INTO `orders` VALUES (10511, 'BONAP', 4, '2017-04-18 00:00:00', '2017-04-21 00:00:00', 3, 350.64, '12-rue des Bouchers', 'Marseille', NULL, '13008', 'France');
INSERT INTO `orders` VALUES (10512, 'FAMIA', 7, '2017-04-21 00:00:00', '2017-04-24 00:00:00', 2, 3.53, 'Rua Orós-92', 'Sao Paulo', 'SP', '05442-030', 'Brazil');
INSERT INTO `orders` VALUES (10513, 'WANDK', 7, '2017-04-22 00:00:00', '2017-04-28 00:00:00', 1, 105.65, 'Adenauerallee 900', 'Stuttgart', NULL, '70563', 'Germany');
INSERT INTO `orders` VALUES (10514, 'ERNSH', 3, '2017-04-22 00:00:00', '2017-05-16 00:00:00', 2, 789.95, 'Kirchgasse 6', 'Graz', NULL, '8010', 'Austria');
INSERT INTO `orders` VALUES (10515, 'QUICK', 2, '2017-04-23 00:00:00', '2017-05-23 00:00:00', 1, 204.47, 'Taucherstraße 10', 'Cunewalde', NULL, '01307', 'Germany');
INSERT INTO `orders` VALUES (10516, 'HUNGO', 2, '2017-04-24 00:00:00', '2017-05-01 00:00:00', 3, 62.78, '8 Johnstown Road', 'Cork', 'Co. Cork', NULL, 'Ireland');
INSERT INTO `orders` VALUES (10517, 'NORTS', 3, '2017-04-24 00:00:00', '2017-04-29 00:00:00', 3, 32.07, 'South House 300 Queensbridge', 'Londo', NULL, 'SW7 1RZ', 'UK');
INSERT INTO `orders` VALUES (10518, 'TORTU', 4, '2017-04-25 00:00:00', '2017-05-05 00:00:00', 2, 218.15, 'Avda. Azteca 123', 'México D.F.', NULL, '05033', 'Mexico');
INSERT INTO `orders` VALUES (10519, 'CHOPS', 6, '2017-04-28 00:00:00', '2017-05-01 00:00:00', 3, 91.76, 'Hauptstr. 31', 'Ber', NULL, '3012', 'Switzerland');
INSERT INTO `orders` VALUES (10520, 'SANTG', 7, '2017-04-29 00:00:00', '2017-05-01 00:00:00', 1, 13.37, 'Erling Skakkes gate 78', 'Staver', NULL, '4110', 'Norway');
INSERT INTO `orders` VALUES (10521, 'CACTU', 8, '2017-04-29 00:00:00', '2017-05-02 00:00:00', 2, 17.22, 'Cerrito 333', 'Buenos Aires', NULL, '1010', 'Argentina');
INSERT INTO `orders` VALUES (10522, 'LEHMS', 4, '2017-04-30 00:00:00', '2017-05-06 00:00:00', 1, 45.33, 'Magazinweg 7', 'Frankfurt a.M.', NULL, '60528', 'Germany');
INSERT INTO `orders` VALUES (10523, 'SEVES', 7, '2017-05-01 00:00:00', '2017-05-30 00:00:00', 2, 77.63, '90 Wadhurst Rd.', 'Londo', NULL, 'OX15 4NB', 'UK');
INSERT INTO `orders` VALUES (10524, 'BERGS', 1, '2017-05-01 00:00:00', '2017-05-07 00:00:00', 2, 244.79, 'Berguvsvägen  8', 'Luleå', NULL, 'S-958 22', 'Sweden');
INSERT INTO `orders` VALUES (10525, 'BONAP', 1, '2017-05-02 00:00:00', '2017-05-23 00:00:00', 2, 11.06, '12-rue des Bouchers', 'Marseille', NULL, '13008', 'France');
INSERT INTO `orders` VALUES (10526, 'WARTH', 4, '2017-05-05 00:00:00', '2017-05-15 00:00:00', 2, 58.59, 'Torikatu 38', 'Oulu', NULL, '90110', 'Finland');
INSERT INTO `orders` VALUES (10527, 'QUICK', 7, '2017-05-05 00:00:00', '2017-05-07 00:00:00', 1, 41.90, 'Taucherstraße 10', 'Cunewalde', NULL, '01307', 'Germany');
INSERT INTO `orders` VALUES (10528, 'GREAL', 6, '2017-05-06 00:00:00', '2017-05-09 00:00:00', 2, 3.35, '2732 Baker Blvd.', 'Eugene', 'OR', '97403', 'USA');
INSERT INTO `orders` VALUES (10529, 'MAISD', 5, '2017-05-07 00:00:00', '2017-05-09 00:00:00', 2, 66.69, 'Rue Joseph-Bens 532', 'Bruxelles', NULL, 'B-1180', 'Belgium');
INSERT INTO `orders` VALUES (10530, 'PICCO', 3, '2017-05-08 00:00:00', '2017-05-12 00:00:00', 2, 339.22, 'Geislweg 14', 'Salzburg', NULL, '5020', 'Austria');
INSERT INTO `orders` VALUES (10531, 'OCEA', 7, '2017-05-08 00:00:00', '2017-05-19 00:00:00', 1, 8.12, 'Ing. Gustavo Moncada 8585 Piso 20-A', 'Buenos Aires', NULL, '1010', 'Argentina');
INSERT INTO `orders` VALUES (10532, 'EASTC', 7, '2017-05-09 00:00:00', '2017-05-12 00:00:00', 3, 74.46, '35 King George', 'Londo', NULL, 'WX3 6FW', 'UK');
INSERT INTO `orders` VALUES (10533, 'FOLKO', 8, '2017-05-12 00:00:00', '2017-05-22 00:00:00', 1, 188.04, 'Åkergatan 24', 'Bräcke', NULL, 'S-844 67', 'Sweden');
INSERT INTO `orders` VALUES (10534, 'LEHMS', 8, '2017-05-12 00:00:00', '2017-05-14 00:00:00', 2, 27.94, 'Magazinweg 7', 'Frankfurt a.M.', NULL, '60528', 'Germany');
INSERT INTO `orders` VALUES (10535, 'ANTO', 4, '2017-05-13 00:00:00', '2017-05-21 00:00:00', 1, 15.64, 'Mataderos  2312', 'México D.F.', NULL, '05023', 'Mexico');
INSERT INTO `orders` VALUES (10536, 'LEHMS', 3, '2017-05-14 00:00:00', '2017-06-06 00:00:00', 2, 58.88, 'Magazinweg 7', 'Frankfurt a.M.', NULL, '60528', 'Germany');
INSERT INTO `orders` VALUES (10537, 'RICSU', 1, '2017-05-14 00:00:00', '2017-05-19 00:00:00', 1, 78.85, 'Starenweg 5', 'Genève', NULL, '1204', 'Switzerland');
INSERT INTO `orders` VALUES (10538, 'BSBEV', 9, '2017-05-15 00:00:00', '2017-05-16 00:00:00', 3, 4.87, 'Fauntleroy Circus', 'Londo', NULL, 'EC2 5NT', 'UK');
INSERT INTO `orders` VALUES (10539, 'BSBEV', 6, '2017-05-16 00:00:00', '2017-05-23 00:00:00', 3, 12.36, 'Fauntleroy Circus', 'Londo', NULL, 'EC2 5NT', 'UK');
INSERT INTO `orders` VALUES (10540, 'QUICK', 3, '2017-05-19 00:00:00', '2017-06-13 00:00:00', 3, 1007.64, 'Taucherstraße 10', 'Cunewalde', NULL, '01307', 'Germany');
INSERT INTO `orders` VALUES (10541, 'HANAR', 2, '2017-05-19 00:00:00', '2017-05-29 00:00:00', 1, 68.65, 'Rua do Paço-67', 'Rio de Janeiro', 'RJ', '05454-876', 'Brazil');
INSERT INTO `orders` VALUES (10542, 'KOENE', 1, '2017-05-20 00:00:00', '2017-05-26 00:00:00', 3, 10.95, 'Maubelstr. 90', 'Brandenburg', NULL, '14776', 'Germany');
INSERT INTO `orders` VALUES (10543, 'LILAS', 8, '2017-05-21 00:00:00', '2017-05-23 00:00:00', 2, 48.17, 'Carrera 52 con Ave. Bolívar #65-98 Llano Largo', 'Barquisimeto', 'Lara', '3508', 'Venezuela');
INSERT INTO `orders` VALUES (10544, 'LONEP', 4, '2017-05-21 00:00:00', '2017-05-30 00:00:00', 1, 24.91, '89 Chiaroscuro Rd.', 'Portland', 'OR', '97219', 'USA');
INSERT INTO `orders` VALUES (10545, 'LAZYK', 8, '2017-05-22 00:00:00', '2017-06-26 00:00:00', 2, 11.92, '12 Orchestra Terrace', 'Walla Walla', 'WA', '99362', 'USA');
INSERT INTO `orders` VALUES (10546, 'VICTE', 1, '2017-05-23 00:00:00', '2017-05-27 00:00:00', 3, 194.72, '2-rue du Commerce', 'Lyo', NULL, '69004', 'France');
INSERT INTO `orders` VALUES (10547, 'SEVES', 3, '2017-05-23 00:00:00', '2017-06-02 00:00:00', 2, 178.43, '90 Wadhurst Rd.', 'Londo', NULL, 'OX15 4NB', 'UK');
INSERT INTO `orders` VALUES (10548, 'TOMSP', 3, '2017-05-26 00:00:00', '2017-06-02 00:00:00', 2, 1.43, 'Luisenstr. 48', 'Münster', NULL, '44087', 'Germany');
INSERT INTO `orders` VALUES (10549, 'QUICK', 5, '2017-05-27 00:00:00', '2017-05-30 00:00:00', 1, 171.24, 'Taucherstraße 10', 'Cunewalde', NULL, '01307', 'Germany');
INSERT INTO `orders` VALUES (10550, 'GODOS', 7, '2017-05-28 00:00:00', '2017-06-06 00:00:00', 3, 4.32, 'C/ Romero-33', 'Sevilla', NULL, '41101', 'Spain');
INSERT INTO `orders` VALUES (10551, 'FURIB', 4, '2017-05-28 00:00:00', '2017-06-06 00:00:00', 3, 72.95, 'Jardim das rosas n. 32', 'Lisboa', NULL, '1675', 'Portugal');
INSERT INTO `orders` VALUES (10552, 'HILAA', 2, '2017-05-29 00:00:00', '2017-06-05 00:00:00', 1, 83.22, 'Carrera 22 con Ave. Carlos Soublette #8-35', 'San Cristóbal', 'Táchira', '5022', 'Venezuela');
INSERT INTO `orders` VALUES (10553, 'WARTH', 2, '2017-05-30 00:00:00', '2017-06-03 00:00:00', 2, 149.49, 'Torikatu 38', 'Oulu', NULL, '90110', 'Finland');
INSERT INTO `orders` VALUES (10554, 'OTTIK', 4, '2017-05-30 00:00:00', '2017-06-05 00:00:00', 3, 120.97, 'Mehrheimerstr. 369', 'Köl', NULL, '50739', 'Germany');
INSERT INTO `orders` VALUES (10555, 'SAVEA', 6, '2017-06-02 00:00:00', '2017-06-04 00:00:00', 3, 252.49, '187 Suffolk Ln.', 'Boise', 'ID', '83720', 'USA');
INSERT INTO `orders` VALUES (10556, 'SIMOB', 2, '2017-06-03 00:00:00', '2017-06-13 00:00:00', 1, 9.80, 'Vinbæltet 34', 'Kobenhav', NULL, '1734', 'Denmark');
INSERT INTO `orders` VALUES (10557, 'LEHMS', 9, '2017-06-03 00:00:00', '2017-06-06 00:00:00', 2, 96.72, 'Magazinweg 7', 'Frankfurt a.M.', NULL, '60528', 'Germany');
INSERT INTO `orders` VALUES (10558, 'AROUT', 1, '2017-06-04 00:00:00', '2017-06-10 00:00:00', 2, 72.97, 'Brook Farm Stratford St. Mary', 'Colchester', 'Essex', 'CO7 6JX', 'UK');
INSERT INTO `orders` VALUES (10559, 'BLONP', 6, '2017-06-05 00:00:00', '2017-06-13 00:00:00', 1, 8.05, '24-place Kléber', 'Strasbourg', NULL, '67000', 'France');
INSERT INTO `orders` VALUES (10560, 'FRANK', 8, '2017-06-06 00:00:00', '2017-06-09 00:00:00', 1, 36.65, 'Berliner Platz 43', 'Münche', NULL, '80805', 'Germany');
INSERT INTO `orders` VALUES (10561, 'FOLKO', 2, '2017-06-06 00:00:00', '2017-06-09 00:00:00', 2, 242.21, 'Åkergatan 24', 'Bräcke', NULL, 'S-844 67', 'Sweden');
INSERT INTO `orders` VALUES (10562, 'REGGC', 1, '2017-06-09 00:00:00', '2017-06-12 00:00:00', 1, 22.95, 'Strada Provinciale 124', 'Reggio Emilia', NULL, '42100', 'Italy');
INSERT INTO `orders` VALUES (10563, 'RICAR', 2, '2017-06-10 00:00:00', '2017-06-24 00:00:00', 2, 60.43, 'Av. Copacabana-267', 'Rio de Janeiro', 'RJ', '02389-890', 'Brazil');
INSERT INTO `orders` VALUES (10564, 'RATTC', 4, '2017-06-10 00:00:00', '2017-06-16 00:00:00', 3, 13.75, '2817 Milton Dr.', 'Albuquerque', 'NM', '87110', 'USA');
INSERT INTO `orders` VALUES (10565, 'MEREP', 8, '2017-06-11 00:00:00', '2017-06-18 00:00:00', 2, 7.15, '43 rue St. Laurent', 'Montréal', 'Québec', 'H1J 1C3', 'Canada');
INSERT INTO `orders` VALUES (10566, 'BLONP', 9, '2017-06-12 00:00:00', '2017-06-18 00:00:00', 1, 88.40, '24-place Kléber', 'Strasbourg', NULL, '67000', 'France');
INSERT INTO `orders` VALUES (10567, 'HUNGO', 1, '2017-06-12 00:00:00', '2017-06-17 00:00:00', 1, 33.97, '8 Johnstown Road', 'Cork', 'Co. Cork', NULL, 'Ireland');
INSERT INTO `orders` VALUES (10568, 'GALED', 3, '2017-06-13 00:00:00', '2017-07-09 00:00:00', 3, 6.54, 'Rambla de Cataluña-23', 'Barcelona', NULL, '8022', 'Spain');
INSERT INTO `orders` VALUES (10569, 'RATTC', 5, '2017-06-16 00:00:00', '2017-07-11 00:00:00', 1, 58.98, '2817 Milton Dr.', 'Albuquerque', 'NM', '87110', 'USA');
INSERT INTO `orders` VALUES (10570, 'MEREP', 3, '2017-06-17 00:00:00', '2017-06-19 00:00:00', 3, 188.99, '43 rue St. Laurent', 'Montréal', 'Québec', 'H1J 1C3', 'Canada');
INSERT INTO `orders` VALUES (10571, 'ERNSH', 8, '2017-06-17 00:00:00', '2017-07-04 00:00:00', 3, 26.06, 'Kirchgasse 6', 'Graz', NULL, '8010', 'Austria');
INSERT INTO `orders` VALUES (10572, 'BERGS', 3, '2017-06-18 00:00:00', '2017-06-25 00:00:00', 2, 116.43, 'Berguvsvägen  8', 'Luleå', NULL, 'S-958 22', 'Sweden');
INSERT INTO `orders` VALUES (10573, 'ANTO', 7, '2017-06-19 00:00:00', '2017-06-20 00:00:00', 3, 84.84, 'Mataderos  2312', 'México D.F.', NULL, '05023', 'Mexico');
INSERT INTO `orders` VALUES (10574, 'TRAIH', 4, '2017-06-19 00:00:00', '2017-06-30 00:00:00', 2, 37.60, '722 DaVinci Blvd.', 'Kirkland', 'WA', '98034', 'USA');
INSERT INTO `orders` VALUES (10575, 'MORGK', 5, '2017-06-20 00:00:00', '2017-06-30 00:00:00', 1, 127.34, 'Heerstr. 22', 'Leipzig', NULL, '04179', 'Germany');
INSERT INTO `orders` VALUES (10576, 'TORTU', 3, '2017-06-23 00:00:00', '2017-06-30 00:00:00', 3, 18.56, 'Avda. Azteca 123', 'México D.F.', NULL, '05033', 'Mexico');
INSERT INTO `orders` VALUES (10577, 'TRAIH', 9, '2017-06-23 00:00:00', '2017-06-30 00:00:00', 2, 25.41, '722 DaVinci Blvd.', 'Kirkland', 'WA', '98034', 'USA');
INSERT INTO `orders` VALUES (10578, 'BSBEV', 4, '2017-06-24 00:00:00', '2017-07-25 00:00:00', 3, 29.60, 'Fauntleroy Circus', 'Londo', NULL, 'EC2 5NT', 'UK');
INSERT INTO `orders` VALUES (10579, 'LETSS', 1, '2017-06-25 00:00:00', '2017-07-04 00:00:00', 2, 13.73, '87 Polk St. Suite 5', 'San Francisco', 'CA', '94117', 'USA');
INSERT INTO `orders` VALUES (10580, 'OTTIK', 4, '2017-06-26 00:00:00', '2017-07-01 00:00:00', 3, 75.89, 'Mehrheimerstr. 369', 'Köl', NULL, '50739', 'Germany');
INSERT INTO `orders` VALUES (10581, 'FAMIA', 3, '2017-06-26 00:00:00', '2017-07-02 00:00:00', 1, 3.01, 'Rua Orós-92', 'Sao Paulo', 'SP', '05442-030', 'Brazil');
INSERT INTO `orders` VALUES (10582, 'BLAUS', 3, '2017-06-27 00:00:00', '2017-07-14 00:00:00', 2, 27.71, 'Forsterstr. 57', 'Mannheim', NULL, '68306', 'Germany');
INSERT INTO `orders` VALUES (10583, 'WARTH', 2, '2017-06-30 00:00:00', '2017-07-04 00:00:00', 2, 7.28, 'Torikatu 38', 'Oulu', NULL, '90110', 'Finland');
INSERT INTO `orders` VALUES (10584, 'BLONP', 4, '2017-06-30 00:00:00', '2017-07-04 00:00:00', 1, 59.14, '24-place Kléber', 'Strasbourg', NULL, '67000', 'France');
INSERT INTO `orders` VALUES (10585, 'WELLI', 7, '2017-07-01 00:00:00', '2017-07-10 00:00:00', 1, 13.41, 'Rua do Mercado-12', 'Resende', 'SP', '08737-363', 'Brazil');
INSERT INTO `orders` VALUES (10586, 'REGGC', 9, '2017-07-02 00:00:00', '2017-07-09 00:00:00', 1, 0.48, 'Strada Provinciale 124', 'Reggio Emilia', NULL, '42100', 'Italy');
INSERT INTO `orders` VALUES (10587, 'QUEDE', 1, '2017-07-02 00:00:00', '2017-07-09 00:00:00', 1, 62.52, 'Rua da Panificadora-12', 'Rio de Janeiro', 'RJ', '02389-673', 'Brazil');
INSERT INTO `orders` VALUES (10588, 'QUICK', 2, '2017-07-03 00:00:00', '2017-07-10 00:00:00', 3, 194.67, 'Taucherstraße 10', 'Cunewalde', NULL, '01307', 'Germany');
INSERT INTO `orders` VALUES (10589, 'GREAL', 8, '2017-07-04 00:00:00', '2017-07-14 00:00:00', 2, 4.42, '2732 Baker Blvd.', 'Eugene', 'OR', '97403', 'USA');
INSERT INTO `orders` VALUES (10590, 'MEREP', 4, '2017-07-07 00:00:00', '2017-07-14 00:00:00', 3, 44.77, '43 rue St. Laurent', 'Montréal', 'Québec', 'H1J 1C3', 'Canada');
INSERT INTO `orders` VALUES (10591, 'VAFFE', 1, '2017-07-07 00:00:00', '2017-07-16 00:00:00', 1, 55.92, 'Smagsloget 45', 'Århus', NULL, '8200', 'Denmark');
INSERT INTO `orders` VALUES (10592, 'LEHMS', 3, '2017-07-08 00:00:00', '2017-07-16 00:00:00', 1, 32.10, 'Magazinweg 7', 'Frankfurt a.M.', NULL, '60528', 'Germany');
INSERT INTO `orders` VALUES (10593, 'LEHMS', 7, '2017-07-09 00:00:00', '2017-08-13 00:00:00', 2, 174.20, 'Magazinweg 7', 'Frankfurt a.M.', NULL, '60528', 'Germany');
INSERT INTO `orders` VALUES (10594, 'OLDWO', 3, '2017-07-09 00:00:00', '2017-07-16 00:00:00', 2, 5.24, '2743 Bering St.', 'Anchorage', 'AK', '99508', 'USA');
INSERT INTO `orders` VALUES (10595, 'ERNSH', 2, '2017-07-10 00:00:00', '2017-07-14 00:00:00', 1, 96.78, 'Kirchgasse 6', 'Graz', NULL, '8010', 'Austria');
INSERT INTO `orders` VALUES (10596, 'WHITC', 8, '2017-07-11 00:00:00', '2017-08-12 00:00:00', 1, 16.34, '1029 - 12th Ave. S.', 'Seattle', 'WA', '98124', 'USA');
INSERT INTO `orders` VALUES (10597, 'PICCO', 7, '2017-07-11 00:00:00', '2017-07-18 00:00:00', 3, 35.12, 'Geislweg 14', 'Salzburg', NULL, '5020', 'Austria');
INSERT INTO `orders` VALUES (10598, 'RATTC', 1, '2017-07-14 00:00:00', '2017-07-18 00:00:00', 3, 44.42, '2817 Milton Dr.', 'Albuquerque', 'NM', '87110', 'USA');
INSERT INTO `orders` VALUES (10599, 'BSBEV', 6, '2017-07-15 00:00:00', '2017-07-21 00:00:00', 3, 29.98, 'Fauntleroy Circus', 'Londo', NULL, 'EC2 5NT', 'UK');
INSERT INTO `orders` VALUES (10600, 'HUNGC', 4, '2017-07-16 00:00:00', '2017-07-21 00:00:00', 1, 45.13, 'City Center Plaza 516 Main St.', 'Elgi', 'OR', '97827', 'USA');
INSERT INTO `orders` VALUES (10601, 'HILAA', 7, '2017-07-16 00:00:00', '2017-07-22 00:00:00', 1, 58.30, 'Carrera 22 con Ave. Carlos Soublette #8-35', 'San Cristóbal', 'Táchira', '5022', 'Venezuela');
INSERT INTO `orders` VALUES (10602, 'VAFFE', 8, '2017-07-17 00:00:00', '2017-07-22 00:00:00', 2, 2.92, 'Smagsloget 45', 'Århus', NULL, '8200', 'Denmark');
INSERT INTO `orders` VALUES (10603, 'SAVEA', 8, '2017-07-18 00:00:00', '2017-08-08 00:00:00', 2, 48.77, '187 Suffolk Ln.', 'Boise', 'ID', '83720', 'USA');
INSERT INTO `orders` VALUES (10604, 'FURIB', 1, '2017-07-18 00:00:00', '2017-07-29 00:00:00', 1, 7.46, 'Jardim das rosas n. 32', 'Lisboa', NULL, '1675', 'Portugal');
INSERT INTO `orders` VALUES (10605, 'MEREP', 1, '2017-07-21 00:00:00', '2017-07-29 00:00:00', 2, 379.13, '43 rue St. Laurent', 'Montréal', 'Québec', 'H1J 1C3', 'Canada');
INSERT INTO `orders` VALUES (10606, 'TRADH', 4, '2017-07-22 00:00:00', '2017-07-31 00:00:00', 3, 79.40, 'Av. Inês de Castro-414', 'Sao Paulo', 'SP', '05634-030', 'Brazil');
INSERT INTO `orders` VALUES (10607, 'SAVEA', 5, '2017-07-22 00:00:00', '2017-07-25 00:00:00', 1, 200.24, '187 Suffolk Ln.', 'Boise', 'ID', '83720', 'USA');
INSERT INTO `orders` VALUES (10608, 'TOMSP', 4, '2017-07-23 00:00:00', '2017-08-01 00:00:00', 2, 27.79, 'Luisenstr. 48', 'Münster', NULL, '44087', 'Germany');
INSERT INTO `orders` VALUES (10609, 'DUMO', 7, '2017-07-24 00:00:00', '2017-07-30 00:00:00', 2, 1.85, '67-rue des Cinquante Otages', 'Nantes', NULL, '44000', 'France');
INSERT INTO `orders` VALUES (10610, 'LAMAI', 8, '2017-07-25 00:00:00', '2017-08-06 00:00:00', 1, 26.78, '1 rue Alsace-Lorraine', 'Toulouse', NULL, '31000', 'France');
INSERT INTO `orders` VALUES (10611, 'WOLZA', 6, '2017-07-25 00:00:00', '2017-08-01 00:00:00', 2, 80.65, 'ul. Filtrowa 68', 'Warszawa', NULL, '01-012', 'Poland');
INSERT INTO `orders` VALUES (10612, 'SAVEA', 1, '2017-07-28 00:00:00', '2017-08-01 00:00:00', 2, 544.08, '187 Suffolk Ln.', 'Boise', 'ID', '83720', 'USA');
INSERT INTO `orders` VALUES (10613, 'HILAA', 4, '2017-07-29 00:00:00', '2017-08-01 00:00:00', 2, 8.11, 'Carrera 22 con Ave. Carlos Soublette #8-35', 'San Cristóbal', 'Táchira', '5022', 'Venezuela');
INSERT INTO `orders` VALUES (10614, 'BLAUS', 8, '2017-07-29 00:00:00', '2017-08-01 00:00:00', 3, 1.93, 'Forsterstr. 57', 'Mannheim', NULL, '68306', 'Germany');
INSERT INTO `orders` VALUES (10615, 'WILMK', 2, '2017-07-30 00:00:00', '2017-08-06 00:00:00', 3, 0.75, 'Keskuskatu 45', 'Helsinki', NULL, '21240', 'Finland');
INSERT INTO `orders` VALUES (10616, 'GREAL', 1, '2017-07-31 00:00:00', '2017-08-05 00:00:00', 2, 116.53, '2732 Baker Blvd.', 'Eugene', 'OR', '97403', 'USA');
INSERT INTO `orders` VALUES (10617, 'GREAL', 4, '2017-07-31 00:00:00', '2017-08-04 00:00:00', 2, 18.53, '2732 Baker Blvd.', 'Eugene', 'OR', '97403', 'USA');
INSERT INTO `orders` VALUES (10618, 'MEREP', 1, '2017-08-01 00:00:00', '2017-08-08 00:00:00', 1, 154.68, '43 rue St. Laurent', 'Montréal', 'Québec', 'H1J 1C3', 'Canada');
INSERT INTO `orders` VALUES (10619, 'MEREP', 3, '2017-08-04 00:00:00', '2017-08-07 00:00:00', 3, 91.05, '43 rue St. Laurent', 'Montréal', 'Québec', 'H1J 1C3', 'Canada');
INSERT INTO `orders` VALUES (10620, 'LAUGB', 2, '2017-08-05 00:00:00', '2017-08-14 00:00:00', 3, 0.94, '2319 Elm St.', 'Vancouver', 'BC', 'V3F 2K1', 'Canada');
INSERT INTO `orders` VALUES (10621, 'ISLAT', 4, '2017-08-05 00:00:00', '2017-08-11 00:00:00', 2, 23.73, 'Garden House Crowther Way', 'Cowes', 'Isle of Wight', 'PO31 7PJ', 'UK');
INSERT INTO `orders` VALUES (10622, 'RICAR', 4, '2017-08-06 00:00:00', '2017-08-11 00:00:00', 3, 50.97, 'Av. Copacabana-267', 'Rio de Janeiro', 'RJ', '02389-890', 'Brazil');
INSERT INTO `orders` VALUES (10623, 'FRANK', 8, '2017-08-07 00:00:00', '2017-08-12 00:00:00', 2, 97.18, 'Berliner Platz 43', 'Münche', NULL, '80805', 'Germany');
INSERT INTO `orders` VALUES (10624, 'THECR', 4, '2017-08-07 00:00:00', '2017-08-19 00:00:00', 2, 94.80, '55 Grizzly Peak Rd.', 'Butte', 'MT', '59801', 'USA');
INSERT INTO `orders` VALUES (10625, 'ANATR', 3, '2017-08-08 00:00:00', '2017-08-14 00:00:00', 1, 43.90, 'Avda. de la Constitución 2222', 'México D.F.', NULL, '05021', 'Mexico');
INSERT INTO `orders` VALUES (10626, 'BERGS', 1, '2017-08-11 00:00:00', '2017-08-20 00:00:00', 2, 138.69, 'Berguvsvägen  8', 'Luleå', NULL, 'S-958 22', 'Sweden');
INSERT INTO `orders` VALUES (10627, 'SAVEA', 8, '2017-08-11 00:00:00', '2017-08-21 00:00:00', 3, 107.46, '187 Suffolk Ln.', 'Boise', 'ID', '83720', 'USA');
INSERT INTO `orders` VALUES (10628, 'BLONP', 4, '2017-08-12 00:00:00', '2017-08-20 00:00:00', 3, 30.36, '24-place Kléber', 'Strasbourg', NULL, '67000', 'France');
INSERT INTO `orders` VALUES (10629, 'GODOS', 4, '2017-08-12 00:00:00', '2017-08-20 00:00:00', 3, 85.46, 'C/ Romero-33', 'Sevilla', NULL, '41101', 'Spain');
INSERT INTO `orders` VALUES (10630, 'KOENE', 1, '2017-08-13 00:00:00', '2017-08-19 00:00:00', 2, 32.35, 'Maubelstr. 90', 'Brandenburg', NULL, '14776', 'Germany');
INSERT INTO `orders` VALUES (10631, 'LAMAI', 8, '2017-08-14 00:00:00', '2017-08-15 00:00:00', 1, 0.87, '1 rue Alsace-Lorraine', 'Toulouse', NULL, '31000', 'France');
INSERT INTO `orders` VALUES (10632, 'WANDK', 8, '2017-08-14 00:00:00', '2017-08-19 00:00:00', 1, 41.38, 'Adenauerallee 900', 'Stuttgart', NULL, '70563', 'Germany');
INSERT INTO `orders` VALUES (10633, 'ERNSH', 7, '2017-08-15 00:00:00', '2017-08-18 00:00:00', 3, 477.90, 'Kirchgasse 6', 'Graz', NULL, '8010', 'Austria');
INSERT INTO `orders` VALUES (10634, 'FOLIG', 4, '2017-08-15 00:00:00', '2017-08-21 00:00:00', 3, 487.38, '184-chaussée de Tournai', 'Lille', NULL, '59000', 'France');
INSERT INTO `orders` VALUES (10635, 'MAGAA', 8, '2017-08-18 00:00:00', '2017-08-21 00:00:00', 3, 47.46, 'Via Ludovico il Moro 22', 'Bergamo', NULL, '24100', 'Italy');
INSERT INTO `orders` VALUES (10636, 'WARTH', 4, '2017-08-19 00:00:00', '2017-08-26 00:00:00', 1, 1.15, 'Torikatu 38', 'Oulu', NULL, '90110', 'Finland');
INSERT INTO `orders` VALUES (10637, 'QUEE', 6, '2017-08-19 00:00:00', '2017-08-26 00:00:00', 1, 201.29, 'Alameda dos Canàrios-891', 'Sao Paulo', 'SP', '05487-020', 'Brazil');
INSERT INTO `orders` VALUES (10638, 'LINOD', 3, '2017-08-20 00:00:00', '2017-09-01 00:00:00', 1, 158.44, 'Ave. 5 de Mayo Porlamar', 'I. de Margarita', 'Nueva Esparta', '4980', 'Venezuela');
INSERT INTO `orders` VALUES (10639, 'SANTG', 7, '2017-08-20 00:00:00', '2017-08-27 00:00:00', 3, 38.64, 'Erling Skakkes gate 78', 'Staver', NULL, '4110', 'Norway');
INSERT INTO `orders` VALUES (10640, 'WANDK', 4, '2017-08-21 00:00:00', '2017-08-28 00:00:00', 1, 23.55, 'Adenauerallee 900', 'Stuttgart', NULL, '70563', 'Germany');
INSERT INTO `orders` VALUES (10641, 'HILAA', 4, '2017-08-22 00:00:00', '2017-08-26 00:00:00', 2, 179.61, 'Carrera 22 con Ave. Carlos Soublette #8-35', 'San Cristóbal', 'Táchira', '5022', 'Venezuela');
INSERT INTO `orders` VALUES (10642, 'SIMOB', 7, '2017-08-22 00:00:00', '2017-09-05 00:00:00', 3, 41.89, 'Vinbæltet 34', 'Kobenhav', NULL, '1734', 'Denmark');
INSERT INTO `orders` VALUES (10643, 'ALFKI', 6, '2017-08-25 00:00:00', '2017-09-02 00:00:00', 1, 29.46, 'Obere Str. 57', 'Berli', NULL, '12209', 'Germany');
INSERT INTO `orders` VALUES (10644, 'WELLI', 3, '2017-08-25 00:00:00', '2017-09-01 00:00:00', 2, 0.14, 'Rua do Mercado-12', 'Resende', 'SP', '08737-363', 'Brazil');
INSERT INTO `orders` VALUES (10645, 'HANAR', 4, '2017-08-26 00:00:00', '2017-09-02 00:00:00', 1, 12.41, 'Rua do Paço-67', 'Rio de Janeiro', 'RJ', '05454-876', 'Brazil');
INSERT INTO `orders` VALUES (10646, 'HUNGO', 9, '2017-08-27 00:00:00', '2017-09-03 00:00:00', 3, 142.33, '8 Johnstown Road', 'Cork', 'Co. Cork', NULL, 'Ireland');
INSERT INTO `orders` VALUES (10647, 'QUEDE', 4, '2017-08-27 00:00:00', '2017-09-03 00:00:00', 2, 45.54, 'Rua da Panificadora-12', 'Rio de Janeiro', 'RJ', '02389-673', 'Brazil');
INSERT INTO `orders` VALUES (10648, 'RICAR', 5, '2017-08-28 00:00:00', '2017-09-09 00:00:00', 2, 14.25, 'Av. Copacabana-267', 'Rio de Janeiro', 'RJ', '02389-890', 'Brazil');
INSERT INTO `orders` VALUES (10649, 'MAISD', 5, '2017-08-28 00:00:00', '2017-08-29 00:00:00', 3, 6.20, 'Rue Joseph-Bens 532', 'Bruxelles', NULL, 'B-1180', 'Belgium');
INSERT INTO `orders` VALUES (10650, 'FAMIA', 5, '2017-08-29 00:00:00', '2017-09-03 00:00:00', 3, 176.81, 'Rua Orós-92', 'Sao Paulo', 'SP', '05442-030', 'Brazil');
INSERT INTO `orders` VALUES (10651, 'WANDK', 8, '2017-09-01 00:00:00', '2017-09-11 00:00:00', 2, 20.60, 'Adenauerallee 900', 'Stuttgart', NULL, '70563', 'Germany');
INSERT INTO `orders` VALUES (10652, 'GOURL', 4, '2017-09-01 00:00:00', '2017-09-08 00:00:00', 2, 7.14, 'Av. Brasil-442', 'Campinas', 'SP', '04876-786', 'Brazil');
INSERT INTO `orders` VALUES (10653, 'FRANK', 1, '2017-09-02 00:00:00', '2017-09-19 00:00:00', 1, 93.25, 'Berliner Platz 43', 'Münche', NULL, '80805', 'Germany');
INSERT INTO `orders` VALUES (10654, 'BERGS', 5, '2017-09-02 00:00:00', '2017-09-11 00:00:00', 1, 55.26, 'Berguvsvägen  8', 'Luleå', NULL, 'S-958 22', 'Sweden');
INSERT INTO `orders` VALUES (10655, 'REGGC', 1, '2017-09-03 00:00:00', '2017-09-11 00:00:00', 2, 4.41, 'Strada Provinciale 124', 'Reggio Emilia', NULL, '42100', 'Italy');
INSERT INTO `orders` VALUES (10656, 'GREAL', 6, '2017-09-04 00:00:00', '2017-09-10 00:00:00', 1, 57.15, '2732 Baker Blvd.', 'Eugene', 'OR', '97403', 'USA');
INSERT INTO `orders` VALUES (10657, 'SAVEA', 2, '2017-09-04 00:00:00', '2017-09-15 00:00:00', 2, 352.69, '187 Suffolk Ln.', 'Boise', 'ID', '83720', 'USA');
INSERT INTO `orders` VALUES (10658, 'QUICK', 4, '2017-09-05 00:00:00', '2017-09-08 00:00:00', 1, 364.15, 'Taucherstraße 10', 'Cunewalde', NULL, '01307', 'Germany');
INSERT INTO `orders` VALUES (10659, 'QUEE', 7, '2017-09-05 00:00:00', '2017-09-10 00:00:00', 2, 105.81, 'Alameda dos Canàrios-891', 'Sao Paulo', 'SP', '05487-020', 'Brazil');
INSERT INTO `orders` VALUES (10660, 'HUNGC', 8, '2017-09-08 00:00:00', '2017-10-15 00:00:00', 1, 111.29, 'City Center Plaza 516 Main St.', 'Elgi', 'OR', '97827', 'USA');
INSERT INTO `orders` VALUES (10661, 'HUNGO', 7, '2017-09-09 00:00:00', '2017-09-15 00:00:00', 3, 17.55, '8 Johnstown Road', 'Cork', 'Co. Cork', NULL, 'Ireland');
INSERT INTO `orders` VALUES (10662, 'LONEP', 3, '2017-09-09 00:00:00', '2017-09-18 00:00:00', 2, 1.28, '89 Chiaroscuro Rd.', 'Portland', 'OR', '97219', 'USA');
INSERT INTO `orders` VALUES (10663, 'BONAP', 2, '2017-09-10 00:00:00', '2017-10-03 00:00:00', 2, 113.15, '12-rue des Bouchers', 'Marseille', NULL, '13008', 'France');
INSERT INTO `orders` VALUES (10664, 'FURIB', 1, '2017-09-10 00:00:00', '2017-09-19 00:00:00', 3, 1.27, 'Jardim das rosas n. 32', 'Lisboa', NULL, '1675', 'Portugal');
INSERT INTO `orders` VALUES (10665, 'LONEP', 1, '2017-09-11 00:00:00', '2017-09-17 00:00:00', 2, 26.31, '89 Chiaroscuro Rd.', 'Portland', 'OR', '97219', 'USA');
INSERT INTO `orders` VALUES (10666, 'RICSU', 7, '2017-09-12 00:00:00', '2017-09-22 00:00:00', 2, 232.42, 'Starenweg 5', 'Genève', NULL, '1204', 'Switzerland');
INSERT INTO `orders` VALUES (10667, 'ERNSH', 7, '2017-09-12 00:00:00', '2017-09-19 00:00:00', 1, 78.09, 'Kirchgasse 6', 'Graz', NULL, '8010', 'Austria');
INSERT INTO `orders` VALUES (10668, 'WANDK', 1, '2017-09-15 00:00:00', '2017-09-23 00:00:00', 2, 47.22, 'Adenauerallee 900', 'Stuttgart', NULL, '70563', 'Germany');
INSERT INTO `orders` VALUES (10669, 'SIMOB', 2, '2017-09-15 00:00:00', '2017-09-22 00:00:00', 1, 24.39, 'Vinbæltet 34', 'Kobenhav', NULL, '1734', 'Denmark');
INSERT INTO `orders` VALUES (10670, 'FRANK', 4, '2017-09-16 00:00:00', '2017-09-18 00:00:00', 1, 203.48, 'Berliner Platz 43', 'Münche', NULL, '80805', 'Germany');
INSERT INTO `orders` VALUES (10671, 'FRANR', 1, '2017-09-17 00:00:00', '2017-09-24 00:00:00', 1, 30.34, '54-rue Royale', 'Nantes', NULL, '44000', 'France');
INSERT INTO `orders` VALUES (10672, 'BERGS', 9, '2017-09-17 00:00:00', '2017-09-26 00:00:00', 2, 95.75, 'Berguvsvägen  8', 'Luleå', NULL, 'S-958 22', 'Sweden');
INSERT INTO `orders` VALUES (10673, 'WILMK', 2, '2017-09-18 00:00:00', '2017-09-19 00:00:00', 1, 22.76, 'Keskuskatu 45', 'Helsinki', NULL, '21240', 'Finland');
INSERT INTO `orders` VALUES (10674, 'ISLAT', 4, '2017-09-18 00:00:00', '2017-09-30 00:00:00', 2, 0.90, 'Garden House Crowther Way', 'Cowes', 'Isle of Wight', 'PO31 7PJ', 'UK');
INSERT INTO `orders` VALUES (10675, 'FRANK', 5, '2017-09-19 00:00:00', '2017-09-23 00:00:00', 2, 31.85, 'Berliner Platz 43', 'Münche', NULL, '80805', 'Germany');
INSERT INTO `orders` VALUES (10676, 'TORTU', 2, '2017-09-22 00:00:00', '2017-09-29 00:00:00', 2, 2.01, 'Avda. Azteca 123', 'México D.F.', NULL, '05033', 'Mexico');
INSERT INTO `orders` VALUES (10677, 'ANTO', 1, '2017-09-22 00:00:00', '2017-09-26 00:00:00', 3, 4.03, 'Mataderos  2312', 'México D.F.', NULL, '05023', 'Mexico');
INSERT INTO `orders` VALUES (10678, 'SAVEA', 7, '2017-09-23 00:00:00', '2017-10-16 00:00:00', 3, 388.98, '187 Suffolk Ln.', 'Boise', 'ID', '83720', 'USA');
INSERT INTO `orders` VALUES (10679, 'BLONP', 8, '2017-09-23 00:00:00', '2017-09-30 00:00:00', 3, 27.94, '24-place Kléber', 'Strasbourg', NULL, '67000', 'France');
INSERT INTO `orders` VALUES (10680, 'OLDWO', 1, '2017-09-24 00:00:00', '2017-09-26 00:00:00', 1, 26.61, '2743 Bering St.', 'Anchorage', 'AK', '99508', 'USA');
INSERT INTO `orders` VALUES (10681, 'GREAL', 3, '2017-09-25 00:00:00', '2017-09-30 00:00:00', 3, 76.13, '2732 Baker Blvd.', 'Eugene', 'OR', '97403', 'USA');
INSERT INTO `orders` VALUES (10682, 'ANTO', 3, '2017-09-25 00:00:00', '2017-10-01 00:00:00', 2, 36.13, 'Mataderos  2312', 'México D.F.', NULL, '05023', 'Mexico');
INSERT INTO `orders` VALUES (10683, 'DUMO', 2, '2017-09-26 00:00:00', '2017-10-01 00:00:00', 1, 4.40, '67-rue des Cinquante Otages', 'Nantes', NULL, '44000', 'France');
INSERT INTO `orders` VALUES (10684, 'OTTIK', 3, '2017-09-26 00:00:00', '2017-09-30 00:00:00', 1, 145.63, 'Mehrheimerstr. 369', 'Köl', NULL, '50739', 'Germany');
INSERT INTO `orders` VALUES (10685, 'GOURL', 4, '2017-09-29 00:00:00', '2017-10-03 00:00:00', 2, 33.75, 'Av. Brasil-442', 'Campinas', 'SP', '04876-786', 'Brazil');
INSERT INTO `orders` VALUES (10686, 'PICCO', 2, '2017-09-30 00:00:00', '2017-10-08 00:00:00', 1, 96.50, 'Geislweg 14', 'Salzburg', NULL, '5020', 'Austria');
INSERT INTO `orders` VALUES (10687, 'HUNGO', 9, '2017-09-30 00:00:00', '2017-10-30 00:00:00', 2, 296.43, '8 Johnstown Road', 'Cork', 'Co. Cork', NULL, 'Ireland');
INSERT INTO `orders` VALUES (10688, 'VAFFE', 4, '2017-10-01 00:00:00', '2017-10-07 00:00:00', 2, 299.09, 'Smagsloget 45', 'Århus', NULL, '8200', 'Denmark');
INSERT INTO `orders` VALUES (10689, 'BERGS', 1, '2017-10-01 00:00:00', '2017-10-07 00:00:00', 2, 13.42, 'Berguvsvägen  8', 'Luleå', NULL, 'S-958 22', 'Sweden');
INSERT INTO `orders` VALUES (10690, 'HANAR', 1, '2017-10-02 00:00:00', '2017-10-03 00:00:00', 1, 15.80, 'Rua do Paço-67', 'Rio de Janeiro', 'RJ', '05454-876', 'Brazil');
INSERT INTO `orders` VALUES (10691, 'QUICK', 2, '2017-10-03 00:00:00', '2017-10-22 00:00:00', 2, 810.05, 'Taucherstraße 10', 'Cunewalde', NULL, '01307', 'Germany');
INSERT INTO `orders` VALUES (10692, 'ALFKI', 4, '2017-10-03 00:00:00', '2017-10-13 00:00:00', 2, 61.02, 'Obere Str. 57', 'Berli', NULL, '12209', 'Germany');
INSERT INTO `orders` VALUES (10693, 'WHITC', 3, '2017-10-06 00:00:00', '2017-10-10 00:00:00', 3, 139.34, '1029 - 12th Ave. S.', 'Seattle', 'WA', '98124', 'USA');
INSERT INTO `orders` VALUES (10694, 'QUICK', 8, '2017-10-06 00:00:00', '2017-10-09 00:00:00', 3, 398.36, 'Taucherstraße 10', 'Cunewalde', NULL, '01307', 'Germany');
INSERT INTO `orders` VALUES (10695, 'WILMK', 7, '2017-10-07 00:00:00', '2017-10-14 00:00:00', 1, 16.72, 'Keskuskatu 45', 'Helsinki', NULL, '21240', 'Finland');
INSERT INTO `orders` VALUES (10696, 'WHITC', 8, '2017-10-08 00:00:00', '2017-10-14 00:00:00', 3, 102.55, '1029 - 12th Ave. S.', 'Seattle', 'WA', '98124', 'USA');
INSERT INTO `orders` VALUES (10697, 'LINOD', 3, '2017-10-08 00:00:00', '2017-10-14 00:00:00', 1, 45.52, 'Ave. 5 de Mayo Porlamar', 'I. de Margarita', 'Nueva Esparta', '4980', 'Venezuela');
INSERT INTO `orders` VALUES (10698, 'ERNSH', 4, '2017-10-09 00:00:00', '2017-10-17 00:00:00', 1, 272.47, 'Kirchgasse 6', 'Graz', NULL, '8010', 'Austria');
INSERT INTO `orders` VALUES (10699, 'MORGK', 3, '2017-10-09 00:00:00', '2017-10-13 00:00:00', 3, 0.58, 'Heerstr. 22', 'Leipzig', NULL, '04179', 'Germany');
INSERT INTO `orders` VALUES (10700, 'SAVEA', 3, '2017-10-10 00:00:00', '2017-10-16 00:00:00', 1, 65.10, '187 Suffolk Ln.', 'Boise', 'ID', '83720', 'USA');
INSERT INTO `orders` VALUES (10701, 'HUNGO', 6, '2017-10-13 00:00:00', '2017-10-15 00:00:00', 3, 220.31, '8 Johnstown Road', 'Cork', 'Co. Cork', NULL, 'Ireland');
INSERT INTO `orders` VALUES (10702, 'ALFKI', 4, '2017-10-13 00:00:00', '2017-10-21 00:00:00', 1, 23.94, 'Obere Str. 57', 'Berli', NULL, '12209', 'Germany');
INSERT INTO `orders` VALUES (10703, 'FOLKO', 6, '2017-10-14 00:00:00', '2017-10-20 00:00:00', 2, 152.30, 'Åkergatan 24', 'Bräcke', NULL, 'S-844 67', 'Sweden');
INSERT INTO `orders` VALUES (10704, 'QUEE', 6, '2017-10-14 00:00:00', '2017-11-07 00:00:00', 1, 4.78, 'Alameda dos Canàrios-891', 'Sao Paulo', 'SP', '05487-020', 'Brazil');
INSERT INTO `orders` VALUES (10705, 'HILAA', 9, '2017-10-15 00:00:00', '2017-11-18 00:00:00', 2, 3.52, 'Carrera 22 con Ave. Carlos Soublette #8-35', 'San Cristóbal', 'Táchira', '5022', 'Venezuela');
INSERT INTO `orders` VALUES (10706, 'OLDWO', 8, '2017-10-16 00:00:00', '2017-10-21 00:00:00', 3, 135.63, '2743 Bering St.', 'Anchorage', 'AK', '99508', 'USA');
INSERT INTO `orders` VALUES (10707, 'AROUT', 4, '2017-10-16 00:00:00', '2017-10-23 00:00:00', 3, 21.74, 'Brook Farm Stratford St. Mary', 'Colchester', 'Essex', 'CO7 6JX', 'UK');
INSERT INTO `orders` VALUES (10708, 'THEBI', 6, '2017-10-17 00:00:00', '2017-11-05 00:00:00', 2, 2.96, '89 Jefferson Way Suite 2', 'Portland', 'OR', '97201', 'USA');
INSERT INTO `orders` VALUES (10709, 'GOURL', 1, '2017-10-17 00:00:00', '2017-11-20 00:00:00', 3, 210.80, 'Av. Brasil-442', 'Campinas', 'SP', '04876-786', 'Brazil');
INSERT INTO `orders` VALUES (10710, 'FRANS', 1, '2017-10-20 00:00:00', '2017-10-23 00:00:00', 1, 4.98, 'Via Monte Bianco 34', 'Torino', NULL, '10100', 'Italy');
INSERT INTO `orders` VALUES (10711, 'SAVEA', 5, '2017-10-21 00:00:00', '2017-10-29 00:00:00', 2, 52.41, '187 Suffolk Ln.', 'Boise', 'ID', '83720', 'USA');
INSERT INTO `orders` VALUES (10712, 'HUNGO', 3, '2017-10-21 00:00:00', '2017-10-31 00:00:00', 1, 89.93, '8 Johnstown Road', 'Cork', 'Co. Cork', NULL, 'Ireland');
INSERT INTO `orders` VALUES (10713, 'SAVEA', 1, '2017-10-22 00:00:00', '2017-10-24 00:00:00', 1, 167.05, '187 Suffolk Ln.', 'Boise', 'ID', '83720', 'USA');
INSERT INTO `orders` VALUES (10714, 'SAVEA', 5, '2017-10-22 00:00:00', '2017-10-27 00:00:00', 3, 24.49, '187 Suffolk Ln.', 'Boise', 'ID', '83720', 'USA');
INSERT INTO `orders` VALUES (10715, 'BONAP', 3, '2017-10-23 00:00:00', '2017-10-29 00:00:00', 1, 63.20, '12-rue des Bouchers', 'Marseille', NULL, '13008', 'France');
INSERT INTO `orders` VALUES (10716, 'RANCH', 4, '2017-10-24 00:00:00', '2017-10-27 00:00:00', 2, 22.57, 'Av. del Libertador 900', 'Buenos Aires', NULL, '1010', 'Argentina');
INSERT INTO `orders` VALUES (10717, 'FRANK', 1, '2017-10-24 00:00:00', '2017-10-29 00:00:00', 2, 59.25, 'Berliner Platz 43', 'Münche', NULL, '80805', 'Germany');
INSERT INTO `orders` VALUES (10718, 'KOENE', 1, '2017-10-27 00:00:00', '2017-10-29 00:00:00', 3, 170.88, 'Maubelstr. 90', 'Brandenburg', NULL, '14776', 'Germany');
INSERT INTO `orders` VALUES (10719, 'LETSS', 8, '2017-10-27 00:00:00', '2017-11-05 00:00:00', 2, 51.44, '87 Polk St. Suite 5', 'San Francisco', 'CA', '94117', 'USA');
INSERT INTO `orders` VALUES (10720, 'QUEDE', 8, '2017-10-28 00:00:00', '2017-11-05 00:00:00', 2, 9.53, 'Rua da Panificadora-12', 'Rio de Janeiro', 'RJ', '02389-673', 'Brazil');
INSERT INTO `orders` VALUES (10721, 'QUICK', 5, '2017-10-29 00:00:00', '2017-10-31 00:00:00', 3, 48.92, 'Taucherstraße 10', 'Cunewalde', NULL, '01307', 'Germany');
INSERT INTO `orders` VALUES (10722, 'SAVEA', 8, '2017-10-29 00:00:00', '2017-11-04 00:00:00', 1, 74.58, '187 Suffolk Ln.', 'Boise', 'ID', '83720', 'USA');
INSERT INTO `orders` VALUES (10723, 'WHITC', 3, '2017-10-30 00:00:00', '2017-11-25 00:00:00', 1, 21.72, '1029 - 12th Ave. S.', 'Seattle', 'WA', '98124', 'USA');
INSERT INTO `orders` VALUES (10724, 'MEREP', 8, '2017-10-30 00:00:00', '2017-11-05 00:00:00', 2, 57.75, '43 rue St. Laurent', 'Montréal', 'Québec', 'H1J 1C3', 'Canada');
INSERT INTO `orders` VALUES (10725, 'FAMIA', 4, '2017-10-31 00:00:00', '2017-11-05 00:00:00', 3, 10.83, 'Rua Orós-92', 'Sao Paulo', 'SP', '05442-030', 'Brazil');
INSERT INTO `orders` VALUES (10726, 'EASTC', 4, '2017-11-03 00:00:00', '2017-12-05 00:00:00', 1, 16.56, '35 King George', 'Londo', NULL, 'WX3 6FW', 'UK');
INSERT INTO `orders` VALUES (10727, 'REGGC', 2, '2017-11-03 00:00:00', '2017-12-05 00:00:00', 1, 89.90, 'Strada Provinciale 124', 'Reggio Emilia', NULL, '42100', 'Italy');
INSERT INTO `orders` VALUES (10728, 'QUEE', 4, '2017-11-04 00:00:00', '2017-11-11 00:00:00', 2, 58.33, 'Alameda dos Canàrios-891', 'Sao Paulo', 'SP', '05487-020', 'Brazil');
INSERT INTO `orders` VALUES (10729, 'LINOD', 8, '2017-11-04 00:00:00', '2017-11-14 00:00:00', 3, 141.06, 'Ave. 5 de Mayo Porlamar', 'I. de Margarita', 'Nueva Esparta', '4980', 'Venezuela');
INSERT INTO `orders` VALUES (10730, 'BONAP', 5, '2017-11-05 00:00:00', '2017-11-14 00:00:00', 1, 20.12, '12-rue des Bouchers', 'Marseille', NULL, '13008', 'France');
INSERT INTO `orders` VALUES (10731, 'CHOPS', 7, '2017-11-06 00:00:00', '2017-11-14 00:00:00', 1, 96.65, 'Hauptstr. 31', 'Ber', NULL, '3012', 'Switzerland');
INSERT INTO `orders` VALUES (10732, 'BONAP', 3, '2017-11-06 00:00:00', '2017-11-07 00:00:00', 1, 16.97, '12-rue des Bouchers', 'Marseille', NULL, '13008', 'France');
INSERT INTO `orders` VALUES (10733, 'BERGS', 1, '2017-11-07 00:00:00', '2017-11-10 00:00:00', 3, 110.11, 'Berguvsvägen  8', 'Luleå', NULL, 'S-958 22', 'Sweden');
INSERT INTO `orders` VALUES (10734, 'GOURL', 2, '2017-11-07 00:00:00', '2017-11-12 00:00:00', 3, 1.63, 'Av. Brasil-442', 'Campinas', 'SP', '04876-786', 'Brazil');
INSERT INTO `orders` VALUES (10735, 'LETSS', 6, '2017-11-10 00:00:00', '2017-11-21 00:00:00', 2, 45.97, '87 Polk St. Suite 5', 'San Francisco', 'CA', '94117', 'USA');
INSERT INTO `orders` VALUES (10736, 'HUNGO', 9, '2017-11-11 00:00:00', '2017-11-21 00:00:00', 2, 44.10, '8 Johnstown Road', 'Cork', 'Co. Cork', NULL, 'Ireland');
INSERT INTO `orders` VALUES (10737, 'VINET', 2, '2017-11-11 00:00:00', '2017-11-18 00:00:00', 2, 7.79, '59 rue de l\'\'Abbaye', 'Reims', NULL, '51100', 'France');
INSERT INTO `orders` VALUES (10738, 'SPECD', 2, '2017-11-12 00:00:00', '2017-11-18 00:00:00', 1, 2.91, '25-rue Lauristo', 'Paris', NULL, '75016', 'France');
INSERT INTO `orders` VALUES (10739, 'VINET', 3, '2017-11-12 00:00:00', '2017-11-17 00:00:00', 3, 11.08, '59 rue de l\'\'Abbaye', 'Reims', NULL, '51100', 'France');
INSERT INTO `orders` VALUES (10740, 'WHITC', 4, '2017-11-13 00:00:00', '2017-11-25 00:00:00', 2, 81.88, '1029 - 12th Ave. S.', 'Seattle', 'WA', '98124', 'USA');
INSERT INTO `orders` VALUES (10741, 'AROUT', 4, '2017-11-14 00:00:00', '2017-11-18 00:00:00', 3, 10.96, 'Brook Farm Stratford St. Mary', 'Colchester', 'Essex', 'CO7 6JX', 'UK');
INSERT INTO `orders` VALUES (10742, 'BOTTM', 3, '2017-11-14 00:00:00', '2017-11-18 00:00:00', 3, 243.73, '23 Tsawassen Blvd.', 'Tsawasse', 'BC', 'T2F 8M4', 'Canada');
INSERT INTO `orders` VALUES (10743, 'AROUT', 1, '2017-11-17 00:00:00', '2017-11-21 00:00:00', 2, 23.72, 'Brook Farm Stratford St. Mary', 'Colchester', 'Essex', 'CO7 6JX', 'UK');
INSERT INTO `orders` VALUES (10744, 'VAFFE', 6, '2017-11-17 00:00:00', '2017-11-24 00:00:00', 1, 69.19, 'Smagsloget 45', 'Århus', NULL, '8200', 'Denmark');
INSERT INTO `orders` VALUES (10745, 'QUICK', 9, '2017-11-18 00:00:00', '2017-11-27 00:00:00', 1, 3.52, 'Taucherstraße 10', 'Cunewalde', NULL, '01307', 'Germany');
INSERT INTO `orders` VALUES (10746, 'CHOPS', 1, '2017-11-19 00:00:00', '2017-11-21 00:00:00', 3, 31.43, 'Hauptstr. 31', 'Ber', NULL, '3012', 'Switzerland');
INSERT INTO `orders` VALUES (10747, 'PICCO', 6, '2017-11-19 00:00:00', '2017-11-26 00:00:00', 1, 117.33, 'Geislweg 14', 'Salzburg', NULL, '5020', 'Austria');
INSERT INTO `orders` VALUES (10748, 'SAVEA', 3, '2017-11-20 00:00:00', '2017-11-28 00:00:00', 1, 232.55, '187 Suffolk Ln.', 'Boise', 'ID', '83720', 'USA');
INSERT INTO `orders` VALUES (10749, 'ISLAT', 4, '2017-11-20 00:00:00', '2017-12-19 00:00:00', 2, 61.53, 'Garden House Crowther Way', 'Cowes', 'Isle of Wight', 'PO31 7PJ', 'UK');
INSERT INTO `orders` VALUES (10750, 'WARTH', 9, '2017-11-21 00:00:00', '2017-11-24 00:00:00', 1, 79.30, 'Torikatu 38', 'Oulu', NULL, '90110', 'Finland');
INSERT INTO `orders` VALUES (10751, 'RICSU', 3, '2017-11-24 00:00:00', '2017-12-03 00:00:00', 3, 130.79, 'Starenweg 5', 'Genève', NULL, '1204', 'Switzerland');
INSERT INTO `orders` VALUES (10752, 'NORTS', 2, '2017-11-24 00:00:00', '2017-11-28 00:00:00', 3, 1.39, 'South House 300 Queensbridge', 'Londo', NULL, 'SW7 1RZ', 'UK');
INSERT INTO `orders` VALUES (10753, 'FRANS', 3, '2017-11-25 00:00:00', '2017-11-27 00:00:00', 1, 7.70, 'Via Monte Bianco 34', 'Torino', NULL, '10100', 'Italy');
INSERT INTO `orders` VALUES (10754, 'MAGAA', 6, '2017-11-25 00:00:00', '2017-11-27 00:00:00', 3, 2.38, 'Via Ludovico il Moro 22', 'Bergamo', NULL, '24100', 'Italy');
INSERT INTO `orders` VALUES (10755, 'BONAP', 4, '2017-11-26 00:00:00', '2017-11-28 00:00:00', 2, 16.71, '12-rue des Bouchers', 'Marseille', NULL, '13008', 'France');
INSERT INTO `orders` VALUES (10756, 'SPLIR', 8, '2017-11-27 00:00:00', '2017-12-02 00:00:00', 2, 73.21, 'P.O. Box 555', 'Lander', 'WY', '82520', 'USA');
INSERT INTO `orders` VALUES (10757, 'SAVEA', 6, '2017-11-27 00:00:00', '2017-12-15 00:00:00', 1, 8.19, '187 Suffolk Ln.', 'Boise', 'ID', '83720', 'USA');
INSERT INTO `orders` VALUES (10758, 'RICSU', 3, '2017-11-28 00:00:00', '2017-12-04 00:00:00', 3, 138.17, 'Starenweg 5', 'Genève', NULL, '1204', 'Switzerland');
INSERT INTO `orders` VALUES (10759, 'ANATR', 3, '2017-11-28 00:00:00', '2017-12-12 00:00:00', 3, 11.99, 'Avda. de la Constitución 2222', 'México D.F.', NULL, '05021', 'Mexico');
INSERT INTO `orders` VALUES (10760, 'MAISD', 4, '2017-12-01 00:00:00', '2017-12-10 00:00:00', 1, 155.64, 'Rue Joseph-Bens 532', 'Bruxelles', NULL, 'B-1180', 'Belgium');
INSERT INTO `orders` VALUES (10761, 'RATTC', 5, '2017-12-02 00:00:00', '2017-12-08 00:00:00', 2, 18.66, '2817 Milton Dr.', 'Albuquerque', 'NM', '87110', 'USA');
INSERT INTO `orders` VALUES (10762, 'FOLKO', 3, '2017-12-02 00:00:00', '2017-12-09 00:00:00', 1, 328.74, 'Åkergatan 24', 'Bräcke', NULL, 'S-844 67', 'Sweden');
INSERT INTO `orders` VALUES (10763, 'FOLIG', 3, '2017-12-03 00:00:00', '2017-12-08 00:00:00', 3, 37.35, '184-chaussée de Tournai', 'Lille', NULL, '59000', 'France');
INSERT INTO `orders` VALUES (10764, 'ERNSH', 6, '2017-12-03 00:00:00', '2017-12-08 00:00:00', 3, 145.45, 'Kirchgasse 6', 'Graz', NULL, '8010', 'Austria');
INSERT INTO `orders` VALUES (10765, 'QUICK', 3, '2017-12-04 00:00:00', '2017-12-09 00:00:00', 3, 42.74, 'Taucherstraße 10', 'Cunewalde', NULL, '01307', 'Germany');
INSERT INTO `orders` VALUES (10766, 'OTTIK', 4, '2017-12-05 00:00:00', '2017-12-09 00:00:00', 1, 157.55, 'Mehrheimerstr. 369', 'Köl', NULL, '50739', 'Germany');
INSERT INTO `orders` VALUES (10767, 'SUPRD', 4, '2017-12-05 00:00:00', '2017-12-15 00:00:00', 3, 1.59, 'Boulevard Tirou-255', 'Charleroi', NULL, 'B-6000', 'Belgium');
INSERT INTO `orders` VALUES (10768, 'AROUT', 3, '2017-12-08 00:00:00', '2017-12-15 00:00:00', 2, 146.32, 'Brook Farm Stratford St. Mary', 'Colchester', 'Essex', 'CO7 6JX', 'UK');
INSERT INTO `orders` VALUES (10769, 'VAFFE', 3, '2017-12-08 00:00:00', '2017-12-12 00:00:00', 1, 65.06, 'Smagsloget 45', 'Århus', NULL, '8200', 'Denmark');
INSERT INTO `orders` VALUES (10770, 'HANAR', 8, '2017-12-09 00:00:00', '2017-12-17 00:00:00', 3, 5.32, 'Rua do Paço-67', 'Rio de Janeiro', 'RJ', '05454-876', 'Brazil');
INSERT INTO `orders` VALUES (10771, 'ERNSH', 9, '2017-12-10 00:00:00', '2018-01-02 00:00:00', 2, 11.19, 'Kirchgasse 6', 'Graz', NULL, '8010', 'Austria');
INSERT INTO `orders` VALUES (10772, 'LEHMS', 3, '2017-12-10 00:00:00', '2017-12-19 00:00:00', 2, 91.28, 'Magazinweg 7', 'Frankfurt a.M.', NULL, '60528', 'Germany');
INSERT INTO `orders` VALUES (10773, 'ERNSH', 1, '2017-12-11 00:00:00', '2017-12-16 00:00:00', 3, 96.43, 'Kirchgasse 6', 'Graz', NULL, '8010', 'Austria');
INSERT INTO `orders` VALUES (10774, 'FOLKO', 4, '2017-12-11 00:00:00', '2017-12-12 00:00:00', 1, 48.20, 'Åkergatan 24', 'Bräcke', NULL, 'S-844 67', 'Sweden');
INSERT INTO `orders` VALUES (10775, 'THECR', 7, '2017-12-12 00:00:00', '2017-12-26 00:00:00', 1, 20.25, '55 Grizzly Peak Rd.', 'Butte', 'MT', '59801', 'USA');
INSERT INTO `orders` VALUES (10776, 'ERNSH', 1, '2017-12-15 00:00:00', '2017-12-18 00:00:00', 3, 351.53, 'Kirchgasse 6', 'Graz', NULL, '8010', 'Austria');
INSERT INTO `orders` VALUES (10777, 'GOURL', 7, '2017-12-15 00:00:00', '2018-01-21 00:00:00', 2, 3.01, 'Av. Brasil-442', 'Campinas', 'SP', '04876-786', 'Brazil');
INSERT INTO `orders` VALUES (10778, 'BERGS', 3, '2017-12-16 00:00:00', '2017-12-24 00:00:00', 1, 6.79, 'Berguvsvägen  8', 'Luleå', NULL, 'S-958 22', 'Sweden');
INSERT INTO `orders` VALUES (10779, 'MORGK', 3, '2017-12-16 00:00:00', '2018-01-14 00:00:00', 2, 58.13, 'Heerstr. 22', 'Leipzig', NULL, '04179', 'Germany');
INSERT INTO `orders` VALUES (10780, 'LILAS', 2, '2017-12-16 00:00:00', '2017-12-25 00:00:00', 1, 42.13, 'Carrera 52 con Ave. Bolívar #65-98 Llano Largo', 'Barquisimeto', 'Lara', '3508', 'Venezuela');
INSERT INTO `orders` VALUES (10781, 'WARTH', 2, '2017-12-17 00:00:00', '2017-12-19 00:00:00', 3, 73.16, 'Torikatu 38', 'Oulu', NULL, '90110', 'Finland');
INSERT INTO `orders` VALUES (10782, 'CACTU', 9, '2017-12-17 00:00:00', '2017-12-22 00:00:00', 3, 1.10, 'Cerrito 333', 'Buenos Aires', NULL, '1010', 'Argentina');
INSERT INTO `orders` VALUES (10783, 'HANAR', 4, '2017-12-18 00:00:00', '2017-12-19 00:00:00', 2, 124.98, 'Rua do Paço-67', 'Rio de Janeiro', 'RJ', '05454-876', 'Brazil');
INSERT INTO `orders` VALUES (10784, 'MAGAA', 4, '2017-12-18 00:00:00', '2017-12-22 00:00:00', 3, 70.09, 'Via Ludovico il Moro 22', 'Bergamo', NULL, '24100', 'Italy');
INSERT INTO `orders` VALUES (10785, 'GROSR', 1, '2017-12-18 00:00:00', '2017-12-24 00:00:00', 3, 1.51, '5ª Ave. Los Palos Grandes', 'Caracas', 'DF', '1081', 'Venezuela');
INSERT INTO `orders` VALUES (10786, 'QUEE', 8, '2017-12-19 00:00:00', '2017-12-23 00:00:00', 1, 110.87, 'Alameda dos Canàrios-891', 'Sao Paulo', 'SP', '05487-020', 'Brazil');
INSERT INTO `orders` VALUES (10787, 'LAMAI', 2, '2017-12-19 00:00:00', '2017-12-26 00:00:00', 1, 249.93, '1 rue Alsace-Lorraine', 'Toulouse', NULL, '31000', 'France');
INSERT INTO `orders` VALUES (10788, 'QUICK', 1, '2017-12-22 00:00:00', '2018-01-19 00:00:00', 2, 42.70, 'Taucherstraße 10', 'Cunewalde', NULL, '01307', 'Germany');
INSERT INTO `orders` VALUES (10789, 'FOLIG', 1, '2017-12-22 00:00:00', '2017-12-31 00:00:00', 2, 100.60, '184-chaussée de Tournai', 'Lille', NULL, '59000', 'France');
INSERT INTO `orders` VALUES (10790, 'GOURL', 6, '2017-12-22 00:00:00', '2017-12-26 00:00:00', 1, 28.23, 'Av. Brasil-442', 'Campinas', 'SP', '04876-786', 'Brazil');
INSERT INTO `orders` VALUES (10791, 'FRANK', 6, '2017-12-23 00:00:00', '2018-01-01 00:00:00', 2, 16.85, 'Berliner Platz 43', 'Münche', NULL, '80805', 'Germany');
INSERT INTO `orders` VALUES (10792, 'WOLZA', 1, '2017-12-23 00:00:00', '2017-12-31 00:00:00', 3, 23.79, 'ul. Filtrowa 68', 'Warszawa', NULL, '01-012', 'Poland');
INSERT INTO `orders` VALUES (10793, 'AROUT', 3, '2017-12-24 00:00:00', '2018-01-08 00:00:00', 3, 4.52, 'Brook Farm Stratford St. Mary', 'Colchester', 'Essex', 'CO7 6JX', 'UK');
INSERT INTO `orders` VALUES (10794, 'QUEDE', 6, '2017-12-24 00:00:00', '2018-01-02 00:00:00', 1, 21.49, 'Rua da Panificadora-12', 'Rio de Janeiro', 'RJ', '02389-673', 'Brazil');
INSERT INTO `orders` VALUES (10795, 'ERNSH', 8, '2017-12-24 00:00:00', '2018-01-20 00:00:00', 2, 126.66, 'Kirchgasse 6', 'Graz', NULL, '8010', 'Austria');
INSERT INTO `orders` VALUES (10796, 'HILAA', 3, '2017-12-25 00:00:00', '2018-01-14 00:00:00', 1, 26.52, 'Carrera 22 con Ave. Carlos Soublette #8-35', 'San Cristóbal', 'Táchira', '5022', 'Venezuela');
INSERT INTO `orders` VALUES (10797, 'DRACD', 7, '2017-12-25 00:00:00', '2018-01-05 00:00:00', 2, 33.35, 'Walserweg 21', 'Aache', NULL, '52066', 'Germany');
INSERT INTO `orders` VALUES (10798, 'ISLAT', 2, '2017-12-26 00:00:00', '2018-01-05 00:00:00', 1, 2.33, 'Garden House Crowther Way', 'Cowes', 'Isle of Wight', 'PO31 7PJ', 'UK');
INSERT INTO `orders` VALUES (10799, 'KOENE', 9, '2017-12-26 00:00:00', '2018-01-05 00:00:00', 3, 30.76, 'Maubelstr. 90', 'Brandenburg', NULL, '14776', 'Germany');
INSERT INTO `orders` VALUES (10800, 'SEVES', 1, '2017-12-26 00:00:00', '2018-01-05 00:00:00', 3, 137.44, '90 Wadhurst Rd.', 'Londo', NULL, 'OX15 4NB', 'UK');
INSERT INTO `orders` VALUES (10801, 'BOLID', 4, '2017-12-29 00:00:00', '2017-12-31 00:00:00', 2, 97.09, 'C/ Araquil-67', 'Madrid', NULL, '28023', 'Spain');
INSERT INTO `orders` VALUES (10802, 'SIMOB', 4, '2017-12-29 00:00:00', '2018-01-02 00:00:00', 2, 257.26, 'Vinbæltet 34', 'Kobenhav', NULL, '1734', 'Denmark');
INSERT INTO `orders` VALUES (10803, 'WELLI', 4, '2017-12-30 00:00:00', '2018-01-06 00:00:00', 1, 55.23, 'Rua do Mercado-12', 'Resende', 'SP', '08737-363', 'Brazil');
INSERT INTO `orders` VALUES (10804, 'SEVES', 6, '2017-12-30 00:00:00', '2018-01-07 00:00:00', 2, 27.33, '90 Wadhurst Rd.', 'Londo', NULL, 'OX15 4NB', 'UK');
INSERT INTO `orders` VALUES (10805, 'THEBI', 2, '2017-12-30 00:00:00', '2018-01-09 00:00:00', 3, 237.34, '89 Jefferson Way Suite 2', 'Portland', 'OR', '97201', 'USA');
INSERT INTO `orders` VALUES (10806, 'VICTE', 3, '2017-12-31 00:00:00', '2018-01-05 00:00:00', 2, 22.11, '2-rue du Commerce', 'Lyo', NULL, '69004', 'France');
INSERT INTO `orders` VALUES (10807, 'FRANS', 4, '2017-12-31 00:00:00', '2018-01-30 00:00:00', 1, 1.36, 'Via Monte Bianco 34', 'Torino', NULL, '10100', 'Italy');
INSERT INTO `orders` VALUES (10808, 'OLDWO', 2, '2018-01-01 00:00:00', '2018-01-09 00:00:00', 3, 45.53, '2743 Bering St.', 'Anchorage', 'AK', '99508', 'USA');
INSERT INTO `orders` VALUES (10809, 'WELLI', 7, '2018-01-01 00:00:00', '2018-01-07 00:00:00', 1, 4.87, 'Rua do Mercado-12', 'Resende', 'SP', '08737-363', 'Brazil');
INSERT INTO `orders` VALUES (10810, 'LAUGB', 2, '2018-01-01 00:00:00', '2018-01-07 00:00:00', 3, 4.33, '2319 Elm St.', 'Vancouver', 'BC', 'V3F 2K1', 'Canada');
INSERT INTO `orders` VALUES (10811, 'LINOD', 8, '2018-01-02 00:00:00', '2018-01-08 00:00:00', 1, 31.22, 'Ave. 5 de Mayo Porlamar', 'I. de Margarita', 'Nueva Esparta', '4980', 'Venezuela');
INSERT INTO `orders` VALUES (10812, 'REGGC', 5, '2018-01-02 00:00:00', '2018-01-12 00:00:00', 1, 59.78, 'Strada Provinciale 124', 'Reggio Emilia', NULL, '42100', 'Italy');
INSERT INTO `orders` VALUES (10813, 'RICAR', 1, '2018-01-05 00:00:00', '2018-01-09 00:00:00', 1, 47.38, 'Av. Copacabana-267', 'Rio de Janeiro', 'RJ', '02389-890', 'Brazil');
INSERT INTO `orders` VALUES (10814, 'VICTE', 3, '2018-01-05 00:00:00', '2018-01-14 00:00:00', 3, 130.94, '2-rue du Commerce', 'Lyo', NULL, '69004', 'France');
INSERT INTO `orders` VALUES (10815, 'SAVEA', 2, '2018-01-05 00:00:00', '2018-01-14 00:00:00', 3, 14.62, '187 Suffolk Ln.', 'Boise', 'ID', '83720', 'USA');
INSERT INTO `orders` VALUES (10816, 'GREAL', 4, '2018-01-06 00:00:00', '2018-02-04 00:00:00', 2, 719.78, '2732 Baker Blvd.', 'Eugene', 'OR', '97403', 'USA');
INSERT INTO `orders` VALUES (10817, 'KOENE', 3, '2018-01-06 00:00:00', '2018-01-13 00:00:00', 2, 306.07, 'Maubelstr. 90', 'Brandenburg', NULL, '14776', 'Germany');
INSERT INTO `orders` VALUES (10818, 'MAGAA', 7, '2018-01-07 00:00:00', '2018-01-12 00:00:00', 3, 65.48, 'Via Ludovico il Moro 22', 'Bergamo', NULL, '24100', 'Italy');
INSERT INTO `orders` VALUES (10819, 'CACTU', 2, '2018-01-07 00:00:00', '2018-01-16 00:00:00', 3, 19.76, 'Cerrito 333', 'Buenos Aires', NULL, '1010', 'Argentina');
INSERT INTO `orders` VALUES (10820, 'RATTC', 3, '2018-01-07 00:00:00', '2018-01-13 00:00:00', 2, 37.52, '2817 Milton Dr.', 'Albuquerque', 'NM', '87110', 'USA');
INSERT INTO `orders` VALUES (10821, 'SPLIR', 1, '2018-01-08 00:00:00', '2018-01-15 00:00:00', 1, 36.68, 'P.O. Box 555', 'Lander', 'WY', '82520', 'USA');
INSERT INTO `orders` VALUES (10822, 'TRAIH', 6, '2018-01-08 00:00:00', '2018-01-16 00:00:00', 3, 7.00, '722 DaVinci Blvd.', 'Kirkland', 'WA', '98034', 'USA');
INSERT INTO `orders` VALUES (10823, 'LILAS', 5, '2018-01-09 00:00:00', '2018-01-13 00:00:00', 2, 163.97, 'Carrera 52 con Ave. Bolívar #65-98 Llano Largo', 'Barquisimeto', 'Lara', '3508', 'Venezuela');
INSERT INTO `orders` VALUES (10824, 'FOLKO', 8, '2018-01-09 00:00:00', '2018-01-30 00:00:00', 1, 1.23, 'Åkergatan 24', 'Bräcke', NULL, 'S-844 67', 'Sweden');
INSERT INTO `orders` VALUES (10825, 'DRACD', 1, '2018-01-09 00:00:00', '2018-01-14 00:00:00', 1, 79.25, 'Walserweg 21', 'Aache', NULL, '52066', 'Germany');
INSERT INTO `orders` VALUES (10826, 'BLONP', 6, '2018-01-12 00:00:00', '2018-02-06 00:00:00', 1, 7.09, '24-place Kléber', 'Strasbourg', NULL, '67000', 'France');
INSERT INTO `orders` VALUES (10827, 'BONAP', 1, '2018-01-12 00:00:00', '2018-02-06 00:00:00', 2, 63.54, '12-rue des Bouchers', 'Marseille', NULL, '13008', 'France');
INSERT INTO `orders` VALUES (10828, 'RANCH', 9, '2018-01-13 00:00:00', '2018-02-04 00:00:00', 1, 90.85, 'Av. del Libertador 900', 'Buenos Aires', NULL, '1010', 'Argentina');
INSERT INTO `orders` VALUES (10829, 'ISLAT', 9, '2018-01-13 00:00:00', '2018-01-23 00:00:00', 1, 154.72, 'Garden House Crowther Way', 'Cowes', 'Isle of Wight', 'PO31 7PJ', 'UK');
INSERT INTO `orders` VALUES (10830, 'TRADH', 4, '2018-01-13 00:00:00', '2018-01-21 00:00:00', 2, 81.83, 'Av. Inês de Castro-414', 'Sao Paulo', 'SP', '05634-030', 'Brazil');
INSERT INTO `orders` VALUES (10831, 'SANTG', 3, '2018-01-14 00:00:00', '2018-01-23 00:00:00', 2, 72.19, 'Erling Skakkes gate 78', 'Staver', NULL, '4110', 'Norway');
INSERT INTO `orders` VALUES (10832, 'LAMAI', 2, '2018-01-14 00:00:00', '2018-01-19 00:00:00', 2, 43.26, '1 rue Alsace-Lorraine', 'Toulouse', NULL, '31000', 'France');
INSERT INTO `orders` VALUES (10833, 'OTTIK', 6, '2018-01-15 00:00:00', '2018-01-23 00:00:00', 2, 71.49, 'Mehrheimerstr. 369', 'Köl', NULL, '50739', 'Germany');
INSERT INTO `orders` VALUES (10834, 'TRADH', 1, '2018-01-15 00:00:00', '2018-01-19 00:00:00', 3, 29.78, 'Av. Inês de Castro-414', 'Sao Paulo', 'SP', '05634-030', 'Brazil');
INSERT INTO `orders` VALUES (10835, 'ALFKI', 1, '2018-01-15 00:00:00', '2018-01-21 00:00:00', 3, 69.53, 'Obere Str. 57', 'Berli', NULL, '12209', 'Germany');
INSERT INTO `orders` VALUES (10836, 'ERNSH', 7, '2018-01-16 00:00:00', '2018-01-21 00:00:00', 1, 411.88, 'Kirchgasse 6', 'Graz', NULL, '8010', 'Austria');
INSERT INTO `orders` VALUES (10837, 'BERGS', 9, '2018-01-16 00:00:00', '2018-01-23 00:00:00', 3, 13.32, 'Berguvsvägen  8', 'Luleå', NULL, 'S-958 22', 'Sweden');
INSERT INTO `orders` VALUES (10838, 'LINOD', 3, '2018-01-19 00:00:00', '2018-01-23 00:00:00', 3, 59.28, 'Ave. 5 de Mayo Porlamar', 'I. de Margarita', 'Nueva Esparta', '4980', 'Venezuela');
INSERT INTO `orders` VALUES (10839, 'TRADH', 3, '2018-01-19 00:00:00', '2018-01-22 00:00:00', 3, 35.43, 'Av. Inês de Castro-414', 'Sao Paulo', 'SP', '05634-030', 'Brazil');
INSERT INTO `orders` VALUES (10840, 'LINOD', 4, '2018-01-19 00:00:00', '2018-02-16 00:00:00', 2, 2.71, 'Ave. 5 de Mayo Porlamar', 'I. de Margarita', 'Nueva Esparta', '4980', 'Venezuela');
INSERT INTO `orders` VALUES (10841, 'SUPRD', 5, '2018-01-20 00:00:00', '2018-01-29 00:00:00', 2, 424.30, 'Boulevard Tirou-255', 'Charleroi', NULL, 'B-6000', 'Belgium');
INSERT INTO `orders` VALUES (10842, 'TORTU', 1, '2018-01-20 00:00:00', '2018-01-29 00:00:00', 3, 54.42, 'Avda. Azteca 123', 'México D.F.', NULL, '05033', 'Mexico');
INSERT INTO `orders` VALUES (10843, 'VICTE', 4, '2018-01-21 00:00:00', '2018-01-26 00:00:00', 2, 9.26, '2-rue du Commerce', 'Lyo', NULL, '69004', 'France');
INSERT INTO `orders` VALUES (10844, 'PICCO', 8, '2018-01-21 00:00:00', '2018-01-26 00:00:00', 2, 25.22, 'Geislweg 14', 'Salzburg', NULL, '5020', 'Austria');
INSERT INTO `orders` VALUES (10845, 'QUICK', 8, '2018-01-21 00:00:00', '2018-01-30 00:00:00', 1, 212.98, 'Taucherstraße 10', 'Cunewalde', NULL, '01307', 'Germany');
INSERT INTO `orders` VALUES (10846, 'SUPRD', 2, '2018-01-22 00:00:00', '2018-01-23 00:00:00', 3, 56.46, 'Boulevard Tirou-255', 'Charleroi', NULL, 'B-6000', 'Belgium');
INSERT INTO `orders` VALUES (10847, 'SAVEA', 4, '2018-01-22 00:00:00', '2018-02-10 00:00:00', 3, 487.57, '187 Suffolk Ln.', 'Boise', 'ID', '83720', 'USA');
INSERT INTO `orders` VALUES (10848, 'CONSH', 7, '2018-01-23 00:00:00', '2018-01-29 00:00:00', 2, 38.24, 'Berkeley Gardens 12  Brewery', 'Londo', NULL, 'WX1 6LT', 'UK');
INSERT INTO `orders` VALUES (10849, 'KOENE', 9, '2018-01-23 00:00:00', '2018-01-30 00:00:00', 2, 0.56, 'Maubelstr. 90', 'Brandenburg', NULL, '14776', 'Germany');
INSERT INTO `orders` VALUES (10850, 'VICTE', 1, '2018-01-23 00:00:00', '2018-01-30 00:00:00', 1, 49.19, '2-rue du Commerce', 'Lyo', NULL, '69004', 'France');
INSERT INTO `orders` VALUES (10851, 'RICAR', 5, '2018-01-26 00:00:00', '2018-02-02 00:00:00', 1, 160.55, 'Av. Copacabana-267', 'Rio de Janeiro', 'RJ', '02389-890', 'Brazil');
INSERT INTO `orders` VALUES (10852, 'RATTC', 8, '2018-01-26 00:00:00', '2018-01-30 00:00:00', 1, 174.05, '2817 Milton Dr.', 'Albuquerque', 'NM', '87110', 'USA');
INSERT INTO `orders` VALUES (10853, 'BLAUS', 9, '2018-01-27 00:00:00', '2018-02-03 00:00:00', 2, 53.83, 'Forsterstr. 57', 'Mannheim', NULL, '68306', 'Germany');
INSERT INTO `orders` VALUES (10854, 'ERNSH', 3, '2018-01-27 00:00:00', '2018-02-05 00:00:00', 2, 100.22, 'Kirchgasse 6', 'Graz', NULL, '8010', 'Austria');
INSERT INTO `orders` VALUES (10855, 'OLDWO', 3, '2018-01-27 00:00:00', '2018-02-04 00:00:00', 1, 170.97, '2743 Bering St.', 'Anchorage', 'AK', '99508', 'USA');
INSERT INTO `orders` VALUES (10856, 'ANTO', 3, '2018-01-28 00:00:00', '2018-02-10 00:00:00', 2, 58.43, 'Mataderos  2312', 'México D.F.', NULL, '05023', 'Mexico');
INSERT INTO `orders` VALUES (10857, 'BERGS', 8, '2018-01-28 00:00:00', '2018-02-06 00:00:00', 2, 188.85, 'Berguvsvägen  8', 'Luleå', NULL, 'S-958 22', 'Sweden');
INSERT INTO `orders` VALUES (10858, 'LACOR', 2, '2018-01-29 00:00:00', '2018-02-03 00:00:00', 1, 52.51, '67-avenue de l\'\'Europe', 'Versailles', NULL, '78000', 'France');
INSERT INTO `orders` VALUES (10859, 'FRANK', 1, '2018-01-29 00:00:00', '2018-02-02 00:00:00', 2, 76.10, 'Berliner Platz 43', 'Münche', NULL, '80805', 'Germany');
INSERT INTO `orders` VALUES (10860, 'FRANR', 3, '2018-01-29 00:00:00', '2018-02-04 00:00:00', 3, 19.26, '54-rue Royale', 'Nantes', NULL, '44000', 'France');
INSERT INTO `orders` VALUES (10861, 'WHITC', 4, '2018-01-30 00:00:00', '2018-02-17 00:00:00', 2, 14.93, '1029 - 12th Ave. S.', 'Seattle', 'WA', '98124', 'USA');
INSERT INTO `orders` VALUES (10862, 'LEHMS', 8, '2018-01-30 00:00:00', '2018-02-02 00:00:00', 2, 53.23, 'Magazinweg 7', 'Frankfurt a.M.', NULL, '60528', 'Germany');
INSERT INTO `orders` VALUES (10863, 'HILAA', 4, '2018-02-02 00:00:00', '2018-02-17 00:00:00', 2, 30.26, 'Carrera 22 con Ave. Carlos Soublette #8-35', 'San Cristóbal', 'Táchira', '5022', 'Venezuela');
INSERT INTO `orders` VALUES (10864, 'AROUT', 4, '2018-02-02 00:00:00', '2018-02-09 00:00:00', 2, 3.04, 'Brook Farm Stratford St. Mary', 'Colchester', 'Essex', 'CO7 6JX', 'UK');
INSERT INTO `orders` VALUES (10865, 'QUICK', 2, '2018-02-02 00:00:00', '2018-02-12 00:00:00', 1, 348.14, 'Taucherstraße 10', 'Cunewalde', NULL, '01307', 'Germany');
INSERT INTO `orders` VALUES (10866, 'BERGS', 5, '2018-02-03 00:00:00', '2018-02-12 00:00:00', 1, 109.11, 'Berguvsvägen  8', 'Luleå', NULL, 'S-958 22', 'Sweden');
INSERT INTO `orders` VALUES (10867, 'LONEP', 6, '2018-02-03 00:00:00', '2018-02-11 00:00:00', 1, 1.93, '89 Chiaroscuro Rd.', 'Portland', 'OR', '97219', 'USA');
INSERT INTO `orders` VALUES (10868, 'QUEE', 7, '2018-02-04 00:00:00', '2018-02-23 00:00:00', 2, 191.27, 'Alameda dos Canàrios-891', 'Sao Paulo', 'SP', '05487-020', 'Brazil');
INSERT INTO `orders` VALUES (10869, 'SEVES', 5, '2018-02-04 00:00:00', '2018-02-09 00:00:00', 1, 143.28, '90 Wadhurst Rd.', 'Londo', NULL, 'OX15 4NB', 'UK');
INSERT INTO `orders` VALUES (10870, 'WOLZA', 5, '2018-02-04 00:00:00', '2018-02-13 00:00:00', 3, 12.04, 'ul. Filtrowa 68', 'Warszawa', NULL, '01-012', 'Poland');
INSERT INTO `orders` VALUES (10871, 'BONAP', 9, '2018-02-05 00:00:00', '2018-02-10 00:00:00', 2, 112.27, '12-rue des Bouchers', 'Marseille', NULL, '13008', 'France');
INSERT INTO `orders` VALUES (10872, 'GODOS', 5, '2018-02-05 00:00:00', '2018-02-09 00:00:00', 2, 175.32, 'C/ Romero-33', 'Sevilla', NULL, '41101', 'Spain');
INSERT INTO `orders` VALUES (10873, 'WILMK', 4, '2018-02-06 00:00:00', '2018-02-09 00:00:00', 1, 0.82, 'Keskuskatu 45', 'Helsinki', NULL, '21240', 'Finland');
INSERT INTO `orders` VALUES (10874, 'GODOS', 5, '2018-02-06 00:00:00', '2018-02-11 00:00:00', 2, 19.58, 'C/ Romero-33', 'Sevilla', NULL, '41101', 'Spain');
INSERT INTO `orders` VALUES (10875, 'BERGS', 4, '2018-02-06 00:00:00', '2018-03-03 00:00:00', 2, 32.37, 'Berguvsvägen  8', 'Luleå', NULL, 'S-958 22', 'Sweden');
INSERT INTO `orders` VALUES (10876, 'BONAP', 7, '2018-02-09 00:00:00', '2018-02-12 00:00:00', 3, 60.42, '12-rue des Bouchers', 'Marseille', NULL, '13008', 'France');
INSERT INTO `orders` VALUES (10877, 'RICAR', 1, '2018-02-09 00:00:00', '2018-02-19 00:00:00', 1, 38.06, 'Av. Copacabana-267', 'Rio de Janeiro', 'RJ', '02389-890', 'Brazil');
INSERT INTO `orders` VALUES (10878, 'QUICK', 4, '2018-02-10 00:00:00', '2018-02-12 00:00:00', 1, 46.69, 'Taucherstraße 10', 'Cunewalde', NULL, '01307', 'Germany');
INSERT INTO `orders` VALUES (10879, 'WILMK', 3, '2018-02-10 00:00:00', '2018-02-12 00:00:00', 3, 8.50, 'Keskuskatu 45', 'Helsinki', NULL, '21240', 'Finland');
INSERT INTO `orders` VALUES (10880, 'FOLKO', 7, '2018-02-10 00:00:00', '2018-02-18 00:00:00', 1, 88.01, 'Åkergatan 24', 'Bräcke', NULL, 'S-844 67', 'Sweden');
INSERT INTO `orders` VALUES (10881, 'CACTU', 4, '2018-02-11 00:00:00', '2018-02-18 00:00:00', 1, 2.84, 'Cerrito 333', 'Buenos Aires', NULL, '1010', 'Argentina');
INSERT INTO `orders` VALUES (10882, 'SAVEA', 4, '2018-02-11 00:00:00', '2018-02-20 00:00:00', 3, 23.10, '187 Suffolk Ln.', 'Boise', 'ID', '83720', 'USA');
INSERT INTO `orders` VALUES (10883, 'LONEP', 8, '2018-02-12 00:00:00', '2018-02-20 00:00:00', 3, 0.53, '89 Chiaroscuro Rd.', 'Portland', 'OR', '97219', 'USA');
INSERT INTO `orders` VALUES (10884, 'LETSS', 4, '2018-02-12 00:00:00', '2018-02-13 00:00:00', 2, 90.97, '87 Polk St. Suite 5', 'San Francisco', 'CA', '94117', 'USA');
INSERT INTO `orders` VALUES (10885, 'SUPRD', 6, '2018-02-12 00:00:00', '2018-02-18 00:00:00', 3, 5.64, 'Boulevard Tirou-255', 'Charleroi', NULL, 'B-6000', 'Belgium');
INSERT INTO `orders` VALUES (10886, 'HANAR', 1, '2018-02-13 00:00:00', '2018-03-02 00:00:00', 1, 4.99, 'Rua do Paço-67', 'Rio de Janeiro', 'RJ', '05454-876', 'Brazil');
INSERT INTO `orders` VALUES (10887, 'GALED', 8, '2018-02-13 00:00:00', '2018-02-16 00:00:00', 3, 1.25, 'Rambla de Cataluña-23', 'Barcelona', NULL, '8022', 'Spain');
INSERT INTO `orders` VALUES (10888, 'GODOS', 1, '2018-02-16 00:00:00', '2018-02-23 00:00:00', 2, 51.87, 'C/ Romero-33', 'Sevilla', NULL, '41101', 'Spain');
INSERT INTO `orders` VALUES (10889, 'RATTC', 9, '2018-02-16 00:00:00', '2018-02-23 00:00:00', 3, 280.61, '2817 Milton Dr.', 'Albuquerque', 'NM', '87110', 'USA');
INSERT INTO `orders` VALUES (10890, 'DUMO', 7, '2018-02-16 00:00:00', '2018-02-18 00:00:00', 1, 32.76, '67-rue des Cinquante Otages', 'Nantes', NULL, '44000', 'France');
INSERT INTO `orders` VALUES (10891, 'LEHMS', 7, '2018-02-17 00:00:00', '2018-02-19 00:00:00', 2, 20.37, 'Magazinweg 7', 'Frankfurt a.M.', NULL, '60528', 'Germany');
INSERT INTO `orders` VALUES (10892, 'MAISD', 4, '2018-02-17 00:00:00', '2018-02-19 00:00:00', 2, 120.27, 'Rue Joseph-Bens 532', 'Bruxelles', NULL, 'B-1180', 'Belgium');
INSERT INTO `orders` VALUES (10893, 'KOENE', 9, '2018-02-18 00:00:00', '2018-02-20 00:00:00', 2, 77.78, 'Maubelstr. 90', 'Brandenburg', NULL, '14776', 'Germany');
INSERT INTO `orders` VALUES (10894, 'SAVEA', 1, '2018-02-18 00:00:00', '2018-02-20 00:00:00', 1, 116.13, '187 Suffolk Ln.', 'Boise', 'ID', '83720', 'USA');
INSERT INTO `orders` VALUES (10895, 'ERNSH', 3, '2018-02-18 00:00:00', '2018-02-23 00:00:00', 1, 162.75, 'Kirchgasse 6', 'Graz', NULL, '8010', 'Austria');
INSERT INTO `orders` VALUES (10896, 'MAISD', 7, '2018-02-19 00:00:00', '2018-02-27 00:00:00', 3, 32.45, 'Rue Joseph-Bens 532', 'Bruxelles', NULL, 'B-1180', 'Belgium');
INSERT INTO `orders` VALUES (10897, 'HUNGO', 3, '2018-02-19 00:00:00', '2018-02-25 00:00:00', 2, 603.54, '8 Johnstown Road', 'Cork', 'Co. Cork', NULL, 'Ireland');
INSERT INTO `orders` VALUES (10898, 'OCEA', 4, '2018-02-20 00:00:00', '2018-03-06 00:00:00', 2, 1.27, 'Ing. Gustavo Moncada 8585 Piso 20-A', 'Buenos Aires', NULL, '1010', 'Argentina');
INSERT INTO `orders` VALUES (10899, 'LILAS', 5, '2018-02-20 00:00:00', '2018-02-26 00:00:00', 3, 1.21, 'Carrera 52 con Ave. Bolívar #65-98 Llano Largo', 'Barquisimeto', 'Lara', '3508', 'Venezuela');
INSERT INTO `orders` VALUES (10900, 'WELLI', 1, '2018-02-20 00:00:00', '2018-03-04 00:00:00', 2, 1.66, 'Rua do Mercado-12', 'Resende', 'SP', '08737-363', 'Brazil');
INSERT INTO `orders` VALUES (10901, 'HILAA', 4, '2018-02-23 00:00:00', '2018-02-26 00:00:00', 1, 62.09, 'Carrera 22 con Ave. Carlos Soublette #8-35', 'San Cristóbal', 'Táchira', '5022', 'Venezuela');
INSERT INTO `orders` VALUES (10902, 'FOLKO', 1, '2018-02-23 00:00:00', '2018-03-03 00:00:00', 1, 44.15, 'Åkergatan 24', 'Bräcke', NULL, 'S-844 67', 'Sweden');
INSERT INTO `orders` VALUES (10903, 'HANAR', 3, '2018-02-24 00:00:00', '2018-03-04 00:00:00', 3, 36.71, 'Rua do Paço-67', 'Rio de Janeiro', 'RJ', '05454-876', 'Brazil');
INSERT INTO `orders` VALUES (10904, 'WHITC', 3, '2018-02-24 00:00:00', '2018-02-27 00:00:00', 3, 162.95, '1029 - 12th Ave. S.', 'Seattle', 'WA', '98124', 'USA');
INSERT INTO `orders` VALUES (10905, 'WELLI', 9, '2018-02-24 00:00:00', '2018-03-06 00:00:00', 2, 13.72, 'Rua do Mercado-12', 'Resende', 'SP', '08737-363', 'Brazil');
INSERT INTO `orders` VALUES (10906, 'WOLZA', 4, '2018-02-25 00:00:00', '2018-03-03 00:00:00', 3, 26.29, 'ul. Filtrowa 68', 'Warszawa', NULL, '01-012', 'Poland');
INSERT INTO `orders` VALUES (10907, 'SPECD', 6, '2018-02-25 00:00:00', '2018-02-27 00:00:00', 3, 9.19, '25-rue Lauristo', 'Paris', NULL, '75016', 'France');
INSERT INTO `orders` VALUES (10908, 'REGGC', 4, '2018-02-26 00:00:00', '2018-03-06 00:00:00', 2, 32.96, 'Strada Provinciale 124', 'Reggio Emilia', NULL, '42100', 'Italy');
INSERT INTO `orders` VALUES (10909, 'SANTG', 1, '2018-02-26 00:00:00', '2018-03-10 00:00:00', 2, 53.05, 'Erling Skakkes gate 78', 'Staver', NULL, '4110', 'Norway');
INSERT INTO `orders` VALUES (10910, 'WILMK', 1, '2018-02-26 00:00:00', '2018-03-04 00:00:00', 3, 38.11, 'Keskuskatu 45', 'Helsinki', NULL, '21240', 'Finland');
INSERT INTO `orders` VALUES (10911, 'GODOS', 3, '2018-02-26 00:00:00', '2018-03-05 00:00:00', 1, 38.19, 'C/ Romero-33', 'Sevilla', NULL, '41101', 'Spain');
INSERT INTO `orders` VALUES (10912, 'HUNGO', 2, '2018-02-26 00:00:00', '2018-03-18 00:00:00', 2, 580.91, '8 Johnstown Road', 'Cork', 'Co. Cork', NULL, 'Ireland');
INSERT INTO `orders` VALUES (10913, 'QUEE', 4, '2018-02-26 00:00:00', '2018-03-04 00:00:00', 1, 33.05, 'Alameda dos Canàrios-891', 'Sao Paulo', 'SP', '05487-020', 'Brazil');
INSERT INTO `orders` VALUES (10914, 'QUEE', 6, '2018-02-27 00:00:00', '2018-03-02 00:00:00', 1, 21.19, 'Alameda dos Canàrios-891', 'Sao Paulo', 'SP', '05487-020', 'Brazil');
INSERT INTO `orders` VALUES (10915, 'TORTU', 2, '2018-02-27 00:00:00', '2018-03-02 00:00:00', 2, 3.51, 'Avda. Azteca 123', 'México D.F.', NULL, '05033', 'Mexico');
INSERT INTO `orders` VALUES (10916, 'RANCH', 1, '2018-02-27 00:00:00', '2018-03-09 00:00:00', 2, 63.77, 'Av. del Libertador 900', 'Buenos Aires', NULL, '1010', 'Argentina');
INSERT INTO `orders` VALUES (10917, 'ROMEY', 4, '2018-03-02 00:00:00', '2018-03-11 00:00:00', 2, 8.29, 'Gran Vía-1', 'Madrid', NULL, '28001', 'Spain');
INSERT INTO `orders` VALUES (10918, 'BOTTM', 3, '2018-03-02 00:00:00', '2018-03-11 00:00:00', 3, 48.83, '23 Tsawassen Blvd.', 'Tsawasse', 'BC', 'T2F 8M4', 'Canada');
INSERT INTO `orders` VALUES (10919, 'LINOD', 2, '2018-03-02 00:00:00', '2018-03-04 00:00:00', 2, 19.80, 'Ave. 5 de Mayo Porlamar', 'I. de Margarita', 'Nueva Esparta', '4980', 'Venezuela');
INSERT INTO `orders` VALUES (10920, 'AROUT', 4, '2018-03-03 00:00:00', '2018-03-09 00:00:00', 2, 29.61, 'Brook Farm Stratford St. Mary', 'Colchester', 'Essex', 'CO7 6JX', 'UK');
INSERT INTO `orders` VALUES (10921, 'VAFFE', 1, '2018-03-03 00:00:00', '2018-03-09 00:00:00', 1, 176.48, 'Smagsloget 45', 'Århus', NULL, '8200', 'Denmark');
INSERT INTO `orders` VALUES (10922, 'HANAR', 5, '2018-03-03 00:00:00', '2018-03-05 00:00:00', 3, 62.74, 'Rua do Paço-67', 'Rio de Janeiro', 'RJ', '05454-876', 'Brazil');
INSERT INTO `orders` VALUES (10923, 'LAMAI', 7, '2018-03-03 00:00:00', '2018-03-13 00:00:00', 3, 68.26, '1 rue Alsace-Lorraine', 'Toulouse', NULL, '31000', 'France');
INSERT INTO `orders` VALUES (10924, 'BERGS', 3, '2018-03-04 00:00:00', '2018-04-08 00:00:00', 2, 151.52, 'Berguvsvägen  8', 'Luleå', NULL, 'S-958 22', 'Sweden');
INSERT INTO `orders` VALUES (10925, 'HANAR', 3, '2018-03-04 00:00:00', '2018-03-13 00:00:00', 1, 2.27, 'Rua do Paço-67', 'Rio de Janeiro', 'RJ', '05454-876', 'Brazil');
INSERT INTO `orders` VALUES (10926, 'ANATR', 4, '2018-03-04 00:00:00', '2018-03-11 00:00:00', 3, 39.92, 'Avda. de la Constitución 2222', 'México D.F.', NULL, '05021', 'Mexico');
INSERT INTO `orders` VALUES (10927, 'LACOR', 4, '2018-03-05 00:00:00', '2018-04-08 00:00:00', 1, 19.79, '67-avenue de l\'\'Europe', 'Versailles', NULL, '78000', 'France');
INSERT INTO `orders` VALUES (10928, 'GALED', 1, '2018-03-05 00:00:00', '2018-03-18 00:00:00', 1, 1.36, 'Rambla de Cataluña-23', 'Barcelona', NULL, '8022', 'Spain');
INSERT INTO `orders` VALUES (10929, 'FRANK', 6, '2018-03-05 00:00:00', '2018-03-12 00:00:00', 1, 33.93, 'Berliner Platz 43', 'Münche', NULL, '80805', 'Germany');
INSERT INTO `orders` VALUES (10930, 'SUPRD', 4, '2018-03-06 00:00:00', '2018-03-18 00:00:00', 3, 15.55, 'Boulevard Tirou-255', 'Charleroi', NULL, 'B-6000', 'Belgium');
INSERT INTO `orders` VALUES (10931, 'RICSU', 4, '2018-03-06 00:00:00', '2018-03-19 00:00:00', 2, 13.60, 'Starenweg 5', 'Genève', NULL, '1204', 'Switzerland');
INSERT INTO `orders` VALUES (10932, 'BONAP', 8, '2018-03-06 00:00:00', '2018-03-24 00:00:00', 1, 134.64, '12-rue des Bouchers', 'Marseille', NULL, '13008', 'France');
INSERT INTO `orders` VALUES (10933, 'ISLAT', 6, '2018-03-06 00:00:00', '2018-03-16 00:00:00', 3, 54.15, 'Garden House Crowther Way', 'Cowes', 'Isle of Wight', 'PO31 7PJ', 'UK');
INSERT INTO `orders` VALUES (10934, 'LEHMS', 3, '2018-03-09 00:00:00', '2018-03-12 00:00:00', 3, 32.01, 'Magazinweg 7', 'Frankfurt a.M.', NULL, '60528', 'Germany');
INSERT INTO `orders` VALUES (10935, 'WELLI', 4, '2018-03-09 00:00:00', '2018-03-18 00:00:00', 3, 47.59, 'Rua do Mercado-12', 'Resende', 'SP', '08737-363', 'Brazil');
INSERT INTO `orders` VALUES (10936, 'GREAL', 3, '2018-03-09 00:00:00', '2018-03-18 00:00:00', 2, 33.68, '2732 Baker Blvd.', 'Eugene', 'OR', '97403', 'USA');
INSERT INTO `orders` VALUES (10937, 'CACTU', 7, '2018-03-10 00:00:00', '2018-03-13 00:00:00', 3, 31.51, 'Cerrito 333', 'Buenos Aires', NULL, '1010', 'Argentina');
INSERT INTO `orders` VALUES (10938, 'QUICK', 3, '2018-03-10 00:00:00', '2018-03-16 00:00:00', 2, 31.89, 'Taucherstraße 10', 'Cunewalde', NULL, '01307', 'Germany');
INSERT INTO `orders` VALUES (10939, 'MAGAA', 2, '2018-03-10 00:00:00', '2018-03-13 00:00:00', 2, 76.33, 'Via Ludovico il Moro 22', 'Bergamo', NULL, '24100', 'Italy');
INSERT INTO `orders` VALUES (10940, 'BONAP', 8, '2018-03-11 00:00:00', '2018-03-23 00:00:00', 3, 19.77, '12-rue des Bouchers', 'Marseille', NULL, '13008', 'France');
INSERT INTO `orders` VALUES (10941, 'SAVEA', 7, '2018-03-11 00:00:00', '2018-03-20 00:00:00', 2, 400.81, '187 Suffolk Ln.', 'Boise', 'ID', '83720', 'USA');
INSERT INTO `orders` VALUES (10942, 'REGGC', 9, '2018-03-11 00:00:00', '2018-03-18 00:00:00', 3, 17.95, 'Strada Provinciale 124', 'Reggio Emilia', NULL, '42100', 'Italy');
INSERT INTO `orders` VALUES (10943, 'BSBEV', 4, '2018-03-11 00:00:00', '2018-03-19 00:00:00', 2, 2.17, 'Fauntleroy Circus', 'Londo', NULL, 'EC2 5NT', 'UK');
INSERT INTO `orders` VALUES (10944, 'BOTTM', 6, '2018-03-12 00:00:00', '2018-03-13 00:00:00', 3, 52.92, '23 Tsawassen Blvd.', 'Tsawasse', 'BC', 'T2F 8M4', 'Canada');
INSERT INTO `orders` VALUES (10945, 'MORGK', 4, '2018-03-12 00:00:00', '2018-03-18 00:00:00', 1, 10.22, 'Heerstr. 22', 'Leipzig', NULL, '04179', 'Germany');
INSERT INTO `orders` VALUES (10946, 'VAFFE', 1, '2018-03-12 00:00:00', '2018-03-19 00:00:00', 2, 27.20, 'Smagsloget 45', 'Århus', NULL, '8200', 'Denmark');
INSERT INTO `orders` VALUES (10947, 'BSBEV', 3, '2018-03-13 00:00:00', '2018-03-16 00:00:00', 2, 3.26, 'Fauntleroy Circus', 'Londo', NULL, 'EC2 5NT', 'UK');
INSERT INTO `orders` VALUES (10948, 'GODOS', 3, '2018-03-13 00:00:00', '2018-03-19 00:00:00', 3, 23.39, 'C/ Romero-33', 'Sevilla', NULL, '41101', 'Spain');
INSERT INTO `orders` VALUES (10949, 'BOTTM', 2, '2018-03-13 00:00:00', '2018-03-17 00:00:00', 3, 74.44, '23 Tsawassen Blvd.', 'Tsawasse', 'BC', 'T2F 8M4', 'Canada');
INSERT INTO `orders` VALUES (10950, 'MAGAA', 1, '2018-03-16 00:00:00', '2018-03-23 00:00:00', 2, 2.50, 'Via Ludovico il Moro 22', 'Bergamo', NULL, '24100', 'Italy');
INSERT INTO `orders` VALUES (10951, 'RICSU', 9, '2018-03-16 00:00:00', '2018-04-07 00:00:00', 2, 30.85, 'Starenweg 5', 'Genève', NULL, '1204', 'Switzerland');
INSERT INTO `orders` VALUES (10952, 'ALFKI', 1, '2018-03-16 00:00:00', '2018-03-24 00:00:00', 1, 40.42, 'Obere Str. 57', 'Berli', NULL, '12209', 'Germany');
INSERT INTO `orders` VALUES (10953, 'AROUT', 9, '2018-03-16 00:00:00', '2018-03-25 00:00:00', 2, 23.72, 'Brook Farm Stratford St. Mary', 'Colchester', 'Essex', 'CO7 6JX', 'UK');
INSERT INTO `orders` VALUES (10954, 'LINOD', 5, '2018-03-17 00:00:00', '2018-03-20 00:00:00', 1, 27.91, 'Ave. 5 de Mayo Porlamar', 'I. de Margarita', 'Nueva Esparta', '4980', 'Venezuela');
INSERT INTO `orders` VALUES (10955, 'FOLKO', 8, '2018-03-17 00:00:00', '2018-03-20 00:00:00', 2, 3.26, 'Åkergatan 24', 'Bräcke', NULL, 'S-844 67', 'Sweden');
INSERT INTO `orders` VALUES (10956, 'BLAUS', 6, '2018-03-17 00:00:00', '2018-03-20 00:00:00', 2, 44.65, 'Forsterstr. 57', 'Mannheim', NULL, '68306', 'Germany');
INSERT INTO `orders` VALUES (10957, 'HILAA', 8, '2018-03-18 00:00:00', '2018-03-27 00:00:00', 3, 105.36, 'Carrera 22 con Ave. Carlos Soublette #8-35', 'San Cristóbal', 'Táchira', '5022', 'Venezuela');
INSERT INTO `orders` VALUES (10958, 'OCEA', 7, '2018-03-18 00:00:00', '2018-03-27 00:00:00', 2, 49.56, 'Ing. Gustavo Moncada 8585 Piso 20-A', 'Buenos Aires', NULL, '1010', 'Argentina');
INSERT INTO `orders` VALUES (10959, 'GOURL', 6, '2018-03-18 00:00:00', '2018-03-23 00:00:00', 2, 4.98, 'Av. Brasil-442', 'Campinas', 'SP', '04876-786', 'Brazil');
INSERT INTO `orders` VALUES (10960, 'HILAA', 3, '2018-03-19 00:00:00', '2018-04-08 00:00:00', 1, 2.08, 'Carrera 22 con Ave. Carlos Soublette #8-35', 'San Cristóbal', 'Táchira', '5022', 'Venezuela');
INSERT INTO `orders` VALUES (10961, 'QUEE', 8, '2018-03-19 00:00:00', '2018-03-30 00:00:00', 1, 104.47, 'Alameda dos Canàrios-891', 'Sao Paulo', 'SP', '05487-020', 'Brazil');
INSERT INTO `orders` VALUES (10962, 'QUICK', 8, '2018-03-19 00:00:00', '2018-03-23 00:00:00', 2, 275.79, 'Taucherstraße 10', 'Cunewalde', NULL, '01307', 'Germany');
INSERT INTO `orders` VALUES (10963, 'FURIB', 9, '2018-03-19 00:00:00', '2018-03-26 00:00:00', 3, 2.70, 'Jardim das rosas n. 32', 'Lisboa', NULL, '1675', 'Portugal');
INSERT INTO `orders` VALUES (10964, 'SPECD', 3, '2018-03-20 00:00:00', '2018-03-24 00:00:00', 2, 87.38, '25-rue Lauristo', 'Paris', NULL, '75016', 'France');
INSERT INTO `orders` VALUES (10965, 'OLDWO', 6, '2018-03-20 00:00:00', '2018-03-30 00:00:00', 3, 144.38, '2743 Bering St.', 'Anchorage', 'AK', '99508', 'USA');
INSERT INTO `orders` VALUES (10966, 'CHOPS', 4, '2018-03-20 00:00:00', '2018-04-08 00:00:00', 1, 27.19, 'Hauptstr. 31', 'Ber', NULL, '3012', 'Switzerland');
INSERT INTO `orders` VALUES (10967, 'TOMSP', 2, '2018-03-23 00:00:00', '2018-04-02 00:00:00', 2, 62.22, 'Luisenstr. 48', 'Münster', NULL, '44087', 'Germany');
INSERT INTO `orders` VALUES (10968, 'ERNSH', 1, '2018-03-23 00:00:00', '2018-04-01 00:00:00', 3, 74.60, 'Kirchgasse 6', 'Graz', NULL, '8010', 'Austria');
INSERT INTO `orders` VALUES (10969, 'COMMI', 1, '2018-03-23 00:00:00', '2018-03-30 00:00:00', 2, 0.21, 'Av. dos Lusíadas-23', 'Sao Paulo', 'SP', '05432-043', 'Brazil');
INSERT INTO `orders` VALUES (10970, 'BOLID', 9, '2018-03-24 00:00:00', '2018-04-24 00:00:00', 1, 16.16, 'C/ Araquil-67', 'Madrid', NULL, '28023', 'Spain');
INSERT INTO `orders` VALUES (10971, 'FRANR', 2, '2018-03-24 00:00:00', '2018-04-02 00:00:00', 2, 121.82, '54-rue Royale', 'Nantes', NULL, '44000', 'France');
INSERT INTO `orders` VALUES (10972, 'LACOR', 4, '2018-03-24 00:00:00', '2018-03-26 00:00:00', 2, 0.02, '67-avenue de l\'\'Europe', 'Versailles', NULL, '78000', 'France');
INSERT INTO `orders` VALUES (10973, 'LACOR', 6, '2018-03-24 00:00:00', '2018-03-27 00:00:00', 2, 15.17, '67-avenue de l\'\'Europe', 'Versailles', NULL, '78000', 'France');
INSERT INTO `orders` VALUES (10974, 'SPLIR', 3, '2018-03-25 00:00:00', '2018-04-03 00:00:00', 3, 12.96, 'P.O. Box 555', 'Lander', 'WY', '82520', 'USA');
INSERT INTO `orders` VALUES (10975, 'BOTTM', 1, '2018-03-25 00:00:00', '2018-03-27 00:00:00', 3, 32.27, '23 Tsawassen Blvd.', 'Tsawasse', 'BC', 'T2F 8M4', 'Canada');
INSERT INTO `orders` VALUES (10976, 'HILAA', 1, '2018-03-25 00:00:00', '2018-04-03 00:00:00', 1, 37.97, 'Carrera 22 con Ave. Carlos Soublette #8-35', 'San Cristóbal', 'Táchira', '5022', 'Venezuela');
INSERT INTO `orders` VALUES (10977, 'FOLKO', 8, '2018-03-26 00:00:00', '2018-04-10 00:00:00', 3, 208.50, 'Åkergatan 24', 'Bräcke', NULL, 'S-844 67', 'Sweden');
INSERT INTO `orders` VALUES (10978, 'MAISD', 9, '2018-03-26 00:00:00', '2018-04-23 00:00:00', 2, 32.82, 'Rue Joseph-Bens 532', 'Bruxelles', NULL, 'B-1180', 'Belgium');
INSERT INTO `orders` VALUES (10979, 'ERNSH', 8, '2018-03-26 00:00:00', '2018-03-31 00:00:00', 2, 353.07, 'Kirchgasse 6', 'Graz', NULL, '8010', 'Austria');
INSERT INTO `orders` VALUES (10980, 'FOLKO', 4, '2018-03-27 00:00:00', '2018-04-17 00:00:00', 1, 1.26, 'Åkergatan 24', 'Bräcke', NULL, 'S-844 67', 'Sweden');
INSERT INTO `orders` VALUES (10981, 'HANAR', 1, '2018-03-27 00:00:00', '2018-04-02 00:00:00', 2, 193.37, 'Rua do Paço-67', 'Rio de Janeiro', 'RJ', '05454-876', 'Brazil');
INSERT INTO `orders` VALUES (10982, 'BOTTM', 2, '2018-03-27 00:00:00', '2018-04-08 00:00:00', 1, 14.01, '23 Tsawassen Blvd.', 'Tsawasse', 'BC', 'T2F 8M4', 'Canada');
INSERT INTO `orders` VALUES (10983, 'SAVEA', 2, '2018-03-27 00:00:00', '2018-04-06 00:00:00', 2, 657.54, '187 Suffolk Ln.', 'Boise', 'ID', '83720', 'USA');
INSERT INTO `orders` VALUES (10984, 'SAVEA', 1, '2018-03-30 00:00:00', '2018-04-03 00:00:00', 3, 211.22, '187 Suffolk Ln.', 'Boise', 'ID', '83720', 'USA');
INSERT INTO `orders` VALUES (10985, 'HUNGO', 2, '2018-03-30 00:00:00', '2018-04-02 00:00:00', 1, 91.51, '8 Johnstown Road', 'Cork', 'Co. Cork', NULL, 'Ireland');
INSERT INTO `orders` VALUES (10986, 'OCEA', 8, '2018-03-30 00:00:00', '2018-04-21 00:00:00', 2, 217.86, 'Ing. Gustavo Moncada 8585 Piso 20-A', 'Buenos Aires', NULL, '1010', 'Argentina');
INSERT INTO `orders` VALUES (10987, 'EASTC', 8, '2018-03-31 00:00:00', '2018-04-06 00:00:00', 1, 185.48, '35 King George', 'Londo', NULL, 'WX3 6FW', 'UK');
INSERT INTO `orders` VALUES (10988, 'RATTC', 3, '2018-03-31 00:00:00', '2018-04-10 00:00:00', 2, 61.14, '2817 Milton Dr.', 'Albuquerque', 'NM', '87110', 'USA');
INSERT INTO `orders` VALUES (10989, 'QUEDE', 2, '2018-03-31 00:00:00', '2018-04-02 00:00:00', 1, 34.76, 'Rua da Panificadora-12', 'Rio de Janeiro', 'RJ', '02389-673', 'Brazil');
INSERT INTO `orders` VALUES (10990, 'ERNSH', 2, '2018-04-01 00:00:00', '2018-04-07 00:00:00', 3, 117.61, 'Kirchgasse 6', 'Graz', NULL, '8010', 'Austria');
INSERT INTO `orders` VALUES (10991, 'QUICK', 1, '2018-04-01 00:00:00', '2018-04-07 00:00:00', 1, 38.51, 'Taucherstraße 10', 'Cunewalde', NULL, '01307', 'Germany');
INSERT INTO `orders` VALUES (10992, 'THEBI', 1, '2018-04-01 00:00:00', '2018-04-03 00:00:00', 3, 4.27, '89 Jefferson Way Suite 2', 'Portland', 'OR', '97201', 'USA');
INSERT INTO `orders` VALUES (10993, 'FOLKO', 7, '2018-04-01 00:00:00', '2018-04-10 00:00:00', 3, 8.81, 'Åkergatan 24', 'Bräcke', NULL, 'S-844 67', 'Sweden');
INSERT INTO `orders` VALUES (10994, 'VAFFE', 2, '2018-04-02 00:00:00', '2018-04-09 00:00:00', 3, 65.53, 'Smagsloget 45', 'Århus', NULL, '8200', 'Denmark');
INSERT INTO `orders` VALUES (10995, 'PERIC', 1, '2018-04-02 00:00:00', '2018-04-06 00:00:00', 3, 46.00, 'Calle Dr. Jorge Cash 321', 'México D.F.', NULL, '05033', 'Mexico');
INSERT INTO `orders` VALUES (10996, 'QUICK', 4, '2018-04-02 00:00:00', '2018-04-10 00:00:00', 2, 1.12, 'Taucherstraße 10', 'Cunewalde', NULL, '01307', 'Germany');
INSERT INTO `orders` VALUES (10997, 'LILAS', 8, '2018-04-03 00:00:00', '2018-04-13 00:00:00', 2, 73.91, 'Carrera 52 con Ave. Bolívar #65-98 Llano Largo', 'Barquisimeto', 'Lara', '3508', 'Venezuela');
INSERT INTO `orders` VALUES (10998, 'WOLZA', 8, '2018-04-03 00:00:00', '2018-04-17 00:00:00', 2, 20.31, 'ul. Filtrowa 68', 'Warszawa', NULL, '01-012', 'Poland');
INSERT INTO `orders` VALUES (10999, 'OTTIK', 6, '2018-04-03 00:00:00', '2018-04-10 00:00:00', 2, 96.35, 'Mehrheimerstr. 369', 'Köl', NULL, '50739', 'Germany');
INSERT INTO `orders` VALUES (11000, 'RATTC', 2, '2018-04-06 00:00:00', '2018-04-14 00:00:00', 3, 55.12, '2817 Milton Dr.', 'Albuquerque', 'NM', '87110', 'USA');
INSERT INTO `orders` VALUES (11001, 'FOLKO', 2, '2018-04-06 00:00:00', '2018-04-14 00:00:00', 2, 197.30, 'Åkergatan 24', 'Bräcke', NULL, 'S-844 67', 'Sweden');
INSERT INTO `orders` VALUES (11002, 'SAVEA', 4, '2018-04-06 00:00:00', '2018-04-16 00:00:00', 1, 141.16, '187 Suffolk Ln.', 'Boise', 'ID', '83720', 'USA');
INSERT INTO `orders` VALUES (11003, 'THECR', 3, '2018-04-06 00:00:00', '2018-04-08 00:00:00', 3, 14.91, '55 Grizzly Peak Rd.', 'Butte', 'MT', '59801', 'USA');
INSERT INTO `orders` VALUES (11004, 'MAISD', 3, '2018-04-07 00:00:00', '2018-04-20 00:00:00', 1, 44.84, 'Rue Joseph-Bens 532', 'Bruxelles', NULL, 'B-1180', 'Belgium');
INSERT INTO `orders` VALUES (11005, 'WILMK', 2, '2018-04-07 00:00:00', '2018-04-10 00:00:00', 1, 0.75, 'Keskuskatu 45', 'Helsinki', NULL, '21240', 'Finland');
INSERT INTO `orders` VALUES (11006, 'GREAL', 3, '2018-04-07 00:00:00', '2018-04-15 00:00:00', 2, 25.19, '2732 Baker Blvd.', 'Eugene', 'OR', '97403', 'USA');
INSERT INTO `orders` VALUES (11007, 'PRINI', 8, '2018-04-08 00:00:00', '2018-04-13 00:00:00', 2, 202.24, 'Estrada da saúde n. 58', 'Lisboa', NULL, '1756', 'Portugal');
INSERT INTO `orders` VALUES (11008, 'ERNSH', 7, '2018-04-08 00:00:00', NULL, 3, 79.46, 'Kirchgasse 6', 'Graz', NULL, '8010', 'Austria');
INSERT INTO `orders` VALUES (11009, 'GODOS', 2, '2018-04-08 00:00:00', '2018-04-10 00:00:00', 1, 59.11, 'C/ Romero-33', 'Sevilla', NULL, '41101', 'Spain');
INSERT INTO `orders` VALUES (11010, 'REGGC', 2, '2018-04-09 00:00:00', '2018-04-21 00:00:00', 2, 28.71, 'Strada Provinciale 124', 'Reggio Emilia', NULL, '42100', 'Italy');
INSERT INTO `orders` VALUES (11011, 'ALFKI', 3, '2018-04-09 00:00:00', '2018-04-13 00:00:00', 1, 1.21, 'Obere Str. 57', 'Berli', NULL, '12209', 'Germany');
INSERT INTO `orders` VALUES (11012, 'FRANK', 1, '2018-04-09 00:00:00', '2018-04-17 00:00:00', 3, 242.95, 'Berliner Platz 43', 'Münche', NULL, '80805', 'Germany');
INSERT INTO `orders` VALUES (11013, 'ROMEY', 2, '2018-04-09 00:00:00', '2018-04-10 00:00:00', 1, 32.99, 'Gran Vía-1', 'Madrid', NULL, '28001', 'Spain');
INSERT INTO `orders` VALUES (11014, 'LINOD', 2, '2018-04-10 00:00:00', '2018-04-15 00:00:00', 3, 23.60, 'Ave. 5 de Mayo Porlamar', 'I. de Margarita', 'Nueva Esparta', '4980', 'Venezuela');
INSERT INTO `orders` VALUES (11015, 'SANTG', 2, '2018-04-10 00:00:00', '2018-04-20 00:00:00', 2, 4.62, 'Erling Skakkes gate 78', 'Staver', NULL, '4110', 'Norway');
INSERT INTO `orders` VALUES (11016, 'AROUT', 9, '2018-04-10 00:00:00', '2018-04-13 00:00:00', 2, 33.80, 'Brook Farm Stratford St. Mary', 'Colchester', 'Essex', 'CO7 6JX', 'UK');
INSERT INTO `orders` VALUES (11017, 'ERNSH', 9, '2018-04-13 00:00:00', '2018-04-20 00:00:00', 2, 754.26, 'Kirchgasse 6', 'Graz', NULL, '8010', 'Austria');
INSERT INTO `orders` VALUES (11018, 'LONEP', 4, '2018-04-13 00:00:00', '2018-04-16 00:00:00', 2, 11.65, '89 Chiaroscuro Rd.', 'Portland', 'OR', '97219', 'USA');
INSERT INTO `orders` VALUES (11019, 'RANCH', 6, '2018-04-13 00:00:00', NULL, 3, 3.17, 'Av. del Libertador 900', 'Buenos Aires', NULL, '1010', 'Argentina');
INSERT INTO `orders` VALUES (11020, 'OTTIK', 2, '2018-04-14 00:00:00', '2018-04-16 00:00:00', 2, 43.30, 'Mehrheimerstr. 369', 'Köl', NULL, '50739', 'Germany');
INSERT INTO `orders` VALUES (11021, 'QUICK', 3, '2018-04-14 00:00:00', '2018-04-21 00:00:00', 1, 297.18, 'Taucherstraße 10', 'Cunewalde', NULL, '01307', 'Germany');
INSERT INTO `orders` VALUES (11022, 'HANAR', 9, '2018-04-14 00:00:00', '2018-05-04 00:00:00', 2, 6.27, 'Rua do Paço-67', 'Rio de Janeiro', 'RJ', '05454-876', 'Brazil');
INSERT INTO `orders` VALUES (11023, 'BSBEV', 1, '2018-04-14 00:00:00', '2018-04-24 00:00:00', 2, 123.83, 'Fauntleroy Circus', 'Londo', NULL, 'EC2 5NT', 'UK');
INSERT INTO `orders` VALUES (11024, 'EASTC', 4, '2018-04-15 00:00:00', '2018-04-20 00:00:00', 1, 74.36, '35 King George', 'Londo', NULL, 'WX3 6FW', 'UK');
INSERT INTO `orders` VALUES (11025, 'WARTH', 6, '2018-04-15 00:00:00', '2018-04-24 00:00:00', 3, 29.17, 'Torikatu 38', 'Oulu', NULL, '90110', 'Finland');
INSERT INTO `orders` VALUES (11026, 'FRANS', 4, '2018-04-15 00:00:00', '2018-04-28 00:00:00', 1, 47.09, 'Via Monte Bianco 34', 'Torino', NULL, '10100', 'Italy');
INSERT INTO `orders` VALUES (11027, 'BOTTM', 1, '2018-04-16 00:00:00', '2018-04-20 00:00:00', 1, 52.52, '23 Tsawassen Blvd.', 'Tsawasse', 'BC', 'T2F 8M4', 'Canada');
INSERT INTO `orders` VALUES (11028, 'KOENE', 2, '2018-04-16 00:00:00', '2018-04-22 00:00:00', 1, 29.59, 'Maubelstr. 90', 'Brandenburg', NULL, '14776', 'Germany');
INSERT INTO `orders` VALUES (11029, 'CHOPS', 4, '2018-04-16 00:00:00', '2018-04-27 00:00:00', 1, 47.84, 'Hauptstr. 31', 'Ber', NULL, '3012', 'Switzerland');
INSERT INTO `orders` VALUES (11030, 'SAVEA', 7, '2018-04-17 00:00:00', '2018-04-27 00:00:00', 2, 830.75, '187 Suffolk Ln.', 'Boise', 'ID', '83720', 'USA');
INSERT INTO `orders` VALUES (11031, 'SAVEA', 6, '2018-04-17 00:00:00', '2018-04-24 00:00:00', 2, 227.22, '187 Suffolk Ln.', 'Boise', 'ID', '83720', 'USA');
INSERT INTO `orders` VALUES (11032, 'WHITC', 2, '2018-04-17 00:00:00', '2018-04-23 00:00:00', 3, 606.19, '1029 - 12th Ave. S.', 'Seattle', 'WA', '98124', 'USA');
INSERT INTO `orders` VALUES (11033, 'RICSU', 7, '2018-04-17 00:00:00', '2018-04-23 00:00:00', 3, 84.74, 'Starenweg 5', 'Genève', NULL, '1204', 'Switzerland');
INSERT INTO `orders` VALUES (11034, 'OLDWO', 8, '2018-04-20 00:00:00', '2018-04-27 00:00:00', 1, 40.32, '2743 Bering St.', 'Anchorage', 'AK', '99508', 'USA');
INSERT INTO `orders` VALUES (11035, 'SUPRD', 2, '2018-04-20 00:00:00', '2018-04-24 00:00:00', 2, 0.17, 'Boulevard Tirou-255', 'Charleroi', NULL, 'B-6000', 'Belgium');
INSERT INTO `orders` VALUES (11036, 'DRACD', 8, '2018-04-20 00:00:00', '2018-04-22 00:00:00', 3, 149.47, 'Walserweg 21', 'Aache', NULL, '52066', 'Germany');
INSERT INTO `orders` VALUES (11037, 'GODOS', 7, '2018-04-21 00:00:00', '2018-04-27 00:00:00', 1, 3.20, 'C/ Romero-33', 'Sevilla', NULL, '41101', 'Spain');
INSERT INTO `orders` VALUES (11038, 'SUPRD', 1, '2018-04-21 00:00:00', '2018-04-30 00:00:00', 2, 29.59, 'Boulevard Tirou-255', 'Charleroi', NULL, 'B-6000', 'Belgium');
INSERT INTO `orders` VALUES (11039, 'LINOD', 1, '2018-04-21 00:00:00', NULL, 2, 65.00, 'Ave. 5 de Mayo Porlamar', 'I. de Margarita', 'Nueva Esparta', '4980', 'Venezuela');
INSERT INTO `orders` VALUES (11040, 'GREAL', 4, '2018-04-22 00:00:00', NULL, 3, 18.84, '2732 Baker Blvd.', 'Eugene', 'OR', '97403', 'USA');
INSERT INTO `orders` VALUES (11041, 'CHOPS', 3, '2018-04-22 00:00:00', '2018-04-28 00:00:00', 2, 48.22, 'Hauptstr. 31', 'Ber', NULL, '3012', 'Switzerland');
INSERT INTO `orders` VALUES (11042, 'COMMI', 2, '2018-04-22 00:00:00', '2018-05-01 00:00:00', 1, 29.99, 'Av. dos Lusíadas-23', 'Sao Paulo', 'SP', '05432-043', 'Brazil');
INSERT INTO `orders` VALUES (11043, 'SPECD', 5, '2018-04-22 00:00:00', '2018-04-29 00:00:00', 2, 8.80, '25-rue Lauristo', 'Paris', NULL, '75016', 'France');
INSERT INTO `orders` VALUES (11044, 'WOLZA', 4, '2018-04-23 00:00:00', '2018-05-01 00:00:00', 1, 8.72, 'ul. Filtrowa 68', 'Warszawa', NULL, '01-012', 'Poland');
INSERT INTO `orders` VALUES (11045, 'BOTTM', 6, '2018-04-23 00:00:00', NULL, 2, 70.58, '23 Tsawassen Blvd.', 'Tsawasse', 'BC', 'T2F 8M4', 'Canada');
INSERT INTO `orders` VALUES (11046, 'WANDK', 8, '2018-04-23 00:00:00', '2018-04-24 00:00:00', 2, 71.64, 'Adenauerallee 900', 'Stuttgart', NULL, '70563', 'Germany');
INSERT INTO `orders` VALUES (11047, 'EASTC', 7, '2018-04-24 00:00:00', '2018-05-01 00:00:00', 3, 46.62, '35 King George', 'Londo', NULL, 'WX3 6FW', 'UK');
INSERT INTO `orders` VALUES (11048, 'BOTTM', 7, '2018-04-24 00:00:00', '2018-04-30 00:00:00', 3, 24.12, '23 Tsawassen Blvd.', 'Tsawasse', 'BC', 'T2F 8M4', 'Canada');
INSERT INTO `orders` VALUES (11049, 'GOURL', 3, '2018-04-24 00:00:00', '2018-05-04 00:00:00', 1, 8.34, 'Av. Brasil-442', 'Campinas', 'SP', '04876-786', 'Brazil');
INSERT INTO `orders` VALUES (11050, 'FOLKO', 8, '2018-04-27 00:00:00', '2018-05-05 00:00:00', 2, 59.41, 'Åkergatan 24', 'Bräcke', NULL, 'S-844 67', 'Sweden');
INSERT INTO `orders` VALUES (11051, 'LAMAI', 7, '2018-04-27 00:00:00', NULL, 3, 2.79, '1 rue Alsace-Lorraine', 'Toulouse', NULL, '31000', 'France');
INSERT INTO `orders` VALUES (11052, 'HANAR', 3, '2018-04-27 00:00:00', '2018-05-01 00:00:00', 1, 67.26, 'Rua do Paço-67', 'Rio de Janeiro', 'RJ', '05454-876', 'Brazil');
INSERT INTO `orders` VALUES (11053, 'PICCO', 2, '2018-04-27 00:00:00', '2018-04-29 00:00:00', 2, 53.05, 'Geislweg 14', 'Salzburg', NULL, '5020', 'Austria');
INSERT INTO `orders` VALUES (11054, 'CACTU', 8, '2018-04-28 00:00:00', NULL, 1, 0.33, 'Cerrito 333', 'Buenos Aires', NULL, '1010', 'Argentina');
INSERT INTO `orders` VALUES (11055, 'HILAA', 7, '2018-04-28 00:00:00', '2018-05-05 00:00:00', 2, 120.92, 'Carrera 22 con Ave. Carlos Soublette #8-35', 'San Cristóbal', 'Táchira', '5022', 'Venezuela');
INSERT INTO `orders` VALUES (11056, 'EASTC', 8, '2018-04-28 00:00:00', '2018-05-01 00:00:00', 2, 278.96, '35 King George', 'Londo', NULL, 'WX3 6FW', 'UK');
INSERT INTO `orders` VALUES (11057, 'NORTS', 3, '2018-04-29 00:00:00', '2018-05-01 00:00:00', 3, 4.13, 'South House 300 Queensbridge', 'Londo', NULL, 'SW7 1RZ', 'UK');
INSERT INTO `orders` VALUES (11058, 'BLAUS', 9, '2018-04-29 00:00:00', NULL, 3, 31.14, 'Forsterstr. 57', 'Mannheim', NULL, '68306', 'Germany');
INSERT INTO `orders` VALUES (11059, 'RICAR', 2, '2018-04-29 00:00:00', NULL, 2, 85.80, 'Av. Copacabana-267', 'Rio de Janeiro', 'RJ', '02389-890', 'Brazil');
INSERT INTO `orders` VALUES (11060, 'FRANS', 2, '2018-04-30 00:00:00', '2018-05-04 00:00:00', 2, 10.98, 'Via Monte Bianco 34', 'Torino', NULL, '10100', 'Italy');
INSERT INTO `orders` VALUES (11061, 'GREAL', 4, '2018-04-30 00:00:00', NULL, 3, 14.01, '2732 Baker Blvd.', 'Eugene', 'OR', '97403', 'USA');
INSERT INTO `orders` VALUES (11062, 'REGGC', 4, '2018-04-30 00:00:00', NULL, 2, 29.93, 'Strada Provinciale 124', 'Reggio Emilia', NULL, '42100', 'Italy');
INSERT INTO `orders` VALUES (11063, 'HUNGO', 3, '2018-04-30 00:00:00', '2018-05-06 00:00:00', 2, 81.73, '8 Johnstown Road', 'Cork', 'Co. Cork', NULL, 'Ireland');
INSERT INTO `orders` VALUES (11064, 'SAVEA', 1, '2018-05-01 00:00:00', '2018-05-04 00:00:00', 1, 30.09, '187 Suffolk Ln.', 'Boise', 'ID', '83720', 'USA');
INSERT INTO `orders` VALUES (11065, 'LILAS', 8, '2018-05-01 00:00:00', NULL, 1, 12.91, 'Carrera 52 con Ave. Bolívar #65-98 Llano Largo', 'Barquisimeto', 'Lara', '3508', 'Venezuela');
INSERT INTO `orders` VALUES (11066, 'WHITC', 7, '2018-05-01 00:00:00', '2018-05-04 00:00:00', 2, 44.72, '1029 - 12th Ave. S.', 'Seattle', 'WA', '98124', 'USA');
INSERT INTO `orders` VALUES (11067, 'DRACD', 1, '2018-05-04 00:00:00', '2018-05-06 00:00:00', 2, 7.98, 'Walserweg 21', 'Aache', NULL, '52066', 'Germany');
INSERT INTO `orders` VALUES (11068, 'QUEE', 8, '2018-05-04 00:00:00', NULL, 2, 81.75, 'Alameda dos Canàrios-891', 'Sao Paulo', 'SP', '05487-020', 'Brazil');
INSERT INTO `orders` VALUES (11069, 'TORTU', 1, '2018-05-04 00:00:00', '2018-05-06 00:00:00', 2, 15.67, 'Avda. Azteca 123', 'México D.F.', NULL, '05033', 'Mexico');
INSERT INTO `orders` VALUES (11070, 'LEHMS', 2, '2018-05-05 00:00:00', NULL, 1, 136.00, 'Magazinweg 7', 'Frankfurt a.M.', NULL, '60528', 'Germany');
INSERT INTO `orders` VALUES (11071, 'LILAS', 1, '2018-05-05 00:00:00', NULL, 1, 0.93, 'Carrera 52 con Ave. Bolívar #65-98 Llano Largo', 'Barquisimeto', 'Lara', '3508', 'Venezuela');
INSERT INTO `orders` VALUES (11072, 'ERNSH', 4, '2018-05-05 00:00:00', NULL, 2, 258.64, 'Kirchgasse 6', 'Graz', NULL, '8010', 'Austria');
INSERT INTO `orders` VALUES (11073, 'PERIC', 2, '2018-05-05 00:00:00', NULL, 2, 24.95, 'Calle Dr. Jorge Cash 321', 'México D.F.', NULL, '05033', 'Mexico');
INSERT INTO `orders` VALUES (11074, 'SIMOB', 7, '2018-05-06 00:00:00', NULL, 2, 18.44, 'Vinbæltet 34', 'Kobenhav', NULL, '1734', 'Denmark');
INSERT INTO `orders` VALUES (11075, 'RICSU', 8, '2018-05-06 00:00:00', NULL, 2, 6.19, 'Starenweg 5', 'Genève', NULL, '1204', 'Switzerland');
INSERT INTO `orders` VALUES (11076, 'BONAP', 4, '2018-05-06 00:00:00', NULL, 2, 38.28, '12-rue des Bouchers', 'Marseille', NULL, '13008', 'France');
INSERT INTO `orders` VALUES (11077, 'RATTC', 1, '2018-05-06 00:00:00', NULL, 2, 8.53, '2817 Milton Dr.', 'Albuquerque', 'NM', '87110', 'USA');
COMMIT;

-- ----------------------------
-- Table structure for products
-- ----------------------------
DROP TABLE IF EXISTS `products`;
CREATE TABLE `products` (
  `product_id` int NOT NULL,
  `product_name` varchar(40) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL,
  `supplier_id` int DEFAULT NULL,
  `category_id` int DEFAULT NULL,
  `quantity_per_unit` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL,
  `unit_price` decimal(10,2) DEFAULT NULL,
  `units_in_stock` smallint DEFAULT NULL,
  `units_on_order` smallint DEFAULT NULL,
  `discontinued` bit(1) DEFAULT NULL,
  PRIMARY KEY (`product_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

-- ----------------------------
-- Records of products
-- ----------------------------
BEGIN;
INSERT INTO `products` VALUES (1, 'Chai', 1, 1, '10 boxes x 20 bags', 18.00, 39, 0, b'0');
INSERT INTO `products` VALUES (2, 'Chang', 1, 1, '24 - 12 oz bottles', 19.00, 17, 40, b'0');
INSERT INTO `products` VALUES (3, 'Aniseed Syrup', 1, 2, '12 - 550 ml bottles', 10.00, 13, 70, b'0');
INSERT INTO `products` VALUES (4, 'Chef Anton\'s Cajun Seasoning', 2, 2, '48 - 6 oz jars', 22.00, 53, 0, b'0');
INSERT INTO `products` VALUES (5, 'Chef Anton\'s Gumbo Mix', 2, 2, '36 boxes', 21.35, 0, 0, b'1');
INSERT INTO `products` VALUES (6, 'Grandma\'s Boysenberry Spread', 3, 2, '12 - 8 oz jars', 25.00, 120, 0, b'0');
INSERT INTO `products` VALUES (7, 'Uncle Bob\'s Organic Dried Pears', 3, 7, '12 - 1 lb pkgs.', 30.00, 15, 0, b'0');
INSERT INTO `products` VALUES (8, 'Northwoods Cranberry Sauce', 3, 2, '12 - 12 oz jars', 40.00, 6, 0, b'0');
INSERT INTO `products` VALUES (9, 'Mishi Kobe Niku', 4, 6, '18 - 500 g pkgs.', 97.00, 29, 0, b'1');
INSERT INTO `products` VALUES (10, 'Ikura', 4, 8, '12 - 200 ml jars', 31.00, 31, 0, b'0');
INSERT INTO `products` VALUES (11, 'Queso Cabrales', 5, 4, '1 kg pkg.', 21.00, 22, 30, b'0');
INSERT INTO `products` VALUES (12, 'Queso Manchego La Pastora', 5, 4, '10 - 500 g pkgs.', 38.00, 86, 0, b'0');
INSERT INTO `products` VALUES (13, 'Konbu', 6, 8, '2 kg box', 6.00, 24, 0, b'0');
INSERT INTO `products` VALUES (14, 'Tofu', 6, 7, '40 - 100 g pkgs.', 23.25, 35, 0, b'0');
INSERT INTO `products` VALUES (15, 'Genen Shouyu', 6, 2, '24 - 250 ml bottles', 15.50, 39, 0, b'0');
INSERT INTO `products` VALUES (16, 'Pavlova', 7, 3, '32 - 500 g boxes', 17.45, 29, 0, b'0');
INSERT INTO `products` VALUES (17, 'Alice Mutton', 7, 6, '20 - 1 kg tins', 39.00, 0, 0, b'1');
INSERT INTO `products` VALUES (18, 'Carnarvon Tigers', 7, 8, '16 kg pkg.', 62.50, 42, 0, b'0');
INSERT INTO `products` VALUES (19, 'Teatime Chocolate Biscuits', 8, 3, '10 boxes x 12 pieces', 9.20, 25, 0, b'0');
INSERT INTO `products` VALUES (20, 'Sir Rodney\'s Marmalade', 8, 3, '30 gift boxes', 81.00, 40, 0, b'0');
INSERT INTO `products` VALUES (21, 'Sir Rodney\'s Scones', 8, 3, '24 pkgs. x 4 pieces', 10.00, 3, 40, b'0');
INSERT INTO `products` VALUES (22, 'Gustaf\'s Knäckebröd', 9, 5, '24 - 500 g pkgs.', 21.00, 104, 0, b'0');
INSERT INTO `products` VALUES (23, 'Tunnbröd', 9, 5, '12 - 250 g pkgs.', 9.00, 61, 0, b'0');
INSERT INTO `products` VALUES (24, 'Guaraná Fantástica', 10, 1, '12 - 355 ml cans', 4.50, 20, 0, b'1');
INSERT INTO `products` VALUES (25, 'NuNuCa Nuß-Nougat-Creme', 11, 3, '20 - 450 g glasses', 14.00, 76, 0, b'0');
INSERT INTO `products` VALUES (26, 'Gumbär Gummibärchen', 11, 3, '100 - 250 g bags', 31.23, 15, 0, b'0');
INSERT INTO `products` VALUES (27, 'Schoggi Schokolade', 11, 3, '100 - 100 g pieces', 43.90, 49, 0, b'0');
INSERT INTO `products` VALUES (28, 'Rössle Sauerkraut', 12, 7, '25 - 825 g cans', 45.60, 26, 0, b'1');
INSERT INTO `products` VALUES (29, 'Thüringer Rostbratwurst', 12, 6, '50 bags x 30 sausgs.', 123.79, 0, 0, b'1');
INSERT INTO `products` VALUES (30, 'Nord-Ost Matjeshering', 13, 8, '10 - 200 g glasses', 25.89, 10, 0, b'0');
INSERT INTO `products` VALUES (31, 'Gorgonzola Telino', 14, 4, '12 - 100 g pkgs', 12.50, 0, 70, b'0');
INSERT INTO `products` VALUES (32, 'Mascarpone Fabioli', 14, 4, '24 - 200 g pkgs.', 32.00, 9, 40, b'0');
INSERT INTO `products` VALUES (33, 'Geitost', 16, 4, '500 g', 2.50, 112, 0, b'0');
INSERT INTO `products` VALUES (34, 'Sasquatch Ale', 16, 1, '24 - 12 oz bottles', 14.00, 111, 0, b'0');
INSERT INTO `products` VALUES (35, 'Steeleye Stout', 16, 1, '24 - 12 oz bottles', 18.00, 20, 0, b'0');
INSERT INTO `products` VALUES (36, 'Inlagd Sill', 17, 8, '24 - 250 g jars', 19.00, 112, 0, b'0');
INSERT INTO `products` VALUES (37, 'Gravad lax', 17, 8, '12 - 500 g pkgs.', 26.00, 11, 50, b'0');
INSERT INTO `products` VALUES (38, 'Côte de Blaye', 18, 1, '12 - 75 cl bottles', 263.50, 17, 0, b'0');
INSERT INTO `products` VALUES (39, 'Chartreuse verte', 18, 1, '750 cc per bottle', 18.00, 69, 0, b'0');
INSERT INTO `products` VALUES (40, 'Boston Crab Meat', 19, 8, '24 - 4 oz tins', 18.40, 123, 0, b'0');
INSERT INTO `products` VALUES (41, 'Jack\'s New England Clam Chowder', 19, 8, '12 - 12 oz cans', 9.65, 85, 0, b'0');
INSERT INTO `products` VALUES (42, 'Singaporean Hokkien Fried Mee', 20, 5, '32 - 1 kg pkgs.', 14.00, 26, 0, b'1');
INSERT INTO `products` VALUES (43, 'Ipoh Coffee', 20, 1, '16 - 500 g tins', 46.00, 17, 10, b'0');
INSERT INTO `products` VALUES (44, 'Gula Malacca', 20, 2, '20 - 2 kg bags', 19.45, 27, 0, b'0');
INSERT INTO `products` VALUES (45, 'Rogede sild', 21, 8, '1k pkg.', 9.50, 5, 70, b'0');
INSERT INTO `products` VALUES (46, 'Spegesild', 21, 8, '4 - 450 g glasses', 12.00, 95, 0, b'0');
INSERT INTO `products` VALUES (47, 'Zaanse koeken', 22, 3, '10 - 4 oz boxes', 9.50, 36, 0, b'0');
INSERT INTO `products` VALUES (48, 'Chocolade', 22, 3, '10 pkgs.', 12.75, 15, 70, b'0');
INSERT INTO `products` VALUES (49, 'Maxilaku', 23, 3, '24 - 50 g pkgs.', 20.00, 10, 60, b'0');
INSERT INTO `products` VALUES (50, 'Valkoinen suklaa', 23, 3, '12 - 100 g bars', 16.25, 65, 0, b'0');
INSERT INTO `products` VALUES (51, 'Manjimup Dried Apples', 24, 7, '50 - 300 g pkgs.', 53.00, 20, 0, b'0');
INSERT INTO `products` VALUES (52, 'Filo Mix', 24, 5, '16 - 2 kg boxes', 7.00, 38, 0, b'0');
INSERT INTO `products` VALUES (53, 'Perth Pasties', 24, 6, '48 pieces', 32.80, 0, 0, b'1');
INSERT INTO `products` VALUES (54, 'Tourtière', 25, 6, '16 pies', 7.45, 21, 0, b'0');
INSERT INTO `products` VALUES (55, 'Pâté chinois', 25, 6, '24 boxes x 2 pies', 24.00, 115, 0, b'0');
INSERT INTO `products` VALUES (56, 'Gnocchi di nonna Alice', 26, 5, '24 - 250 g pkgs.', 38.00, 21, 10, b'0');
INSERT INTO `products` VALUES (57, 'Ravioli Angelo', 26, 5, '24 - 250 g pkgs.', 19.50, 36, 0, b'0');
INSERT INTO `products` VALUES (58, 'Escargots de Bourgogne', 27, 8, '24 pieces', 13.25, 62, 0, b'0');
INSERT INTO `products` VALUES (59, 'Raclette Courdavault', 28, 4, '5 kg pkg.', 55.00, 79, 0, b'0');
INSERT INTO `products` VALUES (60, 'Camembert Pierrot', 28, 4, '15 - 300 g rounds', 34.00, 19, 0, b'0');
INSERT INTO `products` VALUES (61, 'Sirop d\'érable', 29, 2, '24 - 500 ml bottles', 28.50, 113, 0, b'0');
INSERT INTO `products` VALUES (62, 'Tarte au sucre', 29, 3, '48 pies', 49.30, 17, 0, b'0');
INSERT INTO `products` VALUES (63, 'Vegie-spread', 7, 2, '15 - 625 g jars', 43.90, 24, 0, b'0');
INSERT INTO `products` VALUES (64, 'Wimmers gute Semmelknödel', 12, 5, '20 bags x 4 pieces', 33.25, 22, 80, b'0');
INSERT INTO `products` VALUES (65, 'Louisiana Fiery Hot Pepper Sauce', 2, 2, '32 - 8 oz bottles', 21.05, 76, 0, b'0');
INSERT INTO `products` VALUES (66, 'Louisiana Hot Spiced Okra', 2, 2, '24 - 8 oz jars', 17.00, 4, 100, b'0');
INSERT INTO `products` VALUES (67, 'Laughing Lumberjack Lager', 16, 1, '24 - 12 oz bottles', 14.00, 52, 0, b'0');
INSERT INTO `products` VALUES (68, 'Scottish Longbreads', 8, 3, '10 boxes x 8 pieces', 12.50, 6, 10, b'0');
INSERT INTO `products` VALUES (69, 'Gudbrandsdalsost', 16, 4, '10 kg pkg.', 36.00, 26, 0, b'0');
INSERT INTO `products` VALUES (70, 'Outback Lager', 7, 1, '24 - 355 ml bottles', 15.00, 15, 10, b'0');
INSERT INTO `products` VALUES (71, 'Flotemysost', 16, 4, '10 - 500 g pkgs.', 21.50, 26, 0, b'0');
INSERT INTO `products` VALUES (72, 'Mozzarella di Giovanni', 14, 4, '24 - 200 g pkgs.', 34.80, 14, 0, b'0');
INSERT INTO `products` VALUES (73, 'Röd Kaviar', 17, 8, '24 - 150 g jars', 15.00, 101, 0, b'0');
INSERT INTO `products` VALUES (74, 'Longlife Tofu', 4, 7, '5 kg pkg.', 10.00, 4, 20, b'0');
INSERT INTO `products` VALUES (75, 'Rhönbräu Klosterbier', 12, 1, '24 - 0.5 l bottles', 7.75, 125, 0, b'0');
INSERT INTO `products` VALUES (76, 'Lakkalikööri', 23, 1, '500 ml', 18.00, 57, 0, b'0');
INSERT INTO `products` VALUES (77, 'Original Frankfurter grüne Soße', 12, 2, '12 boxes', 13.00, 32, 0, b'0');
COMMIT;

-- ----------------------------
-- Table structure for suppliers
-- ----------------------------
DROP TABLE IF EXISTS `suppliers`;
CREATE TABLE `suppliers` (
  `supplier_id` int NOT NULL,
  `company_name` varchar(40) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL,
  `address` varchar(60) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL,
  `city` varchar(15) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL,
  `region` varchar(15) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL,
  `postal_code` varchar(10) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL,
  `country` varchar(15) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL,
  PRIMARY KEY (`supplier_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

-- ----------------------------
-- Records of suppliers
-- ----------------------------
BEGIN;
INSERT INTO `suppliers` VALUES (1, 'Exotic Liquids', '49 Gilbert St.', 'London', NULL, 'EC1 4SD', 'UK');
INSERT INTO `suppliers` VALUES (2, 'New Orleans Cajun Delights', 'P.O. Box 78934', 'New Orleans', 'LA', '70117', 'USA');
INSERT INTO `suppliers` VALUES (3, 'Grandma Kelly\'s Homestead', '707 Oxford Rd.', 'Ann Arbor', 'MI', '48104', 'USA');
INSERT INTO `suppliers` VALUES (4, 'Tokyo Traders', '9-8 Sekimai Musashino-shi', 'Tokyo', NULL, '100', 'Japan');
INSERT INTO `suppliers` VALUES (5, 'Cooperativa de Quesos \'Las Cabras\'', 'Calle del Rosal 4', 'Oviedo', 'Asturias', '33007', 'Spain');
INSERT INTO `suppliers` VALUES (6, 'Mayumi\'s', '92 Setsuko Chuo-ku', 'Osaka', NULL, '545', 'Japan');
INSERT INTO `suppliers` VALUES (7, 'Pavlova, Ltd.', '74 Rose St. Moonie Ponds', 'Melbourne', 'Victoria', '3058', 'Australia');
INSERT INTO `suppliers` VALUES (8, 'Specialty Biscuits, Ltd.', '29 King\'s Way', 'Manchester', NULL, 'M14 GSD', 'UK');
INSERT INTO `suppliers` VALUES (9, 'PB Knäckebröd AB', 'Kaloadagatan 13', 'Göteborg', NULL, 'S-345 67', 'Sweden');
INSERT INTO `suppliers` VALUES (10, 'Refrescos Americanas LTDA', 'Av. das Americanas 12.890', 'Sao Paulo', NULL, '5442', 'Brazil');
INSERT INTO `suppliers` VALUES (11, 'Heli Süßwaren GmbH & Co. KG', 'Tiergartenstraße 5', 'Berlin', NULL, '10785', 'Germany');
INSERT INTO `suppliers` VALUES (12, 'Plutzer Lebensmittelgroßmärkte AG', 'Bogenallee 51', 'Frankfurt', NULL, '60439', 'Germany');
INSERT INTO `suppliers` VALUES (13, 'Nord-Ost-Fisch Handelsgesellschaft mbH', 'Frahmredder 112a', 'Cuxhaven', NULL, '27478', 'Germany');
INSERT INTO `suppliers` VALUES (14, 'Formaggi Fortini s.r.l.', 'Viale Dante, 75', 'Ravenna', NULL, '48100', 'Italy');
INSERT INTO `suppliers` VALUES (15, 'Norske Meierier', 'Hatlevegen 5', 'Sandvika', NULL, '1320', 'Norway');
INSERT INTO `suppliers` VALUES (16, 'Bigfoot Breweries', '3400 - 8th Avenue Suite 210', 'Bend', 'OR', '97101', 'USA');
INSERT INTO `suppliers` VALUES (17, 'Svensk Sjöföda AB', 'Brovallavägen 231', 'Stockholm', NULL, 'S-123 45', 'Sweden');
INSERT INTO `suppliers` VALUES (18, 'Aux joyeux ecclésiastiques', '203, Rue des Francs-Bourgeois', 'Paris', NULL, '75004', 'France');
INSERT INTO `suppliers` VALUES (19, 'New England Seafood Cannery', 'Order Processing Dept. 2100 Paul Revere Blvd.', 'Boston', 'MA', '2134', 'USA');
INSERT INTO `suppliers` VALUES (20, 'Leka Trading', '471 Serangoon Loop, Suite #402', 'Singapore', NULL, '512', 'Singapore');
INSERT INTO `suppliers` VALUES (21, 'Lyngbysild', 'Lyngbysild Fiskebakken 10', 'Lyngby', NULL, '2800', 'Denmark');
INSERT INTO `suppliers` VALUES (22, 'Zaanse Snoepfabriek', 'Verkoop Rijnweg 22', 'Zaandam', NULL, '9999 ZZ', 'Netherlands');
INSERT INTO `suppliers` VALUES (23, 'Karkki Oy', 'Valtakatu 12', 'Lappeenranta', NULL, '53120', 'Finland');
INSERT INTO `suppliers` VALUES (24, 'G\'day, Mate', '170 Prince Edward Parade Hunter\'s Hill', 'Sydney', 'NSW', '2042', 'Australia');
INSERT INTO `suppliers` VALUES (25, 'Ma Maison', '2960 Rue St. Laurent', 'Montréal', 'Québec', 'H1J 1C3', 'Canada');
INSERT INTO `suppliers` VALUES (26, 'Pasta Buttini s.r.l.', 'Via dei Gelsomini, 153', 'Salerno', NULL, '84100', 'Italy');
INSERT INTO `suppliers` VALUES (27, 'Escargots Nouveaux', '22, rue H. Voiron', 'Montceau', NULL, '71300', 'France');
INSERT INTO `suppliers` VALUES (28, 'Gai pâturage', 'Bat. B 3, rue des Alpes', 'Annecy', NULL, '74000', 'France');
INSERT INTO `suppliers` VALUES (29, 'Forêts d\'érables', '148 rue Chasseur', 'Ste-Hyacinthe', 'Québec', 'J2S 7S8', 'Canada');
COMMIT;

SET FOREIGN_KEY_CHECKS = 1;

```

## 十三、总结
![数据库.png](https://s2.loli.net/2024/03/15/gaYtT2urKIR4yHL.png)
![SQL基础内容.png](https://s2.loli.net/2024/03/15/ylTcCPkJtwmxoVY.png)