---
title: Python Regular Expression
date: 2016-08-28 17:11:18
tags:
---

Reference to:
[runoob](http://www.runoob.com/python/python-reg-expressions.html)
[cnblogs](http://www.cnblogs.com/huxi/archive/2010/07/04/1771073.html)


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

> * 方法
> group([group1, ...]) 获得一个或多个分组的字符串，指定多个参数时将以元组形式返回。group1可以使用编号也可以使用别名。编号0表整个字符串，不写参数放回group(0), 没有截获字符串的组返回None，截获多次组返回最后一次字串。
> groups()  以元组的形式返回全部分组截获的字符串。相当于调用了group(1,2,...last),default表示没有截获字符串的组，默认为None。
> groupdict([default]) 返回以有别名的组的别名为键，以该组截获的字串值为字典，没有别名的组不包含在内
> start([group]) 返回指定的组截获的字串在string的起始索引，group默认值为0
> end([group])  返回指定的组截获的字串在string的结束索引， group默认值为0 
> span([group]) 返回(start(group), end(group))
> expand(template) 将匹配到分组代入template中后返回。

- e.g.
```python
import re
m = re.match(r'(\w+) (\w+)(?P<sign>.*)', 'hello world')
# \w 匹配包括下划线的任何单词字符， 字母或数字或下划线或汉字。
# 等价于「[A-Za-z0-9_]」。\b\w{6}\b 匹配刚好6个字符的单词。

print('m.string: ', m.string)
print('m.re: ', m.re)
print('m.pos: ', m.pos)
print('m.endpos: ',m.endpos)
print('m.lastindex: ', m.lastindex)
print('m.lastgroup: ', m.lastgroup)
print('m.group(1, 2): ', m.group(1, 2))
print('m.groups(): ', m.groups())
print('m.groupdict(): ', m.groupdict())
print('m.start(2): ', m.start(2))
print('m.end(2): ', m.end(2))
print('m.span(2): ', m.span(2))
print(r"m.expand(r'\2 \1\3'): ", m.expand(r'\2 \1\3'))

> 
m.string:  hello world
m.re:  re.compile('(\\w+) (\\w+)(?P<sign>.*)')
m.pos:  0
m.endpos:  11
m.lastindex:  3
m.lastgroup:  sign
m.group(1, 2):  ('hello', 'world')
m.groups():  ('hello', 'world', '')
m.groupdict():  {'sign': ''}
m.start(2):  6
m.end(2):  11
m.span(2):  (6, 11)
m.expand(r'\2 \1\3'):  world hello
```


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

#### Pattern
> * Pattern 对象是一个编译好的正则表达式，通过pattern提供的一系列方法对文本进行匹配查找
> * Pattern不能直接实例化，必须使用re.compile进行构造
> * Pattern提供一下可读属性获取表达式
> 1. pattern：编译时用的表达式字符串
> 2. flags：编译时用的匹配模式，数字形式
> 3. groups：表达式中分组的数量
> 4. groupindex：以表达式中有别名的组的别名为键，以该组对应的编号为值的字典，没有别名的组不包含在内

```python
import re
p = re.compile(r'(\w+) (\w+)(?P<sign>.*)', re.DOTALL)

print('p.pattern: ', p.pattern)
print('p.flags: ', p.flags)
print('p.groups: ', p.groups)
print('p.groupindex: ', p.groupindex)
>
p.pattern:  (\w+) (\w+)(?P<sign>.*)
p.flags:  48
p.groups:  3
p.groupindex:  {'sign': 3}
```


#### match
> match (string[, post[, endpos]]) | re.match(pattern, string[, flags])
> * 从string的pos下标开始匹配pattern；pattern结束时仍然可以匹配，返回match对象；无法匹配或匹配未结束就达到endpos，返回None
> pos默认值为0
> endpos默认值是len(string)
> re.match() 无法指定这两个参数,参数flags用于编译指定pattern的匹配模式

#### search
> search (string[, pos[, endpos]]) | re.search(pattern, string[, flags])
> * 用于查找字符串匹配成功的字串；pattern结束时仍然可以匹配，返回Match对象；无法匹配，将pos加1后尝试；直到pos=endpos 仍然无法匹配返回None
> post 默认值为0
> endpos 默认值为len(string)
> re.search() 无法指定这两个参数，参数flags用于编译指定pattern的匹配模式

```python
import re

pattern = re.compile(r'world') #将正则表达式编译成pattern对象

match = pattern.search('hello world')

if match:
    print(match.group()) #使用match获得分组信息
> 
world
```

#### split
> split(string[, maxsplit]) | re.split(pattern, string[, maxsplit])
> * 能够匹配字串将string 分割后返回列表。maxsplit用于指定最大分割次数，不指定将全部分割

```python
import re

p = re.compile(r'\d+')
print(p.split('one1two2three3four4'))
>
['one', 'two', 'three', 'four', '']
```

#### findall
> findall(string[, pos[, endpos]]) | re.findall(pattern, string[, flags]): 
> * 搜索string，以列表形式返回全部能匹配的子串。 

```python
import re

p = re.compile(r'\d+')
print(p.findall('one1two2three3four4'))
>
['1', '2', '3', '4']
```

#### finditer
> finditer(string[, pos[, endpos]]) | re.finditer(pattern, string[, flags]): 
> * 搜索string，返回一个顺序访问每一个匹配结果（Match对象）的迭代器。 

```python
import re
p = re.compile(r'\d+')

for m in p.finditer('one1two2three3four4'):
    print(m.group())
>
1
2
3
4
```

#### sub
> sub(repl, string[, count]) | re.sub(pattern, repl, string[, count]):
> * 使用repl替换string中每一个匹配的子串后返回替换后的字符串。 
> * 当repl是一个字符串时，可以使用\id或\g<id>、\g<name>引用分组，但不能使用编号0。 
> * 当repl是一个方法时，这个方法应当只接受一个参数（Match对象），并返回一个字符串用于替换（返回的字符串中不能再引用分组）。 
> * count用于指定最多替换次数，不指定时全部替换。 

```python
import re

p = re.compile(r'(\w+) (\w+)')
s = "I say, Hello World!"

print(p.sub(r'\2 \1', s))

def func(m):
    return m.group(1).title() + ' ' + m.group(2).title()

print(p.subn(func, s))
>
say I, World Hello!
('I Say, Hello World!', 2)
```

#### subn
> subn(repl, string[, count]) |re.sub(pattern, repl, string[, count]): 
> * 返回 (sub(repl, string[, count]), 替换次数)。 

```python
import re

p = re.compile(r'(\w+) (\w+)')
s = "I say, Hello World"

print(p.subn(r'\2 \1', s))

def func(m):
    return m.group(1).title() + ' ' + m.group(2).title()

print(p.subn(func, s))
>
('say I, World Hello', 2)
('I Say, Hello World', 2)
```


