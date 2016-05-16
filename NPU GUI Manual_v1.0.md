##**瑞思机器人 NPU 软件使用手册**


##简介
该软件是一款用于对NPU(Navigation Processing Unit)进行控制的上位机。通过它，使用者可以轻松地操作NPU模块中的所有功能。该软件主要分为两种控制模式：建图模式和导航模式。它是基于C#实现的，并且提供了完整的API，供windows用户来实现自定义的多样式的控制方式。

##准备工作
1. 确定NPU模块与上位机电脑的网络连在同一`局域网`内；
2. 确定NPU模块当前的`IP地址`；
3. 启动NPU上位机软件；
4. 建图开始前要提前人工规划好机器人见图时所行进的路线，推荐点到点之间的单向建图，不推荐往返路线建图；
5. 将机器人置于建图或导航的起始点，机器人的正向置于`建地图时的起始朝向`【建议平行于道路正方向】；

##初始化
Step 1: 在Server IP里填写NPU模块的IP地址；

Step 2: 点击Init 按钮，完成NPU模块与上位机软件的初始化连接：

若Is Inited前面出现对号，则说明连接成功；

若界面弹出“`服务器连接失败`”的错误提示，则需要重新检查是否位于同一局域网中以及NPU模块的IP地址是否正确；
![Initial phase](https://raw.githubusercontent.com/Moyago/Mdphotos/master/init.png)

##建图模式

M_Step 3: 点击map 按钮，启动建图模式；

M_Step 4: 点击Start Get Map 按钮，获取当前所建地图；

M_Step 5: 人工推动【推荐】或遥控机器人按照所设定路线进行建图；

M_Step 6: 当机器人行进到建图终点时，从上位机界面来判断本次建图是否成功：

若地图与当前场景同一水平的二维截面相符，则认为建图成功，并点击Save Map 按钮保存地图；

若地图出现明显的边线重叠、覆盖等与当前场景不符的情况时，则认为建图失败，并将机器人重置回建图起点，再点击Reset Map 按钮，重新进行建图；
![Mapping phase](https://raw.githubusercontent.com/Moyago/Mdphotos/master/map.png)

##导航模式

N_Step 3: 点击navi 按钮，启动导航模式；

N_Step 4: 点击Start Get Map 按钮i，获取当前环境地图；

N_Step 5: 将机器人旋转至`建图起始时的`朝向，并在地图中选择机器人当前所在位置，用鼠标中键点击，该点坐标自动读取进Initial Pose 文本框中，并点击Set Initial Pose 按钮， 机器人初始位置将被设定；

N_Step 6: 在地图中选择机器人所要到达的目的点，用鼠标左键/右键点击，该点坐标自动读取进Home Pose/Goal Pose 文本框中，并点击Set Home Pose/Set Goal Pose 按钮，机器人目的点被设定；（Home 和 Goal 是两个目的点的不同叫法，无本质区别）

N_Step 7: 点击Go Home/Go Goal 按钮，机器人开始执行导航。

N_Step 8: 在导航过程中，如果中途需要机器人停止行进，则可以点击Stop 按钮来终止导航；
![Navigation phase](https://raw.githubusercontent.com/Moyago/Mdphotos/master/navi.png)

##数据监控

1. 指令速度 Cmd Vel : 用于监控NPU模块向下位机发送的实时的控制速度；
2. 实际速度 Act Vel : 用于监控从码盘中获取的机器人所执行的实际速度；
3. 实际位置 Act Pose : 用于监控NPU模块对机器人的坐标定位；
4. 实际码盘 Act Encoder : 用于监控从码盘中获取的左右码盘数据；
5. 地图 Map : 在建图过程中每2秒更新一次地图数据；

##参数设置

对底盘的重要参数进行设定：轮距（WheelSpan）、轮半径（WheelRadius）和码盘线数（EncLineNum）；

##其他说明

当机器人既不执行建图也不执行导航时，点击 Kill All 按钮退出所有模式。


>##联系我们
>邮箱：npu@wizrobo.com
>电话：+86 0755-28348179
>地址：深圳市龙岗区梅坂大道与雅宝路交汇处星河world


















