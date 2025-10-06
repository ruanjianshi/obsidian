[TOC]

------



# 1.系统架构

## 1.1 **ROS和ROS2是什么**

智能时代，机器人正在向全场景的高度智能化方向进化，这对机器人开发提出了巨大挑战，机器人操作系统ROS应用而生。

那什么是ROS？什么又是ROS2呢？

接下来，我们就一起掀起ROS的神秘面纱，带领大家认识一下机器人开发中这位重量级的嘉宾。

#### **ROS的诞生**

对于越来越复杂的智能机器人系统，已经不是一个人或者一个团队可以独立完成的，如何高效开发机器人，是技术层面上非常重要的一个问题，针对这个问题，一群斯坦福大学的有志青年尝试给出一个答案，那就是**机器人操作系统**。

![image-20220521163450243](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.1_ROS%E5%92%8CROS2%E6%98%AF%E4%BB%80%E4%B9%88/image-20220521163450243.jpg)

2007年，他们诞生了这样一个想法，我们有没有可能做一款个人服务机器人，帮助我们完成洗衣做饭收拾家等一切你不想做的事情，甚至还可以在你无聊的时候，陪你聊天玩耍，最后他们真的做出来了。

当时，他们深知做出这样一款机器人并不容易，机械、电路、软件等都要涉及，而且横跨很多个专业，光靠自己肯定做不到，此时他们诞生了这样一个想法：**既然自己做不到，那为什么不联合所有人一起干呢？**如果设计一套标准的机器人平台和其中的软件，大家都可以在这个平台上做应用开发，既然应用软件都基于同一平台，应用的分享也很容易实现，这就类似别人开发的苹果手机应用，只要你有苹果手机，同样也可以用。

说干就干，初期的机器人原型是用实验室可以找到的木头和一些零部件组成的，后期有了充足的资金，才得以实现图中这款外观精致、性能强悍的机器人——**PR2**，Personal Robot 2代。

![image-20220521163523779](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.1_ROS%E5%92%8CROS2%E6%98%AF%E4%BB%80%E4%B9%88/image-20220521163523779.jpg)

在上图中，我们可以看到PR2机器人已经可以完成叠毛巾、熨烫衣服、打台球、剪头发等一系列复杂的应用功能，以叠毛巾为例，这在当时是轰动机器人圈的重要研究，因为第一次有机器人可以完成柔性物体的处理，虽然效率很低，在100分钟之内只完成了5条毛巾的整理，但是在学术层面却推动机器人向前走了一大步。

这款机器人中的软件框架就是ROS的原型，所以ROS因这款个人服务机器人而生，很快也从中独立出来，成为一款用于更多机器人的软件系统。

#### **ROS的发展**

ROS诞生于2007年的斯坦福大学，这是早期PR2机器人的原型，这个项目很快被一家商业公司Willow Garage看中，类似现在的风险投资一样，他们投了一大笔钱给这群年轻人，PR2机器人在资本的助推下成功诞生。

![image-20220521163555519](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.1_ROS%E5%92%8CROS2%E6%98%AF%E4%BB%80%E4%B9%88/image-20220521163555519.jpg)

2010年，随着PR2机器人的发布，其中的软件正式确定了名称，就叫做机器人操作系统，Robot Operating System，简称为ROS。同年，ROS也肩负着让更多人使用的使命，正式开源。

PR2机器人虽好，但是成本居高不下，几百万的价格让绝大部分开发者望而却步，官方也注意到了这个问题，所以在2011年发布了一款后期成为ROS圈爆款的机器人——**Turtlebot**，这款机器人采用扫地机器人的底盘，加上xbox游戏机中的体感传感器Kinect，直接使用笔记本电脑就可以控制，支持ROS的所有开源功能，关键是价格便宜，随着这款机器人的普及，大大推动了ROS的应用。

从2012年开始，使用ROS的人越来越多，ROS官方也开始每年举办一届ROS开发者大会——**ROS Conference**，简称**ROSCon**，来自全球的开发者会齐聚一堂分享自己使用ROS开发的机器人应用，其中不乏亚马逊、Intel、微软等大公司的身影，近两年因为疫情原因改为线上举办，名称也变为了ROS World。

经历前几年野蛮而快速的增长，ROS逐渐迭代稳定，2014年起，ROS跟随Ubuntu系统，每两年推出一个长期支持版，每个版本支持五年时间，这标志着ROS的成熟，也让ROS加快了普及的步伐。

回到时间轴的起点，ROS的创始团队原本只想做一款个人服务机器人，万万没想到，**ROS被越来越多机器人使用，受限于当初设计的局限性，ROS的问题也逐渐暴露**。为了能够真正设计一款适用于所有机器人的操作系统，ROS2在2017年底正式发布，历经多年迭代，我们终于在2022年5月底，迎来了ROS2第一个长期支持版——**ROS2 Humble**，ROS2已经成熟，我们也进入了一个全新的ROS2时代。

从ROS发展的时间轴中，我们不仅可以了解到ROS的发展过程，更重要的是熟悉ROS和ROS2诞生的原因。

![image-20220521163636582](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.1_ROS%E5%92%8CROS2%E6%98%AF%E4%BB%80%E4%B9%88/image-20220521163636582.jpg)

这里我们也把ROS2发展的时间轴单独提取出来，介于ROS在各种各样机器人中应用的问题，ROS2在2014年提出，2015年开始迭代，2017年推出第一个正式版，此后快速迭代，直到2022年推出了第一个长期支持版，本教程也会在该版本ROS2之上进行讲解。

#### **ROS的特点**

ROS怀揣“**提高机器人软件复用率**”的目标，促使社区快速发展和繁荣，时至今日，ROS已经广泛用于各种机器人的开发，无论是机械臂、移动机器人、水下机器人，还是人形机器人、复合机器人，统统都可以看到ROS的身影，ROS已经成为机器人领域的普遍标准。

![image-20220521163711567](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.1_ROS%E5%92%8CROS2%E6%98%AF%E4%BB%80%E4%B9%88/image-20220521163711567.jpg)

提高机器人软件复用率，这个目标简单来讲就是**不要重新造轮子**。

![image-20220521163724192](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.1_ROS%E5%92%8CROS2%E6%98%AF%E4%BB%80%E4%B9%88/image-20220521163724192.jpg)

正如一家做汽车的公司，从零制造汽车并不是一个明智的做法，他们通常会采购A家的轮子、B家的引擎、C家的多媒体系统，最后把这些整合到一起做成汽车。同理，我们也可以将ROS社区中已有的各种软件集合到一起，在此之上去实现自己的创意，同时还可以将自己的成果分享给别人，这样大家都可以站在巨人的肩膀上，向前走的更远，一步一步，智能机器人才会有更多沉淀和更长远的进步。

![image-20220521163735720](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.1_ROS%E5%92%8CROS2%E6%98%AF%E4%BB%80%E4%B9%88/image-20220521163735720.jpg)

围绕这个核心目标，ROS在自身的设计上也尽量做到了模块化，由**通信机制、开发工具、应用功能、生态系统**四大部分组成。同时ROS具备多项特点，这里的ROS是ROS1和ROS2的总称， 比如：

> - **社区是全球化**的，那就可以集合全人类的智慧来推进机器人的智能化发展；
> - 这些智慧的结晶都会以各种各样的**应用案例在社区中沉淀**下来；
> - ROS本身也是完全开源的，**商业许可证非常宽松**；
> - 对商业应用功能友好，这就代表着公司可以直接使用ROS开发商业化的机器人产品，**缩短了产品的上市时间**；
> - ROS也可以**跨平台使用**，Linux、Windows、嵌入式系统都可以跑；
> - ROS2中也新增了很多**支持工业应用**的新特性和新技术，促使ROS在越来越多领域中被使用。

#### **ROS的社区**

社区是ROS快速发展的核心动力，什么是社区呢？其实就是ROS相关资源的整合方式，比如wiki说明、问答网站、应用源码、论坛讨论等都算是社区中的元素。

ROS全球社区有几个重要网站：

1. answers.ros.org，这是一个ROS问答网站，大家可以在上边提出任何关于ROS的问题，全球很多开发者都很乐意回答我们的问题；
2. wiki.ros.org，这是ROS的维基百科，记录了ROS教程和各种功能包的使用；
3. discourse.ros.org，这是ROS论坛，关于ROS开发的新鲜事都可以在这里发表和查看，比如ROS的活动、新功能包的发布等等。
4. index.ros.org，是ROS各种资源的一个索引网站；
5. packages.ros.org，是ROS功能包存储的数据库。

这几个网站的使用情况基本就可以代表ROS社区的活跃度了。

![image-20220521163925495](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.1_ROS%E5%92%8CROS2%E6%98%AF%E4%BB%80%E4%B9%88/image-20220521163925495.jpg)

上图是近几年ROS社区页面浏览量的增长曲线，从总体趋势上来看，各项增长速度都非常快，wiki作为日常使用最为频繁的网站，使用度无疑是最高的，现在每个月有**150万左右**的访问量，answers和packages现在差不多，每个月有**80万**左右，其他两个不多，四项加起来每个月基本有**250万左右**的访问量，已经是一个活跃度非常棒的社区了。

![image-20220521163936186](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.1_ROS%E5%92%8CROS2%E6%98%AF%E4%BB%80%E4%B9%88/image-20220521163936186.jpg)

从访问人数上来看，上边这张图更为清晰，**wiki每个月有20到25万人使用**，**answers每个月有15万人以上使用**，四项加起来每个月差不多有40多万的使用人数，这些用户绝大部分都是机器人开发者，可以看到ROS使用人数是越来越多了。

总而言之，通过这些数据，我们可以看到的是ROS发展迅猛，正在助推机器人革命这一波大浪潮，大家每一个人在其中都大有可为。

如果你希望学习机器人开发，ROS绝对会成为你开发机器人的神兵利器，本教程也绝对是你的最佳选择。

#### **参考资料**

关于本教程的参考资料，主要推荐这几个网站。

![image-20220521165541742](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.1_ROS%E5%92%8CROS2%E6%98%AF%E4%BB%80%E4%B9%88/image-20220521165541742.jpg)

首先是最为推荐的搜索之王——**Google**，几乎所有问题，都可以在这里解决，作为开发工程师的同学，一定要掌握这个重要工具的使用方法。

其次是开源项目的主阵地——**Github**，ROS和社区中的绝大部分代码，都在这里托管，还有大量可以作为我们学习参考的开源项目都可以在这里找到，也是我们离不开的一个网站。

然后是**古月居**网站，这里有大量ROS机器人开发的技术内容和视频课程，还可以在泡泡板块中提问，也欢迎大家在这里和120万人分享你所学的知识。

最后是**本教程网站**，会提供详细的ROS2入门教程，后续也会不断更新和扩展，努力成为大家学习ROS机器人开发的百科全书，配合课程视频学习，效果会更好。

好啦，欢迎大家来到ROS的世界，从这里开始，我们将一起踏上一段美妙的机器人开发之旅

## **1.2 ROS2对比ROS1**

在学习ROS2之前，你也许听说或使用过ROS1，ROS2从名称上来看，不就是在第二代ROS么，变化能有多大？

![image-20220523111754433](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.2_ROS2%E5%AF%B9%E6%AF%94ROS1/image-20220523111754433.png)

我们就ROS1和ROS2做一个对比，看看这其中的变化到底有多大。

### **ROS1的局限性**

首先来看第一个问题：**为什么会有ROS2？Why ROS2？**

![image9](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.2_ROS2%E5%AF%B9%E6%AF%94ROS1/image9.png)

当然是因为ROS1有一些问题了，具体是什么问题呢？从ROS发展的历史中，我们似乎可以找到答案。

![image-20220523112451704](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.2_ROS2%E5%AF%B9%E6%AF%94ROS1/image-20220523112451704.png)

ROS最早的设计目标就是开发这样一款PR2家庭服务机器人，这款机器人绝大部分时间都是独立工作，为了让他具备充足的能力：

- 它搭载了**工作站级别的计算平台**和各种先进的通信设备，不用担忧算力不够，有足够的实力支持各种复杂的实时运算和处理；
- 由于是单兵作战，通信绝大部分都自己内部完成，那就可以用有线连接，**保证了良好的网络连接**，没有丢数据或者黑客入侵的风险；
- 这台机器人最终虽然小批量生产，但是由于**高昂的成本和售价**，也只能用于学术研究。

![image-20220523112633134](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.2_ROS2%E5%AF%B9%E6%AF%94ROS1/image-20220523112633134.png)

随着ROS的普及，应用ROS的机器人类型已经和PR2机器人有了天翻地覆的问题，也并不具备PR2这样的条件，那原本针对PR2设计的软件框架，就会出现一些问题，比如：

- 要在资源有限的**嵌入式系统**中运行；
- 要在**有干扰的地方**保证通信的可靠性；
- 要做成**产品走向市场**，甚至用在自动驾驶汽车和航天机器人上。

类似的问题不断涌现，致使更加适合各种机器人应用的新一代ROS诞生了，也就是我们课程的主角——ROS2。

------

### **全新的ROS2**

ROS2怀揣变革智能机器人时代的历史使命，在设计之初，就考虑到要满足各种各样机器人应用的需求。

![image24](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.2_ROS2%E5%AF%B9%E6%AF%94ROS1/image24-16532770312471.gif)

1. **多机器人系统**：未来机器人一定不会是独立的个体，机器人和机器人之间也需要通信和协作，ROS2为多机器人系统的应用提供了标准方法和通信机制。
2. **跨平台**：机器人应用场景不同，使用的控制平台也会有很大差异，比如自动驾驶汽车中的算力性能肯定比AMR机器人强很多，为了让所有机器人都可以运行ROS2，ROS2可以跨平台运行于Linux、Windows、MacOS、RTOS，甚至是没有任何系统的微控制器（MCU）上，这样我们就不用纠结自己的控制器能不能用ROS了。
3. **实时性**：机器人运动控制和很多行为策略要求机器人具备实时性，比如机器人要可靠得在100ms内发现前方的行人，或者稳定的在1ms周期内完成运动学、动力学的解算，ROS2为类似这样的实时性需求提供了基本保障。
4. **网络连接**：无论在怎样的网络环境下，ROS2都可以尽量保障机器人大量数据的完整性和安全性，比如在wifi信号不好的时候数据也要尽力发送过去，在有黑客入侵风险的场景下要对数据进行加密解密。
5. **产品化**：，大量机器人已经走向我们的生活，未来还会越来越多，ROS2不仅可以用于机器人研发阶段，还可以直接搭载在产品中，走向消费市场，这对ROS2的稳定性、强壮性也提除了巨大挑战。
6. **项目管理**：机器人开发是一个复杂的系统工程，设计、开发、调试、测试、部署等全流程的项目管理工具和机制，也会在ROS2中体现，更方便我们去开发一款机器人。

要满足这些需求，ROS2的设计和开发工作并不简单，相对手机这样标准化的产品，Android系统也可以尽量做到标准化，但是机器人课时千差万别，**如何能够适合尽量多的机器人，这可能远比开发一个手机系统或者电脑系统更加复杂。**

![image23](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.2_ROS2%E5%AF%B9%E6%AF%94ROS1/image23-16532773958263.gif)

ROS开发者面对的选择有两个，第一个是在ROS1的架构之上，进行修改和优化，类似一个盖好的房子，我们把它打成毛坯房，重新装修翻新一下，但肯定会受制于原本建筑的格局，长远来看并不是最佳选择，他们最终选择了第二种方案，那就是**推倒重来**。

所以ROS2是一个全新的机器人操作系统，在借鉴ROS1成功经验的基础上，对系统架构和软件代码全部进行了重新设计和实现。与ROS1相比，体现在以下几点：

![image-20220523114359304](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.2_ROS2%E5%AF%B9%E6%AF%94ROS1/image-20220523114359304.png)

- **系统架构进行了颠覆性的变化**，ROS1中所有节点都需要在节点管理器ROS Master的管理下进行工作，一旦Master出现问题，系统就面临宕机的风险，ROS2实现了真正的分布式，不再有Master这个角色，借助一种全新的通信框架DDS，为所有节点的通信提供可靠保障。
- **软件API进行了重新设计**，ROS1原有的接口已经无法满足需求，ROS2结合C++最新标准和Python3语言特性，设计了更具通用性的API，虽然导致原有ROS1的代码无法直接在ROS2中运行，但是尽量保留了类似的使用方法，同时提供了大量移植的说明。
- **编译系统进行了升级**，ROS1中使用的rosbuild和catkin问题诸多，尤其是针对代码较多的大项目以及Python编写的项目，编译、链接经常会出错，ROS2对这些问题也进行了优化，重新优化后的编译系统叫做ament和colcon，大家在后续的课程中就会体验到新版编译器的使用方法。

这几点只是框架层面，ROS1和ROS2的明显变化，具体细节如何呢？我们继续给大家分解。

------

### **ROS2 vs ROS1**

#### **系统架构**

![image26](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.2_ROS2%E5%AF%B9%E6%AF%94ROS1/image26-16532775781034.png)

在这张图中，左侧是ROS1，右侧是ROS2，大家注意看两者最明显的变化，那就是**Master**。

- 在ROS1中，应用层里Master这个节点管理器的角色至关重要，所有节点都得听它指挥，类似是一个公司的CEO，有且只有一个，如果这个CEO突然消失，公司肯定会成一团乱麻。ROS2把这个最不稳定的角色请走了，节点可以通过另外一套discovery——**自发现机制**，找到彼此，从而建立稳定的通信连接。
- 中间层是ROS封装好的标准通信接口，我们写程序的时候，会频繁和这些通信接口打交道，比如发布一个图像的数据，接收一个雷达的信息，客户端库会再调用底层复杂的驱动和通信协议，让我们的开发变得更加简单明了。
- 在ROS1中，ROS通信依赖底层的TCP和UDP协议，而在ROS2中，通信协议更换成了更加复杂但也更加完善的**DDS系统**。
- 如果是在进程内需要进行大量数据的通信，ROS1和ROS2都提供了基于**共享内存**的通信方法，只不过名字不太一样而已。
- 最下边是系统层，也就是可以将ROS安装在哪些操作系统上，ROS1主要安装在Linux上，ROS2的可选项就很多了，**Linux、windows、MacOS、RTOS**都可以。

通过这样对比的方式，我们了解了ROS2的整体架构，如果大家有接触过ROS1，这个框架应该并不难理解，如果大家是从ROS2开始学习，先大致有一个印象，通过后续的学习，就会有更加深入的理解。

#### **DDS通信**

![image27](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.2_ROS2%E5%AF%B9%E6%AF%94ROS1/image27.png)

ROS2相比ROS1最大的变化，除了省略了Master之外，应该就是通信系统的变化了。ROS1中基于TCP/UDP的通信系统，频繁诟病于延迟、丢数据、无法加密等问题，ROS2中的DDS在通信层面的功能就丰富多了。

**DDS其实是物联网中广泛应用的一种通信协议**，类似于我们常听说的5G通信一样，DDS是一个国际标准，能够实现该标准的软件系统并不是唯一的，所以我们可以选择多个厂家提供的DDS系统，比如这里的OpenSplice、FastRTPS，还有更多厂家提供的，每一家的性能不同，适用的场景也不同。

不过这就带来一个问题，每个DDS厂家的软件接口肯定是不一样的，如果我们按照某一家的接口写完了程序，想要切换其他厂家的DDS，不是要重新写代码么？这当然不符合ROS提高软件复用率的目标。

为了解决这个问题，ROS2设计了一个**ROS Middleware，简称RMW**，也就是指定一个标准的接口，比如如何发数据，如何收数据，数据的各种属性如何配置，都定义好了，如果厂家想要接入ROS社区，就得按照这个标准写一个适配的接口，把自家的DDS给移植过来，这样就把问题交给了最熟悉自家DDS的厂商。对于我们这些用户来讲，某一个DDS用的不爽，只要安装另一个，然后做一个简单的配置，程序一行的都不用改，轻松更换底层的通信系统。

举一个例子，比如我们在产品开发时，可以先用开源版本的DDS满足基本需求，部署交付的产品时，再更换为商业版本更稳定的DDS，这样可以减少开发成本。

![image28](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.2_ROS2%E5%AF%B9%E6%AF%94ROS1/image28-16532776651855.png)

总之，DDS的加入，让ROS2系统更加稳定，也更加灵活，当然复杂度也会高一些。这样，我们不用再纠结ROS的通信系统是否稳定、该如何优化等问题，更多精力都可以放在其他三个部分，专注优化我们的机器人应用功能。

#### **核心概念**

ROS1应用已经非常广泛，全球有几百万开发者，大家已经熟悉了ROS1的开发方式以及其中的很多概念。ROS2尽量保留了这些概念，便于开发者从ROS1迁移到ROS2。

![image-20220523114814371](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.2_ROS2%E5%AF%B9%E6%AF%94ROS1/image-20220523114814371.png)

如果各位熟悉ROS1，这里的概念应该并不陌生，在ROS2中，这些概念依然存在，意义也几乎一致，在本课程的第二个部分，我们就会一一讲解这些概念的含义和使用方法，没有学习过ROS的小伙伴也不用担心。

#### **编码方式**

再来看看编码，同样是一个发布者的程序，ROS1和ROS2的实现版本如两个图片所示。

![image-20220523114851763](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.2_ROS2%E5%AF%B9%E6%AF%94ROS1/image-20220523114851763.png)

总体而言，ROS2会用到更多面向对象的实现方法和语言特性，从编程语言的角度来讲，难度确实会提高一些，不过当我们迈过这道坎之后，就会发现我们写的程序会更具备可读性和可移植性，也会更接接近真实企业中机器人软件开发的过程。

具体如何编码，大家暂且稍安勿躁，切记不要搬来一本大部头的编程语言教程，一页一页学习，更好的方式是在项目开发的过程中一边用一边学，后续课程我们也会带领大家一步一步来操作。

#### **命令行**

最后我们再对比下ROS开发中最为常用的一种工具——命令行。

![image-20220523114915528](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.2_ROS2%E5%AF%B9%E6%AF%94ROS1/image-20220523114915528.png)

ROS1中的命令行相对分散，每一个功能都是一个独立的命令，比如rosrun启动某一个节点，rostopic控制话题相关的功能。

ROS2对命令行做了大幅度的集成，所有命令都集成在一个ros2的主命令中，比如ros2 run，表示启动某一个节点，ros2 topic表示话题相关的功能。

除此之外，ros2命令行也会有更多功能，我们在后续教程中陆续揭秘。

------

好啦，以上，我们把ROS2和ROS1做了对比，总结而言就是：

- **节点干掉了Master**
- **通信换成了DDS**
- **核心概念没变化**
- **编程难度有上升**

如果大家初次上手就选择了ROS2，现有一个大致印象即可，跟随教程，你就会慢慢理解这些特性。

## 1.3 **ROS2安装方法**

本节，我们一起安装ROS2，安装前先要了解一下ROS2底层最重要的一种操作系统——Linux。

### **Linux系统简介**

时间回到1991年，一位热爱计算机的芬兰大学生**林纳斯**，在熟悉了操作系统原理和unix系统后，决定自己动手做一个，实践是检验真理的唯一标准，说干就干，他参考已有的一些通用标准，重新设计了一套操作系统内核，不仅可以实现多用户、多任务的管理，还可以兼容unix原有的应用程序。最重要的是，他把这套尚不成熟的操作系统分享到了互联网上，并用自己的名字命名了这套系统，也就是**Linux**。

![image-20220523190154911](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.3_ROS2%E5%AE%89%E8%A3%85%E6%96%B9%E6%B3%95/image-20220523190154911.jpg)

原本出于个人爱好的Linux系统通过互联网快速传播，更多爱好者看到Linux之后，也激发了乐于分享的热情，就把使用过程中的问题和修复方法做了反馈。

一石激起千层浪，越来越多人加入到了Linux维护的行列当中，一个原本功能有限、bug很多的操作系统，快速强大起来，**伴随其中发扬光大的是开源精神**。

与Windows系统收费，或MacOS硬件绑定的模式不同，**Linux是一套免费并且开放源代码的操作系统**，任何人都可以使用或者提交反馈，这就吸引了大量的开发者、爱好者，甚至很多企业，现在，每年对Linux系统提交的代码量已经成为衡量一个大公司技术实力的重要指标之一。

Linux发展迅猛，已经成为了性能稳定的多用户操作系统，也是ROS2依赖的重要底层系统。虽然ROS2目前也支持Windows、MacOS，但对Linux系统的支持最好，在本教程中，我们主要讲解Linux之上的ROS2使用方法，其他系统原理也基本相同。

所以在使用ROS2之前，我们需要先安装Linux，此时会出现另外一个概念——**发行版**。

![image-20220523190248546](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.3_ROS2%E5%AE%89%E8%A3%85%E6%96%B9%E6%B3%95/image-20220523190248546.jpg)

什么叫发行版呢？准确来讲，我们提到的**Linux应该叫做操作系统内核**，并没有可视化界面，发行版就是给这个内核加上华丽的外衣，把操作界面和各种应用软件放到一起，打包成我们安装系统的镜像。

![image-20220523190433729](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.3_ROS2%E5%AE%89%E8%A3%85%E6%96%B9%E6%B3%95/image-20220523190433729.jpg)

所以一般情况下，我们常用到的Linux系统，都是各种各样的发行版，比如Ubuntu、Fedora、RedHat等等，每一个发行版都有其适用的场景，比如RedHat适合商业应用、CentOS适合服务器、Ubuntu、Fedora适合个人使用等，每一个版本的界面不太一样，但核心都是Linux，操作方法基本相同。

------

### **Ubuntu系统简介**

我们后续课程使用到的Linux发行版就是**ubuntu系统**。

![image-20220523190511789](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.3_ROS2%E5%AE%89%E8%A3%85%E6%96%B9%E6%B3%95/image-20220523190511789.jpg)

Ubuntu诞生于2004年10月份，**每六个月发布一个新版本**，用户可以一直免费升级使用，我们常用的浏览器、文件编辑器、通讯软件等一应俱全。在软件开发领域，无论是互联网开发，还是人工智能开发，还是大家关注的机器人开发，Ubuntu都占据绝对重要的位置。

Ubuntu的版本变动比较快，如何选择合适自己使用的版本很重要，因为其中各种软件版本不同会直接影响我们上层应用的移植效果。在选择版本的时候，大家可以关注一下紧随其后的编号，比如Ubuntu22.04。22代表2022年，04表示2022年的4月份发布，除了04还可能会出现的是10，就是10月份发布，所以从数字编号上就可以看出各个版本发布的顺序。

![image-20220526082937949](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.3_ROS2%E5%AE%89%E8%A3%85%E6%96%B9%E6%B3%95/image-20220526082937949.jpg)

但是这样依然会有很多版本，为了让更多开发者有一个稳定的系统环境，Ubuntu每隔两年的4月份会发布一个长期支持版，后缀会加LTS，保证5年之内持续维护更新，比如Ubuntu20.04 LTS，Ubuntu22.04 LTS，除此之外的版本都是普通版，只维护18个月，所以大家在选择时，**优先考虑长期支持版**。

![image-20220523190539261](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.3_ROS2%E5%AE%89%E8%A3%85%E6%96%B9%E6%B3%95/image-20220523190539261.jpg)

在本教程中，我们以**Ubuntu22.04**为例进行讲解，大家也可以选择其他长期支持版本。

好了，大家一定已经摩拳擦掌想要试一试Ubuntu了，安装方法很多，如果你之前已经熟悉Linux，建议在电脑上硬盘安装Ubuntu，这样可以发挥出硬件最大的性能，如果你是第一次接触Linux，建议在已有的windows上通过虚拟机安装，未来熟悉之后再考虑硬盘安装。

![image-20220526082404826](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.3_ROS2%E5%AE%89%E8%A3%85%E6%96%B9%E6%B3%95/image-20220526082404826.jpg)

这里我们主要介绍虚拟机中的安装方法，大家也可以参考课程资料或网络资料，自行考虑硬盘安装。

------

### **Ubuntu虚拟机安装**

虚拟机是一个软件，可以在已有系统之上，构建另外一个虚拟的系统，让多个操作环境同时运行。

这里我们采用的虚拟机软件叫做vmware，下载地址如下，安装步骤和其他软件相同，请大家自行下载并安装：

https://www.vmware.com/products/workstation-pro/workstation-pro-evaluation.html

准备工作完成后，就可以开始系统安装啦，安装步骤如下：

#### 1. 下载系统镜像

下载链接：https://ubuntu.com/download/desktop

![image12](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.3_ROS2%E5%AE%89%E8%A3%85%E6%96%B9%E6%B3%95/image12.jpg)

#### 2. 在虚拟机中创建系统

![image-20220523191817446](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.3_ROS2%E5%AE%89%E8%A3%85%E6%96%B9%E6%B3%95/image-20220523191817446.jpg)

#### 3. 设置虚拟机硬盘大小

![image-20220523191849728](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.3_ROS2%E5%AE%89%E8%A3%85%E6%96%B9%E6%B3%95/image-20220523191849728.jpg)

#### 4. 设置Ubuntu镜像路径

![image-20220523191911217](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.3_ROS2%E5%AE%89%E8%A3%85%E6%96%B9%E6%B3%95/image-20220523191911217.jpg)

#### 5. 启动虚拟机

![image16](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.3_ROS2%E5%AE%89%E8%A3%85%E6%96%B9%E6%B3%95/image16.jpg)

#### 6. 设置用户名和密码

![image17](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.3_ROS2%E5%AE%89%E8%A3%85%E6%96%B9%E6%B3%95/image17.jpg)

#### 7. 等待系统安装

![image18](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.3_ROS2%E5%AE%89%E8%A3%85%E6%96%B9%E6%B3%95/image18.jpg)

#### 8. 完成安装

![image19](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.3_ROS2%E5%AE%89%E8%A3%85%E6%96%B9%E6%B3%95/image19.jpg)

Ubuntu系统安装好后，大家可以先随意使用熟悉一下。

------

### **ROS2系统安装**

接下来，我们就可以把ROS2安装到Ubuntu系统中了。安装步骤如下：

#### 1. 设置编码

```
$ sudo apt update && sudo apt install locales
$ sudo locale-gen en_US en_US.UTF-8
$ sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8 
$ export LANG=en_US.UTF-8
```

#### 2. 添加源

```
$ sudo apt update && sudo apt install curl gnupg lsb-release 
$ sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg 
$ echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(source /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
```

> 如遇报错“**Failed to connect to raw.githubusercontent.com**”，可参考https://www.guyuehome.com/37844

#### 3. 安装ROS2

```
$ sudo apt update
$ sudo apt upgrade
$ sudo apt install ros-humble-desktop
```

#### 4. 设置环境变量

```
$ source /opt/ros/humble/setup.bash
$ echo " source /opt/ros/humble/setup.bash" >> ~/.bashrc 
```

至此，ROS2就已经在系统中安装好了。

------

### **ROS2示例测试**

为了验证ROS2安装成功，我们可以通过以下示例进行测试。

#### **示例一：命令行示例**

先来试试ROS2最为重要的底层通信系统DDS是否正常吧。

启动第一个终端，通过以下命令启动一个数据的发布者节点：

```
$ ros2 run demo_nodes_cpp talker
```

![image-20220523191236749](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.3_ROS2%E5%AE%89%E8%A3%85%E6%96%B9%E6%B3%95/image-20220523191236749.jpg)

启动第二个终端，通过以下命令启动一个数据的订阅者节点：

```
$ ros2 run demo_nodes_py listener
```

![image-20220523191243490](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.3_ROS2%E5%AE%89%E8%A3%85%E6%96%B9%E6%B3%95/image-20220523191243490.jpg)

如果“Hello World”字符串在两个终端中正常传输，说明通信系统没有问题。

#### **示例二：小海龟仿真示例**

再来试一试ROS中的经典示例——小海龟仿真器。

启动两个终端，分别运行如下指令：

```
$ ros2 run turtlesim turtlesim_node
$ ros2 run turtlesim turtle_teleop_key
```

第一句指令将启动一个蓝色背景的海龟仿真器，第二句指令将启动一个键盘控制节点，在该终端中点击键盘上的“上下左右”按键，就可以控制小海龟运动啦。

![image-20220523191347938](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.3_ROS2%E5%AE%89%E8%A3%85%E6%96%B9%E6%B3%95/image-20220523191347938.jpg)

关于小海龟中蕴藏的ROS奥义，我们在后续教程中将持续探索。

至此，ROS2安装成功。

## 1.4 ROS2命令行操作

在之前运行小海龟案例的时候，我们接触到了ROS2中一种重要的调试工具——**命令行**，大家如果第一次使用，可能会有点不太适应，本节将带领大家进一步使用ROS2中的更多命令，随着学习的深入，大家一定可以感受到命令行的魅力。

![image-20220523191347938](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.4_ROS2%E5%91%BD%E4%BB%A4%E8%A1%8C%E6%93%8D%E4%BD%9C/image-20220523191347938.jpg)

