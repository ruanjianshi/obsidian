# 前置知识

简明介绍：三极管就是小电流控制大电流，如同水龙头利用开关小器件控制来自自来水厂的大水流，而输出用户用水。

## 三极管介绍

三极管，全称应为半导体三极管，也称[双极型晶体管](https://so.csdn.net/so/search?q=双极型晶体管&spm=1001.2101.3001.7020)、晶体三极管，是一种电流控制电流的半导体器件·其作用是<u>把微弱信号放大成幅度值较大的电信号</u>， 也用作无触点开关。晶体三极管，是半导体基本元器件之一，具有电流放大作用，是电子电路的核心元件。三极管是在一块半导体基片上制作两个相距很近的PN结，两个PN结把整块半导体分成三部分，中间部分是**基区**，两侧部分是**发射区**和**集电区**，排列方式有*PNP*和*NPN*两种。

> PNP与NPN两种三极管各引脚的表示：**e（发射极）、b（基极）、c（集电极）**

![img](http://qxmapdepot.xiaoq11.cn/picture/c740ec8a86d0204113856178d750e263.jpeg)

![img](http://qxmapdepot.xiaoq11.cn/picture/48ec02e913a6f0ee2e4e4951f76bd4e2.png)

## 三极管工作原理

​        晶体三极管工作原理可以简单地概括为以下几步：

- 基极输入电流或电压的变化，通过空间电荷区的扩散和漂移作用，产生电子和空穴对。

- 电子和空穴对通过扩散和漂移作用进入集电极和发射极，形成集电极电流和发射极电流。

- 由于发射极电流通过基极电极和集电极电极之间的区域，从而控制了集电极电流的大小。

- 当基极输入电流或电压较小的变化时，发射极电流也会随之变化，进而控制集电极电流的大小。

  ![image-20250303160408900](http://qxmapdepot.xiaoq11.cn/picture/image-20250303160408900.png)

## **三极管的三种工作状态**

### 截止状态

​        当加在三极管发射结的电压小于PN结的导通电压，基极电流为零，集电极电流和发射极电流都为零，三极管这时失去了电流放大作用，集电极和发射极之间相当于开关的断开状态，我们称三极管处于截止状态。

![img](http://qxmapdepot.xiaoq11.cn/picture/20b71ef52c877144fabd168233562f98.jpeg)

### 放大状态

​        当加在三极管发射结的电压大于PN结的导通电压，并处于某一恰当的值时，三极管的发射结正向偏置，集电结反向偏置，这时基极电流对集电极电流起着控制作用，使三极管具有电流放大作用，其电流放大倍数β=ΔIc/ΔIb，这时三极管处放大状态。

![img](http://qxmapdepot.xiaoq11.cn/picture/aa1ab8c3f86ffc422c170e7942171503.jpeg)

### 饱和状态

​        当加在三极管发射结的电压大于PN结的导通电压，并当基极电流增大到一定程度时，集电极电流不再随着基极电流的增大而增大，而是处于某一定值附近不怎么变化，这时三极管失去电流放大作用，集电极与发射极之间的电压很小，集电极和发射极之间相当于开关的导通状态。三极管的这种状态我们称之为饱和导通状态。

![img](http://qxmapdepot.xiaoq11.cn/picture/c54252889474baa8dd2d1b9c42df9c72.jpeg)

# MOS管

![image-20250303164123260](http://qxmapdepot.xiaoq11.cn/picture/image-20250303164123260.png)

![image-20250303164146506](http://qxmapdepot.xiaoq11.cn/picture/image-20250303164146506.png)

![image-20250303164220486](http://qxmapdepot.xiaoq11.cn/picture/image-20250303164220486.png)

![image-20250303164239723](http://qxmapdepot.xiaoq11.cn/picture/image-20250303164239723.png)

![image-20250303164305938](http://qxmapdepot.xiaoq11.cn/picture/image-20250303164305938.png)

![image-20250303164341797](http://qxmapdepot.xiaoq11.cn/picture/image-20250303164341797.png)

![image-20250303164409291](http://qxmapdepot.xiaoq11.cn/picture/image-20250303164409291.png)

## 两个特性

![image-20250303164459351](http://qxmapdepot.xiaoq11.cn/picture/image-20250303164459351.png)

![image-20250303164551227](http://qxmapdepot.xiaoq11.cn/picture/image-20250303164551227.png)

![image-20250303164614561](http://qxmapdepot.xiaoq11.cn/picture/image-20250303164614561.png)

![image-20250303164721655](http://qxmapdepot.xiaoq11.cn/picture/image-20250303164721655.png)

![image-20250303164739351](http://qxmapdepot.xiaoq11.cn/picture/image-20250303164739351.png)

![image-20250303164820994](http://qxmapdepot.xiaoq11.cn/picture/image-20250303164820994.png)

## 常见电路

![image-20250303165239319](http://qxmapdepot.xiaoq11.cn/picture/image-20250303165239319.png)

![image-20250303165315818](http://qxmapdepot.xiaoq11.cn/picture/image-20250303165315818.png)