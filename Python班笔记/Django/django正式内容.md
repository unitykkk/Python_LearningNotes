django正式内容

ip对应电脑，端口对应应用程序

```python
22：ssh远程登陆协议规定的默认监听端口
8000：django运行命令默认监听端口
mysql：3306
redis：6379
fiddler：8080
```

```python
1，当我们的kwargs中key与url捕获的key一致时，以kwargs为准
2，url命名name
3，包含其他URLconf ；include
实际开发中我们的视图都在app中，这是怎么访问app中的views呢？

4，总结：
@1，当一个请求过来时，django会查找根url配置，再找路由匹配规则
@2，如果这个路由规则对应的是include，去找这个include包含的url配置
@3，访问的url由你的路由规则来决定

app_name
不同的app都会用不同的名字
```
```python
虚拟环境不等于虚拟机，所以要分很多个虚拟环境来创建不同的项目。
避免冲突
```
```python
必备参数要在默认参数的左边！！记住！！别再犯错！
```