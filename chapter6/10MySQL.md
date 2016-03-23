# MySQL

## 数据库介绍

**DBMS**，`Database Management System`数据库管理系统，简单说：就是管理数据的一个大型软件。DBMS主要对数据进行管理、维护等操作，或者对数据的安全性和完整性的处理。

### 主流的数据库

- **ACCESS**：Microsoft公司开发的小型数据库管理系统；
- **SQL SERVER**：Microsoft公司开发的，面向大中型网站；
- **Oracle**：美国甲骨文公司开发的，大型或超大型数据方面的应用；
- **MySQL**：完美组合Linux+Apache+PHP+MySQL，MySQL是瑞典AB公司开发，现在被Oracle收购了。**开源、免费、轻量**;
- **MongoDB**:是由10gen公司开发的一个介于关系型数据库和非关系型数据库之间的产品，是非关系型数据库中功能最丰富，最像关系型数据库的。他支持的数据结构非常松散，是类似json的格式，所以可以存储比较复杂的数据结构类型。MongoDB数据库管理系统最大的特点就是它支持的查询语言非常强大，语法类似于面向对象的查询语言。它还是一个开源的数据库，对于**大数据量、高并发**的互联网应用，支持非常不错。
操作非关系型数据库不需要使用SQL语言

### 数据库中相关概念

- **数据**：行和列的交叉处，就是真正的“数据”。
- **数据表**：就是存放数据的具体的场所。相当于系统中的不同类型的文件。像公司的一个文件。
- **数据库**：是存放数据的一个仓库。比如：相当于系统中的文件夹。像公司的一个文件柜。
- **记录**：数据表中的一行内容，称为“一条记录” row
因此，我们在创建数据表时，一定要创建一个id列，用于标识“这是第几条记录”，id列的值不能相同，必须唯一，就相当于身份证号一样。
- **字段**：一个表中的各个列，就叫“字段”，在数据库中的每个字段，都是有规定的，比如：字段的数据类型、空与不空的判断、自动增长等。

### 数据存储的表现

我们通过代码（语句），可以对各种数据进行各种操作，但其实，在文件表现，其实只是几个文件名而已，具体在数据库的存储目录中：
1. 每个数据库，会对应一个文件夹；
2. 每个数据表，会对应一个或几个文件：

### mysql数据库操作的基本模式
mysql是一种c/s软件结构。在运行之前，必须保证服务端和客户端同时运行才能正常工作。

1. 建立连接（认证身份）
	- 客户端发送连接请求，建立连接：`mysql –h –P –u –p`
		- -h：host，ip地址或者域名，默认可以没有代表localhost
		- -P：大写，端口默认为3306
		- -u：username，用户名
		- -p：password，用户密码
1. 客户端向服务器端发送sql命令,**准备SQL语句：逐行执行，以分号为结束符**
1. 服务器端执行命令，并返回执行的结果,所有的处理操作都是在服务端，客户端只是负责发送SQL语句和接收执行结果，并解析
1. 客户端接收结果（并显示）
1. 关闭连接`exit`或`\q`

## mysql数据库的系统级操作及基本语法规定

### 管理服务端
**windows下有三种方式进行服务端管理**
1. 通过windows服务管理器
1. 通过服务命令在dos（CMD）下
  - 启动：`net start mysql`
  - 停止：`net stop mysql`
1. 直接通过mysqld.exe启动
mysqld的执行必须要指定配置文件才能启动成功
`mysqld.exe –defaults-file=d:/server/mysql/my.ini`

### 登录MySQL客户端
** 语法格式 **：mysql   –h主机名或ip地址   -u用户名   -p密码  
**参数说明**
-	-h：代表MySQL的主机名或IP地址，如：-h127.0.01   -hlocalhost
-	-u：代表MySQL中的用户名，默认是root
-	-p：代表MySQL中用记的密码，默认是root

>Note：语法中各个段之间用空格分开；如果你不想让别人看到你输入的密码，在登录MySQL客户端可以先不输密码，直接回车，会提示输入密码，这时候的密是以“*”号显示；提示：安装完phpStudy之后，只有一个root用户，它是超级管理员。

### 退出MySQL客户端的命令
`exit`或`quit`
在DOS命令行下，可以使用键盘上的“上下箭头”来把曾经使用过的命令重新调出来执行。

#### 修改root用户的密码
1. 使用**mysqladmin.exe** 程序来进行修改(在DOS命令下)
2. 在MySQL客户端来修改密码(当前账号的密码)
**语法格式**`Mysql>  set password=password(‘新密码’);`

