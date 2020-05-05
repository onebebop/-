# 

使用vscode编译， 按照插件 

[制作导航条的方法](http://www.runoob.com/css/css-navbar.html)

# 常用属性

## 连接 a



根据所处状态决定样式

```
a:link {color:#FF0000;}		/* 未被访问的链接 */
a:visited {color:#00FF00;}	/* 已被访问的链接 */
a:hover {color:#FF00FF;}	/* 鼠标指针移动到链接上 */
a:active {color:#0000FF;}	/* 正在被点击的链接 */
```



> 注意: 一定要按照LVHA的顺序指定！



可用background为连接增加小图标



***



| 属性                  | 说明         | 值                                                           | 备注                                                         |
| --------------------- | ------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
|                       | 背景色       |                                                              | 建议加上，作为后备，以防背景图像无法加载                     |
| background-image      | 背景图像     | url(…)、渐变: linear-gradient(to 渐变的方向,开始的颜色,结尾的颜色) | 渐变可以在中途选择其他的点，渐变不能用于background-color、color |
| background-repeat     | 背景重复     | repeat(默认)、repeat-x、repeat-y、no-repeat                  |                                                              |
| background-position   | 背景定位     | 关键字、百分数值、长度值                                     | 坐标系为x坐标从左到右,y坐标从上到下;可以用于[雪碧图](http://www.imooc.com/learn/93) |
| background-attachment | 背景附着     | scroll(默认)、fixed                                          |                                                              |
| background-size       | 背景图像大小 | 长度值、百分数值、cover、contain [点击查看示例](http://www.w3school.com.cn/tiy/c.asp?f=css_background-size&p=7) |                                                              |
| background            | 背景简写     |                                                              | 可按任意顺序放置                                             |



## 边框 border



| 属性          | 说明     | 值                                                           | 备注                                                         |
| ------------- | -------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| border        | 边框简写 | [border-width border-style border-color /inherit]            | 三角形和梯形可以使用border+transparent来做                   |
| border-style  | 边框样式 | none、hidden、dotted、dashed、solid、double、(groove、ridge、inset、outset、)inherit | [样式预览](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-style) |
| border-width  | 边框宽度 |                                                              | 不支持百分比、默认为medium(3px)                              |
| border-color  | 边框颜色 | 透明:transparent                                             | 默认颜色同color                                              |
| border-radius | 边界圆角 |                                                              |                                                              |



## 列表 list



| 属性                | 说明       | 值                                                           | 备注               |
| ------------------- | ---------- | ------------------------------------------------------------ | ------------------ |
| list-style-type     | 列表标志   | [标志值](http://www.w3school.com.cn/cssref/pr_list-style-type.asp) |                    |
| list-style-image    | 列表项图像 | url()                                                        | 可用background代替 |
| list-style-position | 列表项位置 | inside(文本内文本环绕)、outside(默认)、inherit               |                    |
| list-style          | 列表简写   | 顺序:list-style-type list-style-position list-style-image(可省略某个值) |                    |



