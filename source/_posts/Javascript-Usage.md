---
title: Javascript Usage
date: 2016-10-28 18:08:10
tags: [Javascript]
---

Reference to 
[liaoxuefeng](http://www.liaoxuefeng.com)

<!-- more -->

## Javascript 入门

> * 1. JavaScript代码可以直接嵌在网页的任何地方，不过通常我们都把JavaScript代码放到<head>中

```javascript
<html>
<head>
  <script>
    alert('Hello, world');
  </script>
</head>
<body>
  ...
</body>
</html>
```

> * 2. 第二种方法是把JavaScript代码放到一个单独的.js文件，然后在HTML中通过<script src="..."></script>引入这个文件：
```javascript
<html>
<head>
  <script src="/static/js/abc.js"></script>
</head>
<body>
  ...
</body>
</html>
```

