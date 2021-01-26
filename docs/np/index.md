np.polyfit函数

官方路径：

https://numpy.org/doc/stable/reference/generated/numpy.polyfit.html

采用的是最小二次拟合

numpy.polyfit(x,y,deg,rcond=None,full=False,w=None, cov=False)

前三个参数是必须的

polyfit()函数接受三个不同的输入值：x，y和the polynomial degree。 参数x和y分别对应于我们要拟合的数据点的值，分别位于x和y轴上。 第三个参数指定多项式函数的次数。 例如，要获得线性拟合，请使用次数1。

拟合的最简单类型是线性拟合（一次多项式函数），其中数据点使用直线拟合。直线的一般方程为：

***y = mx + q***

其中“ m”称为*角度系数*，“ q”*截距*。当我们应用线性拟合时，我们基本上是在搜索参数“ m”和“ q”的值，这些参数对我们的数据点产生最佳拟合。在Numpy中，该函数`np.polyfit()`是一个非常直观且功能强大的工具，用于拟合数据点。

```python
import numpy as np
from numpy import random
import matplotlib.pyplot as plt

#---LINEAR FIT----

#生成x数组
x = np.linspace(0,60,60) # 生成60个等距点的数组

#利用random.randint()函数生成y数组，引入一些随机噪声
y = np.array([random.randint(i-2, i+2) for i in x]) # 每个元素都是一个随机数，其值在x轴值+-2之间

#通过.polyfit()应用线性拟合
fit = np.polyfit(x,y,1, full=True)

print(fit)

```

得到值

```
(

array([ 0.98254098, -0.15956284]),  # coefficients 系数

array([72.97164953]),# residuals 残差

2, # rank 等级

array([1.36469006, 0.37097309]), # singular values 奇异值

1.3322676295501878e-14 # conditioning threshold 调节阈值

) 
```

如果去除full=True，则得到的值如下

```
[ 0.98013661 -0.58743169] # coefficients 系数
```

