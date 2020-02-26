## 函数的作用域和匿名函数（pycharm）

### 匿名函数

```python
# lambda写完之后，后面默认是匿名函数
定义格式： lambda 参数:表达式
函数比较简单的情况下，就可以写成匿名函数的形式，增加代码的可读性
li = [1, 2, 3, 11, 22, 33, 44, 55]
a = list(filter(lambda x: x > 5, li))  # 匿名函数 lambda
print(a)

E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
[11, 22, 33, 44, 55]

Process finished with exit code 0

应用
g = lambda a: a > 60
print(g(5))
print(g(80))

E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
False
True

Process finished with exit code 0
案例二
def f1(a, b, func):
    c = func(a, b)
    return c


d = f1(22, 11, lambda a, b: a - b)
print(d)

E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
11

Process finished with exit code 0
案例二
def f1(a, b, func):
    c = func(a, b)
    return c


xx = eval(input('请输入一个匿名函数:'))
d = f1(22, 11, xx)
print(d)

E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
请输入一个匿名函数:lambda a, b:a/b
2.0

Process finished with exit code 0
```

### 函数作用域

命名空间就是对一个名字起作用的范围，当前空间有效

出了这个空间就无效

```python
函数里面可以取到外面的变量，但是修改不了
a = 100  # 全局变量
def func():
    a = 200  # 局部变量
    print(a)


func()
print(a)

E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
200
100

Process finished with exit code 0

如果需要修改全局变量，需要用到 global
a = 100
def func():
    global a   # 声明全局变量，我要修改了
    a = 200
    print(a)


func()
print(a)

E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
200
200

Process finished with exit code 0

函数嵌套里要改局部变量 nonlocal 
def func():
    a = 100
    def func2():
        nonlocal a   # 访问外层的变量
        a += 1
        return a
    return func2()


b = func()
print(b)

E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
101

Process finished with exit code 0
```

### 闭包

```python
内层函数用到了外层函数的变量，外层函数的返回值是内层函数的返回体
def test(num):
    def test_in(num_in):
        return num + num_in
    return test_in


a = test(100)
print(a(120))


E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
220

Process finished with exit code 0
```

### 递归

自己调用自己本身

```python
阶乘
i = 1
n = 1
while i <= 9:
    n = n*i
    i += 1
print(n)

E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
362880

Process finished with exit code 0
```

```python
递归用法
def func(num):
    if num > 1:
        return num*func(num-1)
    else:
        return num


a = func(5)
print(a)

E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
120

Process finished with exit code 0
```