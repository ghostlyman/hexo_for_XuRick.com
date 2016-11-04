---
title: Python-Fast-Tutorial 
date: 2016-11-04 20:02:32
tags: [python]
---

Reference to:
[shiyanlou](https://www.shiyanlou.com/courses/214/labs/648/document)

<!-- more -->


[TOC]
# Python 


## 1. Python 基础上

### 基本数据类型

> 
变量	数据类型
a=10	int 整数
a=1.3	float 浮点数
a=True	真值(True/False)
a='Hello!'	字符串

### 序列
> * 序列有两种
> 1. tuple 元组 (各个元素不可变)
> 2. list 列表 (各个元素可以再变)

--- 

> * 元素引用
```
In [1]: s = [1, [3, 4, 5]]
In [3]: s[0]
Out[3]: 1

In [4]: s[1]
Out[4]: [3, 4, 5]
In [6]: s[1][2]
Out[6]: 5
```

--- 

> * 其他引用方式
[下限:上限:步长]
```
In [11]: s = [1, 2, 3, 4, 5, 6]

In [12]: s[:5]
Out[12]: [1, 2, 3, 4, 5]

In [13]: s[2:]
Out[13]: [3, 4, 5, 6]

In [14]: s[0:5:2]
Out[14]: [1, 3, 5]

In [15]: s[-1]
Out[15]: 6

In [16]: s[-3]
Out[16]: 4
```
---

> * 字符串是元组
```
In [17]: str = 'abcdefg'

In [18]: str[2:4]
Out[18]: 'cd'
```

---

### 运算 

#### 数学运算
```
In [19]: 1+9
Out[19]: 10

In [20]: 1.4-3
Out[20]: -1.6

In [21]: 4*7
Out[21]: 28

In [22]: 4.5/1.5
Out[22]: 3.0

In [23]: 2**8
Out[23]: 256

In [24]: 10%3
Out[24]: 1

In [25]: 10//3
Out[25]: 3
```
---

#### 判断
```
In [26]: 5 == 6
Out[26]: False

In [27]: 8.0 != 8.0
Out[27]: False

In [28]: 3<3, 3<=3
Out[28]: (False, True)

In [29]: 4>5, 4>=0
Out[29]: (False, True)

In [30]: 4 in [1, 2, 4]
Out[30]: True
```

---

#### 逻辑运算
```
In [31]: True and True, True and False
Out[31]: (True, False)

In [32]: True or False
Out[32]: True

In [33]: not True
Out[33]: False
```
---

### 缩进和选择

#### python 一般使用4个空格进行缩进

---

* if 语句
```
In [34]: i = 1

In [35]: x = 1

In [36]: if i > 0:
   ....:     x = x +1
   ....:     

In [37]: x
Out[37]: 2
```
```
i = 1
if i > 0:
    print('positive 1')
    i += 1
elif i == 0:
    print('i is 0')
    i *= 10
else:
    print('negative 1')
    i -= 1

print('New i: ', i)
>>>
positive 1
New i:  2
```
--- 

## 2. Python 基础下

---
### 循环

#### for 循环

```
for a in [3, 4, 4, 'life']:
    print(a)
>>> 
3
4
4 
life
```
```
for a in range(10):
    print(a, end='')
>>>
0123456789
```
---


#### while 循环
while会不停地循环执行隶属于它的语句，直到条件为假(False)。
```
i = 0
while i < 10:
    print(i, end='')
    i += 1
>>>
0123456789
```
--- 

#### 中断循环
##### continue 
continue 在循环的某一次执行中，如果遇到continue, 那么跳过这一次执行，进行下一次的操作

```
for i in range(10):
    if i == 2:
        continue
    print(i, end='')
>>>
013456789
```

##### break 
break 停止执行整个循环
```
for i in range(10):
    if i == 2:
        continue
    print(i, end='')
>>>
013456789
```
---

### 函数
```
def square_sum(a,b):
    c = a**2 + b**2
    return c
```
* 首先，def，这个关键字通知python：我在定义一个函数。square_sum是函数名。

* 括号中的a, b是函数的参数，是对函数的输入。参数可以有多个，也可以完全没有（但括号要保留）。

* return c 表示返回c的值，也可以不会返回

* return 可以返回多个值，使用逗号分开， 相当于返回一个tuple(定值表)

* 在Python中，当程序执行到return的时候，程序将停止执行函数内余下的语句。return并不是必须的，当没有return, 或者return后面没有返回值时，函数将自动返回None。None是Python中的一个特别的数据类型，用来表示什么都没有，相当于C中的NULL。None多用于关键字参数传递的默认值

---
#### 函数调用和参数传递

##### 函数调用
* 整数变量传递给函数
对于基本数据类型的变量，变量传递给函数后，函数会在内存中复制一个新的变量，从而不影响原来的变量。（我们称此为值传递）
```
a = 1
def change_integer(a):
    a += 1
    return a

print(change_integer(a))
print(a)
>>>
2
1
```
---

* 表传递给函数
对于表来说，表传递给函数的是一个指针，指针指向序列在内存中的位置，在函数中对表的操作将在原有内存中进行，从而影响原有变量。 （我们称此为指针传递）
```
b = [1, 2, 3]
def change_list(b):
    b[0] = b[0] + 1
    return b

print(change_list(b))
print(b)
>>>
[2, 2, 3]
[2, 2, 3]
```

---

### 面向对象的基本概念

* Python使用类(class)和对象(object)，进行面向对象（object-oriented programming，简称OOP）的编程

---
#### 面向对象动作
* python 通过在类的内部定义函数，来说明方法，这些行为属性称为方法method
```
class Bird(object):
    owned_feature = True
    producting_ability = 'egg'

    def move(self, dx, dy):
        position = [0, 0]
        position[0] = position[0] + dx
        position[1] = position[1] + dy
        return position

summer = Bird()   # 对象实例化
print('After moving: ', summer.move(5, 8))
>>>
After moving:  [5, 8]
```

---

#### 子类
* 在OOP中，我们通过继承(inheritance)来表达上述概念, 面向对象提高了程序的可重复使用性。

* 在类定义时，括号里为了Bird。这说明，Chicken是属于鸟类（Bird）的一个子类，即Chicken继承自Bird。自然而然，Bird就是Chicken的父类。Chicken将享有Bird的所有属性。尽管我只声明了summer是鸡类，它通过继承享有了父类的属性（无论是变量属性have_feather还是方法属性move）

* 新定义的黄鹂(Oriole)类，同样继承自鸟类。在创建一个黄鹂对象时，该对象自动拥有鸟类的属性。
```
class Bird(object):
    owned_feature = True
    producting_ability = 'egg'

    def move(self, dx, dy):
        position = [0, 0]
        position[0] = position[0] + dx
        position[1] = position[1] + dy
        return position


class Chicken(Bird):
    moving_method = 'walk'
    destiny_in_KFC = True

class Oriole(Bird):
    moving_method = 'fly'
    destiny_in_KFC = False

summer = Chicken()
print(summer.owned_feature)
print(summer.move(5, 8))
>>>
True
[5, 8]
```
--- 

#### 调用类的其它信息
* 使用self，调用类属性

* 在对象中对类属性进行赋值的时候，实际上会在对象定义的作用域中添加一个属性（如果还不存在的话），并不会影响到相应类中定义的同名类属性。但如果是修改类属性的内容（比如类属性是个字典，修改字典内容）时会影响到所有对象实例，因为这个类属性的内容是共享的。
```
class Human(object):
    laugh = 'hahaha'
    def show_laugh(self):
        print(self.laugh)
    def laugh_10th(self):
        for i in range(10):
            self.show_laugh()

Rick_Xu = Human()
Rick_Xu.laugh_10th()
>>>
hahaha
hahaha
hahaha
hahaha
hahaha
hahaha
hahaha
hahaha
hahaha
hahaha
```

---

#### __init__() 方法
* __init__() 是一个特殊方法(special method)。Python有一些特殊方法。Python会特殊的对待它们。特殊方法的特点是名字前后有两个下划线。

* 如果你在类中定义了__init__() 这个方法，创建对象时，Python会自动调用这个方法。这个过程也叫初始化。
```
class Bird(object):
    owned_features = True

class HappyBird(Bird):
    def __init__(self, more_words):
        print('We are the happy birds.', more_words)

summer = HappyBird('Happy, Happy!')
>>>
We are the happy birds. Happy, Happy!
```

---

#### 对象的性质
* 当定义类的方法时，必须要传递一个self的参数。这个参数指代的就是类的一个对象。我们可以通过操纵self，来修改某个对象的性质。
* self会传递给各个方法。在方法内部，可以通过引用self.attribute，查询或修改对象的性质。
```
class Human(object):
    def __init__(self, input_gender):
        self.gender = input_gender
    def print_gender(self):
        print(self.gender)

Rick_Xu = Human('male')  #male作为参数传递给__init__()方法的input_gender变量

print(Rick_Xu.gender) #gender不是一个类属性, 这里专门存储了对象的特有信息
Rick_Xu.print_gender()
>>>
male
male
```

---

#### 内置函数

##### dir()
* dir()用来查询一个类或者对象所有属性。
```
In [45]: print(dir())
['In', 'Out', '_', '_12', '_13', '_14', '_15', '_16', '_18', '_19', '_20', '_21', '_22', '_23', '_24', '_25', '_26', '_27', '_28', '_29', '_3', '_30', '_31', '_32', '_33', '_37', '_38', '_4', '_40', '_42', '_6', '_8', '_9', '__', '___', '__builtin__', '__builtins__', '__doc__', '__loader__', '__name__', '__package__', '__spec__', '_dh', '_i', '_i1', '_i10', '_i11', '_i12', '_i13', '_i14', '_i15', '_i16', '_i17', '_i18', '_i19', '_i2', '_i20', '_i21', '_i22', '_i23', '_i24', '_i25', '_i26', '_i27', '_i28', '_i29', '_i3', '_i30', '_i31', '_i32', '_i33', '_i34', '_i35', '_i36', '_i37', '_i38', '_i39', '_i4', '_i40', '_i41', '_i42', '_i43', '_i44', '_i45', '_i5', '_i6', '_i7', '_i8', '_i9', '_ih', '_ii', '_iii', '_oh', '_sh', 'exit', 'get_ipython', 'i', 'quit', 's', 'str', 'x']
```

--- 

##### help()

* help()用来查询的说明文档
```
In [46]: print(help())

Welcome to Python 3.4's help utility!

If this is your first time using Python, you should definitely check out
the tutorial on the Internet at http://docs.python.org/3.4/tutorial/.

Enter the name of any module, keyword, or topic to get help on writing
Python programs and using Python modules.  To quit this help utility and
return to the interpreter, just type "quit".

To get a list of available modules, keywords, symbols, or topics, type
"modules", "keywords", "symbols", or "topics".  Each module also comes
with a one-line summary of what it does; to list the modules whose name
or summary contain a given string such as "spam", type "modules spam".

help> 
```

---

#### list是一个类
```
In [47]: nl = [1, 2, 5, 3, 5]

In [48]: nl.count(5) #计数多少个5
Out[48]: 2

In [49]: nl.index(3) #nl的第一个3的下标
Out[49]: 3

In [50]: nl.append(6)

In [51]: nl
Out[51]: [1, 2, 5, 3, 5, 6]

In [52]: nl.sort()

In [53]: nl
Out[53]: [1, 2, 3, 5, 5, 6]

In [54]: nl.pop() #去除最后一个元素，并将该元素返回
Out[54]: 6

In [55]: nl
Out[55]: [1, 2, 3, 5, 5]

In [56]: nl.remove(2)

In [57]: nl
Out[57]: [1, 3, 5, 5]

In [58]: nl.insert(0, 9) #在下标0的位置插入9

In [59]: nl
Out[59]: [9, 1, 3, 5, 5]
```

---

#### 运算符是特殊方法
* dir() 方法可以看到一个特殊方法
```
In [63]: nl = [1, 2, 3]

In [64]: print(dir(nl))
['__add__', '__class__', '__contains__', '__delattr__', '__delitem__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__getitem__', '__gt__', '__hash__', '__iadd__', '__imul__', '__init__', '__iter__', '__le__', '__len__', '__lt__', '__mul__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__reversed__', '__rmul__', '__setattr__', '__setitem__', '__sizeof__', '__str__', '__subclasshook__', 'append', 'clear', 'copy', 'count', 'extend', 'index', 'insert', 'pop', 'remove', 'reverse', 'sort']
```
* 这里的__add__是个特殊方法， 如下例子
```
In [65]: [1,2,3] + [5,6,9]
Out[65]: [1, 2, 3, 5, 6, 9]

In [66]: [1,2,3] - [3,4]
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-66-cd77356b97fd> in <module>()
----> 1 [1,2,3] - [3,4]

TypeError: unsupported operand type(s) for -: 'list' and 'list'
```

* 运算符，比如+, -, >, <, 以及下标引用[start:end]等等，从根本上都是定义在类内部的方法。

* 下面我们继承list类，添加对 - 的定义
```
class super_list(list):
    def __sub__(self, b): #内置函数__sub__()定义了-的操作
        a = self[:] #这里, self是super_list的对象。由于super_list继承于list, 利用和list[:]相同的引用方法来表示整个对象
        b = b[:]
        while len(b) > 0:
            element_b = b.pop()
            if element_b in a:
                a.remove(element_b)
        return a

print(super_list([1, 2, 3]) - super_list([3, 4]))
>>>
[1, 2]
```

