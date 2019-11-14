一、flex布局简介
    flex是flexible box（弹性布局）的简介，是一个一维系统，用来为盒状模型提供最大的灵活性。

    使用：任何容器（行内元素可设置为display:inline-block）;
    
    特点：空间分布在行中进行，而非整体

二、grid布局简介
    Gird Layout(css网格布局)是css中最强大的布局系统，是一个二维系统，可以同时处理行和列，可以通过将css规则用于父元素（网格容器）和该元素的子元素（网格元素）来使用网格布局。

    使用：对父元素设置dispay：grid;grid-template-colums和grid-template-rows来设置几行几列，然后对子元素设置占据几行几列
    
    特点：二维网格结构，十分便于操作
    
    基本概念：
    
        *container：网格容器，设置display:grid就将容器变成了网格容器
    
        *item：网格项，指网格容器中每一个子元素
    
        *line：网格线，网格之间的分界线
    
        *track：网格轨道，两条相邻的网格线之间的空间（行或列）
    
        *cell：网格单元，每个小网格
    
        *area：网格区域，四条网格线包围起来的区域
    
        *fr：在自由空间进行分配的一个单位


# Grid的由来

> 一开始我们使用table、float、position以及inline-block进行响应式布局，但都有点 Hack 的方式，并且遗漏了很多重要的功能（例如垂直居中）。
>
> Flexbox的出现在一定程度上解决了这个问题，但是它的目的是为了更简单的一维布局，而不是复杂的二维布局（Flexbox和Grid实际上一起工作得很好）。 只要我们一直在制作网站，我们就一直在为解决布局问题不断探索， 而Grid是第一个专门为解决布局问题而生的CSS模块。

## Gird简介和基本概念

- grid布局又称CSS网格布局，（又名“网格”）是一个二维的基于网格的布局系统，其目的只在于完全改变我们设计基于网格的用户界面的方式。
- grid中的一些概念
  - 网格容器（Grid Container）元素应用display:grid，它是其所有网格项的父元素。
  - 网格项（Grid Item）网格容器的直接子元素
  - 网格线（Grid Line）组成网格线的分界线。它们可以是列网格线（column grid lines），也可以是行网格线（row grid lines）并居于行或列的任意一侧
  - 网格轨道（Grid Track）两个相邻的网格线之间为网格轨道。
  - 网格单元（Grid Cell）两个相邻的列网格线和两个相邻的行网格线组成的是网格单元，它是最小的网格单元。
  - 网格区（Grid Area）网格区是由任意数量网格单元组成
- grid目前兼容性目前还可以，主流浏览器对它的支持力度很大，ie9,10宣布它未来不久会对它有很好的支持，目前则需要使用过时的语法。我相信不久的将来grid将成为每一个前端工作人员必备的布局技能。

## 属性介绍

### 父元素上的属性

| 属性                  | 说明                                              |
| :-------------------- | :------------------------------------------------ |
| display               | 设置grid布局                                      |
| grid-template-rows    | 设置网格的行数                                    |
| grid-template-columns | 设置网格的列数                                    |
| grid-template-areas   | 根据子元素的网格名字来排列                        |
| grid-column-gap       | 用来指定竖网格轨道的大小                          |
| grid-row-gap          | 用来指定行网格轨道的大小                          |
| grid-gap              | grid-column-gap和grid-row-gap这两个属性的缩写方式 |
| justify-items         | 网格中所有单元格中的内容在X轴的对齐方式           |
| align-items           | 网格中所有单元格中的内容在Y轴的对齐方式           |
| justify-content       | 来设置整个网格在网格容器中的X轴的排列方式         |
| align-content         | 来设置整个网格在网格容器中的Y轴的排列方式         |
| grid-auto-columns     | 设定隐藏的网格的高                                |
| grid-auto-rows        | 设定隐藏的网格的宽                                |
| grid-auto-flow        | 在布局的时候，选择网格填充的方法                  |

#### 设置grid布局

```cpp
display:grid | inline-grid |  subgrid;
```

| 属性值      | 说明                                                         |
| :---------- | :----------------------------------------------------------- |
| grid        | 设置块级grid网格布局                                         |
| inline-grid | 设置一个内联级的网格                                         |
| subgrid     | 如果这个网格本身就是父元素中的某一个单元网格，则这个值是用来表示继承父元素,希望它的行/列的大小继承自它的父级网格容器，而不是自己指定的。 |

