## css进阶

一个div必须要给他**设置宽高**，否则background写什么都没有用！！！！！

### 盒子模型

```python
margin:相当于包裹和包裹间隔开的距离，怕压损
padding:包裹内的东西和包裹间的填充物，例如泡沫，防止里面的物品损坏
border:包裹的材质厚度
content:里面的内容了，可以设置width，height
    
border部分
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        .box{
            width: 200px;
            height: 200px;
            /*border:1px solid red ;*/
            /*上下左右外边*/
            border-top: 10px solid greenyellow;
            border-right: 5px solid seagreen;
            border-left: 8px dotted indianred;
            border-bottom: 30px dashed purple;
            padding: 20px 20px;
        }
    </style>
</head>
<body>
    <div class="box">大闸蟹</div>
</body>
</html>

padding部分
注意，padding内边距会撑大盒子
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        .box{
            width: 200px;
            height: 200px;
            border: 1px solid red;
            /*padding如果只设置一个值就是四个内边距都一样
            如果两个值就是上下的和左右的*/
            padding: 25px;
            margin-bottom: 20px;
            /*display: inline-block;*/
        }
        .box2{
            width: 100px;
            height: 100px;
            border: 1px solid rebeccapurple;
            /*display: inline-block;*/
            margin-top: 30px;
        }
    </style>
</head>
<body>
    <div class="box">
        <div class="box3">
            很高兴相遇在这里
        </div>
    </div>
    <div class="box2">今天我不开心</div>
</body>
</html>

margin外边距，一定要有参照物噢！一定要设置border，因为只有找到border才能找到参照物，
两个盒子之间上下的距离不会相加，只会谁的距离大用谁的！左右会相加！
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        *{
            /*所有的都自动居中，上下0，左右自动*/
            margin: 20px auto;
        }
        div[class='box']{	这里用了一下属性选择器的技巧！！
            width: 200px;
            height: 200px;
            border: 1px solid red;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
            /*上外边距*/
            /*margin-top: 100px;*/
            /*左边外边距*/
            /*margin-left: 100px;*/
            /*右外边距*/
            /*margin-right: 100px;*/
            /*下外边距*/
            /*margin-bottom: 100px;*/
            margin: 0 auto;
        }
        div[class='box2']{
            width: 200px;
            height: 200px;
            border: 1px solid rebeccapurple;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }
    </style>
</head>
<body>
    <div class="box">
        仓央嘉措，法名罗桑仁钦仓央嘉措，清朝年间西藏著名的民歌诗人，是六世达赖喇嘛。康熙二十二年，他诞生于藏南一户信奉佛教的门巴族家庭，被选中为五世达赖的转世灵童。如果不是这转世灵童的身份，仓央嘉措是否只是芸芸众生中一位，又或者能与情人深情共白头，命运的安排我们不得而知
    </div>
    <div class="box2">
        既然是转世灵童，仓央嘉措从小就应该住进布达拉宫学习经文。但是五世达赖圆寂时，他的弟子桑杰嘉措封锁了消息，把持着权力。仓央嘉措和他的父母都不知情，生活还是依照原样，于是仓央嘉措在民间无忧无虑的度过了童年时光。直到康熙三十五年，康熙帝平定准噶尔叛乱，无意中发现了五世达赖已经圆寂了这事。抓来桑杰嘉措一问，这才去把转世灵童接进布达拉宫。因此，仓央嘉措得以度过无拘无束的童年，这14年的经历也给他后来的诗歌增添了不少灵感。
    </div>
</body>
</html>
```

### css重置

```python
/* http://meyerweb.com/eric/tools/css/reset/ 
   v2.0 | 20110126
   License: none (public domain)
*/

html, body, div, span, applet, object, iframe,
h1, h2, h3, h4, h5, h6, p, blockquote, pre,
a, abbr, acronym, address, big, cite, code,
del, dfn, em, img, ins, kbd, q, s, samp,
small, strike, strong, sub, sup, tt, var,
b, u, i, center,
dl, dt, dd, ol, ul, li,
fieldset, form, label, legend,
table, caption, tbody, tfoot, thead, tr, th, td,
article, aside, canvas, details, embed, 
figure, figcaption, footer, header, hgroup, 
menu, nav, output, ruby, section, summary,
time, mark, audio, video {
	margin: 0;
	padding: 0;
	border: 0;
	font-size: 100%;
	font: inherit;
	vertical-align: baseline;
}
/* HTML5 display-role reset for older browsers */
article, aside, details, figcaption, figure, 
footer, header, hgroup, menu, nav, section {
	display: block;
}
body {
	line-height: 1;
}
ol, ul {
	list-style: none;
}
blockquote, q {
	quotes: none;
}
blockquote:before, blockquote:after,
q:before, q:after {
	content: '';
	content: none;
}
table {
	border-collapse: collapse;
	border-spacing: 0;
}
```

### 浮动

