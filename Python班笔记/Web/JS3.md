## JS3

### math对象

```python
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <script>
        // random和取整的三个方法
        // round：四舍五入， floor：向下取整，ceil：向上取整
        console.log(Math.ceil(1.2));  // 2
        console.log(Math.floor(1.2)); // 1
        console.log(Math.round(1.6)); // 2

        // 绝对值 abs
        console.log(Math.abs(-1));  // 1

        // random随机
        console.log(Math.random()); // 范围0-1取值
        // 随机数取整
        console.log(Math.round(Math.random()*10));  // 0-10
        console.log(parseInt(Math.random()*10)); // 0-10
    </script>
</body>
</html>
```

### 日期对象

```python
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <script>
        // 获取事件对象
        var time = new Date();
        // 当前时间
        console.log(time);
        // 转换时间戳
        console.log(time.getTime());
        // 年
        var year = time.getFullYear();
        // 月
        var month = time.getMonth();
        // 日
        var date = time.getDate();
        // 时
        var hour = time.getHours();
        // 分
        var min = time.getMinutes();
        // 秒
        var sec = time.getSeconds();
        // 完整输出
        console.log(year+'年'+month+'月'+date+'日'+hour+'时'+min+'分'+sec+'秒');
        // 页面输出
        // 这个是我自己写的
        // var body = document.querySelector('body');
        // body.innerHTML = year+'年'+month+'月'+date+'日'+hour+'时'+min+'分'+sec+'秒';

        // 老师写法
        document.body.innerText = year+'年'+（month+1)+'月'+date+'日'+hour+'时'+min+'分'+sec+'秒'
    </script>
</body>
</html>
```

### 定时器

```python
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <input type="button" name="btn" value="停止">
    <script>
        // setTimeout(),括号里带两个参数，第一个是函数，第二个是毫秒
        // setTimeout(function () {
        //     console.log('我爱你');
        // }, 1000);  // 过一秒后打印函数里的内容
        // setInterval()
        // setInterval(function () {
        //     console.log('大宝贝');
        // }, 1000); // 每隔一秒打印一次

        // 改造
        function f() {
            console.log('心态崩了');
        }
        // 清除定时器：1，定时器命名 2，清除
        var si = setInterval(f, 1000);
        // 清除,这是自己写的！！鼓励，注意获取标签的方法噢！如下
        // 一个input标签，有name="btn"的属性
        var btn = document.querySelectorAll('input[name="btn"]')[0];
        btn.onclick = function () {
            clearInterval(si);
        };
    </script>
</body>
</html>
```

### 函数

```python
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <script>
        // f就是函数名，{}里面就是功能块
        // 有名函数
        function f() {
            alert('ok')
        }
        // 函数调用，执行,在这里，放在函数前面也可以执行，和python不同！
        // python是调用放在函数后面才能执行！
        // f();

        // 匿名函数，加上(+,!,-,(),~)，括号前不取名字,想让他正常执行加上符号和结尾的()调用
        !function () {
            console.log('zzz')
        }();
        (function () {
           console.log('匿名')
        }());

        // 函数参数
        function sum(x,y,z) {
            var s = x+y+z+'呵呵';
            console.log(s);
            console.log('x:'+x+'y:'+y+'z:'+z);
        }
        // sum(1,2,3)
        // sum(1,2); // 缺一个参数被传参，这个参数就是undefined，得到的s就是NaN，
        // sum(1,2,3,4)  // 当多传一个，多的那个会被舍弃掉

        // 优化
        function arg() {
            console.log(arguments);  // arguments获得传进来的所有参数
            console.log(arguments.length);
            var s = 0;
            for (let i=0;i<arguments.length;i++){
                s += arguments[i];
            }
            console.log(s);
            return s;
        }
        y = arg(1,2);  // Arguments(2) [1, 2, callee: ƒ, Symbol(Symbol.iterator): ƒ]

        console.log('返回值：'+y);  // 返回值：undefined,如果在没有return的情况下！
        //  当有return的情况下，就显示return的这个值

        arg(1,2,3);  // Arguments(3) [1, 2, 3, callee: ƒ, Symbol(Symbol.iterator): ƒ]
        arg(1,2,3,4); // Arguments(4) [1, 2, 3, 4, callee: ƒ, Symbol(Symbol.iterator): ƒ]
    </script>
</body>
</html>
```

