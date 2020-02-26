```django
1，python manage.py startapp teacher(app名) 在终端创建一个app
```

![url路径](E:\BaiduYunDownload\笔记\框架笔记\url路径.png)

协议     域名（ip地址和端口）    路径     参数（从前台传入到后台）

url路径



路由系统（url.py）:

url配置   urlconf    python 模块 >>> 是url到视图函数的映射

```python
1,path(route,view,kwargs=None,name=None)
@route：字符串，url的路径
@view：视图
@kwargs：额外参数，字典
@name：
2，通过<>捕获url中的参数
@路径转换器<转换器:参数名>
@str匹配除了‘/’以外的非空字符，默认的
@int匹配整数
@uuid
3，re_path(route,view,kwargs=None,name=None)
命名正则表达式的语法：(?P<组名>正则表达式)
正常用正则分组例举就是用()
```

正则匹配的例子：

![正则匹配例子年月份](E:\BaiduYunDownload\笔记\框架笔记\正则匹配例子年月份.png)

```python
route可以传多个参数，用任意字符隔开，我一般用/
例子如下：
path('index/<int:year>/<int:mouth>/', views.index)

参数必须传，可以在视图函数中不用，但是必须传进去，跟python一样，必备参数。
```

额外参数kwargs的例子：

![kwargs1](E:\BaiduYunDownload\笔记\框架笔记\kwargs1.png)

![kwargs2](E:\BaiduYunDownload\笔记\框架笔记\kwargs2.png)

