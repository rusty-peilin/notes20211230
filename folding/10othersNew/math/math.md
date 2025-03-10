### 什么是标准差

标准差是一种用来衡量数据集合中数据分散程度的统计量。**它是每个数据点与数据集合平均值的差的平方的平均值的平方根。(方差则是标准差的平方，即这里不算平方根)** 标准差越大，数据集合中的数据点越分散。以下是一个简单的 Python 代码示例，用于计算给定数据集合的标准差：

```
import math

def calculate_std_dev(data):
    n = len(data)
    mean = sum(data) / n
    variance = sum((x - mean) ** 2 for x in data) / n
    std_dev = math.sqrt(variance)
    return std_dev
```

在这个示例中，我们首先计算数据集合的平均值，然后计算每个数据点与平均值的差的平方，并将它们相加。这个总和被除以数据点的数量，得到方差。最后，我们计算方差的平方根，得到标准差。

### Pearson, Spearman 相关系数

Pearson 相关系数和 Spearman 相关系数都是用来衡量两个变量之间的相关性的统计量。它们的区别在于，Pearson 相关系数是用来衡量两个连续变量之间的线性相关性，而 Spearman 相关系数则是用来衡量两个变量之间的单调关系，可以是线性或非线性的。

Pearson 相关系数是用来衡量两个连续变量之间的线性相关性的统计量。它的取值范围在-1 到 1 之间，其中-1 表示完全负相关，0 表示没有相关性，1 表示完全正相关。

Spearman 相关系数是用来衡量两个变量之间的单调关系的统计量。它的取值范围在-1 到 1 之间，其中-1 表示完全负相关，0 表示没有相关性，1 表示完全正相关。

Pearson 相关系数和 Spearman 相关系数的区别在于，Pearson 相关系数是用来衡量两个连续变量之间的线性相关性，而 Spearman 相关系数则是用来衡量两个变量之间的单调关系，可以是线性或非线性的。在数据呈现线性关系时，Pearson 相关系数更为适用；而在数据呈现非线性关系时，Spearman 相关系数更为适用。

### 用人话讲明白线性回归 LinearRegression

<img src='./img/2023-04-27-22-36-14.png' height=333px></img>

https://zhuanlan.zhihu.com/p/72513104

### ∑ sigma

### 奇函数偶函数，函数奇偶性，Even function/Odd function

奇函数在其对称区间[a,b]和[-b，-a]上具有相同的单调性，即已知是奇函数，它在区间[a,b]上是增函数（减函数），则在区间[-b，-a]上也是增函数（减函数）；偶函数在其对称区间[a,b]和[-b，-a]上具有相反的单调性，即已知是偶函数且在区间[a,b]上是增函数（减函数），则在区间[-b，-a]上是减函数（增函数）。但由单调性不能代表其奇偶性。验证奇偶性的前提要求函数的定义域必须关于原点对称。

<img src='./img/2023-04-30-21-08-21.png' height=333px></img>
