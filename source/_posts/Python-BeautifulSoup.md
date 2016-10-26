---
title: Python-BeautifulSoup
date: 2016-09-12 20:30:53
tags: [Python]
---

### Reference to
[iteye.com](http://cndenis.iteye.com/blog/1746706)

<!-- more -->
---
## 简介
BeautifulSoup，美好的汤，是一个用于解析HTML文件的Python库。主页在http://www.crummy.com/software/BeautifulSoup/ 

---
### Making the Soup 装汤
* 将需要解析的HTML装入BeautifulSoup
```python
from bs4 import BeautifulSoup

fp = open('index.html')

soup1 = BeautifulSoup(fp)
soup2 = BeautifulSoup('<html>data</html>')
```
---
### Soup中的对象
> #### tag 标签 
> * 标签对应HTML元素，也就是HTML标签以及括起来的内容（包括内层标签和文本）
```python
soup = BeautifulSoup('<b class="boldest">Extremely bold</b>')

tag = soup.b  #soup.b就是一个标签, soup也可以视为一个标签
```
---
> #### name 名字
> * 名字对应HTML标签中的名字（也就是尖括号的第一项）， 每一个标签都具有名字，标签的名字使用.name 访问 
```python
tag.name == u'b'

soup.name == u'[document]'
```
---
> #### Attribute 属性
> * 属性对应HTML标签中的属性部分（也就是尖括号里带等号的那些）。
> * 标签可以有许多属性，也可以没有属性。
> * 属性使用类似于字典的形式访问，用方括号加上属性名
```python
tag['class'] == u'boldest'
tag.attrs == {u'class', u'boldest'}  #.attrs可以直接获得字典
```
---
> #### Text 文本
> * 文本对应HTML中的文本（也就是尖括号外的部分）
> * 使用.text 访问
```python
tag.tex == u'Extremely bold'
```

---
### Soup中的查找 - 找汤料
> #### find() 和findAll 方法
> * find只返回找到的第一个标签，而find_all则返回一个列表。
> * 因为查找用得很多，所以BeautifulSoup做了一些很方便的简化的使用方式：
    
    tag.find_all("a")  #等价于 tag("a")
    tag.find("a") #等价于 tag.a
> * 因为找不到的话，find_all返回空列表，find返回None，而不会抛出异常，所以，也不用担心  tag("a") 或 tag.a 会因为找不到而报错。
> * 限于python的语法对变量名的规定，tag.a 的形式只能是按名字查找，因为点号.后面只能接变量名，而带括号的形式  tag() 或 tag.find() 则可用于以下的各种查找方式
> 
> 1. 字符串： 字符串会匹配标签的名字，例如 tag.a 或 tag("a")
> 2. 列表： 可以按一个字符串列表查找，返回名字匹配任意一个字符串的标签。例如 tag("h2", "p")
> 3. 键-值： 可以用tag(key=value)的形式，来按标签的属性查找。键-值查找小技巧
    * class是Python的保留字，不能当变量名用，偏偏在HTML中会有很多  class=XXX 的情况，BeautifulSoup的解决方法是加一下划线，用 class_ 代替,如  tag(class_=XXX)
    * 当值为True时，会匹配所有带这个键的标签，如 tag(href=True)
    * text做为键时表示查找按标签中的文本查找，如  tag(text=something）
> 4. 正则表达式： 例如 tag(href=re.compile("elsie"))
> 5. 函数： 当以上方法都行不通时，函数是终极方法。写一个以单个标签为参数的函数，传入 find 或find_all 进行查找。如
```python
def fun(tag):
    return tag.has_key("class") and not tag.has_key("id")
tag(fun) # 会返回所有带class属性但不带id属性的标签
```
---
### 按文档结构查找
> * HTML可以解析成一棵标签树，因此也可以按标签在树中的相互关系来查找。
> * 查找上层节点：find_parents() 和 find_parent()
> * 查找下一个兄弟节点：find_next_siblings() 和  find_next_sibling()
> * 查找上一个兄弟节点：find_previous_siblings() 和  find_previous_sibling()
> * 以上四个都只会查同一父节点下的兄弟
> * 查找下层节点：其实上面说的find和find_all就是干这活的
> * 查找下一个节点（无视父子兄弟关系） find_all_next() 和  find_next()
> * 查找上一个节点（无视父子兄弟关系） find_all_previous() 和 find_previous()

---
### 按照CSS查找
> 用 .select()方法，看 http://www.crummy.com/software/BeautifulSoup/bs4/doc/#css-selectors

---
### 小技巧
> * BeautifulSoup 可以支持多种解析器，如lxml, html5lib, html.parser. 如：BeautifulSoup("<a></b>", "html.parser")
具体表现可参考 http://www.crummy.com/software/BeautifulSoup/bs4/doc/#differences-between-parsers
> * BeautifulSoup 在解析之前会先把文本转换成unicode，可以用 from_encoding 指定编码，如：BeautifulSoup(markup, from_encoding="iso-8859-8")
> * soup.prettify()可以输出排列得很好看的HTML文本，遇上中文的话可以指定编码使其显示正常，如 soup.prettify("gbk")
还是有编码问题，看：http://www.crummy.com/software/BeautifulSoup/bs4/doc/#unicode-dammit

