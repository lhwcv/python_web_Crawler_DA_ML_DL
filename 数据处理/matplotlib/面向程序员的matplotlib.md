## 2、 面向程序员的matplotlib

## 2-1、 matplotlib高级常识--面向对象与配置

### 2-1-1、面向对象方式绘图

matplotlib实际上是一套面向对象的绘图库，它所绘制的图表中的每一个绘图元素，例如线条line2D、文字Text、刻度等在内存中都有一个对象与之对应。

### 2-1-2、配置属性

matplotlib所绘制的图表的所有元素均和一个对象对应，因此可以调用这些对象的属性设置方法set\_\*\(\)或者pyplot模块的属性设置函数setp\(\)设置它们的属性值。因此有一个**配置文件**。

### 2-1-3、绘制多个子图

matplotlib里常用类的包含关系为Figure -&gt; Axes -&gt; \(Line2D, Text, etc.\)。 即一个Figure对象可以包含多个子图（Axes），在matplotlib中用Axes对象表示一个绘图区域，可以理解为子图。

子图一般使用subplot\(\)快速绘制包含多个子图的图表，如下：

```py
subplot(numRows,numCols,plotNum)
```

即将整个绘图区域等分为numRows行\*numCols列个子区域，然后 从左到右、从上到下顺序对每个子区域编号，plotNum为子图数。当单个值均小于时，python程序可以将其简写为subplot\(323\)或者subplot\(3，2，3\)等形式。

例如程序：

```py
import matplotlib.pyplot as plt

for idx, color in enumerate('rgbyck'):
    plt.subplot(321+idx,axisbg=color)
plt.show()
```

 结果如下图所示：

![](/assets/subplot_1.png)**绘制多图表：**

当需要同时绘制多副图表，可以给figure\(\)传递一个整数参数指定Figure对象的序号，若此序号指定的Figure对象已经存在，将不创建新的对象，而只是让它成为当前的Figure对象。

举例程序：

```py
import numpy as np
import matplotlib.pyplot as plt
# 创建图表
plt.figure(1)
plt.figure(2)
# 在图二中创建子图
ax1 = plt.subplot(211)
ax2 = plt.subplot(212)
# x为横轴坐标赋值
x = np.linspace(0, 3, 100)

for i in range(5):
    plt.figure(1)
    plt.plot(x, np.exp(i * x / 3))

    plt.sca(ax1)
    plt.plot(x, np.sin(i * x))

    plt.sca(ax2)
    plt.plot(x, np.cos(i * x))
plt.show()
```

 结果：

![](/assets/subplot_同时多幅图.jpg)

### 2-1-4、配置文件

绘制一副图需要对许多对象的属性进行设置，例如：颜色、字体、线型等。一般不设置会有一个缺省配置。matplotlib缺省配置保存在一个名为‘matplotlibrc’的配置文件中，通过修改该文件，可以修改图表的缺省样式。除此之外，配置文件还可以使用rc\_params\(\)，它返回一个配置字典；在matplotlib模块载入时会调用rc\_params\(\)，并把得到的配置字典保存到rcParams变量中，然后使用此进行绘图。

### 2-1-5、显示中文

1、在程序中直接指定字体。  
2、在程序开头修改配置字典rcParams。  
3、修改配置文件。

## 2-2 Artist对象

## 2-3 坐标变换与注释

## 2-4 块、路径和集合

## 2-5 高级绘图函数介绍与部分小技巧



