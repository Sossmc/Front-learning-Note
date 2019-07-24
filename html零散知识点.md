### meta标签

meta是html语言head区的一个辅助性标签。也许你认为这些代码可有可无。其实如果你能够用好meta标签，会给你带来意想不到的效果，meta标签的作用有：搜索引擎优化（SEO），定义页面使用语言，自动刷新并指向新的页面，实现网页转换时的动态效果，控制页面缓冲，网页定级评价，控制网页显示的窗口等！ 

meta标签的组成：meta标签共有两个属性，它们分别是http-equiv属性和name属性，不同的属性又有不同的参数值，这些不同的参数值就实现了不同的网页功能。 

#### 1、name属性

name属性主要用于描述网页，与之对应的属性值为content，content中的内容主要是便于搜索引擎机器人查找信息和分类信息用的。 

meta标签的name属性语法格式是： 

<metaname="参数"content="具体的参数值">。 

其中name属性主要有以下几种参数：　 

A、Keywords(关键字)　 

说明：keywords用来告诉搜索引擎你网页的关键字是什么。 

举例：<metaname="keywords"content="science,education,culture,politics,ecnomics，relationships,entertaiment,human"> 

B、description(网站内容描述) 

说明：description用来告诉搜索引擎你的网站主要内容。 

举例：<metaname="description"content="Thispageisaboutthemeaningofscience,education,culture."> 

C、robots(机器人向导) 

说明：robots用来告诉搜索机器人哪些页面需要索引，哪些页面不需要索引。 

content的参数有all,none,index,noindex,follow,nofollow。默认是all。 

举例：<metaname="robots"content="none"> 

D、author(作者) 

说明：标注网页的作者 

举例：<metaname="author"content="root,root@xxxx.com"> 

#### 2、http-equiv属性 

http-equiv顾名思义，相当于http的文件头作用，它可以向浏览器传回一些有用的信息，以帮助正确和精确地显示网页内容，与之对应的属性值为content，content中的内容其实就是各个参数的变量值。 

meta标签的http-equiv属性语法格式是： 

<metahttp-equiv="参数"content="参数变量值">； 

其中http-equiv属性主要有以下几种参数： 

A、Expires(期限) 

说明：可以用于设定网页的到期时间。一旦网页过期，必须到服务器上重新传输。 

用法：\<metahttp-equiv="expires"content="Fri,12Jan200118:18:18GMT"\> 

注意：必须使用GMT的时间格式。 

B、Pragma(cache模式) 

说明：禁止浏览器从本地计算机的缓存中访问页面内容。 

用法：<metahttp-equiv="Pragma"content="no-cache"> 

注意：这样设定，访问者将无法脱机浏览。 

C、Refresh(刷新) 

说明：自动刷新并指向新页面。 

用法：\<metahttp-equiv="Refresh"content="2;URL=http://www.jb51.net"\>(注意后面的引号，分别在秒数的前面和网址的后面) 

注意：其中的2是指停留2秒钟后自动刷新到URL网址。 

D、Set-Cookie(cookie设定) 

说明：如果网页过期，那么存盘的cookie将被删除。 

用法：\<metahttp-equiv="Set-Cookie"content="cookievalue=xxx;expires=Friday,12-Jan-200118:18:18GMT；path=/"\> 

注意：必须使用GMT的时间格式。 

E、Window-target(显示窗口的设定) 

说明：强制页面在当前窗口以独立页面显示。 

用法：<metahttp-equiv="Window-target"content="_top"> 

注意：用来防止别人在框架里调用自己的页面。 

F、content-Type(显示字符集的设定) 

说明：设定页面使用的字符集。 

用法：<metahttp-equiv="content-Type"content="text/html;charset=gb2312"> 

G、content-Language（显示语言的设定） 

用法：<metahttp-equiv="Content-Language"content="zh-cn"/> 

H、Cache-Control指定请求和响应遵循的缓存机制。 
Cache-Control指定请求和响应遵循的缓存机制。在请求消息或响应消息中设置Cache-Control并不会修改另一个消息处理过程中的缓存处理过程。请求时的缓存指令包括no-cache、no-store、max-age、max-stale、min-fresh、on 

ly-if-cached，响应消息中的指令包括public、private、no-cache、no-store、no-transform、must-revalidate、proxy-revalidate、max-age。各个消息中的指令含义如下 
Public指示响应可被任何缓存区缓存 
Private指示对于单个用户的整个或部分响应消息，不能被共享缓存处理。这允许服务器仅仅描述当用户的部分响应消息，此响应消息对于其他用户的请求无效 
no-cache指示请求或响应消息不能缓存 
no-store用于防止重要的信息被无意的发布。在请求消息中发送将使得请求和响应消息都不使用缓存。 
max-age指示客户机可以接收生存期不大于指定时间（以秒为单位）的响应 
min-fresh指示客户机可以接收响应时间小于当前时间加上指定时间的响应 
max-stale指示客户机可以接收超出超时期间的响应消息。如果指定max-stale消息的值，那么客户机可以接收超出超时期指定值之内的响应消息。 

