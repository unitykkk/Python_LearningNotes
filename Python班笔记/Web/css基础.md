## css基础

### 1，css导入方式

```python
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        p{
            background-color: red;
        }
    </style>
    <link rel="stylesheet" href="./css.css">
</head>
<body>
    <p>第一种css导入方式:head里的style标签</p>
    <div style="color: #4c5bed">第二种css导入方式:通过标签里的style属性</div>
    <h3>第三种css导入方式:通过link导入</h3>
</body>
</html>

如果一个标签连接了link，style还有标签里的，顺序是谁离得最近最大！
```

### 2，css选择器

```python
Id选择器 > class 选择器 > 元素选择器
Id选择器：100 > class 选择器：10 > 元素选择器：1


<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        /*标签选择器*/
        /*p{*/
            /*font-size: 22px;*/
            /*color: #4b1280;*/
        /*}*/
        /*class选择器，加个小.*/
        .p1{
            font-size: 30px;
        }
        /*id选择器加个#*/
        #p1{
            font-size: 50px;
        }
        /*子代选择器,只选儿子*/
        .box>span{
            background-color: #4c5bed;
        }
        /*后代选择器，参照点下的都有属性*/
        .box span{
            font-size: 30px;
            background-color: red;
        }
        /*兄弟选择器*/
        .box2{
            width: 20px;
            height: 20px;
            background-color: #212121;
        }
        .box2~p{
            color: red;
        }
        /*相邻选择器*/
        .box2+p{
            color: seagreen;
        }
        /*全选择器*/
        *{
            font-family: 幼圆;
        }
        /*属性选择器,比如说有一个标签有自定义的属性self_add,
        我们通过这个属性来选定这个标签来添加样式，本身有的也可以用，
        比如name，value，label*/
        div[self_add='test']{
            font-size: 60px;
            font-family: 华文新魏;
            color: slateblue;
        }
        /*分组选择器,解决代码冗余，相同的样式的话用逗号隔开*/
        .box4,.box5{
            height: 200px;
            width: 200px;
            background-color: red;
        }
    </style>
</head>
<body>
<!--基本选择器：标签选择器，class选择器，id选择器-->
    <p class="p1" id="p1">会不会</p>
<!--后代选择器，子代选择器-->
    <div class="box">
        <span>鹅鹅鹅，</span>
        <p>曲 <span>项向天歌</span> </p>
    </div>
<!--兄弟选择器选不到哥哥，只选得到下面的同级的，相邻选择器,只能选下面的第一个同级的，-->
    <p>兄长：我就是我颜色不一样的烟火</p>
    <div class="box2"></div>
    <p>弟弟：白毛浮绿水</p>
    <p>弟弟：红掌拨清波</p>
<!--全选择器 用*选择全部标签 -->
<!--属性选择器-->
    <div class="box3" self_add="test">
        我是属性选择器
    </div>
<!--分组选择器-->
    <div class="box4"></div>
    <p class="box5"></p>
</body>
</html>
```

### 3，文字样式

```python
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        div{
            /*font-family:字体，谷歌浏览器默认微软雅黑，可以同时设置多个字体
             相当于找备胎，以放有的浏览器没有对应字体;*/
            font-family: 华文琥珀, 华文行楷, 华文彩云;

            /*font-size:字体大小,单位px rem % em。谷歌默认大小16px，可识别最小12px
            rem：相当于16px的n次倍数，em：父级标签字体*n
            %：父级字体*%
            ;*/
            font-size: 30px;

            /*font-weight:字体粗细
            如果要给值：100-900的整百数
            400是正常粗细，700=bold;*/
            font-weight: 400;

            /*font-style:文字样式*/
            font-style: italic;

            /*color 文字颜色*/
            /*第一种给指定颜色*/
            /*color: seagreen;*/
            /*第二种给指定16进制数字*/
            /*color: #2E8B57;*/
            /*第三种rgb*/
            color: rgb(46, 139, 87);
            /*第四种透明度rgba, 范围从0-1，0是完全透明，1是不变*/
            color: rgba(46, 139, 87, 0.1);
        }
        div>span{
            font-size: 2em;
        }
    </style>
</head>
<body>
    <div>测 <span>试</span>对象</div>
</body>
</html>

font的综合写法，size和family是必写项
可以按顺序设置如下属性：

font-style （使用斜体、倾斜或正常字体）
font-variant （设置小型大写字母的字体显示文本）
font-weight （设置文本的粗细）
font-size/line-height （设置字体的尺寸和行高）
font-family （规定元素的字体系列）
可以不设置其中的某个值，比如 font:100% verdana; 也是允许的。未设置的属性会使用其默认值。

如：

body{ font: italic small-caps bold 14px/24px "microsoft yahei";}

字体：斜体 小型大写字母 粗体 14号大小/24像素行高 微软雅黑

可以不需要每个都写，但是顺序还是要的
```

### 4，文本样式

