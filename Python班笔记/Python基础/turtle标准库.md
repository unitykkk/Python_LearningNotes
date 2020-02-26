## turtle标准库

正东方为0°，初始爬行方向，正西方为绝对180°

​			左侧方向

后退方向		（0，0）			前进方向

​			右侧方向

```python
from turtle import *
circle(200)

from turtle import circle
circle(200)

import turtle as t
t.circle(200)
这三种方式实现的效果是一样的

```

```python
提起画笔，移动画笔不会绘制形状
import turtle as t
t.penup()


```

```python
# 绘制等边三角形
import turtle as t
t.fd(200)
t.seth(120)
t.fd(200)
t.seth(240)
t.fd(200)
```