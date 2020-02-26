## Django的概念

### 一，django到底是什么？

#### 1，django是一个web应用框架

#### 2，web应用框架：

互联网：是用来传递数据和信息的。

电网：传送电

#### 3，web应用

发电厂 ===== 应用程序（Nginx,apache）

本质就是程序

1，服务器程序

2，应用程序（我们需要去做的）

#### 4，应用程序

电器 ===== 应用程序

#### 5，WSGI（电源模块）

#### 6，web框架

web应用 ===== 造电器

web框架 ===== 基本原理

#### 7，电器有不同的品牌，web也是如此

1，django 全能型web框架

2， web.py 小巧的web框架

3，flask.py 一个轻量级的优秀的web框架，已停更

4，tornado一个异步的web框架

### 二，设计模式

#### 1，MTV

M: models模型：负责业务数据对象和数据库对象

T：template模板：把页面展示给用户，html文件

V：view视图：模型和模板的桥梁，py文件

#### 2，MVC

M: models模型：负责业务数据对象和数据库对象

V：view视图：与用户交互的页面

C：control控制器：模型和视图的桥梁，接收用户的输入。

### 三，django的介绍和环境搭建

```python
查看有哪些虚拟环境：workon
创建一个虚拟环境：mkvirtualenv -p /usr/bin/python3.6 DjangoApp（这个是自定义的名字，不要使用关键字）
退出虚拟环境：deactivate
删除虚拟环境：rmvirtualenv DjangoApp（已有的app名）
```

### 四，项目创建

```python
1，下载django：pip install django==2.1.7
2，cd到项目文件存放的文件夹名
3，选择和编辑器无关的通用方式来创建项目===》命令行：django-admin startproject CRM（自定义名称）
4，在有manage.py的文件夹下运行：python manage.py runserver 0.0.0.0:8888（后四位自定义）
```

### 五，配置pycharm的远程服务

1，在pycharm本地创建一个空项目

2，配置远程解释器（注意：必须和项目的解释器一致）

3，修改文件映射路径

4，设置自动同步

### 六，pycharm里的运行

