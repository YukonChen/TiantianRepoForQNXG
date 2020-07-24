# CSS入门笔记

## 1. 简介

- CSS控制网页的表现
- 网页实际上是一个多层的结构，通过CSS可以分别为网页的每一层设置样式，而最终我们能看到的只是网页的最上边的一层
- 总之，CSS用来设置网页中元素的样式

## 2. 内联样式

```html
<p style="color:red; font-size:60px;">
    少小离家老大回，乡音无改鬓毛衰
</p>
```

- 使用内联样式，只能对一个标签生效
- 如果希望影响到多个元素必须在每一个元素中都要重复一遍
- 并且当样式发生变化时，我们必须要一个个修改非常不方便
- 注意，开发时绝对不要用内联样式

## 3. 内部样式表

- 将样式编写到head中的style标签里
  - 然后通过CSS的选择器来选中元素并为其设置各种样式
  - 可以同时为多个标签设置样式，并且修改时只需要i需改一处就可以全部应用
- 内部样式表更加方便对样式进行复用
- 但内部样式表只能对一个网页起作用
  - 它里边的样式不能跨网页进行复用
- `<style></style>标签中的内容是CSS语法`

## 4. 外部样式表

- 可以将CSS样式编写到一个外部的CSS文件中
  - 然后通过link标签来引入外部的CSS文件放在head中

```html
<link rel="stylesheet" href="./style.css"> 
```

- 开发中一般都这样用
- 将样式编写到外部的CSS文件中，可以使用到浏览器的缓存机制中
- 从而加快网页的加载速度，提高用户的体验



## 5. CSS基本语法

- 选择器
  - 通过选择器可以选中页面中的指定元素
  - 比如p的作用就是选中页面中所有的p元素
- 声明块
  - 通过声明块来指定为元素设置的样式
  - 声明块由一个一个的声明组成
  - 一个样式名对应一个样式值
  - 名和值之间以`:`连接，以`;`结尾



## 6. 常用选择器

### 6.1. 元素选择器

- 作用：根据标签名来选中指定的元素
- 语法：标签名{}
- 例子：p{}，h1{} , div{}

### 6.2. id选择器

- 作用：根据元素的id属性值选中一个元素
- 语法：#id属性值{}
- 例子：#box{} #red{}

### 6.3. 类选择器

- class算是一个标签属性，和id相似但class可以重复
  - 可以通过class属性为元素分组
  - 可以同时为一个元素指定多个class属性
- 作用：根据元素的class属性值选中一组元素
- 语法：.class属性值{}
- 可以同时为一个元素指定多个class属性

### 6.4. 通配选择器

- 作用：选中页面中的所有元素
- 语法： *{}



## 7. 复合选择器

```CSS
    p {
      /*元素选择器*/
      color: red;
      font-size: 50px;
    }

    .yello {
      /*类选择器*/
      color: yellow;
    }

    #blue {
      /*id选择器*/
      color: blue;
    }

    div.yello {
      /*交集选择器*/
      color: blueviolet;
    }

    .a,.b,.c,.d {
      /*选择器分组，也叫并集选择器*/
      color: chartreuse;
    }


    .d.e.f.g {
      color: darkred;
      font-size: xx-large;
```



## 8. 关系选择器

```CSS
  <style>
    /* 子元素选择器 */
    div>p {
      color: blue;
    }

    div>p>span{
      color: brown;
    }

    /* 后代元素选择器 */
    div span {
      color: blueviolet;
    }

    /* 兄弟元素选择器 */
    p + span{
      color: chartreuse;
    }
    p ~ span{
      color: darkblue;
    }
  </style>
```



## 9. 属性选择器

```CSS
  <style>
    /* 选择含有指定属性的元素 */
    h1[title]{
      color: darkblue;
    }
    /* 选择含有指定属性和属性值的元素 */
    p[title=abc]{
      color: darkcyan;
    }
    /* 选择属性值以指定值开头的元素 */
    p[title^=abc]{
      color: darkgoldenrod;
    }
    /* 选择属性值以指定值结尾的元素 */
    p[title$=abc]{
      color: darkmagenta;
    }
    /* 选择属性值中含有指定值的元素 */
    p[title*=abc]{
      color: darkorange;
    }
  </style>
```



## 10. 伪类选择器

[伪类选择器](../Codes/CSSlearncode/05_伪类选择器.html)

- 伪类哟过来描述一个元素的特殊状态
  - 比如，第一个子元素，被点击的元素，鼠标移入的元素....
- 伪类一般情况下都是使用`:`开头
  - `:first-child`第一个子元素
  - `:last-child`最后一个子元素
  - `:nth-child()`选中第n个子元素
    - 特殊值
      - n，选中所有
      - 2n/even，选中所有偶数位
      - 2n+1/odd，选中所有奇数位
- 以上伪类都是根据所有的子元素进行排序的



- 按类型排序的如下
  - `:first-of-type`第一个子元素
  - `:last-of-type`最后一个子元素
  - `:nth-of-type()`选中第n个子元素



- `:not()`否定伪类
  - 将符合条件的元素从选择器中去除

## 11. 超链接的伪类

```html
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <style>
    a:link {
      color: red;
    }

    a:visited {
      color: blue;
    }
  </style>
</head>

<body>
  <a href="https://www.baidu.com">访问过的链接</a>
  <br><br>
  <a href="https://www.baidu1234.com">没访问过的链接</a>
</body>
```

- `:link`用来表示没访问过的链接（正常的链接）
- `:visited`用来表示访问过的链接
  - 由于隐私的原因，所以visited这个伪类只能修改链接的颜色
- `:hover`用来表示鼠标移入的状态
- `:active`用来表示鼠标点击

## 12. 伪元素选择器

