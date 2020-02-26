## js二

### js操作符

```python
算术运算符有 ：+  、-  、 *  、 /  、 %、++、--
赋值运算符有： = 、+=、-=、 *=、/=、
比较运算符有: >、>=、<、<=、==、===（全等）
逻辑运算符有：&&（与）、||（或）、! （非）

提醒：数字加字符串是拼接，其他的减乘除都是正常的

ppt上有详细的运算操作！！！

var n = 5;
console.log(n++);  // 先返回n的值再 n = n + 1
console.log(n);

console.log(++n);  // 直接返回n += 1的值
console.log(n);
自减的原理一样的

逻辑运算符 && 与，有假就停，返回假的值
a&&b 如果a的值可以转化为false就返回a的值，如果不行就返回b的值
console.log(1&&0&&undefined);  // 0
console.log(1&&2&&undefined);  // undefined

|| 或，有真就停，返回真的值
console.log(10||0||false); // 10

! 非，取反！

重点注意：
遇到||运算符，先去左边的表达式得出结果，如果结果为true，则不会去执行右边的表达式，则短路运算生效；如果结果为false，则去执行右边的表达式，再去根据两边的结果去执行||运算
```

### 控制流程

```python
var name = '呵呵';
if (name==='小哥哥'){
    console.log(name+'真帅')
}else if (name==='朦胧'){
    console.log(name+'美丽')
}else {
    console.log('你是谁')
}

// 三目运算
if (name) console.log(name+'不好');

适用于if else
name === '呵呵'?console.log('存在'):console.log('不存在');
    
switch的用法，用于判断
var name = '邱子宸';
switch (name){
    case '朦胧':
        console.log('好漂亮');
        break;
    case '邱子宸':
        console.log('好帅气');
        break;
    default :  来自灵魂的拷问，如果都不符合就执行这里
        console.log('你是谁');
        break
}
```

### 循环

```python
跟python其实大同小异
for (var i =0;i<5;i++){
    if (i===3) continue;
    console.log(i);
}

九九乘法表原理
for (var i=1;i<10;i++){
    for (var j=1;j<i+1;j++){
        console.log(i+'*'+j+'='+i*j)
    }
}

利用for循环操作小圆点，这里定义用let，因为函数作用域的问题。
let是块级作用域，var是单独用于一个函数
var btn = document.querySelectorAll('ul>li');
for (let i=0;i<btn.length;i++){
    btn[i].onclick = function () {
        console.log(i+1)
    }
}

// while循环，一定要给自增
var i = 0;
while (i<10){
    console.log(i);
    i++;  自增
}
区别在于 do会先执行再看条件，而while是先看条件再执行
// do while循环
var i =0;
do {
    console.log(i);
    i++;
}while (i<=10);
```

### 字符串方法

```python
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <script>
        var str = 'wo xue guo python';
        // 空格也是一个字符长度
        console.log(str.length); // 17
        // 通过索引取值
        console.log(str[1]);
        // 字符串可读不可写噢！
        // 通过值取索引,后面跟的是从什么位置开始取起，如果取的到就返回索引值，取不到就返回-1
        console.log(str.indexOf('w')); // 0
        console.log((str.indexOf('o', 3)), 'zzzzz');
        // 修改，并不是真正的修改，只是在这里被修改，原值没变
        console.log(str.replace('wo', 'zz'));

        // split切割,引号中间没距离就是单个字符切割
        console.log(str.split(' '), '空格切割'); //
        console.log(str.split('w')); // ["", "o xue guo python"]

        // 切片: substring, slice
        // substring,从下标开始切,包前不包后,如果有负数就变0
        console.log(str.substring(0, 6));  // wo xue
        console.log(str.substring(-1, 6)); // wo xue
        console.log(str.substring(6, -2), 'hahah');  // 这个是0，6，记住
        // 截取当前位置到末尾
        console.log(str.substring(6), '末尾');  // 从下标6截取到末尾
        // slice,这个就跟python一样切
        console.log(str.slice(-1, -1)); // 取不到
        // 单参数也是截取当前位置到末尾
        console.log(str.slice(6))
    </script>
</body>
</html>
```
### 轮播图点击样式

```python
此处我犯了一个错误，在无序列表的状态下，图片的选中不能用 >li,而是>img,要中图片标签。
在图片的标签选择情况下用后代选择器 .img img，我也很奇怪为什么不能用子代选择器。
突然我想明白了，img标签是在li标签里的，所以就要用后代，用子代只能选到li

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        ul{
            margin: 0;
            padding: 0;
            list-style: none;
        }
        .img{
            width: 800px;
            height: 400px;
        }
        img{
            width: 800px;
            height: 400px;
            float: left;
            position: absolute;
        }
        .btn>li{
            border: 1px solid black;
            border-radius: 50%;
            height: 20px;
            width: 20px;
            float: left;
            /*position: absolute;*/
            background: red;
            margin-left: 20px;
        }
        .btn{
            width: 200px;
            height: 50px;
        }
    </style>
</head>
<body>
    <ul class="btn">
        <li></li>
        <li></li>
        <li></li>
        <li></li>
    </ul>
    <ul class="img">
        <li><img src="./2.jpg" alt=""></li>
        <li><img src="./03.jpg" alt=""></li>
        <li><img src="./timg.jpg" alt=""></li>
        <li><img src="./tim1.jpg" alt=""></li>
    </ul>
    <script>
        var btn = document.querySelectorAll('.btn li');
        var pic = document.querySelectorAll('.img img');
        for (let i=0;i<btn.length;i++){
            btn[i].onclick = function () {
                for (let j=0;j<pic.length;j++){
                    if (i===j){
                        pic[j].style.zIndex = '10';
                        console.log('fuck')
                    }else {
                        pic[j].style.zIndex = '0'
                    }
                }
            }
        }
    </script>
</body>
</html>
```

