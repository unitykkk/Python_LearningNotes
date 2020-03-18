### Page21

```python
from matplotlib import pyplot as plt
import random
from matplotlib import font_manager

# 在我的 notebook 里，要设置下面两行才能显示中文
plt.rcParams['font.family'] = ['sans-serif']
# 如果是在 PyCharm 里，只要下面一行，上面的一行可以删除
plt.rcParams['font.sans-serif'] = ['SimHei']

# 这种方法没搞通,暂不用
# myfont = font_manager.FontProperties(fname="C:\Windows\Fonts\simfang.ttc")

x = range(0, 120)
y = [random.randint(20,35) for i in range(120)]

plt.figure(figsize=(20,8), dpi=80)
plt.plot(x, y)

# 调整x的刻度
_x = list(x)
_xticks_labels = ['10点{}分'.format(i) for i in range(60)]
_xticks_labels += ['11点{}分'.format(i) for i in range(60)]
# rotation旋转的度数
plt.xticks(_x[::10], _xticks_labels[::10], rotation = 45)
# plt.xticks(_x[::10], _xticks_labels[::10], rotation = 45, fontproperties = myfont)

# 添加描述信息
plt.xlabel("时间")
plt.ylabel("温度 单位(℃)")
plt.title("10点到12点每分钟的气温变化情况")

plt.savefig(".\page21.png")
plt.show()
```