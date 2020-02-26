## ajax最后一点

```python
后台加减乘除！

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <input type="text" name="a">+
    <input type="text" name="b">=
    <input type="text" name="c">
    <input type="button" value="计算">
    <script src="https://cdn.bootcss.com/jquery/3.4.1/jquery.min.js"></script>
    <script>
        var $input = $("input");
        $input.eq(3).click(function () {
            var a = $input.eq(0).val();  // 得到的是字符串
            var b = $input.eq(1).val();
            // 用ajax+json实现数据的传递,格式($.ajax(json数据类型))
            $.ajax({
                "type": "post",  // 提交类型
                'url': '/sad',
                "data": {
                    "a": a,
                    "b": b,
                },
                'success': function (data) {  // 接收数据成功时使用的函数，data是用来接收后台传过来的数据的
                    $input.eq(2).val(data['result'])  // 利用字典的取值方式，val直接在括号里加数据
                },
                'error': function () {  // 错误时触发

                },
            });
        });
    </script>
</body>
</html>
```

```python
后台实现，在这里我总会遇到 TypeError: initialize() missing 1 required positional argument: 'url'这个错误，不懂为什么？？？
解决了，是tornado.web.RequestHandler！！！！！ 写在类里

import tornado.ioloop
import tornado.web


class MainHandler(tornado.web.RequestHandler):
    def get(self):
        # self.write("漫漫长夜，cheergo")
        self.render('login.html')

    def post(self):
        print(self.get_argument('user'))
        print(self.get_argument('password'))
        self.write('登陆成功')


class Json_Handler(tornado.web.RequestHandler):
    def get(self):
        self.render('test.html')

    def post(self):
        a = self.get_argument('a')
        b = self.get_argument('b')
        c = float(a)+float(b)
        data = {'result': c}
        self.write(data)
        print(c)


if __name__ == "__main__":
    application = tornado.web.Application([
        (r"/login", MainHandler),
        (r"/sad", Json_Handler),
    ])
    application.listen(8888)
    tornado.ioloop.IOLoop.current().start()
```