

```css
/* <display-outside> values */
display: block;							// 此元素将显示为块级元素，此元素前后会带有换行符。
display: inline;						// 默认。此元素会被显示为内联元素，元素前后没有换行符。
display: run-in;						// 此元素会根据上下文作为块级元素或内联元素显示。

/* <display-inside> values */
display: flow;							// 
display: flow-root;					// 可以理解为父级计算友好的float元素
display: table;							// 此元素会作为块级表格来显示（类似 <table>），表格前后带有换行符。
display: flex;							// 此元素会作为弹性盒子(flexbox)方式进行弹性布局展示
														// 子元素的float、clear和vertical-align属性将失效。
display: grid;							// 此元素会作为网格容器进行网格式布局
display: subgrid;					// 它的行/列的大小继承自它的父级网格容器，而不是自己指定的。
display: ruby;							// 使用类似于汉字注音/训读方式进行文本表示的布局展示

/* <display-outside> plus <display-inside> values */
display: block flow;
display: inline table;
display: flex run-in;

/* <display-listitem> values */
display: list-item;
display: list-item block;
display: list-item inline;
display: list-item flow;
display: list-item flow-root;
display: list-item block flow;
display: list-item block flow-root;
display: flow list-item block;

/* <display-internal> values */
display: table-row-group;
display: table-header-group;
display: table-footer-group;
display: table-row;
display: table-cell;
display: table-column-group;
display: table-column;
display: table-caption;
display: ruby-base;
display: ruby-text;
display: ruby-base-container;
display: ruby-text-container;

/* <display-box> values */
display: contents;				// 不会渲染其背景边框和内边距,但继承的属性还是会对其子元素产生效果
display: none;						// 此元素不会被显示。

/* <display-legacy> values */
display: inline-block;		// 行内块元素。可使用width等属性
display: inline-table;		// 此元素会作为内联表格来显示（类似 <table>），表格前后没有换行符。
display: inline-flex;			// 将对象作为内联块级弹性伸缩盒显示
display: inline-grid;			// 设置一个内联级的网格

/* Global values */
display: inherit;					// 规定应该从父元素继承 display 属性的值
display: initial;					// Element对应的默认属性
display: unset;						// 如果该属性默认可继承，则值为inherit；否则值为initial。相当于不设置
```

### 正式语法/分类

```css
][ <display-outside> || <display-inside> ] | <display-listitem> | <display-internal> | <display-box> | <display-legacy>
```