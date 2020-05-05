资料：
http://www.lvyestudy.com/
http://www.ruanyifeng.com/blog/javascript/
https://developer.mozilla.org/zh-CN/

# ①css选择器

优先顺序：

`!important`总是优先于其他规则

### 属性选择器

​    [属性名] 选择含有指定属性的元素

​      [属性名=属性值] 选择含有指定属性和属性值的元素

​      [属性名^=属性值] 选择属性值以指定值开头的元素

​      [属性名$=属性值] 选择属性值以指定值结尾的元素

​      [属性名*=属性值] 选择属性值中含有某值的元素的元素

###     交集选择器

​        作用：选中同时复合多个条件的元素

​        语法：选择器1选择器2选择器3选择器n{}

​        注意点：

​          交集选择器中如果有元素选择器，必须使用元素选择器开头

   

### 分组和继承


```
分组: 选择器用逗号分开，被分组的选择器可以分享相同的声明
```

```
继承: 正常情况下，子元素从父元素继承属性
但也会出现特殊情况，只能通过组选择器来对待
```



### 派生选择器



```
/* 根据文档的上下文关系来确定某个标签的样式 */
li p {
	
}
```


### 伪类选择器


> CSS 伪类用于向某些选择器添加特殊的效果。 CSS 伪元素用于将特殊的效果添加到某些选择器。



两者区别在于: 伪类的效果可以通过添加一个实际的`类`来达到，而伪元素的效果则需要通过添加一个实际的`元素`才能达到



### 伪类

>不存在的类，表示特殊状态，：开头，好处是不需要额外class
- :last-child
- :first-of-type （last,nth）只找相同类型
- :nth-child  第n个子元素 
- :not() 否定伪类
- a:link   未访问
- a:visited 访问过，由于隐私的原因，这个伪类只能改链接的颜色
- a:hover 移动
- a:active 点击
- 特殊值：n o-正无穷  2n（even） 表示选择偶数位  2n+1（odd） 奇数位

[例如：p:first-child指的是p元素是某元素的第一个子元素](http://www.w3school.com.cn/tiy/t.asp?f=css_sel_firstchild)

***

### 伪元素
>不存在的元素
- ::first-letter 表示第一个字母
- ::first-line 
- ::selection 表示选中的内容
- ::before 元素开头
- ::after 元素最后
    - 必须结合content属性，无法选中（css加载）

![伪元素]()

### 组合器

| [Combinators](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS/Combinators_and_multiple_selectors) | Select                                                       |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| A,B                                                          | 匹配满足A（和/或）B的任意元素（参见下方 同一规则集上的多个选择器）. |
| A B                                                          | 匹配任意元素，满足条件：B是A的后代结点（B是A的子节点，或者A的子节点的子节点） |
| A > B                                                        | 匹配任意元素，满足条件：B是A的直接子节点                     |
| A + B                                                        | 匹配任意元素，满足条件：B是A的下一个兄弟节点（AB有相同的父结点，并且B紧跟在A的后面） |
| A ~ B                                                        | 匹配任意元素，满足条件：B是A之后的兄弟节点中的任意一个（AB有相同的父节点，B在A之后，但不一定是紧挨着A) |



***

### 样式继承
> 继承是发生在祖先后代之间
背景相关，布局相关的样式不被继承

### 权重（优先级）
！important>内联>id>类,伪类选择器>元素>通配>继承

分组选择器单独计算,
- 内联样式 1,0,0,0
- id选择器 0,1,0,0
- 类和伪类选择器 0,0,1,0
- 元素选择器 0,0,0,1
- 继承样式 没有优先级
若选择器优先级计算前后相同,则优先使用靠下的样式.

https://flukeout.github.io/
选择器练习

***

# ②css布局

参考资料：
- 
## 1.1盒子模型