#### 设置网格的列数与行数

1. grid-template-columns 它表示的是设置列数

```css
grid-template-columns:100px 10% 1fr 2fr; /*写几个值表示有几列   值可以是px这种固定大小的，也可以是百分比，也可以使用fr这种单位；fr表示总空间减去固定空间和百分比的大小，然后再分配*/
grid-template-columns: [c1] 200px [c2] 200px [c3] 1fr [c4];/*这里的[]是在给网格线起名字，每个网格线可以有多个名字，用空格隔开就OK，在后面会说到网格线名字的作用*/
grid-template-columns:repeat(12 1fr);    /*这个repeat是重复的意思，也就是我们创建了12个大小相等的列*/
grid-template-columns: repeat(auto-fit, 100px);    /*auto-fit 自适应的意思，也就是说尽可能的每块100px填满网格容器*/
grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));/*上面的这种repeat(auto-fit, 100px)在响应式布局中可能因为不到100像素然后产生留白，所以我们用minmax()来解决，我们用minmax(100px, 1fr)来代替100px   minmax() 函数定义大于或等于 min 且小于或等于 max 的大小范围*/
```

1. grid-template-rows 与grid-template-columns的使用方法相同 设置网格项的行数

```css
grid-template-rows:100px 10% 1fr 2fr; /*写几个值表示有几行   值可以是px这种固定大小的，也可以是百分比，也可以使用fr这种单位；fr表示总空间减去固定空间和百分比的大小，然后再分配*/
```

#### 通过网格单元的名字来布局 grid-template-areas

> 使用这个属性的时候，需要先用子元素上的grid-area属性给子元素起一个名字，然后再配合这个属性来时使用

```css
.box{
            background-color: #999;
            display: grid;
            grid-template-columns: 100px 80% 1fr 1fr;
          grid-template-rows: 200px 300px 300px;
          grid-template-areas: "header header header ."
                               "main main . sidebar"
                               "footer footer footer footer"
            /*名字便是元素的名字，点(.)代表的意思是空一格，这个单元格中不放内容*/
}
.a{
            grid-area:header;
            /*grid-area:;   是给子元素起一个名字*/
            background-color: red;
}
.b{
            grid-area:main;
            background: blue;
}
.c{
            grid-area:sidebar;
            background: pink;
}
.d{
       grid-area:footer;
       background: black;
}
<div class="box">
        <div class="a">
            头部
        </div>
        <div class="b">
            主题
        </div>
        <div class="c">
            侧边栏
        </div>
        <div class="d">
            底部
        </div>
</div>
```

#### 设置网格轨道的大小

- grid-column-gap和grid-row-gap 用来指定横竖网格轨道的大小 只在两个单元格之间产生间距，不再边缘产生
- grid-gap grid-column-gap和grid-row-gap这两个属性的缩写方式

```css
.box{
    grid-row-gap:10px;
    grid-column-gap:20px;
}
.box{
    grid-gap:10px 20px;
    /* grid-gap: grid-row-gap grid-column-gap; */
}
```

#### justify-items 网格中所有单元格中的内容在网格项X轴的对齐方式 默认是占满宽度整个X轴

| 属性值  | 说明                                 |
| :------ | :----------------------------------- |
| start   | 内容在单元格的左端对齐               |
| end     | 内容在单元格的右端对齐               |
| center  | 内容在单元格X轴的中间位置            |
| stretch | 内容宽度占据整个单元格的X轴 (默认值) |

#### align-items 网格中所有单元格中的内容在网格项Y轴的对齐方式 默认是占满宽度整个Y轴 它的值与justify-items相同

| 属性值  | 说明                                 |
| :------ | :----------------------------------- |
| start   | 内容在单元格的顶端对齐               |
| end     | 内容在单元格的底部对齐               |
| center  | 内容在单元格Y轴的中间位置            |
| stretch | 内容高度占据整个单元格的Y轴 (默认值) |

#### justify-content 如果我们使用PX这种固定大小的布局方式的时候，网格的大小可能小于网格容器的大小

> 这个值是用来设置整个网格在网格容器中的X轴的排列方式

| 属性值        | 说明                                              |
| :------------ | :------------------------------------------------ |
| start         | 网格与网格容器的左端对齐                          |
| end           | 网格与网格容器的右端对齐                          |
| center        | 网格处于网格容器的X轴的中间                       |
| stretch       | 调整网格项的大小，使其宽度填充整个网格容器        |
| space-around  | 相当于给每一列单元格添加相同的左右margin          |
| space-between | 在网格容器的X轴的两段对齐                         |
| space-evenly  | 每一列之间的左右间距是相同的 与边缘也有相同的距离 |

