#### 注释的写法

![image-20210717073303059](https://raw.githubusercontent.com/Rainiwalk/Rain_image/main/2021/20210717073310.png)

下面的Pycharm报提示：PEP 8: E262 inline comment should start with '#'



理解：依稀记得PEP 8好像是Python教程里提到的建议遵循的格式标准

处理：Inline comments should have **one space** before the pound sign (`#`) and the comment itself.

所以只需要在#和评论之间加一个空格就好了



#### 类定义的标准状态

如果类没有继承关系

```python
class DrawTool:		
    """画图类"""
```

如果类有继承关系

```python
class DrawTool(Draw):
    # ...
```



有继承的样子是固定的，无继承时，有时会见到这样的代码：

```python
class DrawTool():
```

就是写了一个括号，而让继承父类位置为空，虽然解释器都可以识别，但还是建议没有继承就不写括号比较好。



#### 注释的位置

我总算明白为什么书中对三引号的注释给出了具体要求，比如在函数或类定义下直接一行，至少现在我在Pycharm中见到了

![image-20210717081152980](https://raw.githubusercontent.com/Rainiwalk/Rain_image/main/2021/20210717081153.png)

这样定义之后，再后续代码中使用鼠标悬停over看解释，这个就会出现在那里，这个是很方便的。

但是对于方法来说，尽管这样会看的更清楚，但是我还是有一些自己的编码习惯，我觉得在方法定义的前一行写上也是蛮好的。

```python
# 画点
def drawPoint(self, x, y):
    plt.scatter(x[:, 0], x[:, 1], c=['g' if i == -1 else 'b' for i in y])
```



#### 类与类定义的间隔要求

其实这也是比较好的一种编码习惯，没有没错，有了更好。

如果你在Pycharm中定义的两个类之间只有一个空行，就会报：

PEP 8: E302 expected 2 blank lines, found 1

而你只需要中间再空一行就好了

**标准认为，两个类之间最好是两个空行**

