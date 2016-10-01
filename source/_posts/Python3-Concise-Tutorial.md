---
title: Python3 Concise Tutorial
date: 2016-09-14 14:32:34
tags:
---

Reference to 
[shiyanlou](https://www.shiyanlou.com/courses/596)

---
## 循环

```python
# 斐波那契（Fibonacci）数列

a, b = 0, 1

while b < 20:
    b += a
    print(b)
    a, b = b, a
> 
1
1
2
3
5
8
13
21
34
```





```python
# 计算幂级数：e^x = 1 + x + x^2 / 2! + x^3 / 3! + ... + x^n / n! （0 < x < 1）

x = float(input("Enter the value of x: "))
n = term = num = 1

sum = 1.0

while n <= 100:
    term *= x/n
    sum += term
    n += 1
    if term < 0.0001:
        break
        
print("No of times = {} and Sum = {}".format(n, sum))
> 
Enter the value of x: 7
No of times = 26 and Sum = 1096.6331271341257
```



```python
# 9*9 乘法表

i = 1
print("-" * 45)

while i < 10:
    n = 1
    while n < 10:
        print("{:4d}".format(i*n), end=' ')
        n += 1
    print()
    i += 1

print("-" * 45)
>
---------------------------------------------
   1    2    3    4    5    6    7    8    9 
   2    4    6    8   10   12   14   16   18 
   3    6    9   12   15   18   21   24   27 
   4    8   12   16   20   24   28   32   36 
   5   10   15   20   25   30   35   40   45 
   6   12   18   24   30   36   42   48   54 
   7   14   21   28   35   42   49   56   63 
   8   16   24   32   40   48   56   64   72 
   9   18   27   36   45   54   63   72   81 
---------------------------------------------
```



> * 切片
```
 +---+-----+-----+---------+----------+
 | 1 | 342 | 223 | 'India' | 'Fedora' |
 +---+-----+-----+---------+----------+
 0   1     2     3         4          5
-6  -5    -4    -3        -2         -1
```

> 列表也支持连接这样的操作，它返回一个新的列表
```
In [12]: a = [1, 32, 49, 'China', 'Linux']

In [13]: a + [1, 3, 4, 5]
Out[13]: [1, 32, 49, 'China', 'Linux', 1, 3, 4, 5]
```


> 列表嵌套
```
In [14]: a = ['a', 'b', 'c']

In [15]: n = [1, 2, 3]

In [16]: x = [a, n]

In [17]: x
Out[17]: [['a', 'b', 'c'], [1, 2, 3]]
```


> continue。它会跳过其后的代码回到循环开始处执行。
```python
while True:
    n = int(input("Please input Integer: "))
    if n < 0:
        continue #返回循环体开始出执行
    elif n==0:
        break
    print("Square of it is: ", n ** 2)
print("Good Bye")
> 
Please input Integer: -1
Please input Integer: 1
Square of it is:  1
Please input Integer: 0
Good Bye
```



---
## 数据结构

> * 列表
> append 
> insert
> count (返回元素数量)
> remove (移除任意值)
> reverse (翻转列表)
> extend (将元素添加到另一个列表末尾)
> sort 
> del

> * 栈
> 栈是我们通常所说的一种 LIFO （Last In First Out 后进先出）数据结构。
```
In [22]: a = [1, 2, 3, 4, 5]

In [23]: a
Out[23]: [1, 2, 3, 4, 5]

In [24]: a.pop()
Out[24]: 5

In [25]: a.pop()
Out[25]: 4

In [26]: a
Out[26]: [1, 2, 3]

In [28]: a.append(23)

In [29]: a
Out[29]: [1, 2, 3, 23]
```

> * 队列
>  队列 是一种在末尾追加数据以及在开始弹出数据的数据结构。
```
In [30]: a = [1, 2, 3, 4, 5]

In [31]: a.append(1)

In [32]: a
Out[32]: [1, 2, 3, 4, 5, 1]

In [33]: a.pop(0)
Out[33]: 1

In [34]: a.pop(0)
Out[34]: 2

In [35]: a
Out[35]: [3, 4, 5, 1]
```

> * 列表推导式
```
In [2]: squares = [x**2 for x in range(10)]

In [3]: squares
Out[3]: [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]



In [4]: [(x, y) for x in [1, 2, 3] for y in [3, 1, 4] if x != y]
Out[4]: [(1, 3), (1, 4), (2, 3), (2, 1), (2, 4), (3, 1), (3, 4)]
等同于
combs = [ ]
for x in [1, 2, 3]:
    for y in [3, 1, 4]:
        if x != y:
            combs.append((x, y))

combs

#列表推导式嵌套
In [8]: z = [x + 1 for x in [x ** 2 for x in [1, 2, 3]]]

In [9]: z
Out[9]: [2, 5, 10]

```



> * 元组
```
#元组拆分
In [10]: divmod(15, 2)
Out[10]: (7, 1)

In [11]: x, y = divmod(15, 2)

In [12]: x
Out[12]: 7

In [13]: y
Out[13]: 1

#元组不可变
In [14]: a = (1, 2, 3)

In [15]: del a[0]
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-15-cc06cab42bbe> in <module>()
----> 1 del a[0]

TypeError: 'tuple' object doesn't support item deletion
```




> * 集合
> 集合是一个无序不重复元素的集，其对象支持union, intersection， difference， symmetric difference 

```
# 使用set() 创建空集合
In [16]: a = set()

In [17]: a
Out[17]: set()



#集合操作
In [18]: a = set('abcdefgh')

In [19]: b = set('abcd')

In [20]: a - b
Out[20]: {'e', 'f', 'g', 'h'}

In [21]: a | b
Out[21]: {'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h'}

In [22]: a & b
Out[22]: {'a', 'b', 'c', 'd'}

In [23]: a ^ b
Out[23]: {'e', 'f', 'g', 'h'}

#添加删除元素
In [24]: a.pop()
Out[24]: 'a'

In [25]: a.add('a')

In [26]: a
Out[26]: {'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h'}
```


> * 字典 
> 字典是无序的键值集合
```
In [28]: data = {'name': 'Rick'}

In [29]: data
Out[29]: {'name': 'Rick'}

In [30]: data['name']
Out[30]: 'Rick'

In [31]: data['age'] = '27'

In [32]: data
Out[32]: {'age': '27', 'name': 'Rick'}

In [33]: del data['age']

In [34]: data

In [35]: 'job' in data
Out[35]: False


# dict() 可以从包含键值对的元组中创建字典
In [37]: dict((('Name', 'Rick'),('Age', '27')))
Out[37]: {'Age': '27', 'Name': 'Rick'}

In [38]: d = dict((('Name', 'Rick'),('Age', '27')))

# 遍历字典
In [39]: d
Out[39]: {'Age': '27', 'Name': 'Rick'}

In [40]: for x, y in d.items():
   ....:     print(x, y)
   ....:     
Age 27
Name Rick

# 使用 dict.setdefault(key, default) 往字典中的元素添加数据 
In [41]: data = {}

In [42]: data.setdefault('Name', []).append('Rick')

In [43]: data
Out[43]: {'Name': ['Rick']}

In [44]: data.setdefault('Name', []).append('Xu')

In [45]: data
Out[45]: {'Name': ['Rick', 'Xu']}


# 使用 dict.get(key, default) 来索引键，如果键不存在，那么返回指定的 default 值。
In [46]: data['foo']
---------------------------------------------------------------------------
KeyError                                  Traceback (most recent call last)
<ipython-input-46-b084002d0227> in <module>()
----> 1 data['foo']

KeyError: 'foo'

In [47]: data.get('foo', 0)
Out[47]: 0



#使用 enumerate()  遍历列表（或任何序列类型）的同时获得元素索引值
In [48]: for x, y in enumerate(['a', 'b', 'c']):
   ....:     print(x, y)
   ....:     
0 a
1 b
2 c


#同时遍历两个序列类型，你可以使用 zip() 函数
In [50]: a = ['Name', 'Rick']

In [51]: b = ['Age', '27']

In [52]: for x, y in zip(a, b):
   ....:     print(x, y)
   ....:     
Name Age
Rick 27
```



> 计算两个矩阵的乘积，要求输入矩阵的行/列数（在这里假设我们使用的是 n × n 的矩阵
```python

n = int(input('Enter the value of n: '))
print("Enter the Matrix A")
a = []
for i in range(n):
    a.append([int(x) for x in input().split()])
print("Enter the Matrix B")
b = []
for i in range(n):
    b.append([int(x) for x in input().split()])

c = []
for i in range(n):
    c.append([a[i][j] * b[j][i] for j in range(n)])
print("After Matrix multiplicated")

print('-' * 7 * n)
for x in c:
    for y in x:
        print(str(y).rjust(5), end=' ')
    print()
print('-' * 7 * n)
>>>
Enter the value of n: 3
Enter the Matrix A
9 8 7
6 5 4 
3 2 1
Enter the Matrix B
1 2 3 
4 5 6
7 8 9
After Matrix multiplicated
---------------------
    9    32    49 
   12    25    32 
    9    12     9 
---------------------
```



---
## 字符串
> * 如果你想要分几行输入字符串，并且希望行尾的换行符自动包含到字符串当中，可以使用三对引号："""...""" 或 '''...'''

```
In [55]: s = 'rick xu'

In [56]: s.title()
Out[56]: 'Rick Xu'

In [57]: s.upper()
Out[57]: 'RICK XU'

In [59]: s.swapcase()
Out[59]: 'RICK XU'

In [60]: s = 'rickxu 1989'

In [61]: s.isalnum()
Out[61]: False

In [62]: s = '1989'

In [63]: s.isalnum()
Out[63]: True

In [66]: s = 'rick xu'

In [67]: s.islower()
Out[67]: True

In [68]: s.istitle()
Out[68]: False

In [69]: s.isupper()
Out[69]: False

# split()
In [70]: s = 'I am learning Python'

In [71]: s.split()
Out[71]: ['I', 'am', 'learning', 'Python']

In [72]: s.split(' ')
Out[72]: ['I', 'am', 'learning', 'Python']

In [73]: s = 'Rick:Xu'

In [74]: s.split(':')
Out[74]: ['Rick', 'Xu']

```



> * 字符串剥离
> 用来剥离字符串首尾中指定的字符，它允许有一个字符串参数，这个参数为剥离哪些字符提供依据。不指定参数则默认剥离掉首尾的空格和换行符
```
In [77]: s = 'www.xurick.com'

#左剥离
In [79]: s.lstrip('www.')
Out[79]: 'xurick.com'

#右剥离
In [80]: s.rstrip('.com')
Out[80]: 'www.xurick'
```

> * 文本搜索
```
In [82]: s = 'www.xurick.com'
#会告知字符串位置
In [83]: s.find('xurick')
Out[83]: 4

In [85]: s.startswith('xu')
Out[85]: False

In [86]: s.endswith('com')
Out[86]: True
```

> * 回文 palindrome : 回文是一种无论从左还是从右读都一样的字符序列
```
s = input('Please enter a string: ')

z = s[::-1]

if s == z:
    print("This is a palindrome")
else:
    print("This is not a palindrome")
```



---
## 函数

> * 同一个程序里多次复用代码。函数可以很好的帮助我们完成这一点
```
def palindrome(s):
    return s == s[::-1]

if __name__ == '__main__':
    s = input("Enter a String: ")
    if palindrome(s):
        print("It's a Palindrome")
    else:
        print("It isnt a Palindorme")
>>>
Enter a String: abab
It isnt a Palindorme
```

> * 局域或全局变量
```
def change():
    a = 90
    print(a)

a = 9
print("Before called function", a)
print("Inside function", end=' ')
change()
print("After called function", a)
>>>
Before called function 9
Inside function 90
After called function 9
```

> * global 告知a的定义是全局的
```
def change():
    global a
    a = 90
    print(a)

a = 9
print("Before called function", a)
print("Inside function", end=' ')
change()
print("After called function", a)
>>>
Before called function 9
Inside function 90
After called function 90
```


> * 默认参数值
> 函数的参数变量可以有默认值，也就是说如果我们对指定的参数变量没有给出任何值则会赋其默认值
```
#有默认值的参数后面不能再有普通参数，比如 f(a,b=90,c) 就是错误的
In [91]: def test(a, b=-99):
   ....:     if a>b:
   ....:         return True
   ....:     else:
   ....:         return False
   ....:     

In [92]: test(12, 34)
Out[92]: False

In [93]: test(12)
Out[93]: True
```

```
# 默认值只被赋值一次，因此如果默认值是任何可变对象时会有所不同，比如列表、字典或大多数类的实例。例如，下面的函数在后续调用过程中会累积（前面）传给它的参数
```

In [94]: def f(a, data=[]):
   ....:     data.append(a)
   ....:     return data
   ....: 

In [95]: print(f(1))
[1]

In [96]: print(f(2))
[1, 2]

In [97]: print(f(3))
[1, 2, 3]

#或者
In [99]: def f(a, data=None):
   ....:     if data is None:
   ....:         data=[]
   ....:     data.append(a)
   ....:     return data
   ....: 

In [100]: print(f(1))
[1]

In [101]: print(f(2))
[2]
```

> * 关键字参数
```
In [102]: def func(a, b=5, c=10):
   .....:     print(a, b, c)
   .....:     

In [103]: func(12, 24)
12 24 10

In [104]: func(12, c=24)
12 5 24

In [105]: func(b=12, a=-1, c=8)
-1 12 8
```



> * 强制关键字参数
> 将函数的参数标记为只允许使用关键字参数。用户调用函数时将只能对每一个参数使用相应的关键字参数。
```
In [106]: def hello(*, name='User'):
   .....:     print('Hello', name)
   .....:     

In [107]: hello('Rick')
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-107-20937ca36d34> in <module>()
----> 1 hello('Rick')

TypeError: hello() takes 0 positional arguments but 1 was given

In [108]: hello(name='Rick')
Hello Rick
```

> * 文档字符串
> （docstrings）来说明如何使用代码，这在交互模式非常有用，也能用于自动创建文档。
```python
import math
def longest_side(a, b):
    """
    Function to find the length of the longest side of a right triangle.

    :arg a: Side a of the triangle
    :arg b: Side b of the triangle

    :return: Length of the longest side c as float
    """
    return math.sqrt(a*a + b*b)

if __name__ == '__main__':
    print(longest_side.__doc__)
    print(longest_side(4,5))
>>>

    Function to find the length of the longest side of a right triangle.

    :arg a: Side a of the triangle
    :arg b: Side b of the triangle

    :return: Length of the longest side c as float
    
6.4031242374328485
```


> * 高阶函数（Higher-order function）或仿函数（functor）是内部至少含有一个以下步骤的函数：
> 使用一个或多个函数作为参数
> 返回另一个函数作为输出
```
In [109]: def high(func, value):
   .....:     return func(value)
   .....: 

In [110]: lst = high(dir, int)

In [111]: print(lst[-3:])
['numerator', 'real', 'to_bytes']
```


> * map 函数
> map 是一个在 Python 里非常有用的高阶函数。它接受一个函数和一个序列（迭代器）作为输入，然后对序列（迭代器）的每一个值应用这个函数，返回一个序列（迭代器），其包含应用函数后的结果
```
In [112]: lst = [1, 2, 3, 4]

In [113]: def square(num):
   .....:     return num * num
   .....: 

In [114]: map(square, lst)
Out[114]: <map at 0x1026b3400>

In [115]: list(map(square, lst))
Out[115]: [1, 4, 9, 16]
```


---
## 文件处理

> * open()
> 
> * close()
> 始终确保你显式关闭每个打开的文件，一旦它的工作完成你没有任何理由保持打开文件。因为程序能打开的文件数量是有上限的。如果你超出了这个限制，没有任何可靠的方法恢复，因此程序可能会崩溃。

> read() 方法一次性读取整个文件
```python
f = open('/Users/xhxu/python/liaoxuefeng/test.txt')
a = f.read()
print(a)
>>>
Hello
```

> * readline() 能帮助你每次读取文件的一行。
> * readlines() 方法读取所有行到一个列表中。
```python
f = open('/Users/xhxu/python/liaoxuefeng/test.txt')
a = f.readlines()
print(a)
>>>
['Hello\n', 'World']
```


> * copy文本到指定的一个文本文件
```python
#!/bin/env python

import sys

if len(sys.argv) < 3:
   print("Wrong parameters")
   print('./copyfile.py file1 file2')
   sys.exit(1)

f1 = open(sys.argv[1])
s = f1.read()
f1.close()
f2 = open(sys.argv[2], 'w')
f2.write(s)
f2.close()
>>>
python copyfile.py test.txt test1.txt
$ cat test1.txt
$ Hello
```


> * 文本文件相关信息统计
```python
import os
import sys

def parse_file(path):
    """
       分析给定文本文件，返回其空格、制表符、行的相关信息

       :arg path: 要分析的文本文件的路径

       :return: 包含空格数、制表符数、行数的元组
    """
    fd = open(path)
    i = 0
    space = 0
    tabs = 0
    for i, line in enumerate(fd):
        space += line.count(' ')
        tabs += line.count('\t')
    fd.close()
    # 以元组的形式返回结果
    return space, tabs, i+1

def main(path):
    """
    函数用于打印文件分析结果

    :arg path: 要分析的文本文件的路径
    :return: 若文件存在则为 True，否则 False
    """
    if os.path.exists(path):
        spaces, tabs, lines = parse_file(path)
        print("Space {}, tabs {}, lines {}".format(spaces, tabs, lines))
        return True
    else:
        return False

if __name__ == '__main__':
    if len(sys.argv) > 1:
        main(sys.argv[1])
    else:
        sys.exit(-1)
    sys.exit(0)
>>>
python parsefile.py test.txt
Space 0, tabs 0, lines 2
```


> * with 语句
> with 语句处理文件对象，它会文件用完后会自动关闭，就算发生异常也没关系
```
In [1]: with open('test.txt') as f:
   ...:     for i in f:
   ...:         print(i, end='')
   ...:         
Hello
World
```

