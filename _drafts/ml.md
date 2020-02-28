# 机器学习

## 概述

### 概念

目标： 从数据中归纳出模型（假设、函数），从而利用模型来预测新的数据

预测是离散值的任务叫做分类，只有两个类别的叫做二分类，有多个类别的叫做多分类
预测是连续值的任务叫做回归

### 分类

根据训练数据是否有标记，分类：监督学习和无监督学习
监督学习：分类，回归
无监督学习：聚类

## 归纳偏好

学习是在有限训练集进行，可能有多个假设与训练集一致，所有符合训练集的假设构成版本空间

在学习过程中，对某种假设类型的偏好，成为归纳偏好，应用归纳偏好，我们可以从版本空间
中挑出唯一的最适合的假设

## 模型评估与选择

### 经验误差与过拟合

错误率
精度
误差

经验误差/训练误差：在训练集上的误差
泛化误差：在新样本上的误差

### 评估方法

划分训练集、测试集，用测试集上的误差作为泛化误差的近似（离线实验）

## 评价指标

均方误差
均方根误差
准确率
召回