```python
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        p{
            /*首行缩进*/
            text-indent: 2em;
            /*行高*/
            line-height: 32px;
        }
        div{
            height: 200px;
            width: 800px;
            border: 2px solid red;
            /*文字上下居中line-height，值等于高度*/
            line-height: 200px;
            /*文字左右居中*/
            text-align: center;
            /*文本大小写操作,capitalize是首字母大写*/
            text-transform: capitalize;
        }
        a{
            /*去掉a标签的下划线*/
            /*text-decoration: none;*/
            /*删除线*/
            /*text-decoration: line-through;*/
            /*上划线*/
            /*text-decoration: overline;*/
            /*下划线*/
            text-decoration: underline;
        }
        .box{
            /*换行方式是：不换行*/
            white-space: nowrap;
            /*超出部分隐藏*/
            overflow: hidden;
            /*超出部分省略*/
            text-overflow: ellipsis;
        }
    </style>
</head>
<body>
    <div class="box">我就是我颜色不一样的烟火我就是我颜色不一样的烟火我就是我颜色不一样的烟火
我就是我颜色不一样的烟火我就是我颜色不一样的烟火我就是我颜色不一样的烟火我就是我颜色不一样的烟火我就是我颜色不一样的烟火我就是我颜色不一样的烟火
我就是我颜色不一样的烟火我就是我颜色不一样的烟火我就是我颜色不一样的烟火我就是我颜色不一样的烟火</div>
    <div>文字居中,hello world,HELLO TZ!</div>
    <p>我就是我颜色不一样的烟火我就是我颜色不一样的烟火我就是我颜色不一样的烟火
我就是我颜色不一样的烟火我就是我颜色不一样的烟火我就是我颜色不一样的烟火我就是我颜色不一样的烟火我就是我颜色不一样的烟火我就是我颜色不一样的烟火
我就是我颜色不一样的烟火我就是我颜色不一样的烟火我就是我颜色不一样的烟火我就是我颜色不一样的烟火我就是我颜色不一样的烟火我就是我颜色不一样的烟火
        我就是我颜色不一样的烟火我就是我颜色不一样的烟火我就是我颜色不一样的烟火我就是我颜色不一样的烟火我就是我颜色不一样的烟火我就是我颜色不一样的烟火
        我就是我颜色不一样的烟火我就是我颜色不一样的烟火我就是我颜色不一样的烟火我就是我颜色不一样的烟火我就是我颜色不一样的烟火我就是我颜色不一样的烟火
        我就是我颜色不一样的烟火我就是我颜色不一样的烟火我就是我颜色不一样的烟火我就是我颜色不一样的烟火我就是我颜色不一样的烟火我就是我颜色不一样的烟火
        我就是我颜色不一样的烟火我就是我颜色不一样的烟火我就是我颜色不一样的烟火我就是我颜色不一样的烟火我就是我颜色不一样的烟火我就是我颜色不一样的烟火
        我就是我颜色不一样的烟火我就是我颜色不一样的烟火我就是我颜色不一样的烟火我就是我颜色不一样的烟火我就是我颜色不一样的烟火我就是我颜色不一样的烟火
    </p>
    <a href="javascript:void (0)">我是a标签</a>
</body>
</html>
```

### 5，伪类选择器

```python
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        /*未访问的状态*/
        a:link{
            color: red;
        }
        /*访问过的状态*/
        a:visited{
            color: #0f133d;
        }
        /*划过的状态*/
        a:hover{
            font-size: 50px;
            font-family: 华文行楷;
        }
        /*鼠标按着不动的状态*/
        a:active{
            color: yellow;
        }
        div{
            width: 200px;
            height: 200px;
            background-color: #4c5bed;.
        }
        /*鼠标划入div显示的样式*/
        div:hover{
            background-color: red;
            width: 100px;
        }
        /*都是通用的*/
        div:active{
            background-color: blue;
        }
    </style>
</head>
<body>
    <a href="https://www.baidu.com" >我爱你</a>
    <div>我是div标签</div>
</body>
</html>
```

### 6，背景样式

```python
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        .box{
            width: 1000px;
            height: 1000px;
            border: 1px solid darkred;
            /*背景色*/
            /*background-color: blue;*/

            /*背景图片*/
            /*background-image: url("./03.jpg");*/

            /*背景图片是否平铺*/
            /*background-repeat: no-repeat;*/

            /*背景图片大小，用参数或者单词cover，contain等来控制
            contain:图片可以全看见，但是不一定会铺满背景
            cover:背景会被铺满，但是图片不一定全看见*/
            /*background-size: 200px 100px;*/

            /*背景图片定位,参数顺序，x轴，y轴，以左上角为原点来移动*/
            /*background-position: 80px 40px;*/

            /*复合样式,顺序：color image repeat position/size，当不想给图片设定大小或者定位时
            又或是只设定大小或是定位时，用/来区分，在/前就是定位，在/后就是大小*/
            background:rgba(33, 44, 55, 0.7) url("./03.jpg") no-repeat top/300px 300px ;
        }
    </style>
</head>
<body>
    <div class="box"></div>
</body>
</html>
```
### 7，inline-block

```python
inline-block是什么
　　inline和block是css中元素display属性的两个选项，而inline-block可以说是介于两者之间的属性值。

inline使元素成为内联元素(inline elements)，而block则使之成为块级元素(block elements)。

inline元素里面只能放inline元素。 块级元素的特点是独占一行，并能设置width和height属性。

内联元素不会独占行，且设置width和height属性不产生效果。 padding和margin在水平方向的值有效，但在竖直方向无效。

inline-block会让元素像内联元素一样不换行，但里面的内容仍然是块级的。

.box2>span{
            font: 50px '华文新魏';
            display: inline-block;
            width: 300px;
            height: 300px;
            background: red;
        }
        .box3,.box2{
            display: inline-block;
        }

<div class="box2">
        <span>性感荷官</span>
    </div>
    <div class="box3">小宝宝</div>
```