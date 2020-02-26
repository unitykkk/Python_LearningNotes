## JS一

### js获取元素对象

```python
常用的调试方法

<script>
    alert('我爱你，大哥王');
    console.log('普尼阿姆')
</script>
```

```python
外部文件应用，在外部写了一个js的文件，js的文件就不用写script了

<script src="./first.js"> </script>

可以存放的两个位置，一个放在head里面，一个放在body标签结束之前。
推荐使用body标签结束前，等内容加载完就可以用。
因为放在head里面，body里面的内容还没加载。

如果非要写在head里面
<script>
        window.onload = function () {
            var test = document.getElementsByClassName('box')[0];
            test.innerHTML = '奇怪的上单';
        }
</script>
```

#### 获取元素对象

```python
通过标签名，class名获取，想获取某个，加上索引就可以
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <div class="box" id="box1">我很好</div>
    <div class="test">婷婷</div>
    <script src="zz.js"></script>
</body>
</html>

这个是zz.js里的代码
obj这里获得的是一个列表，所以通过索引获取
var obj = document.getElementsByClassName('box')[0];
obj.onclick = function () {
    alert('心态崩了');
};

var obj1 = document.getElementsByTagName('div')[1];
obj1.onclick = function () {
    console.log('五月天');
};

分清TagName和Name的区别，TagName是标签名，Name是指的name属性，比如input框的name属性
他们获得也是一个列表，通过索引来噢！

常用一种 用css选择器来获取
querySelector只会取第一个找到的
querySelectorAll可以取到符合条件的所有

<p id="now"><input type="text" placeholder="请输入用户名" name="user"></p>
<script src="zz.js"></script>

zz.js下的文件
var obj2 = document.querySelector('#now>input');
obj2.onclick = function () {
    console.log('心态南宋')
};

var obj2 = document.querySelectorAll('#now>input')[0];
obj2.onclick = function () {
    console.log('心态南宋')
};
```

### js简单事件

```python
上面写了一点点击事件，可以参考
详情参考ppt，写的很详细
var obj = document.querySelector('#box');
obj.onclick = function () {
    obj.style['width'] = '400px';
    obj.innerText = '你被单机了'
};
obj.onmouseenter = function () {
  obj.innerText = '你被划入了';
};
obj.ondblclick = function () {
  obj.innerText = '你被双击了'
};


下拉框的样式

<div id="ss">
        <select name="select" id="select">
            <option value="cs">长沙</option>
            <option value="wh">武汉</option>
            <option value="hs">黄石</option>
        </select>
</div>

var obj1 = document.querySelector('#ss>select');
obj1.onchange = function () {
    console.log('下拉框改变了');
};

窗口发生变化时使用
window.onresize = function () {
  console.log('窗口发生改变');
};
```

### js修改样式

#### 修改样式

```python
Obj.style[变量]=变量值


<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        .box{
            width: 200px;
            height: 200px;
            border: 1px solid black;
            background-color: #4b1280;
        }
    </style>
</head>
<body>
    <div class="box">我很好，我爱你！</div>
    <script src="../change.js"></script>
</body>
</html>

// 利用传参的方式，修改样式
var a = 'background';
var b = 'red';
var obj = document.querySelector('.box');
obj.onclick = function () {
  obj.style[a] = b
};

// 多个样式修改
obj.style.cssText = 'width:400px;height:500px;background:yellow;';
记住，多个样式修改和单个只有一个能生效，不能放在一起写！

// 同样，cssText多个赋值的方式也可以通过传参来实现
var a = 'background';
var b = 'red';
var c = 'width';
var d = '600px';
var obj = document.querySelector('.box');
obj.onclick = function () {
    // obj.style[a] = b;
    // obj.style.cssText = 'width:400px;height:500px;background:yellow;';
    同样，cssText多个赋值的方式也可以通过传参来实现
    obj.style.cssText = a+':'+b+';'+c+':'+d;
};
```

### 属性操作

```python
强调一遍，一个标签除了本身标签名和尖括号以外其他都是属性，比如 input 标签里面，除了尖括号的input，其他的东西都是input的属性

html页面
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        .box{
            width: 200px;
            height: 200px;
            border: 1px solid black;
            background-color: #4c5bed;
        }
        .test{
            width: 800px;
            height: 200px;
            border: 1px solid black;
            background-color: #4c5bed;
        }
    </style>
</head>
<body>
    <div class="box"></div>
    <script src="../file/attr.js"></script>
</body>
</html>


js文件页面

var obj = document.querySelector('.box');
// 增
// 前面是属性名,后面是值,不要搞错了
obj.setAttribute('class', 'test');
// 自定义属性增加
obj.setAttribute('name', 'user');

// 删
// obj.removeAttribute('class');

// 改
// obj.className = 'test';
// 改也可以用这个
obj.setAttribute('name', 'lover');

// 查
// 判断
console.log(obj.hasAttribute('class')); //true //有这个属性返回true,没有返回false
console.log(obj.hasAttribute('zz'));  //false
```

### 数据类型

```python
详情参考ppt

var a 这种情况，声明了未赋值的话，就是undefined
```

### 自己完成的作业

```python
html页面

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <link rel="stylesheet" href="./作业.css">
</head>
<body>
    <p>属&emsp;性:<input type="text" placeholder="请输入css属性" name="v1"></p>
    <p>属性值:<input type="text" placeholder="请输入css的属性值" name="v2"></p>
    <input type="button" value="设置" class="box">
    <div class="box1">我就是我</div>
    <script src="./作业.js"></script>
</body>
</html>

css页面

.box{
    width:200px;
    height: 50px;
    background-color: black;
    color: whitesmoke;
    margin-bottom: 30px;
    border-radius: 10%;
    /*line-height: 30px;*/
    /*padding-left: 10px;*/
}
.box1{
    width:200px;
    height: 200px;
    background-color: #679bdd;
    color: black;
    border-radius: 10%;
    line-height: 200px;
}

js页面

var obj = document.querySelectorAll('input')[0];
var obj1 = document.querySelectorAll('input')[1];
var btn = document.querySelector('.box');
var div = document.querySelector('.box1');

btn.onclick = function () {
  var v1 = obj.value;
  var v2 = obj1.value;
  div.style.cssText = v1+':'+v2+';'
};
```
实现坦克大战的效果的时候请用backgroud来实现，background-position