```python
注意一下浮动带来的高度塌陷，用.clearfix::after{
            display: block;
            clear: both;
            content: "";
        }来解决，在父级的div里的class里加上clearfix就可以了

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        li{
            float: left;
            list-style: none;
            margin-right: 10px;
        }
        .box{
            border: 10px solid red;
        }
        .box div{
            height: 100px;
            width: 100px;
        }
        .left{
            background: #4c5bed;
            float: left;
        }
        .right{
            background: yellow;
            float: left;
        }
        .clearfix::after{
            display: block;
            clear: both;
            content: "";
        }
    </style>
</head>
<body>
    <!--浮动的应用，一列变一行-->
    <!--<ul>-->
        <!--<li>首页</li>-->
        <!--<li>课堂</li>-->
        <!--<li>搜索</li>-->
    <!--</ul>-->
    <!--浮动带来的高度塌陷-->
    <div class="box clearfix">
        <div class="left"></div>
        <div class="right"></div>
    </div>
</body>
</html>
```

### 定位

记住 父相子绝，一个布局大的div位置先固定，布局里的东西就用绝对定位来自己定义位置。

#### 1，固定定位

```python
固定定位是脱离文档流的，就是不占原来的位置

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        body{
            width: 5000px;
            height: 8000px;
        }
        div{
            position: fixed;
            width: 200px;
            height: 200px;
            background-color: #4c5bed;
            right: 0;
            bottom: 0;
        }
        p{
            margin: 20px;
        }
    </style>
</head>
<body>
    <div>
        <p>我是小广告</p>
    </div>
</body>
</html>
```

#### 2，相对定位

```python
相对定位是相对于自身来定位，没有脱离文档流，原来位置依然占位置

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        .box1{
            width: 200px;
            height: 200px;
            background-color: greenyellow;
            border: 1px solid black;
            position: relative;
            left: 200px;
            top: 200px;
        }
        .box2{
            width: 200px;
            height: 200px;
            background-color: #4b1280;
            border: 1px solid black;
        }
    </style>
</head>
<body>
    <div class="box1">物体</div>
    <div class="box2">参照物</div>
</body>
</html>
```

#### 3，绝对定位

```python
绝对定位脱离文档流，相对于父级当作参照物，不占位置

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        div[class='box1']{
            position: absolute;
            width: 200px;
            height: 200px;
            border: 1px solid black;
            left: 50px;
        }
        .box2,.box3{
            width: 200px;
            height: 200px;
            background-color: greenyellow;
            border: 1px solid black;
            position: absolute;
        }
    </style>
</head>
<body>
    <div class="box1"></div>
    <div class="box2"></div>
    <div class="box3"></div>
</body>
</html>
```

#### 4，父相子绝

```python
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        .parent{
            height: 800px;
            width: 400px;
            border: 1px solid black;
            position: relative;
            left: 500px;
        }
        .child{
            height: 200px;
            width: 200px;
            background-color: #679bdd;
            border: 1px solid black;
            position: absolute;
            top: 20px;
            left: 50px;
        }
        .son{
            width: 200px;
            height: 200px;
            border-radius: 50%;
            background-color: red;
            position: absolute;
            top: 50px;
            left: 300px;
        }
        .z{
            position: absolute;
            width: 50px;
            height: 50px;
            background-color: greenyellow;
            left: 50%;
            top: 50%;
            margin-top: -25px;
            margin-left: -25px;
        }
    </style>
</head>
<body>
    <div class="parent">
        <div class="child"></div>
        <div class="son"></div>
        <div class="z"></div>
    </div>
</body>
</html>
```

### 自己写的轮播图样式

```python
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
       .box{
           position: relative;
           margin: 0 auto;
           width: 800px;
           height: 400px;
           border: 1px solid black;
       }
       .left{
           float: left;
           font-size: 50px;
           position: absolute;
           top: 50%;
           margin-top: -40px;
           z-index: 100;
       }
       .right{
           float: right;
           font-size: 50px;
           position: absolute;
           right: 0;
           top: 50%;
           margin-top: -40px;
           z-index: 100;
       }
        .p1{
            width: 800px;
            height: 400px;
            background-image: url("2.jpg");
            background-size: 800px 400px;
            position: absolute;
            z-index: 10;
        }
        .p2{
            width: 800px;
            height: 400px;
            background-size: 800px 400px;
            background-image: url("./03.jpg");
            position: absolute;
            z-index: 2;
        }
        .p3{
            width: 800px;
            height: 400px;
            background-size: 800px 400px;
            background-image: url("timg.jpg");
            position: absolute;
        }
        .p4{
            width: 800px;
            height: 400px;
            background-size: 800px 400px;
            background-image: url("tim1.jpg");
            position: absolute;
            z-index: 20;
        }
        ul>li{
            list-style: none;
            height: 10px;
            width: 10px;
            border: 1px solid black;
            border-radius: 50%;
            z-index: 100;
            float: left;
            margin-right: 20px;
        }
        .bad{
            width: 800px;
            height: 50px;
            position: absolute;
            bottom: 0;
            left: 50%;
            margin-left: -100px;
            z-index: 100;
        }
    </style>
</head>
<body>
    <div class="box">
        <div class="p1"></div>
        <div class="p2"></div>
        <div class="p3"></div>
        <div class="p4"></div>
        <div class="left">&lt;</div>
        <div class="right"> &gt;</div>
        <div class="bad">
            <ul>
                <li></li>
                <li></li>
                <li></li>
                <li></li>
            </ul>
        </div>
    </div>
</body>
</html>
```