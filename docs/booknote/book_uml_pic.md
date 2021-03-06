# UML建模图解教程

## UML概述

### 1.1 统一建模语言

#### 1.1.1 什么是UML

UML（Unified Modeling Language）是统一建模语言的简称。UML是一种可视化的建模语言，能让系统构造者用标准的、易于理解的方式表达出系统蓝图，便于用户、开发者之间进行交流设计结果。


**UML静态模型图**
 
|模型图	|说明					|
|-------|-----------------------|
|类图	|略|
|对象图	|略|
|组件图	|略|
|部署图	|略|
|包图	|略|
|组成结构图|可以把每一个构件类放到一个整体中，从类的内部结构来审视这个类。|


**UML动态模型图**
 
|模型图	|说明					|
|-------|-----------------------|
|用例图	|描述系统外部的执行者与系统提供的用例之间的某种联系。|
|序列图	|也叫时序图、顺序图。用于描述系统对象之间的动态协作关系。突出时间顺序。|
|协作图	|与序列图类似，用于描述系统对象之间的动态协作关系。与序列图相比，不突出时间顺序。|
|状态图	|状态图是对类描述的补充，用于展示此类对象所具有的状态以及某些事件发生时状态的迁移情况。|
|活动图	|活动图是一种特殊的状态图。活动图描述一个操作中要进行的各项活动的执行流程。|
|交互纵览图|可以直观地表达一组相关顺序图之间的流转逻辑。|
|计时图	|一种可选的交互图，展示交互过程中的真实时间信息，具体描述对象状态变化的时间点以及维持特定状态的时间段。|


## 面向对象的分析与设计方法

### 2.1 面向对象机制

#### 2.1.1 面向对象的要素

|要素	|说明					|
|-------|-----------------------|
|类		|略|
|对象	|略|
|消息	|略|
|封装	|把对象的属性和操作结合在一起，构成一个独立的对象，它的内部信息对外隐藏，外界对象不允许直接存取对象的属性，只能通过对象提供的接口进行操作。|
|继承	|子类自动地共享父类中数据和方法的机制。|
|多态	|指同一个操作作用于不同的对象，可以有不同的解释，产生不同的执行结果。多态通常通过派生类重载基类中的同名函数来实现。|

```
多态分为以下两种：
1. 编译时的多态。编译时的多态通过重载来实现。系统在编译时，根据传递的参数和返回的
   类型等信息决定实现何种操作。
2. 运行时的多态。运行时的多态是指直到系统运行时，才根据实际情况决定实现何种操作。
```


#### 2.1.2 主要原则

- 开放-闭合原则
- 替换原则
- 依赖倒转原则


## UML与Java项目开发

### 3.1 基于UML开发项目的基本过程

1. 业务建模和需求分析（常用：用例图）
2. 建立设计模型（常用：类图、时序图）
3. 系统的实现、测试和系统配置

```
在实际项目开发过程中，用例图、类图和时序图是UML中使用最广泛的图。
```


## 用例图

### 4.1 用例图概念

#### 4.1.1 概述

**用例图**（Use Case Diagram）也称为**用户模型图**，是由软件需求分析到最终实现的第一步。用例图从用户的角度来描述系统的功能，描述人们希望如何使用一个系统。


#### 4.1.3 主要组件

用例图包含4个基本组件：参与者、用例、关系、系统。


## 静态模型图

略。


## 动态模型图

略。


## 实现与部署模型图

略。


## UML与统一开发过程

略。


## 双向工程

略。


## 在线销售系统

略。


## 在线银行系统

略。

