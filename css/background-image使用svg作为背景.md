### 概述

background-image引入图片，之前的想象是利用background-size属性、background-repeat属性可以控制图片的缩放，拉伸从而实现背景图片的自适应。但是当遇到background-image遇到svg时，发现了不一样的结果。主要原因是 — SVG可以设置比例（viewBox、preserveAspectRatio）造成。

### 例子

SVG图像也可以`background-image`在CSS中使用，就像PNG，JPG或GIF一样

```css
.element {
  background-image: url(/images/image.svg);
}
```

所有相同的SVG都非常出色，因为灵活性同时保持了清晰度。此外，您可以执行光栅图形可以执行的任何操作，例如重复。

### 掌握的知识

#### background-image相关属性

- **background-image**
  通过url加载图片资源，比如说svg、png等等
- **background-size**
  控制加载资源的大小，这个属性可以覆盖svg的宽高

#### svg相关属性
- **viewBox**
  视图坐标系（个人定义，因为既有坐标系的功能，又定义了绘制图片的范围），在此坐标系内绘制各种图形。

- **preserveAspectRatio**
  统一缩放比例，该属性用于当视窗（viewport）与视图坐标系（viewBox）比例不一致时，该如何缩放摆放

### 核心

因为通过使用background-size的属性，控制viewport，通过viewBox控制视窗的大小，由于preserverAspectRatio的默认属性不是none。所以无法拉伸，只能调节viewBox的位置来布局。



