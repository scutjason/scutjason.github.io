---
title: 变分推断Variational-Inference
date: 2019-03-18 17:06:21
tags:
 - 变分贝叶斯推断
 - 变分法
categories:
 - machine learning
---
本文剖析机器学习中最常见的公式之一变分推断Variational Inference
<!--more-->
# 变分法
变分法是17世纪末发展起来的一门数学分支，是泛函分析里面的一个领域，在普通的最优化问题中，往往求解得到的是一个最优值解，而在一个变分问题中，求解得到的是一个最优函数解，因此变分问题可以看成是泛函的一个极值问题。最经典的一个变分问题就是最速下降曲线问题：在重力作用下一个粒子沿着该路径可以在最短时间从点A到达不直接在它底下的一点B。在所有从A到B的曲线中必须极小化代表下降时间的表达式。该问题由从约翰·伯努利(Johann Bernoulli)1696年提出，并由此发展成了变分法这门数学分支。在统计机器学习里变分法也起着至关重要的作用，比如在最大熵问题中，可以利用变分法推导出正态分布。在统计机器学习里面还有一个重要的概念叫做变分贝叶斯推断(Variational Bayesian Inference)。很多统计机器学习问题里面，往往需要去近似求解不可观测变量或者叫隐变量(latent variable)的后验概率分布，而变分贝叶斯推断关注的就是如何求解一个近似后验概率分布，因此在统计机器学习里面应用比较广泛。下面会首先介绍变分法的相关知识，然后再介绍变分贝叶斯推断的相关知识。

变分问题在数学上的定义通俗地可以理解为泛函的极值问题。通常函数可以表示成自变量到因变量的映射关系：y=f(x)，泛函一般可以理解为函数的函数：J(f(x))，一般称J(f(x))为f(x)的泛函，但是泛函要求f(x)满足一定的边界条件，并且具有连续的二阶导数。这样的f(x)称为可取函数。通常一个最优化问题中，求解的是一个最优数值解，而在变分问题中，往往求解的是一个最优函数解。比如在求解最大熵的问题上，最终求解得到的就是一个概率分布，在该概率分布下使得熵最大，由于概率分布本身可以看成一个函数，因此可以把最大熵求解问题看成是一个变分求解问题。变分法相当于把微积分从变量推广到函数上。在普通的微积分中可以通过对变量求导数，然后令导数为0来求解一个极值问题，通过变分法一样可以通过导数为0的条件求解无约束极值问题，以及引入拉格朗日乘子来求解有约束极值问题。下面将通过一个求解最大熵分布的例子来展示，通过变分法是如何来求解一个函数的极值问题的。

首先给出一个概率质量分布函数f(x)，定义该分布下的信息熵为：

http://jorbe.sinaapp.com/2017/09/23/variational_and_variational_bayes_methods/
https://blog.csdn.net/qq_36080693/article/details/80214167
https://www.jianshu.com/p/b8ecabf9af07
https://chuansongme.com/n/1069106652650
https://blog.csdn.net/u012313437/article/details/84329339
https://blog.csdn.net/weixin_40255337/article/details/83088786
https://www.jianshu.com/p/76e0ad0d8778
https://blog.csdn.net/step_forward_ML/article/details/78077383
https://limengweb.wordpress.com/2017/11/13/%E6%B7%B1%E5%85%A5%E7%90%86%E8%A7%A3%E5%8F%98%E5%88%86%E6%8E%A8%E6%96%AD/
