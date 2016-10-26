---
title: Python Basic Knowledges
date: 2016-08-30 14:54:59
tags: [Python]
---
Reference to:
[saltycrane](http://www.saltycrane.com/blog/2009/05/converting-time-zones-datetime-objects-python/)
[peiqian.net](http://peiqiang.net/2014/08/15/python-time-and-datetime.html)

<!-- more -->
## Python 概述

## Python 语言基础

### 常量
1. 数字
2. 字符串

#### 转义字符
|转义字符|Description|
|-|-|
|\n| 换行|
|\r| 回车|
|\(在行尾时) | 续行符|
|\b| 退格(Backspace)|
|\000|空|
|\v|纵向制表符|
|\t|横向制表符|

3. 布尔值
True 
False

4. 空值
Null


### 变量
* 标识符名字的第一个字符必须是字母或下划线
* 标识符的第一个字符后面可以由字母，下划线，或数字构成
* 标识符区分大小写，即Score和score是不同的

#### 常量变量的数据类型转换
* 字符串转整数
int(x [,base ])

* 字符串或数字转换为浮点数
float (x) 

* eval() 函数计算字符串中有效的Python表达式，并返回结果
eval(str)
```python
a = "1+2"
print(eval(a))
> 
3
```
* 数值转换为字符串
str(x)

* repr() 函数将对象转换为可打印字符串
repr(obj)

* hex() 将一个整数转换为一个十六进制字符串
hex()

* oct() 将一个整数转换为一个八进制字符串
oct()


### 运算符和表达式

#### 运算符
##### 1. 算数运算符
##### 2. 赋值运算符
##### 3. 位运算符
##### 4. 比较运算符
##### 5. 逻辑运算符
##### 6. 字符串运算符
|字符串运算符|Description|
|-|-|
|+|字符串连接|
|*|重复输出字符串|
|[] | 获取字符串中指定索引位置的字符，索引从0开始|
| [start, end] | 截取字符串中的一部分，从索引位置start开始到end结束|
| in| 成员运算符，如果字符串中包含给定的字符则返回True|
|not in| 成员运算符，如果字符串中不包含给定的字符则返回True|
| r 或者R| 指定原始字符串。原始字符串是指所有的字符串都是直接按照字面的意思来使用，没有转义字符，特殊字符或不能打印的字符串。原始字符串的第一个引号加上字母r或者R|

##### 7. 字符串优先级

### 常用语句
#### 1. 赋值语句
#### 2. 条件分支语句
* if
* else
* elif
#### 3. 循环语句
* while
* for
* continue
* break

### 序列数据结构
#### 1. 列表 list
* len() 列表长度
* index 元素索引
* append() 尾部添加元素
* extend() 将元素分别添加到另一个列表中
* del 删除元素
* list.index() 获取元素索引
* for range() 遍历列表
* for enumerate() 遍历列表的元素索引和元素值
* sort() 正向排序
* reverse() 反向排序
* range(start, end) 

#### 2. 元组 tuple

* len() 元组长度
* index 元素索引
* append() 尾部添加元素
* extend() 将元素分别添加到另一个列表中
* del 删除元素
* list.index() 获取元素索引
* for range() 遍历列表
* for enumerate() 遍历列表的元素索引和元素值
* 内容不可变，没有排序，只能是转换为列表后排序

#### 3. 字典 dict
* len() 字典长度
* dict[] 访问字典值
* update() 合并字典 
* pop() 删除字典元素
* key in dict 判断是否存在
* for in 遍历字典
* dict.clear() 清空字典元素
* dict [] [] 字典嵌套 

#### 4. 集合 set
* set() 创建可变集合
* frozenset() 创建不可变集合
* len() 集合长度
* for in 遍历集合
* set().add 添加元素
* update() 添加元素
* remove() 删除集合
* key in set() 判断元素
* union() 计算两个集合的并集
* | 计算并集
* & 计算交集
* \- 计算差集
* ^ 计算差分


## 函数
### 1. 自定义函数
```python
def 函数名(参数列表):
    函数体
```
* 变量作用域
```python
a = 100        #全局变量
def setNum():
    a = 10     #局部变量
    print(a)   #打印局部变量

setNum()       #调用函数
print(a)       #打印全局变量
```

### 2. 函数参数和返回值
* 普通参数
```python
def func(num):
    print('形参num地址', id(num))

a = 10
func(a)
print('实参a的地址', id(a))
>
形参num地址 4352594864
实参a的地址 4352594864
```

* 列表参数
```python
def sum(list):
    total = 0
    for x in range(len(list)):
        print(list[x], '+')
        total += list[x]
    print('=', total)

list = [15, 25, 35, 45]
sum(list)
>
15 +
25 +
35 +
45 +
= 120
```
* 字典参数
```python
def print_dict(dict):
    for k, v in dict.items():
        print('dict[%s] = ' % k, v)

dict = {'a': 'Apple', 'b': 'Banana', 'g': 'Grape', 'o': 'Orange'}
print_dict(dict)
> 
dict[a] =  Apple
dict[o] =  Orange
dict[b] =  Banana
dict[g] =  Grape
```

* 参数默认值
```python
def say(message, times =1 ):
    print(message * times)

say('Hello')
say('Python', 3)
>
Hello
PythonPythonPython
```
* 默认值参数需要在前
```python
def func(a =1, b, c=10):
    d = a+b*c

func(10, 20, 30)
>
    def func(a =1, b, c=10):
            ^
SyntaxError: non-default argument follows default argument
```

* 函数返回值
```python
def sum(num1, num2):
    return num1 + num2
print(sum(1, 3))
> 
4
````

```python
def filter_even(list):
    list1 = []
    for i in range(len(list)):
        if list[i] % 2 ==0:
            list1.append(list[i])
            i -= 1
    return list1
list = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
list2 = filter_even(list)
print(list2)
> 
[2, 4, 6, 8, 10]
```

#### Python 内置函数

* abs()
```python
print(abs(-1))
>
1
```

* pow() pow(x, y) 返回x的y次幂
```python
print(pow(2, 3))
> 
8
```

* Round()  round(x[, n]) 返回浮点数x的四舍五入值
```python
print(round(80.2345, 2))
>
80.23
```

* divmod()   divmod(a, b) 返回a除以b的商和余数，返回一个元组
```python
print(divmod(8, 3))
>
(2, 2)
```

* lower(), upper(), swapcase(), capitalize(), title()
```python
str = 'Hello World'
print(str.lower())
print(str.upper())
print(str.swapcase())
print(str.capitalize())
print(str.title())
> 
hello world
HELLO WORLD
hELLO wORLD
Hello world
Hello World
```
* ljust(), rjust(), center(), zfil()
```python
str = 'Hello World'
print(str.ljust(20, '*'))
print(str.rjust(20, '*'))
print(str.center(20, '*'))
print(str.zfill(20))
> 
Hello World*********
*********Hello World
****Hello World*****
000000000Hello World
```
* find(), index(), rfind(), rindex(), count(), replace(), strip(), lstrip(), rstrip(), expandtabs()
```python
str = 'Hello World'
print(str.find('l'))
print(str.index('l'))
print(str.rfind('l'))
print(str.rindex('l'))
print(str.count('l'))
print(str.replace(' ', '*'))
print(str.strip())
print(str.lstrip())
print(str.rstrip())
print(str.expandtabs())
>
2
2
9
9
3
Hello*World
Hello World
Hello World
Hello World
Hello World
```
* split()
```python
str = 'Hello World'
print(str.split(' '))
>
['Hello', 'World']
```
* splitlines()
```python
str = 'Hello World'
print(str.splitlines())
>
['Hello World']
```
* join()
```python
list = ['Hello', 'World']
str = '#'
print(str.join(list))
>
Hello#World
```
* 字符串判断 startswith(), endswith(), isalnum(), isalpha(), isdigit(), islower(), isupper()
```python
str = 'Python String Function'
print(str.startswith('P'))
print(str.endswith('P'))
print(str.isalnum())
print(str.isalpha())
print(str.isdigit())
print(str.islower())
print(str.isupper())
>
True
False
False
False
False
False
False
```
* help()
```python
help('print')
> 
Help on built-in function print in module builtins:

print(...)
    print(value, ..., sep=' ', end='\n', file=sys.stdout, flush=False)
    
    Prints the values to a stream, or to sys.stdout by default.
    Optional keyword arguments:
    file:  a file-like object (stream); defaults to the current sys.stdout.
    sep:   string inserted between values, default a space.
    end:   string appended after the last value, default a newline.
    flush: whether to forcibly flush the stream.
```
* type() 
```python
str = 'Hello'
print(type(str))
num = 8
print(type(num))
list = [1, 2, 3]
print(type(list))
>
<class 'str'>
<class 'int'>
<class 'list'>
```

### 面向对象
> * 对象 object：面向对象程序设计思想可以将一组数据和与这组数据有关操作组装在一起，形成实体，这个实体就是对象。
> * 类 class： 具有相同或相似性质的对象的抽象就是类。 若人类是一个类，具体的人就是一个对象
> * 封装：将数据和操作捆绑在一起，定义一个新类的过程就是封装
> * 继承： 继承描述了类之间的关系
> * 方法：也称成员函数，是指对象上的操作，作为类声明的一部分来定义。方法定义了对一个对象可以执行的操作
> * 构造函数：一种成员函数，用来创建对象时初始化对象。构造函数一般与它所属的类完全同名
> * 析构函数：析构函数与构造函数相反，当对象脱离作用域时（例如对象所在的函数已调用完毕），系统自动执行析构函数。

#### 1. 类的声明
```python
class Person:          #定义一个类Person
    def SayHi(self):   #类成员函数必须要有一个参数self,表示类的实例(对象)自身
        print('Hi')

p = Person()           #定义类Person的对象p, 用p来访问类的成员变量和成员函数
p.SayHi()              #调用类Person的成员函数SayHi() 
> 
hi
```
```python
class MyString:
    str = "MyString"
    def output(self):
        print(self.str)

s = MyString()
s.output()
>
MyString
```

#### 2. 构造函数
```python
class MyString:
    def __init__(self):      # __init__构造函数, 通过构造函数对类进行初始化操作
        self.str = "MyString"

    def output(self):
        print(self.str)

s = MyString()
s.output()
>
MyString
```
> * 带参数的构造函数

```python
class UserInfo:
    def __init__(self, name, pwd):
        self.username = name
        self._pwd = pwd

    def output(self):
        print("User: "+self.username+"\nPasswd:" +self._pwd)

u = UserInfo("Rick", "123456")
u.output()
>
User: Rick
Passwd:123456
```

#### 3. 析构函数
```python
class MyString:
    def __init__(self):  #构造函数
        self.str = "MyString"
    def __del__(self):   #析构函数
        print("Bye")

    def output(self):
        print(self.str)

s = MyString()

s.output()
del s   # 删除对象
>
MyString
Bye
```

#### 4. 静态变量
> 静态变量和静态方法是类的静态成员，他们与普通的成员变量和成员方法不同，静态类成员与具体的对象没有关系，而是只属于定义他们的类
```python
class Users(object):
    online_count = 0   # 静态变量 记录当前用户数量
    def __init__(self):  #构造函数, 创建对象时Users.online_count +1
        Users.online_count += 1
    def __del__(self):   #析构函数,释放对象时Users.online_count -1
        Users.online_count -= 1

a = Users()  #创建Users对象
a.online_count += 1
print(Users.online_count)
>
1
```

> * 静态方法
> 静态方法只属于定义他的类，而不属于任何一个具体的对象
> 特点
> 1. 静态方法无需传入self参数，因此在静态方法中无法访问实例变量
> 2. 静态方法不能直接访问类的静态变量，但可以通过类名引用静态变量

```python
class MyClass:
    var1 = "String1"
    @staticmethod   #静态方法
    def staticmd():
        print('I am static method')

MyClass.staticmd()  #调用了静态方法
c = MyClass()
c.staticmd()
>
I am static method
I am static method
```

> * 类方法
> 特点
> 1. 与静态方法一样，类方法可以使用类名调用类方法
> 2. 与静态方法一样，类成员方法也无法访问实例变量，但可以访问类的静态变量
> 3. 类方法需传入代表类的cls参数

```python
class MyClass:
    val1 = "String1"  #静态变量
    def __init__(self):
        self.val2 = "Value 2"
    @classmethod      #类方法
    def classmd(cls):
        print('Class: ' + str(cls) + ',val1: ' + cls.val1 + ', Cannot access value 2')

MyClass.classmd()
c = MyClass()
c.classmd()
> 
Class: <class '__main__.MyClass'>,val1: String1, Cannot access value 2
Class: <class '__main__.MyClass'>,val1: String1, Cannot access value 2
```

#### 5. instance() 函数判断对象类型
> 使用instance()函数检测一个给定的对象是否属于（继承）某个类或类型，是为True，否为False
```python
class MyClass:
    val1 = "String1"   #静态变量
    def __init__(self):
        self.val2 = "Value 2"

c = MyClass()
print(isinstance(c, MyClass))
l = [1, 2, 3, 4]
print(isinstance(l, list))
> 
True
True
```

#### 6. 类的继承
> 类可以继承其他类的内容，包括成员变量和成员函数
```python
import time

class Users:
    username = ""
    def __init__(self, uname):      #构造函数
        self.username = uname
        print('(Construct fucntion:'+self.username+')')

    def DisplayUsername(self):      #类Users的成员函数DisplayUsername
        print(self.username)

#继承类Users
class UserLogin(Users):   #类Users的子类
    def __init__(self, uname, LastLoginTime):
        Users.__init__(self, uname)       #调用父类的Users的构造函数
        self.LastLoginTime = LastLoginTime

    def DisplayLoginTime(self):
        print('Login time: '+self.LastLoginTime)

#获取当前时间
now = time.strftime('%Y-%m-%d %H:%M:%S', time.localtime(time.time()))

MyUser1 = UserLogin('Rick', now)
MyUser2 = UserLogin('Leo', now)
MyUser3 = UserLogin('Josh', now)

MyUser1.DisplayUsername()   #访问类Users的函数
MyUser1.DisplayLoginTime()     #访问子类的函数
MyUser2.DisplayUsername()
MyUser2.DisplayLoginTime()
MyUser3.DisplayUsername()
MyUser3.DisplayLoginTime()

>
(Construct fucntion:Rick)
(Construct fucntion:Leo)
(Construct fucntion:Josh)
Rick
Login time: 2016-09-10 16:20:45
Leo
Login time: 2016-09-10 16:20:45
Josh
Login time: 2016-09-10 16:20:45
```
#### 7. 多态
> 抽象类中定义的一个方法，可以在其子类中重新实现，不同子类中实现的方法也不相同

```python
from abc import ABCMeta, abstractclassmethod

class Shape(object):
    __metaclass__ = ABCMeta
    def __init__(self):
        self.color = "Black"

@abstractclassmethod
def draw(self):
    pass

class circle(Shape):   #Shape子类circle
    def __init__(self, x, y, r):
        self.x = x
        self.y = y
        self.r = r

    def draw(self):
        print("Draw Circle: (%d, %d, %d)" %(self.x, self.y, self.r))

class line(Shape):     #Shape 子类line
    def __init__(self, x1, y1, x2, y2):
        self.x1 = x1
        self.y1 = y1
        self.x2 = x2
        self.y2 = y2

    def draw(self):       #抽象方法draw()又不同的实现,这就是多态
        print("Draw Line: (%d, %d, %d, %d)" %(self.x1, self.y1, self.x2, self.y2))

c = circle(10, 10, 5)
c.draw()

l = line(10, 10, 20, 20)
l.draw()

>
Draw Circle: (10, 10, 5)
Draw Line: (10, 10, 20, 20)
```


### Python 模块

#### sys
```python
import sys

print(sys.platform) #获取当前操作系统平台

#argv可获取命令行参数
print(sys.argv[0])  #当前脚本的文件名

sys.exit()   #退出应用程序

sys.path   #系统路径

>
darwin
/Users/xhxu/python/magedu/test.py
```

---
#### platform

```python

import platform
print(platform.platform()) #获取操作系统类型
print(platform.system())   #获取平台系统信息
print(platform.version())  #操作系统版本
print(platform.machine())  #计算机类型
print(platform.node())     #计算机网络名称
print(platform.processor())#处理器信息
print(platform.uname())    #综合信息
print(platform.python_build())  #python 版本信息
print(platform.python_version()) #Python主版本信息
print(platform.python_compiler()) #Python编译器信息
print(platform.python_branch())   #获取Python的分支情况
>
Darwin-15.5.0-x86_64-i386-64bit
Darwin
Darwin Kernel Version 15.5.0: Tue Apr 19 18:36:36 PDT 2016; root:xnu-3248.50.21~8/RELEASE_X86_64
x86_64
xhxu-mac
i386
uname_result(system='Darwin', node='xhxu-mac', release='15.5.0', version='Darwin Kernel Version 15.5.0: Tue Apr 19 18:36:36 PDT 2016; root:xnu-3248.50.21~8/RELEASE_X86_64', machine='x86_64', processor='i386')
('v3.5.1:37a07cee5969', 'Dec  5 2015 21:12:44')
3.5.1
GCC 4.2.1 (Apple Inc. build 5666) (dot 3)
v3.5.1
```

> * python 解释器有多种版本实现方式
> 1. CPython	默认Python是实现方式。用C语言编写的，当执行代码的时候，Python代码会被转化成字节码，所有CPython是一个字节码解释器
> 2. PyPy	Python写成的解释器，这个解释器代码先转化成c，然后再编译。比CPython性能要好，会把代码转化成机器码
> 3. Jython	Java实现的一个解释器，可以把java模块加载在Python模块中使用
> 4. IronPython C#语言实现，可以使用在.NET & Mono平台的解释器





---
#### math
```python
import math
print(math.e)       #自然对数
print(math.pi)      #pi的值

print('math.ceil(3.4)= ', math.ceil(3.4))       #返回大于等于x的最小整数
print('math.fabs(-3)= ', math.fabs(-3))         #返回x的绝对值
print('math.floor(3.4)= ', math.floor(3.4))     #返回小于等于x的最大整数
print('math.sqrt(4)= ', math.sqrt(4))           #返回x的平方根
print('math.trunc(3.4)=', math.trunc(3.4))      #返回x的整数部分
>
2.718281828459045
3.141592653589793
math.ceil(3.4)=  4
math.fabs(-3)=  3.0
math.floor(3.4)=  3
math.sqrt(4)=  2.0
math.trunc(3.4)= 3
```

---
#### random 
```python
import random
print(random.randint(0, 99))        #随机0-100的整数
print(random.randrange(0, 101, 2))  #随机0-100的偶数
print(random.choice('jklhgy&#&*()%^@'))   #指定字符集随机取一个字符

lst = [1, 2, 3, 4, 5]
random.shuffle(lst)                 #将列表中元素打乱
print(lst)


lst1 = [1, 2, 3, 4, 5, 6]           
print(random.sample(lst1, 3))       #取指定长度片段

>
30
62
@
[4, 5, 2, 1, 3]
[1, 2, 6]
```


---
#### decimal
```python
from decimal import Decimal

print(Decimal('1.0') / Decimal('3.0'))  #浮点计算


from decimal import Decimal
from decimal import getcontext    # getcontext() 获取当前环境
getcontext().prec = 6
print(Decimal('1.0') / Decimal('3.0'))  
>
0.3333333333333333333333333333
0.333333
```

---
#### fractions
```python
import fractions        #处理和表现分数
# x = fractions.Fraction(分子, 分母)

x = fractions.Fraction(1, 6)
print(x)
>
1/6
```

---
#### time

> * Unix timestamp 是一种时间表示方式，是指定义为格林威治时间1970年01月01日00时00分00秒（北京时间1970年01月01日08时00分00秒）起至现在的总秒数。
> * struct_time数组包含9个元素
> 1. year,  4位
> 2. month, 1-12
> 3. day, 1-31
> 4. hours, 0-23
> 5. minutes, 0-59
> 6. seconds, 0-59
> 7. weekday, 0-6
> 8. Julian day, 一年有几天, 1-366
> 9. DST 是否为夏令时



```python
import time
print(time.time())
print(time.localtime(time.time()))  #转换成当前时区的struct_time
>
1473921640.010664
time.struct_time(tm_year=2016, tm_mon=9, tm_mday=15, tm_hour=14, tm_min=40, tm_sec=40, tm_wday=3, tm_yday=259, tm_isdst=0)
```



> * time.strftime(format[, t]) 可以按照指定的格式输出struct_time时间
> %y	两位数的年份表示(00-99)
> %Y	四位数的年份表示（000-9999）
> %m 	月份(01-12)
> %d 	月内中的一天(0-31)
> %H 	24小时制小时数(0-23)
> %I 	12小时制小时数(01-12)
> %M 	分钟数(00-59)
> %S	秒(00-59)
> %a	本地简化星期名称
> %A	本地完整星期名称
> %b	本地简化月份名称
> %B	本地完整月份名称
> %c 	本地相应的日期表示和时间表示
> %j	年内的一天(001-366)
> %p	本地A.M或P.M
> %U 	一年中的星期数(00-53), 星期天为星期开始
> %w	星期(0-6), 星期天为开始
> %W	一年中星期数(00-53), 星期一为星期的开始
> %x 	本地相应的日期表示
> %X	本地相应的时间表示
> %Z	当前时区的名称
> %%	%号本身



```python
import time
print(time.strftime('%Y-%m-%d', time.localtime(time.time())))
>
2016-09-15
```

```python
import time
print(time.ctime())     #返回当前时间的字符串
>
Thu Sep 15 14:51:38 2016
```


```python
#获取当前时间
In [1]: import time

In [2]: time.time()
Out[2]: 1475033600.054703

#将时间戳转换为时间元组
In [3]: time.localtime(time.time())
Out[3]: time.struct_time(tm_year=2016, tm_mon=9, tm_mday=28, tm_hour=11, tm_min=33, tm_sec=26, tm_wda

#格式化输出当前时间
In [4]: time.strftime('%Y-%m-%d %H:%M:%S')
Out[4]: '2016-09-28 11:34:29'
```

```python
#获取时间差
In [10]: import time

In [11]: def t():
   ....:     start = time.time()
   ....:     time.sleep(10)
   ....:     end = time.time()
   ....:     print(end-start)
   ....:     

In [12]: t()
10.004667043685913
```


> * time.clock()
> 这个需要注意，在不同的系统上含义不同。在UNIX系统上，它返回的是“进程时间”，它是用秒表示的浮点数（时间 戳）。而在WINDOWS中，第一次调用，返回的是进程运行的实际时间。而第二次之后的调用是自第一次调用以后到现在的运行时间。（实际上是以WIN32 上QueryPerformanceCounter()为基础，它比毫秒表示更为精确）


```python
import time

if __name__ == '__main__':
    time.sleep(1)
    print('Clock 1:%s ' % time.clock())
    time.sleep(1)
    print('Clock 2:%s ' % time.clock())
    time.sleep(1)
    print('Clock 3:%s ' % time.clock())
>>>
Clock 1:0.028168 
Clock 2:0.028281 
Clock 3:0.028409 
```


> * time.sleep(seconds)
> 延迟时间运行
```python
In [27]: while True:
   ....:     time.sleep(3)
   ....:     print(time.strftime('%H:%M:%S'))
   ....:     

11:58:02

11:58:05

11:58:08
11:58:11
```



> * time.mktime(t)
```python
# 将一个struct_time转换为时间戳,如下time.localtime接收一个时间戳返回一个struct_time，而time.mktime接收一个struct_time，返回一个时间戳

In [1]: import time

In [2]: time.localtime(1407945600.0)
Out[2]: time.struct_time(tm_year=2014, tm_mon=8, tm_mday=14, tm_hour=0, tm_min=0, tm_sec=0, tm_wday=

In [3]: time.mktime(time.localtime(1607945600.0))
Out[3]: 1607945600.0

```


---
### datetime

```python
In [5]: import datetime

In [6]: t = time.time()

获取当前时间
In [8]: datetime.datetime.now().strftime('%Y-%m-%d %H:%M:%S')
Out[8]: '2016-09-28 11:36:53'

In [9]: datetime.datetime.today().strftime('%Y-%m-%d %H:%M:%S')
Out[9]: '2016-09-28 11:37:02'
```


```python
#获取时间差
In [13]: import datetime

In [14]: starttime = datetime.datetime.now()

In [15]: endtime = datetime.datetime.now()

In [22]: print(endtime.second - starttime.second)
19

```

```python
#时间元组struct_time 转化为时间戳
In [23]: import datetime

In [24]: datetime.datetime.now()
Out[24]: datetime.datetime(2016, 9, 28, 11, 51, 21, 305523)

In [25]: datetime.datetime.now().timetuple()
Out[25]: time.struct_time(tm_year=2016, tm_mon=9, tm_mday=28, tm_hour=11, tm_min=51, tm_sec=37, tm_w

In [26]: time.mktime(datetime.datetime.now().timetuple())
Out[26]: 1475034719.0

```




> *  datetime.date: 是指年月日构成的日期(相当于日历)
```python

In [4]: import datetime

In [5]: today = datetime.date.today()

In [6]: today
Out[6]: datetime.date(2016, 9, 28)

# 格式化需要的时间
In [7]: today.strftime('%Y-%m-%d %H:%M:%S')
Out[7]: '2016-09-28 00:00:00'

#转换成struct_time格式，传递给time.mktime(t), 转换成时间戳格式
In [9]: today.timetuple()
Out[9]: time.struct_time(tm_year=2016, tm_mon=9, tm_mday=28, tm_hour=0, tm_min=0, tm_sec=0, tm_wday=


In [11]: time.mktime(today.timetuple())
Out[11]: 1474992000.0

#replace  替换date对象
In [12]: today.replace(year=2014)
Out[12]: datetime.date(2014, 9, 28)

# 将时间戳转化为date对象
In [13]: datetime.date.fromtimestamp(1608058729)
Out[13]: datetime.date(2020, 12, 16)

```


> *  datetime.time: 是指时分秒微秒构成的一天24小时中的具体时间(相当于手表)

```python

In [19]: t = datetime.time(16, 9, 28)

In [20]: t
Out[20]: datetime.time(16, 9, 28)

In [21]: t.strftime('%Y-%m-%d %H:%M:%S')
Out[21]: '1900-01-01 16:09:28'

#datetime.time.replace([hour[, minute[, second[, microsecond[, tzinfo]]]]]) 返回一个替换后的time对象
In [22]: t.replace(hour=9)
Out[22]: datetime.time(9, 9, 28)

In [23]: datetime.time(9, 45, 20)
Out[23]: datetime.time(9, 45, 20)
```


> *  datetime.datetime: 上面两个合在一起，既包含时间又包含日期
```python

In [24]: d1 = datetime.datetime.today()

In [25]: d1
Out[25]: datetime.datetime(2016, 9, 28, 12, 16, 4, 629514)

In [26]: d2 = datetime.datetime(2015, 5, 25, 11, 11, 11, 790945)

In [27]: d2
Out[27]: datetime.datetime(2015, 5, 25, 11, 11, 11, 790945)


# datetime.datetime.now([timezone])
In [28]: datetime.datetime.now()
Out[28]: datetime.datetime(2016, 9, 28, 12, 17, 22, 551326)
```

```python
#获取不同时区
In [63]: from pytz import all_timezones

In [64]: for zone in all_timezones:
   ....:     if 'Asia' in zone:
   ....:         print(zone)
   ....:         
Asia/Aden
Asia/Almaty
Asia/Amman
Asia/Anadyr
Asia/Aqtau
Asia/Aqtobe
Asia/Ashgabat
Asia/Ashkhabad
Asia/Baghdad
Asia/Bahrain
Asia/Baku
Asia/Bangkok
Asia/Barnaul
Asia/Beirut
Asia/Bishkek
Asia/Brunei
Asia/Calcutta
Asia/Chita
Asia/Choibalsan
Asia/Chongqing
Asia/Chungking
Asia/Colombo
Asia/Dacca
Asia/Damascus
Asia/Dhaka
Asia/Dili
Asia/Dubai
Asia/Dushanbe
Asia/Gaza
Asia/Harbin
Asia/Hebron
Asia/Ho_Chi_Minh
Asia/Hong_Kong
Asia/Hovd
Asia/Irkutsk
Asia/Istanbul
Asia/Jakarta
Asia/Jayapura
Asia/Jerusalem
Asia/Kabul
Asia/Kamchatka
Asia/Karachi
Asia/Kashgar
Asia/Kathmandu
Asia/Katmandu
Asia/Khandyga
Asia/Kolkata
Asia/Krasnoyarsk
Asia/Kuala_Lumpur
Asia/Kuching
Asia/Kuwait
Asia/Macao
Asia/Macau
Asia/Magadan
Asia/Makassar
Asia/Manila
Asia/Muscat
Asia/Nicosia
Asia/Novokuznetsk
Asia/Novosibirsk
Asia/Omsk
Asia/Oral
Asia/Phnom_Penh
Asia/Pontianak
Asia/Pyongyang
Asia/Qatar
Asia/Qyzylorda
Asia/Rangoon
Asia/Riyadh
Asia/Saigon
Asia/Sakhalin
Asia/Samarkand
Asia/Seoul
Asia/Shanghai
Asia/Singapore
Asia/Srednekolymsk
Asia/Taipei
Asia/Tashkent
Asia/Tbilisi
Asia/Tehran
Asia/Tel_Aviv
Asia/Thimbu
Asia/Thimphu
Asia/Tokyo
Asia/Tomsk
Asia/Ujung_Pandang
Asia/Ulaanbaatar
Asia/Ulan_Bator
Asia/Urumqi
Asia/Ust-Nera
Asia/Vientiane
Asia/Vladivostok
Asia/Yakutsk
Asia/Yekaterinburg
Asia/Yerevan



#获得东京时间
In [66]: datetime.now(timezone('Asia/Tokyo'))
Out[66]: datetime.datetime(2016, 9, 28, 14, 28, 0, 738564, tzinfo=<DstTzInfo 'Asia/Tokyo' JST+9:00:0

```



> *  datetime.timedelta: 时间间隔对象(timedelta)。一个时间点(datetime)加上一个时间间隔(timedelta)可以得到一个新的时间点(datetime)。比如今天的上午3点加上5个小时得到今天的上午8点。同理，两个时间点相减会得到一个时间间隔。

```python

In [67]: import datetime

In [68]: today = datetime.datetime.today()

In [69]: yesterday = today - datetime.timedelta(days=1)

In [70]: yesterday
Out[70]: datetime.datetime(2016, 9, 27, 13, 29, 59, 72827)

In [71]: today
Out[71]: datetime.datetime(2016, 9, 28, 13, 29, 59, 72827)
```


---
#### 自定义模块
> * 模块是一个.py 的文件，其中包含函数的定义
> * import MODULE_NAME 方法，在同一目录下引用改模块

```python
# mymodule.py
def PrintString(str):
    print(str)

def sum(num1, num2):
    print(num1 + num2)

# test.py
import mymodule
mymodule.PrintString("Hello World")
mymodule.sum(1, 2)
>>>
Hello World
3
```


---
#### os 模块
> * python 的exec系统方法同Unix的exec系统调用是一致的，这些方法适用于子进程中调用外部程序的情况。
> 
> os.system("some_command with args")将命令以及参数传递给你的系统shell，这很好，因为你可以用这种方法同时运行多个命令并且可以设置管道以及输入输出重定向。比如：os.system("some_command < input_file | another_command > output_file")
> 然而，虽然这很方便，但是你需要手动处理shell字符的转义，比如空格等。此外，这也只能让你运行简单的shell命令而且不能运行外部程序。
> 
> 
> system 方法，会运行外部程序，返回外部程序结果。适用于外部程序没有输出结果的情况。
```
In [3]: import os

In [4]: os.system('echo \"Hello World\"')
Hello World
Out[4]: 0



In [8]: val = os.system('ls -la')
total 184
drwxr-xr-x  26 xhxu  FREEWHEELMEDIA\Domain Users   884 Sep 25 20:40 .
drwxr-xr-x   7 xhxu  FREEWHEELMEDIA\Domain Users   238 Sep  6 20:54 ..
-rw-r--r--@  1 xhxu  FREEWHEELMEDIA\Domain Users  6148 Sep 18 19:39 .DS_Store
drwxr-xr-x  13 xhxu  FREEWHEELMEDIA\Domain Users   442 Sep 26 19:29 .git
drwxr-xr-x   7 xhxu  FREEWHEELMEDIA\Domain Users   238 Sep 26 19:29 .idea
-rw-r--r--   1 xhxu  FREEWHEELMEDIA\Domain Users     9 Jul  2 15:48 .python-version
-rw-r--r--   1 xhxu  FREEWHEELMEDIA\Domain Users   199 Sep  8 17:56 1.py
-rw-r--r--   1 xhxu  FREEWHEELMEDIA\Domain Users   936 Sep  8 17:55 1.svg

In [10]: print(val)
0					# 0表示运行正常, 如果是没有返回结果的命令，返回值为256

```


> popen方法， 当需要得到外部程序输出结果时使用。要得到命令的输出内容，需调用read()或readlines()
> 使用stream = os.popen("some_command with args")也能做与os.system一样的事，与os.system不同的是os.popen会给你一个像文件的对象从而你可以使用它来访问哪个程序的标准输入、输出。而且popen还有三个变种都是在I/O处理上有轻微不同。假如你通过一个字符串传递所有东西，你的命令会传递给shell；如果你通过一个列表传递他们，你不用担心逃避任何事。
> 
```
In [11]: os.popen('ls -l ')
Out[11]: <os._wrap_close at 0x10978d828>

In [13]: print(os.popen('ls -l').read())		#调用read()
total 160
-rw-r--r--   1 xhxu  FREEWHEELMEDIA\Domain Users   199 Sep  8 17:56 1.py
-rw-r--r--   1 xhxu  FREEWHEELMEDIA\Domain Users   936 Sep  8 17:55 1.svg
-rw-r--r--   1 xhxu  FREEWHEELMEDIA\Domain Users   331 Aug 12 16:47 Find_name_with-slice-feature.py
-rw-r--r--   1 xhxu  FREEWHEELMEDIA\Domain Users   439 Jul 30 11:36 Happy_Number.py
-rw-r--r--   1 xhxu  FREEWHEELMEDIA\Domain Users   231 Aug 15 17:44 Prime_num.py
-rw-r--r--   1 xhxu  FREEWHEELMEDIA\Domain Users   218 Aug 18 21:04 Prime_num2.py



n [14]: val = os.popen('ls -l').read()			#变量接收命令的返回值

In [15]: if '1.py' in val:				#使用in来判断返回值是否含有此字符串
   ....:     print('Exist')
   ....: else:
   ....:     print('No Exist')
   ....:     
Exist
```


---
#### subprocess模块
> 此模块用于取代os.system, os.popen 模块
> mssh 实现并行ssh的一个工具
```
In [3]: from subprocess import call

In [4]: call(['ls', '-l'])
total 160
-rw-r--r--   1 xhxu  FREEWHEELMEDIA\Domain Users   199 Sep  8 17:56 1.py
-rw-r--r--   1 xhxu  FREEWHEELMEDIA\Domain Users   936 Sep  8 17:55 1.svg
-rw-r--r--   1 xhxu  FREEWHEELMEDIA\Domain Users   331 Aug 12 16:47 Find_name_with-slice-feature.py
-rw-r--r--   1 xhxu  FREEWHEELMEDIA\Domain Users   439 Jul 30 11:36 Happy_Number.py
-rw-r--r--   1 xhxu  FREEWHEELMEDIA\Domain Users   231 Aug 15 17:44 Prime_num.py
-rw-r--r--   1 xhxu  FREEWHEELMEDIA\Domain Users   218 Aug 18 21:04 Prime_num2.py
```









---
### Chapter 6 函数式编程
> * 函数式编程是一种基本风格，其将计算过程看做是数学函数，在代码中，函数的返回值只依赖传入函数的参数，因此使用相同的函数调用函数两次，会得到相同的结果
> 
> * 头等函数(First-class function) 
> 因编程语言把函数视为头等函数，称其拥有头等函数。拥有头程函数的编程语言将函数作为其他函数的参数，也可以将函数作为其他函数的返回值。可以把函数赋值给变量或存储在元组，列表，字典，集合和对象的数据结构中。
>
> * 高阶函数(Higher-order function)
> 其为头等函数的一种实践，将其他函数作为参数或返回结果的函数。
> 
> * 纯函数
> 1. 纯函数与外界交换数据只有唯一的渠道 --- 参数和返回值
> 2. 纯函数不操作全局变量，没有状态，无I/O操作，不改变传入的任何参数的值。
> 3. 容易将纯函数移植到新的运行环境
> 4. 具有透明性，对同一个输入的值，得到相同的输出值
> 
> * 递归
> 递归就是函数里调用自身，使用时，一定要明确递归结束条件，称为递归出口

---
#### lambda 匿名函数
> * 返回函数名 = lambda 参数列表 : 函数返回值表达式语句
```
sum = lambda x, y, z : x+y+z
等同于
def sum(x, y, z):
    return x, y, z
```

> * 数组名 = [(lambda 表达式1)， (lambda 表达式2), ...]
```python
Arr = [(lambda x: x**2), (lambda x: x**3), (lambda x: x**4)]
print(Arr[0](2), Arr[1](2), Arr[2](2))
>>>
4 8 16
```


```python
def math(o):
    if(o==1):
        return lambda x, y: x+y
    if(o==2):
        return lambda x, y: x-y
    if(o==3):
        return lambda x, y: x*y
    if(o==4):
        return lambda x, y: x/y

action = math(1)
print('10+2=', action(10, 2))
action = math(2)
print('10-2=', action(10, 2))
action = math(3)
print('10*2=', action(10, 2))
action = math(4)
print('10/2=', action(10, 2))
>>>
10+2= 12
10-2= 8
10*2= 20
10/2= 5.0
```

#### map() 函数
> * 用于将制定序列中的所有元素作为参数调用制定函数，并将结果构成一个新的序列返回。
> 结果序列 = map(映射函数， 序列1[, 序列2, ...])
```python
arr = map(lambda x: x**2, [2, 4, 6, 8, 10])
for e in enumerate(arr):   #enumerate 会将返回的值中包含索引信息
    print(e)
> 
(0, 4)
(1, 16)
(2, 36)
(3, 64)
(4, 100)
```

```python
arr = map(lambda x, y: x+y, [1, 3, 5, 7, 9], [2, 4, 6, 8, 10])
for e in enumerate(arr):
    print(e)
>
(0, 3)
(1, 7)
(2, 11)
(3, 15)
(4, 19)
```

#### filter() 
> * 对指定的序列执行过滤操作
> filter(函数function, 序列sequence)

```python
def is_even(x):
    return x % 2 == 0

arr = filter(is_even, [1, 2, 3, 4, 5, 6, 7, 8, 9])
for e in enumerate(arr):
    print(e)
> 
(0, 2)
(1, 4)
(2, 6)
(3, 8)
```

#### reduce()
> * 用于将指定序列中的所有元素作为参数按照一定的规则调用指定函数
> 计算结果 = reduce(映射序列，序列)

```python
from functools import reduce
def myadd(x, y):
    return x+y


sum = reduce(myadd, (2, 4, 6, 8, 10))
print(sum)

sum1 = reduce(lambda x, y: x+y, (2, 4, 6, 8, 10))
print(sum1)
>>>
30
30
```

#### zip()
> * 以一系列列表作为参数，将列表中对应的元素打包成一个元组，然后返回元组组成的列表
```python
#长度相等的列表
a = [1, 2, 3]
b = [4, 5, 6]

zipped = zip(a, b)

for i in zipped:
    print(i)
>>>
(1, 4)
(2, 5)
(3, 6)
```

```python
#长度不等的列表, 以最短的列表相同

a = [1, 2, 3]
b = [4, 5, 6, 7, 8, 9]

zipped = zip(a, b)

for i in zipped:
    print(i)
>>> 
(1, 4)
(2, 5)
(3, 6)
```


```python
a = [1, 2, 3]
b = [4, 5, 6]

zipped = zip(a, b)
unzipped = zip(*zipped)  #加上*表示调用zip()函数,将打包结果解压
for i in unzipped:
    print(i)
>>>
(1, 2, 3)
(4, 5, 6)
```

#### 普通以及函数式编程对比
```python
# 普通编程方式
list = [2, -6, 11, -7, 8, 15, -14, -1, 10, -13, 18]
sum = 0
for i in range(len(list)):
    if list[i] > 0:
        sum += list[i]
print(sum)

#函数式编程方式
from functools import reduce
list1 = [2, -6, 11, -7, 8, 15, -14, -1, 10, -13, 18]
sum1 = filter(lambda x: x>0, list1)
s = reduce(lambda x, y: x+y, sum1)
print(s)
>>>
64
64
```

---
#### 闭包 
> * 闭包(closure) 指函数嵌套， 将函数内部的嵌套函数视为一个对象，可以将嵌套函数座位定义他的函数的返回结果
```python
def func_lib():
    def add(x, y):
        return x+y
    return add     #返回函数对象

fadd = func_lib()
print(fadd(1, 2))
>>>
3
```

---
#### 递归函数
> * 指直接或间接调用函数本身的函数
```python
#阶乘计算
def fact(n):
    if n == 1:
        return 1
    return n * fact(n - 1)

print(fact(5))
>>>
120
```

---
#### 迭代器 
> * 访问集合内元素的一种方式，从序列(列表，元组，字典，集合)的第一元素开始访问，直到所有元素都被访问一遍后结束。
> 迭代器对象 = iter(序列对象)
```python
list = [111, 222, 333]
it = iter(list)
print(next(it))
print(next(it))
print(next(it))
>>>
111
222
333
```

#### enumerate()
> * 将列表或元组生成一个有序号的序列
list = [111, 222, 333]
for i, v in enumerate(list):
    print(i, v)
>>>
0 111
1 222
2 333
```

---
#### 生成器(Generator)
> * 生成器包含一个yield语句，执行到yield语句时函数返回
> * 生成器函数可以记住上一次函数体的位置，对生成器函数的下一次调用跳转至改函数中间，而上次调用的所有局部变量都保持不变
```python
def addlist(alist):
    for i in alist:
        yield i + 1

alist = [1, 2, 3, 4]
for x in addlist(alist):
    print(x)
>>>
2
3
4
5
```






---
### I/O 编程

#### 输入数据
> 用户输入数据 = input(提示字符串)
```python
name = input('Please input your name: ')
print('###############')
print('Hello', name)
>>>
Rick
Hello Rick
```

---
#### 输出数据
> print(字符串常量或字符串变量)
> print('...%s...' % (string))

```python
for i in range(5):
    print(i)

# end="" 不换行
for i in range(5):
    print(i, end='')
>>>
0
1
2
3
4
01234
```

---
#### 文件操作
> * 打开文件 f = open(文件名， 访问模式，buffering)

|模式参数| 含义| 
|-|-|
|r |只读方式打开|
|w | 以写的方式打开，此时文件内容会被清空。文件不存在会创建新的文件|
|a | 以追加的模式打开，从文件末尾开始，必要时创建新文件|
|r+ | 以读写模式打开|
|w+ | 以读写模式打开|
|a+ | 以追加的读写模式打开|
|rb | 以二进制读模式打开|
|wb | 以二进制写模式打开|
|ab | 以二进制追加模式打开|
|rb+ | 以二进制读写模式打开|
|wb+ | 以二进制读写模式打开|
|ab+ | 以二进制读写模式打开|


> * buffering = 0	不缓冲
> * buffering = 1	缓冲一行数据
> * buffering > 1	使用给定值作为缓冲区大小



> * 关闭文件 f.close()


--- 
#### read() 方法
> * str = f.read([b])

```python
f = open('test.txt')
str = f.read()
f.close()
print(str)
>>>
Hello World
```

```python

pen('test.txt')
while True:
    chunk = f.read(2)  #读取两个字节到chunk
    if not chunk:
        break
    print(chunk)
f.close()
>>>
He
ll
o 
Wo
rl
d
```


---
#### readlines() 方法
> * list = f.readlines()  
> 读取文件的所有行
```python
f = open('test.txt')
list = f.readlines()
f.close()
print(list)
>>>
['Hello World']
```


---
#### readline()
> str = f.readline()
> 一次性读取文件中的所有行，使用readline()方法可以逐行读取文件内容
```python
f = open('test.txt')
while True:
    chunk = f.readline()
    if not chunk:
        break
    print(chunk)
f.close()
>>>
Hello World
```


---
#### in 关键字
> for line in 文件对象:
>     处理行数据line
```python
f = open('test.txt')
for line in f:
    print(line)
f.close()
>>>
Hello World
```


---
#### 写入文件
> f.write(写入文件内容)
```python
fname = input('Please input filename: ')
f = open(fname, 'w')
content = input("input something: ")
f.write(content)
f.close()
>>>
Please input filename: test_file
input something: Hello World
```

---
#### 追加写入
> * a 或a+参数调用open()方法
```python
fname = input('Please enter filename: ')
f = open(fname, 'w')
content = input("input something: ")
f.write(content)
f.close()
f = open(fname, 'a')
f.write("This is only for comments: ")
f.close()
```

---
#### writelines() 方法: 向文件中写入字符串序列
> f.writelines(seq)
```python
menulist = ['a', 'b', 'c', 'd']

fname = input("Please input name: ")

f = open(fname, 'w')

f.writelines(menulist)
f.close()
```




--- 
#### 文件指针
> 指向文件的指针变量，用于标识当前读写文件的位置。
> * tell() 方法获取文件指针位置
> 
```python
f = open('test.txt', 'w')

print(f.tell())
f.write('hello')
print(f.tell())
f.write('python')
print(f.tell())
f.close()       #关闭文件,将重新测试读取文件的指针位置
>>>
0
5	#因为加入了一个长度为5的字符串
11
```

> * 移动文件指针
> 
> seek() 方法手动移动文件指针位置
> 文件对象.seek((offset, where))
> offset: 移动偏移量，单位为字节。
> where: 指定何处开始移动
```python
f = open('test.txt', 'w+')
print(f.tell())
f.write('Hello')
print(f.tell())
f.seek(0, 0)    #指定文件指针开始位置
print(f.tell())
str = f.readline()
print(str)
f.close()
>>>
0
5
0
Hello
```


---
#### 截断文件
> 文件对象.truncate([size])
> size指定截取文件大小，单位为字节。
```python
f = open('test.txt', 'w')
f.write('Hello World')
f.truncate(5)
>>>
Hello		#test.txt文件内容只有Hello
```


---
#### 文件属性
> os 模块中的stat() 函数，可以获取文件时间属性
> 文件属性元组 = os.stat(文件路径)
```python
import os
filestatus = os.stat('test.txt')
print(filestatus)
>>>
os.stat_result(st_mode=33188, st_ino=8204874, st_dev=16777220, st_nlink=1, st_uid=1204811411, st_gid=254449427, st_size=5, st_atime=1475221440, st_mtime=1475221438, st_ctime=1475221438)
```

> * stat模块中的文件属性元组索引对应的常用常量

|索引|常量|
|-|-|
|0|stat.ST_MODE|
|6|stat.ST_SIZE|
|7|stat.ST_MTIME|
|8|stat.ST_ATIME|
|9|stat.ST_CTIME|

```python
import os, stat, time
filestatus = os.stat('test.txt')
print(filestatus[stat.ST_SIZE])
print(filestatus[stat.ST_MTIME])
print(filestatus[stat.ST_ATIME])
print(time.ctime(filestatus[stat.ST_CTIME]))
>>>
5
1475221438
1475221440
Fri Sep 30 15:43:58 2016
```


> * 复制文件  copy()
> copy(src, dst)
```python
import shutil
shutil.copy('/Users/xhxu/python/liaoxuefeng/test.txt', '/Users/xhxu/python/liaoxuefeng/test')
```

> * 移动文件
```python
import shutil
shutil.move('/Users/xhxu/python/liaoxuefeng/test.txt', '/Users/xhxu/python/liaoxuefeng/test')
```

> * 删除文件
```python
import os
os.move('/Users/xhxu/python/liaoxuefeng/test.txt')
```

> * 重命名
```python
import os
os.rename('/Users/xhxu/python/liaoxuefeng/test.txt', '/Users/xhxu/python/liaoxuefeng/test1.txt')
```

> * 获取当期目录
```python
import os
print(os.getcwd())
>>>
/Users/xhxu/python/liaoxuefeng
```

> * 获取目录内容
```python
import os
print(os.listdir('/Users/xhxu/python/liaoxuefeng'))
>>>
['.idea', '.python-version', '__pycache__', 'call_func.py', 'Decoration', 'do_iter.py', 'do_slice.py', 'foo.txt', 'func.py', 'Gdoc', 'hello world', 'hex.py', 'kw_args.py', 'login.py', 'Machine Learning', 'move.py', 'phone', 'practice', 'quadratic.py', 'recur.py', 'speedtest', 'support.py', 'test', 'test.py', 'test1.py', 'test1.txt', 'var_args.py']
```

> * 创建目录
```python
import os
print(os.mkdir('/Users/xhxu/python/liaoxuefeng/test1'))
```

> * 删除目录
```python
import os
print(os.rmdir('/Users/xhxu/python/liaoxuefeng/test1'))
```



---
### 图形化编程
> * python 提供了一些图形化模块，Tkinter, wxWidgets, easygui, wxpython

#### Tkinter 模块使用
```
In [2]: from tkinter.messagebox import *
In [4]: showinfo(title='test', message='welcome')
Out[4]: 'ok'

In [5]: showwarning(title='test', message='warning')
Out[5]: 'ok'

In [6]: showerror(title='test', message='Error')
Out[6]: 'ok'

```



--- 
### 多进程编程
> * 进程是正在运行的程序实例。
> * 每个进程至少包含一个线程，从主程序开始执行，直到退出程序；主线程结束，该进程也被从内存中卸载掉。
>
> * 进程一般如下组成
> 1. 与程序相关联的可执行代码的映像
> 2. 内存空间(通常是虚拟内存中的一些区域)， 其中保存可执行代码，进程的特定数据，用于记录活动例程和其他时间的调用栈(stack)，用于保存实时产生的中间结果的堆(heap)
> 3. 分配给进程的资源的操作系统描述符(比如文件句柄)以及其他数据资源
> 4. 安全属性，进程的所有者和权限
> 5. 处理器状态，寄存器的内容，物理内存地址等
> 
> * 操作系统在进程控制块(Process control block, PCB)的数据结构中保存活动进程的上述信息。



---
#### 进程编程
```
In [10]: import subprocess
In [11]: retcode = subprocess.call('/Applications/ShadowsocksX.app/Contents/MacOS/ShadowsocksX')	#调用可执行程序
[VERBOSE] GCDWebServer started on port 8090
[VERBOSE] Registered Bonjour service "webserver" with type '_http._tcp.' on port 8090
2016-09-30 16:37:05.757 ShadowsocksX[98086:7948318] Connecting accounts.google.com
2016-09-30 16:37:06.590 ShadowsocksX[98086:7948318] Connecting apis.google.com
2016-09-30 16:37:08.101 ShadowsocksX[98086:7948318] Connecting ssl.gstatic.com
2016-09-30 16:37:09.322 ShadowsocksX[98086:7948318] Connecting mail.google.com
2016-09-30 16:37:09.339 ShadowsocksX[98086:7948318] Connecting mail.google.com
2016-09-30 16:37:10.683 ShadowsocksX[98086:7948318] Connecting drive.google.com
```


> * subprocess.Popen() 函数
> 进程对象 = subprocess.Popen(args, bufsize=0, executable=None, stdin=None, stdout=None, stderr=None, preexec_fn=None, close_fds=False, shell=False, cwd=None, env=None, universal_newlines=False, startupinfo=None, creationflags=0)
> args, 可以是字符串或者序列类型(list, tuple), 用于指定进程可执行文件及其参数
> executable, 指定可执行程序。一般通过args指定所要运行的程序。如果将参数shell为True，则指定为shell。windows下，默认shell由COMSPEC环境变量来指定
> stdin, 默认为键盘
> stdout, 默认为屏幕
> stderr, 默认为屏幕
> preexec_fn, 只在Unix有效，用于指定一个可执行对象，将在子进程运行前被调用
> close_fds, windows下，若为True，新创建的子进程将不会继承父进程的输入，输出和错误管道。
> cwd, 指定进程的当前目录
> universal_newlines, 指定是否使用统一的文本换行符，在不同的操作系统下，文本的换行符不一样。windows为/r/n, Linux是/n
> startupinfo, windows下有效
> creationflags, windows 下有效

```
In [14]: import subprocess

In [15]: p = subprocess.Popen('ls', shell=True)		#执行ls命令

In [16]: Decoration		do_slice.py		login.py		speedtest		test1.txt
Gdoc			foo.txt			move.py			support.py		var_args.py
Machine Learning	func.py			phone			test
__pycache__		hello world		practice		test.py
call_func.py		hex.py			quadratic.py		test1
do_iter.py		kw_args.py		recur.py		test1.py


In [16]: p.wait()
Out[16]: 0
```


```python
import subprocess
import datetime

print(datetime.datetime.now())
p = subprocess.Popen('ping xurick.com ', shell=True)
print('processing')
p.wait()
print(datetime.datetime.now())
>>>
2016-09-30 16:55:59.156533
processing
PING xurick.com (192.30.252.153): 56 data bytes
64 bytes from 192.30.252.153: icmp_seq=0 ttl=48 time=556.738 ms
64 bytes from 192.30.252.153: icmp_seq=1 ttl=48 time=782.376 ms
64 bytes from 192.30.252.153: icmp_seq=2 ttl=48 time=700.090 ms
64 bytes from 192.30.252.153: icmp_seq=3 ttl=48 time=479.052 ms
64 bytes from 192.30.252.153: icmp_seq=4 ttl=48 time=669.792 ms
64 bytes from 192.30.252.153: icmp_seq=5 ttl=48 time=611.724 ms
```


> * CreateProcess 函数
> CreateProcess(appName, commandLine, processAttribute, TreadAttributes, bInheritHandles, dwCreationFlags, newEnvironment, currentDirectory, startupinfo)
> appName: 执行的程序名，包括路径和文件名，通常可以为Null
> processAttribute: 新进程的安全属性，如果为None，默认为安全属性
> ThreadAttribute: 线程安全属性，None表示默认安全属性
> bInheritHandles: 继承属性，None为默认继承属性
> dwCreationFlags: 指定附加，用来控制优先类和进程创建的标志。
> newEnvironment: 进程环境模块。Null为调用CreateProcess() 函数的进程环境
> startupinfo: 指定新进程的主窗口特性。


> * ctype库赋予了Python类似于C语言一样底层的操作能力。
```python
from ctypes.wintypes import * 
from ctypes import *
```


```python
#利用进程快照枚举当前Windows运行进程信息
from ctypes.wintypes import *
from ctypes import *


kernel32 = windll.kernel32
# 定义进程信息结构体
class tagPROCESSENTRY32(Structure):
    _fields = [('dwSize',           DWORD),
               ('cntUsage',         DWORD),
               ('th32ProcessID',    POINTER(ULONG)),
               ('th32ModuleID',     DWORD),
               ('cntThreads',       DWORD),
               ('th32ParentProcessID', DWORD),
               ('pcPriClassBase',   LONG),
               ('dwFlags',          DWORD),
               ('szExeFile',        c_char * 260)]

# 获取当前系统运行进程的快照
hSnapshot = kernel32.CreateToolhelp32Snapshot(15, 0)
fProcessEntry32 = tagPROCESSENTRY32()
# 初始化进程信息结构体的大小
fProcessEntry32.dwSize = sizeof(fProcessEntry32)

#获取第一个进程信息
listloop = kernel32.Process32First(hSnapshot, byref(fProcessEntry32))
while listloop: #若获取进程信息,则继续
    processName = (fProcessEntry32.szExeFile)
    processID = fProcessEntry32.th32ProcessID
    print('%d:%s' % (processID,processName))
    # 获取下一个进程信息
    listloop = kernel32.Process32Next(hSnapshot, byref(fProcessEntry32))
```



> * 终止进程
> 进程终止之后，会执行下面的操作
> 1. 进程中的所有线程都被标记为"终止"状态
> 2. 分配给进程的所有资源都会被释放掉
> 3. 所有与该进程相关的内核对象都会被关闭
> 4. 从内存中移除该进程的代码
> 5. 系统设置进程的退出代码
> 6. 将该进程对象设置为"受信"(Sigaled)状态
> 
> TASKKILL [/S system [/U username [/P [password]]]]
> 	{[/FI filter] [/PID processid] | [/IM imagename]} [/T] [/F]
> /S system	指定要连接的远程系统
> /U [domain\user] 	指定应该在哪个用户上下执行命令
> /P [password] 	为提供的用户上下文指定密码
> /FI filter		应用筛选器以选择一组任务。允许使用'*', 例如映像名称 eq acme*
> /PID	processid	指定要终止的进程PID
> /IM  imagename	指定要终止的进程映像名称，通配符'*' 可以用来指定所有任务或映像名称
> /T			指定的进程由它启用子进程
> /F 			强制终止进程






> * 进程池
> 进程池是管理进程的一种机制。程序同时运行多个进程时，可以使用进程池对进程进行管理和调度。
> 
> * multiprocessing包是Python中多进程管理包
> from multiprocessing import pool
> 进程池对象 = Pool(processes=n)
> 
> multiprocessing.Pool.apply_async(func[, args[, kwargs[, callback]]])
> func:	异步地执行函数名
> args 和 kwargs: func() 函数的参数
> callback: 可调用对象，接收输入参数。当func的结果变为可用时，将立即传递给callback
> 
> * 关闭进程池
> close() 函数会等进程池中的工作进程执行结束再关闭进程池
> terminate() 函数会直接关闭
> join() 函数可以等待进程池中的工作进程执行完毕，以防止主进程在工作进程结束前结束.
```
#进程池例子
```python
from multiprocessing import Pool
from time import sleep
import subprocess

def f(x):
    retcode = subprocess.call('/Applications/ShadowsocksX.app/Contents/MacOS/ShadowsocksX')
    sleep(1)

def main():
    pool = Pool(processes=3)    #最多工作进程数为3
    for i in range(1, 10):
        result = pool.apply_async(f, (i, ))
    pool.close()
    pool.join()
    if result.successful():
        print('Successful')


if __name__ == '__main__':
    main()
# 内建变量__name__通常为模块文件名。如果直接运行标准程序,则__name__的值等于'__main__'。本例中,只有__name__ == '__main__'时,
#  才会运行main()函数创建和使用进程池。而运行进程池中的工作进程时,则不会运行main() 函数
>>>
bind: Address already in use
2016-10-01 16:40:57.857 ShadowsocksX[2143:8138105] Could not bind
bind: Address already in use
2016-10-01 16:40:57.857 ShadowsocksX[2144:8138066] Could not bind
bind: Address already in use
2016-10-01 16:40:57.857 ShadowsocksX[2142:8138069] Could not bind
```


---
#### 多线程编程



 
