### 设置图片左对齐

还是左对齐看着方便

方法：文件 - 偏好设置 - 外观 - 打开主题文件夹，选择你使用的主题名.css（默认是Github.css），在最后插入下面的CSS代码，重新打开软件就可以了。

```css
p .md-image:only-child{
    width: auto;
    text-align: inherit;
}
```



理解：就是加了一些css代码，我其实也应该会的

附：但是有人反映导出到pdf又变成居中了，未来可能需要注意！