### **Linux中的命令行**

类似于科幻电影中的片段，命令行操作异常炫酷，但是其上手并不容易。为什么这样一种操作看似并不便捷的方式会被一直保留至今呢？无论对于Linux还是ROS来讲，都是必不可少的，大家先来想象一种场景。

![image-20220526083430852](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.4_ROS2%E5%91%BD%E4%BB%A4%E8%A1%8C%E6%93%8D%E4%BD%9C/image-20220526083430852.jpg)

比如我们去商场买衣服，商场里边的衣服虽然多，但并不是每次都可以满足我们的需求，总有一些时候我们逛来逛去就是哪一件都没有看中，此时你看到某一个商家推出服装定制服务，可以根据现有的所有款式，结合我们自己的需求，自主定制，虽然操作起来麻烦一点，但是灵活度高呀，你想要什么样的就可以设计成什么样的，完全不受既定规则的约束。

![image-20220526084719912](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.4_ROS2%E5%91%BD%E4%BB%A4%E8%A1%8C%E6%93%8D%E4%BD%9C/image-20220526084719912.jpg)

在这种场景中，其他商家为我们呈现出已经做好的衣服，就类似于可视化软件一样，都是被精心设计的，但是并不一定能够完全解决我们的问题，这里定制服务中的各种布料、工具等就类似命令行，我们可以使用这些材料和工具灵活定制各种功能，约束就小很多了。

#### **启动方式**

回到命令行来，一系列的命令都是通过字符的方式输入的，怎么输入呢，并不是使用写字本，而是使用专门的软件，叫做**Terminal，终端**。

启动终端的方式有很多种：

- 在应用列表中打开
- 快捷键Ctrl+Alt+T打开
- 鼠标右键选择打开终端

![image-20220524082310466](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.4_ROS2%E5%91%BD%E4%BB%A4%E8%A1%8C%E6%93%8D%E4%BD%9C/image-20220524082310466.jpg)

打开后这个深色背景的窗口就是终端，因为都是命令的输入，所以我们很少会用到鼠标，这也是为什么科幻电影中看到的黑客，笔记本电脑随身带，但是从来看不到鼠标的原因。

初次上手，大家一定会觉得命令行既枯燥，又难以记忆，这很正常，随着我们对这项工具的熟悉，大家一定可以慢慢体会到命令行操作的魅力所在。

至于命令行指令及功能参数的数量，确实多到令人发指，不过不用死机硬背，我们常用的命令也就一二十个，其他命令在需要用的时候搜索一下即可。

#### **常用命令操作**

我们先来体验一下Linux的常用命令，找找感觉。

**cd**

- 语法：cd <目录路径>
- 功能：改变工作目录。若没有指定“目录路径”，则回到用户的主目录

**pwd**

- 语法：pwd
- 功能：此命令显示出当前工作目录的绝对路径

![image-20220526085342690](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.4_ROS2%E5%91%BD%E4%BB%A4%E8%A1%8C%E6%93%8D%E4%BD%9C/image-20220526085342690.jpg)

**mkdir**

- 语法：mkdir [选项] <目录名称>
- 功能：创建一个目录/文件夹

**ls**

- 语法：ls [选项] [目录名称…]
- 功能：列出目录/文件夹中的文件列表

![image-20220526100604610](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.4_ROS2%E5%91%BD%E4%BB%A4%E8%A1%8C%E6%93%8D%E4%BD%9C/image-20220526100604610.jpg)

**gedit**

- 语法：gedit <文件名称>
- 功能：打开gedit编辑器编辑文件，若没有此文件则会新建

![image-20220526100617130](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.4_ROS2%E5%91%BD%E4%BB%A4%E8%A1%8C%E6%93%8D%E4%BD%9C/image-20220526100617130.jpg)

**mv**

- 语法：mv [选项] <源文件或目录> <目地文件或目录>
- 功能：为文件或目录改名或将文件由一个目录移入另一个目录中

**cp**

- 语法：cp [选项] <源文件名称或目录名称> <目的文件名称或目录名称>
- 功能：把一个文件或目录拷贝到另一文件或目录中，或者把多个源文件复制到目标目录中

![image-20220526100626936](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.4_ROS2%E5%91%BD%E4%BB%A4%E8%A1%8C%E6%93%8D%E4%BD%9C/image-20220526100626936.jpg)

**rm**

- 语法：rm [选项] <文件名称或目录名称…>
- 功能：该命令的功能为删除一个目录中的一个或多个文件或目录，它也可以将某个目录及其下的所有文件及子目录均删除。对于链接文件，只是删除了链接，原有文件均保持不变

![image-20220526100643866](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.4_ROS2%E5%91%BD%E4%BB%A4%E8%A1%8C%E6%93%8D%E4%BD%9C/image-20220526100643866.jpg)

**sudo**

- 语法：sudo [选项] [指令]
- 功能：以系统管理员权限来执行指令

![image-20220526100724300](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.4_ROS2%E5%91%BD%E4%BB%A4%E8%A1%8C%E6%93%8D%E4%BD%9C/image-20220526100724300.jpg)

这些命令大家不需要死记硬背，未来一边用一边查，用的多了，就会熟悉。

------

### **ROS2中的命令行**

ROS2命令行的操作机制与Linux相同，不过所有操作都集成在一个ros2的总命令中，后边第一个参数表示不同的操作目的，比如node表示对节点的操作，topic表示对话题的操作，具体操作干什么，还可以在后边继续跟一系列参数内容。

![image-20220524082444725](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.4_ROS2%E5%91%BD%E4%BB%A4%E8%A1%8C%E6%93%8D%E4%BD%9C/image-20220524082444725.jpg)

接下来我们就以小海龟仿真为例，一起感受下ROS2命令行的主要功能，也对ROS2中的核心概念有一个大致了解。

#### **运行节点程序**

想要运行ROS2中某个节点，我们可以使用ros2 run命令进行操作，例如我们要运行海龟仿真节点和键盘控制节点：

```
$ ros2 run turtlesim turtlesim_node
$ ros2 run turtlesim turtle_teleop_key
```

![image-20220524082526919](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.4_ROS2%E5%91%BD%E4%BB%A4%E8%A1%8C%E6%93%8D%E4%BD%9C/image-20220524082526919.jpg)

#### **查看节点信息**

当前运行的ROS系统中都有哪些节点呢？可以这样来查看：

```
$ ros2 node list
```

![image-20220524082550228](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.4_ROS2%E5%91%BD%E4%BB%A4%E8%A1%8C%E6%93%8D%E4%BD%9C/image-20220524082550228.jpg)

如果对某一个节点感兴趣，加上一个info子命令，就可以知道它的详细信息啦：

```
$ ros2 node info /turtlesim 
```

![image-20220524082558457](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.4_ROS2%E5%91%BD%E4%BB%A4%E8%A1%8C%E6%93%8D%E4%BD%9C/image-20220524082558457.jpg)

#### **查看话题信息**

当前系统中都有话题呢，使用如下命令即可查看：

```
$ ros2 topic list
```

![image-20220524082639408](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.4_ROS2%E5%91%BD%E4%BB%A4%E8%A1%8C%E6%93%8D%E4%BD%9C/image-20220524082639408.jpg)

还想看到某一个话题中的消息数据，加上echo子命令试一试：

```
$ ros2 topic echo /turtle1/pose 
```



![image-20220524082647033](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.4_ROS2%E5%91%BD%E4%BB%A4%E8%A1%8C%E6%93%8D%E4%BD%9C/image-20220524082647033.jpg)

#### **发布话题消息**

想要控制海龟动起来，我们还可以直接通过命令行发布话题指令：

```
$ ros2 topic pub --rate 1 /turtle1/cmd_vel geometry_msgs/msg/Twist "{linear: {x: 2.0, y: 0.0, z: 0.0}, angular: {x: 0.0, y: 0.0, z: 1.8}}"
```



![image-20220524082721919](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.4_ROS2%E5%91%BD%E4%BB%A4%E8%A1%8C%E6%93%8D%E4%BD%9C/image-20220524082721919.jpg)

![image-20220524082711671](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.4_ROS2%E5%91%BD%E4%BB%A4%E8%A1%8C%E6%93%8D%E4%BD%9C/image-20220524082711671.jpg)

#### **发送服务请求**

一只海龟太孤单，仿真器还提供改了一个服务——产生海龟，我们试一试服务调用，再来一只海龟：

```
$ ros2 service call /spawn turtlesim/srv/Spawn "{x: 2, y: 2, theta: 0.2, name: ''}"
```

![image-20220524082737479](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.4_ROS2%E5%91%BD%E4%BB%A4%E8%A1%8C%E6%93%8D%E4%BD%9C/image-20220524082737479.jpg)

![image-20220524082745776](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.4_ROS2%E5%91%BD%E4%BB%A4%E8%A1%8C%E6%93%8D%E4%BD%9C/image-20220524082745776.jpg)

#### **发送动作目标**

想要让海龟完成一个具体动作，比如转到指定角度，仿真器中提供的这个action可以帮上忙，通过命令行这样发送动作目标：

```
$ ros2 action send_goal /turtle1/rotate_absolute turtlesim/action/RotateAbsolute "theta: 3"
```

![image-20220524082809463](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.4_ROS2%E5%91%BD%E4%BB%A4%E8%A1%8C%E6%93%8D%E4%BD%9C/image-20220524082809463.jpg)

#### **录制控制命令**

系统运行中的数据有很多，如果想要把某段数据录制下来，回到实验室再复现这段数据如何？ROS2中的rosbag功能还是很好用的，轻松实现数据的录制与播放：

```
$ ros2 bag record /turtle1/cmd_vel
$ ros2 bag play rosbag2_2022_04_11-17_35_40/rosbag2_2022_04_11-17_35_40_0.db3
```

![image-20220524082824817](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.4_ROS2%E5%91%BD%E4%BB%A4%E8%A1%8C%E6%93%8D%E4%BD%9C/image-20220524082824817.jpg)

以上就是ROS2中我们常用的命令啦，每一个命令的子命令还有很多，大家可以自己尝试看看。

## 1.5 ROS2开发环境配置

ROS机器人开发肯定离不开代码编写，我们课程中会给大家提供大量示例源码，这些代码如何查看、编写、编译呢？我们需要先做一些准备，完成开发环境的配置，给大家推荐两款重要的开发工具——vscode和git。

### **Git**

git是一个**版本管理软件**，也是因Linux而生。

![image-20220524082928485](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.5_ROS2%E5%BC%80%E5%8F%91%E7%8E%AF%E5%A2%83%E9%85%8D%E7%BD%AE/image-20220524082928485.png)

Linux发展迅速，成千上万人都会贡献代码，这些代码有些是修复bug的，有些是贡献新硬件驱动的，有些是增加系统新特性的，几千万行的代码人工一行一行审核合并肯定是不可能的，这就需要有一款软件，可以高效管理所有提交的代码，让开发者看到每次提交变更的代码具体是哪里，自动判断会不会有已有代码冲突，以及在多个不同版本之间切换等等功能，所以Linux之父Linus就设计并开发了这款版本管理工具——git，之后也被广泛应用，比如我们常听到的开源项目网站Github，和国内的码云Gitee，都在使用git工具进行众多开源项目的内容管理。

Linux中安装git的方法非常简单，大家直接在终端中使用这一行命令就可以完成安装。

```
$ sudo apt install git
```

#### **下载教程源码**

《ROS2入门21讲》课程源码的下载方式：

```
$ git clone https://gitee.com/guyuehome/ros2_21_tutorials.git
```

![image-20220524083019307](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.5_ROS2%E5%BC%80%E5%8F%91%E7%8E%AF%E5%A2%83%E9%85%8D%E7%BD%AE/image-20220524083019307.png)

下载好的课程代码是这样的，里边有很多文件夹，文件夹中还会有更多文件夹和代码文件，如果用系统自带的文件浏览器和记事本查看，就略显复杂，这里推荐另外一个集成开发环境——VSCode。

------

### **VSCode**

![image-20220524083148659](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.5_ROS2%E5%BC%80%E5%8F%91%E7%8E%AF%E5%A2%83%E9%85%8D%E7%BD%AE/image-20220524083148659.png)

Visual Studio Code，简称VSCode，是微软在2015年推出的一个轻量但功能强大的源代码编辑器，支持 Windows、Linux和 macOS操作系统，扩展组件非常丰富，可以快速搭建成为项目开发的神兵利器。

官方网站：https://code.visualstudio.com/

下载链接：https://code.visualstudio.com/Download

------

#### **VSCode插件配置**

为了便于后续ROS2的开发与调试，我们还可以安装一系列插件，无限扩展VSCode的功能。

##### **中文语言包**

![image-20220524083416831](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.5_ROS2%E5%BC%80%E5%8F%91%E7%8E%AF%E5%A2%83%E9%85%8D%E7%BD%AE/image-20220524083416831.png)

##### **Python插件**

![image-20220524083425555](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.5_ROS2%E5%BC%80%E5%8F%91%E7%8E%AF%E5%A2%83%E9%85%8D%E7%BD%AE/image-20220524083425555.png)

##### **C++插件**

![image-20220524083431845](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.5_ROS2%E5%BC%80%E5%8F%91%E7%8E%AF%E5%A2%83%E9%85%8D%E7%BD%AE/image-20220524083431845.png)

##### **CMake插件**

![image-20220524083440356](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.5_ROS2%E5%BC%80%E5%8F%91%E7%8E%AF%E5%A2%83%E9%85%8D%E7%BD%AE/image-20220524083440356.png)

##### **vscode-icons**

![image-20220524083446105](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.5_ROS2%E5%BC%80%E5%8F%91%E7%8E%AF%E5%A2%83%E9%85%8D%E7%BD%AE/image-20220524083446105.png)

##### **ROS插件**

![image-20220524083451914](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.5_ROS2%E5%BC%80%E5%8F%91%E7%8E%AF%E5%A2%83%E9%85%8D%E7%BD%AE/image-20220524083451914.png)

##### **Msg Language Support**

![image-20220524083458340](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.5_ROS2%E5%BC%80%E5%8F%91%E7%8E%AF%E5%A2%83%E9%85%8D%E7%BD%AE/image-20220524083458340.png)

##### **Visual Studio IntelliCode**

![image-20220524083504097](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.5_ROS2%E5%BC%80%E5%8F%91%E7%8E%AF%E5%A2%83%E9%85%8D%E7%BD%AE/image-20220524083504097.png)

##### **URDF**

![image-20220524083509721](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.5_ROS2%E5%BC%80%E5%8F%91%E7%8E%AF%E5%A2%83%E9%85%8D%E7%BD%AE/image-20220524083509721.png)

##### **Markdown All in One**