#### align-content 如果我们使用PX这种固定大小的布局方式的时候，网格的大小可能小于网格容器的大小

> 这个值是用来设置整个网格在网格容器中的Y轴的排列方式

| 属性值        | 说明                                              |
| :------------ | :------------------------------------------------ |
| start         | 网格与网格容器的顶部对齐                          |
| end           | 网格与网格容器的底部对齐                          |
| center        | 网格处于网格容器的Y轴的中间                       |
| stretch       | 调整网格项的大小，使其高度填充整个网格容器        |
| space-around  | 相当于给每一行单元格添加相同的上下margin          |
| space-between | 在网格容器的Y轴的两段对齐                         |
| space-evenly  | 每一行之间的上下间距是相同的 与边缘也有相同的距离 |

#### grid-auto-columns和grid-auto-rows 设定隐藏的网格轨道的大小

> 自动生成隐式网格轨道（列和行），当你定位的网格项超出网格容器范围时，将自动创建隐式网格轨道。网格轨道大小,可以是固定值，百分比或者是分数（fr单位）。

#### grid-auto-flow 在布局是时候，选择网格填充的方法

> 在没有设置网格项的位置时，这个属性控制网格项怎样排列。

| 属性值 | 说明                   |
| :----- | :--------------------- |
| row    | 按照行依次从左到右排列 |
| column | 按照列依次从上倒下排列 |
| dense  | 按先后顺序排列         |

#### grid的简写方式和属性的顺序,设置网格容器所有属性。

> grid: none | grid-template-rows / grid-template-columns | grid-auto-flow [grid-auto-rows [ / grid-auto-columns] ];

### 设置子元素上的属性

| 属性              | 说明                                                   |
| :---------------- | :----------------------------------------------------- |
| grid-area         | 给单个子元素起名字                                     |
| grid-column-start | 元素的位置哪跟竖线开始                                 |
| grid-column-end   | 哪跟竖线结束                                           |
| grid-row-start    | 哪跟横线开始                                           |
| grid-row-end      | 哪跟横线结束                                           |
| grid-row          | grid-row-start和grid-row-end的缩写                     |
| grid-column       | grid-column-start和grid-column-end这两个属性的缩写方式 |
| grid-area         | grid-row和grid-column的缩写                            |
| justify-self      | 设置单个子元素在其所在的小网格中的X轴排列方式          |
| align-self        | 设置单个子元素在其所在的小网格中的Y轴排列方式          |
| align-content     | 来设置整个网格在网格容器中的Y轴的排列方式              |

#### grid-area 给单个子元素起名字

> 这个属性就是配合父元素上的grid-template-areas属性来使用，grid-area就是给单个网格项起个名字

#### 设置网格项位置的三种写法

1. grid-column-start grid-column-end grid-row-start grid-row-end

```undefined
从左到右的四个属性的含义：  
            哪跟竖线开始
            哪跟竖线结束
            哪跟横线开始
            哪跟横线结束
值写数字表示第几跟网格线       也可以写网格线的名字
```

1. grid-column grid-row

```undefined
grid-column: 1 / 2;
grid-row: 1 / 2;
```

1. grid-area grid-column和grid-row的缩写

```css
grid-area: 1/1/2/2;
/*第三种写法  行起始位置/列起始位置/行结束位置/列结束位置*/
```

#### 设置单个子元素在其所在的网格项中的排列方式

1. justify-self 用来设置单个元素在单个网格项中X轴的布局

| 属性    | 说明                         |
| :------ | :--------------------------- |
| start   | 元素与网格的左端对齐         |
| end     | 元素与网格的右端对齐         |
| center  | 元素放置在网格X轴的中间      |
| stretch | 元素占满整个网格空间(默认值) |

1. align-self 与justify-self:;类似，用来设置单个元素在单个网格中Y轴的布局方式，和justify-self有4个相同的值

| 属性    | 说明                         |
| :------ | :--------------------------- |
| start   | 元素与网格的顶部对齐         |
| end     | 元素与网格的底部对齐         |
| center  | 元素放置在网格Y轴的中间      |
| stretch | 元素占满整个网格空间(默认值) |





