### 定义

K最近邻法(KNN，K-Nearest Neighbour)：分类算法中最简单的算法之一，其核心思想是如果离某一个样本最近的k个样本中大多数属于某一个类别，则该样本也属于这个类别，并具有这个类别上样本的特性。

KNN不但可以预测分类，还可以做回归分析(预测具体的值)。

理解：预测回归是什么？是不是因为判别了类别之后，我就可以找到它附近最近的节点，然后近似认为那个的特征就和它的差不了多少，于是近似？



### 算法步骤

![image-20210726153953642](https://raw.githubusercontent.com/Rainiwalk/Rain_image/main/2021/20210726153953.png)





#### 1.常见距离运算公式

![image-20210726154816226](https://raw.githubusercontent.com/Rainiwalk/Rain_image/main/2021/20210726154816.png)

**我们平常还是最常用欧式距离。**

曼哈顿距离就是横坐标差的绝对值+纵坐标差的绝对值。

余弦相似度就是看二者的夹角

注：K的取值不宜过大，一般使用**交叉验证**来确定，本例选为10.



#### 2and3.求解r与所有样本点距离

![image-20210726155140684](https://raw.githubusercontent.com/Rainiwalk/Rain_image/main/2021/20210726155140.png)



#### 4.统计这k个样本的分类，确定r的分类

![image-20210726155300949](https://raw.githubusercontent.com/Rainiwalk/Rain_image/main/2021/20210726155300.png)





### 优缺点

![image-20210726155426056](https://raw.githubusercontent.com/Rainiwalk/Rain_image/main/2021/20210726155426.png)

及时性差：每次都是不确定的，都要现算

这是一个懒惰算法，它实际上并没有生成一个真正的模型，它只是当新的记录来了我再现算。