![image-20220524083515945](https://book.guyuehome.com/ROS2/1.%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/image/1.5_ROS2%E5%BC%80%E5%8F%91%E7%8E%AF%E5%A2%83%E9%85%8D%E7%BD%AE/image-20220524083515945.png)

VSCode支持的插件众多，以上只作为个人推荐，大家也可以在网上搜索，配置出自己最喜欢的开发环境。

# 2. 核心概念

## 2.1 概念总览

从本节开始，我们将进入第二个篇章，以ROS2的核心概念为线索，详细讲解ROS2的应用开发方法。

![img](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/image-20220523114814371.png)

大家在之前的学习和开发中，应该有接触过某些集成开发环境，比如Visual Studio、Eclipse、Qt Creator等，当我们想要编写程序之前，都会在这些开发环境的工具栏中，点击一个“创建新工程”的选项，此时就产生一个文件夹，后续所有工作产生的文件，都会放置在这个文件夹中，这个文件夹以及里边的内容，就叫做是**工程**。

## 2.2 工作空间

### **工作空间是什么**

类似的，在ROS机器人开发中，我们针对机器人某些功能进行代码开始时，各种编写的代码、参数、脚本等文件，也需要放置在某一个文件夹里进行管理，这个文件夹在ROS系统中就叫做**工作空间**。

所以工作空间是一个存放项目开发相关文件的文件夹，也是**开发过程中存放所有资料的大本营**。

ROS系统中一个典型的工作空间结构如图所示，这个dev_ws就是工作空间的根目录，里边会有四个子目录，或者叫做四个子空间。

![image-20220524111415729](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.1_%E5%B7%A5%E4%BD%9C%E7%A9%BA%E9%97%B4/image-20220524111415729.png)

- **src，代码空间**，未来编写的代码、脚本，都需要人为的放置到这里；
- **build，编译空间**，保存编译过程中产生的中间文件；
- **install，安装空间**，放置编译得到的可执行文件和脚本；
- **log，日志空间**，编译和运行过程中，保存各种警告、错误、信息等日志。

总体来讲，这四个空间的文件夹，我们绝大部分操作都是在src中进行的，编译成功后，就会执行install里边的结果，build和log两个文件夹用的很少。

这里也要强调一点，**工作空间的名称我们可以自己定义**，数量也并不是唯一的，比如：

> 工作空间1：dev_w_a，用于A机器人的开发；
>
> 工作空间2：dev_ws_b，用于B机器人的一部分功能；
>
> 工作空间3：dev_ws_b2，用于开发B机器人另外一些功能。

以上情况是完全允许的，就像是我们在集成开发环境中创建了多个新工程一样，都是并列存在的关系。

### **创建工作空间**

了解了工作空间的概念和结果，接下来我们可以使用如下命令创建一个工作空间，并且下载教程的代码：

```
$ mkdir -p ~/dev_ws/src
$ cd ~/dev_ws/src
$ git clone https://gitee.com/guyuehome/ros2_21_tutorials.git
```

### **自动安装依赖**

我们从社区中下载的各种代码，多少都会有一些依赖，我们可以手动一个一个安装，也可以使用rosdep工具自动安装：

```
$ sudo apt install -y python3-pip
$ sudo pip3 install rosdepc
$ sudo rosdepc init
$ rosdepc update
$ cd ..
$ rosdepc install -i --from-path src --rosdistro humble -y
```

### **编译工作空间**

依赖安装完成后，就可以使用如下命令编译工作空间啦，如果有缺少的依赖，或者代码有错误，编译过程中会有报错，否则编译过程应该不会出现任何错误：

```
$ sudo apt install python3-colcon-ros
$ cd ~/dev_ws/
$ colcon build
```

编译成功后，就可以在工作空间中看到自动生产的build、log、install文件夹了。

![image-20220524111804569](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.1_%E5%B7%A5%E4%BD%9C%E7%A9%BA%E9%97%B4/image-20220524111804569.png)

### **设置环境变量**

编译成功后，为了让系统能够找到我们的功能包和可执行文件，还需要设置环境变量：

```
$ source install/local_setup.sh # 仅在当前终端生效
$ echo " source ~/dev_ws/install/local_setup.sh" >> ~/.bashrc # 所有终端均生效
```

至此，我们就完成了工作空间的创建、编译和配置。

## 2.3 功能包

在下载的教程代码中，大家可以看到有很多不同名称的文件夹，这些在ROS2并不是普通的文件夹，而是叫做**功能包**。

每个机器人可能有很多功能，比如移动控制、视觉感知、自主导航等，如果我们把这些功能的源码都放到一起当然也是可以的，但是当我们想把其中某些功能分享给别人时，就会发现代码都混合到了一起，很难拆分出来。

![image-20220606103223675](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.2_%E5%8A%9F%E8%83%BD%E5%8C%85/image-20220606103223675.png)

举个例子，我们手上有很多红豆、绿豆、黄豆，假设都放在一个袋子里，如果只想把黄豆都拿出来，是不是得在五颜六色的豆子里一颗一颗都找出来，数量越多，你就越头疼；如果我们把不同颜色的豆子放在不同的三个袋子里，需要拿出某种豆子的时候，不就立刻可以找出来了么。

功能包就是这个原理，我们把不同功能的代码划分到不同的功能包中，尽量降低他们之间的耦合关系，当需要在ROS社区中分享给别人的时候，只需要说明这个功能包该如何使用，别人很快就可以用起来了。

所以功能包的机制，是提高ROS中软件复用率的重要方法之一。

### **创建功能包**

如何在ROS2中创建一个功能包呢？我们可以使用这个指令：

```
$ ros2 pkg create --build-type <build-type> <package_name>
```

ros2命令中：

- **pkg**：表示功能包相关的功能；
- **create**：表示创建功能包；
- **build-type**：表示新创建的功能包是C++还是Python的，如果使用C++或者C，那这里就跟ament_cmake，如果使用Python，就跟ament_python；
- **package_name**：新建功能包的名字。

比如在终端中分别创建C++和Python版本的功能包：

```
$ cd ~/dev_ws/src
$ ros2 pkg create --build-type ament_cmake learning_pkg_c               # C++
$ ros2 pkg create --build-type ament_python learning_pkg_python # Python
```

### **编译功能包**

在创建好的功能包中，我们可以继续完成代码的编写，之后需要编译和配置环境变量，才能正常运行：

```
$ cd ~/dev_ws
$ colcon build   # 编译工作空间所有功能包
$ source install/local_setup.bash
```

### **功能包的结构**

功能包并不是普通的文件夹，那如何判断一个文件夹是否是功能包呢？我们来分析下刚才新创建两个功能包的结构。

#### **C++功能包**

首先看下C++类型的功能包，其中必然存在两个文件：**package.xml**和**CMakerLists.txt**。

![image-20220524112122164](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.2_%E5%8A%9F%E8%83%BD%E5%8C%85/image-20220524112122164.png)

package.xml文件的主要内容如下，包含功能包的版权描述，和各种依赖的声明。

![image-20220524112141298](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.2_%E5%8A%9F%E8%83%BD%E5%8C%85/image-20220524112141298.png)

CMakeLists.txt文件是编译规则，C++代码需要编译才能运行，所以必须要在该文件中设置如何编译，使用CMake语法。

![image-20220524112132626](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.2_%E5%8A%9F%E8%83%BD%E5%8C%85/image-20220524112132626.png)

#### **Python功能包**

C++功能包需要将源码编译成可执行文件，但是Python语言是解析型的，不需要编译，所以会有一些不同，但也会有这两个文件：**package.xml**和**setup.py**。

![image-20220524112228806](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.2_%E5%8A%9F%E8%83%BD%E5%8C%85/image-20220524112228806.png)

package.xml文件的主要内容和C++版本功能包一样，包含功能包的版权描述，和各种依赖的声明。

![image-20220524112246102](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.2_%E5%8A%9F%E8%83%BD%E5%8C%85/image-20220524112246102.png)

setup.py文件里边也包含一些版权信息，除此之外，还有“entry_points”配置的程序入口，在后续编程讲解中，我们会给大家介绍如何使用。

![image-20220524112235574](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.2_%E5%8A%9F%E8%83%BD%E5%8C%85/image-20220524112235574.png)

## 

## 2.4 节点

机器人是各种功能的综合体，每一项功能就像机器人的一个工作细胞，众多细胞通过一些机制连接到一起，成为了一个机器人整体。

在ROS中，我们给这些 “细胞”取了一个名字，那就是**节点**。

------

### **通信模型**

完整的机器人系统可能并不是一个物理上的整体，比如这样一个的机器人：

![image-20220526231417594](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.3_%E8%8A%82%E7%82%B9/image-20220526231417594.png)

在机器人身体里搭载了一台计算机A，它可以通过机器人的眼睛——摄像头，获取外界环境的信息，也可以控制机器人的腿——轮子，让机器人移动到想要去的地方。除此之外，可能还会有另外一台计算机B，放在你的桌子上，它可以远程监控机器人看到的信息，也可以远程配置机器人的速度和某些参数，还可以连接一个摇杆，人为控制机器人前后左右运动。

**这些功能虽然位于不同的计算机中，但都是这款机器人的工作细胞，也就是节点，他们共同组成了一个完整的机器人系统。**

- 节点在机器人系统中的职责就是**执行某些具体的任务**，从计算机操作系统的角度来看，也叫做进程；
- 每个节点都是一个可以**独立运行的可执行文件**，比如执行某一个python程序，或者执行C++编译生成的结果，都算是运行了一个节点；
- 既然每个节点都是独立的执行文件，那自然就可以想到，得到这个执行文件的**编程语言可以是不同的**，比如C++、Python，乃至Java、Ruby等更多语言。
- 这些节点是功能各不相同的细胞，根据系统设计的不同，可能位于计算机A，也可能位于计算机B，还有可能运行在云端，这叫做**分布式**，也就是可以分布在不同的硬件载体上；
- 每一个节点都需要有**唯一的命名**，当我们想要去找到某一个节点的时候，或者想要查询某一个节点的状态时，可以通过节点的名称来做查询。

节点也可以比喻是一个一个的工人，分别完成不同的任务，他们有的在一线厂房工作，有的在后勤部门提供保障，他们互相可能并不认识，但却一起推动机器人这座“工厂”，完成更为复杂的任务。

接下来，我们就来看看， 节点这个工作细胞，到底该如何实现。

------

#### **案例一：Hello World节点（面向过程）**

ROS2中节点的实现当然是需要编写程序了，我们从Hello World例程开始，先来实现一个最为简单的节点，功能并不复杂，就是循环打印一个“Hello World”字符串到终端中。

##### **运行效果**

大家先不要着急看代码，是骡子是马，先拉出来溜溜，我们通过ros2 run命令，运行编译好的课程代码，看下这个节点执行的效果如何，然后再来分析代码的实现过程，做到知其然也知其所以然。

```
$ ros2 run learning_node node_helloworld
```

运行成功后，可以在终端中看到循环打印“Hello World”字符串的效果。

![image-20220526231556483](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.3_%E8%8A%82%E7%82%B9/image-20220526231556483.png)

##### **代码解析**

这个节点是如何实现的呢？我们来看下代码。

learning_node/node_helloworld.py

```
#!/usr/bin/env python3 
# -*- coding: utf-8 -*-

"""
@作者: 古月居(www.guyuehome.com)
@说明: ROS2节点示例-发布“Hello World”日志信息, 使用面向过程的实现方式
"""

import rclpy                                   # ROS2 Python接口库
from rclpy.node import Node                    # ROS2 节点类
import time

def main(args=None):                           # ROS2节点主入口main函数
    rclpy.init(args=args)                      # ROS2 Python接口初始化
    node = Node("node_helloworld")             # 创建ROS2节点对象并进行初始化

    while rclpy.ok():                          # ROS2系统是否正常运行
        node.get_logger().info("Hello World")  # ROS2日志输出
        time.sleep(0.5)                        # 休眠控制循环时间

    node.destroy_node()                        # 销毁节点对象    
    rclpy.shutdown()                           # 关闭ROS2 Python接口
```

完成代码的编写后需要设置功能包的编译选项，让系统知道Python程序的入口，打开功能包的setup.py文件，加入如下入口点的配置：

```
    entry_points={
        'console_scripts': [
         'node_helloworld       = learning_node.node_helloworld:main',
        ],
```

**创建节点流程**

代码中出现的函数大家未来会经常用到，大家先不用纠结函数的具体使用方法，更重要的是理解节点的编码流程。

总结一下，想要实现一个节点，代码的实现流程是这样做：

- 编程接口初始化
- 创建节点并初始化
- 实现节点功能
- 销毁节点并关闭接口

大家如果有学习过C++或者Pyhton的话，应该可以发现这里我们使用的是面向过程的编程方法，这种方式虽然实现简单，但是对于稍微复杂一点的机器人系统，就很难做到模块化编码。

#### **案例二：Hello World节点（面向对象）**

所以在ROS2的开发中，我们更**推荐大家使用面向对象的编程方式**，比如刚才的代码就可以改成这样，虽然看上去复杂了一些，但是代码会具备更好的可读性和可移植性，调试起来也会更加方便。

##### **运行效果**

接下来运行一下调整后的节点：

```
$ ros2 run learning_node node_helloworld_class
```

运行成功后，可以还是可以在终端中看到循环打印“Hello World”字符串的效果。

![image-20220527083908311](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.3_%E8%8A%82%E7%82%B9/image-20220527083908311.png)

##### **代码解析**

功能虽然一样，但是程序的结构发生了变化，我们具体看一下这份代码。

learning_node/node_helloworld_class.py

```
#!/usr/bin/env python3
# -*- coding: utf-8 -*-

"""
@作者: 古月居(www.guyuehome.com)
@说明: ROS2节点示例-发布“Hello World”日志信息, 使用面向对象的实现方式
"""

import rclpy                                     # ROS2 Python接口库
from rclpy.node import Node                      # ROS2 节点类
import time

"""
创建一个HelloWorld节点, 初始化时输出“hello world”日志
"""
class HelloWorldNode(Node):
    def __init__(self, name):
        super().__init__(name)                     # ROS2节点父类初始化
        while rclpy.ok():                          # ROS2系统是否正常运行
            self.get_logger().info("Hello World")  # ROS2日志输出
            time.sleep(0.5)                        # 休眠控制循环时间

def main(args=None):                               # ROS2节点主入口main函数
    rclpy.init(args=args)                          # ROS2 Python接口初始化
    node = HelloWorldNode("node_helloworld_class") # 创建ROS2节点对象并进行初始化
    rclpy.spin(node)                               # 循环等待ROS2退出
    node.destroy_node()                            # 销毁节点对象
    rclpy.shutdown()                               # 关闭ROS2 Python接口
```

完成代码的编写后需要设置功能包的编译选项，让系统知道Python程序的入口，打开功能包的setup.py文件，加入如下入口点的配置：

```
    entry_points={
        'console_scripts': [
         'node_helloworld       = learning_node.node_helloworld:main',
         'node_helloworld_class = learning_node.node_helloworld_class:main',
        ],
```

**创建节点流程**

所以总体而言，节点的实现方式依然是这四个步骤，只不过编码方式做了一些改变而已。

- 编程接口初始化
- 创建节点并初始化
- 实现节点功能
- 销毁节点并关闭接口

到这里为止，大家是不是心里还有一个疑惑，机器人中的节点不能只是打印Hello World吧，是不是得完成一些具体的任务。

------

#### **案例三：物体识别节点**

没错，接下来我们就以机器视觉的任务为例，模拟实际机器人中节点的实现过程。

![image-20220527101249842](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.3_%E8%8A%82%E7%82%B9/image-20220527101249842.png)

我们先从网上找到一张苹果的图片，通过编写一个节点来识别图片中的苹果。

##### **运行效果**

在这个例程中，我们将用到一个图像处理的库——OpenCV，运行前请使用如下指令安装：

```
$ sudo apt install python3-opencv
```

然后就可以运行例程啦：

```
$ ros2 run learning_node node_object    #注意修改图片路径后重新编译
```

<details class="attention" open="open" style="box-sizing: inherit; display: flow-root; overflow: visible; padding: 0px 0.6rem; background-color: var(--md-admonition-bg-color); border-width: 0px 0px 0px 0.2rem; border-style: solid; border-color: rgb(255, 145, 0); border-image: initial; border-radius: 0.1rem; box-shadow: var(--md-shadow-z1); color: rgba(0, 0, 0, 0.87); font-size: 0.64rem; margin: 1.5625em 0px; break-inside: avoid; font-family: Roboto, -apple-system, BlinkMacSystemFont, Helvetica, Arial, sans-serif; font-style: normal; font-variant-ligatures: normal; font-variant-caps: normal; font-weight: 400; letter-spacing: normal; orphans: 2; text-align: start; text-indent: 0px; text-transform: none; widows: 2; word-spacing: 0px; -webkit-text-stroke-width: 0px; white-space: normal; text-decoration-thickness: initial; text-decoration-style: initial; text-decoration-color: initial;"><summary style="box-sizing: border-box; cursor: pointer; display: block; min-height: 1rem; background-color: rgba(255, 145, 0, 0.1); border-top: none; border-right: none; border-bottom: none; border-left: 0.2rem none; border-image: initial; font-weight: 700; margin: 0px -0.6rem 0px -0.8rem; padding: 0.4rem 0.6rem 0.4rem 2.2rem; position: relative; border-top-left-radius: 0.1rem; border-top-right-radius: 0.1rem; -webkit-tap-highlight-color: transparent; outline: none;">Attention</summary><p style="box-sizing: border-box;">运行前需要将learning_node/node_object.py代码中的图片路径，修改为实际路径，修改后重新编译运行即可：</p><p style="box-sizing: border-box; margin-bottom: 0.6rem;">image = cv2.imread('<font color="Blue" style="box-sizing: inherit;">/home/hcx/dev_ws/src/ros2_21_tutorials/learning_node/learning_node/apple.jpg</font>')</p></details>

例程运行成功后，会弹出一个可视化窗口，可以看到苹果被成功识别啦，一个绿色框会把苹果的轮廓勾勒出来，中间的绿点表示中心点。

![image-20220527101716204](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.3_%E8%8A%82%E7%82%B9/image-20220527101716204.png)

##### **代码解析**

在这个例程中，我们加入了图像识别的处理过程，模拟一个节点的功能，关于图像处理的具体实现，并不是此处的重点，大家更多要关注我们是如何通过节点的概念来实现一个具体的机器人功能。

learning_node/node_object.py

```
#!/usr/bin/env python3 
# -*- coding: utf-8 -*-

"""
@作者: 古月居(www.guyuehome.com)
@说明: ROS2节点示例-通过颜色识别检测图片中出现的苹果
"""

import rclpy                            # ROS2 Python接口库
from rclpy.node import Node             # ROS2 节点类

import cv2                              # OpenCV图像处理库
import numpy as np                      # Python数值计算库

lower_red = np.array([0, 90, 128])     # 红色的HSV阈值下限
upper_red = np.array([180, 255, 255])  # 红色的HSV阈值上限

def object_detect(image):
    hsv_img = cv2.cvtColor(image, cv2.COLOR_BGR2HSV)      # 图像从BGR颜色模型转换为HSV模型
    mask_red = cv2.inRange(hsv_img, lower_red, upper_red) # 图像二值化

    contours, hierarchy = cv2.findContours(mask_red, cv2.RETR_LIST, cv2.CHAIN_APPROX_NONE) # 图像中轮廓检测

    for cnt in contours:                                  # 去除一些轮廓面积太小的噪声
        if cnt.shape[0] < 150:
            continue

        (x, y, w, h) = cv2.boundingRect(cnt)              # 得到苹果所在轮廓的左上角xy像素坐标及轮廓范围的宽和高
        cv2.drawContours(image, [cnt], -1, (0, 255, 0), 2)# 将苹果的轮廓勾勒出来
        cv2.circle(image, (int(x+w/2), int(y+h/2)), 5, (0, 255, 0), -1)# 将苹果的图像中心点画出来

    cv2.imshow("object", image)                           # 使用OpenCV显示处理后的图像效果
    cv2.waitKey(0)
    cv2.destroyAllWindows()

def main(args=None):                                      # ROS2节点主入口main函数
    rclpy.init(args=args)                                 # ROS2 Python接口初始化
    node = Node("node_object")                            # 创建ROS2节点对象并进行初始化
    node.get_logger().info("ROS2节点示例：检测图片中的苹果")

    image = cv2.imread('/home/hcx/dev_ws/src/ros2_21_tutorials/learning_node/learning_node/apple.jpg')  # 读取图像
    object_detect(image)                                   # 苹果检测
    rclpy.spin(node)                                       # 循环等待ROS2退出
    node.destroy_node()                                    # 销毁节点对象
    rclpy.shutdown()                                       # 关闭ROS2 Python接口
```

完成代码的编写后需要设置功能包的编译选项，让系统知道Python程序的入口，打开功能包的setup.py文件，加入如下入口点的配置：

```
entry_points={
    'console_scripts': [
     'node_helloworld       = learning_node.node_helloworld:main',
     'node_helloworld_class = learning_node.node_helloworld_class:main',
     'node_object           = learning_node.node_object:main',
    ],
```

------

#### **案例四：机器视觉识别节点**

![image-20220527102124347](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.3_%E8%8A%82%E7%82%B9/image-20220527102124347.png)

用图片进行识别好像还不太合理，机器人应该有眼睛呀，没问题，接下来我们就让节点读取摄像头的图像，动态识别其中的苹果，或者类似颜色的物体。

##### **运行效果**

启动一个终端，运行如下节点：

```
$ ros2 run learning_node node_object_webcam #注意设置摄像头
```

<details class="attention" open="open" style="box-sizing: inherit; display: flow-root; overflow: visible; padding: 0px 0.6rem; background-color: var(--md-admonition-bg-color); border-width: 0px 0px 0px 0.2rem; border-style: solid; border-color: rgb(255, 145, 0); border-image: initial; border-radius: 0.1rem; box-shadow: var(--md-shadow-z1); color: rgba(0, 0, 0, 0.87); font-size: 0.64rem; margin: 1.5625em 0px; break-inside: avoid; font-family: Roboto, -apple-system, BlinkMacSystemFont, Helvetica, Arial, sans-serif; font-style: normal; font-variant-ligatures: normal; font-variant-caps: normal; font-weight: 400; letter-spacing: normal; orphans: 2; text-align: start; text-indent: 0px; text-transform: none; widows: 2; word-spacing: 0px; -webkit-text-stroke-width: 0px; white-space: normal; text-decoration-thickness: initial; text-decoration-style: initial; text-decoration-color: initial;"><summary style="box-sizing: border-box; cursor: pointer; display: block; min-height: 1rem; background-color: rgba(255, 145, 0, 0.1); border-top: none; border-right: none; border-bottom: none; border-left: 0.2rem none; border-image: initial; font-weight: 700; margin: 0px -0.6rem 0px -0.8rem; padding: 0.4rem 0.6rem 0.4rem 2.2rem; position: relative; border-top-left-radius: 0.1rem; border-top-right-radius: 0.1rem; -webkit-tap-highlight-color: transparent; outline: none;">Attention</summary><p style="box-sizing: border-box; margin-bottom: 0.6rem;">如果是在虚拟机中操作，需要进行以下设置： 1. 把虚拟机设置为兼容USB3.1； 2. 在可移动设备中将摄像头连接至虚拟机。</p></details>

运行成功后，该节点就可以驱动摄像头，并且实时识别摄像头中的红色物体啦。

![image-20220527102431854](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.3_%E8%8A%82%E7%82%B9/image-20220527102431854.png)

##### **代码解析**

相比之前的程序，这里最大的变化是修改了图片的来源，使用OpenCV中的VideoCapture()来驱动相机，并且周期read摄像头的信息，并进行识别。

learning_node/node_object_webcam.py

```
#!/usr/bin/env python3 
# -*- coding: utf-8 -*-

"""
@作者: 古月居(www.guyuehome.com)
@说明: ROS2节点示例-通过摄像头识别检测图片中出现的苹果
"""

import rclpy                            # ROS2 Python接口库
from rclpy.node import Node             # ROS2 节点类

import cv2                              # OpenCV图像处理库
import numpy as np                      # Python数值计算库

lower_red = np.array([0, 90, 128])     # 红色的HSV阈值下限
upper_red = np.array([180, 255, 255])  # 红色的HSV阈值上限

def object_detect(image):
    hsv_img = cv2.cvtColor(image, cv2.COLOR_BGR2HSV)       # 图像从BGR颜色模型转换为HSV模型
    mask_red = cv2.inRange(hsv_img, lower_red, upper_red)  # 图像二值化

    contours, hierarchy = cv2.findContours(mask_red, cv2.RETR_LIST, cv2.CHAIN_APPROX_NONE) # 图像中轮廓检测

    for cnt in contours:                                   # 去除一些轮廓面积太小的噪声
        if cnt.shape[0] < 150:
            continue

        (x, y, w, h) = cv2.boundingRect(cnt)               # 得到苹果所在轮廓的左上角xy像素坐标及轮廓范围的宽和高
        cv2.drawContours(image, [cnt], -1, (0, 255, 0), 2) # 将苹果的轮廓勾勒出来
        cv2.circle(image, (int(x+w/2), int(y+h/2)), 5, (0, 255, 0), -1)    # 将苹果的图像中心点画出来

    cv2.imshow("object", image)                            # 使用OpenCV显示处理后的图像效果
    cv2.waitKey(50)

def main(args=None):                                       # ROS2节点主入口main函数
    rclpy.init(args=args)                                  # ROS2 Python接口初始化
    node = Node("node_object_webcam")                      # 创建ROS2节点对象并进行初始化
    node.get_logger().info("ROS2节点示例：检测图片中的苹果")

    cap = cv2.VideoCapture(0)


    while rclpy.ok():
        ret, image = cap.read()          # 读取一帧图像

        if ret == True:
            object_detect(image)         # 苹果检测

    node.destroy_node()                  # 销毁节点对象
    rclpy.shutdown()                     # 关闭ROS2 Python接口
```

完成代码的编写后需要设置功能包的编译选项，让系统知道Python程序的入口，打开功能包的setup.py文件，加入如下入口点的配置：

```
entry_points={
    'console_scripts': [
     'node_helloworld       = learning_node.node_helloworld:main',
     'node_helloworld_class = learning_node.node_helloworld_class:main',
     'node_object           = learning_node.node_object:main',
     'node_object_webcam    = learning_node.node_object_webcam:main',
    ],
```

------

### **节点命令行操作**

![image-20220527103004411](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.3_%E8%8A%82%E7%82%B9/image-20220527103004411.png)

节点命令的常用操作如下：

```
$ ros2 node list               # 查看节点列表
$ ros2 node info <node_name>   # 查看节点信息
```

![image-20220527102838748](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.3_%E8%8A%82%E7%82%B9/image-20220527102838748.png)

------

### **思考题**

现在，大家应该熟悉节点这个工作细胞的概念和实现方法了，回到这个机器人系统的框架图，我们还会发现另外一个问题。

![image-20220526232702419](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.3_%E8%8A%82%E7%82%B9/image-20220526232702419.png)

电脑B中的摇杆，要控制机器人运动，这两个节点岂不是应该有某种连接，比如摇杆节点发送一个速度指令给运动节点，收到后机器人开始运动。

同理，如果我们想要改变机器人的速度，负责配置参数的节点就得发送一个指令给运动节点，如果电脑B想要显示机器人看到的图像，电脑A中的摄像头节点就得把图像发送过来。

没错，在一个ROS机器人的系统中，**节点并不是孤立的，他们之间会有很多种机制保持联系**，下一节，我们将给大家介绍这些机制中最为常用的一种。

## 2.5 话题

节点实现了机器人各种各样的功能，但这些功能并不是独立的，之间会有千丝万缕的联系，其中最重要的一种联系方式就是话题，它是**节点间传递数据的桥梁**。

### **通信模型**

以两个机器人节点为例。A节点的功能是驱动相机这个硬件设备，获取得到相机拍摄的图像信息，B节点的功能是视频监控，将相机拍摄到的图像实时显示给用户查看。

![image-20220524141342311](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.4_%E8%AF%9D%E9%A2%98/image-20220524141342311.png)

大家可以想一下，这两个节点是不是必然存在某种关系？没错，节点A要将获取的图像数据传输给节点B，有了数据，节点B才能做这样可视化的渲染。

此时从节点A到节点B传递图像数据的方式，在ROS中，我们就称之为**话题**，它作为一个桥梁，实现了节点之间某一个方向上的数据传输。

#### **发布/订阅模型**

从话题本身的实现角度来看，使用了基于DDS的**发布/订阅模型**，什么叫发布和订阅呢？

![image8](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.4_%E8%AF%9D%E9%A2%98/image8.gif)

话题数据传输的特性是从一个节点到另外一个节点，发送数据的对象称之为**发布者**，接收数据的对象称之为**订阅者**，每一个话题都需要有一个名字，传输的数据也需要有固定的数据类型。

![image-20220527224626092](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.4_%E8%AF%9D%E9%A2%98/image-20220527224626092.png)

打一个比方，大家平时应该也会看微信公众号，比如有一个公众号，它的名字叫做“古月居”，这个古月居就是话题名称，公众号的发布者是古月居的小编，他会把组织好的机器人知识排版成要求格式的公众号文章，发布出去，这个文章格式，就是话题的数据类型。如果大家对这个话题感兴趣，就可以订阅“古月居”，成为订阅者之后自然就可以收到古月居的公众号文章，没有订阅的话，也就无法收到。

类似这样的发布/订阅模型在生活中随处可见，比如订阅报纸、订阅杂志等等。

#### **多对多通信**

![image9](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.4_%E8%AF%9D%E9%A2%98/image9.gif)

大家再仔细想下这些可以订阅的东西，是不是并不是唯一的，我们每个人可以订阅很多公众号、报纸、杂志，这些公众号、报纸、杂志也可以被很多人订阅，没错，ROS里的话题也是一样，发布者和订阅者的数量并不是唯一的，可以称之为是多对多的通信模型。

因为话题是多对多的模型，发布控制指令的摇杆可以有一个，也可以有2个、3个，订阅控制指令的机器人可以有1个，也可以有2个、3个，大家可以想象一下这个画面，似乎还是挺魔性的，如果存在多个发送指令的节点，建议大家要**注意区分优先级**，不然机器人可能不知道该听谁的了。

#### **异步通信**

话题通信还有一个特性，那就是异步，这个词可能有同学是第一次听说？所谓异步，只要是指发布者发出数据后，并不知道订阅者什么时候可以收到，类似古月居公众号发布一篇文章，你什么时候阅读的，古月居根本不知道，报社发出一份报纸，你什么时候收到，报社也是不知道的。这就叫做异步。

异步的特性也让话题更适合用于一些周期发布的数据，比如传感器的数据，运动控制的指令等等，如果某些逻辑性较强的指令，比如修改某一个参数，用话题传输就不太合适了。

#### **消息接口**

最后，既然是数据传输，发布者和订阅者就得统一数据的描述格式，不能一个说英文，一个理解成了中文。在ROS中，话题通信数据的描述格式称之为消息，对应编程语言中数据结构的概念。比如这里的一个图像数据，就会包含图像的长宽像素值、每个像素的RGB等等，在ROS中都有标准定义。

**消息是ROS中的一种接口定义方式**，与编程语言无关，我们也可以通过**.msg**后缀的文件自行定义，有了这样的接口，各种节点就像积木块一样，通过各种各样的接口进行拼接，组成复杂的机器人系统。

------

### **案例一：Hello World话题通信**

了解了话题的基本原理，接下来我们就要开始编写代码啦。

![image-20220524141514506](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.4_%E8%AF%9D%E9%A2%98/image-20220524141514506.png)

还是从Hello World例程开始，我们来创建一个发布者，发布话题“chatter”，周期发送“Hello World”这个字符串，消息类型是ROS中标准定义的String，再创建一个订阅者，订阅“chatter”这个话题，从而接收到“Hello World”这个字符串。

#### **运行效果**

启动第一个终端，运行话题的发布者节点：

```
$ ros2 run learning_topic topic_helloworld_pub
```

![image-20220524141606868](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.4_%E8%AF%9D%E9%A2%98/image-20220524141606868.png)

启动第二个终端，运行话题的订阅者节点：

```
$ ros2 run learning_topic topic_helloworld_sub
```

![image-20220524141614633](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.4_%E8%AF%9D%E9%A2%98/image-20220524141614633.png)

可以看到发布者循环发布“Hello World”字符串消息，订阅者也以几乎同样的频率收到该话题的消息数据。

#### **发布者代码解析**

我们来看下发布者的实现方法。

##### 程序实现

learning_topic/topic_helloworld_pub.py

```
#!/usr/bin/env python3
# -*- coding: utf-8 -*-

"""
@作者: 古月居(www.guyuehome.com)
@说明: ROS2话题示例-发布“Hello World”话题
"""

import rclpy                                     # ROS2 Python接口库
from rclpy.node import Node                      # ROS2 节点类
from std_msgs.msg import String                  # 字符串消息类型

"""
创建一个发布者节点
"""
class PublisherNode(Node):

    def __init__(self, name):
        super().__init__(name)                                    # ROS2节点父类初始化
        self.pub = self.create_publisher(String, "chatter", 10)   # 创建发布者对象（消息类型、话题名、队列长度）
        self.timer = self.create_timer(0.5, self.timer_callback)  # 创建一个定时器（单位为秒的周期，定时执行的回调函数）

    def timer_callback(self):                                     # 创建定时器周期执行的回调函数
        msg = String()                                            # 创建一个String类型的消息对象
        msg.data = 'Hello World'                                  # 填充消息对象中的消息数据
        self.pub.publish(msg)                                     # 发布话题消息
        self.get_logger().info('Publishing: "%s"' % msg.data)     # 输出日志信息，提示已经完成话题发布

def main(args=None):                                 # ROS2节点主入口main函数
    rclpy.init(args=args)                            # ROS2 Python接口初始化
    node = PublisherNode("topic_helloworld_pub")     # 创建ROS2节点对象并进行初始化
    rclpy.spin(node)                                 # 循环等待ROS2退出
    node.destroy_node()                              # 销毁节点对象
    rclpy.shutdown()                                 # 关闭ROS2 Python接口
```

完成代码的编写后需要设置功能包的编译选项，让系统知道Python程序的入口，打开功能包的setup.py文件，加入如下入口点的配置：

```
    entry_points={
        'console_scripts': [
         'topic_helloworld_pub  = learning_topic.topic_helloworld_pub:main',
        ],
    },
```

##### 流程总结

对以上程序进行分析，如果我们想要实现一个发布者，流程如下：

- 编程接口初始化
- 创建节点并初始化
- 创建发布者对象
- 创建并填充话题消息
- 发布话题消息
- 销毁节点并关闭接口

#### **订阅者代码解析**

我们再来看下订阅者的实现方法。

##### 程序实现

learning_topic/topic_helloworld_sub.py

```
#!/usr/bin/env python3
# -*- coding: utf-8 -*-

"""
@作者: 古月居(www.guyuehome.com)
@说明: ROS2话题示例-订阅“Hello World”话题消息
"""

import rclpy                      # ROS2 Python接口库
from rclpy.node   import Node     # ROS2 节点类
from std_msgs.msg import String   # ROS2标准定义的String消息

"""
创建一个订阅者节点
"""
class SubscriberNode(Node):

    def __init__(self, name):
        super().__init__(name)                             # ROS2节点父类初始化
        self.sub = self.create_subscription(\
            String, "chatter", self.listener_callback, 10) # 创建订阅者对象（消息类型、话题名、订阅者回调函数、队列长度）

    def listener_callback(self, msg):                      # 创建回调函数，执行收到话题消息后对数据的处理
        self.get_logger().info('I heard: "%s"' % msg.data) # 输出日志信息，提示订阅收到的话题消息

def main(args=None):                               # ROS2节点主入口main函数
    rclpy.init(args=args)                          # ROS2 Python接口初始化
    node = SubscriberNode("topic_helloworld_sub")  # 创建ROS2节点对象并进行初始化
    rclpy.spin(node)                               # 循环等待ROS2退出
    node.destroy_node()                            # 销毁节点对象
    rclpy.shutdown()                               # 关闭ROS2 Python接口
```

完成代码的编写后需要设置功能包的编译选项，让系统知道Python程序的入口，打开功能包的setup.py文件，加入如下入口点的配置：

```
    entry_points={
        'console_scripts': [
         'topic_helloworld_pub  = learning_topic.topic_helloworld_pub:main',
         'topic_helloworld_sub  = learning_topic.topic_helloworld_sub:main',
        ],
    },
```

##### 流程总结

对以上程序进行分析，如果我们想要实现一个订阅者，流程如下：

- 编程接口初始化
- 创建节点并初始化
- 创建订阅者对象
- 回调函数处理话题数据
- 销毁节点并关闭接口

好啦，Hello World例程大家一定还不过瘾，接下来我们基于话题通信，继续优化下之前的机器视觉例程。

------

### **案例二：机器视觉识别**

在节点概念的讲解过程中，我们通过一个节点驱动了相机，并且实现了对红色物体的识别。功能虽然没问题，但是对于机器人开发来讲，并没有做到程序的模块化，更好的方式是将相机驱动和视觉识别做成两个节点，节点间的联系就是这个图像数据，通过话题周期传输即可。

![image-20220524141708449](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.4_%E8%AF%9D%E9%A2%98/image-20220524141708449.png)

#### **运行效果**

这个图像消息在ROS中是标准定义好的，如果未来要更换另一个相机，只需要修改驱动节点，视觉识别节点完全是软件功能，就可以保持不变了，这种模块化的设计思想，可以更好的保证软件的可移植性。

好啦，说干就干，我们先来看下效果如何？

启动两个终端，分别运行以下两个节点，第一个节点驱动相机并发布图像话题，第二个节点订阅图像话题并实现视觉识别。

```
$ ros2 run learning_topic topic_webcam_pub
$ ros2 run learning_topic topic_webcam_sub
```

将红色物体放入相机范围内，即可看到识别效果。

![image-20220527231048652](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.4_%E8%AF%9D%E9%A2%98/image-20220527231048652.png)

#### **发布者代码解析**

learning_topic/topic_webcam_pub.py

```
#!/usr/bin/env python3
# -*- coding: utf-8 -*-

"""
@作者: 古月居(www.guyuehome.com)
@说明: ROS2话题示例-发布图像话题
"""

import rclpy                        # ROS2 Python接口库
from rclpy.node import Node         # ROS2 节点类
from sensor_msgs.msg import Image   # 图像消息类型
from cv_bridge import CvBridge      # ROS与OpenCV图像转换类
import cv2                          # Opencv图像处理库

"""
创建一个发布者节点
"""
class ImagePublisher(Node):

    def __init__(self, name):
        super().__init__(name)                                           # ROS2节点父类初始化
        self.publisher_ = self.create_publisher(Image, 'image_raw', 10)  # 创建发布者对象（消息类型、话题名、队列长度）
        self.timer = self.create_timer(0.1, self.timer_callback)         # 创建一个定时器（单位为秒的周期，定时执行的回调函数）
        self.cap = cv2.VideoCapture(0)                                   # 创建一个视频采集对象，驱动相机采集图像（相机设备号）
        self.cv_bridge = CvBridge()                                      # 创建一个图像转换对象，用于稍后将OpenCV的图像转换成ROS的图像消息

    def timer_callback(self):
        ret, frame = self.cap.read()                         # 一帧一帧读取图像

        if ret == True:                                      # 如果图像读取成功
            self.publisher_.publish(
                self.cv_bridge.cv2_to_imgmsg(frame, 'bgr8')) # 发布图像消息

        self.get_logger().info('Publishing video frame')     # 输出日志信息，提示已经完成图像话题发布

def main(args=None):                                 # ROS2节点主入口main函数
    rclpy.init(args=args)                            # ROS2 Python接口初始化
    node = ImagePublisher("topic_webcam_pub")        # 创建ROS2节点对象并进行初始化
    rclpy.spin(node)                                 # 循环等待ROS2退出
    node.destroy_node()                              # 销毁节点对象
    rclpy.shutdown()                                 # 关闭ROS2 Python接口
```

完成代码的编写后需要设置功能包的编译选项，让系统知道Python程序的入口，打开功能包的setup.py文件，加入如下入口点的配置：

```
    entry_points={
        'console_scripts': [
         'topic_helloworld_pub  = learning_topic.topic_helloworld_pub:main',
         'topic_helloworld_sub  = learning_topic.topic_helloworld_sub:main',
         'topic_webcam_pub      = learning_topic.topic_webcam_pub:main',
        ],
    },
```

#### **订阅者代码解析**

learning_topic/topic_webcam_sub.py

```
#!/usr/bin/env python3
# -*- coding: utf-8 -*-

"""
@作者: 古月居(www.guyuehome.com)
@说明: ROS2话题示例-订阅图像话题
"""

import rclpy                            # ROS2 Python接口库
from rclpy.node import Node             # ROS2 节点类
from sensor_msgs.msg import Image       # 图像消息类型
from cv_bridge import CvBridge          # ROS与OpenCV图像转换类
import cv2                              # Opencv图像处理库
import numpy as np                      # Python数值计算库

lower_red = np.array([0, 90, 128])      # 红色的HSV阈值下限
upper_red = np.array([180, 255, 255])   # 红色的HSV阈值上限

"""
创建一个订阅者节点
"""
class ImageSubscriber(Node):
    def __init__(self, name):
        super().__init__(name)                                # ROS2节点父类初始化
        self.sub = self.create_subscription(
            Image, 'image_raw', self.listener_callback, 10)   # 创建订阅者对象（消息类型、话题名、订阅者回调函数、队列长度）
        self.cv_bridge = CvBridge()                           # 创建一个图像转换对象，用于OpenCV图像与ROS的图像消息的互相转换

    def object_detect(self, image):
        hsv_img = cv2.cvtColor(image, cv2.COLOR_BGR2HSV)      # 图像从BGR颜色模型转换为HSV模型
        mask_red = cv2.inRange(hsv_img, lower_red, upper_red) # 图像二值化
        contours, hierarchy = cv2.findContours(
            mask_red, cv2.RETR_LIST, cv2.CHAIN_APPROX_NONE)   # 图像中轮廓检测

        for cnt in contours:                                  # 去除一些轮廓面积太小的噪声
            if cnt.shape[0] < 150:
                continue

            (x, y, w, h) = cv2.boundingRect(cnt)              # 得到苹果所在轮廓的左上角xy像素坐标及轮廓范围的宽和高
            cv2.drawContours(image, [cnt], -1, (0, 255, 0), 2)# 将苹果的轮廓勾勒出来
            cv2.circle(image, (int(x+w/2), int(y+h/2)), 5,
                       (0, 255, 0), -1)                       # 将苹果的图像中心点画出来

        cv2.imshow("object", image)                           # 使用OpenCV显示处理后的图像效果
        cv2.waitKey(10)

    def listener_callback(self, data):
        self.get_logger().info('Receiving video frame')     # 输出日志信息，提示已进入回调函数
        image = self.cv_bridge.imgmsg_to_cv2(data, 'bgr8')  # 将ROS的图像消息转化成OpenCV图像
        self.object_detect(image)                           # 苹果检测


def main(args=None):                            # ROS2节点主入口main函数
    rclpy.init(args=args)                       # ROS2 Python接口初始化
    node = ImageSubscriber("topic_webcam_sub")  # 创建ROS2节点对象并进行初始化
    rclpy.spin(node)                            # 循环等待ROS2退出
    node.destroy_node()                         # 销毁节点对象
    rclpy.shutdown()                            # 关闭ROS2 Python接口
```

完成代码的编写后需要设置功能包的编译选项，让系统知道Python程序的入口，打开功能包的setup.py文件，加入如下入口点的配置：

```
    entry_points={
        'console_scripts': [
         'topic_helloworld_pub  = learning_topic.topic_helloworld_pub:main',
         'topic_helloworld_sub  = learning_topic.topic_helloworld_sub:main',
         'topic_webcam_pub      = learning_topic.topic_webcam_pub:main',
         'topic_webcam_sub      = learning_topic.topic_webcam_sub:main',
        ],
    },
```

### **案例三：机器视觉识别优化**

通过话题对原本节点功能的解耦，似乎让视觉识别的例程焕然一新了，不过似乎还有哪里不太对劲，大家有感觉到么？

ROS的目标不是提高软件复用率么，现在视觉识别的节点可以复用了，相机驱动节点好像不行呀，每换一个相机，是不是都得换一个驱动节点？这当然是不可能的！

常用的usb相机驱动一般都是通用的，ROS中也集成了usb相机的标准驱动，我们只需要通过这样一行指令，就可以安装好，无论你用什么样的相机，只要符合usb接口协议，就可以直接使用ROS中的相机驱动节点，发布标准的图像话题了。

```
$ sudo apt install ros-humble-usb-cam
```

这样，我们的代码又得到了进一步精简，刚才自己写的图像发布节点换成了这样一句指令，视觉识别节点不需要做任何变化。

```
$ ros2 run usb_cam usb_cam_node_exe
$ ros2 run learning_topic topic_webcam_sub
```

![image-20220527231048652](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.4_%E8%AF%9D%E9%A2%98/image-20220527231048652.png)

------

### **话题命令行操作**

话题命令的常用操作如下：

```
$ ros2 topic list                # 查看话题列表
$ ros2 topic info <topic_name>   # 查看话题信息
$ ros2 topic hz <topic_name>     # 查看话题发布频率
$ ros2 topic bw <topic_name>     # 查看话题传输带宽
$ ros2 topic echo <topic_name>   # 查看话题数据
$ ros2 topic pub <topic_name> <msg_type> <msg_data>   # 发布话题消息
```

![image-20220524141906673](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.4_%E8%AF%9D%E9%A2%98/image-20220524141906673.png)

### **思考题**

![image-20220524141933643](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.4_%E8%AF%9D%E9%A2%98/image-20220524141933643.png)

关于话题通信的原理和实现方法我们就讲到这里，给大家留一个思考题：话题通信的特性是单向传输，适合周期性的数据传递，对于一个复杂的机器人系统来讲，这种特性肯定无法满足所有数据传输的需求，大家是否能够举几个例子，是话题通信无法完成的呢？

## 2.6 服务

话题通信可以实现多个ROS节点之间数据的单向传输，使用这种异步通信机制，发布者无法准确知道订阅者是否收到消息，本讲我们将一起学习ROS另外一种常用的通信方法——**服务**，可以实现类似**你问我答的同步通信**效果。

### **通信模型**

在之前的课程中，我们通过一个节点驱动相机，发布图像话题，另外一个节点订阅图像话题，并实现对其中红色物体的识别，此时我们可以按照图像识别的频率，周期得到物体的位置。

![image-20220527232959464](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.5_%E6%9C%8D%E5%8A%A1/image-20220527232959464.png)

这个位置信息可以继续发给机器人的上层应用使用，比如可以跟随目标运动，或者运动到目标位置附近。此时，我们并不需要这么高的频率一直订阅物体的位置，而是更希望在需要这个数据的时候，发一个查询的请求，然后尽快得到此时目标的最新位置。

这样的通信模型和话题单向传输有所不同，变成了发送一个请求，反馈一个应答的形式，好像是你问我答一样，这种通信机制在ROS中成为**服务，Service**。

#### **客户端/服务器模型**

从服务的实现机制上来看，这种你问我答的形式叫做**客户端/服务器模型**，简称为CS模型，客户端在需要某些数据的时候，针对某个具体的服务，发送请求信息，服务器端收到请求之后，就会进行处理并反馈应答信息。

![image8](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.5_%E6%9C%8D%E5%8A%A1/image8.gif)

这种通信机制在生活中也很常见，比如我们经常浏览的各种网页，此时你的电脑浏览器就是客户端，通过域名或者各种操作，向网站服务器发送请求，服务器收到之后返回需要展现的页面数据。

#### **同步通信**

这个过程一般要求越快越好，假设服务器半天没有反应，你的浏览器一直转圈圈，那有可能是服务器宕机了，或者是网络不好，所以相比话题通信，在服务通信中，客户端可以通过接收到的应答信息，判断服务器端的状态，我们也称之为同步通信。

#### **一对多通信**

![image9](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.5_%E6%9C%8D%E5%8A%A1/image9.gif)

比如古月居这个网站，服务器是唯一存在的，并没有多个完全一样的古月居网站，但是可以访问古月居网站的客户端是不唯一的，大家每一个人都可以看到同样的界面。所以服务通信模型中，服务器端唯一，但客户端可以不唯一。

#### **服务接口**

和话题通信类似，服务通信的核心还是要传递数据，数据变成了两个部分，一个**请求的数据**，比如请求苹果位置的命令，还有一个**反馈的数据**，比如反馈苹果坐标位置的数据，这些数据和话题消息一样，在ROS中也是要标准定义的，话题使用.msg文件定义，服务使用的是.srv文件定义，后续我们会给大家介绍定义的方法。

### **案例一：加法求解器**

大家现在对ROS服务通信应该有了基本了解，接下来我们就要开始编写代码啦。还是从一个相对简单的例程开始，也是ROS官方的一个例程，通过服务实现一个加法求解器的功能。

![image-20220527233716400](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.5_%E6%9C%8D%E5%8A%A1/image-20220527233716400.png)

当我们需要计算两个加数的求和结果时，就通过客户端节点，将两个加数封装成请求数据，针对服务“add_two_ints”发送出去，提供这个服务的服务器端节点，收到请求数据后，开始进行加法计算，并将求和结果封装成应答数据，反馈给客户端，之后客户端就可以得到想要的结果啦。

#### **运行效果**

我们一起操作下这个例程，并且看下代码的实现原理。

启动两个终端，并运行如下节点，第一个节点是服务端，等待请求数据并提供求和功能，第二个节点是客户端，发送传入的两个加数并等待求和结果。

```
$ ros2 run learning_service service_adder_server
$ ros2 run learning_service service_adder_client 2 3
```

![image-20220527233928009](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.5_%E6%9C%8D%E5%8A%A1/image-20220527233928009.png)

![image-20220527233916665](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.5_%E6%9C%8D%E5%8A%A1/image-20220527233916665.png)

#### **客户端代码解析**

我们来看下客户端的实现方法。

##### **程序实现**

learning_service/service_adder_client.py

```
#!/usr/bin/env python3
# -*- coding: utf-8 -*-

"""
@作者: 古月居(www.guyuehome.com)
@说明: ROS2服务示例-发送两个加数，请求加法器计算
"""

import sys

import rclpy                                  # ROS2 Python接口库
from rclpy.node   import Node                 # ROS2 节点类
from learning_interface.srv import AddTwoInts # 自定义的服务接口

class adderClient(Node):
    def __init__(self, name):
        super().__init__(name)                                       # ROS2节点父类初始化
        self.client = self.create_client(AddTwoInts, 'add_two_ints') # 创建服务客户端对象（服务接口类型，服务名）
        while not self.client.wait_for_service(timeout_sec=1.0):     # 循环等待服务器端成功启动
            self.get_logger().info('service not available, waiting again...') 
        self.request = AddTwoInts.Request()                          # 创建服务请求的数据对象

    def send_request(self):                                          # 创建一个发送服务请求的函数
        self.request.a = int(sys.argv[1])
        self.request.b = int(sys.argv[2])
        self.future = self.client.call_async(self.request)           # 异步方式发送服务请求

def main(args=None):
    rclpy.init(args=args)                        # ROS2 Python接口初始化
    node = adderClient("service_adder_client")   # 创建ROS2节点对象并进行初始化
    node.send_request()                          # 发送服务请求

    while rclpy.ok():                            # ROS2系统正常运行
        rclpy.spin_once(node)                    # 循环执行一次节点

        if node.future.done():                   # 数据是否处理完成
            try:
                response = node.future.result()  # 接收服务器端的反馈数据
            except Exception as e:
                node.get_logger().info(
                    'Service call failed %r' % (e,))
            else:
                node.get_logger().info(          # 将收到的反馈信息打印输出
                    'Result of add_two_ints: for %d + %d = %d' % 
                    (node.request.a, node.request.b, response.sum))
            break

    node.destroy_node()                          # 销毁节点对象
    rclpy.shutdown()                             # 关闭ROS2 Python接口
```

完成代码的编写后需要设置功能包的编译选项，让系统知道Python程序的入口，打开功能包的setup.py文件，加入如下入口点的配置：

```
    entry_points={
        'console_scripts': [
         'service_adder_client  = learning_service.service_adder_client:main',
        ],
    },
```

##### **流程总结**

对以上程序进行分析，如果我们想要实现一个客户端，流程如下：

- 编程接口初始化
- 创建节点并初始化
- 创建客户端对象
- 创建并发送请求数据
- 等待服务器端应答数据
- 销毁节点并关闭接口

#### **服务端代码解析**

至于服务器端的实现，有点类似话题通信中的订阅者，并不知道请求数据什么时间出现，也用到了回调函数机制。

##### **程序实现**

learning_service/service_adder_server.py

```
#!/usr/bin/env python3
# -*- coding: utf-8 -*-

"""
@作者: 古月居(www.guyuehome.com)
@说明: ROS2服务示例-提供加法器的服务器处理功能
"""

import rclpy                                     # ROS2 Python接口库
from rclpy.node   import Node                    # ROS2 节点类
from learning_interface.srv import AddTwoInts    # 自定义的服务接口

class adderServer(Node):
    def __init__(self, name):
        super().__init__(name)                                                           # ROS2节点父类初始化
        self.srv = self.create_service(AddTwoInts, 'add_two_ints', self.adder_callback)  # 创建服务器对象（接口类型、服务名、服务器回调函数）

    def adder_callback(self, request, response):   # 创建回调函数，执行收到请求后对数据的处理
        response.sum = request.a + request.b       # 完成加法求和计算，将结果放到反馈的数据中
        self.get_logger().info('Incoming request\na: %d b: %d' % (request.a, request.b))   # 输出日志信息，提示已经完成加法求和计算
        return response                          # 反馈应答信息

def main(args=None):                             # ROS2节点主入口main函数
    rclpy.init(args=args)                        # ROS2 Python接口初始化
    node = adderServer("service_adder_server")   # 创建ROS2节点对象并进行初始化
    rclpy.spin(node)                             # 循环等待ROS2退出
    node.destroy_node()                          # 销毁节点对象
    rclpy.shutdown()                             # 关闭ROS2 Python接口
```

完成代码的编写后需要设置功能包的编译选项，让系统知道Python程序的入口，打开功能包的setup.py文件，加入如下入口点的配置：

```
    entry_points={
        'console_scripts': [
         'service_adder_client  = learning_service.service_adder_client:main',
         'service_adder_server  = learning_service.service_adder_server:main',
        ],
    },
```

##### **流程总结**

对以上程序进行分析，如果我们想要实现一个服务端，流程如下：

- 编程接口初始化
- 创建节点并初始化
- 创建服务器端对象
- 通过回调函数处进行服务
- 向客户端反馈应答结果
- 销毁节点并关闭接口

### **案例二：机器视觉识别**

好啦，加法求解器已经实现了，回想下刚才我们提到的视觉识别流程，当我们需要知道目标物体位置的时候，通过服务通信的机制，岂不是更加合理。

![image-20220527235027462](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.5_%E6%9C%8D%E5%8A%A1/image-20220527235027462.png)

#### **运行效果**

此时会有三个节点出现：

1. **相机驱动节点**，发布图像数据；
2. **视觉识别节点**，订阅图像数据，并且集成了一个服务器端对象，随时准备提供目标位置；
3. **客户端节点**，我们可以认为是一个机器人目标跟踪的节点，当需要根据目标运动时，就发送一次请求，然后拿到一个当前的目标位置。

启动三个终端，分别运行上述三个节点：

```
$ ros2 run usb_cam usb_cam_node_exe
$ ros2 run learning_service service_object_server
$ ros2 run learning_service service_object_client
```

![image-20220527235144680](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.5_%E6%9C%8D%E5%8A%A1/image-20220527235144680.png)

![image-20220527235132847](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.5_%E6%9C%8D%E5%8A%A1/image-20220527235132847.png)

#### **客户端代码解析**

learning_service/service_object_client.py

```
#!/usr/bin/env python3
# -*- coding: utf-8 -*-

"""
@作者: 古月居(www.guyuehome.com)
@说明: ROS2服务示例-请求目标识别，等待目标位置应答
"""

import rclpy                                            # ROS2 Python接口库
from rclpy.node   import Node                           # ROS2 节点类
from learning_interface.srv import GetObjectPosition    # 自定义的服务接口

class objectClient(Node):
    def __init__(self, name):
        super().__init__(name)                          # ROS2节点父类初始化
        self.client = self.create_client(GetObjectPosition, 'get_target_position')
        while not self.client.wait_for_service(timeout_sec=1.0):
            self.get_logger().info('service not available, waiting again...')
        self.request = GetObjectPosition.Request()

    def send_request(self):
        self.request.get = True
        self.future = self.client.call_async(self.request)

def main(args=None):
    rclpy.init(args=args)                             # ROS2 Python接口初始化
    node = objectClient("service_object_client")      # 创建ROS2节点对象并进行初始化
    node.send_request()

    while rclpy.ok():
        rclpy.spin_once(node)

        if node.future.done():
            try:
                response = node.future.result()
            except Exception as e:
                node.get_logger().info(
                    'Service call failed %r' % (e,))
            else:
                node.get_logger().info(
                    'Result of object position:\n x: %d y: %d' %
                    (response.x, response.y))
            break
    node.destroy_node()                              # 销毁节点对象
    rclpy.shutdown()                                 # 关闭ROS2 Python接口
```

完成代码的编写后需要设置功能包的编译选项，让系统知道Python程序的入口，打开功能包的setup.py文件，加入如下入口点的配置：

```
    entry_points={
        'console_scripts': [
         'service_adder_client  = learning_service.service_adder_client:main',
         'service_adder_server  = learning_service.service_adder_server:main',
         'service_object_client = learning_service.service_object_client:main',
        ],
    },
```

#### **服务端代码解析**

learning_service/service_object_server.py

```
#!/usr/bin/env python3
# -*- coding: utf-8 -*-

"""
@作者: 古月居(www.guyuehome.com)
@说明: ROS2服务示例-提供目标识别服务
"""

import rclpy                                           # ROS2 Python接口库
from rclpy.node import Node                            # ROS2 节点类
from sensor_msgs.msg import Image                      # 图像消息类型
import numpy as np                                     # Python数值计算库
from cv_bridge import CvBridge                         # ROS与OpenCV图像转换类
import cv2                                             # Opencv图像处理库
from learning_interface.srv import GetObjectPosition   # 自定义的服务接口

lower_red = np.array([0, 90, 128])     # 红色的HSV阈值下限
upper_red = np.array([180, 255, 255])  # 红色的HSV阈值上限

class ImageSubscriber(Node):
    def __init__(self, name):
        super().__init__(name)                              # ROS2节点父类初始化
        self.sub = self.create_subscription(
            Image, 'image_raw', self.listener_callback, 10) # 创建订阅者对象（消息类型、话题名、订阅者回调函数、队列长度）
        self.cv_bridge = CvBridge()                         # 创建一个图像转换对象，用于OpenCV图像与ROS的图像消息的互相转换

        self.srv = self.create_service(GetObjectPosition,   # 创建服务器对象（接口类型、服务名、服务器回调函数）
                                       'get_target_position',
                                       self.object_position_callback)    
        self.objectX = 0
        self.objectY = 0                              

    def object_detect(self, image):
        hsv_img = cv2.cvtColor(image, cv2.COLOR_BGR2HSV)      # 图像从BGR颜色模型转换为HSV模型
        mask_red = cv2.inRange(hsv_img, lower_red, upper_red) # 图像二值化
        contours, hierarchy = cv2.findContours(
            mask_red, cv2.RETR_LIST, cv2.CHAIN_APPROX_NONE)   # 图像中轮廓检测

        for cnt in contours:                                  # 去除一些轮廓面积太小的噪声
            if cnt.shape[0] < 150:
                continue

            (x, y, w, h) = cv2.boundingRect(cnt)              # 得到苹果所在轮廓的左上角xy像素坐标及轮廓范围的宽和高
            cv2.drawContours(image, [cnt], -1, (0, 255, 0), 2)# 将苹果的轮廓勾勒出来
            cv2.circle(image, (int(x+w/2), int(y+h/2)), 5,
                       (0, 255, 0), -1)                       # 将苹果的图像中心点画出来

            self.objectX = int(x+w/2)
            self.objectY = int(y+h/2)

        cv2.imshow("object", image)                            # 使用OpenCV显示处理后的图像效果
        cv2.waitKey(50)

    def listener_callback(self, data):
        self.get_logger().info('Receiving video frame')        # 输出日志信息，提示已进入回调函数
        image = self.cv_bridge.imgmsg_to_cv2(data, 'bgr8')     # 将ROS的图像消息转化成OpenCV图像
        self.object_detect(image)                              # 苹果检测

    def object_position_callback(self, request, response):     # 创建回调函数，执行收到请求后对数据的处理
        if request.get == True:
            response.x = self.objectX                          # 目标物体的XY坐标
            response.y = self.objectY
            self.get_logger().info('Object position\nx: %d y: %d' %
                                   (response.x, response.y))   # 输出日志信息，提示已经反馈
        else:
            response.x = 0
            response.y = 0
            self.get_logger().info('Invalid command')          # 输出日志信息，提示已经反馈
        return response


def main(args=None):                                 # ROS2节点主入口main函数
    rclpy.init(args=args)                            # ROS2 Python接口初始化
    node = ImageSubscriber("service_object_server")  # 创建ROS2节点对象并进行初始化
    rclpy.spin(node)                                 # 循环等待ROS2退出
    node.destroy_node()                              # 销毁节点对象
    rclpy.shutdown()                                 # 关闭ROS2 Python接口
```

完成代码的编写后需要设置功能包的编译选项，让系统知道Python程序的入口，打开功能包的setup.py文件，加入如下入口点的配置：

```
    entry_points={
        'console_scripts': [
         'service_adder_client  = learning_service.service_adder_client:main',
         'service_adder_server  = learning_service.service_adder_server:main',
         'service_object_client = learning_service.service_object_client:main',
         'service_object_server = learning_service.service_object_server:main',
        ],
    },
```

### **服务命令行操作**

服务命令的常用操作如下：

```
$ ros2 service list                  # 查看服务列表
$ ros2 service type <service_name>   # 查看服务数据类型
$ ros2 service call <service_name> <service_type> <service_data>   # 发送服务请求
```

![image-20220527235949170](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.5_%E6%9C%8D%E5%8A%A1/image-20220527235949170.png)

### **思考题**

话题和服务是ROS中最为常用的两种数据通信方法，前者适合传感器、控制指令等周期性、单向传输的数据，后者适合一问一答，同步性要求更高的数据，比如获取机器视觉识别到的目标位置。

![image-20220527235904825](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.5_%E6%9C%8D%E5%8A%A1/image-20220527235904825.png)

在机器人开发过程中，类似的通信应用比比皆是，ROS针对绝大部分通用场景，都设计了标准的话题和服务数据类型，比如图像数据、雷达数据、里程计数据等等，不过机器人软硬件繁杂，很多时候这些标准定义也无法满足我们的需求，这个时候，我们就要自定义通信接口了。

## 2.7 通信接口

在ROS系统中，无论话题还是服务，或者我们后续将要学习的动作，都会用到一个重要的概念——**通信接口**。

通信并不是一个人自言自语，而是两个甚至更多个人，你来我往的交流，交流的内容是什么呢？为了让大家都好理解，我们可以给传递的数据定义一个标准的结构，这就是通信接口。

### **接口的定义**

接口的概念在各个领域随处可见，无论是硬件结构还是软件开发，都有广泛的应用。

![image-20220528001307706](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.6_%E9%80%9A%E4%BF%A1%E6%8E%A5%E5%8F%A3/image-20220528001307706.png)

比如生活中最为常见的插头和插座，两者必须匹配才能使用，电脑和手机上的USB接口也是，什么Micro-USB、TypeC等等，都是关于接口的具体定义。

![image-20220528001318495](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.6_%E9%80%9A%E4%BF%A1%E6%8E%A5%E5%8F%A3/image-20220528001318495.png)

软件开发中，接口的使用就更多了，比如我们在编写程序时，使用的函数和函数的输入输出也称之为接口，每一次调用函数的时候，就像是把主程序和调用函数通过这个接口连接到一起，系统才能正常工作。

更为形象的是图形化编程中使用的程序模块，每一个模块都有固定的结构和形状，只有两个模块相互匹配，才能在一起工作，这就很好的讲代码形象化了。

**所以什么是接口，它是一种相互关系，只有彼此匹配，才能建立连接。**

![image-20220528001346095](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.6_%E9%80%9A%E4%BF%A1%E6%8E%A5%E5%8F%A3/image-20220528001346095.png)

回到ROS的通信系统，它的主要目的就是传输数据，那就得让大家高效的建立连接，并且准确包装和解析传输的数据内容，话题、服务等机制也就诞生了，他们传输的数据，都要**符合通信接口的标准定义**。

比如摄像头驱动发布的图像话题，由每个像素点的R、G、B三原色值组成，控制机器人运动的速度指令，由线速度和角速度组成，进行机器人配置的服务，有配置的参数和反馈的结果组成等等，类似这些常用的定义，在ROS系统中都有提供，我们也可以自己开发。

**这些接口看上去像是给我们加了一些约束，但却是ROS系统的精髓所在**。举个例子，我们使用相机驱动节点的时候，完全不用关注它是如何驱动相机的，只要一句话运行，我们就可以知道发布出来的图像数据是什么样的了，直接开始我们的应用开发；类似的，键盘控制我们也可以安装一个ROS包，如何实现的呢？不用关心，反正它发布出来的肯定是线速度和角速度。

### **ROS通信接口**

接口可以让程序之间的依赖降低，便于我们使用别人的代码，也方便别人使用我们的代码，这就是ROS的核心目标，减少重复造轮子。

![image-20220528001533911](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.6_%E9%80%9A%E4%BF%A1%E6%8E%A5%E5%8F%A3/image-20220528001533911.png)

ROS有三种常用的通信机制，分别是**话题、服务、动作**，通过每一种通信种定义的接口，各种节点才能有机的联系到一起。

#### **语言无关**

为了保证每一个节点可以使用不同语言编程，ROS将这些接口的设计做成了和**语言无关**的，比如这里看到的int32表示32位的整型数，int64表示64位的整型数，bool表示布尔值，还可以定义数组、结构体，这些定义在编译过程中，会自动生成对应到C++、Python等语言里的数据结构。

![image-20220528001633925](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.6_%E9%80%9A%E4%BF%A1%E6%8E%A5%E5%8F%A3/image-20220528001633925.png)

- 话题通信接口的定义使用的是.msg文件，由于是单向传输，只需要描述传输的每一帧数据是什么就行，比如在这个定义里，会传输两个32位的整型数，x、y，我们可以用来传输二维坐标的数值。
- 服务通信接口的定义使用的是.srv文件，包含请求和应答两部分定义，通过中间的“---”区分，比如之前我们学习的加法求和功能，请求数据是两个64位整型数a和b，应答是求和的结果sum。
- 动作是另外一种通信机制，用来描述机器人的一个运动过程，使用.action文件定义，比如我们让小海龟转90度，一边转一边周期反馈当前的状态，此时接口的定义分成了三个部分，分别是动作的目标，比如是开始运动，运动的结果，最终旋转的90度是否完成，还有一个周期反馈，比如每隔1s反馈一下当前转到第10度、20度还是30度了，让我们知道运动的进度。

#### **标准接口**

大家可能好奇ROS系统到底给我们定义了哪些接口呢？我们可以在ROS安装路径中的share文件夹中找到，涵盖众多标准定义，大家可以打开几个看看。

![image-20220528001914859](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.6_%E9%80%9A%E4%BF%A1%E6%8E%A5%E5%8F%A3/image-20220528001914859.png)

![image-20220528001943541](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.6_%E9%80%9A%E4%BF%A1%E6%8E%A5%E5%8F%A3/image-20220528001943541.png)

### **案例一：服务接口的定义与使用**

了解了通信接口的概念，接下来我们再从代码实现的角度，研究下如何定义以及使用一个接口。

在之前服务概念讲解的课程中，我们编写了这样一个例程，我们再来回顾下。

![image-20220528002304850](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.6_%E9%80%9A%E4%BF%A1%E6%8E%A5%E5%8F%A3/image-20220528002304850.png)

有三个节点，第一个驱动相机发布图像话题，第二个是机器视觉识别节点，封装了一个服务的服务端对象，提供目标识别位置的查询服务，第三个节点在需要目标位置的时候，就可以发送请求，收到位置进行使用了。

![image-20220527235132847](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.6_%E9%80%9A%E4%BF%A1%E6%8E%A5%E5%8F%A3/image-20220527235132847.png)

#### **接口定义**

在这个例程中，我们使用GetObjectPosition.srv定义了服务通信的接口：

learning_interface/srv/GetObjectPosition.srv

```
bool get      # 获取目标位置的指令
---
int32 x       # 目标的X坐标
int32 y       # 目标的Y坐标
```

定义中有两个部分，上边是获取目标位置的指令，get为true的话，就表示我们需要一次位置，服务端就会反馈这个x、y坐标了。

完成定义后，还需要在功能包的CMakeLists.txt中配置编译选项，让编译器在编译过程中，根据接口定义，自动生成不同语言的代码：

```
...

find_package(rosidl_default_generators REQUIRED)

rosidl_generate_interfaces(${PROJECT_NAME}
  "srv/GetObjectPosition.srv"
)

...
```

功能包的package.xml文件中也需要添加代码生成的功能依赖：

```
 ...

 <build_depend>rosidl_default_generators</build_depend>
 <exec_depend>rosidl_default_runtime</exec_depend>
 <member_of_group>rosidl_interface_packages</member_of_group>

 ...
```

#### 程序调用

我们在代码中再来重点看下接口的使用方法。

##### **客户端接口调用**

learning_service/service_object_client.py

```
#!/usr/bin/env python3
# -*- coding: utf-8 -*-

"""
@作者: 古月居(www.guyuehome.com)
@说明: ROS2服务示例-请求目标识别，等待目标位置应答
"""

import rclpy                                            # ROS2 Python接口库
from rclpy.node   import Node                           # ROS2 节点类
from learning_interface.srv import GetObjectPosition    # 自定义的服务接口

class objectClient(Node):
    def __init__(self, name):
        super().__init__(name)                          # ROS2节点父类初始化
        self.client = self.create_client(GetObjectPosition, 'get_target_position')
        while not self.client.wait_for_service(timeout_sec=1.0):
            self.get_logger().info('service not available, waiting again...')
        self.request = GetObjectPosition.Request()

    def send_request(self):
        self.request.get = True
        self.future = self.client.call_async(self.request)

def main(args=None):
    rclpy.init(args=args)                             # ROS2 Python接口初始化
    node = objectClient("service_object_client")      # 创建ROS2节点对象并进行初始化
    node.send_request()

    while rclpy.ok():
        rclpy.spin_once(node)

        if node.future.done():
            try:
                response = node.future.result()
            except Exception as e:
                node.get_logger().info(
                    'Service call failed %r' % (e,))
            else:
                node.get_logger().info(
                    'Result of object position:\n x: %d y: %d' %
                    (response.x, response.y))
            break
    node.destroy_node()                              # 销毁节点对象
    rclpy.shutdown()                                 # 关闭ROS2 Python接口
```

##### **服务端接口调用**

learning_service/service_object_server.py

```
#!/usr/bin/env python3
# -*- coding: utf-8 -*-

"""
@作者: 古月居(www.guyuehome.com)
@说明: ROS2服务示例-提供目标识别服务
"""

import rclpy                                           # ROS2 Python接口库
from rclpy.node import Node                            # ROS2 节点类
from sensor_msgs.msg import Image                      # 图像消息类型
import numpy as np                                     # Python数值计算库
from cv_bridge import CvBridge                         # ROS与OpenCV图像转换类
import cv2                                             # Opencv图像处理库
from learning_interface.srv import GetObjectPosition   # 自定义的服务接口

lower_red = np.array([0, 90, 128])     # 红色的HSV阈值下限
upper_red = np.array([180, 255, 255])  # 红色的HSV阈值上限

class ImageSubscriber(Node):
    def __init__(self, name):
        super().__init__(name)                              # ROS2节点父类初始化
        self.sub = self.create_subscription(
            Image, 'image_raw', self.listener_callback, 10) # 创建订阅者对象（消息类型、话题名、订阅者回调函数、队列长度）
        self.cv_bridge = CvBridge()                         # 创建一个图像转换对象，用于OpenCV图像与ROS的图像消息的互相转换

        self.srv = self.create_service(GetObjectPosition,   # 创建服务器对象（接口类型、服务名、服务器回调函数）
                                       'get_target_position',
                                       self.object_position_callback)    
        self.objectX = 0
        self.objectY = 0                              

    def object_detect(self, image):
        hsv_img = cv2.cvtColor(image, cv2.COLOR_BGR2HSV)      # 图像从BGR颜色模型转换为HSV模型
        mask_red = cv2.inRange(hsv_img, lower_red, upper_red) # 图像二值化
        contours, hierarchy = cv2.findContours(
            mask_red, cv2.RETR_LIST, cv2.CHAIN_APPROX_NONE)   # 图像中轮廓检测

        for cnt in contours:                                  # 去除一些轮廓面积太小的噪声
            if cnt.shape[0] < 150:
                continue

            (x, y, w, h) = cv2.boundingRect(cnt)              # 得到苹果所在轮廓的左上角xy像素坐标及轮廓范围的宽和高
            cv2.drawContours(image, [cnt], -1, (0, 255, 0), 2)# 将苹果的轮廓勾勒出来
            cv2.circle(image, (int(x+w/2), int(y+h/2)), 5,
                       (0, 255, 0), -1)                       # 将苹果的图像中心点画出来

            self.objectX = int(x+w/2)
            self.objectY = int(y+h/2)

        cv2.imshow("object", image)                            # 使用OpenCV显示处理后的图像效果
        cv2.waitKey(50)

    def listener_callback(self, data):
        self.get_logger().info('Receiving video frame')        # 输出日志信息，提示已进入回调函数
        image = self.cv_bridge.imgmsg_to_cv2(data, 'bgr8')     # 将ROS的图像消息转化成OpenCV图像
        self.object_detect(image)                              # 苹果检测

    def object_position_callback(self, request, response):     # 创建回调函数，执行收到请求后对数据的处理
        if request.get == True:
            response.x = self.objectX                          # 目标物体的XY坐标
            response.y = self.objectY
            self.get_logger().info('Object position\nx: %d y: %d' %
                                   (response.x, response.y))   # 输出日志信息，提示已经反馈
        else:
            response.x = 0
            response.y = 0
            self.get_logger().info('Invalid command')          # 输出日志信息，提示已经反馈
        return response


def main(args=None):                                 # ROS2节点主入口main函数
    rclpy.init(args=args)                            # ROS2 Python接口初始化
    node = ImageSubscriber("service_object_server")  # 创建ROS2节点对象并进行初始化
    rclpy.spin(node)                                 # 循环等待ROS2退出
    node.destroy_node()                              # 销毁节点对象
    rclpy.shutdown()                                 # 关闭ROS2 Python接口
```

### **案例二：话题接口的定义与使用**

话题通信接口的定义也是类似的，继续从之前的机器视觉案例中来衍生，我们想把服务换成话题，周期发布目标识别的位置，不管有没有人需要。

![image-20220528003434007](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.6_%E9%80%9A%E4%BF%A1%E6%8E%A5%E5%8F%A3/image-20220528003434007.png)

#### **运行效果**

现在我们会运行三个节点：

- 第一个节点，将驱动相机并发布图像话题，此时的话题数据使用的是ROS中标准定义的Image图像消息；
- 第二个节点，会运行视觉识别功能，识别目标的位置，这个位置我们希望封装成话题消息，发布出去，谁需要使用谁就来订阅；
- 第三个节点，订阅位置话题，打印到终端中。

启动三个终端，分别运行以上节点：

```
$ ros2 run usb_cam usb_cam_node_exe
$ ros2 run learning_topic interface_object_pub
$ ros2 run learning_topic interface_object_sub
```

![image-20220528003829553](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.6_%E9%80%9A%E4%BF%A1%E6%8E%A5%E5%8F%A3/image-20220528003829553.png)

#### **接口定义**

在这个例程中，我们使用ObjectPosition.msg定义了服务通信的接口：

learning_interface/msg/ObjectPosition.msg

```
int32 x      # 表示目标的X坐标
int32 y      # 表示目标的Y坐标
```

话题消息的内容是一个位置，我们使用x、y坐标值进行描述。

完成定义后，还需要在功能包的CMakeLists.txt中配置编译选项，让编译器在编译过程中，根据接口定义，自动生成不同语言的代码：

```
...

find_package(rosidl_default_generators REQUIRED)

rosidl_generate_interfaces(${PROJECT_NAME}
  "msg/ObjectPosition.msg"
)

...
```

#### **程序调用**

我们在代码中再来重点看下接口的使用方法。

##### **发布者接口调用**

learning_topic/interface_object_pub.py

```
#!/usr/bin/env python3
# -*- coding: utf-8 -*-

"""
@作者: 古月居(www.guyuehome.com)
@说明: ROS2接口示例-发布目标位置
"""

import rclpy                                       # ROS2 Python接口库
from rclpy.node import Node                        # ROS2 节点类
from sensor_msgs.msg import Image                  # 图像消息类型
from cv_bridge import CvBridge                     # ROS与OpenCV图像转换类
import cv2                                         # Opencv图像处理库
import numpy as np                                 # Python数值计算库
from learning_interface.msg import ObjectPosition  # 自定义的目标位置消息

lower_red = np.array([0, 90, 128])                 # 红色的HSV阈值下限
upper_red = np.array([180, 255, 255])              # 红色的HSV阈值上限

"""
创建一个订阅者节点
"""
class ImageSubscriber(Node):

    def __init__(self, name):
        super().__init__(name)                                  # ROS2节点父类初始化
        self.sub = self.create_subscription(
            Image, 'image_raw', self.listener_callback, 10)     # 创建订阅者对象（消息类型、话题名、订阅者回调函数、队列长度）
        self.pub = self.create_publisher(
            ObjectPosition, "object_position", 10)              # 创建发布者对象（消息类型、话题名、队列长度）
        self.cv_bridge = CvBridge()                             # 创建一个图像转换对象，用于OpenCV图像与ROS的图像消息的互相转换

        self.objectX = 0
        self.objectY = 0   

    def object_detect(self, image):      
        hsv_img = cv2.cvtColor(image, cv2.COLOR_BGR2HSV)        # 图像从BGR颜色模型转换为HSV模型
        mask_red = cv2.inRange(hsv_img, lower_red, upper_red)   # 图像二值化
        contours, hierarchy = cv2.findContours(
            mask_red, cv2.RETR_LIST, cv2.CHAIN_APPROX_NONE)     # 图像中轮廓检测
        for cnt in contours:                                    # 去除一些轮廓面积太小的噪声
            if cnt.shape[0] < 150:
                continue

            (x, y, w, h) = cv2.boundingRect(cnt)                # 得到苹果所在轮廓的左上角xy像素坐标及轮廓范围的宽和高

            cv2.drawContours(image, [cnt], -1, (0, 255, 0), 2)  # 将苹果的轮廓勾勒出来
            cv2.circle(image, (int(x+w/2), int(y+h/2)), 5,      # 将苹果的图像中心点画出来
                       (0, 255, 0), -1)   

            self.objectX = int(x+w/2)
            self.objectY = int(y+h/2)

        cv2.imshow("object", image)                             # 使用OpenCV显示处理后的图像效果
        cv2.waitKey(50)

    def listener_callback(self, data):
        self.get_logger().info('Receiving video frame')         # 输出日志信息，提示已进入回调函数
        image = self.cv_bridge.imgmsg_to_cv2(data, 'bgr8')      # 将ROS的图像消息转化成OpenCV图像
        position = ObjectPosition()
        self.object_detect(image)                               # 苹果检测
        position.x, position.y = int(self.objectX), int(self.objectY)
        self.pub.publish(position)                              # 发布目标位置

def main(args=None):                                        # ROS2节点主入口main函数
    rclpy.init(args=args)                                   # ROS2 Python接口初始化
    node = ImageSubscriber("topic_webcam_sub")              # 创建ROS2节点对象并进行初始化
    rclpy.spin(node)                                        # 循环等待ROS2退出
    node.destroy_node()                                     # 销毁节点对象
    rclpy.shutdown()                                        # 关闭ROS2 Python接口
```

##### **订阅者接口调用**

learning_topic/interface_object_sub.py

```
#!/usr/bin/env python3
# -*- coding: utf-8 -*-

"""
@作者: 古月居(www.guyuehome.com)
@说明: ROS2接口示例-订阅目标位置
"""

import rclpy                                       # ROS2 Python接口库
from rclpy.node   import Node                      # ROS2 节点类
from std_msgs.msg import String                    # 字符串消息类型
from learning_interface.msg import ObjectPosition  # 自定义的目标位置消息

"""
创建一个订阅者节点
"""
class SubscriberNode(Node):
    def __init__(self, name):
        super().__init__(name)                                                # ROS2节点父类初始化
        self.sub = self.create_subscription(\
            ObjectPosition, "/object_position", self.listener_callback, 10)   # 创建订阅者对象（消息类型、话题名、订阅者回调函数、队列长度

    def listener_callback(self, msg):                                         # 创建回调函数，执行收到话题消息后对数据的处理
        self.get_logger().info('Target Position: "(%d, %d)"' % (msg.x, msg.y))# 输出日志信息，提示订阅收到的话题消息


def main(args=None):                                 # ROS2节点主入口main函数
    rclpy.init(args=args)                            # ROS2 Python接口初始化
    node = SubscriberNode("interface_position_sub")  # 创建ROS2节点对象并进行初始化
    rclpy.spin(node)                                 # 循环等待ROS2退出
    node.destroy_node()                              # 销毁节点对象
    rclpy.shutdown()                                 # 关闭ROS2 Python接口
```

### 接口命令行操作

接口命令的常用操作如下：

```
$ ros2 interface list                    # 查看系统接口列表
$ ros2 interface show <interface_name>   # 查看某个接口的详细定义
$ ros2 interface package <package_name>  # 查看某个功能包中的接口定义
```

![image-20220528004610983](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.6_%E9%80%9A%E4%BF%A1%E6%8E%A5%E5%8F%A3/image-20220528004610983.png)

![image-20220528004525471](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.6_%E9%80%9A%E4%BF%A1%E6%8E%A5%E5%8F%A3/image-20220528004525471.png)

![image-20220528004538865](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.6_%E9%80%9A%E4%BF%A1%E6%8E%A5%E5%8F%A3/image-20220528004538865.png)

## 2.8 动作

机器人是一个复杂的智能系统，并不仅仅是键盘遥控运动、识别某个目标这么简单，我们需要实现的是送餐、送货、分拣等满足具体场景需求的机器人。

在这些应用功能的实现中，另外一种ROS通信机制也会被常常用到——那就是**动作**。从这个名字上就可以很好理解这个概念的含义，这种通信机制的目的就是便于**对机器人某一完整行为的流程进行管理**。

### **通信模型**

举个例子，比如我们想让机器人转个圈，这肯定不是一下就可以完成的，机器人得一点一点旋转，直到360度才能结束，假设机器人并不在我们眼前，发出指令后，我们根本不知道机器人到底有没有开始转圈，转到哪里了？

![image-20220528005012082](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.7_%E5%8A%A8%E4%BD%9C/image-20220528005012082.png)

OK，现在我们需要的是一个反馈，比如每隔1s，告诉我们当前转到多少度了，10度、20度、30度，一段时间之后，到了360度，再发送一个信息，表示动作执行完成。

这样一个需要执行一段时间的行为，使用动作的通信机制就更为合适，就像装了一个进度条，我们可以随时把控进度，如果运动过程当中，我们还可以随时发送一个取消运动的命令。

#### **客户端/服务器模型**

动作和服务类似，使用的也是客户端和服务器模型，客户端发送动作的目标，想让机器人干什么，服务器端执行动作过程， 控制机器人达到运动的目标，同时周期反馈动作执行过程中的状态。

![image8](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.7_%E5%8A%A8%E4%BD%9C/image8.gif)

客户端发送一个运动的目标，想让机器人动起来，服务器端收到之后，就开始控制机器人运动，一边运动，一边反馈当前的状态，如果是一个导航动作，这个反馈可能是当前所处的坐标，如果是机械臂抓取，这个反馈可能又是机械臂的实时姿态。当运动执行结束后，服务器再反馈一个动作结束的信息。整个通信过程就此结束。

#### **一对多通信**

和服务一样，动作通信中的客户端可以有多个，大家都可以发送运动命令，但是服务器端只能有一个，毕竟只有一个机器人，先执行完成一个动作，才能执行下一个动作。

#### **同步通信**

既然有反馈，那动作也是一种同步通信机制，之前我们也介绍过，动作过程中的数据通信接口，使用.action文件进行定义。

#### **由服务和话题合成**

大家再仔细看下上边的动图，是不是还会发现一个隐藏的秘密。

动作的三个通信模块，竟然有两个是服务，一个是话题，当客户端发送运动目标时，使用的是服务的请求调用，服务器端也会反馈一个应带，表示收到命令。动作的反馈过程，其实就是一个话题的周期发布，服务器端是发布者，客户端是订阅者。

没错，动作是一种应用层的通信机制，其底层就是基于话题和服务来实现的。

### **案例一：小海龟的动作**

我们再用小海龟的案例加深对动作概念的理解。

按照以下命令启动小海龟仿真器，接下来使用action命令控制小海龟的动作，可以让海龟运动到某一指定的姿态：

```
$ ros2 run turtlesim turtlesim_node
$ ros2 run turtlesim turtle_teleop_key
$ ros2 action info /turtle1/rotate_absolute
$ ros2 action send_goal /turtle1/rotate_absolute turtlesim/action/RotateAbsolute "{theta: -1.57}"
$ ros2 action send_goal /turtle1/rotate_absolute turtlesim/action/RotateAbsolute "{theta: -1.57}" --feedback
```

![image-20220528005909408](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.7_%E5%8A%A8%E4%BD%9C/image-20220528005909408.png)

![image-20220528005935269](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.7_%E5%8A%A8%E4%BD%9C/image-20220528005935269.png)

### **案例二：机器人画圆**

如何通过代码来实现动作的编程呢？

动作虽然是基于话题和服务实现的，但在实际使用中，并不会直接使用话题和服务的编程方法，而是有一套针对动作特性封装好的编程接口，接下来我们就一起试一试。

![image-20220528010032315](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.7_%E5%8A%A8%E4%BD%9C/image-20220528010032315.png)

假设我们有一个机器人，我们希望通过动作的通信方法，让机器人转个圈，请编程实现动作通信中，客户端和服务器端的实现过程。

#### **运行效果**

启动两个终端，分别运行一下命令，启动动作示例的服务端和客户端：

```
$ ros2 run learning_action action_move_server 
$ ros2 run learning_action action_move_client
```

![image-20220528010905277](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.7_%E5%8A%A8%E4%BD%9C/image-20220528010905277.png)

![image-20220528010845943](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.7_%E5%8A%A8%E4%BD%9C/image-20220528010845943.png)

终端中，我们可以看到客户端发送动作目标之后，服务器端开始模拟机器人运动，每30度发送一次反馈信息，最终完成运动，并反馈结束运动的信息。

接下来我们就分析下这个例程实现背后的原理。

#### **接口定义**

例程使用的动作并不是ROS中的标准定义，我们通过MoveCircle.action进行自定义：

learning_interface/action/MoveCircle.action

```
bool enable     # 定义动作的目标，表示动作开始的指令
---
bool finish     # 定义动作的结果，表示是否成功执行
---
int32 state     # 定义动作的反馈，表示当前执行到的位置
```

包含三个部分：

- 第一块是**动作的目标**，enable为true时，表示开始运动；
- 第二块是**动作的执行结果**，finish为true，表示动作执行完成；
- 第三块是**动作的周期反馈**，表示当前机器人旋转到的角度。

完成定义后，还需要在功能包的CMakeLists.txt中配置编译选项，让编译器在编译过程中，根据接口定义，自动生成不同语言的代码：

```
...

find_package(rosidl_default_generators REQUIRED)

rosidl_generate_interfaces(${PROJECT_NAME}
  "action/MoveCircle.action"
)

...
```

#### **通信模型**

通信模型就是这样，客户端发送给一个动作目标，服务器控制机器人开始运动，并周期反馈，结束后反馈结束信息。

![image-20220528010217043](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.7_%E5%8A%A8%E4%BD%9C/image-20220528010217043.png)

思路理清楚，接下来开始写代码。相比之前话题和服务的程序，动作通信的例程相对较长，我们一起来运行并分析一下。

#### **服务端代码解析**

learning_action/action_move_server.py

```
#!/usr/bin/env python3
# -*- coding: utf-8 -*-

"""
@作者: 古月居(www.guyuehome.com)
@说明: ROS2动作示例-负责执行圆周运动动作的服务端
"""

import time

import rclpy                                      # ROS2 Python接口库
from rclpy.node   import Node                     # ROS2 节点类
from rclpy.action import ActionServer             # ROS2 动作服务器类
from learning_interface.action import MoveCircle  # 自定义的圆周运动接口

class MoveCircleActionServer(Node):
    def __init__(self, name):
        super().__init__(name)                   # ROS2节点父类初始化
        self._action_server = ActionServer(      # 创建动作服务器（接口类型、动作名、回调函数）
            self,
            MoveCircle,
            'move_circle',
            self.execute_callback)

    def execute_callback(self, goal_handle):            # 执行收到动作目标之后的处理函数
        self.get_logger().info('Moving circle...')
        feedback_msg = MoveCircle.Feedback()            # 创建一个动作反馈信息的消息

        for i in range(0, 360, 30):                     # 从0到360度，执行圆周运动，并周期反馈信息
            feedback_msg.state = i                      # 创建反馈信息，表示当前执行到的角度
            self.get_logger().info('Publishing feedback: %d' % feedback_msg.state)
            goal_handle.publish_feedback(feedback_msg)  # 发布反馈信息
            time.sleep(0.5)

        goal_handle.succeed()                           # 动作执行成功
        result = MoveCircle.Result()                    # 创建结果消息
        result.finish = True                            
        return result                                   # 反馈最终动作执行的结果

def main(args=None):                                    # ROS2节点主入口main函数
    rclpy.init(args=args)                               # ROS2 Python接口初始化
    node = MoveCircleActionServer("action_move_server") # 创建ROS2节点对象并进行初始化
    rclpy.spin(node)                                    # 循环等待ROS2退出
    node.destroy_node()                                 # 销毁节点对象
    rclpy.shutdown()                                    # 关闭ROS2 Python接口
```

完成代码的编写后需要设置功能包的编译选项，让系统知道Python程序的入口，打开功能包的setup.py文件，加入如下入口点的配置：

```
    entry_points={
        'console_scripts': [
         'action_move_server    = learning_action.action_move_server:main',
        ],
    },
```

#### **客户端代码解析**

learning_action/action_move_client.py

```
#!/usr/bin/env python3
# -*- coding: utf-8 -*-

"""
@作者: 古月居(www.guyuehome.com)
@说明: ROS2动作示例-请求执行圆周运动动作的客户端
"""

import rclpy                                      # ROS2 Python接口库
from rclpy.node   import Node                     # ROS2 节点类
from rclpy.action import ActionClient             # ROS2 动作客户端类

from learning_interface.action import MoveCircle  # 自定义的圆周运动接口

class MoveCircleActionClient(Node):
    def __init__(self, name):
        super().__init__(name)                   # ROS2节点父类初始化
        self._action_client = ActionClient(      # 创建动作客户端（接口类型、动作名）
            self, MoveCircle, 'move_circle') 

    def send_goal(self, enable):                 # 创建一个发送动作目标的函数
        goal_msg = MoveCircle.Goal()             # 创建一个动作目标的消息
        goal_msg.enable = enable                 # 设置动作目标为使能，希望机器人开始运动

        self._action_client.wait_for_server()    # 等待动作的服务器端启动
        self._send_goal_future = self._action_client.send_goal_async(   # 异步方式发送动作的目标
            goal_msg,                                                   # 动作目标
            feedback_callback=self.feedback_callback)                   # 处理周期反馈消息的回调函数

        self._send_goal_future.add_done_callback(self.goal_response_callback) # 设置一个服务器收到目标之后反馈时的回调函数

    def goal_response_callback(self, future):           # 创建一个服务器收到目标之后反馈时的回调函数
        goal_handle = future.result()                   # 接收动作的结果
        if not goal_handle.accepted:                    # 如果动作被拒绝执行
            self.get_logger().info('Goal rejected :(')
            return

        self.get_logger().info('Goal accepted :)')                            # 动作被顺利执行

        self._get_result_future = goal_handle.get_result_async()              # 异步获取动作最终执行的结果反馈
        self._get_result_future.add_done_callback(self.get_result_callback)   # 设置一个收到最终结果的回调函数 

    def get_result_callback(self, future):                                    # 创建一个收到最终结果的回调函数
        result = future.result().result                                       # 读取动作执行的结果
        self.get_logger().info('Result: {%d}' % result.finish)                # 日志输出执行结果

    def feedback_callback(self, feedback_msg):                                # 创建处理周期反馈消息的回调函数
        feedback = feedback_msg.feedback                                      # 读取反馈的数据
        self.get_logger().info('Received feedback: {%d}' % feedback.state) 

def main(args=None):                                       # ROS2节点主入口main函数
    rclpy.init(args=args)                                  # ROS2 Python接口初始化
    node = MoveCircleActionClient("action_move_client")    # 创建ROS2节点对象并进行初始化
    node.send_goal(True)                                   # 发送动作目标
    rclpy.spin(node)                                       # 循环等待ROS2退出
    node.destroy_node()                                    # 销毁节点对象
    rclpy.shutdown()                                       # 关闭ROS2 Python接口
```

完成代码的编写后需要设置功能包的编译选项，让系统知道Python程序的入口，打开功能包的setup.py文件，加入如下入口点的配置：

```
    entry_points={
        'console_scripts': [
         'action_move_client    = learning_action.action_move_client:main',
         'action_move_server    = learning_action.action_move_server:main',
        ],
    },
```

### **动作命令行操作**

动作命令的常用操作如下：

```
$ ros2 action list                  # 查看服务列表
$ ros2 action info <action_name>    # 查看服务数据类型
$ ros2 action send_goal <action_name> <action_type> <action_data>   # 发送服务请求
```

![image-20220528005935269](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.7_%E5%8A%A8%E4%BD%9C/image-20220528005935269.png)

## 2.9 参数

话题、服务、动作，不知道这三种通信机制大家是否已经了解清楚，本节我们再来介绍一种ROS系统中常用的数据传输方式——**参数**。

类似C++编程中的全局变量，可以便于在多个程序中共享某些数据，**参数是ROS机器人系统中的全局字典，可以运行多个节点中共享数据。**

### **通信模型**

比如在机器视觉识别的时候，有很多参数都会影响视觉识别的效果。

![image-20220528013439656](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.8_%E5%8F%82%E6%95%B0/image-20220528013439656.png)

在NodeA相机驱动节点中，就需要考虑很多问题，相机连接到哪个usb端口，使用的图像分辨率是多少，曝光度和编码格式分别是什么，这些都可以通过参数设置，我们可以通过配置文件或者程序进行设置。

NodeB节点中也是一样，图像识别使用的阈值是多少，整个图像面积很大，那个部分是我们关注的核心区域，识别过程是否需要美颜等等，就像我们使用美颜相机一样，我们可以通过滑动条或者输入框设置很多参数，不同参数设置后，都会改变执行功能的一些效果。

这就是参数的作用。

#### **全局字典**

在ROS系统中，参数是以**全局字典**的形态存在的，什么叫字典？就像真实的字典一样，由名称和数值组成，也叫做键和值，合成**键值**。或者我们也可以理解为，就像编程中的参数一样，有一个参数名 ，然后跟一个等号，后边就是参数值了，在使用的时候，访问这个参数名即可。

#### **可动态监控**

在ROS2中，参数的特性非常丰富，比如某一个节点共享了一个参数，其他节点都可以访问，如果某一个节点对参数进行了修改，其他节点也有办法立刻知道，从而获取最新的数值。这在**参数的高级编程**中，大家都可能会用到。

### **案例一：小海龟例程中的参数**

在小海龟的例程中，仿真器也提供了不少参数，我们一起来通过这个例程，熟悉下参数的含义和命令行的使用方法。

启动两个终端，分别运行小海龟仿真器和键盘控制节点：

```
$ ros2 run turtlesim turtlesim_node
$ ros2 run turtlesim turtle_teleop_key
```

![image-20220528013639558](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.8_%E5%8F%82%E6%95%B0/image-20220528013639558.png)

#### **查看参数列表**

当前系统中有哪些参数呢？我们可以启动一个终端，并使用如下命令查询：

```
$ ros2 param list
```

![image-20220528013700730](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.8_%E5%8F%82%E6%95%B0/image-20220528013700730-16536730268421.png)

#### **参数查询与修改**

如果想要查询或者修改某个参数的值，可以在param命令后边跟get或者set子命令：

```
$ ros2 param describe turtlesim background_b   # 查看某个参数的描述信息
$ ros2 param get turtlesim background_b        # 查询某个参数的值
$ ros2 param set turtlesim background_b 10     # 修改某个参数的值
```

#### **参数文件保存与加载**

一个一个查询/修改参数太麻烦了，不如试一试参数文件，ROS中的参数文件使用yaml格式，可以在param命令后边跟dump子命令，将某个节点的参数都保存到文件中，或者通过load命令一次性加载某个参数文件中的所有内容：

```
$ ros2 param dump turtlesim >> turtlesim.yaml  # 将某个节点的参数保存到参数文件中
$ ros2 param load turtlesim turtlesim.yaml     # 一次性加载某一个文件中的所有参数
```

![image-20220528013752068](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.8_%E5%8F%82%E6%95%B0/image-20220528013752068.png)

### **案例二：参数编程**

接下来就要开始写程序了，在程序中设置参数和读取参数都比较简单，一两句函数就可以实现，我们先来体验一下这几个函数的使用方法。

#### **运行效果**

启动一个终端，先运行第一句指令，启动param_declare节点，终端中可以看到循环打印的日志信息，其中的“mbot”就是我们设置的一个参数值，参数名称是“robot_name”，通过命令行修改这个参数，看下终端中会发生什么？

```
$ ros2 run learning_parameter param_declare
$ ros2 param set param_declare robot_name turtle
```

![image-20220528014153014](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.8_%E5%8F%82%E6%95%B0/image-20220528014153014.png)

#### **代码解析**

我们来看下在代码中，如何声明、创建、修改一个参数的值。

learning_parameter/param_declare.py

```
#!/usr/bin/env python3
# -*- coding: utf-8 -*-

"""
@作者: 古月居(www.guyuehome.com)
@说明: ROS2参数示例-创建、读取、修改参数
"""

import rclpy                                     # ROS2 Python接口库
from rclpy.node   import Node                    # ROS2 节点类

class ParameterNode(Node):
    def __init__(self, name):
        super().__init__(name)                                    # ROS2节点父类初始化
        self.timer = self.create_timer(2, self.timer_callback)    # 创建一个定时器（单位为秒的周期，定时执行的回调函数）
        self.declare_parameter('robot_name', 'mbot')              # 创建一个参数，并设置参数的默认值

    def timer_callback(self):                                      # 创建定时器周期执行的回调函数
        robot_name_param = self.get_parameter('robot_name').get_parameter_value().string_value   # 从ROS2系统中读取参数的值

        self.get_logger().info('Hello %s!' % robot_name_param)     # 输出日志信息，打印读取到的参数值

        new_name_param = rclpy.parameter.Parameter('robot_name',   # 重新将参数值设置为指定值
                            rclpy.Parameter.Type.STRING, 'mbot')
        all_new_parameters = [new_name_param]
        self.set_parameters(all_new_parameters)                    # 将重新创建的参数列表发送给ROS2系统

def main(args=None):                                 # ROS2节点主入口main函数
    rclpy.init(args=args)                            # ROS2 Python接口初始化
    node = ParameterNode("param_declare")            # 创建ROS2节点对象并进行初始化
    rclpy.spin(node)                                 # 循环等待ROS2退出
    node.destroy_node()                              # 销毁节点对象
    rclpy.shutdown()                                 # 关闭ROS2 Python接口
```

完成代码的编写后需要设置功能包的编译选项，让系统知道Python程序的入口，打开功能包的setup.py文件，加入如下入口点的配置：

```
entry_points={
    'console_scripts': [
     'param_declare          = learning_parameter.param_declare:main',
    ],
},
```

### **案例三：机器视觉应用**

参数大家已经会使用了，如何在机器人中应用呢？

继续优化机器视觉的示例，物体识别对光线比较敏感，不同的环境大家使用的阈值也是不同的，每次在代码中修改阈值还挺麻烦，不如我们就把阈值提炼成参数，运行过程中就可以动态设置，不是大大提高了程序的易用性么？

说干就干，我们先来看下效果如何，再看下代码中的变化。

#### 运行效果

启动三个终端，分别运行：

1. 相机驱动节点
2. 视觉识别节点
3. 修改红色阈值

```
$ ros2 run usb_cam usb_cam_node_exe 
$ ros2 run learning_parameter param_object_detect
$ ros2 param set param_object_detect red_h_upper 180
```

在启动的视觉识别节点中，我们故意将视觉识别中红色阈值的上限设置为0，如果不修改参数，将无法实现目标识别。

![image-20220530160304929](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.8_%E5%8F%82%E6%95%B0/image-20220530160304929.png)

为了便于调整阈值，我们在节点中将红色阈值的限位修改为了ROS参数，通过命令行修改该参数的值，就可以实现视觉识别啦。

![image-20220528014323915](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.8_%E5%8F%82%E6%95%B0/image-20220528014323915.png)

![image-20220530160505538](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.8_%E5%8F%82%E6%95%B0/image-20220530160505538.png)

#### 代码解析

我们来看下在视觉识别的代码中，是如何通过参数来设置阈值的。

learning_parameter/param_object_detect.py

```
#!/usr/bin/env python3
# -*- coding: utf-8 -*-

"""
@作者: 古月居(www.guyuehome.com)
@说明: ROS2参数示例-设置目标识别的颜色阈值参数
"""

import rclpy                      # ROS2 Python接口库
from rclpy.node import Node       # ROS2 节点类
from sensor_msgs.msg import Image # 图像消息类型
from cv_bridge import CvBridge    # ROS与OpenCV图像转换类
import cv2                        # Opencv图像处理库
import numpy as np                # Python数值计算库

lower_red = np.array([0, 90, 128])     # 红色的HSV阈值下限
upper_red = np.array([180, 255, 255])  # 红色的HSV阈值上限

"""
创建一个订阅者节点
"""
class ImageSubscriber(Node):
  def __init__(self, name):
    super().__init__(name)                                  # ROS2节点父类初始化    
    self.sub = self.create_subscription(Image,              # 创建订阅者对象（消息类型、话题名、订阅者回调函数、队列长度）     
                  'image_raw', self.listener_callback, 10) 
    self.cv_bridge = CvBridge()                             # 创建一个图像转换对象，用于OpenCV图像与ROS的图像消息的互相转换

    self.declare_parameter('red_h_upper', 0)                # 创建一个参数，表示阈值上限
    self.declare_parameter('red_h_lower', 0)                # 创建一个参数，表示阈值下限

  def object_detect(self, image):
    upper_red[0] = self.get_parameter('red_h_upper').get_parameter_value().integer_value    # 读取阈值上限的参数值
    lower_red[0] = self.get_parameter('red_h_lower').get_parameter_value().integer_value    # 读取阈值下限的参数值
    self.get_logger().info('Get Red H Upper: %d, Lower: %d' % (upper_red[0], lower_red[0])) # 通过日志打印读取到的参数值

    hsv_img = cv2.cvtColor(image, cv2.COLOR_BGR2HSV)                                        # 图像从BGR颜色模型转换为HSV模型
    mask_red = cv2.inRange(hsv_img, lower_red, upper_red)                                   # 图像二值化
    contours, hierarchy = cv2.findContours(mask_red, cv2.RETR_LIST, cv2.CHAIN_APPROX_NONE)  # 图像中轮廓检测
    for cnt in contours:                                                                    # 去除一些轮廓面积太小的噪声
        if cnt.shape[0] < 150:
            continue

        (x, y, w, h) = cv2.boundingRect(cnt)                            # 得到苹果所在轮廓的左上角xy像素坐标及轮廓范围的宽和高
        cv2.drawContours(image, [cnt], -1, (0, 255, 0), 2)              # 将苹果的轮廓勾勒出来
        cv2.circle(image, (int(x+w/2), int(y+h/2)), 5, (0, 255, 0), -1) # 将苹果的图像中心点画出来

    cv2.imshow("object", image)                                         # 使用OpenCV显示处理后的图像效果
    cv2.waitKey(50)

  def listener_callback(self, data):
    self.get_logger().info('Receiving video frame')     # 输出日志信息，提示已进入回调函数
    image = self.cv_bridge.imgmsg_to_cv2(data, "bgr8")  # 将ROS的图像消息转化成OpenCV图像
    self.object_detect(image)                            # 苹果检测

def main(args=None):                                    # ROS2节点主入口main函数
    rclpy.init(args=args)                               # ROS2 Python接口初始化
    node = ImageSubscriber("param_object_detect")       # 创建ROS2节点对象并进行初始化
    rclpy.spin(node)                                    # 循环等待ROS2退出
    node.destroy_node()                                 # 销毁节点对象
    rclpy.shutdown()                                    # 关闭ROS2 Python接口
```

完成代码的编写后需要设置功能包的编译选项，让系统知道Python程序的入口，打开功能包的setup.py文件，加入如下入口点的配置：

```python
entry_points={
    'console_scripts': [
     'param_declare          = learning_parameter.param_declare:main',
     'param_object_detect    = learning_parameter.param_object_detect:main',
    ],
},
```

## 2.10 分布式通信

智能机器人的功能繁多，全都放在一个计算机里，经常会遇到计算能力不够、处理出现卡顿等情况，如果可以将这些任务拆解，分配到多个计算机中运行岂不是可以减轻压力？

这就是分布式系统，**可以实现多计算平台上的任务分配。**

### **分布式通信**

什么叫分布式？

之前我们也讲过，在ROS系统中，机器人功能是由各种节点组成的，这些节点可能位于不同的计算机中，这种结构可以将原本资源消耗较多的任务，分配到不同的平台上，减轻计算压力，这就是分布式通信框架的典型应用之一。

![image-20220528014805888](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.9_%E5%88%86%E5%B8%83%E5%BC%8F%E9%80%9A%E4%BF%A1/image-20220528014805888.jpg)

比如这款机器人系统中，有两个计算平台。

机器人体积比较小，不适合放一个笔记本电脑在上边，于是采用**树莓派**作为控制器，主要实现传感器驱动和电机控制等功能，不过视觉处理和应用功能就不适合在树莓派里运行了，我们放在另外一个性能更强的**笔记本电脑**中，此外我们还需要在电脑上监控机器人的传感器信息，并且远程控制机器人运动。

两个电脑之间的通信，看上去还有点复杂，毕竟相互传输的数据还挺多的，不过ROS系统都已经为我们设计好了，我们只需要在每一个电脑上配置好ROS环境，功能开发上完全不需要做任何变化，实现非常方便。

接下来，我们就带领大家一起来感受下ROS分布式系统的魅力。

### **分布式网络搭建**

除了我使用的笔记本电脑之外，另外一个计算平台我们选择了树莓派，模拟一个放置在机器人上的控制器。

#### **树莓派配置**

在开发之前，我们需要先配置好树莓派的环境，网上也有很多资料，大家都可以参考。

##### **装系统**

我们先要给树莓派装系统，这里我们选择的是**Ubuntu Mate**针对树莓派的镜像，下载镜像之后，烧写到树莓派的SD卡中就可以启动系统了。

Ubuntu MATE镜像下载链接：https://ubuntu-mate.org/download/

![image-20220528014953068](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.9_%E5%88%86%E5%B8%83%E5%BC%8F%E9%80%9A%E4%BF%A1/image-20220528014953068.jpg)

##### **安装ROS2**

在安装好的Ubuntu Mate系统中，安装ROS2，和电脑端安装的流程一样。

![image-20220528015120229](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.9_%E5%88%86%E5%B8%83%E5%BC%8F%E9%80%9A%E4%BF%A1/image-20220528015120229.jpg)

##### **编译代码**

将我们课程的代码也下载到树莓派中，进行编译。

![image-20220528015158916](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.9_%E5%88%86%E5%B8%83%E5%BC%8F%E9%80%9A%E4%BF%A1/image-20220528015158916.jpg)

##### **远程桌面**

如果大家有显示器，可以直接在树莓派上连接键盘鼠标显示器使用，如果使用不方便的话，也可以在树莓派上配置好远程桌面，就可以通过网络访问树莓派的桌面系统了。

![image-20220528015246648](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.9_%E5%88%86%E5%B8%83%E5%BC%8F%E9%80%9A%E4%BF%A1/image-20220528015246648.jpg)

以上步骤的整体流程和电脑端操作基本一致，大家也可以参考如下链接配置树莓派：

https://blog.csdn.net/qq_52785580/article/details/122599728

#### **分布式数据传输**

树莓派配置完成后，确保已经和你所使用的电脑连接到了同一个局域网络中。接下来我们打通两个计算平台的通信能力。具体需要做什么呢？

简而言之，什么都不需要做。我们直接用命令行测试一下话题通信的效果。

<details class="attention" open="open" style="box-sizing: inherit; display: flow-root; overflow: visible; padding: 0px 0.6rem; background-color: var(--md-admonition-bg-color); border-width: 0px 0px 0px 0.2rem; border-style: solid; border-color: rgb(255, 145, 0); border-image: initial; border-radius: 0.1rem; box-shadow: var(--md-shadow-z1); color: rgba(0, 0, 0, 0.87); font-size: 0.64rem; margin: 1.5625em 0px; break-inside: avoid; font-family: Roboto, -apple-system, BlinkMacSystemFont, Helvetica, Arial, sans-serif; font-style: normal; font-variant-ligatures: normal; font-variant-caps: normal; font-weight: 400; letter-spacing: normal; orphans: 2; text-align: start; text-indent: 0px; text-transform: none; widows: 2; word-spacing: 0px; -webkit-text-stroke-width: 0px; white-space: normal; text-decoration-thickness: initial; text-decoration-style: initial; text-decoration-color: initial;"><summary style="box-sizing: border-box; cursor: pointer; display: block; min-height: 1rem; background-color: rgba(255, 145, 0, 0.1); border-top: none; border-right: none; border-bottom: none; border-left: 0.2rem none; border-image: initial; font-weight: 700; margin: 0px -0.6rem 0px -0.8rem; padding: 0.4rem 0.6rem 0.4rem 2.2rem; position: relative; border-top-left-radius: 0.1rem; border-top-right-radius: 0.1rem; -webkit-tap-highlight-color: transparent; outline: none;">Attention</summary><p style="box-sizing: border-box; margin-bottom: 0.6rem;">如使用虚拟机，请将虚拟机网络修改为<strong style="box-sizing: inherit;">桥接模式</strong></p></details>

在树莓派端，使用如下命令启动一个发布者节点：

```
$ ros2 run demo_nodes_cpp talker  #树莓派端
```

![image-20220528015555968](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.9_%E5%88%86%E5%B8%83%E5%BC%8F%E9%80%9A%E4%BF%A1/image-20220528015555968.jpg)

接下来在电脑端，使用如下命令启动一个订阅者节点：

```
$ ros2 run demo_nodes_py listener #PC端
```

![image-20220528015604383](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.9_%E5%88%86%E5%B8%83%E5%BC%8F%E9%80%9A%E4%BF%A1/image-20220528015604383.jpg)

神奇的事情就这样发生了，只要两个计算机安装好ROS2，并且处于同一网络中，他们就可以实现之前讲过的话题、服务、动作等通信了，感觉就像在一个电脑里一样。

不过这也会带来一个问题，如果一个网络中有很多个计算机，我们并不希望他们都可以互通互联，而是可以分组通信，小组之间是无法实现通信的。

#### **分布式网络分组**

没问题，ROS2提供了一个DOMAIN的机制，就类似分组一样，处于同一个DOMAIN中的计算机才能通信，我们可以在电脑和树莓派端的.bashrc中加入这样一句配置，即可将两者分配到一个小组中：

```
$ export ROS_DOMAIN_ID=<your_domain_id>
```

![image-20220528015831296](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.9_%E5%88%86%E5%B8%83%E5%BC%8F%E9%80%9A%E4%BF%A1/image-20220528015831296.jpg)

如果分配的ID不同，则两者无法实现通信。

### **案例一：小海龟分布式控制**

分布式通信网络似乎已经建立成功了，是否真有我们想的这么神奇，我们继续测试之前学习过的一些例程。

先来试试ROS中的经典案例——小海龟。

我们可以在电脑端启动小海龟仿真器，树莓派上启动键盘控制节点，或者反过来也可以，依然可以流畅的控制小海龟运动：

```
$ ros2 run turtlesim turtlesim_node      # PC端
$ ros2 run turtlesim turtle_teleop_key   # 树莓派端
```

![image-20220528020030460](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.9_%E5%88%86%E5%B8%83%E5%BC%8F%E9%80%9A%E4%BF%A1/image-20220528020030460.jpg)

### **案例二：话题分布式通信**

我们之前编写的例程是否可以在不修改任何代码的情况下，直接使用呢？

![image-20220528020152073](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.9_%E5%88%86%E5%B8%83%E5%BC%8F%E9%80%9A%E4%BF%A1/image-20220528020152073.jpg)

先试试话题通信，树莓派作为发布者，发布Hello World字符串，电脑作为订阅者，订阅Hello World字符串：

```
$ ros2 run learning_topic topic_helloworld_pub  # 树莓派端
$ ros2 run learning_topic topic_helloworld_sub  # PC端
```

![image-20220528020226552](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.9_%E5%88%86%E5%B8%83%E5%BC%8F%E9%80%9A%E4%BF%A1/image-20220528020226552.jpg)

![image-20220528020236580](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.9_%E5%88%86%E5%B8%83%E5%BC%8F%E9%80%9A%E4%BF%A1/image-20220528020236580.jpg)

### **案例三：服务分布式通信**

话题没有问题，服务也不在话下。

![image-20220528020302983](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.9_%E5%88%86%E5%B8%83%E5%BC%8F%E9%80%9A%E4%BF%A1/image-20220528020302983.jpg)

我们电脑端运行服务器程序，树莓派端运行客户端程序，还是可以顺利实现加法求和功能：

```
$ ros2 run learning_service service_adder_server        # PC端
$ ros2 run learning_service service_adder_client 2 3    # 树莓派端
```

![image-20220528020326594](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.9_%E5%88%86%E5%B8%83%E5%BC%8F%E9%80%9A%E4%BF%A1/image-20220528020326594.jpg)

![image-20220528020332776](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.9_%E5%88%86%E5%B8%83%E5%BC%8F%E9%80%9A%E4%BF%A1/image-20220528020332776.jpg)

### **案例四：机器视觉分布式应用**

以上这些功能还不够复杂？没问题，视觉识别的例程安排上。

![image-20220528020414866](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.9_%E5%88%86%E5%B8%83%E5%BC%8F%E9%80%9A%E4%BF%A1/image-20220528020414866.jpg)

接下来，我们将使用树莓派连接摄像头，模拟一个小型机器人，可以采集实时图像，然后再通过分布式网络，将图像发给电脑端的处理节点，识别图像中的红色物体：

```
$ ros2 run usb_cam usb_cam_node_exe           # 树莓派端
$ ros2 run learning_topic topic_webcam_sub    # PC端
```

没有任何问题，视觉识别的效果如下。

![image-20220528020538737](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.9_%E5%88%86%E5%B8%83%E5%BC%8F%E9%80%9A%E4%BF%A1/image-20220528020538737.jpg)

好啦，我们在分布式网络中测试了ROS一系列例程，都没有任何问题，在实际的机器人开发中，类似的方法会频繁用到，ROS为分布式网络的搭建提供了非常友好的支持，我们几乎不需要任何配置，代码也不需要做任何修改，**只要使用ROS系统，一切都会变得如此轻松**。

## 2.11 DDS

Hello，大家好，欢迎来到《ROS2入门21讲》，我是主讲人古月。

终于讲到ROS2中最为重大的变化——**DDS**，我们在前边课程中学习的话题、服务、动作，他们底层通信的具体实现过程，都是靠DDS来完成的，它相当于是**ROS机器人系统中的神经网络**。

### **通信模型**

DDS的核心是通信，能够实现通信的模型和软件框架非常多，这里我们列出常用的四种模型。

![image-20220528020740057](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.10_DDS/image-20220528020740057.jpg)

- 第一种，**点对点模型**，许多客户端连接到一个服务端，每次通信时，通信双方必须建立一条连接。当通信节点增多时，连接数也会增多。而且每个客户端都需要知道服务器的具体地址和所提供的服务，一旦服务器地址发生变化，所有客户端都会受到影响。
- 第二种，**Broker模型**，针对点对点模型进行了优化，由Broker集中处理所有人的请求，并进一步找到真正能响应该服务的角色。这样客户端就不用关心服务器的具体地址了。不过问题也很明显，Broker作为核心，它的处理速度会影响所有节点的效率，当系统规模增长到一定程度，Broker就会成为整个系统的性能瓶颈。更麻烦是，如果Broker发生异常，可能导致整个系统都无法正常运转。之前的ROS1系统，使用的就是类似这样的架构。
- 第三种，**广播模型**，所有节点都可以在通道上广播消息，并且节点都可以收到消息。这个模型解决了服务器地址的问题，而且通信双方也不用单独建立连接，但是广播通道上的消息太多了，所有节点都必须关心每条消息，其实很多是和自己没有关系的。
- 第四种，就是**以数据为中心的DDS模型**了，这种模型与广播模型有些类似，所有节点都可以在DataBus上发布和订阅消息。但它的先进之处在于，通信中包含了很多并行的通路，每个节点可以只关心自己感兴趣的消息，忽略不感兴趣的消息，有点像是一个旋转火锅，各种好吃的都在这个DataBus传送，我们只需要拿自己想吃的就行，其他的和我们没有关系。

可见，在这几种通信模型中，DDS的优势更加明显。

### **DDS**

DDS并不是一个新的通信方式，在ROS2之前，DDS已经广泛应用在很多领域，比如航空，国防，交通，医疗，能源等。

![image-20220528020829304](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.10_DDS/image-20220528020829304.jpg)

比如在自动驾驶领域，通常会存在感知，预测，决策和定位等模块，这些模块都需要非常高速和频繁地交换数据。借助DDS，可以很好地满足它们的通信需求。

#### **什么是DDS**

好啦，说了半天DDS，到底啥意思呢？我们来做一个完整的介绍

![image-20220528020842533](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.10_DDS/image-20220528020842533.jpg)

DDS的全称是**Data Distribution Service**，也就是**数据分发服务**，2004年由**对象管理组织OMG**发布和维护，是一套专门为**实时系统**设计的**数据分发/订阅标准**，最早应用于美国海军， 解决舰船复杂网络环境中大量软件升级的兼容性问题，现在已经成为强制标准。

DDS强调**以数据为中心**，可以提供丰富的**服务质量策略**，以保障数据进行实时、高效、灵活地分发，可满足各种分布式实时通信应用需求。

这里也提一下对象管理组织OMG，成立于1989年，它的使命是开发技术标准，为数以千计的垂直行业提供真实的价值，比如大家课可能听说过的统一建模语言SYSML和UML，还有中间件标准CORBA等，当然还有DDS。

#### **DDS在ROS2中的应用**

DDS在ROS2系统中的位置至关重要，所有上层建设都建立在DDS之上。在这个ROS2的架构图中，蓝色和红色部分就是DDS。

![image-20220528020937717](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.10_DDS/image-20220528020937717.jpg)

刚才我们也提到，DDS是一种通信的标准，就像4G、5G一样，既然是标准，那大家都可以按照这个标准来实现对应的功能，所以华为、高通都有很多5G的技术专利，DDS也是一样，**能够按照DDS标准实现的通信系统很多**，这里每一个红色模块，就是某一企业或组织实现的一种DDS系统。

既然可选用的DDS这么多，那我们该用哪一个呢？具体而言，他们肯定都符合基本标准，但还是会有性能上的差别，ROS2的原则就是尽量兼容，让用户根据使用场景选择，比如个人开发，我们选择一个开源版本的DDS就行，如果是工业应用，那可能得选择一个商业授权的版本了。

为了实现对多个DDS的兼容，ROS设计了一个**Middleware中间件**，也就是一个统一的标准，不管我们用那个DDS，保证上层编程使用的函数接口都是一样的。此时兼容性的问题就转移给了DDS厂商，如果他们想让自己的DDS系统进入ROS生态，就得按照ROS的接口标准，开发一个驱动，也就是这个部分。

无论如何，ROS的宗旨不变，要提高软件代码的复用性，下边DDS任你边，上边的软件没影响。

![image-20220528020948738](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.10_DDS/image-20220528020948738.jpg)

在ROS的四大组成部分中，由于DDS的加入，大大提高了分布式通信系统的综合能力，这样我们在开发机器人的过程中，就不需要纠结通信的问题，可以把更多时间放在其他部分的应用开发上。

#### **质量服务策略QoS**

DDS为ROS的通信系统提供提供了哪些特性呢？我们通过这个通信模型图来看下。

![image-20220528021108329](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.10_DDS/image-20220528021108329.jpg)

DDS中的基本结构是**Domain**，Domain将各个应用程序绑定在一起进行通信，回忆下之前我们配置树莓派和电脑通信的时候，配置的那个DOMAIN ID，就是对全局数据空间的分组定义，只有处于同一个DOMAIN小组中的节点才能互相通信。这样可以避免无用数据占用的资源。

DDS中另外一个重要特性就是**质量服务策略，QoS**。

QoS是一种网络传输策略，应用程序指定所需要的网络传输质量行为，QoS服务实现这种行为要求，尽可能地满足客户对通信质量的需求，可以理解为**数据提供者和接收者之间的合约**。

![image-20220528021119863](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.10_DDS/image-20220528021119863.jpg)

具体会有哪些策略？比如：

- **DEADLINE**策略，表示通信数据必须要在每次截止时间内完成一次通信；
- **HISTORY**策略，表示针对历史数据的一个缓存大小；
- **RELIABILITY**策略，表示数据通信的模式，配置成BEST_EFFORT，就是尽力传输模式，网络情况不好的时候，也要保证数据流畅，此时可能会导致数据丢失，配置成RELIABLE，就是可信赖模式，可以在通信中尽量保证图像的完整性，我们可以根据应用功能场景选择合适的通信模式；
- **DURABILITY**策略，可以配置针对晚加入的节点，也保证有一定的历史数据发送过去，可以让新节点快速适应系统。

![image-20220528021133020](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.10_DDS/image-20220528021133020.jpg)

所有这些策略在ROS系统中都可以通过类似这样的结构体配置，如果不配置的话，系统也会使用默认的参数。

举一个机器人的例子便于大家理解。

![image-20220528021146141](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.10_DDS/image-20220528021146141.jpg)

比如我们遥控一个无人机航拍，如果网络情况不好的话，遥控器向无人机发送运动指令的过程，可以用reliable通信模式，保证每一个命令都可以顺利发送给无人机，但是可能会有一些延时，无人机传输图像的过程可以用best effort模式，保证视频的流畅性，但是可能会有掉帧。

![image-20220528021158778](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.10_DDS/image-20220528021158778.jpg)

如果此时出现一个黑客黑入我们的网络，也没有关系，我们可以给ROS2的通信数据进行加密，黑客也没有办法直接控制无人机。

DDS的加入，让ROS2的通信系统焕然一新，多众多样的通信配置，可以更好的满足不同场景下的机器人应用。

好啦，DDS这么好，那该如何配置和使用呢？我们先带大家入个门。

### **案例一：在命令行中配置DDS**

我们先来试一试在命令行中配置DDS的参数。

启动第一个终端，我们使用best_effort创建一个发布者节点，循环发布任意数据，在另外一个终端中，如果我们使用reliable模型订阅同一话题，无法实现数据通信，如果修改为同样的best_effort，才能实现数据传输。

```
$ ros2 topic pub /chatter std_msgs/msg/Int32 "data: 42" --qos-reliability best_effort 
$ ros2 topic echo /chatter --qos-reliability reliable
$ ros2 topic echo /chatter --qos-reliability best_effort
```

![image-20220528021233993](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.10_DDS/image-20220528021233993.jpg)

![image-20220528021243492](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.10_DDS/image-20220528021243492.jpg)

如何去查看ROS2系统中每一个发布者或者订阅者的QoS策略呢，在topic命令后边跟一个"--verbose"参数就行了。

```
$ ros2 topic info /chatter --verbose
```

![image-20220528021257958](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.10_DDS/image-20220528021257958.jpg)

### **案例二：DDS编程示例**

接下来，我们尝试在代码中配置DDS，以之前Hello World话题通信为例。

![image-20220528021328306](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.10_DDS/image-20220528021328306.jpg)

#### **运行效果**

启动两个终端，分别运行发布者和订阅者节点：

```
$ ros2 run learning_qos qos_helloworld_pub
$ ros2 run learning_qos qos_helloworld_sub
```

可以看到两个终端中的通信效果如下，和之前貌似并没有太大区别。

![image-20220528021427415](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.10_DDS/image-20220528021427415.jpg)

![image-20220528021440872](https://book.guyuehome.com/ROS2/2.%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5/image/2.10_DDS/image-20220528021440872.jpg)

看效果确实差不多，不过底层通信机理上可是有所不同的。

#### **发布者代码解析**

我们看下在代码中，如果加入QoS的配置。

learning_qos/qos_helloworld_pub.py

```python
#!/usr/bin/env python3
# -*- coding: utf-8 -*-

"""
@作者: 古月居(www.guyuehome.com)
@说明: ROS2 QoS示例-发布“Hello World”话题
"""

import rclpy                     # ROS2 Python接口库
from rclpy.node import Node      # ROS2 节点类
from std_msgs.msg import String  # 字符串消息类型
from rclpy.qos import QoSProfile, QoSReliabilityPolicy, QoSHistoryPolicy # ROS2 QoS类

"""
创建一个发布者节点
"""
class PublisherNode(Node):

    def __init__(self, name):
        super().__init__(name)        # ROS2节点父类初始化

        qos_profile = QoSProfile(     # 创建一个QoS原则
            # reliability=QoSReliabilityPolicy.BEST_EFFORT,
            reliability=QoSReliabilityPolicy.RELIABLE,
            history=QoSHistoryPolicy.KEEP_LAST,
            depth=1
        )
        self.pub = self.create_publisher(String, "chatter", qos_profile) # 创建发布者对象（消息类型、话题名、QoS原则）
        self.timer = self.create_timer(0.5, self.timer_callback)         # 创建一个定时器（单位为秒的周期，定时执行的回调函数）

    def timer_callback(self):                                # 创建定时器周期执行的回调函数
        msg = String()                                       # 创建一个String类型的消息对象
        msg.data = 'Hello World'                             # 填充消息对象中的消息数据
        self.pub.publish(msg)                                # 发布话题消息
        self.get_logger().info('Publishing: "%s"' % msg.data)# 输出日志信息，提示已经完成话题发布

def main(args=None):                           # ROS2节点主入口main函数
    rclpy.init(args=args)                      # ROS2 Python接口初始化
    node = PublisherNode("qos_helloworld_pub") # 创建ROS2节点对象并进行初始化
    rclpy.spin(node)                           # 循环等待ROS2退出
    node.destroy_node()                        # 销毁节点对象
    rclpy.shutdown()                           # 关闭ROS2 Python接口
```

完成代码的编写后需要设置功能包的编译选项，让系统知道Python程序的入口，打开功能包的setup.py文件，加入如下入口点的配置：

```python
entry_points={
    'console_scripts': [
     'qos_helloworld_pub  = learning_qos.qos_helloworld_pub:main',
},
```

#### **订阅者代码解析**

订阅者中的QoS配置和发布者类似。

learning_qos/qos_helloworld_sub.py

```python
#!/usr/bin/env python3
# -*- coding: utf-8 -*-

"""
@作者: 古月居(www.guyuehome.com)
@说明: ROS2 QoS示例-订阅“Hello World”话题消息
"""

import rclpy                                     # ROS2 Python接口库
from rclpy.node   import Node                    # ROS2 节点类
from std_msgs.msg import String                  # ROS2标准定义的String消息
from rclpy.qos import QoSProfile, QoSReliabilityPolicy, QoSHistoryPolicy  # ROS2 QoS类

"""
创建一个订阅者节点
"""
class SubscriberNode(Node):

    def __init__(self, name):
        super().__init__(name)         # ROS2节点父类初始化

        qos_profile = QoSProfile(      # 创建一个QoS原则
            # reliability=QoSReliabilityPolicy.BEST_EFFORT,
            reliability=QoSReliabilityPolicy.RELIABLE,
            history=QoSHistoryPolicy.KEEP_LAST,
            depth=1
        )

        self.sub = self.create_subscription(\
            String, "chatter", self.listener_callback, qos_profile) # 创建订阅者对象（消息类型、话题名、订阅者回调函数、QoS原则）

    def listener_callback(self, msg):                      # 创建回调函数，执行收到话题消息后对数据的处理
        self.get_logger().info('I heard: "%s"' % msg.data) # 输出日志信息，提示订阅收到的话题消息

def main(args=None):                               # ROS2节点主入口main函数
    rclpy.init(args=args)                          # ROS2 Python接口初始化
    node = SubscriberNode("qos_helloworld_sub")    # 创建ROS2节点对象并进行初始化
    rclpy.spin(node)                               # 循环等待ROS2退出
    node.destroy_node()                            # 销毁节点对象
    rclpy.shutdown()                               # 关闭ROS2 Python接口
```

完成代码的编写后需要设置功能包的编译选项，让系统知道Python程序的入口，打开功能包的setup.py文件，加入如下入口点的配置：

```python
entry_points={
    'console_scripts': [
     'qos_helloworld_pub  = learning_qos.qos_helloworld_pub:main',
     'qos_helloworld_sub  = learning_qos.qos_helloworld_sub:main',
    ],
},
```

DDS本身是一个非常复杂的系统，ROS2使用的也只是冰山一角，我们主要带领大家认识DDS，更多使用方法和相关内容，大家也可以参考下边的链接进行学习。

## 3. 常用工具

## 3.1 Launch(**多节点启动与配置脚本**)

到目前为止，每当我们运行一个ROS节点，都需要打开一个新的终端运行一个命令。机器人系统中节点很多，每次都这样启动好麻烦呀。有没有一种方式可以一次性启动所有节点呢？答案当然是肯定的，那就是**Launch启动文件**，它是ROS系统中多节点启动与配置的一种脚本。

### **Launch文件**

![image-20220528140958189](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.1_Launch/image-20220528140958189.png)

这是一个完整的Launch文件，乍看上去，好像Python代码呀，没错，**ROS2中的Launch文件就是基于Python描述的**。

Launch的核心目的是**启动节点**，我们在命令行中输入的各种参数，在Launch文件中，通过类似这样的很多代码模版，也可以进行配置，甚至还可以使用Python原有的编程功能，大大丰富了启动过程中的多样化配置。

Launch文件在ROS系统中出现的频次相当之高，它就像粘合剂一样，可以自由组装和配置各个节点，那如何编写或者阅读一个Launch文件呢，我们通过一系列例程带领大家来了解。

### **多节点启动**

先来看看如何启动多个节点。

#### **运行效果**

启动终端，使用ros2中的launch命令来启动第一个launch文件示例：

```
$ ros2 launch learning_launch simple.launch.py
```

运行成功后，就可以在终端中看到发布者和订阅者两个节点的日志信息啦。

![image-20220530163837942](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.1_Launch/image-20220530163837942.png)

#### **文件解析**

这两个节点是如何启动的呢？我们来分析下这个launch文件。

learning_launch/simple.launch.py

```
from launch import LaunchDescription           # launch文件的描述类
from launch_ros.actions import Node            # 节点启动的描述类

def generate_launch_description():             # 自动生成launch文件的函数
    return LaunchDescription([                 # 返回launch文件的描述信息
        Node(                                  # 配置一个节点的启动
            package='learning_topic',          # 节点所在的功能包
            executable='topic_helloworld_pub', # 节点的可执行文件
        ),
        Node(                                  # 配置一个节点的启动
            package='learning_topic',          # 节点所在的功能包
            executable='topic_helloworld_sub', # 节点的可执行文件名
        ),
    ])
```

### **命令行参数配置**

我们使用ros2命令在终端中启动节点时，还可以在命令后配置一些传入程序的参数，使用launch文件一样可以做到。

#### **运行效果**

比如我们想要运行一个Rviz可视化上位机，并且加载某一个配置文件，使用命令行的话，是这样的：

```
$ ros2 run rviz2 rviz2 -d <PACKAGE-PATH>/rviz/turtle_rviz.rviz
```

命令后边还得跟一长串配置文件的路径，如果放在launch文件里，启动就优雅很多了：

```
$ ros2 launch learning_launch rviz.launch.py
```

![image-20220530164738675](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.1_Launch/image-20220530164738675.png)

#### **文件解析**

命令行后边的参数是如何通过launch传入节点的呢？来看下这个launch文件。

learning_launch/rviz.launch.py

```
import os

from ament_index_python.packages import get_package_share_directory # 查询功能包路径的方法

from launch import LaunchDescription    # launch文件的描述类
from launch_ros.actions import Node     # 节点启动的描述类


def generate_launch_description():      # 自动生成launch文件的函数
   rviz_config = os.path.join(          # 找到配置文件的完整路径
      get_package_share_directory('learning_launch'),
      'rviz',
      'turtle_rviz.rviz'
      )

   return LaunchDescription([           # 返回launch文件的描述信息
      Node(                             # 配置一个节点的启动
         package='rviz2',               # 节点所在的功能包
         executable='rviz2',            # 节点的可执行文件名
         name='rviz2',                  # 对节点重新命名
         arguments=['-d', rviz_config]  # 加载命令行参数
      )
   ])
```

### **资源重映射**

ROS社区中的资源非常多，当我们使用别人代码的时候，经常会发现通信的话题名称不太符合我们的要求，能否对类似的资源重新命名呢？

为了提高软件的复用性，ROS提供了资源重映射的机制，可以帮助我们解决类似的问题。

#### **运行效果**

启动一个终端，运行如下例程，很快会看到出现了两个小海龟仿真器界面；再打开一个终端，发布如下话题，让海龟1动起来，海龟2也会一起运动：

```
$ ros2 launch learning_launch rviz.launch.py
$ ros2 topic pub --rate 1 /turtle1/cmd_vel geometry_msgs/msg/Twist "{linear: {x: 2.0, y: 0.0, z: 0.0}, angular: {x: 0.0, y: 0.0, z: 1.8}}"
```

![image-20220530165536359](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.1_Launch/image-20220530165536359.png)

#### **文件解析**

为什么两个海龟都会动呢？这里要用到turtlesim功能包里另外一个节点，叫做mimic，它的功能是订阅某一个海龟的Pose位置，通过计算，变换成一个同样运动的速度指令，发布出去。

至于mimic节点订阅或者发布的话题名叫什么呢？我们就可以通过重映射修改成对应任意海龟的名字。

learning_launch/remapping.launch.py

```
from launch import LaunchDescription      # launch文件的描述类
from launch_ros.actions import Node       # 节点启动的描述类

def generate_launch_description():        # 自动生成launch文件的函数
    return LaunchDescription([            # 返回launch文件的描述信息
        Node(                             # 配置一个节点的启动
            package='turtlesim',          # 节点所在的功能包
            namespace='turtlesim1',       # 节点所在的命名空间
            executable='turtlesim_node',  # 节点的可执行文件名
            name='sim'                    # 对节点重新命名
        ),
        Node(                             # 配置一个节点的启动
            package='turtlesim',          # 节点所在的功能包
            namespace='turtlesim2',       # 节点所在的命名空间
            executable='turtlesim_node',  # 节点的可执行文件名
            name='sim'                    # 对节点重新命名
        ),
        Node(                             # 配置一个节点的启动
            package='turtlesim',          # 节点所在的功能包
            executable='mimic',           # 节点的可执行文件名
            name='mimic',                 # 对节点重新命名
            remappings=[                  # 资源重映射列表
                ('/input/pose', '/turtlesim1/turtle1/pose'),         # 将/input/pose话题名修改为/turtlesim1/turtle1/pose
                ('/output/cmd_vel', '/turtlesim2/turtle1/cmd_vel'),  # 将/output/cmd_vel话题名修改为/turtlesim2/turtle1/cmd_vel
            ]
        )
    ])
```

### **ROS参数设置**

ROS系统中的参数，也可以在Launch文件中设置。

#### **运行效果**

启动一个终端，运行如下命令：

```
$ ros2 launch learning_launch parameters.launch.py
```

在启动的海龟仿真器中，我们看到背景颜色被改变了，这个颜色参数的设置就是在launch文件中完成的。

![image-20220530170726913](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.1_Launch/image-20220530170726913.png)

#### **文件解析**

我们看下在launch文件中如何来设置参数的。

learning_launch/parameters.launch.py

```
from launch import LaunchDescription                   # launch文件的描述类
from launch.actions import DeclareLaunchArgument       # 声明launch文件内使用的Argument类
from launch.substitutions import LaunchConfiguration, TextSubstitution

from launch_ros.actions import Node                    # 节点启动的描述类


def generate_launch_description():                     # 自动生成launch文件的函数
   background_r_launch_arg = DeclareLaunchArgument(
      'background_r', default_value=TextSubstitution(text='0')     # 创建一个Launch文件内参数（arg）background_r
   )
   background_g_launch_arg = DeclareLaunchArgument(
      'background_g', default_value=TextSubstitution(text='84')    # 创建一个Launch文件内参数（arg）background_g
   )
   background_b_launch_arg = DeclareLaunchArgument(
      'background_b', default_value=TextSubstitution(text='122')   # 创建一个Launch文件内参数（arg）background_b
   )

   return LaunchDescription([                                      # 返回launch文件的描述信息
      background_r_launch_arg,                                     # 调用以上创建的参数（arg）
      background_g_launch_arg,
      background_b_launch_arg,
      Node(                                                        # 配置一个节点的启动
         package='turtlesim',
         executable='turtlesim_node',                              # 节点所在的功能包
         name='sim',                                               # 对节点重新命名
         parameters=[{                                             # ROS参数列表
            'background_r': LaunchConfiguration('background_r'),   # 创建参数background_r
            'background_g': LaunchConfiguration('background_g'),   # 创建参数background_g
            'background_b': LaunchConfiguration('background_b'),   # 创建参数background_b
         }]
      ),
   ])
```

<details class="attention" open="open" style="box-sizing: inherit; display: flow-root; overflow: visible; padding: 0px 0.6rem; background-color: var(--md-admonition-bg-color); border-width: 0px 0px 0px 0.2rem; border-style: solid; border-color: rgb(255, 145, 0); border-image: initial; border-radius: 0.1rem; box-shadow: var(--md-shadow-z1); color: rgba(0, 0, 0, 0.87); font-size: 0.64rem; margin: 1.5625em 0px; break-inside: avoid; font-family: Roboto, -apple-system, BlinkMacSystemFont, Helvetica, Arial, sans-serif; font-style: normal; font-variant-ligatures: normal; font-variant-caps: normal; font-weight: 400; letter-spacing: normal; orphans: 2; text-align: start; text-indent: 0px; text-transform: none; widows: 2; word-spacing: 0px; -webkit-text-stroke-width: 0px; white-space: normal; text-decoration-thickness: initial; text-decoration-style: initial; text-decoration-color: initial;"><summary style="box-sizing: border-box; cursor: pointer; display: block; min-height: 1rem; background-color: rgba(255, 145, 0, 0.1); border-top: none; border-right: none; border-bottom: none; border-left: 0.2rem none; border-image: initial; font-weight: 700; margin: 0px -0.6rem 0px -0.8rem; padding: 0.4rem 0.6rem 0.4rem 2.2rem; position: relative; border-top-left-radius: 0.1rem; border-top-right-radius: 0.1rem; -webkit-tap-highlight-color: transparent; outline: none;">Attention</summary><p style="box-sizing: border-box; margin-bottom: 0.6rem;">launch文件中出现的argument和parameter，虽都译为“参数”，但含义不同： - argument：仅限launch文件内部使用，方便在launch中调用某些数值； - parameter：ROS系统的参数，方便在节点见使用某些数值。</p></details>

#### 加载参数文件

以上例程我们在launch文件中一个一个的设置参数，略显麻烦，当参数比较多的时候，建议使用参数文件进行加载。

learning_launch/parameters_yaml.launch.py

```
import os

from ament_index_python.packages import get_package_share_directory  # 查询功能包路径的方法

from launch import LaunchDescription   # launch文件的描述类
from launch_ros.actions import Node    # 节点启动的描述类


def generate_launch_description():     # 自动生成launch文件的函数
   config = os.path.join(              # 找到参数文件的完整路径
      get_package_share_directory('learning_launch'),
      'config',
      'turtlesim.yaml'
      )

   return LaunchDescription([          # 返回launch文件的描述信息
      Node(                            # 配置一个节点的启动
         package='turtlesim',          # 节点所在的功能包
         executable='turtlesim_node',  # 节点的可执行文件名
         namespace='turtlesim2',       # 节点所在的命名空间
         name='sim',                   # 对节点重新命名
         parameters=[config]           # 加载参数文件
      )
   ])
```

### **Launch文件包含**

在复杂的机器人系统中，launch文件也会有很多，此时我们可以使用类似编程中的include机制，让launch文件互相包含。

#### **文件解析**

learning_launch/namespaces.launch.py

```
import os

from ament_index_python.packages import get_package_share_directory  # 查询功能包路径的方法

from launch import LaunchDescription                 # launch文件的描述类
from launch.actions import IncludeLaunchDescription  # 节点启动的描述类
from launch.launch_description_sources import PythonLaunchDescriptionSource
from launch.actions import GroupAction               # launch文件中的执行动作
from launch_ros.actions import PushRosNamespace      # ROS命名空间配置

def generate_launch_description():                   # 自动生成launch文件的函数
   parameter_yaml = IncludeLaunchDescription(        # 包含指定路径下的另外一个launch文件
      PythonLaunchDescriptionSource([os.path.join(
         get_package_share_directory('learning_launch'), 'launch'),
         '/parameters_nonamespace.launch.py'])
      )

   parameter_yaml_with_namespace = GroupAction(      # 对指定launch文件中启动的功能加上命名空间
      actions=[
         PushRosNamespace('turtlesim2'),
         parameter_yaml]
      )

   return LaunchDescription([                        # 返回launch文件的描述信息
      parameter_yaml_with_namespace
   ])
```

#### **功能包编译配置**

```
    ...

    data_files=[
        ('share/ament_index/resource_index/packages',
            ['resource/' + package_name]),
        ('share/' + package_name, ['package.xml']),
        (os.path.join('share', package_name, 'launch'), glob(os.path.join('launch', '*.launch.py'))),
        (os.path.join('share', package_name, 'config'), glob(os.path.join('config', '*.*'))),
        (os.path.join('share', package_name, 'rviz'), glob(os.path.join('rviz', '*.*'))),
    ],

    ...
```

## 3.2 TF:机器人坐标系管理神器

坐标系是我们非常熟悉的一个概念，也是机器人学中的重要基础，在一个完整的机器人系统中，会存在很多坐标系，这些坐标系之间的位置关系该如何管理？

ROS给我们提供了一个坐标系的管理神器——**TF**。

### **机器人中的坐标系**

机器人中都有哪些坐标系呢？

![image-20220528142046330](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.2_TF/image-20220528142046330.png)

比如在机械臂形态的机器人中，机器人安装的位置叫做**基坐标系**Base Frame，机器人安装位置在外部环境下的参考系叫做**世界坐标系**World Frame，机器人末端夹爪的位置叫做**工具坐标系**，外部被操作物体的位置叫做**工件坐标系**，在机械臂抓取外部物体的过程中，这些坐标系之间的关系也在跟随变化。

![image-20220528142052573](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.2_TF/image-20220528142052573.png)

在移动机器人系统中，坐标系一样至关重要，比如一个移动机器人的中心点是**基坐标系**Base Link，雷达所在的位置叫做**雷达坐标系**laser link，机器人要移动，里程计会累积位置，这个位置的参考系叫做**里程计坐标系**odom，里程计又会有累积误差和漂移，绝对位置的参考系叫做**地图坐标系**map。

一层一层坐标系之间关系复杂，有一些是相对固定的，也有一些是不断变化的，看似简单的坐标系也在空间范围内变得复杂，良好的坐标系管理系统就显得格外重要。

![image-20220528142112163](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.2_TF/image-20220528142112163.png)

关于坐标系变换关系的基本理论，在每一本机器人学的教材中都会有讲解，可以分解为**平移和旋转**两个部分，通过一个四乘四的矩阵进行描述，在空间中画出坐标系，那两者之间的变换关系，其实就是向量的数学描述。

ROS中TF功能的底层原理，就是对这些数学变换进行了封装，详细的理论知识大家可以参考机器人学的教材，我们主要讲解TF坐标管理系统的使用方法。

### **TF命令行操作**

ROS中的TF该如何使用呢？我们先通过两只小海龟的示例，了解下基于坐标系的一种机器人跟随算法。

#### **小海龟跟随例程**

这个示例需要我们先安装相应的功能包，然后就可以通过一个launch文件启动，之后我们可以控制其中的一只小海龟，另外一只小海龟会自动跟随运动。

```
$ sudo apt install ros-humble-turtle-tf2-py ros-humble-tf2-tools
$ sudo pip3 install transforms3d
```

具体运行的效果如何？我们来试一试。

```
$ ros2 launch turtle_tf2_py turtle_tf2_demo.launch.py
$ ros2 run turtlesim turtle_teleop_key
```

当我们控制一只海龟运动时，另外一只海龟也会跟随运动。

![image-20220528142340425](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.2_TF/image-20220528142340425.png)

#### **查看TF树**

在当前运行的两只海龟中，有哪些坐标系呢，我们可以通过这个小工具来做查看。

```
$ ros2 run tf2_tools view_frames 
```

默认在当前终端路径下生成了一个frames.pdf文件，打开之后，就可以看到系统中各个坐标系的关系了。

![image-20220528142507581](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.2_TF/image-20220528142507581.png)

#### **查询坐标变换信息**

只看到坐标系的结构还不行，如果我们想要知道某两个坐标系之间的具体关系，可以通过tf2_echo这个工具查看：

```
$ ros2 run tf2_ros tf2_echo turtle2 turtle1
```

运行成功后，终端中就会循环打印坐标系的变换数值了，由平移和旋转两个部分组成，还有旋转矩阵。

![image-20220530173017084](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.2_TF/image-20220530173017084.png)

#### **坐标系可视化**

看数值还不直观？可以试试用可视化软件来做显示：

```
$ ros2 run rviz2 rviz2 -d $(ros2 pkg prefix --share turtle_tf2_py)/rviz/turtle_rviz.rviz
```

再让小海龟动起来，Rviz中的坐标轴就会开始运动，这样是不是更加直观了呢！

![image-20220528142546418](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.2_TF/image-20220528142546418.png)

小海龟跟随的案例有点意思，这背后的原理是怎样的呢？大家不要着急，我们先来了解下TF的使用方法，便于大家慢慢理解。

### **静态TF广播**

我们说TF的主要作用是对坐标系进行管理，那就管理一个试试呗？

坐标变换中最为简单的应该是相对位置不发生变化的情况，比如你家的房子在哪个位置，只要房子不拆，这个坐标应该就不会变化。

在机器人系统中也很常见，比如激光雷达和机器人底盘之间的位置关系，安装好之后基本不会变化。

在TF中，这种情况也称之为**静态TF变换**，我们来看看在程序中该如何实现？

#### **运行效果**

启动终端，运行如下命令：

```
$ ros2 run learning_tf static_tf_broadcaster
$ ros2 run tf2_tools view_frames 
```

可以看到当前系统中存在两个坐标系，一个是world，一个是house，两者之间的相对位置不会发生改变，通过一个静态的TF对象进行维护。

![image-20220528142707675](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.2_TF/image-20220528142707675.png)

#### **代码解析**

来看下在代码中是如何创建坐标系并且发布静态变换的。

learning_tf/static_tf_broadcaster.py

```
#!/usr/bin/env python3
# -*- coding: utf-8 -*-

"""
@作者: 古月居(www.guyuehome.com)
@说明: ROS2 TF示例-广播静态的坐标变换
"""

import rclpy                                                                 # ROS2 Python接口库
from rclpy.node import Node                                                  # ROS2 节点类
from geometry_msgs.msg import TransformStamped                               # 坐标变换消息
import tf_transformations                                                    # TF坐标变换库
from tf2_ros.static_transform_broadcaster import StaticTransformBroadcaster  # TF静态坐标系广播器类

class StaticTFBroadcaster(Node):
    def __init__(self, name):
        super().__init__(name)                                                  # ROS2节点父类初始化
        self.tf_broadcaster = StaticTransformBroadcaster(self)                  # 创建一个TF广播器对象

        static_transformStamped = TransformStamped()                            # 创建一个坐标变换的消息对象
        static_transformStamped.header.stamp = self.get_clock().now().to_msg()  # 设置坐标变换消息的时间戳
        static_transformStamped.header.frame_id = 'world'                       # 设置一个坐标变换的源坐标系
        static_transformStamped.child_frame_id  = 'house'                       # 设置一个坐标变换的目标坐标系
        static_transformStamped.transform.translation.x = 10.0                  # 设置坐标变换中的X、Y、Z向的平移
        static_transformStamped.transform.translation.y = 5.0                    
        static_transformStamped.transform.translation.z = 0.0
        quat = tf_transformations.quaternion_from_euler(0.0, 0.0, 0.0)          # 将欧拉角转换为四元数（roll, pitch, yaw）
        static_transformStamped.transform.rotation.x = quat[0]                  # 设置坐标变换中的X、Y、Z向的旋转（四元数）
        static_transformStamped.transform.rotation.y = quat[1]
        static_transformStamped.transform.rotation.z = quat[2]
        static_transformStamped.transform.rotation.w = quat[3]

        self.tf_broadcaster.sendTransform(static_transformStamped)              # 广播静态坐标变换，广播后两个坐标系的位置关系保持不变

def main(args=None):
    rclpy.init(args=args)                                # ROS2 Python接口初始化
    node = StaticTFBroadcaster("static_tf_broadcaster")  # 创建ROS2节点对象并进行初始化
    rclpy.spin(node)                                     # 循环等待ROS2退出
    node.destroy_node()                                  # 销毁节点对象
    rclpy.shutdown()
```

完成代码的编写后需要设置功能包的编译选项，让系统知道Python程序的入口，打开功能包的setup.py文件，加入如下入口点的配置：

```
    entry_points={
        'console_scripts': [
            'static_tf_broadcaster = learning_tf.static_tf_broadcaster:main',
        ],
    },
```

经过这段代码，两个坐标系的变化是描述清楚了，到了使用的时候，我们又该如何查询呢？

### **TF监听**

我们再来学习下如何查询两个坐标系之间的位置关系。

#### **运行效果**

启动一个终端，运行如下节点，就可以在终端中看到周期显示的坐标关系了。

```
$ ros2 run learning_tf tf_listener
```

![image-20220528143704578](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.2_TF/image-20220528143704578.png)

#### **代码解析**

这个节点中是如何查询坐标关系的，我们来看下代码。

learning_tf/tf_listener.py

```
#!/usr/bin/env python3
# -*- coding: utf-8 -*-

"""
@作者: 古月居(www.guyuehome.com)
@说明: ROS2 TF示例-监听某两个坐标系之间的变换
"""

import rclpy                                              # ROS2 Python接口库
from rclpy.node import Node                               # ROS2 节点类
import tf_transformations                                 # TF坐标变换库
from tf2_ros import TransformException                    # TF左边变换的异常类
from tf2_ros.buffer import Buffer                         # 存储坐标变换信息的缓冲类
from tf2_ros.transform_listener import TransformListener  # 监听坐标变换的监听器类

class TFListener(Node):

    def __init__(self, name):
        super().__init__(name)                                      # ROS2节点父类初始化

        self.declare_parameter('source_frame', 'world')             # 创建一个源坐标系名的参数
        self.source_frame = self.get_parameter(                     # 优先使用外部设置的参数值，否则用默认值
            'source_frame').get_parameter_value().string_value

        self.declare_parameter('target_frame', 'house')             # 创建一个目标坐标系名的参数
        self.target_frame = self.get_parameter(                     # 优先使用外部设置的参数值，否则用默认值
            'target_frame').get_parameter_value().string_value

        self.tf_buffer = Buffer()                                   # 创建保存坐标变换信息的缓冲区
        self.tf_listener = TransformListener(self.tf_buffer, self)  # 创建坐标变换的监听器

        self.timer = self.create_timer(1.0, self.on_timer)          # 创建一个固定周期的定时器，处理坐标信息

    def on_timer(self):
        try:
            now = rclpy.time.Time()                                 # 获取ROS系统的当前时间
            trans = self.tf_buffer.lookup_transform(                # 监听当前时刻源坐标系到目标坐标系的坐标变换
                self.target_frame,
                self.source_frame,
                now)
        except TransformException as ex:                            # 如果坐标变换获取失败，进入异常报告
            self.get_logger().info(
                f'Could not transform {self.target_frame} to {self.source_frame}: {ex}')
            return

        pos  = trans.transform.translation                          # 获取位置信息
        quat = trans.transform.rotation                             # 获取姿态信息（四元数）
        euler = tf_transformations.euler_from_quaternion([quat.x, quat.y, quat.z, quat.w])
        self.get_logger().info('Get %s --> %s transform: [%f, %f, %f] [%f, %f, %f]' 
          % (self.source_frame, self.target_frame, pos.x, pos.y, pos.z, euler[0], euler[1], euler[2]))

def main(args=None):
    rclpy.init(args=args)                       # ROS2 Python接口初始化
    node = TFListener("tf_listener")            # 创建ROS2节点对象并进行初始化
    rclpy.spin(node)                            # 循环等待ROS2退出
    node.destroy_node()                         # 销毁节点对象
    rclpy.shutdown()                            # 关闭ROS2 Python接口
```

完成代码的编写后需要设置功能包的编译选项，让系统知道Python程序的入口，打开功能包的setup.py文件，加入如下入口点的配置：

```
    entry_points={
        'console_scripts': [
            'static_tf_broadcaster = learning_tf.static_tf_broadcaster:main',
            'tf_listener = learning_tf.tf_listener:main',
        ],
    },
```

好啦，大家现在对TF的基本使用有所了解了。我们继续挑战两只海龟跟随的案例。

### **海龟跟随功能解析**

还是之前小海龟跟随的示例，我们自己通过代码来实现一下。

#### **运行效果**

先看下实现的效果，启动终端后，通过如下命令启动例程：

```
$ ros2 launch learning_tf turtle_following_demo.launch.py
$ ros2 run turtlesim turtle_teleop_key
```

看到的效果和ROS自带的例程相同。

![image-20220528142340425](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.2_TF/image-20220528142340425.png)

#### **原理解析**

![image-20220528143750881](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.2_TF/image-20220528143750881.png)

在两只海龟的仿真器中，我们可以定义三个坐标系，比如仿真器的全局参考系叫做world，turtle1和turtle2坐标系在两只海龟的中心点，这样，turtle1和world坐标系的相对位置，就可以表示海龟1的位置，海龟2也同理。

要实现海龟2向海龟1运动，我们在两者中间做一个连线，再加一个箭头，怎么样，是不是有想起高中时学习的向量计算？我们说坐标变换的描述方法就是向量，所以在这个跟随例程中，用TF就可以很好的解决。

向量的长度表示距离，方向表示角度，有了距离和角度，我们随便设置一个时间，不就可以计算得到速度了么，然后就是速度话题的封装和发布，海龟2也就可以动起来了。

所以这个例程的核心就是通过坐标系实现向量的计算，两只海龟还会不断运动，这个向量也得按照某一个周期计算，这就得用上TF的动态广播与监听了。

我们一起看下代码该如何实现。

#### **Launch文件解析**

先来看下刚才运行的launch文件，里边启动了四个节点，分别是：

- 小海龟仿真器
- 海龟1的坐标系广播
- 海龟2的坐标系广播
- 海龟跟随控制

其中，两个坐标系的广播复用了turtle_tf_broadcaster节点，通过传入的参数名修改维护的坐标系名称。

learning_tf/launch/turtle_following_demo.launch.py

```
from launch import LaunchDescription
from launch.actions import DeclareLaunchArgument
from launch.substitutions import LaunchConfiguration
from launch_ros.actions import Node


def generate_launch_description():
    return LaunchDescription([
        Node(
            package='turtlesim',
            executable='turtlesim_node',
            name='sim'
        ),
        Node(
            package='learning_tf',
            executable='turtle_tf_broadcaster',
            name='broadcaster1',
            parameters=[
                {'turtlename': 'turtle1'}
            ]
        ),
        DeclareLaunchArgument(
            'target_frame', default_value='turtle1',
            description='Target frame name.'
        ),
        Node(
            package='learning_tf',
            executable='turtle_tf_broadcaster',
            name='broadcaster2',
            parameters=[
                {'turtlename': 'turtle2'}
            ]
        ),
        Node(
            package='learning_tf',
            executable='turtle_following',
            name='listener',
            parameters=[
                {'target_frame': LaunchConfiguration('target_frame')}
            ]
        ), 
    ])
```

#### **坐标系动态广播**

海龟1和海龟2在world坐标系下的坐标变换，在turtle_tf_broadcaster节点中实现，除了海龟坐标系的名字不同之外，针对两个海龟的功能是一样的。

learning_tf/turtle_tf_broadcaster.py

```
#!/usr/bin/env python3
# -*- coding: utf-8 -*-

"""
@作者: 古月居(www.guyuehome.com)
@说明: ROS2 TF示例-广播动态的坐标变换
"""

import rclpy                                       # ROS2 Python接口库
from rclpy.node import Node                        # ROS2 节点类
from geometry_msgs.msg import TransformStamped     # 坐标变换消息
import tf_transformations                          # TF坐标变换库
from tf2_ros import TransformBroadcaster           # TF坐标变换广播器
from turtlesim.msg import Pose                     # turtlesim小海龟位置消息

class TurtleTFBroadcaster(Node):

    def __init__(self, name):
        super().__init__(name)                                # ROS2节点父类初始化

        self.declare_parameter('turtlename', 'turtle')        # 创建一个海龟名称的参数
        self.turtlename = self.get_parameter(                 # 优先使用外部设置的参数值，否则用默认值
            'turtlename').get_parameter_value().string_value

        self.tf_broadcaster = TransformBroadcaster(self)      # 创建一个TF坐标变换的广播对象并初始化

        self.subscription = self.create_subscription(         # 创建一个订阅者，订阅海龟的位置消息
            Pose,
            f'/{self.turtlename}/pose',                       # 使用参数中获取到的海龟名称
            self.turtle_pose_callback, 1)

    def turtle_pose_callback(self, msg):                              # 创建一个处理海龟位置消息的回调函数，将位置消息转变成坐标变换
        transform = TransformStamped()                                # 创建一个坐标变换的消息对象

        transform.header.stamp = self.get_clock().now().to_msg()      # 设置坐标变换消息的时间戳
        transform.header.frame_id = 'world'                           # 设置一个坐标变换的源坐标系
        transform.child_frame_id = self.turtlename                    # 设置一个坐标变换的目标坐标系
        transform.transform.translation.x = msg.x                     # 设置坐标变换中的X、Y、Z向的平移
        transform.transform.translation.y = msg.y
        transform.transform.translation.z = 0.0
        q = tf_transformations.quaternion_from_euler(0, 0, msg.theta) # 将欧拉角转换为四元数（roll, pitch, yaw）
        transform.transform.rotation.x = q[0]                         # 设置坐标变换中的X、Y、Z向的旋转（四元数）
        transform.transform.rotation.y = q[1]
        transform.transform.rotation.z = q[2]
        transform.transform.rotation.w = q[3]

        # Send the transformation
        self.tf_broadcaster.sendTransform(transform)     # 广播坐标变换，海龟位置变化后，将及时更新坐标变换信息

def main(args=None):
    rclpy.init(args=args)                                # ROS2 Python接口初始化
    node = TurtleTFBroadcaster("turtle_tf_broadcaster")  # 创建ROS2节点对象并进行初始化
    rclpy.spin(node)                                     # 循环等待ROS2退出
    node.destroy_node()                                  # 销毁节点对象
    rclpy.shutdown()                                     # 关闭ROS2 Python接口
```

完成代码的编写后需要设置功能包的编译选项，让系统知道Python程序的入口，打开功能包的setup.py文件，加入如下入口点的配置：

```
    entry_points={
        'console_scripts': [
            'static_tf_broadcaster = learning_tf.static_tf_broadcaster:main',
            'turtle_tf_broadcaster = learning_tf.turtle_tf_broadcaster:main',
            'tf_listener = learning_tf.tf_listener:main',
        ],
    },
```

#### **海龟跟随**

坐标系都正常广播了，接下来我们就可以订阅两只海龟的位置关系，并且变换成速度指令进行控制啦。

learning_tf/turtle_following.py

```
#!/usr/bin/env python3
# -*- coding: utf-8 -*-

"""
@作者: 古月居(www.guyuehome.com)
@说明: ROS2 TF示例-通过坐标变化实现海龟跟随功能
"""

import math
import rclpy                                              # ROS2 Python接口库
from rclpy.node import Node                               # ROS2 节点类
import tf_transformations                                 # TF坐标变换库
from tf2_ros import TransformException                    # TF左边变换的异常类
from tf2_ros.buffer import Buffer                         # 存储坐标变换信息的缓冲类
from tf2_ros.transform_listener import TransformListener  # 监听坐标变换的监听器类
from geometry_msgs.msg import Twist                       # ROS2 速度控制消息
from turtlesim.srv import Spawn                           # 海龟生成的服务接口
class TurtleFollowing(Node):

    def __init__(self, name):
        super().__init__(name)                                      # ROS2节点父类初始化

        self.declare_parameter('source_frame', 'turtle1')           # 创建一个源坐标系名的参数
        self.source_frame = self.get_parameter(                     # 优先使用外部设置的参数值，否则用默认值
            'source_frame').get_parameter_value().string_value

        self.tf_buffer = Buffer()                                   # 创建保存坐标变换信息的缓冲区
        self.tf_listener = TransformListener(self.tf_buffer, self)  # 创建坐标变换的监听器

        self.spawner = self.create_client(Spawn, 'spawn')           # 创建一个请求产生海龟的客户端
        self.turtle_spawning_service_ready = False                  # 是否已经请求海龟生成服务的标志位
        self.turtle_spawned = False                                 # 海龟是否产生成功的标志位

        self.publisher = self.create_publisher(Twist, 'turtle2/cmd_vel', 1) # 创建跟随运动海龟的速度话题

        self.timer = self.create_timer(1.0, self.on_timer)         # 创建一个固定周期的定时器，控制跟随海龟的运动

    def on_timer(self):
        from_frame_rel = self.source_frame                         # 源坐标系
        to_frame_rel   = 'turtle2'                                 # 目标坐标系

        if self.turtle_spawning_service_ready:                     # 如果已经请求海龟生成服务
            if self.turtle_spawned:                                # 如果跟随海龟已经生成
                try:
                    now = rclpy.time.Time()                        # 获取ROS系统的当前时间
                    trans = self.tf_buffer.lookup_transform(       # 监听当前时刻源坐标系到目标坐标系的坐标变换
                        to_frame_rel,
                        from_frame_rel,
                        now)
                except TransformException as ex:                   # 如果坐标变换获取失败，进入异常报告
                    self.get_logger().info(
                        f'Could not transform {to_frame_rel} to {from_frame_rel}: {ex}')
                    return

                msg = Twist()                                      # 创建速度控制消息
                scale_rotation_rate = 1.0                          # 根据海龟角度，计算角速度
                msg.angular.z = scale_rotation_rate * math.atan2(
                    trans.transform.translation.y,
                    trans.transform.translation.x)

                scale_forward_speed = 0.5                          # 根据海龟距离，计算线速度
                msg.linear.x = scale_forward_speed * math.sqrt(
                    trans.transform.translation.x ** 2 +
                    trans.transform.translation.y ** 2)

                self.publisher.publish(msg)                        # 发布速度指令，海龟跟随运动
            else:                                                  # 如果跟随海龟没有生成
                if self.result.done():                             # 查看海龟是否生成
                    self.get_logger().info(
                        f'Successfully spawned {self.result.result().name}')
                    self.turtle_spawned = True                     
                else:                                              # 依然没有生成跟随海龟
                    self.get_logger().info('Spawn is not finished')
        else:                                                      # 如果没有请求海龟生成服务
            if self.spawner.service_is_ready():                    # 如果海龟生成服务器已经准备就绪
                request = Spawn.Request()                          # 创建一个请求的数据
                request.name = 'turtle2'                           # 设置请求数据的内容，包括海龟名、xy位置、姿态
                request.x = float(4)
                request.y = float(2)
                request.theta = float(0)

                self.result = self.spawner.call_async(request)     # 发送服务请求
                self.turtle_spawning_service_ready = True          # 设置标志位，表示已经发送请求
            else:
                self.get_logger().info('Service is not ready')     # 海龟生成服务器还没准备就绪的提示


def main(args=None):
    rclpy.init(args=args)                       # ROS2 Python接口初始化
    node = TurtleFollowing("turtle_following")  # 创建ROS2节点对象并进行初始化
    rclpy.spin(node)                            # 循环等待ROS2退出
    node.destroy_node()                         # 销毁节点对象
    rclpy.shutdown()                            # 关闭ROS2 Python接口
```

完成代码的编写后需要设置功能包的编译选项，让系统知道Python程序的入口，打开功能包的setup.py文件，加入如下入口点的配置：

```
    entry_points={
        'console_scripts': [
            'static_tf_broadcaster = learning_tf.static_tf_broadcaster:main',
            'turtle_tf_broadcaster = learning_tf.turtle_tf_broadcaster:main',
            'tf_listener = learning_tf.tf_listener:main',
            'turtle_following = learning_tf.turtle_following:main',
        ],
    },
```

## 3.3 URDF：机器人建模方法

ROS是机器人操作系统，当然要给机器人使用啦，不过在使用之前，还得让ROS认识下我们使用的机器人，如何把一个机器人介绍给ROS呢？

为此，ROS专门提供了一种机器人建模方法——**URDF**，用来描述机器人外观、性能等各方面属性。

### **机器人的组成**

建模描述机器人的过程中，我们自己需要先熟悉机器人的组成和参数，比如机器人一般是由**硬件结构、驱动系统、传感器系统、控制系统**四大部分组成，市面上一些常见的机器人，无论是移动机器人还是机械臂，我们都可以按照这四大组成部分进行分解。

![image-20220528144350325](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.3_URDF/image-20220528144350325.png)

- 硬件结构就是底盘、外壳、电机等实打实可以看到的设备；
- 驱动系统就是可以驱使这些设备正常使用的装置，比如电机的驱动器，电源管理系统等；
- 传感系统包括电机上的编码器、板载的IMU、安装的摄像头、雷达等等，便于机器人感知自己的状态和外部的环境；
- 控制系统就是我们开发过程的主要载体了，一般是树莓派、电脑等计算平台，以及里边的操作系统和应用软件。

机器人建模的过程，其实就是按照类似的思路，通过建模语言，把机器人每一个部分都描述清楚，再组合起来的过程。

### **URDF**

![image-20220528144416270](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.3_URDF/image-20220528144416270.png)

ROS中的建模方法叫做**URDF**，全称是**统一机器人描述格式**，不仅可以清晰描述机器人自身的模型，还可以描述机器人的外部环境，比如这里的桌子，也可以算作一个模型。

![image-20220528144424329](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.3_URDF/image-20220528144424329.png)

URDF模型文件使用的是**XML格式**，右侧就是一个机器人的URDF描述，乍看上去，有点像网页开发的源代码，都是由一系列尖括号包围的标签和其中的属性组合而成。

如何使用这样一个文件描述机器人呢？比如这个机械臂，大家可以看下自己的手臂，我们的手臂是由大臂和小臂组成，他们独自是无法运动的，必须通过一个手肘关节连接之后，才能通过肌肉驱动，产生相对运动。

在建模中，大臂和小臂就类似机器人的这些独立的刚体部分，称为**连杆Link**，手肘就类似于机器人电机驱动部分，称为**关节joint**。

所以在URDF建模过程中，关键任务就是通过这里的<link>和<joint>，理清楚每一个连杆和关节的描述信息。

#### **连杆Link的描述**

<link>标签用来描述机器人某个刚体部分的**外观和物理属性**，外观包括尺寸、颜色、形状，物理属性包括质量、惯性矩阵、碰撞参数等。

![image-20220528144534685](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.3_URDF/image-20220528144534685.png)

以这个机械臂连杆为例，它的link描述如下：

![image-20220528144549092](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.3_URDF/image-20220528144549092.png)

link标签中的name表示该连杆的名称，我们可以自定义，未来joint连接link的时候，会使用到这个名称。

link里边的<visual>部分用来描述机器人的外观，比如：

- <geometry>表示**几何形状**，里边使用<mesh>调用了一个在三维软件中提前设计好的蓝色外观，就是这个stl文件，看上去和真实机器人是一致的
- <origin>表示**坐标系相对初始位置的偏移**，分别是x、y、z方向上的平移，和roll、pitch、raw旋转，不需要偏移的话，就全为0。

第二个部分<collision>，描述**碰撞参数**，里边的内容似乎和<visual>一样，也有<geometry>和<origin>，看似相同，其实区别还是比较大的。

- <visual>部分重在描述机器人看上去的状态，也就是视觉效果；
- <collision>部分则是描述机器人运动过程中的状态，比如机器人与外界如何接触算作碰撞。

在这个机器人模型中，蓝色部分是通过<visual>来描述的，在实际控制过程中，这样复杂的外观在计算碰撞检测时，要求的算力较高，为了简化计算，我们将碰撞检测用的模型简化为了绿色框的圆柱体，也就是<collision>里边<geometry>描述的形状。<origin>坐标系偏移也是类似，可以描述刚体质心的偏移。

![image-20220528144603646](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.3_URDF/image-20220528144603646.png)

如果是移动机器人的话，link也可以用来描述小车的车体、轮子等部分。

#### **关节Joint描述**

机器人模型中的刚体最终要通过关节joint连接之后，才能产生相对运动。

URDF中的关节有六种运动类型。

![image-20220528144655899](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.3_URDF/image-20220528144655899.png)

1. continuous，描述旋转运动，可以围绕某一个轴无限旋转，比如小车的轮子，就属于这种类型。
2. revolute，也是旋转关节，和continuous类型的区别在于不能无限旋转，而是带有角度限制，比如机械臂的两个连杆，就属于这种运动。
3. prismatic，是滑动关节，可以沿某一个轴平移，也带有位置的极限，一般直线电机就是这种运动方式。
4. fixed，固定关节，是唯一一种不允许运动的关节，不过使用还是比较频繁的，比如相机这个连杆，安装在机器人上，相对位置是不会变化的，此时使用的连接方式就是Fixed。
5. Floating是浮动关节，第六种planar是平面关节，这两种使用相对较少。

![image-20220528144722751](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.3_URDF/image-20220528144722751.png)

在URDF模型中，每一个link都使用这样一段xml内容描述，比如关节的名字叫什么，运动类型是哪一种。

![image-20220528144729633](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.3_URDF/image-20220528144729633-16537204524521.png)

- parent标签：描述父连杆；
- child标签：描述子连杆，子连杆会相对父连杆发生运动；
- origin：表示两个连杆坐标系之间的关系，也就是图中红色的向量，可以理解为这两个连杆该如何安装到一起；
- axis表示关节运动轴的单位向量，比如z等于1，就表示这个旋转运动是围绕z轴的正方向进行的；
- limit就表示运动的一些限制了，比如最小位置，最大位置，和最大速度等。

<details class="info" open="open" style="box-sizing: inherit; display: flow-root; overflow: visible; padding: 0px 0.6rem; background-color: var(--md-admonition-bg-color); border-width: 0px 0px 0px 0.2rem; border-style: solid; border-color: rgb(0, 184, 212); border-image: initial; border-radius: 0.1rem; box-shadow: var(--md-shadow-z1); color: rgba(0, 0, 0, 0.87); font-size: 0.64rem; margin: 1.5625em 0px; break-inside: avoid; font-family: Roboto, -apple-system, BlinkMacSystemFont, Helvetica, Arial, sans-serif; font-style: normal; font-variant-ligatures: normal; font-variant-caps: normal; font-weight: 400; letter-spacing: normal; orphans: 2; text-align: start; text-indent: 0px; text-transform: none; widows: 2; word-spacing: 0px; -webkit-text-stroke-width: 0px; white-space: normal; text-decoration-thickness: initial; text-decoration-style: initial; text-decoration-color: initial;"><summary style="box-sizing: border-box; cursor: pointer; display: block; min-height: 1rem; background-color: rgba(0, 184, 212, 0.1); border-top: none; border-right: none; border-bottom: none; border-left: 0.2rem none; border-image: initial; font-weight: 700; margin: 0px -0.6rem 0px -0.8rem; padding: 0.4rem 0.6rem 0.4rem 2.2rem; position: relative; border-top-left-radius: 0.1rem; border-top-right-radius: 0.1rem; -webkit-tap-highlight-color: transparent; outline: none;">Info</summary><p style="box-sizing: border-box; margin-bottom: 0.6rem;">ROS中关于平移的默认单位是m，旋转是弧度（不是度），所以这里的3.14就表示可以在-180度到180度之间运动，线速度是m/s，角速度是rad/s。</p></details>

#### **完整机器人模型**

![image-20220528144900705](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.3_URDF/image-20220528144900705.png)

最终所有的link和joint标签完成了对机器人每个部分的描述和组合，全都放在一个robot标签中，就形成了完整的机器人模型。

![image-20220528144824234](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.3_URDF/image-20220528144824234.png)

所以大家在看某一个URDF模型时，先不着急看每一块代码的细节，先来找link和joint，看下这个机器人是由哪些部分组成的，了解完全局之后，再看细节。

### **创建机器人模型**

好啦，讲了这么多，还是要看一个完整的示例。

![image-20220528145019891](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.3_URDF/image-20220528145019891.png)

我们以这款移动机器人模型为例，一起看下它的URDF建模过程。

#### **功能包结构**

机器人的模型放置在learning_urdf功能包中，功能包中包含的文件夹如下：

![image-20220528145030778](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.3_URDF/image-20220528145030778.png)

- urdf：存放机器人模型的URDF或xacro文件
- meshes：放置URDF中引用的模型渲染文件
- launch：保存相关启动文件
- rviz：保存rviz的配置文件

#### **模型可视化效果**

我们先来看下这个模型的效果，尝试逆向分下一下机器人的结构。

```
$ ros2 launch learning_urdf display.launch.py
```

很快就可以看到Rviz中显示的机器人模型啦，大家可以使用鼠标拖拽观察。

![image-20220530175131389](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.3_URDF/image-20220530175131389.png)

从可视化的效果来看，这个机器人由五个link和4个joint组成。

#### **查看URDF模型结构**

我们分析的对不对呢，可以在模型文件的路径下，使用urdf_to_graphviz这个小工具来分析下。

```
$ urdf_to_graphviz mbot_base.urdf  # 在模型文件夹下运行
```

运行成功后会产生一个pdf文件，打开之后就可以看到URDF模型分析的结果啦，是不是和我们的猜测完全相同呢！

![image-20220528145132111](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.3_URDF/image-20220528145132111.png)

#### **模型文件解析**

具体URDF模型什么样的，还是要打开模型来研究。

learning_urdf/urdf/mbot_base.urdf

```
<?xml version="1.0" ?>
<robot name="mbot">

    <link name="base_link">
        <visual>
            <origin xyz=" 0 0 0" rpy="0 0 0" />
            <geometry>
                <cylinder length="0.16" radius="0.20"/>
            </geometry>
            <material name="yellow">
                <color rgba="1 0.4 0 1"/>
            </material>
        </visual>
    </link>

    <joint name="left_wheel_joint" type="continuous">
        <origin xyz="0 0.19 -0.05" rpy="0 0 0"/>
        <parent link="base_link"/>
        <child link="left_wheel_link"/>
        <axis xyz="0 1 0"/>
    </joint>

    <link name="left_wheel_link">
        <visual>
            <origin xyz="0 0 0" rpy="1.5707 0 0" />
            <geometry>
                <cylinder radius="0.06" length = "0.025"/>
            </geometry>
            <material name="white">
                <color rgba="1 1 1 0.9"/>
            </material>
        </visual>
    </link>

    <joint name="right_wheel_joint" type="continuous">
        <origin xyz="0 -0.19 -0.05" rpy="0 0 0"/>
        <parent link="base_link"/>
        <child link="right_wheel_link"/>
        <axis xyz="0 1 0"/>
    </joint>

    <link name="right_wheel_link">
        <visual>
            <origin xyz="0 0 0" rpy="1.5707 0 0" />
            <geometry>
                <cylinder radius="0.06" length = "0.025"/>
            </geometry>
            <material name="white">
                <color rgba="1 1 1 0.9"/>
            </material>
        </visual>
    </link>

    <joint name="front_caster_joint" type="continuous">
        <origin xyz="0.18 0 -0.095" rpy="0 0 0"/>
        <parent link="base_link"/>
        <child link="front_caster_link"/>
        <axis xyz="0 1 0"/>
    </joint>

    <link name="front_caster_link">
        <visual>
            <origin xyz="0 0 0" rpy="0 0 0"/>
            <geometry>
                <sphere radius="0.015" />
            </geometry>
            <material name="black">
                <color rgba="0 0 0 0.95"/>
            </material>
        </visual>
    </link>

    <joint name="back_caster_joint" type="continuous">
        <origin xyz="-0.18 0 -0.095" rpy="0 0 0"/>
        <parent link="base_link"/>
        <child link="back_caster_link"/>
        <axis xyz="0 1 0"/>
    </joint>

    <link name="back_caster_link">
        <visual>
            <origin xyz="0 0 0" rpy="0 0 0"/>
            <geometry>
                <sphere radius="0.015" />
            </geometry>
            <material name="black">
                <color rgba="0 0 0 0.95"/>
            </material>
        </visual>
    </link>

</robot>
```

## 3.4 Gazebo：三维物理仿真平台

ROS机器人开发，机器人当然是主角，如果我们手边没有实物机器人，怎么办呢？没问题，机器人三维物理仿真平台**Gazebo**，了解一下。

### **Gazebo仿真平台**

#### **介绍**

Gazebo是ROS系统中最为常用的**三维物理仿真平台**，支持动力学引擎，可以实现高质量的图形渲染，不仅可以模拟机器人及周边环境，还可以加入摩擦力、弹性系数等物理属性。

![image-20220528145639277](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.4_Gazebo/image-20220528145639277.png)

比如我们要开发一个火星车，那就可以在Gazebo中模拟火星表面的环境，再比如我们做无人机，续航和限飞都导致我们没有办法频繁用实物做实验，此时不妨使用Gazebo先做仿真，等算法开发的差不多了，再部署到实物上来运行。

所以类似Gazebo这样的仿真平台，可以帮助我们验证机器人算法、优化机器人设计、测试机器人场景应用，为机器人开发提供更多可能。

#### **安装**

Gazebo如何使用呢？我们不妨先把它给跑起来，互相认识一下。

为了确保系统中已经完整安装了Gazebo相关的功能包，大家可以通过这样一个命令，简单直接的把和gazebo相关的包都给装上：

```
$ sudo apt install ros-humble-gazebo-*
```

#### **运行**

通过这句命令就可以启动啦：

```
$ ros2 launch gazebo_ros gazebo.launch.py
```

![image-20220528145818827](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.4_Gazebo/image-20220528145818827.png)

<details class="attention" open="open" style="box-sizing: inherit; display: flow-root; overflow: visible; padding: 0px 0.6rem; background-color: var(--md-admonition-bg-color); border-width: 0px 0px 0px 0.2rem; border-style: solid; border-color: rgb(255, 145, 0); border-image: initial; border-radius: 0.1rem; box-shadow: var(--md-shadow-z1); color: rgba(0, 0, 0, 0.87); font-size: 0.64rem; margin: 1.5625em 0px; break-inside: avoid; font-family: Roboto, -apple-system, BlinkMacSystemFont, Helvetica, Arial, sans-serif; font-style: normal; font-variant-ligatures: normal; font-variant-caps: normal; font-weight: 400; letter-spacing: normal; orphans: 2; text-align: start; text-indent: 0px; text-transform: none; widows: 2; word-spacing: 0px; -webkit-text-stroke-width: 0px; white-space: normal; text-decoration-thickness: initial; text-decoration-style: initial; text-decoration-color: initial;"><summary style="box-sizing: border-box; cursor: pointer; display: block; min-height: 1rem; background-color: rgba(255, 145, 0, 0.1); border-top: none; border-right: none; border-bottom: none; border-left: 0.2rem none; border-image: initial; font-weight: 700; margin: 0px -0.6rem 0px -0.8rem; padding: 0.4rem 0.6rem 0.4rem 2.2rem; position: relative; border-top-left-radius: 0.1rem; border-top-right-radius: 0.1rem; -webkit-tap-highlight-color: transparent; outline: none;">Attention</summary><p style="box-sizing: border-box; margin-bottom: 0.6rem;">为保证模型顺利加载，请将离线模型下载并放置到~/.gazebo/models路径下</p></details>

，下载链接如下：https://github.com/osrf/gazebo_models

认识了Gazebo，接下来是不是该试试机器人仿真啦？

大家还记得之前课程中，我们设计的移动机器人模型么？我们一起尝试把它放到Gazebo中，还要控制它在仿真环境中运动。

### **XACRO机器人模型优化**

我们之前设计好的URDF模型此时还不能直接放到Gazebo中，需要我们做一些优化。这里给大家介绍一个URDF文件格式的升级版本——**XACRO文件**。

同样也是对机器人URDF模型的创建，XACRO文件加入了更多编程化的实现方法，可以让模型创建更友好。

![image-20220528145940535](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.4_Gazebo/image-20220528145940535.png)

比如：

- **宏定义**，一个小车有4个轮子，每个轮子都一样，我们就没必要创建4个一样的link，像函数定义一样，做一个可重复使用的模块就可以了。
- **文件包含**，复杂机器人的模型文件可能会很长，为了切分不同的模块，比如底盘、传感器，我们还可以把不同模块的模型放置在不同的文件中，然后再用一个总体文件做包含调用。
- **可编程接口**，比如在XACRO模型文件中，定义一些常量，描述机器人的尺寸，定义一些变量，在调用宏定义的时候传递数据，还可以在模型中做数据计算，甚至加入条件语句，比如你的机器人叫A，就有摄像头，如果叫B，就没有摄像头。

XACRO建模过程就像写代码一样，功能更为丰富了。

接下来，我们就通过XACRO文件对移动机器人的模型做一下优化，大家先要使用这句命令安装必要的功能包。

```
$ sudo apt install ros-humble-xacro
```

以下是一些常用的XACRO文件语法，大家了解下。

#### **常量定义**

![image-20220528150321426](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.4_Gazebo/image-20220528150321426.png)

<xacro:property>标签用来定义一些常量，比如这样定义一个PI的常量名为“M_PI”，值为“3.14159”，在调用的时候，通过$加大括号，里边就可以使用定义好的常量了。

![image-20220528150331042](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.4_Gazebo/image-20220528150331042.png)

针对原本移动机器人的URDF文件，我们就可以把底盘的质量、尺寸，轮子的质量、尺寸、安装位置，这些不会变化的数据，都通过常量定义，未来需要修改的时候也很方便，就不需要在模型文件中一行一行找了。

![image-20220528150338969](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.4_Gazebo/image-20220528150338969.png)

#### **数学计算**

![image-20220528150430205](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.4_Gazebo/image-20220528150430205.png)

如果需要做数学计算，同样是在“${}”中进行，比如某一个位置，我们可以通过这两个常量做运算得到，就加入了加法和除法运算。

![image-20220528150435206](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.4_Gazebo/image-20220528150435206.png)

在移动机器人的模型中，很多有相对关系的数据，我们尽量都改成公式计算，如果直接写结果的数值，未来修改的时候，可能根本想不起来这个数据是怎么来的。

<details class="info" open="open" style="box-sizing: inherit; display: flow-root; overflow: visible; padding: 0px 0.6rem; background-color: var(--md-admonition-bg-color); border-width: 0px 0px 0px 0.2rem; border-style: solid; border-color: rgb(0, 184, 212); border-image: initial; border-radius: 0.1rem; box-shadow: var(--md-shadow-z1); color: rgba(0, 0, 0, 0.87); font-size: 0.64rem; margin: 1.5625em 0px; break-inside: avoid; font-family: Roboto, -apple-system, BlinkMacSystemFont, Helvetica, Arial, sans-serif; font-style: normal; font-variant-ligatures: normal; font-variant-caps: normal; font-weight: 400; letter-spacing: normal; orphans: 2; text-align: start; text-indent: 0px; text-transform: none; widows: 2; word-spacing: 0px; -webkit-text-stroke-width: 0px; white-space: normal; text-decoration-thickness: initial; text-decoration-style: initial; text-decoration-color: initial;"><summary style="box-sizing: border-box; cursor: pointer; display: block; min-height: 1rem; background-color: rgba(0, 184, 212, 0.1); border-top: none; border-right: none; border-bottom: none; border-left: 0.2rem none; border-image: initial; font-weight: 700; margin: 0px -0.6rem 0px -0.8rem; padding: 0.4rem 0.6rem 0.4rem 2.2rem; position: relative; border-top-left-radius: 0.1rem; border-top-right-radius: 0.1rem; -webkit-tap-highlight-color: transparent; outline: none;">Info</summary><p style="box-sizing: border-box; margin-bottom: 0.6rem;">所有数学运算都会转换成浮点数进行，以保证运算精度</p></details>

#### **宏定义**

![image-20220528150542643](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.4_Gazebo/image-20220528150542643.png)

机器人的轮子我们也做成宏定义，定义方式是通过这个<xacro:macro>标签描述的，还可以像函数一样，设置里边会用到的一些参数，比如这里的A、B、C。

当需要使用这个宏的时候，就可以像这样，通过宏名字的标签，来调用，同时要记得把几个参数设置好。

![image-20220528150603346](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.4_Gazebo/image-20220528150603346.png)

比如在模型中，轮子的宏定义是这样的，包含了link描述和joint关节设置，link的名称和关节的位置，是通过输入的参数来区分的，在使用的时候，通过这两句调用，两个轮子就出现了。

![image-20220528150619175](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.4_Gazebo/image-20220528150619175.png)

这里的1和-1，是设置关节位置的，刚好是一个镜像关系。

#### **文件包含**

![image-20220528150712684](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.4_Gazebo/image-20220528150712684.png)

宏定义是可以嵌套的，于是我们把机器人的底盘也做成了一个宏，然后使用另外一个模型文件，对底盘宏定义的文件做了一个包含，然后再调用。

![image-20220528150741631](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.4_Gazebo/image-20220528150741631.png)

这种流程是不是似曾相识，很像C语言中的include文件包含，然后再去调用里边的某些函数。

到这里为止，仿真使用的模型优化还没有结束，接下来我们还得加入一些仿真必备的模块和参数。

### **机器人仿真模型配置**

#### **完善物理参数**

第一步是确保每一个link都有惯性参数和碰撞属性，因为Gazebo是物理仿真平台，必要的物理参数是一定需要的。

![image-20220528150842585](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.4_Gazebo/image-20220528150842585.png)

![image-20220528150832258](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.4_Gazebo/image-20220528150832258.png)

#### **添加Gazebo标签**

第二步是为link添加gazebo标签，主要是为了可以在gazebo中渲染每一个link的颜色，因为URDF中的颜色系统和gazebo中的不同，所以得做一步这样的冗余配置。

![image-20220528150931153](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.4_Gazebo/image-20220528150931153.png)

#### **配置传动装置**

第三步是要给运动的joint配置传动装置，可以理解为仿真了一个电机。

![image-20220528150958309](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.4_Gazebo/image-20220528150958309.png)

#### **添加控制器插件**

第四步，要添加一个gazebo的控制器插件，小车是差速控制的，那就添加差速控制器插件，这样在不同角度下两个电机的速度分配，就可以交给控制器插件来完成了。

![image-20220528151019063](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.4_Gazebo/image-20220528151019063.png)

#### **构建仿真环境**

接下来就考虑如何把模型加载到Gazebo中了，需要用到一个gazebo提供的功能节点spwan_entity。

learning_gazebo/launch/load_urdf_into_gazebo.launch.py

```
import os

from ament_index_python.packages import get_package_share_directory


from launch import LaunchDescription
from launch.actions import IncludeLaunchDescription
from launch.launch_description_sources import PythonLaunchDescriptionSource

from launch_ros.actions import Node


def generate_launch_description():


    # Include the robot_state_publisher launch file, provided by our own package. Force sim time to be enabled
    # !!! MAKE SURE YOU SET THE PACKAGE NAME CORRECTLY !!!

    package_name='learning_gazebo' #<--- CHANGE ME
    world_file_path = 'worlds/neighborhood.world'

    pkg_path = os.path.join(get_package_share_directory(package_name))
    world_path = os.path.join(pkg_path, world_file_path)  

    # Pose where we want to spawn the robot
    spawn_x_val = '0.0'
    spawn_y_val = '0.0'
    spawn_z_val = '0.0'
    spawn_yaw_val = '0.0'

    mbot = IncludeLaunchDescription(
                PythonLaunchDescriptionSource([os.path.join(
                    get_package_share_directory(package_name),'launch','mbot.launch.py'
                )]), launch_arguments={'use_sim_time': 'true', 'world':world_path}.items()
    )

    # Include the Gazebo launch file, provided by the gazebo_ros package
    gazebo = IncludeLaunchDescription(
                PythonLaunchDescriptionSource([os.path.join(
                    get_package_share_directory('gazebo_ros'), 'launch', 'gazebo.launch.py')]),
             )

    # Run the spawner node from the gazebo_ros package. The entity name doesn't really matter if you only have a single robot.
    spawn_entity = Node(package='gazebo_ros', executable='spawn_entity.py',
                        arguments=['-topic', 'robot_description',
                                   '-entity', 'mbot',
                                   '-x', spawn_x_val,
                                   '-y', spawn_y_val,
                                   '-z', spawn_z_val,
                                   '-Y', spawn_yaw_val],
                        output='screen')



    # Launch them all!
    return LaunchDescription([
        mbot,
        gazebo,
        spawn_entity,
    ])
```

### **机器人运动仿真**

万事俱备，接下来就是见证奇迹的时刻。

我们需要运行两句命令，第一句启动仿真环境，第二句启动键盘控制节点。

```
$ ros2 launch learning_gazebo load_urdf_into_gazebo.launch.py
$ ros2 run teleop_twist_keyboard teleop_twist_keyboard 
```

![image-20220528151226864](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.4_Gazebo/image-20220528151226864.png)

<details class="attention" open="open" style="box-sizing: inherit; display: flow-root; overflow: visible; padding: 0px 0.6rem; background-color: var(--md-admonition-bg-color); border-width: 0px 0px 0px 0.2rem; border-style: solid; border-color: rgb(255, 145, 0); border-image: initial; border-radius: 0.1rem; box-shadow: var(--md-shadow-z1); color: rgba(0, 0, 0, 0.87); font-size: 0.64rem; margin: 1.5625em 0px; break-inside: avoid; font-family: Roboto, -apple-system, BlinkMacSystemFont, Helvetica, Arial, sans-serif; font-style: normal; font-variant-ligatures: normal; font-variant-caps: normal; font-weight: 400; letter-spacing: normal; orphans: 2; text-align: start; text-indent: 0px; text-transform: none; widows: 2; word-spacing: 0px; -webkit-text-stroke-width: 0px; white-space: normal; text-decoration-thickness: initial; text-decoration-style: initial; text-decoration-color: initial;"><summary style="box-sizing: border-box; cursor: pointer; display: block; min-height: 1rem; background-color: rgba(255, 145, 0, 0.1); border-top: none; border-right: none; border-bottom: none; border-left: 0.2rem none; border-image: initial; font-weight: 700; margin: 0px -0.6rem 0px -0.8rem; padding: 0.4rem 0.6rem 0.4rem 2.2rem; position: relative; border-top-left-radius: 0.1rem; border-top-right-radius: 0.1rem; -webkit-tap-highlight-color: transparent; outline: none;">Attention</summary><p style="box-sizing: border-box; margin-bottom: 0.6rem;">虚拟机中运行时需要关闭硬件加速：echo " export SVGA_VGPU10=0" &gt;&gt; ~/.bashrc</p></details>

通过键盘上的“i、j、，、l”几个按键，就可以控制机器人前后左右运动啦。

![image-20220528151237654](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.4_Gazebo/image-20220528151237654.png)

整个仿真有点像控制小海龟的过程，不过此时的机器人和仿真环境，已经比小海龟复杂很多了。

以上就是Gazebo机器人的仿真的基本流程。

### **Ignition：下一代Gazebo**

随着技术的进步，Gazebo仿真平台也在不断迭代，新一代的Gazebo命名为**Ignition**，从渲染效果和仿真流畅度上都有较大的变化，我们不妨也来试一下。

```
$ sudo apt install ros-humble-ros-ign 
$ ros2 launch ros_ign_gazebo_demos rgbd_camera_bridge.launch.py
```

运行成功后，会打开Ignition的仿真界面和Rviz上位机，我们可以看到RGBD相机仿真后发布的图像数据。

![image-20220528151350359](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.4_Gazebo/image-20220528151350359.png)

![image-20220528151358409](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.4_Gazebo/image-20220528151358409.png)

更多新版本仿真器的信息，大家也可以参考官方网站:

[www.ignitionrobotics.org/](https://book.guyuehome.com/ROS2/3.常用工具/3.4_Gazebo/www.ignitionrobotics.org/)

### **附录：机器人完整模型**

- learning_gazebo/urdf/mbot_gazebo.xacro

```
<?xml version="1.0"?>
<robot name="mbot" xmlns:xacro="http://www.ros.org/wiki/xacro">

    <xacro:include filename="$(find learning_gazebo)/urdf/mbot_base_gazebo.xacro" />

    <xacro:mbot_base_gazebo/>

</robot>
```

- learning_gazebo/urdf/mbot_base_gazebo.xacro

```
<?xml version="1.0"?>
<robot name="mbot" xmlns:xacro="http://www.ros.org/wiki/xacro">

    <!-- PROPERTY LIST -->
    <xacro:property name="M_PI" value="3.1415926"/>
    <xacro:property name="base_mass"   value="1" /> 
    <xacro:property name="base_radius" value="0.20"/>
    <xacro:property name="base_length" value="0.16"/>

    <xacro:property name="wheel_mass"   value="0.2" />
    <xacro:property name="wheel_radius" value="0.06"/>
    <xacro:property name="wheel_length" value="0.025"/>
    <xacro:property name="wheel_joint_y" value="0.19"/>
    <xacro:property name="wheel_joint_z" value="0.05"/>

    <xacro:property name="caster_mass"    value="0.2" /> 
    <xacro:property name="caster_radius"  value="0.015"/> <!-- wheel_radius - ( base_length/2 - wheel_joint_z) -->
    <xacro:property name="caster_joint_x" value="0.18"/>

    <!-- Defining the colors used in this robot -->
    <material name="yellow">
        <color rgba="1 0.4 0 1"/>
    </material>
    <material name="black">
        <color rgba="0 0 0 0.95"/>
    </material>
    <material name="gray">
        <color rgba="0.75 0.75 0.75 1"/>
    </material>

    <!-- Macro for inertia matrix -->
    <xacro:macro name="sphere_inertial_matrix" params="m r">
        <inertial>
            <mass value="${m}" />
            <inertia ixx="${2*m*r*r/5}" ixy="0" ixz="0"
                iyy="${2*m*r*r/5}" iyz="0" 
                izz="${2*m*r*r/5}" />
        </inertial>
    </xacro:macro>

    <xacro:macro name="cylinder_inertial_matrix" params="m r h">
        <inertial>
            <mass value="${m}" />
            <inertia ixx="${m*(3*r*r+h*h)/12}" ixy = "0" ixz = "0"
                iyy="${m*(3*r*r+h*h)/12}" iyz = "0"
                izz="${m*r*r/2}" /> 
        </inertial>
    </xacro:macro>

    <!-- Macro for robot wheel -->
    <xacro:macro name="wheel" params="prefix reflect">
        <joint name="${prefix}_wheel_joint" type="continuous">
            <origin xyz="0 ${reflect*wheel_joint_y} ${-wheel_joint_z}" rpy="0 0 0"/>
            <parent link="base_link"/>
            <child link="${prefix}_wheel_link"/>
            <axis xyz="0 1 0"/>
        </joint>

        <link name="${prefix}_wheel_link">
            <visual>
                <origin xyz="0 0 0" rpy="${M_PI/2} 0 0" />
                <geometry>
                    <cylinder radius="${wheel_radius}" length = "${wheel_length}"/>
                </geometry>
                <material name="gray" />
            </visual>
            <collision>
                <origin xyz="0 0 0" rpy="${M_PI/2} 0 0" />
                <geometry>
                    <cylinder radius="${wheel_radius}" length = "${wheel_length}"/>
                </geometry>
            </collision>
            <xacro:cylinder_inertial_matrix  m="${wheel_mass}" r="${wheel_radius}" h="${wheel_length}" />
        </link>

        <gazebo reference="${prefix}_wheel_link">
            <material>Gazebo/Gray</material>
        </gazebo>

        <!-- Transmission is important to link the joints and the controller -->
        <transmission name="${prefix}_wheel_joint_trans">
            <type>transmission_interface/SimpleTransmission</type>
            <joint name="${prefix}_wheel_joint" >
                <hardwareInterface>hardware_interface/VelocityJointInterface</hardwareInterface>
            </joint>
            <actuator name="${prefix}_wheel_joint_motor">
                <hardwareInterface>hardware_interface/VelocityJointInterface</hardwareInterface>
                <mechanicalReduction>1</mechanicalReduction>
            </actuator>
        </transmission>
    </xacro:macro>

    <!-- Macro for robot caster -->
    <xacro:macro name="caster" params="prefix reflect">
        <joint name="${prefix}_caster_joint" type="fixed">
            <origin xyz="${reflect*caster_joint_x} 0 ${-(base_length/2 + caster_radius)}" rpy="0 0 0"/>
            <parent link="base_link"/>
            <child link="${prefix}_caster_link"/>
        </joint>

        <link name="${prefix}_caster_link">
            <visual>
                <origin xyz="0 0 0" rpy="0 0 0"/>
                <geometry>
                    <sphere radius="${caster_radius}" />
                </geometry>
                <material name="black" />
            </visual>
            <collision>
                <origin xyz="0 0 0" rpy="0 0 0"/>
                <geometry>
                    <sphere radius="${caster_radius}" />
                </geometry>
            </collision>      
            <xacro:sphere_inertial_matrix  m="${caster_mass}" r="${caster_radius}" />
        </link>

        <gazebo reference="${prefix}_caster_link">
            <material>Gazebo/Black</material>
        </gazebo>
    </xacro:macro>

    <xacro:macro name="mbot_base_gazebo">
        <link name="base_footprint">
            <visual>
                <origin xyz="0 0 0" rpy="0 0 0" />
                <geometry>
                    <box size="0.001 0.001 0.001" />
                </geometry>
            </visual>
        </link>
        <gazebo reference="base_footprint">
            <turnGravityOff>false</turnGravityOff>
        </gazebo>

        <joint name="base_footprint_joint" type="fixed">
            <origin xyz="0 0 ${base_length/2 + caster_radius*2}" rpy="0 0 0" />        
            <parent link="base_footprint"/>
            <child link="base_link" />
        </joint>

        <link name="base_link">
            <visual>
                <origin xyz=" 0 0 0" rpy="0 0 0" />
                <geometry>
                    <cylinder length="${base_length}" radius="${base_radius}"/>
                </geometry>
                <material name="yellow" />
            </visual>
            <collision>
                <origin xyz=" 0 0 0" rpy="0 0 0" />
                <geometry>
                    <cylinder length="${base_length}" radius="${base_radius}"/>
                </geometry>
            </collision>   
            <xacro:cylinder_inertial_matrix  m="${base_mass}" r="${base_radius}" h="${base_length}" />
        </link>

        <gazebo reference="base_link">
            <material>Gazebo/Blue</material>
        </gazebo>

        <xacro:wheel prefix="left"  reflect="1"/>
        <xacro:wheel prefix="right" reflect="-1"/>

        <xacro:caster prefix="front" reflect="-1"/>
        <xacro:caster prefix="back"  reflect="1"/>

        <!-- controller -->
        <gazebo>
            <plugin name="differential_drive_controller" 
                    filename="libgazebo_ros_diff_drive.so">                
                  <update_rate>30</update_rate>
                  <left_joint>left_wheel_joint</left_joint>
                  <right_joint>right_wheel_joint</right_joint>
                  <wheel_separation>${wheel_joint_y*2}</wheel_separation>
                  <wheel_diameter>${2*wheel_radius}</wheel_diameter>
                  <max_wheel_torque>20</max_wheel_torque>
                  <max_wheel_acceleration>1.0</max_wheel_acceleration>
                  <command_topic>cmd_vel</command_topic>
                  <publish_odom>true</publish_odom>
                  <publish_odom_tf>true</publish_odom_tf>
                  <publish_wheel_tf>true</publish_wheel_tf>
                  <odometry_topic>odom</odometry_topic>
                  <odometry_frame>odom</odometry_frame>
                  <robot_base_frame>base_footprint</robot_base_frame>
                  <odometry_source>1</odometry_source>
            </plugin>
        </gazebo> 
    </xacro:macro>

</robot>
```

## 3.5 Rviz：三维可视化显示平台

大家有没有畅想过一个问题，机器人眼中的世界是什么样的呢？如何能够看到机器人摄像头拍摄到的图像？

这就涉及到可视化显示的范畴了，本讲我们介绍一位ROS中的重量级嘉宾——**Rviz**，一款**三维可视化显示**的神器。

### **Rviz三维可视化平台**

机器人开发过程中，各种各样的功能，如果我们只是从数据层面去做分析，很难快速理解数据的效果，比如给你一堆0到255的数字，问这幅图像描述的内容是什么？你肯定一脸懵。但如果我们把这些数字通过颜色渲染出来，岂不就一目了然么？

![image-20220528152054838](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.5_Rviz/image-20220528152054838.jpg)

![image-20220528152050544](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.5_Rviz/image-20220528152050544.jpg)

类似的场景还有很多，比如机器人模型，我们需要知道自己设计的模型长啥样，还有模型内部众多坐标系在运动过程中都在哪些位置。

再比如机械臂运动规划和移动机器人自主导航，我们希望可以看到机器人周边的环境、规划的路径，当然还有传感器的信息，摄像头、三维相机、激光雷达等等，数据是用来做计算的，可视化的效果才是给人看的。

所以，数据可视化可以大大提高开发效率，Rviz就是这样一款机器人开发过程中的数据可视化软件，机器人模型、传感器信息、环境信息等等，全都可以在这里搞定。

#### **Rviz介绍**

一句话说明Rviz的功能，只要有数据，它就可以可视化，只有我们想不到的，没有Rviz做不到的。

![image-20220528151929609](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.5_Rviz/image-20220528151929609.jpg)

Rviz的核心框架是基于**Qt可视化工具**打造的一个开放式平台，官方出厂就自带了很多机器人常用的可视化显示插件，只要我们按照ROS中的消息发布对应的话题，就可以看到图形化的效果了。如果我们对显示的效果不满意，或者想添加某些新的显示项，也可以在Rviz这个平台中，开发更多可视化效果，方便打造我们自己的上位机。

#### **运行方法**

启动一个终端，使用如下命令即可启动：

```
$ ros2 run rviz2 rviz2
```

![image-20220528152204601](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.5_Rviz/image-20220528152204601.jpg)

### **彩色相机仿真与可视化**

摄像头肯定是最为常用的一种传感器了，我们先来给机器人装上摄像头。

#### **仿真插件配置**

关于传感器的仿真，都需要使用Gazebo提供的插件，摄像头对应的插件叫做libgazebo_ros_camera.so，我们对照模型的代码给大家介绍这个插件的使用方法。

learning_gazebo/urdf/sensers/camera_gazebo.xacro

```
<gazebo reference="${prefix}_link">
    <sensor type="camera" name="camera_node">
        <update_rate>30.0</update_rate>
        <camera name="head">
            <horizontal_fov>1.3962634</horizontal_fov>
            <image>
                <width>1280</width>
                <height>720</height>
                <format>R8G8B8</format>
            </image>
            <clip>
                <near>0.02</near>
                <far>300</far>
            </clip>
            <noise>
                <type>gaussian</type>
                <mean>0.0</mean>
                <stddev>0.007</stddev>
            </noise>
        </camera>
        <plugin name="gazebo_camera" filename="libgazebo_ros_camera.so">
            <ros>
                <!-- <namespace>stereo</namespace> -->
                <remapping>~/image_raw:=image_raw</remapping>
                <remapping>~/camera_info:=camera_info</remapping>
            </ros>
            <camera_name>${prefix}</camera_name>
            <frame_name>${prefix}_link</frame_name>
            <hack_baseline>0.2</hack_baseline>
        </plugin>
    </sensor>
</gazebo>
```

主要配置项如下：

- <sensor>标签：描述传感器

> type：传感器类型，camera
>
> name：摄像头命名，自由设置

- <camera>标签：描述摄像头参数

> 分辨率，编码格式，图像范围，噪音参数等

- <plugin>标签：加载摄像头仿真插件

#### **运行仿真环境**

模型已经配置好啦，能不能把摄像头成功仿真出来，并且在Rviz中看到图像信息，我们拭目以待。

```
$ ros2 launch learning_gazebo load_mbot_camera_into_gazebo.launch.py
```

![image-20220528152414923](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.5_Rviz/image-20220528152414923.jpg)

可以使用命令行看下仿真出来的图像话题：

![image-20220528152456256](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.5_Rviz/image-20220528152456256.jpg)

#### **图像数据可视化**

我们使用Rviz可视化显示图像信息，先来启动Rviz：

```
$ ros2 run rviz2 rviz2
```

启动成功后，在左侧Displays窗口中点击“Add”，找到Image显示项，OK确认后就可以加入显示列表啦，然后配置好该显示项订阅的图像话题，就可以顺利看到机器人的摄像头图像啦。

![image-20220528152442483](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.5_Rviz/image-20220528152442483.jpg)

### **三维相机仿真与可视化**

二维摄像头不过瘾，想不想试试三维相机，比如我们常用的Kinect体感传感器，或者Intel的Realsense，可以获取外部环境的点云数据。这种相机的价格比usb摄像头可贵不少，不过我们也可以通过仿真，一分钱不用，就可以玩起来。

#### **仿真插件配置**

三维相机使用的Gazebo插件也是libgazebo_ros_camera.so，配置方法如下：

learning_gazebo/urdf/sensers/kinect_gazebo.xacro

```
<gazebo reference="${prefix}_link">
    <sensor type="depth" name="${prefix}">
        <always_on>true</always_on>
        <update_rate>15.0</update_rate>
        <pose>0 0 0 0 0 0</pose>
        <camera name="kinect">
            <horizontal_fov>${60.0*M_PI/180.0}</horizontal_fov>
            <image>
                <format>R8G8B8</format>
                <width>640</width>
                <height>480</height>
            </image>
            <clip>
                <near>0.05</near>
                <far>8.0</far>
            </clip>
        </camera>
        <plugin name="${prefix}_controller" filename="libgazebo_ros_camera.so">
            <ros>
                <!-- <namespace>${prefix}</namespace> -->
                <remapping>${prefix}/image_raw:=rgb/image_raw</remapping>
                <remapping>${prefix}/image_depth:=depth/image_raw</remapping>
                <remapping>${prefix}/camera_info:=rgb/camera_info</remapping>
                <remapping>${prefix}/camera_info_depth:=depth/camera_info</remapping>
                <remapping>${prefix}/points:=depth/points</remapping>
            </ros>
            <camera_name>${prefix}</camera_name>
            <frame_name>${prefix}_frame_optical</frame_name>
            <hack_baseline>0.07</hack_baseline>
            <min_depth>0.001</min_depth>
            <max_depth>300.0</max_depth>
        </plugin>
    </sensor>
</gazebo>
```

#### **运行仿真环境**

使用如下命令启动仿真环境：

```
$ ros2 launch learning_gazebo load_mbot_rgbd_into_gazebo.launch.py
```

![image-20220528152559248](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.5_Rviz/image-20220528152559248.jpg)

启动成功后，可以看下当前的话题列表，已经产生了三维相机的相关话题。

![image-20220528152611362](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.5_Rviz/image-20220528152611362.jpg)

#### **点云数据可视化**

运行Rviz：

```
$ ros2 run rviz2 rviz2
```

同样的流程，点击Add，添加PointCloud2，设置订阅的点云话题，还要配置Rviz的参考系是odom，就可以看到点云数据啦，每一个点都是由xyz位置和rgb颜色组成。

![image-20220528152552742](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.5_Rviz/image-20220528152552742.jpg)

### **激光雷达仿真与可视化**

除了摄像头和三维相机，激光雷达也是很多移动机器人常备的传感器，包括自动驾驶汽车，我们也来试一试。

#### **仿真插件配置**

雷达使用的Gazebo插件是libgazebo_ros_ray_sensor.so，配置方法如下：

learning_gazebo/urdf/sensers/lidar_gazebo.xacro

```
<gazebo reference="${prefix}_link">
    <sensor type="ray" name="rplidar">
        <update_rate>20</update_rate>
        <ray>
            <scan>
              <horizontal>
                <samples>360</samples>
                <resolution>1</resolution>
                <min_angle>-3</min_angle>
                <max_angle>3</max_angle>
              </horizontal>
            </scan>
            <range>
              <min>0.10</min>
              <max>30.0</max>
              <resolution>0.01</resolution>
            </range>
            <noise>
              <type>gaussian</type>
              <mean>0.0</mean>
              <stddev>0.01</stddev>
            </noise>
        </ray>
        <plugin name="gazebo_rplidar" filename="libgazebo_ros_ray_sensor.so">
      <ros>
    <namespace>/</namespace>
    <remapping>~/out:=scan</remapping>
      </ros>
      <output_type>sensor_msgs/LaserScan</output_type>
        </plugin>
    </sensor>
</gazebo>
```

#### **运行仿真环境**

使用如下命令启动仿真环境：

```
$ ros2 launch learning_gazebo load_mbot_laser_into_gazebo.launch.py
```

![image-20220528152754541](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.5_Rviz/image-20220528152754541.jpg)

在话题列表中也可以看到激光雷达啦。

![image-20220528152810332](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.5_Rviz/image-20220528152810332.jpg)

#### **点云数据可视化**

启动Rviz：

```
$ ros2 run rviz2 rviz2
```

点击Add，选择Laserscan，然后配置订阅的话题名，rviz的固定坐标系依然是odom，此时就可以看到激光点啦。

![image-20220528152821691](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.5_Rviz/image-20220528152821691.jpg)

### **Rviz vs Gazebo**

好啦，通过这几个案例，相信大家对Rviz可视化平台的使用流程已经非常熟悉了，也了解了常用传感器的仿真方法。

讲到这里，Gazebo和Rviz这两个软件的具体功能，大家是不是会有一些混淆。

![image-20220528152913715](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.5_Rviz/image-20220528152913715.jpg)

我们再来强调下：

- Gazebo是**仿真平台**，核心功能是**创造数据**，我们没有机器人或者传感器，它可以帮我们做一个虚拟的；
- Rviz是**可视化平台**，核心功能是**显示数据**，如果没有数据，它也巧妇难为无米之炊。

所以在很多时候，我们使用Gazebo做机器人仿真的时候，也会启动Rviz来显示仿真环境的信息，如果自己手上有真实机器人的话，Gazebo就用不到了，不过还是会用Rviz显示真实机器人传感器的信息。

## 3.6  RQT：模块化可视化工具

ROS中的Rviz功能已经很强大了，不过有些场景下，我们可能更需要一些简单的模块化的可视化工具，比如只显示一个摄像头的图像，使用Rviz的话，难免会觉得操作有点麻烦。

此时，我们就会用到ROS提供的另外一种模块化可视化工具——**rqt**。

### **rqt介绍**

正如RQT的命名，它和Rviz一样，也是基于QT可视化工具开发而来，在使用前，我们需要通过这样一句指令进行安装，然后就可以通过rqt这个命令启动使用了。

```
$ sudo apt install ros-humble-rqt
$ rqt
```

![image-20220528153119321](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.6_Rqt/image-20220528153119321.png)

类似这个界面一样，里边可以加载很多小模块，每个模块都可以实现一个具体的小功能，一些常用的功能如下：

### **日志显示**

![image-20220528153332794](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.6_Rqt/image-20220528153332794.png)

### **图像显示**

![image-20220528153354370](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.6_Rqt/image-20220528153354370.png)

### **发布话题数据/调用服务请求**

![image-20220528153406339](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.6_Rqt/image-20220528153406339.png)

### **绘制数据曲线**

![image-20220528153414784](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.6_Rqt/image-20220528153414784.png)

### **数据包管理**

![image-20220528153423185](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.6_Rqt/image-20220528153423185.png)

### **节点可视化**

![image-20220528153433016](https://book.guyuehome.com/ROS2/3.%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/image/3.6_Rqt/image-20220528153433016.png)

