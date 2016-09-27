---
title: PyMySQL Usage
date: 2016-08-27 20:45:41
tags:
---


Reference to:
[runoob](http://www.runoob.com/python3/python3-mysql.html)
[pythontab](http://www.pythontab.com/html/2015/pythonjichu_1009/962.html)

## PyMySQL
Python 3.X 版本默认连接MySQL的一个库

## Install & Download
Official URL -> https://github.com/PyMySQL/PyMySQL (https://github.com/PyMySQL/PyMySQL) 

OR install it with pip 
```
$ pip install PyMySQL
```

OR git the package and install by manually
```
$ git clone https://github.com/PyMySQL/PyMySQL
$ cd PyMySQL/
$ python3 setup.py install
```

OR curl with specified veriosn that you want
```
$ # X.X 为 PyMySQL 的版本号
$ curl -L https://github.com/PyMySQL/PyMySQL/tarball/pymysql-X.X | tar xz
$ cd PyMySQL*
$ python3 setup.py install
$ # 现在你可以删除 PyMySQL* 目录
```



---
### 数据库连接

```
import pymysql

#打开数据库连接
conn = pymysql.connect('localhost', 'username', 'password', 'db_name')

#获取一个游标
cur = conn.cursor()

#执行查询命令
cur.execute("select * from user")

# 获取数据
data = cur.fetchall()
data = cur.fetchone()		#获取单条数据

# 关闭游标
cur.close()

# 关闭数据库资源
conn.close()
```



---
### 创建数据库表
```
cursor.execute('DROP TABLE IF EXISTS EMPLOYEE')

sql = '''CREATE TABLE EMPLOYEE (
	FIRST_NAME	CHAR(20) NOT NULL,
	LAST_NAME	CHAR(20),
	AGE	INT,
	SEX	CHAR(1),
	INCOME	FLOAT)'''

cursor.execute(sql)

db.close()
```



---
### 数据库插入操作

```
cursor = db.cursor()

#SQL 插入语句
sql = """INSERT INTO EMPLOYEE(FIRST_NAME,
         LAST_NAME, AGE, SEX, INCOME)
         VALUES ('Mac', 'Mohan', 20, 'M', 2000)"""

# 或这种形式
sql = "INSERT INTO EMPLOYEE(FIRST_NAME, \
       LAST_NAME, AGE, SEX, INCOME) \
       VALUES ('%s', '%s', '%d', '%c', '%d' )" % \
       ('Mac', 'Mohan', 20, 'M', 2000)

try:
    cursor.execute(sql)
    db.commit()
except:
    db.rollback()	#发生错误实行回滚操作

db.close()		
```



---
### 数据库查询操作
> * fetchone()	获取下一个查询结果集，结果集是一个对象
> * fetchall()	接收所有返回行
> * rowcount()	只读属性，返回execute()方法后影响的行数





