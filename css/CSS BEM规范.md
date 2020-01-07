[https://github.com/Tencent/tmt-workflow/wiki/⒛-[规范]--CSS-BEM-书写规范](https://github.com/Tencent/tmt-workflow/wiki/⒛-[规范]--CSS-BEM-书写规范)

### 什么是BEM

BEM其实是块（block）、元素（element）、修饰符（modifier）的缩写，利用不同的区块，功能以及样式来给元素命名。这三个部分使用`__`与`--`连接（这里用两个而不是一个是为了留下用于块儿的命名）。命名约定的模式如下：

```css
.block{}
.block__element{}
.block--modifier{}
```

- `block` 代表了更高级别的抽象或组件
- `block__element` 代表 `block` 的后代，用于形成一个完整的 `block` 的整体
- `block--modifier`代表 `block` 的不同状态或不同版本



![img](assets/webp)

bem.png

上图很直观的反映出BEM的含义，block代表一个组，而element代表组里面的成员，而modifier，虽然在上图没有画出，但是可以知道这个则是用于描述每一个元素的具体的属性。可以看出范围在一步步缩小，使命名更加具体。

### BEM的优势

BEM的关键是光凭class名字就可以让其他开发者知道某个标记用来做什么的，明白各个模块之间的关系，例如如下的命名：

```css
.nav{}
.nav__item{}
.nav--blue{}
.nav--item__hand{}
```

这几个class名很明显能看出各个块儿的作用，顶级快儿是`nav`，它有一些元素比如`item`，`item`又有一些属性，例如`blue`，但是如果写成常规的css就会很难看得出它们的关系：

```css
.nav{}
.item{}
.blue{}
```

虽然看每一个class名知道它们代表什么，但是却看不出它们之间的关系，这样对比，很明显能看出BEM命名的优势。

再看一个更具体的例子，如果写一个搜索模块，按照常规，我们会写出如下代码：

```html
<form class="site-search  full">
  <input type="text" class="field">
  <input type="Submit" value ="Search" class="button">
</form> 
```

但是如果时用BEM规范去写，代码如下：

```html
<form class="site-search  site-search--full">
  <input type="text" class="site-search__field">
  <input type="Submit" value ="Search" class="site-search__button">
</form> 
```

对比一下不难发现使用BEM可以使我们的代码可读性更高。

### BEM与SCSS

现在的开发很多时候都会用到SCSS，那么如果使用SCSS的嵌套写BEM规范呢，在SCSS中可以使用`@at-root`：

```scss
.block {
  @at-root #{&}__element {
  }
  @at-root #{&}--modifier {
  }
}
/*生成的css*/
.block {
}
.block__element {
}
.block--modifier {
}
```

非常的方便。