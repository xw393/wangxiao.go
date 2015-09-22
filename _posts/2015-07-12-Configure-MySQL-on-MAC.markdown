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