```python
自己写用classname的方式，有两种方法，一种使用className，一种用setAttribute来改
还有使用伪类选择器来实现，鼠标划入的时才显示小圆点和箭头，display:block, 放在hover放在整体盒子后面，例如 .box:hover .bad,
有一点发现，左右箭头不能用分组选择器实现，只能一个个写，比如
.box:hover .right{
            display: block;
        }
.box:hover .left{
        display: block;
    }
发现一点，只能用箭头的父类盒子来控制哦，相邻的格子是不可以的！！！            
cursor: pointer;这个属性实现划入变成小手指            

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
           display: none;
       }
       .right{
           float: right;
           font-size: 50px;
           position: absolute;
           right: 0;
           top: 50%;
           margin-top: -40px;
           z-index: 100;
           display: none;
       }
        #box img{
            width: 800px;
            height: 400px;
            background-size: 800px 400px;
            position: absolute;
            display: none;
        }
        #box img.show{
            display: block;
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
            display: none;
        }
        .box:hover .bad{
            display: block;
        }
        .box:hover .right{
            display: block;
        }
       .box:hover .left{
            display: block;
        }
    </style>
</head>
<body>
    <div class="box">
        <div id="box">
            <div><img class="show" src="2.jpg" alt=""></div>
            <div><img src="03.jpg" alt=""></div>
            <div><img src="tim1.jpg" alt=""></div>
            <div><img src="timg.jpg" alt=""></div>
        </div>
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
    <script>
        var pic = document.querySelectorAll('#box img');
        var btn = document.querySelectorAll('.bad li');
        for (let i=0;i<btn.length;i++){
            btn[i].onclick = function () {
                for (let j=0;j<pic.length;j++){
                    if (i===j){
                        pic[j].setAttribute('class', 'show')
                    }else {
                        pic[j].removeAttribute('class')
                    }
                }
            }
        }
    </script>
</body>
</html>
```

### 数组

```python
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <script>
        // 数组的创建
        var a = [];
        var b = new Array();
        // 数组的操作方法
        var obj = [1, 2, 3, 4, 5];
        console.log(obj.length);  // 5
        // 添加 push,数组可读可写
        obj.push('a', 'b');
        console.log(obj);
        obj[0] = 33;
        console.log(obj);

        // 前面添加unshift
        obj.unshift('python');
        console.log(obj);
        // 移除,从尾部移除pop
        obj.pop();
        console.log(obj);
        // 从头部删除shift
        obj.shift();
        console.log(obj);
        //替换splice,传一个参数代表从0索引开始截取个数
        console.log(obj);  // [33, 2, 3, 4, 5, "a"]
        // obj.splice(1);
        // console.log(obj, 'zzz');
        // 传两个参数, 第一个代表开始删的位置，从当前位置开始往后删后面一个参数的个数，
        // 比如传a，b，就是从a索引位置开始，删除b个元素
        // obj.splice(2, 3);
        // console.log(obj, 'aaa');
        // 传三个参数a，b，c , 前面a和b正常的操作，把删掉的位置换成c,c可以是多个值
        obj.splice(2,2,6);
        console.log(obj);

        // 排序 sort() reverse() 通过ASCII来排的
        // ASCII码排序
        var a = [0, -5, -1, -3, 4, 6, 3];
        console.log(a.sort(), 'sort');
        console.log(a.reverse(), 'reverse');
        // 数学排序
        console.log(a.sort(function (x, y) {
            return x-y;  // 这样就表示由小到大来排序
        }));
        console.log(a.reverse(function (x, y) {
            return x+y;  // 这样就表示由大到小
        }));

        // join拼接
        var b = ['a','b','c','d'];
        console.log(b.join('+'));  // a+b+c+d
    </script>
</body>
</html>
```

### 补充方法

```python
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <script>
        // toString()
        var a = 123.456;
        b = a.toString();
        console.log(typeof b, b);  // string

        // toFixed()
        c = a.toFixed(); // 不加参数就去掉小数，传几就是保留几位
        console.log(typeof c, c); // string 123

        // parseInt() 转换成整数,如果整数部分遇到不是数字就停止
        console.log(parseInt(a)); // 123

        // parseFloat  保留小数，小数部分遇到不是数字就停止
        console.log(parseFloat(a));  //

        // Number 强制转换成数字类型
        var d = '123456.aa';
        console.log(typeof Number(d)); // number

        // isNaN() 判断是否不是一个number
        console.log(isNaN(d)) // true
    </script>
</body>
</html>
```