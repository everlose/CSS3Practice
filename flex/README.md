## flex布局初步介绍



### 概述

在很多方面HTML和CSS是一个强大的内容发布机制——易学、灵活和强大。但复杂的布局是他不擅长的。如果你想创建一个简单的图片与文本的布局，那么还算简单，但是制作一个复杂的多列布局，要做的众多浏览器的兼容一致那还是很复杂的。我们通常都是使用浮动或者其他方法来实现这个目的，而其中出现的bug和浏览器的差异性使用对布局失去兴趣。为了应对这种情况，CSS3包含了许多模块，使用不同的布局更加容易，由此引入flex布局模式。flex布局，它是为更加复杂的应用和网页而设计的。



    * 它可以在任何方向上布局（向左，向右，向下，甚至向上！）

    * 可以将显示的内容顺序颠倒（flex-direction: row-reverse）或者重新安排它们的顺序（order）

    * 可以线性布局在单个（主）轴，也可以沿（侧）轴包裹在多行中

    * 可以伸缩它们的尺寸以响应可用的空间

    * 能够相对于它们的容器对齐，或者彼此对齐

    * 可以动态的沿着主轴折叠或不折叠，同时保持容器的侧轴尺寸



### 介绍基础概念

* 伸缩容器

* 伸缩项目

* 主轴方向

* 主轴起点、主轴终点

* 主轴长度

* 侧轴方向

* 侧轴起点、侧轴终点

* 侧轴长度



