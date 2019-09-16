#### 服务器相关

|要求|语句|
| ---------- | ---------------------------------------------------- |
| 连接数据库 | mysql -h 地址 -P 端口 -u 用户名 -p密码 [数据库名] |
| 修改用户密码 | set password=password("youpassword");或<br />alter user 'root'@'localhost' identified by 'youpassword'; |
| 刷新权限 | flush privileges; |

#### show语句

| 要求                                     | 语句                                        |
| ---------------------------------------- | ------------------------------------------- |
| 查看所有表                               | show tables ；<br />show tables from 表名； |
| 查看表索引                               | show index from 表名；                      |
| 显示创建表信息                           | show create table 表名；                    |
| 显示哪些线程正在运行（连接器的连接状态） | show processlist；                          |
| 显示系统变量信息                         | show variables；                            |
| 创建数据库                               | create database [ if not exists ] 数据库名; |
| 查看已有数据库                           | show databases;                             |
| 查看当前数据库信息                       | show create database 数据库名;              |
|                                          |                                             |
#### select语句

| 要求                                               | 语句                                                         |
| -------------------------------------------------- | ------------------------------------------------------------ |
| 查看当前数据库                                     | select database();                                           |
| 显示当前时间、用户名、数据库版本                   | select now(), user(), version();                             |
| 查看表的分片信息                                   | explain select * from 表名；                                 |
| 拼接字符串（根据具体需求对concat里的参数进行修改） | select concat(‘user:’,'name',字段,':',user_id)from 表名；    |
| 根据条件判断数量                                   | select userId，count(1) from 表名 where 条件 group by userId； |
| 查询出的数据不为空                                 | 条件后添加 <br />`trim(字段)<>''` 或<br />`trim(字段)!=''` 或<br />`字段 is not null`； |
| 不包含0-9的数字                                    | 条件后添加  not like ‘%[ ^0-9 ]%’                            |
| 从指定的位置查数据                                 | 最后加 limit 20，10；（从第20条开始查，查询10条数据）        |
| 查找15位身份证                                     | 条件后加 length(表示身份证的字段) = 15；                     |

#### insert语句

| 要求           | 语句                                                         |
| -------------- | ------------------------------------------------------------ |
| 整条数据的插入 | insert into 表名 (字段1，字段2,...) values ('值1','值2',...); |

update语句

| 要求         | 语句                                            |
| ------------ | ----------------------------------------------- |
| 更新某个字段 | update 表名 set 字段 = ‘值’ where 字段 = ‘值’； |

#### delete语句

| 要求             | 语句                                                         |
| ---------------- | ------------------------------------------------------------ |
| 根据字段删除数据 | delete from 表名 where 字段 = ‘值’；（不带where条件可删除表中所有的数据） |
| 删除表           | drop table 表名；                                            |
| 删除数据库       | drop database [if exists] 数据库名 （慎用）                  |
| 删除表的数据     | truncate table 表名；（相当于保留表的结构，重新创建了这个表，所有状态相当于新表） |

#### alter语句

| 要求             | 语句                                                         |
| ---------------- | ------------------------------------------------------------ |
| 删除表索引       | alter table 表名 drop index 索引名称key；                    |
| 新增表唯一索引   | alter table 表名 add unique key 索引名称key (索引字段value)； |
| 修改字段为非空   | alter table 表名 modify 字段 类型(长度)  not null；          |
| 修改字段为非必输 | alter table 表名 modify 字段 类型(长度)  default null；      |

