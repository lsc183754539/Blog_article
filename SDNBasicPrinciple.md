---
title: SDN笔记2——基本原理
date: 2020-04-10 12:07:26
tags: [SDN,概述,笔记 ]
categories: [SDN ]
---
## 软件定义网络的基本架构-ONF定义的三层架构

### ONF定义的基于OpenFlow的三层架构

#### 技术特点

##### 技术架构
* 转发与控制分离
* 转发面进行了标准化

##### 优点
* 流量调度
* 开放生态链
<!--more-->
### IETF提出的技术架构

#### 主要思想

##### 技术架构
* 开放现有网络设备的能力
* 标准化开放的API
<!--moe-->
##### 优点
* 充分利用了现有的网络设备和路由协议
* 快速实现

### NICRA（被VM收购）提出的Overlay技术架构

#### 技术特点

##### 技术架构
* 网络边缘软件化
* Overlay技术

##### 优点
* 与物理网络解耦
* 部署非常灵活

### ETSI的NFV技术

#### 运营商网络

##### 技术架构
* NFV与SDN互补
* 本质有很大不同

##### 不能算是SDN架构

## ONF定义的SDN基本架构

### 基本架构自下而上分为：转发层、控制层、应用层
* 转发层：一种新型网络创新架构，实现了网络设备控制与转发的分离
* 控制层：网络虚拟化的一种实现方式，核心技术为OpenFlow
* 应用层：实现了网络流量的灵活控制，使网络作为管道变得更加智能。

### 四个平面
![四个平面](https://imgkr.cn-bj.ufileos.com/a3646d64-2ae1-400e-8768-d30b03fd31d6.png)

#### 管理平面
* 负责静态的工作：网元初始化配置、指定控制器、定义控制器及应用的控制范围。

#### 应用平面
* SDN应用逻辑与北向接口（NBI）驱动
* 通过北向接口与SDN控制器交互

##### 应用逻辑方面
* 应用交付能力（负载均衡、访问控制、应用加速）

#### 控制平面

##### 三个部分
* 北向接口（NBI）代理
* SDN控制逻辑（ControlLogic）
* 控制数据平面接口驱动（CDPI Driver）

##### 两个任务
* 将SDN应用层请求转换到SDN Datapath
* 为SDN应用提供底层网络的抽象模型（状态或事件）

##### 关键技术
* 控制器，网络操作系统（NOS）或网络控制器（开源SDN控制器有NOX、POX、FloodLight、RYU、OpenDayLight、ONOS等）

#### 数据平面

##### 若干网元（NetWork Element）：包含一个或多个SDN数据路径（SDN Datapath）

###### SDN datapath：
* 逻辑上的网络设备，负责转发和处理数据
* 一个SDN Datapath包含控制数据平面接口表和处理功能

##### 关键技术
* 对数据面进行抽象建模
![](https://imgkr.cn-bj.ufileos.com/bb65dbe4-2607-4519-ad5d-675e64c7b718.png)


### 两大接口

#### 南向接口
* 控制平面和数据平面之间的接口（CDPI）
* 功能：转发行为控制、设备性能查询、统计报告、时间通知等
* ONF架构特点：标准化的南向接口协议（OpenFlow），不依赖于底层具体的厂商的交换设备。

##### 南向接口的关键技术
* 转发面开放协议（南向接口协议）：允许控制器控制交换机的配置以及相关转发行为。![](https://imgkr.cn-bj.ufileos.com/014b28ea-16e2-4328-9ce6-11e8fd330a59.png)

#### 北向接口
* 应用平面与控制平面之间的接口（NBI），向应用层提供抽象的网络视图，使应用能直接控制网络的行为。
* 开放的、与厂商无关的接口

##### 北向接口的关键技术
* SDN北向接口设计：控制器将网络能力封装后开放接口，提供上层业务调用。
* REST API成为SDN北向接口的主流设计
* 交换机状态采集、静态流表推送、防火墙策略等多种类型的接口。![](https://imgkr.cn-bj.ufileos.com/7da0ee38-2a98-4e4f-be2b-7e9cf29bb1c9.png)

## SDN网络核心思想
* 解耦
* 抽象
* 可编程

### 解耦
* 将控制平面和数据平面分离：解决两层在物理上紧耦合导致的问题
* 解耦后，控制平面负责上层的控制决策，数据平面负责数据的交换转发，双方需遵行开放接口进行通信
* 传统网络![传统网络](https://imgkr.cn-bj.ufileos.com/fbcbcd82-b612-468a-8b71-a4206202d97d.png)
* SDN网络![SDN网络](https://imgkr.cn-bj.ufileos.com/4ca592e8-9807-449f-8662-71aafeb0ddd7.png)
* 解耦合带来的问题  
    * 控制平面的服务能力成为网络性能的瓶颈
    * 多控制器如何交互路由信息，保持分布式节点状态的一致性
    * 控制平面的响应延迟。导致的数据平面可用性问题

### 抽象
![](https://imgkr.cn-bj.ufileos.com/cacd7127-5dab-4478-a19a-6dcd223dc244.png)
* 转发抽象![转发抽象](https://imgkr.cn-bj.ufileos.com/e382c7c0-835e-434d-b17d-b81be4caf654.png)
* 分布状态抽象![分布状态抽象](https://imgkr.cn-bj.ufileos.com/211647c9-a1c3-42bb-b3ed-adadc5c7ccf5.png)
* 配置抽象：网络行为的表达通过编程语言实现，基于简化抽象模型，将抽象配置映射为物理配置（命令行、网关协议接口、控制器提供的API）
* Overlay架构上的抽象![Overlay架构上的抽象](https://imgkr.cn-bj.ufileos.com/fdaeedcd-6e65-4fae-b04a-13e07ef29c01.png)


### 可编程
* SDN在数据平面与控制平面解耦后提供了开放的可编程接口
* 传统网络管理接口：命令行、网管协议、脚本语言等初级管理方式
* 网络管理员需要基于整个网络的更高级的编程方式
* 网络可编程：主动网络（开放网络节点的编程接口、用户数据上根据用户需求执行相应计算）、4D架构（数据平面、发现平面、扩展平面、决策平面）
* SDN的可编程接口![SDN的可编程接口](https://imgkr.cn-bj.ufileos.com/53c8995d-3813-4a18-b3a5-68d89643455a.png)
* SDN的数据平面也支持可编程（Intel高性能网络数据处理框架DPDK、斯坦福大学 数据平面可编程语言P4）


## 实验一：Mininet的应用实践