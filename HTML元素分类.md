html中有一写些常用的基本html元素(Element), 如p, h1~h6, br, div, li, ul, img等.如果将这些元素细分, 又可以分别归为顶级(top-level)元素,块级(block-level)元素和内联(inline)元素.

**1. Top-level element 【顶级元素】:    { html, body, frameset }**

包括html, body, frameset, 表现如Block-level element, 属于高级块级元素.  

**2. Block-level element 【块级元素】:   { p, h1~h6, div, ul }**

顾名思义就是以块显示的元素，高度宽度都是可以设置的。比如我们常用的 p, h1~h6, div, ul 默认状态下都是属于块级元素。块级元素比较霸道，默认状态下每次都占据一整个行，后面的内容也必须再新起一行显示。当然非块级元素也可以通过css的`display:block`;将其更改成块级元素。此外还有个特殊的，float也具有此功能。块级元素能够独立存在, 一般的块级元素之间以换行(如一个段落结束后另起一行)分隔。块级元素是构成一个html的主要和关键元素, 而任意一个块级元素均可以用Box model来解释说明.

**3. Inline element 【内联元素】: { a, br, em, img, li, span }**

通俗点来说就是文本的显示方式，与块级元素相反，内联元素的高度宽度是不可以设置的，其宽度就是自身文字或者图片的宽度。我们常用到的`<a>`、`<span>`、`<em>`都属于内联元素。内联元素的显示特点就是像文本一样的显示，不会独自占据一个行。当然内联元素也能变成块级元素，那就是通过css的display:inline;和float来实现。内联元素依附其他块级元素存在, 紧接于被联元素之间显示, 而不换行.

​      在《CSS权威指南》这样定义到，“**任何不是块级元素的可见元素都是内联元素。**

#### 特点

block元素的特点：

总是另起一行开始；

高度，行高以及顶、底边距都可控制；

宽度缺省是它所在容器的100%，除非设定一个宽度。

 

inline元素的特点：

和其它元素都在一行上；

高度，行高以及顶、底边距不可改变；

宽度就是它所容纳的文字或图片的宽度，不可改变。



### 几种居中内联元素和块元素的方法

#### 一. 内联元素居中（文本text、图片img、按钮button等） 

给父元素设置text-align:center。 

给一个例子：使若干个元素（数量可变），在一行中居中显示，可用列表实现。我们知道列表中的\<li\>标签元素为块级元素，故可先将其display:inline，在一行中显示，然后将\<li\>的父元素，\<ul\>水平居中显示即可，代码如下：

```html
<!DOCTYPE html>
<html>
<head>
<title>test</title> 
 <style type="text/css">
    li{display: inline;}
    ul{text-align: center;}
 </style>
</head>
<body>
<ul>
    <li>1</li>
    <li>2</li>
    <li>3</li>
    <li>4</li>
</ul>
</body>
</html>
```

> **注意：**前提是子元素（即例子中的\<li\>）没有被设置浮动。

#### 二. 块级元素居中 

①定宽块级元素居中 
margin:0 auto; 
②不定宽块级元素居中 
总共有三种方法可解： 
Ⅰ.利用display:inline使块级元素内联显示； 
Ⅱ.利用\<table\>长度自适应的特性； 
Ⅲ.结合父元素，设置浮动和定位。 
方法Ⅰ详见以上 内联元素水平浮动 。 
方法Ⅱ：\<table\>是个盛放其他元素的块级容器，其宽度不默认父元素的宽，而是随其中文本长度决定，因此可看作一个定宽块级元素。 
给需要水平浮动的元素设定display:table或放入\<table\>标签中，即可使用margin:0 auto像定宽块级元素一样居中显示了。代码如下： 

```html
<!DOCTYPE html>
<html>
<head>
    <title>test</title>

 <style type="text/css">
 table{margin: 0 auto;}
 </style>
</head>
<body>
<table>
<tr>
<td>
<p>这是一个不定宽的块级元素,增删其中文字后仍然居中</p>
</td>
</tr>
</table>
</body>
</html>
```

display:table;

```html
<!DOCTYPE html>
<html>
<head>
    <title>test</title>
 <style type="text/css">
 p{display: table;margin: 0 auto;}
 </style>
</head>
<body>
<p>这是一个不定宽的块级元素,增删其中文字后仍然居中</p>

</body>
</html>
```

方法Ⅲ：利用相对定位，使父元素相对于body向右偏移50%，再使需要居中的元素相对于父元素向左偏移50%，为了防止高度塌陷**设置浮动前一定要给父元素清除浮动**。为了更直观的看到两div位置，给父元素加了黑色边框，子元素加了红色边框，代码如下：

```html
<!DOCTYPE html>
<html>
<head>
    <title>test</title>

 <style type="text/css">
 #father{
    position: relative;
    clear:both;
    float: left;
    left: 50%;
    border: 1px solid black;
 }
 #child{
    position: relative;
    float: left;
    left: -50%;
    border: 1px solid red;
 }
 </style>
</head>
<body>
<div id="father">
    <div id="child">
        这是一个不定宽的块级元素,增删其中文字后仍然居中
    </div>
</div>
</body>
</html>
```

> 父元素position:absolute，子元素保持相对定位也可以实现水平居中， 
> 因为绝对定位使父元素脱离了文档流



