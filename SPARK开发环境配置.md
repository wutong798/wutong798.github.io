之前一直都是单机跑模型，无奈性能有限，跑程序时只能玩手机。

一直心水能够把模型部署到集群上，最近终于动手了！配置环境爬了些小坑，这里稍微总结一下



本文主要包括两个部分。

1，服务器环境配置

2，本地IDE配置



## 服务器配置

##### 阿里云ECS集群

可参考[在阿里云上搭建 Spark 实验平台](http://www.cnblogs.com/NaughtyBaby/p/5402569.html)，在此基础上补充几点：

1. 主机购买：2-3台阿里云ECS即可，如果需要跑模型的，建议选2G内存。建议选经典网络，我使用专有网络的主机作为master时，不能成功调起slave。


2. 主机连接xshell和传文件Xftp

3. 不要用yum/apt-get安装java/scala，下载tar.gz文件，解压配环境路径。因为后面spark配置时需要输入jdk/scalal的环境路径。

4. 选择合适的scala版本。spark是用scala写的，解压在官网下载的spark压缩包，解压后看jar文件内spark的核心库“spark-core_2.11-2.2.0.jar”、“spark-sql_2.11-2.2.0.jar”、“spark-streaming_2.11-2.2.0.jar”，这说明用此版本是scala 2.11.X编写的Spark 2.2.0版本。我们同样选择2.11.X即可。

   ​

个人服务器

与上面类似，不需要设置主机通信步骤，slaves文件中写localhost即可

##### 本地IDE配置

JDK+SCALA+SPARK+IDEA+SBT

可参考[001-使用IDEA 工具创建Spark项目](http://blog.csdn.net/shenfuli/article/details/51534734)，补充几点：

1. 先在本机上安装jdk,scala,sbt。选择exe或msi自动安装即可。
2. 在build.sbt中设置librarydependcies第一次会很慢，因为会下载很多包。如果没有复杂的外部依赖，可以不写librarydependcies
3. 通过命令行sbt打包或者Idea自带的buid工具打包，用Idea打包时注意不要把不需要的外部库也打包进去，注意设置main函数
4. 通过maven/本地引入spark jar包后即可在Idea中右键运行spark程序。Idea中运行中注意：
   1. SparkConf中要设置setMaster("local[*]")
   2. 在顶部菜单中Run /Run Configuration页面中选择自己的module可以设置program argument，即主函数接收的参数。



部署完毕后，可以在IDE中跑一跑官方WordCount的例子，如果没问题，再打包放到服务器环境上跑（Xshell+Xftp）