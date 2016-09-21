---
title: SVG-Usage
date: 2016-09-19 20:35:40
tags:
---

Reference to 
[w3school.com.cn](http://www.w3school.com.cn/svg/svg_example.asp)

## SVG简介
> * SVG (Scalable Vector Graphics) 可缩放矢量图形
> * 使用XML格式定义图像
> * SVG 图像子啊放大和改变尺寸的情况下图形质量不会有所损失


---
## SVG 实例

```
<?xml version="1.0" standalone="no"?>

<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" 
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg width="100%" height="100%" version="1.1"
xmlns="http://www.w3.org/2000/svg">

<circle cx="100" cy="50" r="40" stroke="black"
stroke-width="2" fill="red"/>

</svg>
```
> 1. 第一行包含了 XML 声明。请注意 standalone 属性！该属性规定此 SVG 文件是否是“独立的”，或含有对外部文件的引用。
standalone="no" 意味着 SVG 文档会引用一个外部文件 - 在这里，是 DTD 文件。
> 2. 第二和第三行引用了这个外部的 SVG DTD。该 DTD 位于 “http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd”。该 DTD 位于 W3C，含有所有允许的 SVG 元素。
> 3. SVG 代码以 <svg> 元素开始，包括开启标签 <svg> 和关闭标签 </svg> 。这是根元素。width 和 height 属性可设置此 SVG 文档的宽度和高度。version 属性可定义所使用的 SVG 版本，xmlns 属性可定义 SVG 命名空间。
> 4. SVG 的 <circle> 用来创建一个圆。cx 和 cy 属性定义圆中心的 x 和 y 坐标。如果忽略这两个属性，那么圆点会被设置为 (0, 0)。r 属性定义圆的半径。
> 5. stroke 和 stroke-width 属性控制如何显示形状的轮廓。我们把圆的轮廓设置为 2px 宽，黑边框。
fill 属性设置形状内的颜色。我们把填充颜色设置为红色。
> 6. 关闭标签的作用是关闭 SVG 元素和文档本身。
> 7. 注释：所有的开启标签必须有关闭标签！



---
## SVG 嵌入 HTML
> * <embed> 标签
> <embed> 标签被所有主流的浏览器支持，并允许使用脚本。

```
# 语法
<embed src="rect.svg" width="300" height="100" 
type="image/svg+xml"
pluginspage="http://www.adobe.com/svg/viewer/install/" /> 	#pluginspage 属性指向下载插件的 URL。
```

> * <object> 标签
> <object> 标签是 HTML 4 的标准标签，被所有较新的浏览器支持。它的缺点是不允许使用脚本。

```
<object data="rect.svg" width="300" height="100" 
type="image/svg+xml"
codebase="http://www.adobe.com/svg/viewer/install/" />		# codebase 属性指向下载插件的 URL。
```


> * <iframe> 标签
> <iframe> 标签可工作在大部分的浏览器中。

```
<iframe src="rect.svg" width="300" height="100">
</iframe>
```


---
## SVG 形状

### 矩形<rect>

```
<?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" 
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg width="100%" height="100%" version="1.1"
xmlns="http://www.w3.org/2000/svg">

<rect width="300" height="100"			# rect 元素的 width 和 height 属性可定义矩形的高度和宽度
style="fill:rgb(0,0,255);stroke-width:1;	# style 属性用来定义 CSS 属性, CSS的fill定义颜色， stroke-width定义宽度
stroke:rgb(0,0,0)"/>				# stroke定义矩形边框颜色

</svg>
```


```
<?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" 
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg width="100%" height="100%" version="1.1"		#
xmlns="http://www.w3.org/2000/svg">

<rect x="20" y="20" width="250" height="250"		# x定义矩形左侧位置（例如，x="0" 定义矩形到浏览器窗口左侧的距离是 0px），y为顶端位置(例如，y="0" 定义矩形到浏览器窗口顶端的距离是 0px)
style="fill:blue;stroke:pink;stroke-width:5;		
fill-opacity:0.1;stroke-opacity:0.9"/>			# CSS的fill-opacity 定义透明度(0-1取值)， stroke-opacity 属性定义笔触颜色的透明度（0-1取值）

</svg>
```


```
#带有圆角的矩形
<?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" 
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg width="100%" height="100%" version="1.1"
xmlns="http://www.w3.org/2000/svg">

<rect x="20" y="20" rx="20" ry="20" width="250"   	#rx和ry定义矩形产生的圆角
height="100" style="fill:red;stroke:black;
stroke-width:5;opacity:0.5"/>

</svg>
```

---
### 圆形 <circle>

```
<?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" 
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg width="100%" height="100%" version="1.1"
xmlns="http://www.w3.org/2000/svg">

<circle cx="100" cy="50" r="40" stroke="black" 		#cx和cy定义圆点的x和y坐标，省略cx和cy，圆中心会被设置成(0, 0),    r定义园的半径
stroke-width="2" fill="red"/>

</svg>
```

---
### 椭圆 <ellipse>

```
<?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" 
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg width="100%" height="100%" version="1.1"
xmlns="http://www.w3.org/2000/svg">

<ellipse cx="300" cy="150" rx="200" ry="80"	# cx 定义圆点x坐标，cy定义圆点y坐标，rx定义水平半径，ry定义垂直半径
style="fill:rgb(200,100,50);
stroke:rgb(0,0,100);stroke-width:2"/>

</svg>
```

```
<?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" 
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg width="100%" height="100%" version="1.1"
xmlns="http://www.w3.org/2000/svg">

<ellipse cx="240" cy="100" rx="220" ry="30"
style="fill:yellow"/>				#黄色椭圆

<ellipse cx="220" cy="100" rx="190" ry="20"
style="fill:white"/>				#白色椭圆

</svg>
```


---
### <line> 标签创建线条

```
<?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" 
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg width="100%" height="100%" version="1.1"
xmlns="http://www.w3.org/2000/svg">

<line x1="0" y1="0" x2="300" y2="300"		#x1 定义x轴线条开始， y1定义y轴线条开始， x2定义x轴线条结束，y2定义y轴线条结束
style="stroke:rgb(99,99,99);stroke-width:2"/>

</svg>
```

---
### <polygon> 创建不少于三个边的图形

```
<?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" 
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg width="100%" height="100%" version="1.1"
xmlns="http://www.w3.org/2000/svg">

<polygon points="220,100 300,210 170,250"	#points属性定义多边形每个角的x和y坐标
style="fill:#cccccc;
stroke:#000000;stroke-width:1"/>

</svg>
```

```
<?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" 
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg width="100%" height="100%" version="1.1"
xmlns="http://www.w3.org/2000/svg">

<polygon points="220,100 300,210 170,250 123,234"	#四边形
style="fill:#cccccc;
stroke:#000000;stroke-width:1"/>

</svg>
```


---
### <polyline> 创建仅包含直线的形状

```
<?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" 
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg width="100%" height="100%" version="1.1"
xmlns="http://www.w3.org/2000/svg">

<polyline points="0,0 0,20 20,20 20,40 40,40 40,60"	#仅包含直线的形状
style="fill:white;stroke:red;stroke-width:2"/>

</svg>
```


---
### <path> 表示路径
> 路径数据
> * M = moveto
> * L = lineto
> * H  = horizontal lineto
> * V = vertical lineto
> * C = curveto
> * S = smooth curveto
> * Q = quadratic belzier curveto
> * T = smooth quadratic Belzier curveto
> * A = elliptical Arc
> * Z = closepath

```
<?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" 
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg width="100%" height="100%" version="1.1"
xmlns="http://www.w3.org/2000/svg">

<path d="M250 150 L150 350 L350 350 Z" />   		#路径开始于250 150，到达150 350， 然后从那里开始到350 350， 最后在250 150 闭合路径

</svg>
```


```
<?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" 
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg width="100%" height="100%" version="1.1"
xmlns="http://www.w3.org/2000/svg">

<path d="M153 334					#螺旋路径
C153 334 151 334 151 334
C151 339 153 344 156 344
C164 344 171 339 171 334
C171 322 164 314 156 314
C142 314 131 322 131 334
C131 350 142 364 156 364
C175 364 191 350 191 334
C191 311 175 294 156 294
C131 294 111 311 111 334
C111 361 131 384 156 384
C186 384 211 361 211 334
C211 300 186 274 156 274"
style="fill:white;stroke:red;stroke-width:2"/>

</svg>
```



---
### SVG 滤镜
> * 滤镜用来向形状和文本添加特殊的效果
> 
> SVG 可使用的滤镜有
> * feBlend
> * feColorMatrix
> * feComponentTransfer
> * feComposite
> * feConvolveMatrix
> * feDiffuseLighting
> * feDisplacementMap
> * feFlood
> * feGaussianBlur
> * feImage
> * feMerge
> * feMorphology
> * feOffset
> * feSpecularLighting
> * feTile
> * feTurbulence
> * feDistantLight
> * fePointLight
> * feSpotLight



---
### 高斯模糊(Gaussian Blur)
> 必须在<defs> 标签中定义SVG滤镜
> 
> * <filter> 标签用来定义SVG滤镜,  <filter> 标签使用必须的id属性来定义向图形应用具体哪个滤镜
> * <filter> 标签必须嵌套在<defs>, 标签内。他允许诸如滤镜等特殊元素进行定义

```
<?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" 
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg width="100%" height="100%" version="1.1"
xmlns="http://www.w3.org/2000/svg">

<defs>
<filter id="Gaussian_Blur">				#id属性可为滤镜定义一个唯一的名称（同一滤镜可被文档中的多个元素使用）
<feGaussianBlur in="SourceGraphic" stdDeviation="3" />	#滤镜效果是通过 <feGaussianBlur> 标签进行定义的。fe 后缀可用于所有的滤镜 <feGaussianBlur> 标签的 stdDeviation 属性可定义模糊的程度;   in="SourceGraphic" 这个部分定义了由整个图像创建效果
</filter>
</defs>

<ellipse cx="200" cy="150" rx="70" ry="40"
style="fill:#ff0000;stroke:#000000;
stroke-width:2;filter:url(#Gaussian_Blur)"/>

</svg>
```


```
<?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" 
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg width="100%" height="100%" version="1.1"
xmlns="http://www.w3.org/2000/svg">

<defs>
<filter id="Gaussian_Blur">
<feGaussianBlur in="SourceGraphic" stdDeviation="20"/>		#stdDeviation 值不同,效果也不相同
</filter>
</defs>

<ellipse cx="200" cy="150" rx="70" ry="40"
style="fill:#ff0000;stroke:#000000;
stroke-width:2;filter:url(#Gaussian_Blur)"/>

</svg>
```



---
### SVG 线性渐变
> * SVG 渐变必须在<defs>标签中定义
> * 渐变是从一种颜色到另一种颜色平滑过渡。另外，可以把多个颜色的过渡应用到同一个元素上。
> 
> * 线性渐变
> * <linearGradient> 可以定义SVG的线性渐变
> * <linearGradient> 标签必须嵌套在 <defs> 的内部。<defs> 标签是 definitions 的缩写，它可对诸如渐变之类的特殊元素进行定义。
> 
> 线性渐变可被定义为水平、垂直或角形的渐变：
> 当 y1 和 y2 相等，而 x1 和 x2 不同时，可创建水平渐变
> 当 x1 和 x2 相等，而 y1 和 y2 不同时，可创建垂直渐变
> 当 x1 和 x2 不同，且 y1 和 y2 不同时，可创建角形渐变


```
<?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" 
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg width="100%" height="100%" version="1.1"
xmlns="http://www.w3.org/2000/svg">

<defs>
<linearGradient id="orange_red" x1="0%" y1="0%" x2="100%" y2="0%">	#<linearGradient> 标签的 id 属性可为渐变定义一个唯一的名称;   <linearGradient> 标签的 x1、x2、y1、y2 属性可定义渐变的开始和结束位置
<stop offset="0%" style="stop-color:rgb(255,255,0);			#渐变的颜色范围可由两种或多种颜色组成。每种颜色通过一个 <stop> 标签来规定。offset 属性用来定义渐变的开始和结束位置
stop-opacity:1"/>
<stop offset="100%" style="stop-color:rgb(255,0,0);
stop-opacity:1"/>
</linearGradient>
</defs>

<ellipse cx="200" cy="190" rx="85" ry="55"
style="fill:url(#orange_red)"/>						#fill:url(#orange_red) 属性把 ellipse 元素链接到此渐变

</svg>
```


```
# 垂直渐变
<?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" 
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg width="100%" height="100%" version="1.1"
xmlns="http://www.w3.org/2000/svg">

<defs>
<linearGradient id="orange_red" x1="0%" y1="0%" x2="0%" y2="100%">
<stop offset="0%" style="stop-color:rgb(255,255,0);
stop-opacity:1"/>
<stop offset="100%" style="stop-color:rgb(255,0,0);
stop-opacity:1"/>
</linearGradient>
</defs>

<ellipse cx="200" cy="190" rx="85" ry="55"
style="fill:url(#orange_red)"/>

</svg>
```

---
### 放射性渐变
> * <radialGradient> 用来定义放射性渐变。
> * <radialGradient> 标签必须嵌套在 <defs> 中。<defs> 标签是 definitions 的缩写，它允许对诸如渐变等特殊元素进行定义。

```
<?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" 
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg width="100%" height="100%" version="1.1"
xmlns="http://www.w3.org/2000/svg">

<defs>
<radialGradient id="grey_blue" cx="50%" cy="50%" r="50%"		#<radialGradient> 标签的 id 属性可为渐变定义一个唯一的名称; cx、cy 和 r 属性定义外圈，而 fx 和 fy 定义内圈 渐变的颜色范围可由两种或多种颜色组成。
fx="50%" fy="50%">
<stop offset="0%" style="stop-color:rgb(200,200,200);
stop-opacity:0"/>
<stop offset="100%" style="stop-color:rgb(0,0,255);			#每种颜色通过一个 <stop> 标签来规定。offset 属性用来定义渐变的开始和结束位置。
stop-opacity:1"/>
</radialGradient>
</defs>

<ellipse cx="230" cy="200" rx="110" ry="100"
style="fill:url(#grey_blue)"/>						#fill:url(#grey_blue) 属性把 ellipse 元素链接到此渐变

</svg>
```



```
#另一个例子
<?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" 
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg width="100%" height="100%" version="1.1"
xmlns="http://www.w3.org/2000/svg">

<defs>
<radialGradient id="grey_blue" cx="20%" cy="40%" r="50%"
fx="50%" fy="50%">
<stop offset="0%" style="stop-color:rgb(200,200,200);
stop-opacity:0"/>
<stop offset="100%" style="stop-color:rgb(0,0,255);
stop-opacity:1"/>
</radialGradient>
</defs>

<ellipse cx="230" cy="200" rx="110" ry="100"
style="fill:url(#grey_blue)"/>

</svg>
```


```
#红色警报闪烁
<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
	<rect x="20" y="20" width="250" height="250">
		<animate attributeType="CSS" attributeName="fill" from="#f00" to="#ffd2d2" dur="600ms" repeatCount="indefinite" />
	</rect>
	<text font-family="microsoft yahei" font-size="40" y="100" x="160" text-anchor="middle" fill="#b90000">警报！</text>
</svg>
```

```
#蓝色渐变
<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
  <rect x="20" y="20" width="250" height="250" style="fill:blue">
    <animate attributeType="CSS" attributeName="opacity" from="1" to="0" dur="5s" repeatCount="indefinite" />
  </rect>
</svg>
```



---
### SVG 元素


|元素|描述|
|-|-|
|a|定义超链接|
|altGlyph| 允许对象性文字进行控制，来呈现特殊的字符数据（例如，音乐符号或亚洲的文字）|
|altGlyphDef 定义一系列象性符号的替换（例如，音乐符号或者亚洲文字）|
|altGlyphItem| 定义一系列候选的象性符号的替换|
|animate |随时间动态改变属性|
|animateColor| 规定随时间进行的颜色转换|
|animateMotion|使元素沿着动作路径移动|
|animateTransform| 对元素进行动态的属性转换|
|circle|定义圆|
|clipPath||
|color-profile|规定颜色配置描述|
|cursor|定义独立于平台的光标|
|definition-src|定义单独的字体定义源|
|defs| 被引用元素的容器|
|desc| 对 SVG 中的元素的纯文本描述 - 并不作为图形的一部分来显示。用户代理会将其显示为工具提示。|
|ellipse |定义椭圆|
|feBlend |SVG 滤镜。使用不同的混合模式把两个对象合成在一起。|
|feColorMatrix|SVG 滤镜。应用matrix转换。|
|feComponentTransfer |SVG 滤镜。执行数据的 component-wise 重映射。|
|feComposite |SVG 滤镜。|
|feConvolveMatrix| SVG 滤镜。|
|feDiffuseLighting|SVG 滤镜。|
|feDisplacementMap|SVG 滤镜。|
|feDistantLight|SVG 滤镜。 Defines a light source|
|feFlood |SVG 滤镜。|
|feFuncA |SVG 滤镜。feComponentTransfer 的子元素。|
|feFuncB |SVG 滤镜。feComponentTransfer 的子元素。|
|feFuncG |SVG 滤镜。feComponentTransfer 的子元素。|
|feFuncR |SVG 滤镜。feComponentTransfer 的子元素。|
|feGaussianBlur|SVG 滤镜。对图像执行高斯模糊。|
|feImage |SVG 滤镜。|
|feMerge |SVG 滤镜。创建累积而上的图像。|
|feMergeNode |SVG 滤镜。feMerge的子元素。|
|feMorphology| SVG 滤镜。 对源图形执行"fattening" 或者 "thinning"。|
|feOffset| SVG 滤镜。相对与图形的当前位置来移动图像。|
|fePointLight| SVG 滤镜。|
|feSpecularLighting|SVG 滤镜。|
|feSpotLight |SVG 滤镜。|
|feTile|SVG 滤镜。|
|feTurbulence| SVG 滤镜。|
|filter|滤镜效果的容器。|
|font| 定义字体。|
|font-face|描述某字体的特点。|
|font-face-format||
|font-face-name||
|font-face-src| |
|font-face-uri| |
|foreignObject| |
|g|用于把相关元素进行组合的容器元素。|
|glyph|为给定的象形符号定义图形。|
|glyphRef| 定义要使用的可能的象形符号。|
|hkern| |
|image| |
|line| 定义线条。|
|linearGradient|定义线性渐变。|
|marker||
|mask||
|metadata| 规定元数据。|
|missing-glyph| |
|mpath| |
|path| 定义路径。|
|pattern||
|polygon 定义由一系列连接的直线组成的封闭形状。|
|polyline| 定义一系列连接的直线。|
|radialGradient|定义放射形的渐变。|
|rect| 定义矩形。|
|script|脚本容器。（例如ECMAScript）|
|set |为指定持续时间的属性设置值|
|stop||
|style|可使样式表直接嵌入SVG内容内部。|
|svg |定义SVG文档片断。|
|switch||
|symbol||
|text||
|textPath||
|title|对 SVG 中的元素的纯文本描述 - 并不作为图形的一部分来显示。用户代理会将其显示为工具提示。|
|tref||
|tspan| |
|use||
|view||
|vkern||




---
## svgwrite 模块

