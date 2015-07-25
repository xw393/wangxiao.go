---
layout: post
title: Configure MySQL database on Mac
date: 2015-07-22
categories: resources how-to
tags: [Mac, R, MySQL]
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


Then, MySQL can be easily opened in the terminal just using the code: `mysql -u root -p`.



###Basic MySQL commands:


{%highlight SQL%}
show databases; 
/*Display all the databases in MySQL*/

use xxx(dataBaseName);  /*Open a database*/

create database (dataBaseName);
/*Create a new database*/

/*The operations below require a database being opened first*/

show tables; 
/* Display all the tables in the current database*/

create table tableName (column1 dataType,
                        column2 dataType,
                        ...);
/* Create a new table in the database. After the datatype, primary key, foreign key or not null can be set.*/

{%endhighlight%}



### Create New Users

{%highlight SQL%}
/* Login into database using administrator account*/
@>mysql -u root -p
@>password

/* Set the dedault database.*/
mysql>use mysql

/* create a new user */
mysql>create user 'testuser'@'localhost' identified by 'testpassword';

mysql>flush privileges; /*confirm changes */

/* create a new database. */
mysql>create database testdb;

/* Grant privilegs of a database to the user*/
mysql>grant all privileges on testdb.* to testuser@localhost identified  by 'testpassword';

mysql>flush privileges

/* login database with a specific user.*/
@>mysql -u testuser -p
@>password

{%endhighlight%}


### Delete Users

When we want to delete a user created before, we first need to login MySQL using administrator account.

{% highlight bash %}
> @>mysql -u root -p  
> @>password
{% endhighlight%}

The code to delete specific user or database is shown below:
{% highlight SQL%}
 mysql>Delete FROM user Where User='test' and Host='localhost';

 mysql>flush privileges;

 mysql>drop database testDB; -- delete the database

 mysql>drop user username@'%'(or @localhost);

 mysql>drop user username@ localhost; 

{% endhighlight%}


###Change User's Password 

{%highlight SQL%}
  @>mysql -u root -p

  @>password

  mysql>update mysql.user set password=password('new password')
         where User="test" and Host="localhost";
         
  mysql>flush privileges;
{%endhighlight%}


##Connect to MySQL with Python in MAC

  **Installation environment: OS X Yosemite, Python 2.7.9**


  
  The official API MySQLdb is contained in the package `MySQL-python`. Therefore, when using `pip` to install the `MySQLdb`, just simply execute the command in Terminal:`pip install MySQL-python`.

  
### Solve an error `Reason: image not found`

  
  After installing the `MySQL-python` successfully, let's import this package in the Python to connect to MySQL database. However, an error as follows may occur:
  
 {% highlight python %}
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
 {% endhighlight %}
  
  
Don't worry. The solution is easy. Just open the terminal and execute command:  

{% highlight bash%}   
> sudo ln -s /usr/local/mysql/lib/libmysqlclient.18.dylib /usr/lib/libmysqlclient.18.dylib

> sudo ln -s /usr/local/mysql/lib /usr/local/mysql/lib/mysql
{% endhighlight%}


Just want to have a test whether the code highlight works, so show some python code below.

{% highlight python %}
import numpy
from scipy import stats
import pandas
import matplotlib.pyplot as plt

print 'Hello, world!!'

x = 11111
b = 2222
y = x + b

{% endhighlight %}

Then re-open your Python and import the package again, I think the problem will probably be solved. Yeah! :)

