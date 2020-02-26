## json

```python
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <script>
        // json对象,json数据对象, 其实跟js就是格式不一样
        var user = {
            "name": "qzc",
            "age": 18,
            "sex": "male",
        };

        // js对象
        // var user = {
        //     name: 'qzc',
        //     age: 18,
        //     sex: 'male',
        // }

        // json读
        console.log(user.name);  // qzc
        // json写,直接改就可以
        user.name = 'feifei';
        console.log(user.name);
        // json遍历
        for (var key in user){
            console.log(key); // name age sex,得到的是属性名
            console.log(key+':'+user[key]);  // 这里不要想当然，要用[]来取值
        }
        // json转字符串
        var str = JSON.stringify(user);
        console.log(str, typeof str); // {"name":"feifei","age":18,"sex":"male"} string
        // 字符串转json
        var obj = JSON.parse(str);
        console.log(obj, typeof obj); // {name: "feifei", age: 18, sex: "male"} "object"
    </script>
</body>
</html>
```

