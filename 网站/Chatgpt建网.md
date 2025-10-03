# 2024最新：GPT+GPTs+MJ+Claude3程序搭建

 本期教程搭建的程序集齐了市场上超火的AI功能 

1.GPT-3.5

2.GPT-4.0 ( 最新版 )

3.GPTs ( 联网、数据分析、文生图等超多插件功能)

4.Claude-3 ( sonnet、opus 2个版本都有 ) 

5.Midjourney 超强Ai绘图

6.DALL-E 绘图

6.suno 音乐模型（创作歌曲）



  

 准备 

1.云服务器

2.支持GPT+GPTs+MJ+Claude3的key密钥

3.资料包

 1.云服务器 

因内地服务器备案流程复杂，这里选择无需备案的香港服务器

 推荐：香草云，性价比高，安全稳定，本人常用 

网址：[https://www.xiangcaoyun.com/](https://www.xiangcaoyun.com/?ie607f6)

香港1核2g即可 注意：购买云服务器，一定要选择CentOS系统，版本选择默认的就行

![image.png](http://qxmapdepot.xiaoq11.cn/picture/1711735531014-8049ec99-1d30-4355-add5-a2915d368ac3.png)



![img](http://qxmapdepot.xiaoq11.cn/picture/1703594766130-d124e5a0-12ff-4c95-981a-43c7ed7c22d7.png)



![img](http://qxmapdepot.xiaoq11.cn/picture/1703594797295-afeabf8c-56a2-42bb-a33f-5b1cecbce96b.png)





 2.支持ChatGPT+Midjourney的服务的秘钥 

中转key获取网站：[https://openai-hk.com/](https://openai-hk.com/?i=1088)

如果打不开，可以试试下面的备用的 [https://tw.openai-hk.com/](https://tw.openai-hk.com/?i=1088) [https://open-hk.com/](https://open-hk.com/?i=1088)

![img](http://qxmapdepot.xiaoq11.cn/picture/1703595005940-98279bbf-7134-4913-b5ba-07291acb0b61.png)



![img](http://qxmapdepot.xiaoq11.cn/picture/1703595012116-a649e0a3-e741-4e96-a41e-7055a6bc34af.png)



![img](http://qxmapdepot.xiaoq11.cn/picture/1703595018574-17e5bb76-65b7-4d75-8c5b-1eebcb6385f0.png)



 3.准备的资料 



 安装FinalShell软件 



![image.png](http://qxmapdepot.xiaoq11.cn/picture/1712757342106-40851ad0-221a-41fa-8762-8cb7b92f671c.png)



下载链接：https://www.hostbuf.com/t/988.html

 资料包 

![image.png](http://qxmapdepot.xiaoq11.cn/picture/1712757178706-7edc58a9-365c-4729-b7bd-dca71b808b44.png)



下载链接：https://share.weiyun.com/rZy0yeND



将docker-compose.yml用记事本（其他编辑软件都可）打开，需要修改4个值，如下图框中的4处

![image.png](http://qxmapdepot.xiaoq11.cn/picture/1712757527588-6b499a4d-a245-4d47-8344-ba8acffc86a4.png)



修改好后，ctrl+s保存即可



 开始搭建 



 1. 打开软件，点击箭头所示按钮 

![img](http://qxmapdepot.xiaoq11.cn/picture/1703595104831-5b5a6064-4c02-46e0-b7e2-3277316a860b.png)



 2. 会跳出个窗口，接着点击箭头所示按钮，点击SSH链接 

![img](http://qxmapdepot.xiaoq11.cn/picture/1703595104988-678a73e3-6a85-4e9a-987c-f2ecffd37eba.png)

 3. 把红框里的内容填进去 

![img](http://qxmapdepot.xiaoq11.cn/picture/1703595104971-27c710dc-67b8-4d22-a939-9f1b453694a0.png)



 4. 填完后，这里会记录，双击打开它 

![img](http://qxmapdepot.xiaoq11.cn/picture/1703595105140-e8a27235-445a-4be8-9802-d16639001738.png)



 5. 即可链接成功 

![image.png](http://qxmapdepot.xiaoq11.cn/picture/1703596120452-61d4e4dc-7db1-4e5c-8f57-a4fe8f22de64.png)



![img](http://qxmapdepot.xiaoq11.cn/picture/1703595104942-115c1a4f-2ae2-4085-86db-8a5c25c205ab.png)



![(http://qxmapdepot.xiaoq11.cn/picture/1711739226294-3a3b5154-0e06-4e81-902e-562cd6df2253.png)

![image.png](http://qxmapdepot.xiaoq11.cn/picture/1711739226294-3a3b5154-0e06-4e81-902e-562cd6df2253.png)



 6.安装docker 

```bash
curl -fsSL https://get.docker.com -o get-docker.sh
```

如果docker安装失败，可以看这个教程：https://www.yuque.com/zeejk/dvbgxk/vdu2br1ia3e6yl3y?singleDoc# 

 7. 列出下载的内容 

```bash
ls
```

![img](http://qxmapdepot.xiaoq11.cn/picture/1712376134607-ac79c804-99f5-4eb2-80d9-86af37374988.png)



有这个说明下载成功



 8.安装docker，这一步安装过程有点久，5-20分钟左右 



![img](http://qxmapdepot.xiaoq11.cn/picture/1712376135858-39fd5f5c-7701-41f6-9e67-e6aaa7ecc385.png)



如上图所示，即说明安装成功



 8.1 运行Docker服务 

```bash
systemctl start docker
```



 9. 检查docker服务运行状态 

```bash
systemctl status docker
```

![img](http://qxmapdepot.xiaoq11.cn/picture/1712376135678-570a905e-87af-4665-8b1d-ca4923371989.png)



当出现active (running)… 即说明安装成功



 9.1执行下面的指令，防止服务器重启打不开网页 

```bash
systemctl enable docker
```

到这一步，Docker即可安装成功

 9.2安装Ai程序 

```bash
 sh ./deploy.sh
```

出现下图所示，说明在自动安装程序



![image.png](http://qxmapdepot.xiaoq11.cn/picture/1712376672544-21e7c10f-3529-4a15-8ac4-f69a1fca9372.png)



出现这个，说明程序已经安装完成



![image.png](http://qxmapdepot.xiaoq11.cn/picture/1712376866166-35584133-e25a-45aa-9cfb-9ef2a46f62e4.png)





 绑定域名 

域名购买网站：

西部数码：https://www.west.cn/