>Note：password( )是MySQL的一个加密函数,md5( )是PHP中的一个加密函数

```sql
C:\> mysqladmin.exe  –hlocalhost  –uroot  –proot  password  新密码
```
>Note：mysqladmin.exe这命令的使用，是在DOS命令使用，并不是MySQL的客户端。新密码可以不加引号；

### 数据库的备份和恢复
备份：就是将一个数据库，完整地“转换为”一个可以随时“携带和传送”的文件。
语法：mysqldump  -h服务器地址  -u登录名  -p   数据库名 > 文件名

```sql
mysqldump -hlocalhost -uroot -proot database_name > filename

```

恢复： 就是讲一个备份的数据库文件，完整地还原为一个可以使用的数据库。
语法：mysql  -h服务器地址  -u登录名   -p   数据库名 < 文件名

```sql
mysql -hlocalhost -uroot -proot database_name < filename

```

>Note:
1，这两个命令，都是在“没有登录mysql”的时候使用。
2，其中mysqldump命令还要求为管理员身份。
3，通常，恢复，就是指恢复原来数据库中的所有表数据信息及其他信息，而数据库名可以是原来的名字或新的名字。

### 基础语法规定
#### 注释
1. 单行注释：    #注释内容
2. 单行注释：    -- 注释内容（注意：--后面有一个空格）
3. 多行注释：   /* 注释内容*/

#### 语句行
默认情况下，以一个英文分号作为一条语句的结束！
而且，常规的操作中，都是“一次执行一条语句”；
但：mysql中，可以可以人为设定语句结束符，做法如下：
**delimiter  新的结束符** 此行之后 ，就可以使用新的结束符了：

#### 大小写问题
1. mysql语言内部本身不区分大小写；
2. mysql的某些命令执行会生成文件(夹)，此时他们就可能会区分大小写
	- 在文件(夹)名称 区分大小 写的系统中，这些名字也会区分大小写，比如unix，linux系统；
	- 在文件(夹)名称不区分大小写的系统中，他们同样不区分大小写，比如window系统。

#### 命名问题
- 可以自己命名的名字，称为标识符，包括：数据库名， 表名，字段名，视图名，函数名，过程名，变量名，用户名，，等等。
- 可以命名标识符的字符比常规的语言多，但特别建议只用：字母数字和下划线，并不用数字开头。
- 非常规字符或系统关键字虽然可以作为标识符使用，但最好要包在反引号（数字1左边那个反撇 ` ）中，并且不推荐。
- 对数据库名，表名，和视图名，在window系统中不区分大小写，而其他系统中区分，建议全使用小写，并采用下划线分割法。
- 对其他自己命名的标识符（字段名，函数名，过程名），不区分大小写，但也建议全使用小写，并采用下划线分割法

## 数据库操作
### 创建数据库
**语法**：Create Database [IF NOT EXISTS] db_name [CHARSET] [collate 排序规则]
```sql
CREATE DATABASE  [IF NOT EXISTS] db_name [CHARSET] [collate 排序规则];
CREATE DATABASE IF NOT EXISTS zhangsan CHARSET utf8;#使用的是默认字符集latin1