![](http://www.w3.org/html/ig/zh/wiki/images/b/bf/Flex-direction-terms-new.zh-hans.png)



### 介绍伸缩容器的属性

* display

    * flex 定义一个块级的伸缩容器

    * inline-flex  定义一个行级的伸缩容器

* flex-direction  

    * row（默认值）：主轴为水平方向，起点在左端。

    * row-reverse：主轴为水平方向，起点在右端。

    * column：主轴为垂直方向，起点在上沿。

    * column-reverse：主轴为垂直方向，起点在下沿。

    ![](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071005.png)

* flex-wrap

    * nowrap(默认值)

    * wrap

    * wrap-reverse;

* flex-flow

    * <flex-direction> || <flex-wrap>; 默认为row nowrap 

* justify-content

    * flex-start（默认值）：左对齐

    * flex-end：右对齐

    * center： 居中

    * space-between：两端对齐，项目之间的间隔都相等。

    * space-around：每个项目两侧的间隔相等。所以，项目之间的间隔比项目与边框的间隔大一倍。

    ![](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071010.png)

* align-items

    * flex-start：交叉轴的起点对齐。

    * flex-end：交叉轴的终点对齐。    

    * center：交叉轴的中点对齐。

    * baseline: 项目的第一行文字的基线对齐。

    * stretch（默认值）：如果项目未设置高度或设为auto，将占满整个容器的高度。

    ![](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071011.png)

* align-content 属性定义了多根轴线的对齐方式。如果项目只有一根轴线，该属性不起作用。

    * flex-start：与交叉轴的起点对齐。

    * flex-end：与交叉轴的终点对齐。

    * center：与交叉轴的中点对齐。

    * space-between：与交叉轴两端对齐，轴线之间的间隔平均分布。

    * space-around：每根轴线两侧的间隔都相等。所以，轴线之间的间隔比轴线与边框的间隔大一倍。

    * stretch（默认值）：轴线占满整个交叉轴。

    ![](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071012.png)



### 项目上的属性值

* order css改变伸缩项目排列顺序，数值越小，排列越靠前，默认为0



* flex-grow 定义项目的放大比例，默认为0，即如果存在剩余空间，也不放大



* flex-shrink 缩小比例，默认为1，即如果空间不足，该项目将缩小



* flex-basis 可以设为跟width或height属性一样的值（比如350px），则项目将占据固定空间



* flex flex-grow, flex-shrink 和 flex-basis的简写，默认值为0 1 auto。后两个属性可选。该属性有两个快捷值：auto (1 1 auto) 和 none (0 0 auto)



* align-self 允许单个项目有与其他项目不一样的对齐方式，可覆盖align-items属性。默认值为auto，表示继承父元素的align-items属性



### 介绍语法的demo如下

```

<!DOCTYPE html>

<html>

<head>

<meta charset="UTF-8">

<title>flex</title>

<style>

.flex {

    display: flex;

    flex-direction: row;

    align-items: stretch;

    justify-content: space-between;

}

img{

    margin-top: 50px;

}

.item {



}

.item1 {

    flex: 1 100px;

    background-color: #ccc;



}

.item2 {

    flex: 2 100px;

    background-color: #0f0;

}

.item3 {

    flex: 1 100px;

    height: 40px;

    background-color: #eee

}

.item4 {

    width: 30%;

    height: 60px;

    background-color: green;

    order: 1;

}

.item5 {

    width: 25%;

    background-color: yellow;

}

.item5-1{

    width: 10%;

    color: white;

    background-color: black;

}

.item6 {

    flex: 1 1 200px;

    background-color: beige;

    align-self: auto;

}

.item7 {

    flex: 1 1 200px;

    background-color: orange;

}

.item8 {

    flex: 2 1 200px;

    height: 50px;

    background-color: red;

}

</style>

</head>

<body>

    <section>

        <div class="item item1">陈君</div>

        <div class="item item2">名</div>

        <div class="item item3">通塔</div>

    </section>

    <section>

        <div class="item item4">字</div>

        <div class="item item5">子</div>

        <div class="item item5-1">云</div>

    </section>

    <section>

        <div class="item item6">号</div>

        <div class="item item7">三</div>

        <div class="item item8">好</div>

    </section>

    <img src="http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071012.png" width="100%">

</body>

</html>

```





### 布局实战

1. 二、三、四等分布局

2. 网站常规三列布局



demo如下

```

<!DOCTYPE html>

<html>

<head>

<meta charset="UTF-8">

<title>flex</title>

<style>

.flex {

    display: flex;

    background: green;



}

.item {

    text-align: center;

    background: #fff;

    padding: 10px;

    margin: 10px;

    border-radius: 5px

}



.box {

    display: flex;

    min-height: 800px;

    flex-direction: column;

    text-align: center;

}

header,

footer {

    flex: 0 100px;

    background: #666;

    color: #fff;

}

.mnc {

    display: flex;

    flex: 1;

}



.main {

    flex: 1;

    background-color: #eee;

}



.ads {

    /* 两个边栏的宽度设为12em */

    flex: 0 0 12em;

    background-color: orange;

}



.nav {

    /* 导航放到最左边 */

    order: -1;

    flex: 0 0 10em;

    background: blue;

}

</style>

</head>

<body>

    <section>

        <div>1/2</div>

        <div>1/2</div>

    </section>

    <section>

        <div>1/3</div>

        <div>1/3</div>

        <div>1/3</div>

    </section>

    <section>

        <div>1/4</div>

        <div>1/4</div>

        <div>1/4</div>

        <div>1/4</div>

    </section>

    <br>

    <br>

    <section>

        <header>header</header>

        <div>

            <nav>nav</nav>

            <div>main</div>

            <aside>ads</aside>

        </div>

        <footer>footer</footer>

    </section>

</body>

</html>

```



### 兼容性简要介绍

* 一.W3C各个版本的flex

    * 2009 version  标志：display: box; or a property that is box-{*} (eg. box-pack)

    * 2011 version  标志：display: flexbox; or the flex() function or flex-pack property

    * 2012 version 标志：display: flex/inline-flex; and flex-{*} properties

    * 2014 version 新增了对flex项z-index的规定

    * 2015 W3C Editor’s Draft  没有大的改动



* 二.浏览器兼容性

    [浏览器兼容性参考网站链接](http://caniuse.com/#feat=flexbox)

    * IE10部分支持2012，需要-ms-前缀

    * Android Browser

        * Android Browser2.1~4.3部分支持2009 ，需要-webkit-前缀

        * Android Browser4.4及以上完全支持2012 不需要前缀

    * Safari6.1~8部分支持2012，需要-webkit-前缀, 9及以上不需要

    * chrome21~28部分支持2012，需要-webkit-前缀, 29及以上不需要

    * IOS Safari

        * IOS Safari3.2～6.1部分支持2009，需要-webkit-前缀。

        * IOS Safari7.1～8.4部分支持2012，需要-webkit-前缀。

        * IOS Safari9及以上完全支持2012，不需要前缀。

    * 所以需要考虑新版本2012： http://www.w3.org/TR/2012/CR-css3-flexbox-20120918/

    * 而Android需要考虑旧版本2009： http://www.w3.org/TR/2009/WD-css3-flexbox-20090723/



![](http://b0.hucdn.com/quick/img/upload_6104f7e57d16f1d38e4afc2b6d29310e.png)

* 三. 部分老的机型会出现的奇怪的兼容问题。
    行内元素如a标签使用flex布局需要注意先把此标签的display属性设置为block。

兼容性demo如下

```

display: box;             /* OLD 2009版 - Android 4.4- */ 

display: -webkit-box;     /* OLD - iOS 6-, Safari 3.1-6 */

display: -moz-box;       /* OLD - Firefox 19- (buggy but mostly works) */

display: -ms-flexbox;     /* TWEENER 2011版- IE 10 */

display: -webkit-flex;   /* NEW - Chrome */

display: flex;           /* NEW, Spec - chrome21+ Opera 12.1, Firefox 20+ */





/* 09版 */

-webkit-box-orient: horizontal;

/* 12版 */

-webkit-flex-direction: row;

-moz-flex-direction: row;

-ms-flex-direction: row;

-o-flex-direction: row;

flex-direction: row;





/* 09版 */

-webkit-box-align: stretch;

/* 12版 */

-webkit-align-items: stretch;

-moz-align-items: stretch;

-ms-align-items: stretch;

-o-align-items: stretch;

align-items: stretch;





/* 09版 */

-webkit-box-pack: space-between;

/* 12版 */

-webkit-justify-content: space-between;

-moz-justify-content: space-between;

-ms-justify-content: space-between;

-o-justify-content: space-between;

justify-content: space-between;



-webkit-box-flex: 1 100px;    /* OLD - iOS 6-, Safari 3.1-6 */

-moz-box-flex: 1 100px;      /* OLD - Firefox 19- */

-webkit-flex: 1 100px;        /* Chrome */

-ms-flex: 1 100px;            /* IE 10 */

flex: 1 100px;

```



### 参考文献

> 基础语法

http://www.w3cplus.com/css3/flexbox-basics.html

http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html

http://www.html-js.com/article/CSS-learning-CSS3-Flexbox

应用场景

http://www.ruanyifeng.com/blog/2015/07/flex-examples.html?bsh_bid=683103006

兼容性

http://www.tuicool.com/articles/Afq6Bzq

