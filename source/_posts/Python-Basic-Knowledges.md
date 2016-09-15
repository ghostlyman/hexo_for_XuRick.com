---
title: Python Basic Knowledges
date: 2016-08-30 14:54:59
tags:
---

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

> * time.strftime() 可以按照指定的格式输出struct_time时间
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
> 
Hello World
3
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
