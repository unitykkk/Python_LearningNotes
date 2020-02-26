### CSS基础—背景

```html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        #div1{
            width: 400px;
            height: 200px;
            background-color: aquamarine;
            background-image: url("a.jpg");
            /*平铺*/
            background-repeat: no-repeat;
            /*背景定位*/
            background-position:center;
            /*背景图片大小*/
            /*background-size:400px 200px;*/
            /*渐变颜色*/
            /*background-image: linear-gradient(red,gray);*/
            /*左侧渐变 从右到左*/
            /*background-image: linear-gradient(to left,red,gray);*/
            /*从左上角到右下角*/
            /*background-image: linear-gradient(to bottom right,red,gray);*/

        }
    </style>
</head>
<body>
<div id="div1"></div>
</body>
</html>
```

