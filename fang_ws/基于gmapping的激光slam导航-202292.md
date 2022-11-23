# 基于gmapping的激光slam导航-2022/9/2

### 1、概述

本文内容为，使用wheeltec淘宝店旗下（独立悬挂常规版）四轮两驱差速机器人，进行建图与自主导航的使用经验。

机器人本身自带stm32底盘及配套程序，郭同学后续针对底盘进行了（增加巡航模式、蓝牙模式等修改，详见说明文档"版本修改.txt"），本人和郭同学在以上基础上对该产品进行二次开发，实现了该机器人在室内的建图和自主导航。

### 2、硬件说明

①wheeltec四轮两驱差速独立悬挂常规版机器人（含stm32、底盘）

②工控机（酷睿i7-10710U；六核十二线程；32G内存＋512G固态硬盘）

③激光雷达（速腾聚创 RS-LiDAR-16）

④航模遥控器（wheeltec HOTRC）

⑤路由器（水星 百兆端口）

⑥24v锂电池

⑦杂项（降压模块、一分三插头、魔术贴、绝缘束带、亚克力板、上层铝合金板等）

### 3、算法框架

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220902153118436.png" alt="image-20220902153118436" style="zoom:150%;" />

### 主要功能包如下：

#### ①bay_pack

该功能包的作用是实现通过若干个launch文件集成并调用其他功能包，同时也包含了param参数文件夹和map文件夹等。

#### ②pointcloud_to_laserscan

该功能包的作用是实现激光三维点云地图转成二位栅格地图，从github克隆下来，功能包内无需任何变动，调用时在bay_pack中对应的launch文件中修改参数。

#### ③rslidar_sdk

该功能包是激光雷达的软件驱动，从github官方账号下载下来后需要在该功能包下修改参数，详见功能包内含的官方说明文档，在bay_pack中调用时直接调用start.launch。

#### ④turn_on_wheeltec_robot

该功能包是wheeltec自带的功能包，包含了机器人底盘的驱动，urdf模型，以及大量的样板示例（包括gmapping、hector_map、karto_slam等建图算法和自主导航算法的示例等）。在本算法框架中，建图部分只使用了该功能包中的turn_on_wheeltec_robot.launch(修改后)文件，导航部分借鉴了该功能包中的示例。

#### ⑤wheeltec_robot_rc

该功能包的作用是使用键盘远程遥控机器人，实际情况中，使用航模遥控（直接与底盘传递信号）替代了，所以该功能包并未调用，读者可以根据需要自行研究。

### 4、实际效果

二楼：

![2楼](C:\Users\Administrator\Desktop\2022物联网＋比赛（华为杯）\map\2楼.png)

七楼：![7楼](C:\Users\Administrator\Desktop\2022物联网＋比赛（华为杯）\map\7楼.png)









