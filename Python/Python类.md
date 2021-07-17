### 创建和使用类





### 导入类

随着你不断给类添加功能，文件会变得越来越长。为了遵循Python的总体理念，应让文件尽可能简洁。

为了再这方面提供帮助，**Python允许你将类存储在模块中，然后在主程序中导入所需的模块。**



#### 导入某个类

首先是自己写一个模块。

创建一个py文件，命名应该有明确的含义，比如类名的小写状态。

这里就创建一个模块car.py(一个文件)，其中只包含Car类的代码。

```python
"""一个可用于表示汽车的类"""	# 一个模块级文档字符串，对该模块的内容做了简要的描述。

class Car:
    """一次模拟汽车的简单尝试"""
    
    def __init__(self,make,model,year):
        
 # ...
```



其他文件使用这个Car类：

```Python
from car import Car		# 从模块文件car.py导入里面的类Car

my_new_car = Car('audi','a4',2016)	# 这样方法导入的类，可以直接调用
```



同时，如果有很多类和这个模块有关系，那就应该把这些类都放到这个模块里面。

只需要在导入时import不同的类就行了。



如果要一次导入多个类

```python
from car import Car,ElectricCar		#只需要像这样用逗号进行分隔就好
```





#### 导入整个模块

你可以导入整个模块，**再使用句点表示法访问需要的类。**

而且由于创建类实例的代码都包含模块名，因此不会与当前文件使用的任何名称发生冲突。

```python
import car

# 使用语法module_name.class_name访问需要的类
my_beetle = car.Car('volkswagen','beetle',2016)	
print(my_beetle.get_descriptive_name())
```



#### 导入模块中的所有类

```python
from module_name import *
```



**存在这种用法，但是作者不推荐。**作者讲一下只是为了帮助你理解别人的代码(他可能会用)。

首先，如果只是使用少量的类，那么单个导入(就是那种指定模块某个类导入)的样子更好，那样看了开头你就可以知道程序使用了哪些类，将大有裨益；但现在这种全导入的方法就不知道。

而且这种导入方法还可能引发名称的困惑。如果你不小心导入了一个与程序文件中其他东西同名的类，将引发难以判断的错误。



如果你需要导入很多的类，那就直接导入整个模块，然后用module_name.class_name的语法来访问类。

这样做，虽然开头没法列出用到的类了，但是你将清楚知道程序在哪些地方使用了导入的模块；你还避免了导入模块中每个类可能引发的名称冲突。



#### 在一个模块中导入另一个模块

有时候，需要将类分散到多个模块，以免模块太大，或在同一个模块中存储不相关的类。

将类存储在多个模块中时，你可能会发现一个模块中的类依赖于另一个模块中的类(比如继承关系)。在这种情况下，可在前一个模块中导入必要的类。



比如下面这个模块文件 electric_car.py

```python
"""一组可用于表示电动汽车的类"""

from car import Car

class Battery:
    --snip--
class ElectricCar(Car):		#注意这里，他继承的类可不在这个模块，所以才需要上面导入。
    --snip--
```



**有一个疑问：**我是在这个模块里导入了Car类让ElectricCar有了可以继承的类，但是我使用from .. import 导入ElectricCar类时，还用不用导入其父类呢？

我更愿意相信不用导入，不然的话问题就变得复杂了，我还需要提前知道哪个类对应父类是啥，那也太麻烦了。

可以现在还是没有找到证据，作者这里给的代码反而是导入了的。

```python
from car import Car
from electric_car import ElectricCar

my_beetle = Car('volkkswagen','beetle',2016)
print(my_beetle.get_descriptive_name())

my_tesla = ElectricCar('tesla','roadster',2016)
print(my_tesla.get_descriptive_name())

```



### Python标准库

尽管自己也可以定义很多东西，但这终究是孤军奋战。

有很多东西你大可不必自己写，直接导入别人的库就ok了。

安装的Python就自带了Python标准库(其实就是一组模块)。

但有时候这个未必够用，还可以用pip或者直接下载集成好的Python发行版本。



### 类编码风格

类名应该采用驼峰命名法。

待续...