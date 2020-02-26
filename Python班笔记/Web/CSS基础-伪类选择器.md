### CSS基础-伪类选择器

```html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        /*未访问过的*/
        a:link{
            color: red;
        }
        /*访问过后的*/
        a:visited{
            color: gold;
        }
        /*鼠标划过*/
        a:hover{
            font-size: 30px;
        }
        /*激活状态的*/
        a:active{
            color: black;
        }

    </style>
</head>
<body>

<a href="https://www.baidu.com">百度一下</a>
<a href="作业.html">作业</a>
<a href="#">空链接</a>

</body>
</html>
```