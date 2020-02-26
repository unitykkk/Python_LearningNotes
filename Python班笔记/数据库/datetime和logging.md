## datetime和logging

### datetime

```python
datetime下面的date模块，年月日
import datetime

d = datetime.date(2019, 10, 28)  # 年月日格式，不能多或者少
print(d)

C:\Users\Administrator\Desktop\env\monster\Scripts\python.exe E:/monster/datetime和logging模块/时间模块.py
2019-10-28

Process finished with exit code 0
```

```python
datetime下面的time是表示 时分秒毫秒
import datetime

t = datetime.time(22, 57, 35, 1)
print(t)

C:\Users\Administrator\Desktop\env\monster\Scripts\python.exe E:/monster/datetime和logging模块/时间模块.py
22:57:35.000001

Process finished with exit code 0
```

```python
datetime下面的datetime，年月日时分秒
import datetime

dt = datetime.datetime(2019, 10, 28, 22, 59, 37, 1)
print(dt)

C:\Users\Administrator\Desktop\env\monster\Scripts\python.exe E:/monster/datetime和logging模块/时间模块.py
2019-10-28 22:59:37.000001

Process finished with exit code 0
```

```python
import datetime

now = datetime.datetime.now()
print(now)

C:\Users\Administrator\Desktop\env\monster\Scripts\python.exe E:/monster/datetime和logging模块/时间模块.py
2019-10-28 23:07:28.574242

Process finished with exit code 0
```

```python
从datetime模块导入datetime类
from datetime import datetime

now = datetime.now()
print(now)  # 当前时间日期对象
print(now.date())  # 年月日
print(now.time())  # 时分秒

C:\Users\Administrator\Desktop\env\monster\Scripts\python.exe E:/monster/datetime和logging模块/时间模块.py
2019-10-28 23:08:13.473152
2019-10-28
23:09:29.382718        

Process finished with exit code 0
```

```python
from datetime import datetime

# datetime类中的常用方法
# 1，获取当前时间
now = datetime.now()
# print(now)
# 2，转换为时间戳
res = now.timestamp()
# print(res)
# 3,时间戳转换为日期时间
res = datetime.fromtimestamp(res)
# print(res)
# print(type(res))  # <class 'datetime.datetime'>
# 4,格式化输出
res = res.strftime('%Y %m %d')
# print(res)
# print(type(res))  # 字符串

# 5,字符串转时间日期对象
s = '29 10 2019 00:36:51'
res1 = datetime.strptime(s, '%d %m %Y %H:%M:%S')  # 格式要求非常严格
print(res1)
```

```python
测试<class 'datetime.timedelta'>，timedelta模块
import datetime

# 必须是时间对象减去timedelta对象，否则报错
now = datetime.datetime.now()
td = datetime.timedelta(hours=24, minutes=11, seconds=57)
print(type(td))  # <class 'datetime.timedelta'>
print(now-td)  # 当前时间减去timedelta设置的时间
print(now+td)  # 当前时间加上timedelta设置的时间

# 两个日期时间对象的差值就是<class 'datetime.timedelta'>对象

# res = now.timestamp()  # 时间戳
# print(res)
res = datetime.datetime.fromtimestamp(1572282251.152205)  # 选取的一个时间戳转化为日期时间对象
t = now - res
print(type(t))  # <class 'datetime.timedelta'> ，为了测试两个时间的差值就是 <class 'datetime.timedelta'> 对象！
```

### logging

```python
import logging
from datetime import datetime


now = datetime.now()
# print(now)

x = logging.basicConfig(level=logging.DEBUG,  # 配置日志级别，注意大写
                        format='时间：%(asctime)s 文件名：%(filename)s 行号：%(lineno)d',  # 日志格式
                        filename='info.txt',  # 写到指定的文件里去，防止丢失
                        filemode='a',  # 指定写入方式,跟文件一样，r，w，a。
                        )  # basicConfig只写一次，多了只执行第一个


# 在测试代码时可以用到这个方法，检查无误后，改变等级就可以
a = 1 + 6
logging.info(a)
b = a * 2
logging.info(b)

# logging.info(now)  # 级别不够不会记录
# logging.warning(now)  # 级别够了就记录  WARNING:root:2019-10-29 13:50:48.017892
# logging.error(now)
# logging.critical(now)
```

```python
日志模块化组件使用
import logging

# 1, 创建一个logger（日志处理对象）
# 2，定义handler（日志处理器），决定把日志发到哪里
# 3，设置日志级别（level）和输出格式Formatters（日志格式器）
# 4，把handler添加到对应的logger去

# 常用的是：
# SteamHandler输出到控制台
# FileHandler输出到文件

my_logger = logging.Logger('白展堂')  # 创建一个日志处理器logger对象

# ==========================================

# 第一个处理器
my_handler = logging.FileHandler('my.log')  # 定一个handler日志处理器
my_handler.setLevel(logging.DEBUG)  # 设置级别level
fmt = logging.Formatter('时间：%(asctime)s 文件名：%(filename)s 行号：%(lineno)d 文本信息：%(message)s')  # 设置日志格式

# 第二个处理器
your_handler = logging.StreamHandler()  # 在终端显示，不用写入文件
your_handler.setLevel(logging.WARNING)
your_format = logging.Formatter('Stream时间：%(asctime)s Stream文件名：%(filename)s Stream行号：%(lineno)d Stream文本信息：%(message)s')

# ==========================================
# 添加,要把设置的格式放到对应的日志处理器中去
my_handler.setFormatter(fmt)
my_logger.addHandler(my_handler)

# 添加第二个
your_handler.setFormatter(your_format)
my_logger.addHandler(your_handler)
# ==========================================

# 设置完，添加完，开始使用
my_logger.info('我是日志组件')
my_logger.warning('警告，严重警告')
```