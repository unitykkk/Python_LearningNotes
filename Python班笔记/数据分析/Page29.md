### Page29

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

y1 = [1,0,1,1,2,4,3,2,3,4,4,5,6,5,4,3,3,1,1,1]
y2 = [2,0,3,1,2,2,3,3,2,1,2,1,1,1,1,1,1,1,1,1]

x = range(11, 31)

plt.figure(figsize=(20,8), dpi=80)
plt.plot(x, y1, label = '自己', color = 'orange',linestyle = ':')
plt.plot(x, y2, label = '同桌', color = 'cyan', linestyle = '-.')

_xticks_labels = ['{}岁'.format(i) for i in x]
plt.xticks(x, _xticks_labels)
plt.yticks(range(0,10))

# 添加描述信息
plt.xlabel("年龄")
plt.ylabel("交往的女朋友数量")
plt.title("11岁到30岁交往的女朋友数量统计")

plt.legend(loc = 'upper left')

# 显示网格，网格透明度设置为0.4
# plt.grid(alpha = 0.4)
plt.grid(alpha = 0.4, linestyle=':')

plt.savefig(".\page29.png")
plt.show()
```

