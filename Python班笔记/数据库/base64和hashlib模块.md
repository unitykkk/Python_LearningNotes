## base64和hashlib模块

### hashlib

```python
散列函数，一般翻译为哈希，把输入的任意长度的数据，通过散列函数进行转化，变成一个长度固定的值（散列值），这个值基本是唯一的，简单来说，hash算法就是一种将任意长度的数据变成一个长度固定的数据的函数
特点：
1，不可逆：无法根据散列值来还原原来的数据
2，定长输出：无论原始数据有多长，结果长度是固定的
3，抗修改性：输入的微小改变，哪怕只有一个字符，会引起结果巨大的改变
4，强碰撞性：很难找到两段内容不同的数据，使他们产生的hash值一致，几乎不可能
```

```python
import hashlib
# 注意二进制
res = hashlib.new('md5', data='f欸非'.encode('utf8'))
print(res.digest())  # 转化为二进制
print(res.hexdigest())  # 转化为字符串

E:\基础\venv\Scripts\python.exe E:/基础/进阶/task.py
b'\x1f*\xbc%F\xc2\x1d\xe9\xe8W\xc7\x0b^Nf\xcf'
1f2abc2546c21de9e857c70b5e4e66cf

Process finished with exit code 0
#########################################
和上面的new方法一样
res = hashlib.md5('f欸非'.encode('utf8'))
print(res.hexdigest())

E:\基础\venv\Scripts\python.exe E:/基础/进阶/task.py
1f2abc2546c21de9e857c70b5e4e66cf

Process finished with exit code 0
```

```python
# update
可以重复使用
res = hashlib.sha256()
res.update('霏霏'.encode())
print(res.hexdigest())
res.update('飞飞'.encode())
print(res.hexdigest())

E:\基础\venv\Scripts\python.exe E:/基础/进阶/task.py
8126ea4d4ada90ab7b407b262d91289b64771ac81e21cbf17ae05a582466987e
284766f32f9200a39b160e3185feaa8137d228372bfe18edc74e827738ce6feb

Process finished with exit code 0
```

### base64

```python
base64是一种用64个字符来表示任意二进制数据的方法，将二进制数据编码成ASCII字符，使用了A-Z,a-z,0-9，+,/这64个字符

特点：
用来将非ASCII字符的数据转化成ASCII字符的一种方法
常用于对URL编码
可以将不可打印的二进制数据转化为可打印的字符串
```
![base64](C:\Users\Administrator\Desktop\数据库\base64.png)

```python
import base64

# 正常使用，一个中文三个字节
data = '你好世界'
res = base64.b64encode(data.encode())  # 编码，参数必须是二进制
print(res)

E:\基础\venv\Scripts\python.exe E:/基础/进阶/task2.py
b'5L2g5aW95LiW55WM'

Process finished with exit code 0
```

```python
# 字节数不是三的倍数
data = 'hello world'  # 11个字节
res = base64.b64encode(data.encode())
print(res)

data = 'hello worl'  # 10个字节
res = base64.b64encode(data.encode())
print(res)

E:\基础\venv\Scripts\python.exe E:/基础/进阶/task2.py
b'aGVsbG8gd29ybGQ='
b'aGVsbG8gd29ybA=='

Process finished with exit code 0
区别在于缺多少字节就用多少个等号补齐
```

```python
data = 'hello worlfasfas飞洒发生发'  # 10个字节
res = base64.b64encode(data.encode())
print(res)

res = base64.urlsafe_b64encode(data.encode())
print(res)

E:\基础\venv\Scripts\python.exe E:/基础/进阶/task2.py
b'aGVsbG8gd29ybGZhc2Zhc+mjnua0kuWPkeeUn+WPkQ=='
b'aGVsbG8gd29ybGZhc2Zhc-mjnua0kuWPkeeUn-WPkQ=='

Process finished with exit code 0
有+号是看运气的，换成urlsafe就会把+变-好。/变_,对url编码就用urlsafe
```

```python
########解密#######
data = '你好潭州'
res = base64.b64encode(data.encode())  # 编码
res = base64.b64decode(res)
print(res)  # 得到的是一个二进制的数据，所以下一行要解码
print(res.decode())

E:\基础\venv\Scripts\python.exe E:/基础/进阶/task2.py
b'\xe4\xbd\xa0\xe5\xa5\xbd\xe6\xbd\xad\xe5\xb7\x9e'
你好潭州

Process finished with exit code 0
```