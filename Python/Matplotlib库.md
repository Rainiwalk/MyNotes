### 定义

Matplotlib 可能是 Python 2D-绘图领域使用最广泛的套件。它能让使用者很轻松地将**数据图形化**，并且提供多样化的输出格式。

Matplotlib 可以用来绘制各种静态，动态，交互式的图表。

Matplotlib 可以绘制线图、散点图、等高线图、条形图、柱状图、3D 图形、甚至是图形动画等等。

Matplotlib 通常与 NumPy 和 SciPy（Scientific Python）一起使用， 这种组合广泛用于替代 MatLab，是一个强大的科学计算环境，有助于我们通过 Python 学习数据科学或者机器学习。



### Matplotlib Pyplot

**Pyplot 是 Matplotlib 的子库，提供了和 MATLAB 类似的绘图 API。**

Pyplot 是常用的绘图模块，能很方便让用户绘制 2D 图表。

Pyplot 包含一系列绘图函数的相关函数，每个函数会对当前的图像进行一些修改，例如：给图像加上标记，生新的图像，在图像中产生新的绘图区域等等。



使用的时候，我们可以使用 import 导入 pyplot 库，并设置一个别名 **plt**：

```python
import matplotlib.pyplot as plt
```





### 基本画线/点

示例

```python
import matplotlib.pyplot as plt
import numpy as np

xpoints = np.array([0,6])		# 注意看法，竖着看两点
ypoints = np.array([0,100])		# 分别(0,0),(6,100)，所有就是绘制这两点连线

plt.plot(xpoints,ypoints)
plt.show()
```



输出结果

![QQ截图20210717200500](https://raw.githubusercontent.com/Rainiwalk/Rain_image/main/2021/20210717200805.png)





上面用到了Pyplot的plot()函数，plot()函数是绘制二维图形的最基本函数。

plot()用于画图它可以绘制点和线，语法格式如下

```python
# 画单条线
plot([x], y, [fmt], *, data=None, **kwargs)
# 画多条线
plot([x], y, [fmt], [x2], y2, [fmt2], ..., **kwargs)
```



参数说明：

* x,y：点或线的节点，x为x轴数据，y为y轴数据，数据可以是列表或数组。
* fmt：可选，定义基本格式(如颜色、标记和线条样式)
* **\**kwargs：**可选，用在二维平面图上，设置指定属性，如标签，线的宽度等。

示例

```python
plot(x, y)        # 创建 y 中数据与 x 中对应值的二维线图，使用默认样式
plot(x, y, 'bo')  # 创建 y 中数据与 x 中对应值的二维线图，使用蓝色实心圈绘制
plot(y)           # x 的值为 0..N-1(原来是有预设)
plot(y, 'r+')     # 使用红色 + 号
```



**颜色字符：**'b' 蓝色，'m' 洋红色，'g' 绿色，'y' 黄色，'r' 红色，'k' 黑色，'w' 白色，'c' 青绿色，'#008000' RGB 颜色符串。多条曲线不指定颜色时，会自动选择不同颜色。

**线型参数：**'‐' 实线，'‐‐' 破折线，'‐.' 点划线，':' 虚线。

**标记字符：**'.' 点标记，',' 像素标记(极小点)，'o' 实心圈标记，'v' 倒三角标记，'^' 上三角标记，'>' 右三角标记，'<' 左三角标记...等等。

理解：这些是算作fmt呢，还是kwargs呢？



---

如果我们只想绘制两个坐标点，而不是一条线，可以使用**o**参数，表示一个实心圈标记。

上面代码修改倒数第2行

```python
plt.plot(xpoints, ypoints, 'o')		# 加了个参
```

结果

![QQ截图20210717202054](https://raw.githubusercontent.com/Rainiwalk/Rain_image/main/2021/20210717202211.png)





绘制不规则线

```python
import matplotlib.pyplot as plt
import numpy as np

xpoints = np.array([1, 2, 6, 8])	#原来是前后两个连线
ypoints = np.array([3, 8, 1, 10])

plt.plot(xpoints, ypoints)
plt.show()
```





![QQ截图20210717202326](https://raw.githubusercontent.com/Rainiwalk/Rain_image/main/2021/20210717202405.png)







### 画散点图

我们可以用pyplot中的scatter()方法来绘制散点图。



scatter()方法语法格式：

```python
matplotlib.pyplot.scatter(x, y, s=None, c=None, marker=None, cmap=None, norm=None, vmin=None, vmax=None, alpha=None, linewidths=None, *, edgecolors=None, plotnonfinite=False, data=None, **kwargs)
```

参数说明：

**x，y**：长度相同的数组，也就是我们即将**绘制散点图的数据点**，输入数据。

**s**：点的大小，默认 20，也可以是个数组，数组每个参数为对应点的大小。

**c**：点的颜色，默认蓝色 'b'，也可以是个 RGB 或 RGBA 二维行数组。

**marker**：点的样式，默认小圆圈 'o'。

**cmap**：Colormap，默认 None，标量或者是一个 colormap 的名字，只有 c 是一个浮点数数组的时才使用。如果没有申明就是 image.cmap。

**norm**：Normalize，默认 None，数据亮度在 0-1 之间，只有 c 是一个浮点数的数组的时才使用。

**vmin，vmax：**：亮度设置，在 norm 参数存在时会忽略。

**alpha：**：透明度设置，0-1 之间，默认 None，即不透明。

**linewidths：**：标记点的长度。

**edgecolors：**：颜色或颜色序列，默认为 'face'，可选值有 'face', 'none', None。

**plotnonfinite：**：布尔值，设置是否使用非限定的 c ( inf, -inf 或 nan) 绘制点。

***\*kwargs：**：其他参数。



理解：感觉scatter和基本画点画出的东西一样啊



