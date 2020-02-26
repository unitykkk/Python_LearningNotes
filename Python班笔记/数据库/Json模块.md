## Json模块

```python
数据由键值对组成
键值对由逗号分隔
大括号里保存对象
中括号里保存数组
```

```python
1，字符串必须用双引号来包括 " "
2，值可以是字符串，数字，true，false，null，列表或字典
```

```python
python的字典对象json的对象
列表或元组对应数组
字符串对应字符串
int或float对应数字
True或False对应 true或false
None对应null
```

### dumps，python转为json

```python
import json
# dump/load/dumps/loads
# dumps : 将python转化为json
my_dict = {'name': 'fei',
           'age': 18,
           'sex': [0, 1],
           'tu': (1, 2, 3),
           'bool': True,
           'time': None,
           }
res = json.dumps(my_dict)
print(res)

E:\基础\venv\Scripts\python.exe E:/基础/补笔记/test3.py
{"name": "fei", "age": 18, "sex": [0, 1], "tu": [1, 2, 3], "bool": true, "time": null}

Process finished with exit code 0
转换了之后，单引号变成双引号，元组列表都变成数组[]的形式，True变成true，None变成null
```

```python
这里的my_dict用的上面的
# pretty ==> indent  # 优化格式，缩进
res2 = json.dumps(my_dict, indent=1)
print(res2)

E:\基础\venv\Scripts\python.exe E:/基础/补笔记/test3.py
{
 "name": "fei",
 "age": 18,
 "sex": [
  0,
  1
 ],
 "tu": [
  1,
  2,
  3
 ],
 "bool": true,
 "time": null
}

Process finished with exit code 0
```

```python
# 对于中文的编码处理
my_dict = {'name': '飞',
           }
res = json.dumps(my_dict)
print(res)

E:\基础\venv\Scripts\python.exe E:/基础/补笔记/test3.py
{"name": "\u98de"}  

Process finished with exit code 0

# 如果不想编成ascii码，加上ensure_ascii=False
my_dict = {'name': '飞',
           }
res = json.dumps(my_dict, ensure_ascii=False)  # 
print(res)

E:\基础\venv\Scripts\python.exe E:/基础/补笔记/test3.py
{"name": "飞"}

Process finished with exit code 0
```

### loads，json转化为python

```python
# loads 将json转化为python
my_dict = {
    'name': '飞',
    'age': None,
    'sex': (1, 2, 0),
    'bool': True,
}
res = json.dumps(my_dict)  # 转化为json
res2 = json.loads(res)
print(res2)
print(type(res))
print(type(res2))

E:\基础\venv\Scripts\python.exe E:/基础/补笔记/test3.py
{'name': '飞', 'age': None, 'sex': [1, 2, 0], 'bool': True}
<class 'str'>
<class 'dict'>

Process finished with exit code 0
```

### dump

```python
my_dict = {
    'name': '飞',
    'age': None,
    'sex': (1, 2, 0),
    'bool': True,
}

# dump ,将python转换为json，将转换的数据保存到文件中去
with open('test_json', 'w') as f:
    res = json.dump(my_dict, fp=f, ensure_ascii=False)  # fp是必须写的默认的，这里的fp=f指明读哪个文件
    
E:\基础\venv\Scripts\python.exe E:/基础/补笔记/test3.py

Process finished with exit code 0
运行成功就可以去查看是否生成文件
```

### load

```python
# load, 先读取文件，再将json数据转化为python数据
with open('test_json', 'r') as f:
    res = json.load(fp=f)  # 这里的fp=f指明读哪个文件
    print(res)
    
E:\基础\venv\Scripts\python.exe E:/基础/补笔记/test3.py
{'name': '飞', 'age': None, 'sex': [1, 2, 0], 'bool': True}

Process finished with exit code 0
```