#### 关于在cmd中直接python报warning的问题

![image-20210716111750138](https://raw.githubusercontent.com/Rainiwalk/Rain_image/main/20210716111757.png)

只需要通过Navigator启动Prompt就好了

![image-20210716111902678](https://raw.githubusercontent.com/Rainiwalk/Rain_image/main/20210716111902.png)





#### Anaconda的地位

它只是一个Python的开发版而已，并不是什么IDE，也就是说，有了它你只不过能在命令行里调用和写Python程序而已。

还是需要Pycharm的。





#### 在Pycharm中导入Conda

![QQ截图20210716145012](https://raw.githubusercontent.com/Rainiwalk/Rain_image/main/20210716150105.png)



第一个那个项目位置有点烦，每次创建新项目还要给他建好文件夹(就算项目的名字)。

下面这个存环境的location不用管，找到下面那个conda就会自己确定。



我的最终结果

![QQ截图20210716145351](https://raw.githubusercontent.com/Rainiwalk/Rain_image/main/20210716150248.png)



但是，配好create之后却报了

python3 check_hostname requires server_hostname

错误。



经网络大佬指点，停下科学上网就ok.



但是那个却没有导入库，好像我是又建立了一个新环境，但是不太对。

总之生成的py3.9库少的可怜。



最后反而是很简单的一步导入interpreter，把Acon里面最浅层的python.exe导入解决了所有问题。

![QQ截图20210716151237](https://raw.githubusercontent.com/Rainiwalk/Rain_image/main/20210716202114.png)

![QQ截图20210716151247](https://raw.githubusercontent.com/Rainiwalk/Rain_image/main/20210716202134.png)

这包就多起来了



执行：Shift+F10



