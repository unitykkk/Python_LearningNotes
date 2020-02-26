## 函数基础和函数参数（pycharm种运行）

### 函数基础

函数的定义: 把独立的代码块写进函数里重复使用

函数本身不会执行，当找到调用的时候才会执行

函数的定义一定在函数调用的上面

```python
def func():    # 函数定义
    for i in range(10):
        print('我爱你')


func()    # 函数的调用

E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
我爱你
我爱你
我爱你
我爱你
我爱你
我爱你
我爱你
我爱你
我爱你
我爱你

Process finished with exit code 0

可以理解为封装，达到多次使用的效果。
```

```python
当不知道写什么的时候可以用pass跳过
def func():
    pass
```

```python
函数的返回值 return, 当代码执行到return时就结束，下面的代码不会执行！
选择执行的时候可以有多个return，但是最终只会执行一个return
def func():
    a = 1
    return a


b = func()
print(b)

E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
1

Process finished with exit code 0
```

```python
传参
def func(a, b):
    res = a - b
    return res


c = func(10, 5)
print(c)

E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
5

Process finished with exit code 0
```

```python
简单的案例
def func(a, b):
    return '身高差为%s' % (a - b)


while True:
    num1 = eval(input('请输入男生身高：'))
    if num1 == 200:
        break
    num2 = eval(input('请输入女生身高：'))
    c = func(num1, num2)
    print(c)
    
E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
请输入男生身高：180
请输入女生身高：160
身高差为20
请输入男生身高：200

Process finished with exit code 0
```

### 函数参数

参数可以接收任何对象，包括函数，元组，列表等

#### 必备参数

```python
写了几个参数就必须传几个参数
def func(a, b):
    print(a + b)


func(2, 3)

E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
5

Process finished with exit code 0
```

#### 默认参数

```python
没传参就用自己的，传参了就用传参的
def func(a, b=6):
    print(a + b)


func(2)

E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
8

Process finished with exit code 0
```

#### 不定长参数

```python
#*args可以接受多个值，以元组的形式接收,位置参数
def func(*args):
    print(args)


func(1, 2, 3)

E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
(1, 2, 3)

Process finished with exit code 0

# *kwargs，关键字参数
def func(**kwargs):
    print(kwargs)


func(a=1, b='aaa')

E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
{'a': 1, 'b': 'aaa'}

Process finished with exit code 0
```

### 内置函数

已经写好的一些函数，我们直接拿来用

```python
查看内置函数，大约72种
print(dir(__builtins__))

E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
['ArithmeticError', 'AssertionError', 'AttributeError', 'BaseException', 'BlockingIOError', 'BrokenPipeError', 'BufferError', 'BytesWarning', 'ChildProcessError', 'ConnectionAbortedError', 'ConnectionError', 'ConnectionRefusedError', 'ConnectionResetError', 'DeprecationWarning', 'EOFError', 'Ellipsis', 'EnvironmentError', 'Exception', 'False', 'FileExistsError', 'FileNotFoundError', 'FloatingPointError', 'FutureWarning', 'GeneratorExit', 'IOError', 'ImportError', 'ImportWarning', 'IndentationError', 'IndexError', 'InterruptedError', 'IsADirectoryError', 'KeyError', 'KeyboardInterrupt', 'LookupError', 'MemoryError', 'ModuleNotFoundError', 'NameError', 'None', 'NotADirectoryError', 'NotImplemented', 'NotImplementedError', 'OSError', 'OverflowError', 'PendingDeprecationWarning', 'PermissionError', 'ProcessLookupError', 'RecursionError', 'ReferenceError', 'ResourceWarning', 'RuntimeError', 'RuntimeWarning', 'StopAsyncIteration', 'StopIteration', 'SyntaxError', 'SyntaxWarning', 'SystemError', 'SystemExit', 'TabError', 'TimeoutError', 'True', 'TypeError', 'UnboundLocalError', 'UnicodeDecodeError', 'UnicodeEncodeError', 'UnicodeError', 'UnicodeTranslateError', 'UnicodeWarning', 'UserWarning', 'ValueError', 'Warning', 'WindowsError', 'ZeroDivisionError', '__build_class__', '__debug__', '__doc__', '__import__', '__loader__', '__name__', '__package__', '__spec__', 'abs', 'all', 'any', 'ascii', 'bin', 'bool', 'bytearray', 'bytes', 'callable', 'chr', 'classmethod', 'compile', 'complex', 'copyright', 'credits', 'delattr', 'dict', 'dir', 'divmod', 'enumerate', 'eval', 'exec', 'exit', 'filter', 'float', 'format', 'frozenset', 'getattr', 'globals', 'hasattr', 'hash', 'help', 'hex', 'id', 'input', 'int', 'isinstance', 'issubclass', 'iter', 'len', 'license', 'list', 'locals', 'map', 'max', 'memoryview', 'min', 'next', 'object', 'oct', 'open', 'ord', 'pow', 'print', 'property', 'quit', 'range', 'repr', 'reversed', 'round', 'set', 'setattr', 'slice', 'sorted', 'staticmethod', 'str', 'sum', 'super', 'tuple', 'type', 'vars', 'zip']

Process finished with exit code 0
```

