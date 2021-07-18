### 定义

NumPy(Numerical Python) 是 Python 语言的一个扩展程序库，支持大量的维度数组与矩阵运算，此外也针对数组运算提供大量的数学函数库。

Numpy是一个开源的Python科学计算库，它是python科学计算库的基础库，许多其他著名的科学计算库如Pandas，Scikit-learn等都要用到Numpy库的一些功能。

理解：Python的Eigen?



为什么用numpy?

* Python中提供了list(列表)容器，可以当作数组使用。但列表中的元素可以是任何对象，因此列表中保存的是对象的指针，这样一来，为了保存一个简单的列表[1,2,3]。就需要三个指针和三个整数对象。对于数值运算来说，这种结构显然不够高效。 
* Python虽然也提供了array模块，但其只支持一维数组，不支持多维数组，也没有各种运算函数。因此不适合数值运算。
* 而NumPy的出现弥补了这些不足。

-----张若愚的《Python科学计算》



**Numpy应用**

NumPy 通常与 SciPy（Scientific Python）和 Matplotlib（绘图库）一起使用， 这种组合广泛用于替代 MatLab，是一个强大的科学计算环境，有助于我们通过 Python 学习数据科学或者机器学习。

SciPy 是一个开源的 Python 算法库和数学工具包。

SciPy 包含的模块有最优化、线性代数、积分、插值、特殊函数、快速傅里叶变换、信号处理和图像处理、常微分方程求解和其他科学与工程中常用的计算。

Matplotlib 是 Python 编程语言及其数值数学扩展包 NumPy 的**可视化操作界面**。它为利用通用的图形用户界面工具包，如 Tkinter, wxPython, Qt 或 GTK+ 向应用程序嵌入式绘图提供了应用程序接口（API）。



### Numpy数组对象

Numpy中的多维数组称为ndarray，这是Numpy中最常见的数组对象。

ndarray对象通常包含两个部分：

* ndarray数据本身
* 描述数据的元数据



Numpy数组的优势

- Numpy数组通常是由相同种类的元素组成的，即数组中的数据项的类型一致。这样有一个好处，由于知道数组元素的类型相同，所以能快速确定存储数据所需空间的大小。
- Numpy数组能够运用**向量化运算**来处理整个数组，速度较快；而Python的列表则通常需要借助循环语句遍历列表，运行效率相对来说要差。
- Numpy使用了优化过的C API，运算速度较快



关于向量化和标量化运算，对比下面的参考例子可看出差异。

* 使用Python的list进行循环遍历运算

  ```python
  def pySum():
      a = list(range(10000))		# 建立一个从0~9999的列表
      b = list(range(10000))
      c = []
      
      for i in range(len(a)):		# 传入一个数字序列来由i依次走到0~len-1
          c.append(a[i]**2 + b[i]**2)
          
      return c
          
  # timeit pySum()
  # 结果：10 loops, best of 3: 49.4 ms per loop
  ```

* 使用numpy进行向量化运算

  ```python
  import numpy as np
  def npSum():
      a = np.arange(10000)
      b = np.arange(10000)
      c = a**2 + b**2
      return c
  
  # timeit npSum()
  # 结果：The slowest run took 262.56 times longer than the fastest. This could mean that an intermediate result is being cached.
  # 1000 loops, best of 3: 128 µs per loop
  ```



从运算结果来看，numpy的向量化运算效率越高于python的循环遍历运算。(1 ms = 1000µs)



### 创建ndarray数组

首先需要导入numpy库，在导入numpy库时通常使用“np”作为简写，这也是Numpy官方倡导的写法。

```python
import numpy as np
```



创建ndarray数组的方式有很多种，这里介绍我使用的较多的几种：

#### 基于list或tuple

```python
# 建立一维数组

# 基于list
arr1 = np.array([1,2,3,4])
print(arr1)

# 基于tuple
arr_tuple = np.array((1,2,3,4))
print(arr_tuple)

# 建立二维数组(2*3)
arr2 = np.array([[1,2,4],[3,4,5]])	# 里面仍是一个list，但是list里面也都是list。感觉就是用,来分隔每一行，每一行是一个list
print(arr2)


# 输出结果
[1 2 3 4]
[1 2 3 4]
[[1 2 4]
 [3 4 5]]

# 其实这里学到的这个只能创建二维数组，推广也没用
arr2 = np.array([[1,2,4],[3,4,5],[9,8,7]])
print(arr2)

# 输出
[[1 2 4]
 [3 4 5]
 [9 8 7]]

# 只不过是一个3*3二维数组,里面列表数控制多少行，每个列表里面控制多少列
```



注意

* 一维数组用print输出时为[1 2 3 4]，跟列表时有差异的，没有","
* 在创建二维数组时，每个list外面还有一个"[]"，形如"[[list1],[list2]]"



#### 基于np.arange

```python
# 一维数组
arr1 = np.arange(5)
print(arr1)

#二维数组
arr2 = np.array([np.arange(3), np.arange(3)])
print(arr2)

# 输出结果
[0 1 2 3 4]
[[0 1 2]
 [0 1 2]]
```







### 从数值范围创建数组

numpy 包中使用 arange 函数创建数值范围并返回 ndarray 对象，函数格式如下：

```python
numpy.arange(start, stop, step, dtype)
```



根据 start 与 stop 指定的范围以及 step 设定的步长，生成一个 ndarray。

参数说明：

* start：起始值，默认为0
* stop：终止值(不包含)
* step：步长，默认为1
* dtype：返回的ndarray的数据类型，如果没有提供，则会使用输入数据的类型。



理解：感觉和平常的range()用法差不多，只不过是numpy带的而已



示例

```python
# 生成0到5的数组
import numpy as np
 
x = np.arange(5)  
print (x)

# 输出结果
[0 1 2 3 4]


# 设置返回类型为float
x = np.arange(5, dtype =  float)  
print(x)

# 输出结果
[0.  1.  2.  3.  4.]

# 指定步长
x = np.arange(10,20,2)  
print (x)

# 输出结果
[10  12  14  16  18]
```







https://www.runoob.com/numpy/numpy-array-from-numerical-ranges.html



学习链接：https://www.cnblogs.com/lemonbit/p/7043879.html





#### np.zeros()

用法：zeros(shape, dtype=float, order='C')

返回：返回一个给定形状和类型的用0填充的数组；



    shape:形状
    
    dtype:数据类型，可选参数，默认numpy.float64  t ,位域,如t4代表4位
    
    b,布尔值，true or false
    
    i,整数,如i8(64位）
    
    u,无符号整数，u8(64位）
    
    f,浮点数，f8（64位）
    
    c,浮点负数，
    
    o,对象，
    
    s,a，字符串，s24
    
    u,unicode,u24
    
    
    order:可选参数，c代表与c语言类似，行优先；F代表列优先


示例

```python
np.zeros(5)
array([ 0.,  0.,  0.,  0.,  0.])

np.zeros((5,), dtype=np.int)
array([0, 0, 0, 0, 0])

np.zeros((2, 1))
array([[ 0.],
       [ 0.]])

s = (2,2)
np.zeros(s)
array([[ 0.,  0.],
       [ 0.,  0.]])
```

