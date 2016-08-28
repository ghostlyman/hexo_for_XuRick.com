---
title: Python Regular Expression
date: 2016-08-28 17:11:18
tags:
---

Reference to:
[runoob](http://www.runoob.com/python/python-reg-expressions.html)


## Python 正则表达式

### re.compile 函数

> re.compile(strPattern[, flag])
- strPattern 这个是pattern类的工厂方法，用于将字符串形式的正则表达式编译为pattern对象。
- flag 匹配模式，取值可以使用按位或运算符'|' 表示同时生效
- re.compile('pattern', re.I|re.M) 与re.compile('(?im)pattern')是等价的


### flags 可选标志
|Flags| Description|
|-|-|
|re.I| (re.IGNORECASE) 忽略大小写|
|re.L| (re.LOCALE) 对本地化识别(locale-aware) 匹配,使预定字符\w \W \b \B \s \S 取决于当前区域设定|
|re.M| (re.MULTILINE) 多行匹配，影响^ 和$|
|re.S| (re.DOTALL) 使.匹配包括换行在内的所有字符，改变.行为|
|re.U| (re.UNICODE) 根据Unicode字符集解析字符属性，影响\w \W \b \B \s \S \d \D|
|re.X| (re.VERBOSE) 详细模式，忽略空白字符可以加上注释|
```
a = re.compile(r'''\d +
                   \.
                   \d *''', re.X)
#等价于
a = re.compile(r'\d+\.|d*')
```




### re.match 函数
匹配从字符串的其实位置匹配模式，若默认不是起始位置匹配成功的话，match() 就返回None

> re.match(pattern, string, flags=0)
- pattern	匹配的正则表达式
- string	要匹配的字符串
- flags		标志位，用于控制表达式方式，是否区分大小写等

> group(num=0) 匹配整个表达式的字符串
> groups()  一次可以输入多个组号，返回一个包含所有小组字符串的远足，从1到所含的小组号


- e.g. 
```python
import re
print(re.match('xurick', 'www.xurick.com')) #不在起始位置匹配

> 
None
```

- e.g. 
```python
import re

line = 'welcome to XuRick.com'

matchOBJ = re.match(r'(.*) to (.*?).*', line, re.M|re.I)

if matchOBJ:
    print('matchOBJ.group(): ', matchOBJ.group())
    print('matchOBJ.group(1): ', matchOBJ.group(1))
    print('matchOBJ.group(2): ', matchOBJ.group(2))
else:
    print('No match!')

>
matchOBJ.group():  welcome to XuRick.com
matchOBJ.group(1):  welcome
matchOBJ.group(2): 
```


### re.search 函数
扫描整个字符串并返回第一个成功的匹配

> re.search(pattern, string, flags=0)
- pattern 匹配的正则表达式
- string 要匹配的字符串
- flags 标志位，用于控制表达式方式，是否区分大小写等

> group(num=0) 匹配整个表达式的字符串
> groups()  一次可以输入多个组号，返回一个包含所有小组字符串的远足，从1到所含的小组号

- e.g.

```python
import re
print(re.search('xurick', 'www.xurick.com').span())  #在起始位置匹配
print(re.search('com', 'www.xurick.com').span())    #不在起始位置匹配

> 
(4, 10)
(11, 14)
```

- e.g. 

```python
import re

line = 'welcome to XuRick.com'

searchOBJ = re.search(r'(.*) to (.*?).*', line, re.M|re.I)

if searchOBJ:
    print('searchOBJ.group(): ', searchOBJ.group())
    print('searchOBJ.group(1): ', searchOBJ.group(1))
    print('searchOBJ.group(2): ', searchOBJ.group(2))
else:
    print('No search!')

> 
searchOBJ.group():  welcome to XuRick.com
searchOBJ.group(1):  welcome
searchOBJ.group(2):  
```

#### re.match 与re.search区别
- e.g. 

```python
import re

line = 'Welcome to XuRick.com'

matchOBJ = re.match(r'XuRick', line, re.M | re.I)
if matchOBJ:
    print('match -> matchOBJ.group(): ', matchOBJ.group())
else:
    print('No match!')

searchOBJ = re.search(r'XuRick', line, re.M | re.I)
if searchOBJ:
    print('search -> searchOBJ.group(): ', searchOBJ.group())
else:
    print('No search!')

> 
No match!
search -> searchOBJ.group():  XuRick
```

### re.sub 函数
替换字符串中的匹配项

> re.sub(patttern, repl, string, max=0)
- 返回的字符串是在字符串中用RE最左边不重复的匹配来替换。如果模式没有发现，字符将被没有改变的返回
- 可选参数count 是模式匹配后替换的最大次数；count必须是非负整数；缺省值是0表示替换左右匹配

```python
import re
date = '2016-08-28' # The date of today

# Deleting Python-style comments
date1 = re.sub(r'#.*$', '', date)
print('Date1 of today: ', date1)

# Removing anything other than digits
date2 = re.sub(r'\D', '', date)    #\D 表示匹配一个非数字字符。等价于[^0-9]。
print('Date2 of today: ', date2)

>
Date1 of today:  2016-08-28
Date2 of today:  20160828
```