#### Meta标签使用技巧： 

Meta标签是用来描述网页属性的一种语言，标准的Meta标签可以便于搜索引擎排序，提高搜索引擎网站权重排名。要想网站做的更符合搜索引擎标准就必须了解meta标签，下面由Seoer惜缘于大家讲讲meta标签含义与使用方法： 

1、META标签的keywords 

写法为：<metaname="Keywords"content="信息参数"/> 

meat标签的Keywords的的信息参数，代表说明网站的关键词是什么。 

2、META标签的Description 

<metaname="Description"content="信息参数"/> 

meta标签的Description的信息参数，代表说明网站的主要内容，概况是什么。 

3、META标签的http-equiv=Content-Typecontent="text/html 

http-equiv=Content-Type代表的是HTTP的头部协议，提示浏览器网页的信息， 

<metahttp-equiv="Content-Type"content="text/html;charset=信息参数"/> 

meta标签的charset的信息参数如GB2312时，代表说明网站是采用的编码是简体中文； 

meta标签的charset的信息参数如BIG5时，代表说明网站是采用的编码是繁体中文； 

meta标签的charset的信息参数如iso-2022-jp时，代表说明网站是采用的编码是日文； 

meta标签的charset的信息参数如ks_c_5601时，代表说明网站是采用的编码是韩文； 

meta标签的charset的信息参数如ISO-8859-1时，代表说明网站是采用的编码是英文； 

meta标签的charset的信息参数如UTF-8时，代表世界通用的语言编码； 

4、META标签的generator 

<metaname="generator"content="信息参数"/> 

meta标签的generator的信息参数，代表说明网站的采用的什么软件制作。 

5、META标签的author 

<metaname="author"content="信息参数"> 

meta标签的author的信息参数，代表说明网页版权作者信息。 

6、META标签的http-equiv="Refresh" 

<Metahttp-equiv="Refresh"Content="时间;Url=网址参数"> 

meta标签的Refresh代表多少时间网页自动刷新，加上Url中的网址参数就代表，多长时间自动链接其他网址。 

7、META标签的HTTP-EQUIV="Pragma"CONTENT="no-cache" 

<METAHTTP-EQUIV="Pragma"CONTENT="no-cache">代表禁止浏览器从本地计算机的缓存中访问页面内容,这样设定，访问者将无法脱机浏览。 

8、META标签的COPYRIGHT 

<METANAME="COPYRIGHT"CONTENT="信息参数"> 

meta标签的COPYRIGHT的信息参数，代表说明网站版权信息。 

9、META标签的http-equiv="imagetoolbar" 

<metahttp-equiv="imagetoolbar"content="false"/> 

指定是否显示图片工具栏，当为false代表不显示，当为true代表显示。 

10、META标签的Content-Script-Type 

<Metahttp-equiv="Content-Script-Type"Content="text/javascript"> 

W3C网页规范，指明页面中脚本的类型。 

11、META标签的revisit-after 

<METAname="revisit-after"CONTENT="7days"> 

revisit-after代表网站重访,7days代表7天，依此类推。 

12、META标签的Robots<metaname="Robots"contect="信息参数"> 

Robots代表告诉搜索引擎机器人抓取哪些页面 

其中的属性说明如下： 

信息参数为all：文件将被检索，且页面上的链接可以被查询； 

信息参数为none：文件将不被检索，且页面上的链接不可以被查询； 

信息参数为index：文件将被检索； 

信息参数为follow：页面上的链接可以被查询； 

信息参数为noindex：文件将不被检索，但页面上的链接可以被查询； 

信息参数为nofollow：文件将被检索，但页面上的链接不可以被查询；





###  \<a\>标签中target属性

有 4 个保留的目标名称用作特殊的文档重定向操作：

#### _blank
浏览器总在一个新打开、未命名的窗口中载入目标文档。

#### _self

这个目标的值对所有没有指定目标的 标签是默认目标，它使得目标文档载入并显示在相同的框架或者窗口中作为源文档。这个目标是多余且不必要的，除非和文档标题 标签中的 target 属性一起使用。

#### _parent

这个目标使得文档载入父窗口或者包含来超链接引用的框架的框架集。如果这个引用是在窗口或者在顶级框架中，那么它与目标 _self 等效。

#### _top

这个目标使得文档载入包含这个超链接的窗口，用 _top 目标将会清除所有被包含的框架并将文档载入整个浏览器窗口。

#### 默认属性

```html
window.open('url', '_blank')   //默认
<a href='url' target='_self'></a> //默认
```





### HTML元素分类

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

