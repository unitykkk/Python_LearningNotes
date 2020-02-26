### HTML表单

```html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>表单</title>
</head>
<body>
<!--<form action="https://www.baidu.com/s" method="get" target="_blank">-->
    <!--<input type="text" placeholder="请输入你要查询的关键字" name="wd">-->
    <!--<input type="submit" value="搜索">-->
<!--</form>-->
<form>
    <!--文本域-->
    文本框：<input type="text"><br>
    <!--复选框-->
    <input type="checkbox">小天<br>
    <input type="checkbox">不找了<br>
    <input type="checkbox">魔鬼天才<br>
    <!--单选按钮-->
    <input type="radio">小强墙
    <input type="radio">鲸落
    <input type="radio">罗塔<br>

    <!--普通按钮-->
    <input type="button" value="普通按钮"> <br>
    <!--密码框-->
    <input type="password" placeholder="请输入密码"><br>
    <!--文件上传-->
    <input type="file"><br>
    <!--下拉框-->
    <select>
        <optgroup label="地区">
            <option>湖南</option>
            <option>湖北</option>
            <option>河南</option>
            <option>河北</option>
        </optgroup>
    </select><br>
    <!--多行文本域-->
    <textarea rows="10" cols="20"></textarea>

</form>

</body>
</html>
```