```python
内置函数介绍
# len  计算长度
a = [1, 5, 7, 9, 8]
print(len(a))

E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
5

Process finished with exit code 0

# min 求元素的最小值
a = [1, 5, 7, 9, 8]
print(min(a))

E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
1

Process finished with exit code 0

# max 求最大值
a = [1, 5, 7, 9, 8]
print(max(a))

E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
9

Process finished with exit code 0

# sorted 排序
a = [1, 5, 7, 9, 8]
print(sorted(a))

E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
[1, 5, 7, 8, 9]

Process finished with exit code 0

# reversed 顺序倒过来
a = [1, 5, 7, 9, 8]
print(list(reversed(a)))

E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
[8, 9, 7, 5, 1]

Process finished with exit code 0

# sum求和
a = [1, 5, 7, 9, 8]
print(sum(a))

E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
30

Process finished with exit code 0

# bin 十二进制
print(bin(12))

E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
0b1100

Process finished with exit code 0

# oct 八进制
print(oct(8))

E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
0o10

Process finished with exit code 0

# hex 十六进制
print(hex(16))

E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
0x10

Process finished with exit code 0

# ord ASCII表
print(ord('A'))

E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
65

Process finished with exit code 0

# enumerate 枚举，可以把索引取出来
li = ['a', 'b', 'c', 'd']
print(list(enumerate(li)))

E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
[(0, 'a'), (1, 'b'), (2, 'c'), (3, 'd')]

Process finished with exit code 0

# eval 把字符串内容取出，并计算里面的表达式的值
a = '1+2'
print(eval(a))

E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
3

Process finished with exit code 0

# exec 执行一个编译的表达式
exec('a=1')
print(a)

E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
1

Process finished with exit code 0

# filter 过滤
li = [1, 2, 3, 11, 22, 33, 44, 55]
def func(x):		 #	过滤函数
    return x > 10    # 过滤条件


b = list(filter(func, li))
print(b)

E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
[11, 22, 33, 44, 55]

Process finished with exit code 0

# map 把列表种所有的元素都对应条件进行运算，映射
li = [1, 2, 3, 11, 22, 33, 44, 55]
def func(x):
    return x*10


b = list(map(func, li))
print(b)

E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
[10, 20, 30, 110, 220, 330, 440, 550]

Process finished with exit code 0

# zip 配对，多余的就不会配对
li = [1, 2, 3, 11, 22, 33, 44, 55]
li2 = [22, 666, 99]
print(list(zip(li, li2)))

E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
[(1, 22), (2, 666), (3, 99)]

Process finished with exit code 0
```