![盒子模型](https://www.runoob.com/images/box-model.gif)

默认情况下，`width`和`height`只包括内容区域的宽和高，不包括border、padding、margin。
使用`box-sizing`可以使其包含content、padding、border

`box-sizing`的值:

```css
/* 默认值，标准盒子模型，只含内容区 */ 
box-sizing:content-box;
/* width 和 height 属性包括内容，内边距和边框，但不包括外边距 */ 
box-sizing:border-box;
```

行内元素的盒模型
- 不支持宽度和高度
- 垂直方向padding,border,margin ,不会影响布局(不显示)
- display: inline/block/inline-block(既可以设置宽高,又不会独占一行,但会有空隙,避免)/table/none(隐藏元素)
- visibility :显示元素状态
    - 默认值,正常显示
    - hidden 隐藏不显示,但依然占据位置


默认样式:
    通常浏览器会为元素设置默认样式
    通常需要去除浏览器的默认样式(PC的页面)
引入重置样式表

文字居中,只需要height与父类的line-height
***
## 1.2 浮动模型

***

###  浮动的背景和工作原理


> 浮动的最初是用来**让文字环绕图片**, 所以能推出:
> 浮动会**脱离**正常的文档流，并吸附到其**父容器**左边，正常布局中位于浮动元素下的内容会**围绕**着浮动元素
脱离文档流后，不再区分行内和块 
### 浮动的包裹性：

> 包裹性指的是元素尺寸刚好容纳内容, 表现得就像`diaplay:inline-block`一样

具有包裹性的其他属性:

```css
display:inline-block
position:absolute/fixed/sticky
overflow:hidden/scroll
```

### 浮动的破坏性：

会使父元素**高度塌陷**——为了实现文字环绕效果

浮动布局中，父类的高度默认被子类撑开
当子类浮动后，会脱离文档流，导致父类高度丢失
具有破坏性的其他属性:

```css
display:none
position:absolute/fixed/sticky
```

那怎么解决破坏性带来的问题呢？

(把高度写死，但会没有继承的好处)
***





##  1.3清除浮动 (clearfix hack)



### 投机取巧法

在父元素底部加上`<div style="clear:both;"></div>`虽说兼容性好，但是浪费一个标签，违反了**语义化**，不推荐

###  overflow + zoom法

------

补充知识: BFC(Block Formatting Context)


BFC:块级格式化上下文【在css3中叫Flow Root】是一个独立布局环境，相邻盒子margin垂直方向会重叠。
隐藏属性，会变成一个**独立的布局区域**

什么样的元素会为其内容生成一个BFC呢？

1. （设置父类为）浮动元素，即float:left/right  
2. 🍕绝对定位元素，即position:absolute/fixed  
3. 块容器，即display:table-cell/table-caption/inline-block    设置为行内块
4. 设置了除visible外的overflow值的块盒子，即overflow:hidden/scroll/auto

BFC特性：

1. 创建了BFC的元素中，**子浮动元素也会参与高度计算**  
2. 与浮动元素相邻的、创建了BFC的元素，都不能与浮动元素相互覆盖
3. 创建了BFC的元素不会与它们的子元素margin重叠
4. 开启后可以包含浮动的子元素
------

因为子浮动元素也会参与高度计算, 所以借此可以得到以下方法:


1.清除浮动

设置清除浮动以后，浏览器会自动为元素添加？？？
以使得位置不受其他

clear
- left
- right
- both 清除两侧中影响最大的影响

额外标签法
但增加了无关结构的累赘

```css
.fix {
    overflow:hidden; zoom:1;
}
```

方法不错，但是可能内容会被裁减掉，可以偶尔用用

2. after伪元素 + zoom法 

看一下2.4.1，虽然不错，但是违反语义化; 所以就想到了通过CSS来添加子元素，不修改HTML代码 —— `:after`选择符


```css
.clearfix:after {
    content: " ";  //content可以任意发挥
    display: block;//转为块
    line-height: 0;  //height: 0也行
    clear: both;
}
.clearfix {
    zoom: 1; 
}

.clearfix::before,.clearfix::after{
    content:'';
    display:table;//既可以解决外边距重叠和高度塌陷，table无内容
    clear:both;
}
```
这个方法最佳, 推荐这个方法



浮动布局

转发自 [CSS深入理解之float浮动(张鑫旭)](https://www.imooc.com/learn/121)

***


作业中有一个简历需要两个分栏高度相等，这里提供一个解决方法

[使分栏高度一致的纯CSS解决办法](http://www.zhangxinxu.com/wordpress/2010/03/纯css实现侧边栏分栏高度自动相等/)

## 1.4 定位position

- static,默认值，一个 static 元素表示它*不会被“positioned”*
- relative,在一个相对定位（position属性的值为relative）的元素上设置 `top` 、 `right` 、 `bottom` 和 `left` 属性会使其偏离其正常位置。其他的元素的位置则不会受该元素的影响发生位置改变来弥补它偏离后剩下的空隙。
- fixed:相对固定，移动浏览器对 fixed 的支持很差
- absolute：绝对固定，它相对于它的父元素定位。
```css
overflow: auto;
```


在父元素 绝对定位
水平布局-居中-9
垂直布局-居中-9
margin-top:auto;
margin-bottom:auto;
###  侧边栏分栏高度自动相等

层级：
对于开启定位元素，可通过z-index属性来确认优先显示
若层级相同，优先显示向下的（一般不玩负数）
祖先元素盖不住子类
absolute>
***
有空格特殊符号需要加‘’
字体族
- em ：相当于当前元素
- rem :相对于根元素的一个fond-side
font-family :
- 可以同时执行多个字体
- serif 衬线字
- sans-serif 非衬线
- monospace  等宽
- cursive
- 用户自己的字体
@font-face{
    指定服务器的字体
    问题 1. 加载速度
        2. 版权问题
}

iconfont:
注意版权
font awesome:



## 1.5 框类型 `display`

|      值      | 说明                                                         |
| :----------: | :----------------------------------------------------------- |
|    block     | 块框（ block box）是定义为堆放在其他框上的框（例如：其内容会独占一行），而且可以设置它的宽高，之前所有对于框模型的应用适用于块框 （ block box） |
|    inline    | 行内框（ inline box）与块框是相反的，它随着文档的文字（例如：它将会和周围的文字和其他行内元素出现在同一行，而且它的内容会像一段中的文字一样随着文字部分的流动而打乱），对行内盒设置宽高无效，设置padding, margin 和 border都会更新周围文字的位置，但是对于周围的的块框（ block box）不会有影响。 |
| inline-block | 行内块状框（inline-block box） 像是上述两种的集合：它不会重新另起一行但会像行内框（ inline box）一样随着周围文字而流动，而且他能够设置宽高，并且像块框一样保持了其块特性的完整性，它不会在段落行中断开。 |

|    table     | 像处理table布局那样处理非table元素，而不是滥用HTML的<table>;标签来达到同样的目的  。 |
|     flex     | 处理一些困扰CSS已久的一些传统布局问题，例如布置一系列弹性等宽容器或者垂直居中内容。 |
|     grid     | 给出一种简单实现CSS网格系统的方式，而在传统上它依赖于一些棘手难以处理的CSS网格框架 | 

 ***

 flex-direction 指定容器中弹性元素的排列方式

      flex-basis 指定的是元素在主轴上的基础长度
                    如果主轴是 横向的 则 该值指定的就是元素的宽度
                    如果主轴是 纵向的 则 该值指定的是就是元素的高度
                    - 默认值是 auto，表示参考元素自身的高度或宽度
                    - 如果传递了一个具体的数值，则以该值为准

                 /* order 决定弹性元素的排列顺序 */


      flex 可以设置弹性元素所有的三个样式
                    flex 增长 缩减 基础;
                        initial "flex: 0 1 auto".
                        auto  "flex: 1 1 auto"
                        none "flex: 0 0 auto" 弹性元素没有弹性
           

###像素

像素：
            - 屏幕是由一个一个发光的小点构成，这一个个的小点就是像素
            - 分辨率：1920 x 1080 说的就是屏幕中小点的数量
            - 在前端开发中像素要分成两种情况讨论：CSS像素 和 物理像素
            - 物理像素，上述所说的小点点就属于物理像素
            - CSS像素，编写网页时，我们所用像素都是CSS像素
                - 浏览器在显示网页时，需要将CSS像素转换为物理像素然后再呈现
                - 一个css像素最终由几个物理像素显示，由浏览器决定：
                    默认情况下在pc端，一个css像素 = 一个物理像素

        视口（viewport）
            - 视口就是屏幕中用来显示网页的区域
            - 可以通过查看视口的大小，来观察CSS像素和物理像素的比值
            - 默认情况下：
                视口宽度 1920px（CSS像素）
                        1920px（物理像素）
                        - 此时，css像素和物理像素的比是 1:1

            - 放大两倍的情况：
                视口宽度 960px（CSS像素）
                        1920px（物理像素）
                        - 此时，css像素和物理像素的比是1:2

            - 我们可以通过改变视口的大小，来改变CSS像素和物理像素的比值

移动端默认的视口大小是980px(css像素)，
            默认情况下，移动端的像素比就是  980/移动端宽度  （980/750）
            如果我们直接在网页中编写移动端代码，这样在980的视口下，像素比是非常不好，
                导致网页中的内容非常非常的小
            编写移动页面时，必须要确保有一个比较合理的像素比：
                1css像素 对应 2个物理像素
                1css像素 对应 3个物理像素

            - 可以通过meta标签来设置视口大小

            - 每一款移动设备设计时，都会有一个最佳的像素比，
                一般我们只需要将像素比设置为该值即可得到一个最佳效果
                将像素比设置为最佳像素比的视口大小我们称其为完美视口

                将网页的视口设置为完美视口
                <meta name="viewport" content="width=device-width, initial-scale=1.0">

                结论：以后再写移动端的页面，就把上边这个玩意先写上


    <!-- 
        不同的设备完美视口的大小是不一样的
            iphone6 -- 375
            iphone6plus -- 414

        由于不同设备视口和像素比不同，所以同样的375个像素在不同的设备下意义是不一样，
            比如在iphone6中 375就是全屏，而到了plus中375就会缺一块

        所以在移动端开发时，就不能再使用px来进行布局了

        vw 表示的是视口的宽度（viewport width）
            - 100vw = 一个视口的宽度
            - 1vw = 1%视口宽度

            vw这个单位永远相当于视口宽度进行计算

            设计图的宽度
                750px 1125px

            设计图 
                750px  

            使用vw作为单位
                100vw

            创建一个 48px x 35px 大小的元素

            100vw = 750px(设计图的像素) 0.1333333333333333vw = 1px
            6.4vw = 48px(设计图像素)
            4.667vw = 35px


/*
        使用媒体查询 
            语法： @media 查询规则{}
                媒体类型：
                    all 所有设备
                    print 打印设备
                    screen 带屏幕的设备
                    speech 屏幕阅读器
                    - 可以使用,连接多个媒体类型，这样它们之间就是一个或的关系

                可以在媒体类型前添加一个only，表示只有。
                    only的使用主要是为了兼容一些老版本浏览器
         */

        /* @media print,screen{
            body{
                background-color: #bfa;
            }
            */


      /*
             媒体特性：
                width 视口的宽度
                height 视口的高度

                min-width 视口的最小宽度（视口大于指定宽度时生效）
                max-width 视口的最大宽度（视口小于指定宽度时生效）
         */

         /* @media (max-width: 500px){
             body{
                background-color: #bfa;
             }
         } */

/* 
         样式切换的分界点，我们称其为断点，也就是网页的样式会在这个点时发生变化
         一般比较常用的断点

         小于768 超小屏幕 max-width=768px
         大于768 小屏幕   min-width=768px
         大于992 中型屏幕 min-width=992px
         大于1200 大屏幕  min-width=1200px

*/