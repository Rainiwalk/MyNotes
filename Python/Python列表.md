### 列表概念定义

列表是一系列按特定顺序排列的元素组成。

鉴于其一般包含多个元素，给他一个复数的名称(比如letters、digits、names)比较好。

理解：算是Python中的数组，但是功能更强



### 列表元素操作

#### 定义

在Python中，用**方括号[]**来表示列表，并用逗号来分隔其中的元素。



示例

```python
bicycles = ['trek','cannondale','redline','specialized']	#定义
print(bicycles)		# 打印列表

# 输出结果
# ['trek','cannondale','redline','specialized']
```



#### 访问列表元素

列表是有序集合，想要访问元素，只需要将该元素的位置或索引告诉Python即可。

方法：指出列表名称，再指出元素的索引，并将其放在方括号内。



示例

```python
bicycles = ['trek','cannondale','redline','specialized']	
print(bicycles[0])		# 打印第一个元素trek
```



访问索引从0~N-1，这个你我都知道。

但Python对于访问倒数的元素提供了特殊的语法。

例如，通过将索引定为-1，可让Python返回最后一个列表元素。



```python
bicycles = ['trek','cannondale','redline','specialized']	
print(bicycles[-1])		# 打印最后一个元素specialized
```



这个方法是很有用的，因为你常常需要在不知道列表长度的情况下访问最后的元素。

这种负数索引也是可以推广的，-2就是倒2元素，-3就是倒3。



#### 修改列表元素

就是一个覆盖的赋值语句。

```python
bicycles = ['trek','cannondale','redline','specialized']
print(bicycles[0])
bicycles[0] = 'ducati'			# 进行修改
print(bicycles[0])

'''
输出
trek
ducati
'''
```



#### 添加列表元素

##### 在列表末尾添加元素

使用append()，需要指定插入的值。

```python
bicycles = ['trek','cannondale','redline','specialized']
print(bicycles)
bicycles.append('ducati')		# 末尾添加
print(bicycles)


'''
输出
['trek', 'cannondale', 'redline', 'specialized']
['trek', 'cannondale', 'redline', 'specialized', 'ducati']
'''
```



一个比较常见的做法是这样：

```python
motorcycles = []			#建立一个空列表
motocycles.append('honda')	#尾部添加
motocycles.append('yamaha')
```



理解：其实这和我C++开vector然后不停push_back基本一样



##### 在列表中插入元素

使用insert()，需要指定插入位置和值。

```python
bicycles = ['trek','cannondale','redline','specialized']
bicycles.insert(0,'ducati')		#在索引为0的位置插入'ducati'
print(bicycles)
```

随着它的插入，列表元素位置会进行移动。

理解：Python在这方面似乎并不在乎，而C却不行，所以C把它分成了链表和数组。



#### 删除列表元素

del,pop...





### 列表组织



### 遍历列表

这里的分类很混乱，我得后期自己调整。



#### 创建数值列表

##### 使用函数range()

Python函数range()让你能轻松生成一系列数字。



示例

```python
for value in range(1,5):		#range()生成一系列有序数字，遵循左闭右开
    print(value)
    
# 输出
1 2 3 4(我不写换行了)
```



##### 使用range()创建数字列表

方法：使用range()生成数字，再用list()把range()结果转换成列表



示例

```python
numbers = list(range(1,6))		#双参range生成列表
print(numbers)

# 输出
[1, 2, 3, 4, 5]

# 此外，range()还可以三参，即low,high,pace，再指定步长。
even_numbers = list(range(2,11,2))
print(even_numbers)

# 输出
[2, 4, 6, 8, 10]
```



##### 数字列表常用统计计算

* min(digits)	返回数字列表digits中的最小值
* max(digits)    最大值
* sum(digits)     求和







#### 列表解析(常见代码结构)



我们平常生成一个有些操作的列表。

比如，生成前10个数平方列表。

```python
squares = []
for value in range(1,11):
    square = value**2
    squares.append(square)
    
print(squares)

# 输出
[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
```



但其实你一行代码就可以做到。

列表解析将for循环和创建新元素的代码合并成一行，并自动附加新元素。

上面代码的修改版本

```python
squares = [value**2 for value in range(1,11)]
print(squares)
```



适应于要通过循环来创建一个列表的情况。

循环还是那样写，放在后面。

每次添加的值和循环遍历value的关系放在前面。



格式：

首先指定一个描述性列表名，如squares；然后，指定一个左方括号，并定义一个表达式，用于生成你要存储的列表中的值。在这个示例中，表达式为value**2，它计算平方值。

接下来，编写一个for循环，用于给表达式提供值，再加上右方括号。在这个示例中，for循环为for value in range(1,11)，它将值1~10提供给表达式value**2。

注意：这里for语句末尾无冒号。







#### 使用列表的一部分

我们还可以处理列表的部分元素------Python称之为**切片**。

