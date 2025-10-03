# [一键安装ROS2](https://fishros.com/d2lros2/#/humble/chapt1/get_started/3.动手安装ROS2?id=_1一键安装ros2)

首先启动虚拟机或者启动双系统中的ubuntu，打开终端，输入下面的指令。

```
 wget http://fishros.com/install -O fishros && . fishros
 sudo apt update
 sudo apt install python3-argcomplete -y
 sudo apt remove ros-humble-*
 sudo apt autoremove
 cd /opt/ros/humble/
 ls
```

# 配置下载

```
 sudo apt install gazebo
 sudo apt-get install ros-humble-gazebo-plugins
 sudo apt install ros-humble-gazebo-*
 sudo apt install ros-humble-rqt-tf-tree
 sudo apt install ros-$ROS_DISTRO-ros2-controllers
 sudo apt install ros-$ROS_DISTRO-xacro
 sudo apt install ros-$ROS_DISTRO-ros2-control
 sudo apt-get install ros-humble-joint-state-publisher
 sudo apt install jupyter-notebook
 sudo apt install ros-$ROS_DISTRO-slam-toolbox
 sudo apt install ros-$ROS_DISTRO-nav2-map-server
 sudo apt install ros-$ROS_DISTRO-navigation2
 sudo apt install ros-$ROS_DISTRO-nav2-bringup
 sudo apt install ros-humble-nav2-map-server
 sudo apt install ros-$ROS_DISTRO-tf-transformations
 sudo pip3 install transforms3d
 sudo apt install python3-pip -y
 pip3 install espeakng
 sudo apt install espeak-ng
 sudo apt install ros-$ROS_DISTRO-pluginlib -y
```

 

 

# 常用指令

```
 colcon build
 source install/setup.bash
 ros2 run teleop_twist_keyboard teleop_twist_keyboard
 ros2 launch slam_toolbox online_async_launch.py use_sim_time:=True
 ros2 run nav2_map_server map_saver_cli -f room
 cp /opt/ros/$ROS_DISTRO/share/nav2_bringup/params/nav2_params.yaml
```

 

 

# VSCODE配置

> code ./在vscode中打开当前文件夹。

## **Python**

![image-20210909005232983](http://qxmapdepot.xiaoq11.cn/picture/image-20210909005232983.png)

## **C++**

![image-20210909005135905](http://qxmapdepot.xiaoq11.cn/picture/image-20210909005135905.png)

## 汉化插件

![image-20210720135816630](http://qxmapdepot.xiaoq11.cn/picture/image-20210720135816630.png)

## Fitten

![img](http://qxmapdepot.xiaoq11.cn/picture/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE-2024-12-25-105802.png)

## Codesnap

![img](http://qxmapdepot.xiaoq11.cn/picture/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE-2024-12-25-110240-e1735199422463.png)

## ROS

![img](http://qxmapdepot.xiaoq11.cn/picture/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE-2024-12-25-110453.png)

## MSG

![img](http://qxmapdepot.xiaoq11.cn/picture/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE-2024-12-25-110806-e1735199461593.png)

## URDF

![img](http://qxmapdepot.xiaoq11.cn/picture/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE-2024-12-25-110907-e1735199474971.png)

## C++路径配置

> /opt/ros/ros版本/**

![img](http://qxmapdepot.xiaoq11.cn/picture/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE-2024-12-25-111624.png)![img](http://qxmapdepot.xiaoq11.cn/picture/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE-2024-12-25-111707-e1735097036643.png)

 