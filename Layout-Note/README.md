# 常规布局方式
- box-sizing: border-box属性：内边距和边框不会增加它的宽度；
- max/min-width 属性：能够让元素随着浏览器窗口改变大小；
- margin:auto 属性：让元素水平居中；
- 盒模型：使用position/float来实现布局；
- 清除浮动最好的方式是用伪元素：

```
 eg:
 //兼容IE6以下
 .clearfix{
    zoom:1;
 }
 .clearfix::after{
    content:'';
    display:block;
    height:0;
    visibility:hidden;
    clear:both;
 }
```
- inline-block配合使用百分比宽度布局；

# flexbox 布局

## 介绍
- Flexible Box的缩写，弹性布局；
- 任何一个容器都可以指定为Flex布局；
- 设为Flex布局以后，子元素的float/clear/vertical-align属性将失效；

## 基本概念
- 采用Flex布局的元素叫容器，子元素叫容器成员，称为项目；
- 容器存在两根轴，水平的主轴和垂直的交叉轴；
- 项目默认沿主轴排列；

## 容器的六个属性

1. flex-direction属性:决定主轴的方向；
- row(默认值):主轴为水平方向，起点在左端；
- row-reverse:主轴为水平方向，起点在右端；
- column:主轴为垂直方向，起点在上沿；
- column-reverse:主轴为垂直方向，起点在下沿；

2. flex-wrap属性：如果一条轴线排不下，如何换行
- nowrap(默认):不换行；
- wrap:换行，第一行在上方；
- wrap-reverse:换行，第一行在下方；

3. flex-flow属性：是flex-direction属性和flex-wrap属性的简写形式
- row nowrap(默认值)；

4. justify-content属性：项目在主轴上的对其方式
- flex-start(默认值):左对齐；
- flex-end:右对齐；
- center:居中；
- space-between:两端对其，项目之间的间隔都相等；
- space-around:每个项目两侧的间隔相等。所以，项目之间的间隔比项目与边框的间隔大一倍；

5. align-items：项目在交叉轴上如何对齐；
- flex-start:交叉轴的起点对齐；
- flex-end:交叉轴的终点对齐；
- center:交叉轴的中点对齐；
- baseline:项目的第一行文字的基线对齐；
- stretch(默认值):如果项目未设置高度或设为auto，将占满整个容器的高度；

6. align-content:多跟轴线的对齐方式，如果只有一根，该属性不起作用
- flex-start:与交叉轴的起点对齐；
- flex-end:与交叉轴的终点对齐；
- center:与交叉轴的中点对齐；
- space-between:与交叉轴两端对齐，轴线之间的间隔平均分布；
- space-around:每根轴线两侧的间隔都相等，所以，轴线之间的间隔比轴线与边框的间隔大一倍；
- stretch(默认值):轴线占满整个交叉轴；

## 项目的六个属性

1. order:项目的排列顺序，数值越小，排列越靠前，默认为0；
2. flex-grow:项目的放大比例，默认为0；
3. flex-shrink：项目的缩小比例，默认为1；（一个项目为0，其余为1，前者不缩小，负值对该属性无效）
4. flex-basis：项目占据的主轴空间，默认为auto（项目本来大小）；
5. flex：是flex-grow/flex-shrink/flex-basis的简写，默认值为0 1 auto；（后两个属性可选）；
6. align-self：允许单个项目有与其他项目不一样的对齐方式，可覆盖align-items属性（默认值为auto，继承父元素的align-items属性，没有父元素等同于stretch）；
   