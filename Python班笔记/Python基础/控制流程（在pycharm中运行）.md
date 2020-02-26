## 控制流程（在pycharm中运行）

### 条件判断

#### 执行顺序

```python
python中代码的执行顺序是由上至下执行的，如何改变顺序，需要通过条件判断
a = [1, 2, 3]
print(a)
a.append('a')
print(a)

E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
[1, 2, 3]
[1, 2, 3, 'a']

Process finished with exit code 0

条件：判断语句  if
laowang = '男'
if laowang == '男':   # if下面的语句严格要求缩进
    print('老王是男生')    # if的语句成立时执行

E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
老王是男生

Process finished with exit code 0    

# else
laowang = '女'
if laowang == '男':   # if下面的语句严格要求缩进
    print('老王是男生')    # if的语句成立时执行

else:   #  if不成立的时候执行
    print('老王是女生')
   
E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
老王是女生

Process finished with exit code 0

#elif  当if不成立时，就elif的条件来判断，elif不成立时就执行else
laowang = '女'
if laowang == '男':   # if下面的语句严格要求缩进
    print('老王是男生')    # if的语句成立时执行

elif laowang == '人妖':
    print('老王是人妖')

else:   #  if不成立的时候执行
    print('老王是女生')

E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
老王是女生

Process finished with exit code 0
```

#### input

```python
输入函数  input：把内容都转成字符串
while True:
    a = input('请输入您的身高（cm）')
    if a >= '180':
        print('男神身高')

    elif a == '173':
        print('标准身高')

    elif '160' < a < '173':
        print('中等身高')

    else:
        print('萝莉身高')

E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
请输入您的身高（cm）200
男神身高
请输入您的身高（cm）180
男神身高
请输入您的身高（cm）175
萝莉身高
请输入您的身高（cm）158
萝莉身高
请输入您的身高（cm）161
中等身高
请输入您的身高（cm）

```

#### 三目运算

```python
三目运算：可以把简单的条件判断写成一行，节省代码，又称之语法糖
a = 4
print(True) if a > 5 else print(False)

E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
False

Process finished with exit code 0
```

### while循环

#### 程序执行三大流程：

1，顺序执行  2，选择执行  3，循环执行

#### while用法:

i 相当于时计数器，用来控制循环

```python
# while后面跟条件，成立就执行，当执行的内容不成立时，就跳出循环
i = 1
while i <= 10:
    print(i)
    i += 1 
    
E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
1
2
3
4
5
6
7
8
9
10

Process finished with exit code 0
```

```python
# 遍历列表里的值
mylist = [1, 3, 7, 9]
i = 0
while i < len(mylist):
    print(mylist[i])
    i += 1
    
E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
1
3
7
9

Process finished with exit code 0
```

```python
#  加条件
mylist = [1, 3, 32, 20, 39, 50, 7, 9]
i = 0
while i < len(mylist):
    if mylist[i] > 19:
        print('%s大于19' % mylist[i])
    else:
        print('%s小于19' % mylist[i])
    i += 1
    
E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
1小于19
3小于19
32大于19
20大于19
39大于19
50大于19
7小于19
9小于19

Process finished with exit code 0    
```

```python
# continue 跳出当次循环，回到while
mylist = [1, 3, 32, 20, 39, 50, 7, 9]
i = -1
while i < len(mylist) - 1:
    i += 1
    if mylist[i] == 3:
        continue
    print(mylist[i])
    
E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
1
32
20
39
50
7
9

Process finished with exit code 0

```

```python
# break 终止循环
mylist = [1, 3, 32, 20, 39, 50, 7, 9]
i = -1
while i < len(mylist) - 1:
    i += 1
    if mylist[i] == 3:
        break
    print(mylist[i])
    
E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
1

Process finished with exit code 0
```

```python
# else     跳出循环后执行
mylist = [1, 3, 32, 20, 39, 50, 7, 9]
i = -1
while i < len(mylist) - 1:
    print(mylist[i])
    i += 1
else:
    print('循环结束')
    
E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
9
1
3
32
20
39
50
7
循环结束

Process finished with exit code 0
```

### for循环，迭代循环

```python
# 遍历可迭代对象，能被for循环取值就是可迭代对象
mylist = [1, 3, 32, 20, 39, 50, 7, 9]
for i in mylist:
    print(i)
    
E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
1
3
32
20
39
50
7
9

Process finished with exit code 0
```

```python
# 内置函数 range，范围，遵循左闭右开
for i in range(1, 10):
    print(i)
    
E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
1
2
3
4
5
6
7
8
9

Process finished with exit code 0
也可以使用步长
for i in range(1, 10, 2):
    print(i)
    
E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
1
3
5
7
9

Process finished with exit code 0
```

```python
# 加条件
for i in range(1, 10):
    if i % 5 == 0:
        continue
    print(i)
    
E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
1
2
3
4
6
7
8
9

Process finished with exit code 0
```

判断一个对象是否为可迭代对象的最简单方法：

dir(对象) 如果有__iter__方法就是可迭代对象，没有就不是

```python
print(dir(range(0, 10)))

E:\基础\venv\Scripts\python.exe E:/基础/补笔记/条件判断.py
['__class__', '__contains__', '__delattr__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__getitem__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__iter__', '__le__', '__len__', '__lt__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__reversed__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', 'count', 'index', 'start', 'step', 'stop']

Process finished with exit code 0
```