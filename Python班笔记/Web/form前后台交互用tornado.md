## form前后台交互用tornado

```python
login.html文件 ，实现和demo.py的交互

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <form action="/login" method="post">
    <!--action是去向哪里-->
       <p><label for="user">用户名:</label> <input type="text" id="user" name="user" placeholder="请输入用户名"></p>
       <p><label for="password">密&emsp;码:</label> <input type="password" id="password" name="password" placeholder="请输入密码"></p>
        <p><input type="submit" value="登录"></p>
    </form>
</body>
</html>
```

```python
这里是demo.py文件

import tornado.ioloop
import tornado.web


class MainHandler(tornado.web.RequestHandler):
    def get(self):
        # self.write("漫漫长夜，cheergo")
        self.render('login.html')

    def post(self):
        print(self.get_argument('user'))
        print(self.get_argument('password'))
        user = self.get_argument('user')
        password = self.get_argument('password')
        self.write('登陆成功')


if __name__ == "__main__":
    application = tornado.web.Application([
        (r"/login", MainHandler),
    ])
    application.listen(8888)
    tornado.ioloop.IOLoop.current().start()



```