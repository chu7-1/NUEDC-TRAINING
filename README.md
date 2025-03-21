# 未命名组备赛规划

## 一.选做方向，题目

1.方向：控制类方向

2.题目：2021年电赛F题（主）		2022年电赛C题（副）

3.题目分析：（由于时间较赶，这里仅对主方向被选题进行分析）

​	a.车辆大小25X25X20（单位:cm）(车辆种类不限)﻿（暂定三轮小车平台）

​	b.装载药品检测(200g)(需要检测重力)以确定是否已经装载药品﻿，装载药品后反馈相应信号

​	c.视觉识别：需要视觉模块正确识别数字，以便反馈相应信号﻿

​	d.寻迹路线：提前规划好小车需要行走的路线，由pid控制(速度环)小车直行，红外寻迹模块进行扫描，并到指定方向进行转向﻿（时间允许情况下尝试角度环+陀螺仪）

​	e.到达病房后，红灯亮起，取下药品后，红灯熄灭

​	f.小车返回原点，然后绿亮起

（注：单程时长不超过20s，需要对速度有所限制。)

## 二.备赛学习规划

a.小组信息及分工

​	成员1： （视觉方向）

​	技术栈：了解基于Arduino框架的ESP32开发版的使用，电路图的基本绘制

​	成员2:    （硬件方向）

​	技术栈：会stm32（f103C8t6）的基本使用，开发，电路图的基本绘制

​	成员3：  （软件方向）

​	技术栈：会一点ESP32，会一点stm32，电路图的基本绘制

b.方向选择

​	初步选择主方向为控制方向

c.方向所需技术栈

​	--stm32（暂定f103c8t6，后续尝试转MSPM0G3507）

​		a.进行HAL库的学习

​		b.进阶知识的学习（PID算法，非阻塞式程序）

​		c.常用模块的库函数搭建（MPU6050,HC-SR04,OLED）

​		d.为迁移到MSPM0G3507做准备

​	--电路板绘制（决定对功能板进行堆叠化设置）

​		a.第一层（供电层）：负责提供12V电源以及稳压，电压的转换及输出

​		b.第二层（驱动层）：负责电机部分的驱动

​		c.第三层（逻辑层）：负责系统板以及外设的连接

​	--openmv视觉学习：能跑简单的例程，满足所需就好

​	--SolidWorks3D建模：实现简单3D模型的绘制（循迹模块支架，药品放置栏）

​	（注：本阶段学习以赛题为导向，涵盖赛题所需的技术栈。）

## 三.设备清单

a.设备清单

| 模块                   | 数量 | 单位 | 功用                       | 备注                       |
| ---------------------- | ---- | ---- | -------------------------- | -------------------------- |
| 18650电池              | 9    | 节   | 3/4节为为一组，提供12V电源 |                            |
| 电池盒（18650）        | 2    | 个   | N/A                        |                            |
| 充电器（18650）        | 2    | 个   | N/A                        | 充电器暂定1大1小           |
| MP1584EN               | 2    | 个   | 为单片机提供3.3V电源       | 采购回来后必须测量输出电压 |
| LM2596（S）（可调）    | 2    | 个   | 提供5V/3.3V电源            | 采购回来后必须测量输出电压 |
| TB6612带稳压           | 2    | 个   | 驱动电机                   |                            |
| stm32（f103c8t6）      | 2    | 个   | N/A                        |                            |
| MSPM0G3507             | 1    | 个   | N/A                        |                            |
| TCRT5000循迹模块       | 5    | 个   | 红外循迹                   |                            |
| HC-SR04超声波模块      | 2    | 个   | 超声波测距/避障            |                            |
| jy901陀螺仪模块        | 1    | 个   | 测量角度/加速度等          |                            |
| MPU6050/6500（一个库） | 1    | 个   | 测量角度/加速度等          |                            |
| 310编码电机小车平台    | 2    | 套   | 整个项目搭建的平台         | 现有1套，后续再收1套       |

b.工具

| 工具               | 数量 | 单位 | 备注                              |
| ------------------ | ---- | ---- | --------------------------------- |
| 螺丝刀和批头       | 3    | 套   |                                   |
| 2.54mm排针         | 100  | 针   |                                   |
| 2.54mm排母（常用） | 10   | 个   | 一种至少预留十个                  |
| XH2.54端子         | 5    | 个   | 主要是520编码电机接口             |
| PH2.0端子          | 5    | 个   | 一种预留5个，用于功能板之间的连接 |
| M3螺柱，螺母       | 5    | 个   | 买一盒，常用的一种有5个           |
| 焊台               | 0    | 台   | 实验室有                          |
| 风枪               | 0    | 台   | 实验室有                          |
| 热熔胶枪，胶棒     | 1    | 个   |                                   |
| 封装箱             | 2    | 个   |                                   |
| 水口钳             | 1    | 个   |                                   |

c.软件工具链

​	keil5，stm32cubeMX，立创EDA，SolidWorks，OpenMV IDE

## 四.学习计划

1.3.17-3.28模块学习时间﻿

​	1.要求pid速度环，位置环，转向环学习完成(提交串口波形等)﻿

​	2.视觉识别 要求识别基本识别1-10的数字以及字母﻿（源代码，效果图）

​	3.通信 要求OpenMV模块能与stm32主控能够通信﻿（源代码）

​	4.超声波测距 要求超声波模块能够测试距离 并在OLED 上显示﻿（源代码，效果图、视频）

​	5.陀螺仪库函数搭建以及陀螺仪的使用（提交源代码，OLED测量角度，加速度等）

​	（注：以上任务不分先后，同期执行，同期结束。）

3.29-4.11任务全面制作时期﻿

​	进行小车全面制作，实现基本功能。



​	预计3.28结束pid（位置环，速度环，转向环），openmv（stm32H750）的学习；

​	3.28-4.11为项目一的制作期，截至4.11基本要求小车稳定行走，视觉识别数字，抵达指定方向后反馈相应信号，并能返回原点



