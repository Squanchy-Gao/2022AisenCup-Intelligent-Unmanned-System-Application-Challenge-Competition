fang_ws中的功能包详解

1、fang_pack/bay_pack

launch：存放调用其他功能包launch的launch文件；

map：存放二维栅格地图；

src：存放完成主体任务的cpp文件

2、pointcloud_to_laserscan

下载的官方功能包，功能是将三维点云转成二维点云，用于二维激光slam算法（gmapping、hector）。

3、rslidar_sdk

下载的雷达驱动功能包，功能是实现该型号雷达的通讯。

4、serial

下载的机器人串口功能包，用来和stm32通讯。

5、turn_on_wheeltec_robot

下载的机器人底层驱动功能包，启动底盘。