### 函数的作用域

```python
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <script>
        var a = 100;
        !function () {
            var a =200
        }();
        console.log(a);  // 100,注意，这里函数内的 var a 是声明并不是赋值

        var b = 100;
        !function () {
            b = 200;
        }();
        console.log(b);  // 200，这里就是赋值了！

        // 分析函数执行顺序
        function c() {
            console.log('hello')
        }
        c();
        function c() {
            console.log('world')
        }
        c();
        var c = function () {
            console.log('hi')
        };
        c(); // 上面的c是一个变量，他的值是一个函数,var的时候还未赋值！

        // function c ====> console.log('hello')
        // function c ====> console.log('world')
        // c ===> function c
        // 所以打印的两个world，因为顺序是先找函数，函数的调用无论放在前后都无所谓！

        // 外面var全局变量整个js生效，函数内var只有在这个函数内生效
    </script>
</body>
</html>
```

### 敌军战场

```python
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        .test{
            font-size: 30px;
            color: #9dfffd;
        }
    </style>
</head>
<body>
    <h3>敌军还有<span class="time" style="color: red;font-size: 30px">10</span>s到达战场</h3>
    <h3>现在是北京时间 <span class="date"></span> </h3>
    <script>
        // 实现倒计时
        var obj = document.querySelector('h3>.time');
        var time = obj.innerText;
        // console.log(time)
        function f() {
            // 实现时间的减少
            time = time-1;
            obj.innerText = time;
            if (time===0){
                clearInterval(si);
                document.querySelector('h3').innerText = '全军出击';
            }
        }
        var si = setInterval(f, 1000);
        // 实现现在时间
        function f1() {
            var date = new Date();
            year = date.getFullYear();
            month = date.getMonth() + 1;
            d = date.getDate();
            hour = date.getHours();
            min = date.getMinutes();
            sec = date.getSeconds();

            if (sec<10){
                sec = '0'+sec;
            }

            document.querySelector('.date').innerHTML = year+'<span class="test">年</span>'+ month +'<span class="test">月</span>'+ d +'<span class="test">日</span>'+ hour + '时' + min + '分' + sec + '秒';
        }
        f1();  // 这里要放出来，消除一秒的延迟
        var si2 = setInterval(f1, 1000);
    </script>
</body>
</html>
```

### 轮播图功能总共实现

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
            cursor: pointer;
        }
        .box:hover .right{
            display: block;
            cursor: pointer;
        }
       .box:hover .left{
            display: block;
            cursor: pointer;
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
        var n = 1; // 设定一个变量来控制左右箭头
        for (let i=0;i<btn.length;i++){
            btn[i].onclick = function () {
                for (let j=0;j<pic.length;j++){
                    if (i===j){
                        pic[j].setAttribute('class', 'show');
                        n = j;
                    }else {
                        pic[j].removeAttribute('class')
                    }
                }
            }
        }
        // 左右箭头
        var left = document.querySelector('.left');
        var right = document.querySelector('.right');
        left.onclick = function () {
            // console.log(n)
            pic[n].className = '';
            n = n-1;
            if (n<0){
                n = pic.length-1
            }
            pic[n].className = 'show';
        };
        right.onclick = function () {
            pic[n].className = '';
            n = n+1;
            if (n>pic.length-1){
                n = 0
            }
            pic[n].className = 'show';
        };
        // 自动轮播,原理就是每隔一段时间点一下右箭头
        function auto() {
            pic[n].className = '';
            n = n+1;
            if (n>pic.length-1){
                n = 0
            }
            pic[n].className = 'show'
        }
        var timer = setInterval(auto, 1000);
        // 当鼠标划入悬停,退出恢复！
        // onmouseenter进入，onmouseleave退出
        var box = document.querySelector('.box');
        box.onmouseenter = function () {
            clearInterval(timer);
        };
        box.onmouseleave = function () {
            timer=setInterval(auto, 1000);
        };
    </script>
</body>
</html>
```

### iframe

```python
一般局部刷新都不用iframe，不够安全，src很容易被修改，一般都用ajax

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <!--src是表单的页面-->
    <iframe src="./form.html" style="width: 800px;height: 800px">

    </iframe>
    <div>这是我之际</div>
</body>
</html>
```