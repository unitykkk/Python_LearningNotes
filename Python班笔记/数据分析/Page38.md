### Page38

```python
from matplotlib import pyplot as plt
import matplotlib

# 在我的 notebook 里，要设置下面两行才能显示中文
plt.rcParams['font.family'] = ['sans-serif']
# 如果是在 PyCharm 里，只要下面一行，上面的一行可以删除
plt.rcParams['font.sans-serif'] = ['SimHei']

y_3 = [11,17,16,11,12,11,12,6,6,7,8,9,12,15,14,17,18,21,16,17,20,14,15,15,15,19,21,22,22,22,23]
y_10 = [26,26,28,19,21,17,16,19,18,20,20,19,22,23,17,20,21,20,22,15,11,15,5,13,17,10,11,13,12,13,6]

x_3 = range(1,32)
x_10 = range(51,82)

plt.figure(figsize=(20,8), dpi=80)
plt.scatter(x_3, y_3, label = "3月份温度")
plt.scatter(x_10, y_10, label = "10月份温度")

# 调整x轴的刻度
_x = list(x_3) + list(x_10)
xticks_labels = ['3月{}日'.format(i) for i in range(1, 32)]
xticks_labels += ['10月{}日'.format(i) for i in range(1, 32)]
plt.xticks(_x[::3], xticks_labels[::3], rotation = 45)

# 这句必须加上，scatter里的label才会显示
plt.legend(loc = 'upper left')

# 保存图片一定要在show之前
plt.savefig('.\page38.png')

plt.show()
```