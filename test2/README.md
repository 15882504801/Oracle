# Oracle
 第1步：以system登录到pdborcl，创建角色wangyu_res_view和用户wangyu，并授权和分配空间：

```sql
$ sqlplus system/123@pdborcl
SQL> CREATE ROLE wangyu_res_view;
Role created.
SQL> GRANT connect,resource,CREATE VIEW TO wangyu_res_view;
Grant succeeded.
SQL> CREATE USER wangyu IDENTIFIED BY 123 DEFAULT TABLESPACE users TEMPORARY TABLESPACE temp;
User created.
SQL> ALTER USER wangyu QUOTA 50M ON users;
User altered.
SQL> GRANT wangyu_res_view TO wangyu;
Grant succeeded.
SQL> exit
```

![第一步截图](https://github.com/15882504801/Oracle/blob/master/test2/第一步.jpg)

- 第2步：新用户wangyu连接到pdborcl，创建表mytable和视图myview，插入数据，最后将myview的SELECT对象权限授予hr用户。

```sql
$ sqlplus wangyu/123@pdborcl
SQL> show user;
USER is "NEW_USER"
SQL> CREATE TABLE mytable (id number,name varchar(50));
Table created.
SQL> INSERT INTO mytable(id,name)VALUES(1,'zhang');
1 row created.
SQL> INSERT INTO mytable(id,name)VALUES (2,'wang');
1 row created.
SQL> CREATE VIEW myview AS SELECT name FROM mytable;
View created.
SQL> SELECT * FROM myview;
NAME
--------------------------------------------------
zhang
wang
SQL> GRANT SELECT ON myview TO hr;
Grant succeeded.
SQL>exit
```

![第二步截图](https://github.com/15882504801/Oracle/blob/master/test2/第二步.jpg)

- 第3步：用户hr连接到pdborcl，查询wangyu授予它的视图myview

```sql
$ sqlplus hr/123@pdborcl
SQL> SELECT * FROM wangyu.myview;
NAME
--------------------------------------------------
zhang
wang
SQL> exit
```
![第三步截图](https://github.com/15882504801/Oracle/blob/master/test2/第三步.jpg)

查看数据库的使用情况

![查看数据库的使用情况截图](https://github.com/15882504801/Oracle/blob/master/test2/查看数据库使用情况.jpg)
