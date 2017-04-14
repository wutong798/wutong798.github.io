<<<<<<< HEAD
﻿#数据科学入门

一直对数据科学很感兴趣，也陆陆续续学了很多东西。以下是个人觉得需要掌握的一些知识。

##1，入门
-----
####**学习要求**
 - 掌握R、python、SAS语言（任意一种即可）
 - 掌握sql
 - 熟悉数据清洗，统计分析、可视化常用的方法
 - 了解数据开发的基本流程以及要求。
 - 能够独立完成数据研究报告

----- 
####**学习方法**
 - 学习语言：推荐使用R语言。相比于Python，R数据分析、数据建模的package更强大。
    - 推荐先学Roger D.Peng的 [R Programming for Data Science](https://leanpub.com/rprogramming)（免费pdf）
    - 深入了解R可以读一下官方[Mannual](https://cran.r-project.org/manuals.html)，或者官方推荐[书籍](https://www.r-project.org/doc/bib/R-books.html)
 - 开发环境：Rstudio。Rstudio的包管理，数据预览非常方便。参考（需要梯子）：[R环境安装-win](https://www.youtube.com/watch?v=Ohnk9hcxf9M&feature=youtu.be)+[R环境安装-mac](https://www.youtube.com/watch?v=uxuuWXU-7UQ&feature=youtu.be)+[Rstudio安装](https://www.youtube.com/watch?v=bM7Sfz-LADM&feature=youtu.be)。
 - 以下是学习常用的package，足以胜任对数据的统计性分析。很多书都对其中一些package进行了介绍，但更推荐使用时查看官方文档。
    - 数据获取：
        -  RODBC, RMySQL, RPostgresSQL, RSQLite - 从sql数据库获得数据
        -  XLConnect, xlsx - 获得excel数据
        -  foreign - 获得SAS数据
    - 数据操作：
        - dplyr - 最常用的数据操作功能包。subsetting, summarizing, rearranging, joining等操作
        - tidyr - 表变换。列合并，列展开操作
    - 可视化
        - ggolot2 - 最常用的数据可视化包。除了官方文档，推荐个函数速查[cheet sheet](https://www.rstudio.com/wp-content/uploads/2015/03/ggplot2-cheatsheet.pdf)

 - [swirl](http://swirlstats.com/) - “swirl teaches you R programming and data science interactively, at your own pace, and right in the R console!swirl”. swirl内置了数据集和步骤引导，值得反复练习。

----------
####**其他好的学习资源**

 - Rstudio官方推荐的一些好的[packages](https://www.google.com/#q=good+package+R)。针对数据分析不同阶段给出package推荐，基本可以覆盖入门阶段需求。

                
    
 
##2，进阶
####**学习要求**

 - 掌握数据的推论性分析，回归分析
 - 掌握相关统计学知识
 - 掌握特征工程相关知识
    - 预处理
        - 无量纲化。实际上很多学习算法都内置了一些类似功能，因此在数据质量较好的情况下，为了避免引入误差，可以不用进行此步骤。
            - 标准化
            - 区间放缩
            - 归一化
        - 重编码
            - 二值化
            - [onehotencoding](http://blog.csdn.net/ariessurfer/article/details/42526673)/[dummy coding](http://blog.csdn.net/lime1991/article/details/41653841)
        - 数据变换
            - log
            - Box-Cox
        - 缺失值
        - 降维
            - PCA
            - LDA
    - 特征选择。
        - Filter:通过自变量和目标变量的关系选择特征。卡方检验，互信息。
        - Wrapper：通过目标函数来决定是否决定加入特征。RFE
        - Embedded：很多学习模型都自带特征选择特性‘XGBtree
 - 了解相关机器学习模型，掌握模型选择、使用、调参、融合
    - 常用回归模型
        - Linear Regression
        - Losgistc Regresson
        - 决策树
        - bagging
        - Random Forest
        - Boosting
        - Bayes
        - Regularized Regression
    - 模型融合
        - 简单组合
        - ensemlble
    - 模型调参
        - 贪心调参：grid search
    - 模型选择。
        - 需要考虑的因素：
            - Accuracy
            - Training Time
            - Linearity
            - Number of feature 
            - Number of parameters
            - 其他特性
        - 模型比较
        - 
                - 掌握高级可视化技巧

####**学习资源**

####机器学习
 - 首推的是Stanford的Machine Learning课程。相比于其他教程更加精简，但对核心原理的讲解和推导却非常细致。该课程也是Cousera上最火的课程之一，讲师吴恩达背景很厉害。
 - [The Elements of Statistical Learning](http://statweb.stanford.edu/~tibs/ElemStatLearn/printings/ESLII_print10.pdf)国外的经典教材，有免费pdf版本，相较于国内亚马逊卖的勘正了很多错误。
 - 李航的[《统计学习方法》](https://www.amazon.cn/dp/B007TSFMTA/ref=sr_1_1?ie=UTF8&qid=1491993158&sr=8-1&keywords=%E6%9D%8E%E8%88%AA)和[周志华]的[《机器学习》](https://www.amazon.cn/%E5%9B%BE%E4%B9%A6/dp/B01ARKEV1G/ref=sr_1_1?ie=UTF8&qid=1491993216&sr=8-1&keywords=%E6%9C%BA%E5%99%A8%E5%AD%A6%E4%B9%A0)也是国内最经典的教材了。特点是大而全，很多东西并不详细，但对形成知识框架很有帮助，有时间可以反复阅读。


 
##3，进一步提高

####**学习要求**

数据分析产品化
常见数据产品





=======
## 个人项目

[通过手机传感器数据实现人体运动识别](https://github.com/wutong798/Human_Activity_Recognition_with_Smartphones)
>>>>>>> origin/master
