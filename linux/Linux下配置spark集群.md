0、购买阿里云ESC服务器（centos7.2 x64）



1、修改主机名

用 vi 打开 etc/hostname，三台服务器的主机名依次修改为 master、slave1 和 slave2。

```
hostnamectl set-hostname 新主机名
```

 2、配置 hosts 文档

```
# vi /etc/hosts
```

在 hosts 文件中添加三台服务器的 IP 地址和对应的主机名。

47.94.140.216 master
120.77.67.64 slave0
120.77.58.169 slave1

配置之后 ping 一下用户名看是否生效

```
# ping master
# ping slave1
# ping slave2
```

安装openssh，用于传文件

```
$ yum install openssh-server
```

安装jdk

```
yum -y install java-1.8.0-openjdk*
```







在三台服务器上执行：cd root/.ssh，cat id_rsa.pub>>authorized_keys，将 id_rsa.pub 追加到 authorized_keys。

将 slave1 和 slave2 的 id_rsa.pub 拷贝到 master（传输文件可用 scp），并将其内容追加到 master 的 root/.ssh/authorized_keys 中。同理，将 slave1 和 master 的 id_rsa.pub 追加到 slave2 的 authorized_keys，将 slave2 和 master 的 id_rsa.pub 追加到 slave1 的 authorized_keys。



生成密钥

```
ssh-keygen -t rsa
```

将client端的密钥添加到server端的authorized_key中

```
cat id_rsa.pub>>authorized_keys

```

将client端的密钥传到server端可以使用scp

```
scp id_rsa.pub root@slave1:/root/.ssh/key_from_master
cat key_from_slave1>>authorized_keys
```

为了实现master和slave之间自由通信，每台主机都应该配置所有主机的key



关闭防火墙

centos 7

```
# systemctl start firewalld.service#启动firewall
# systemctl stop firewalld.service#停止firewall
# systemctl disable firewalld.service#禁止firewall开机启动
scp id_rsa.pub root@slave1:/root/.ssh/authorized_keys_from_master
sudo gedit /etc/profile
```





上传scala和spark

```
scp scala-2.10.6.tgz root@47.94.140.216:/root/hadoop/spark/
scp spark-1.6.2-bin-hadoop2.6.tgz root@47.94.140.216:/root/hadoop/spark/


```

解压scala和spark

```
tar xvzf scala-2.10.6.tgz
tar xvzf spark-1.6.2-bin-hadoop2.6.tgz


```

环境变量配置, source生效

```
vi /etc/profile
source /etc/profile
```

在文件末尾添加以下内容

```
#scala&spark environment
export SCALA_HOME=/root/hadoop/spark/scala-2.10.6
export SPARK_HOME=/root/hadoop/spark/spark-1.6.2-bin-hadoop2.6
export PATH=$SPARK_HOME/sbin:$SCALA_HOME/bin:$PATH

```

修改配置文件 /usr/local/spark/conf 中：

```
# mv spark-env.sh.template spark-env.sh
# mv log4j.properties.template log4j.properties
# mv slaves.template slaves
```

在 spark-env.sh 结尾添加

```
export SCALA_HOME=/root/hadoop/spark/scala-2.10.6
```

修改 slaves 文件

```
master
slave1
slave2
```

开启集群 start-all.sh

查看spark进程 jps