```
-	`Create Database` 创建数据库的命令；
-	`[IF NOT EXISTS]` 可选项，如果不存在，再进行创建；
-	`db_name` 要创建的数据库的名称，命名方式跟变量一样，但不加$符号；
-	`[CHARSET]`设置数据库的字符集，如果不设置会用MySQL的默认字符集`latin1`
>1，字符编码名称是用于设定当前数据库中存储的字符内容以什么编码来存储。
2，collate排序规则用于设定其中的字符内容的“大小关系”（先后顺序）

### 显示所有数据库
**语法**：`show databases`
### 删除数据库
** 语法 ** `DROP DATABASE [IF EXISTS] db_name`
-	`Drop database`是删除数据库的命令；
-	`[IF EXISTS]`是可选项，如果存在，再进行删除，如果数据库不存在，也不会报错。否则会报错。

```sql
DROP DATABASE IF EXISTS zhang; #删除数据库zhang
```

### 选择数据库
** 语法 ** `USE db_name`
** 举例：** `use saixinjituan`;  //选择saixinjituan的数据库

#### 更改数据库默认字符集
1. 更改MySQL的配置文件：`C:\Program Files (x86)\phpStudy\MySQL\my.ini`
	客户端(Client Section)：default-character-set=gbk
	服务器端(Server Section)：default-character-set=latin1
2. 在MySQL客户端使用命令修改
	`ALTER DATABASE  dbname  DEFAULT CHARACTER SET   gbk`

### 数据表操作
一个网站可以有多张表：新闻表、管理员表、产品表、留言表.
#### 显示当前数据库中的所有表
** 语法 ** ：`show tables  FROM db_name`
** 说明 **：查询某一个数据库中的所有的表

#### 创建数据表
** 语法结构： ** `CREATE TABLE table_name(
	列名1  列的类型类型   列的属性,
	列名2  列的数据类型   列的属性,
	列名3  列的数据类型   列的属性
)`
** 参数说明：**

-	列名1，指定每个字段的名称，命名跟变量一样；
-	列的数据类型：指定每个字段存储什么样的数据；
-	列的属性：对列更详细的设置

```sql
CREATE TABLE 007_news(
	id 		int				not null auto_increment primary key,
	title		varchar(50)		not null,
	content	text				null,
	addate	int(12)			no null
);
```

## 列(字段)的常用属性
### 常用属性

1. `not null | null` 指定列的值可以为空，还是不空，默认为null，一般id字段不能为空
2. ` DEFAULT default_value` ，设置某个列的默认值，默认值可以是字符串或数字。举例：`sex  tinyint   not null  DEFAULT 1;`
3. `auto_increment`：指定某个列为自动增长型，一般是指为id字段，可以保证id的值永不重复；
4. `primary key`：是主键索引。主键索引必须给具有auto_increment属性的字段来添加。主键索引只能是一个，其它的都是普通索引。
	>**索引**：就相当于一本书的目录索引，通过目录查询要看的内容，比直接翻书翻到要快得多。
	id字段是每个数据表都必须有的字段，id字段必须具有这三个属性：not null、auto_increment、primary key。


### MySQL数据类型

#### 整型
- **tinyint**：最小整数，1个字节表示，-128~127(带符号)  0-255、如：性别、邮件是否已读
-	**smallint**：小型整数，2个字节表示，0-65535，如：工资
-	**mediumint**：中型整数，3个字节表示，0-1677万
-	**int**：一般整数，4个字节表示，0-42亿，如：文章的点击率
-	**bigint**：大型整数，8个字节表示，2^64-1

#### 浮点型
-	**float(m,d)**：可以精确到小数点后7位，m代表总长度，d代表小数位数；
		-	**float(6,2)**：表示总长度为6位(不含小数点)，小数位数是2位。如：1200.65
-	**double**：可以精确到小数点后15位。

#### 字符型

-	**char(M)**：固定宽度，取值范围0-255个,9字符，如：新闻标题、贴子标题等
		-	**char[10]**，假设我存了5个字符，其它的空间会用空格填充。**参数M**指定字段的宽度；
-	**varchar(M)**：自动伸缩型，取值范围0-65535个字符，如：新闻标题、贴子标题等
		-	**varchar(10)**，假设我存了5个字节，它的长度应该是6，这里多出的1是字符长度。

#### 文本型
**TINYTEXT**，1个字节，0-255个字符
**TEXT**，2个字节，0-65535个字符
**MEDIUMTEXT**，3个字节，0-1677万个字符
**LONGTEXT**，4个字节，0-42亿个字符

#### 日期时间型
**Date**：格式YYYY-MM-DD存储，如：2014-08-01
**Time**：格式HH:mm:ss存储，如：12:09:30
**Datetime**：格式YYYY-MM-DD HH:mm:ss存储
**Timestamp**：格式YYYY-MM-DD HH:mm:ss

#### 在MySQL的客户端如何显示简体中文？
因为MySQL的客户端默认字符集，应该是GBK，因此显示时，要把当前的显示字符集改为GBK；
格式：`set names gbk`
只需要设置数组库的字符集，数据表将继承数据库中的字符集。

#### show命令
1. 显示MySQL主机的所有数据库：`SHOW DATABASES`;
2. 显示某个数据库中的所有表格：`SHOW TABLES [FROM db_name]`;
3. 显示创建数据库时的语句：`SHOW create database db_name`
4. 显示某个数据库中表的结构：`SHOW TABLE table_name [FROM db_name]`

### SQL简介
**SQL**，`Structured Query Language`结构化查询语言。SQL是操作和管理数据库的语言。
常用的SQL语句：增加、删除、修改、查询。

表定义语句
#### 修改数据表
**语法**：`ALTER TABLE table_name`
**提示**：使用phpMyAdmin来修改数据表
#### 删除数据表
**语法**：`DROP TABLE table_name FROM db_name`
#### 显示表结构
**语法**：`Describe table_name`
**功能**：显示某一个表的结构

#### 增加数据 INSERT INTO
语法：`INSERT INTO table_name(title,author,content,addate) VALUES(‘从8月开始每个人都可以申请城市户口’,’admin’,’内容……’,11010101010)`
**注意事项**：
- 字段列表与值的内容列表，个数和顺序必须一致；
- id字段不需要管它，它是自动增长型。

#### 删除记录DELETE FROM
**语法**：`DELETE FROM table_name [WHERE条件]`
**举例**：

```sql
DELETE FROM news WHERE id=3;  #删除id=3的记录
DELETE FROM news WHERE id<4;  #删除id<4的记录
DELETE FROM news WHERE id>10 and id<20;  #删除20>id>10的记录
DELETE FROM news WHERE id>10 or author=’admin’ ; #删除id>10的所有记录，或者author=’admin’记录
```
`TRUNCATE table_name`
**功能**：删除所有数据，并重新将id值归0.
**说明**：与`delete from`删除全部数据要**快的多**。
**举例**：TRUNCATE news

#### 修改记录 UPDATE SET
**语法**：`UPDATE table_name SET 字段1=新值1,字段2=新值2 [WHERE条件]`
**注意**：更新数据时，一定要指定**WHERE**条件，否则，整个表都会更新为一样

```sql
#举例：
	UPDATE news SET author=’zhangsan’,hits=100000 WHERE id=120  //id=120的记录修改
	UPDATE news SET title=’新闻的新标题’ WHERE id=130;
