Sybase ASE参考
===================

常用数据类型
----------------
* int
* numeric(p, s) (精确)
* float (非精确)
* money
* datetime
* date
* time
* char/char(n)/character
* varchar/varchar(n)
* bit (0或1)

常用全局变量
----------------
@@datefirst: 一周首日
@@dbts: 系统时间戳
@@error: 系统最近生成的错误代码
@@procid: 当前存储过程ID
@@rowcount: 上一个query影响的行数
@@servername: 服务器名
@@spid: 当前系统进程ID
@@version: 系统版本信息

常用函数
-------------

数学
*********
abs(nums)
avg(nums)
sum(nums)
max(nums)
min(nums)
var(nums)
ceiling(num)
floor(num)
round(num, decimal_places)
count(expr)
sign(num)

转换/运算
***********
cast（expr as datatype)
isnull(expr1, expr2): 若expr1是null，则expr2
nullif(expr1, expr2): 若expr1 == expr2则null
space(int): 空格*int
str(num)
case: case when condition then expr else expr end 或者 case expr when expr then expr else expr end

数据/类型
**************
datalength(expr): 数据多少bytes
hash(expr): 返回hash string

字符串
**********
len(str) = char_length(str)
charindex(str1, str2): str1在str2中的位置(索引基数1), 若无返回0
replicate(str, int): str重复int次
substring(str, start, length)
str_replace(str1, str2, str3): 将str1中出现的str2替换为str3

isdate(str)
isnumeric(str)

left(str, int)
right(str, int)

upper(str)
lower(str)

时间
**********
current_date() -> date
current_time() -> time
getdate() -> datetime

dateadd(date_part, integer, date/time): 加减时间, date_part = year|month|day|yy|mm...
datediff(date_part, date/time1, date/time2): 时间差

datename(date_part, date/time) -> str: 返回时间的date_part的字符串表示
datepart(date_part, date/time) -> date/time: 返回时间的date_part的date/time类型
day(date/time)
month(date/time)
year(date/time)

其他
*********
db_id(db_name)
db_name(db_id)
tempdb_id()

user: 返回当前用户名，注意没有括号
user_id(user_name)
user_name(user_id)


object_id(object_name)
object_name(object_id)
object_owner_id(object_id)
col_name(object_id, column_id)

col_length(object_name, column_name)
row_count(dbid, object_id): 表的估计行数

lockscheme() -> 'allpages', 'datapages', 'datarows'
next_identity(table): 该表下一个insert将用的identity值

is_singleusermode()
pagesize(object_name/object_id)
used_pages(dbid, obejct_id): 目前已用page量

show_role(): 当前用户的role
role_id(role_name)
role_name(role_id)
role_contain(role1, role2): 若role2包含role1则返回1

常用命令
----------------

DDL
********
CREATE DATABASE
CREATE TABLE
CREATE PROCEDURE
CREATE FUNCTION
CREATE INDEX
CREATE VIEW
CREATE TRIGGER
CREATE SCHEMA
CREATE PLAN
CREATE PROXY_TABLE
CREATE SERVICE

ALTER DATABASE
ALTER TABLE
TRUNCATE TABLE

DROP TABLE
DROP PROCEDURE
DROP FUNCTION
DROP INDEX
DROP VIEW
DROP TRIGGER
DROP SERVICE

DML
********
SELECT ... FROM ... WHERE ... GROUPY BY ... HAVING ...
INSERT
UPDATE
DELETE
MERGE

Procedural/Transactional
****************************
USE
DECLARE
SET
IF ... ELSE ...
WHILE
BEGIN ... END
CONTINUE/BREAK
WAITFOR
RETURN

PRINT
RAISERROR

EXECUTE
LOCK TABLE

BEGIN TRANSACTION
ROLLBACK
COMMIT
CHECKPOINT

COMPUTE CLAUSE
