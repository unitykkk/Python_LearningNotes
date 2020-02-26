## HTML标签

### 1，常用标签

#### 块级标签

```python
独占一行
标题标签 h1-h6
段落标签 p 

无序列表
<ul>
    <li>苹果</li>
    <li>梨子</li>
    <li>香蕉</li>
</ul>
有序列表
<ol>
    <li>平爬取</li>
    <li>打篮球</li>
    <li>游泳</li>
</ol>
自定义列表
<dl>
    <dt>湖北</dt>
    <dd>武汉</dd>
    <dd>黄石</dd>
    <dt>湖南</dt>
    <dd>长沙</dd>
    <dd>岳阳</dd>
</dl>
```

```python
div标签：页面布局
div本身是没有样式的

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>div布局</title>
    <style>
        #top{
            height: 64px;
            background-color: #212121;
        }
        #content{
            height: 800px;
            background-color: #4b1280;
        }
        #bottom{
            height: 128px;
            background-color: #4c5bed;
        }
    </style>
</head>
<body>
    <div id="top">top</div>
    <div id="content">content</div>
    <div id="bottom">bottom</div>
</body>
</html>
```

```python
<div id="top">top <img src="./timg.jpg" alt="下载失败" title="提示文本"></div>
src是图片路径，alt是图片路径错误时的显示，title是鼠标放在图片上显示的文字
```

#### 行内标签

```python
在一行
i标签，a标签，b标签，input标签
```

```python
<a href="https://www.baidu.com" target="_top" title="鼠标滑过显示">百度一下</a>
target是关于窗口的消失还是存在。。

<p><a href="#first" title="第一章">第一章</a></p>
<p><a href="#second" title="第二章">第二章</a></p>
  这里href里面给的参数是锚点，对应的id或者class，跳到指定的地方，比如有一个图片或者段落的id为first，点击第一章就会跳转过去

<a href="#"><h1 id="second">第二章</h1></a>  这里href设置的 # 锚点可以跳回顶部    

 <a href="javascript:void (0)">我想要a标签的样式，但是不想让他跳转</a>
    像要a标签的样式但是不想让他跳转，在href加上"javascript:void (0)"就可以
```

```python
利用span标签实现样式的不同

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        span{
            color: red;
            font-size: 20px;
        }
    </style>
</head>
<body>
我就是我颜色 <span>不一样</span> 的烟火
</body>
</html>
```

### 2，特殊符号

```python
&lt 小于号 
&gt 大于号
&emsp; 一个字符的间隔
&nbsp; 一个空格的间距
```

### 3，表格标签

```python
这里table标签就是表格，一开始是没有样式的，也是要自己添加，thead是表头字段，tr和td是每一列的表，caption是表格标题。
table style="border-collapse: collapse" 就是把线连到一起
th,td{
    border: 1px solid red;
    width: 50px;
}
这个是利用css选择器来添加表格的样式

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>表格</title>
    <style>
        th,td{
            border: 1px solid red;
            width: 50px;
        }
    </style>
</head>
<body> <table style="border-collapse: collapse">
        <caption>学生表</caption>
        <thead>
        <tr>
            <th>姓名</th>
            <th>年纪</th>
            <th>体重</th>
        </tr>
        </thead>
        <tbody>
        <tr>
            <td>小名</td>
            <td></td>
            <td></td>
        </tr>
        <tr>
            <td>小红</td>
            <td></td>
            <td></td>
        </tr>
        <tr>
            <td>小蓝</td>
            <td></td>
            <td></td>
        </tr>
        </tbody>
    </table>
</body>
</html>
```

### 4，表单标签

```python
注意几点： 1，label的用法，加上for，相当于是锚点，把label放在比如 密码 那里：<p><label for="target">密&emsp;码:</label> <input id="target" type="password" placeholder="请输入密码" name="password"></p>，这样点击密码两个字就可以跳到密码输入那里了。
2，select 标签下面的，默认选中就是selected
3，textarea个人简介


<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <form action="https://www.baidu.com" method="get" enctype="multipart/form-data" >
        <p>用户名:<input type="text" placeholder="请输入用户名" name="user" value="霏霏"></p>
        <p><label for="target">密&emsp;码:</label> <input id="target" type="password" placeholder="请输入密码" name="password"></p>
        <p>性别<input type="radio" name="sex" value="1">男
               <input type="radio" name="sex" value="0">女
        </p>
        <p>爱好 <input type="checkbox" name="sing" value="sing">唱
                <input type="checkbox" name="dance" value="dance">跳
                <input type="checkbox" name="rap" value="rap">rap
        </p>
        <p>上传文件<input type="file" name="file" multiple="multiple"></p>
        <p>
            地&emsp;址<select name="add" id="sel">
            <optgroup label="湖南省">
                <option value="">岳阳</option>
                <option value="">长沙</option>
                <option value="">常德</option>
            </optgroup>
            <optgroup label="湖北">
                <option value="wh" selected>武汉</option>
                <option value="hg">黄冈</option>
                <option value="hs">黄石</option>
            </optgroup>
                      </select>
        </p>
        <p>
            个人简介: <textarea name="profile" id="profile" cols="30" rows="10" placeholder="请输入个人信息"></textarea>
        </p>
               <p><input type="submit" value="提交">
            <input type="reset" value="重置">
        </p>
    </form>
</body>
</html>
```