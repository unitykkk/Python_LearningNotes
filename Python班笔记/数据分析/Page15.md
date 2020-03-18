### Page15

```python
from matplotlib import pyplot as plt

x = range(2, 26, 2)
y = [15,13,14.5,17,20,25,26,26,24,22,18,15]

# 设置图片大小
plt.figure(figsize=(20,8), dpi=80)

# 绘图
plt.plot(x, y)
# 设置x的刻度
xticks_lables = [i/2 for i in range(4,49)]
plt.xticks(xticks_lables)
plt.yticks(range(min(y), max(y) + 1))
# 保存图片
plt.savefig(".\page15.png")
# svg为矢量图格式,放大不会有锯齿
plt.savefig(".\page15.svg")
# 显示图片
plt.show()
```