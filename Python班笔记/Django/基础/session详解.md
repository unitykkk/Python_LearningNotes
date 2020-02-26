## session详解

```python
def login(request):
    if request.method == 'POST':
        username = request.POST['username']
        password = request.POST.get('password')
        if username == 'fei' and password == 'fei':
            request.session['username'] = username  注意此处request.session['username']里面的username是自己设定的，所以之后用到校验的名字也是这个，不要犯错
            # request.session.set_expiry(5)  # 设置过期时间
            return redirect('student:demo')
    return render(request, 'student/login.html')


def demo(request):  渲染的页面
    username = request.session.get('username', default='游客')  这里的request.session得到的就是上面login传进来的，所以说设定的什么就写什么，默认值是必须要写的，为了实现退出的状态
    return render(request, 'student/demo.html', context={
        'username': username,
    })


def logout(request):  退出的页面
    request.session.flush()  清除session_id，所以就变成退出状态，实现登入登出
    return redirect('student:demo')
```

```python
这里是渲染的demo页面，也就是登录后的界面
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    {{ username }}访问  # 灵活的从后台传入的数据，后台得到的也就是我们输入的
    {% if request.session.username %}  # 使用if判断来实现登录和退出的效果，如果有这个username，显示的就是退出。这里的username也是我们最一开始在login里设定的，一定要注意。
        <a href="{% url 'student:logout' %}">退出</a>
    {% else %}  没有username就是登录
        <a href="{% url 'student:login' %}">登录</a>
    {% endif %}

</body>
</html>
```
```python
login的界面，注意一点 每个后台要用到的标签带上name和value
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>登录</title>
</head>
<body>
<form action="" method="post">
    {% csrf_token %}
    <p><input type="text" placeholder="请输入用户名" name="username"></p>
    <p><input type="password" placeholder="请输入密码" name="password"></p>
    <p><input type="submit" value="提交"></p>
</form>
</body>
</html>
```