---
layout: post
title:"Configure MySQL on MAC"
---

In the root directory, open the `.bash_profile` to add the MySQL path in it.

```
cd ~  
vi .bash_profile
```

Add the codes below to set the default address of your MySQL, and restart the terminal:

```
export PATH=$PATH:/usr/local/mysql/bin
```

Then, MySQL can be easily opened in the terminal just using the code:

```
mysql -u root -p
```

###Basic MySQL commands:
```
show databases; /*Display all the databases in MySQL*/
use xxx(dataBaseName);  /*Open a database*/
create database (dataBaseName); /*Create a new database*/

/*The operations below require a database being opened first*/

show tables; /* Display all the tables in the current database*/
create table tableName (column1 dataType,
						column2 dataType,
						...);
/* Create a new table in the database.
		After the datatype, primary key, foreign key or not null can be set.*/
```

### Create New Users
```
以管理员身份登录mysql

@>mysql -u root -p
@>password

选择mysql数据库

mysql>use mysql

创建用户并设定密码

mysql>create user 'testuser'@'localhost' identified by 'testpassword';

使操作生效

mysql>flush privileges;

为用户创建数据库

mysql>create database testdb;

为用户赋予操作数据库testdb的所有权限

mysql>grant all privileges on testdb.* to testuser@localhost identified  by 'testpassword';

使操作生效

mysql>flush privileges

8、用新用户登录

@>mysql -u testuser -p
@>password
```

### Delete Users
```
 @>mysql -u root -p

 @>密码

 mysql>Delete FROM user Where User='test' and Host='localhost';

 mysql>flush privileges;

 mysql>drop database testDB; //删除用户的数据库

删除账户及权限：>drop user 用户名@'%';

　　　　　　　　>drop user 用户名@ localhost; 
```


###Change User's Password 
```
  @>mysql -u root -p

  @>密码

  mysql>update mysql.user set password=password('新密码')
  		 where User="test" and Host="localhost";
  		 
  mysql>flush privileges;
```
  
  
  
  
###Connect to MySQL with Python in MAC
  
  **Installation environment: OS X Yosemite, Python 2.7.9**
  
  The official API MySQLdb is contained in the package `MySQL-python`. Therefore, when using `pip` to install the `MySQLdb`, just simply execute the command in Terminal:
  
  ```
  pip install MySQL-python
  ```
  
### Solve an error `Reason: image not found`
  
  After installing the `MySQL-python` successfully, let's import this package in the Python to connect to MySQL database. However, an error as follows may occur:
  
  ```python
  >>> import MySQLdb
/Library/Python/2.7/site-packages/MySQL_python-1.2.3-py2.7-macosx-10.7-intel.egg/_mysql.py:3: UserWarning: Module _mysql was already imported from /Library/Python/2.7/site-packages/MySQL_python-1.2.3-py2.7-macosx-10.7-intel.egg/_mysql.pyc, but /Users/***/Downloads/MySQL-python-1.2.3
 is being added to sys.path
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "MySQLdb/__init__.py", line 19, in <module>
    import _mysql
  File "build/bdist.macosx-10.7-intel/egg/_mysql.py", line 7, in <module>
  File "build/bdist.macosx-10.7-intel/egg/_mysql.py", line 6, in __bootstrap__
ImportError: dlopen(/Users/***/.python-eggs/MySQL_python-1.2.3-py2.7-macosx-10.7-intel.egg-tmp/_mysql.so, 2): Library not loaded: libmysqlclient.18.dylib
  Referenced from: /Users/***/.python-eggs/MySQL_python-1.2.3-py2.7-macosx-10.7-intel.egg-tmp/_mysql.so
  Reason: image not found
  ```
  
  Don't worry. The solution is easy. Just open the terminal and execute command:
  
  ```
  sudo ln -s /usr/local/mysql/lib/libmysqlclient.18.dylib /usr/lib/libmysqlclient.18.dylib
  sudo ln -s /usr/local/mysql/lib /usr/local/mysql/lib/mysql
  ```
  
  Then re-open your Python and import the package again, I think the problem will probably be solved. Yeah! :)
  
  
  