```

#### 查询数据SELECT
**语法**：`SELECT *|字段列表 FROM table_name [WHERE条件] [ORDER BY 字段 ASC|DESC] [LIMIT限定输出的结果]`
**参数**：
-	`*`：将列出所有字段的数据，一般是当字段少的时候才用
-	**字段列表**：指定要查询的字段，多个字段间用逗号隔开，如：SELECT id,title,addate FROM 007_news
-	**[WHERE条件]**指定查询的条件；
-	**[ORDER BY]**对哪些字段进行排序，排序分升序(ASC)和降序(DESC)
-	**[LIMIT]**限制输出的记录数

**WHERE条件子句**
`Like`运算符：实现字段模糊查询，比如：查询所有标题中含有北京的所有记录。
`%`：相当于windows系统中的搜索中的匹配符号“*”

```sql
WHERE title LIKE ‘%北京%’;   #标题中含有北京的记录
WHERE author LIKE ‘a%’;     #查询以“a”字符开头的作者
```

**Order By排序子句**
对一个字段或多个字段进行排序，排序的关键字有两个：升序(ASC)默认、降序(DESC)

```sql
SELECT * FROM news ORDER BY id DESC  #对id字段进行降序排列
SELECT * FROM news ORDER BY author ASC,addate DESC  #作者升序排列，时间倒序排列
```

**Limit子句**
限定要输出的记录数。
**语法**：LIMIT startrow,rows
**参数**：startrow表示开始行号，rows表示要显示多少条记录
**提示**：LIMIT语句主要应用于 ，网页的数据分页。
**举例**：

```sql
LIMIT 0,10   #从第0行起，输出10条记录，不包括第0行。
LIMIT 1,10   #从第1行起，输出10条记录，不包括第1行。
LIMIT 15,10  #从第15行起，输出10条记录，不包括第15行。
```
# mysql数据库(2)

### 数据库词汇
- **数据**：data，凡是能携带信息的媒介都是数据
	- **硬盘数据**：保存在磁盘中，以二进制形式保存
	- **内存数据**：运行在内存中
- **数据库**：Database，高效存储和处理数据的媒介（凡是存放数据的地方都可以称之为数据库），数据库分为两大阵营：关系型数据库，非关系型数据库。
- **数据库系统**：Database System = DBMS +DB，DBMS（Database Management System）管理数据库
- **DBA**：Database Administrator，。

#### 关系型数据库SQL
**定义**：建立在关系模型上的数据库。
**关系模型**：通过各种关系来体现数据与数据之间的联系的模型。

**关系型数据库**：大型（ORACLE，DB2），中型（mysql，SqlServer），小型（access）
**mysql**：最高并发量千万级，免费
**ORACLE**：收费

**通俗**：关系型数据库就是一张二维表（具有行和列，还有表头），用来管理表内的数据关系和表与表之间的关系。
设计一个简单的教学系统
	**实体**：entity，自然界中所看到的实物的一种分类。
	**实体**：学生，老师，教室

体现表内数据与数据之间的关系

**关系型数据库特点**：如果某个数据不完整，那么数据库在磁盘空间上一样的需要分配空间来保存该数据。关系型数据库比较占磁盘空间。

学生与班级有关系
通过在学生表增加一个字段保存对应的班级名称，从而实现了学生表与班级表的
以上体现的就是实体与实体之间的联系
#### 非关系型数据库
**定义**：所有不是关系型数据库的数据库都是非关系型数据库
**NOSQL**：Not Only SQL。
**非关系型数据库保存数据的方式**：键值对

**特点**：
- 运行在内存
- 使用键值对来保存和表示数据
- 运行之后，会进行数据同步（将内存的数据写入到磁盘）

**关系型数据库和非关系型数据对比**
- 保存数据的介质不同（关系型在磁盘，非关系型在内存）
- 非关系型数据库效率比关系型数据库高得多
- 关系型数据库比非关系型数据库安全

### SQL：Structured Query Language，结构化查询语言。
**SQL是一种关系型数据库操作语言，也是一种编程语言**
#### SQL包含三个部分：
- **DDL**：`Data Definition Language`，数据定义语言，库和表的维护create，drop，alter
- **DML**：`Data manipulation Language`，数据操作语言（DQL：Data Query Language），数据的查询，select
- **DCL**：`Data Control Language`，数据控制语言，用于数据库的权限管理，grant，revoke

### SQL的基本操作

`CRUD`：create（创建：增），read/retrieve（读取：查），update（更新：改），delete（删除：删）



#### 服务端内部结构
服务器是由数据库系统在帮助运行。
在服务器端，有四个对象，分别是：数据库管理系统->数据库->数据表->数据字段->管理数据
### 数据库基本操作
**数据库基本操作包含三个部分：库操作，表操作（字段操作），数据操作**
### 库操作
SQL语句是以行为执行单位，每行结束都应该有结束符号分号（有特例：建议每行语句
都有分号）
**新增数据库**：create database 数据库名字 [库选项];
**库选项：**
**字符集设置**（charset）：表示以后在当前数据库存储的数据，默认采用utf-8的字符集存储
校对集设置（collate）：如何比较大小

##### 执行以上语句，数据库管理系统做了哪些事情？
- 创建了一个叫做mydatabase的数据库（默认使用utf8来存储数据）
- 会在磁盘里开辟一块空间来存储数据（对应外部体现就是创建一个文件夹，文件夹的名字叫做mydatabase）
- 文件夹的路径可以通过my.ini查看

新建的数据库
库选项在数据库文件夹下有一个对应的文件db.opt

#### 数据库命名规范
- 使用字母，下划线和数字构成
- 不能是关键字，如果是关键字，需要使用反引号将名字包裹
- 反引号：esc下面的波浪线按键对应的英文状态下的输出

> 可以使用中文作为数据库名字，但是也需要使用反引号（强烈建议：不用使用中文）


#### 查看数据库：
查看数据库基本信息：`show databases`;||模糊查询`：show databases like ‘pattern’`

**模糊匹配**：%匹配任何内容，_表示匹配一个字符

下划线使用
查看数据库创建语句：`show create database 数据库名字`

**修改数据库**：数据库名称不可修改，只能修改数据库的库选项
语法：alter database 数据库名字 [库选项]

删除数据库：`drop Database 数据库名字;`

#### 表操作
**表不能脱离字段存在，字段也不能脱离表，所谓的表操作就是表和字段同时操作。**
- 新增表：`create table 表名(字段1 字段类型,字段2 字段类型)[表选项]`
  - 字段必须要有字段类型：字段 字段类型
  - 字段与字段之间使用逗号分隔
  - 最后一个字段不需要使用逗号

- **表选项**
	- **字符集**：当前表的数据采用什么字符集保存，字符集以表的字符集为标准
	- **存储引擎**：当前表的数据采用什么样的存储引擎来存储
存储引擎：不同存储和处理数据的方式

**创建数据库出现问题**
>注意：数据表必须存储在数据库的内部。
两种方式解决以上问题
1. 显示指定数据库：在创建表名的时候使用：库.表名

2. 隐式的指定数据：事先进入到某个数据库的环境：use 数据库名字

创建表语句执行之后的结果：在对应的数据库文件夹下创建两个对应的数据表的结构文件

该结构与选定的存储引擎有关系

#### 存储引擎：InnoDB和Myisam
- InnoDB：只会创建一个表结构文件，其他的索引和数据存放在ibdata1文件中
- Myisam：会创建三个文件，一个是结构文件，一个是数据文件，一个是索引文件

- 查看表
  - **查看表基本信息**：`show tables || show tables like ‘pattern’;`
  - **查看表的创建语句**：`show create table表名;`
  - **查看表结构**：`desc|describe 表名/show columns from 表名`


- 修改表
可以修改表的名字，表的字段的增删改查，字段的属性的修改，字段的位置的修改
**语法**：`alter table 表名 [add/modify/drop] [column] 字段名字 [字段类型] [字段位置]`
增加字段
`alter table 表名 add column 字段名字 字段类型 [位置]`
字段默认在表最后增加

位置：first表示在最前面，after表示在某个字段之后（默认其实是after在最后一个字段之后）

- 修改字段
修改字段位置，修改字段的类型，修改字段的名字
修改字段类型+字段位置

- 修改字段名字
alter table 表名 change 旧字段 new字段 字段类型 字段位置

注意：不管是修改字段的那部分都应该跟上字段类型。

- 删除字段
alter table 表名 drop 字段名字


语法：rename table 旧表名 to 新表名


- 删除表：drop table 表名

删除表还会对表文件进行删除

>注意：
创建过程中会不知道当前表名是否存在：if not exists表示只有表名不存在的时候才去创建，否则放弃执行；

删除表的过程中，不知道表是否已经存在：if exists

数据库和数据表都不能随意的删除，删除具有不可逆性。如果确定要删除数据库或者数据表，那么必须要事先备份。


### 数据操作
新增数据：insert into 表名 (字段列表) values(值列表)
字段列表可以没有，意味着值列表里的字段数必须与表中的字段数完全一致


**插入数据必须注意**
插入的值类型必须与数据字段定义的数据类型一致，除了`整型`可以不加引号之外，其他的都要加上引号
整型也可以加上引号

在严格模式下，只能将数值字符串转化成数值
在严格模式下，自增不能使用空字符串来代替
允许一次性插入多条记录，在values字段后面使用逗号分隔即可


- 查看数据：`select 字段列表 from 表名 [where 条件]`
- 修改（更新）数据：`update 表名 set 字段 = 值 [where条件]`
- 删除数据：`delete from 表名 [where条件]`

>注意：一定要小心删除数据，切记需要使用where条件，在删除之前需要对数据进行备份

行（row）和记录（record）：行和记录表示的意思是完全一样的，行是站在表结构的角度上定义，而记录是站在数据的角度上去定义
列（column）和字段（Field）：与行和记录的区别是一样的。

### 字符集问题（乱码问题）
mytable1存储的数据是utf8字符集（在创建表的时候，指定了表的数据存储字符集为utf8）
cmd控制台只能是gbk格式的数据：说明cmd下只能输入和显示gbk格式的数据

set names gbk的功能


客户端与服务端进行不同编码的通信的原理


了解数据库的字符集
查看数据库支持哪些字符集？show character set;

mysql支持39中字符集编码。

查看服务器对客户端的默认识别方式：将客户端当前何种字符集对待。
show variables like ‘character_set_%’;


- 要保证服务器能够正确识别客户端传过去的数据，只要保证character_set_client的字符集与客户端的字符集一致即可。
set character_set_client = gbk;

- 要保证服务器能够正确的给客户端提供对应字符集的数据，只要保证character_set_results与客户端的字符集一致即可
set character_set_results = gbk;

- set names gbk:所做的事情就是将传输数据以及接受数据都设置成当前客户端的字符集
set names gbk;
<=========>
set character_set_client = gbk;
set character_set_connection = gbk;
set character_set_results = gbk
set character_set_database = gbk;

在使用cmd下面的mysql.exe的时候：set names gbk
在使用EditPlus的时候，EditPlus下面的编码是ANSI，ANSI代表当前电脑默认的字符集，中国大陆销售的电脑默认都是gbk编码：set names gbk
在使用EditPlus的时候，EditPlus下面的编码是utf-8：set names utf8

一旦数据库存储的数据本身是乱码，那么任何修改都不可以生效，全部查看到的都是乱码。
