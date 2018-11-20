[TOC]

##### MySQL 5.6 大小写敏感

1. 文件: /etc/mysql/mysql.conf.d/mysqld.cnf
2. 在 [mysqld] 下 添加 lower_case_table_names = 1
3. 重启MySQL, /etc/init.d/mysql restart

##### MySQL dump

```shell
# 指定数据库的导入导出
mysqldump -u root -p123456 test > out.sql # 将test数据库dump到out.sql中
mysql -u root -p123456 test < out.sql # 将out.sql 导入 test 数据库中
# 所有数据库
mysqldump -u root -p123456 --all-databases > all.sql
mysql -u root -p123456 < all.sql
# 指定表
mysqldump -u root -p123456 test table01 > test_table01.sql
mysql -u root -p123456 test < test_table01.sql
or
mysql -u root -p
use test;
source /home/ice/sql/test_table01.sql # 导入某表，
# 导出表结构与数据
mysqldump -h localhost -uroot -p1234 dbname table1 table2 > dump.sql
# 导出表结构
mysqldump -h localhost -uroot -p1234 -d dbname table > dump.sql
```

##### MySQL 添加用户 与 授权

```mysql
# 添加用户 # localhost为用户只能本地登录，远程登录将localhost改为%
insert into mysql.user(Host, User, Password) values("localhost", "test", password("1234"));
# 授权test用户拥有testDB数据库的所有权限
grant all privileges on testDB.* to test@'%' identified by '1234';
# 授权test用户拥有所有数据库的某些权限
grant select, delete, update,create, drop on *.* to test@'%' identified by '1234';
# 刷新系统权限表
flush privileges;
# 删除数据库
drop database test;
# 删除用户
delete from mysql.user where user = 'test' and host = 'localhost';
flush privileges;
```

