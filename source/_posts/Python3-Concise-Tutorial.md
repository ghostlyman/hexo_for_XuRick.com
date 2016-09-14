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

