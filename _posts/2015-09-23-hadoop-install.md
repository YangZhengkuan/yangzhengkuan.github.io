---
layout: post
title: Hadoop的伪分布安装步骤
tags: Hadoop
---

## Hadoop的伪分布安装步骤

PS: 使用root用户登录

1. Linux常用命令

	.	当前目录

	..	上级目录

	~	主目录

2. 修改主机名

	<1>修改当前回话中的主机名，执行命令hostname hadoop

	<2>修改配置文件中的主机名，vi /etc/sysconfig/network

        vi三种模式
            只读，不能写【进入编辑器时默认模式】
            编辑，能读也能写【按下键盘“a”或“i”】
                    【按ESC键退出该模式】
            命令，需要输入执行命令【按SHIFT和：组合键进入命令行模式】
                保存退出:wq或:wq!
                直接退出:q或:q!

	<3>验证	重启 PieTTY

3. 把hostname和IP绑定

        执行命令vi /etc/hosts，增加一行内容如下
            192.168.235.100 hadoop
            保存退出	
        验证	ping hadoop

4. 关闭防火墙【hadoop通信时会使用大量端口，为提高通信效率，并避免每次均需关闭防火墙，在此关闭防火墙服务，安全性会降低，但由于hadoop服务器构成一个局域网，安全性还是比较高的】

        service iptables stop
        验证：service iptables status
            结果：Firewall is not running
    
        关闭防火墙自动启动
            查看系统服务	chkconfig --list
            查看防火墙服务	chkconfig --list | grep iptables
            关闭防火墙自动启动	chkconfig iptables off
            验证			chkconfig --list | grep iptables 结果全为off

5. SSH（secure shell）的免密码登录

	<1>执行命令 ssh-keygen -t rsa 产生秘钥，然后点击几次回车即可，秘钥位于当前用户目录下ssh文件夹中【~/.ssh】

	<2>执行命令 cp ~/.ssh/id_rsa.pub ~/.ssh/authorized_keys【cp id_rsa.pub authorized_keys】

	<3>验证 ssh localhost，回车再输入yes

6. 安装JDK

	<1>执行命令 rm -rf /usr/local/* 删除所有内容

	<2>使用winscap把jdk把jdk文件从Windows复制到/usr/local 目录下

	<3>执行命令 chmod u+x jdk-6u24-linux-i586.bin 赋予执行权限

		验证 ls -l 查看权限

	<4>在当前目录下执行命令 ./jdk-6u24-linux-i586.bin解压缩

	<5>执行命令 mv jdk1.6.0_24 jdk

	<6>设置环境变量

        执行命令 vi /etc/profile
            增加了两条内容
                export JAVA_HOME=/usr/local/jdk
                export PATH=.:$JAVA_HOME/bin:$PATH
            保存退出
        执行命令 source /etc/profile 让该设置立即生效
        验证	 java -version

7. 安装Hadoop

	<1>执行命令 tar -zxvf hadoop-1.1.2.tar.gz 进行解压缩

	<2>重命名 mv hadoop-1.1.2.tar.gz hadoop

	<3>设置环境变量

		执行命令 vi /etc/profile
			增加了一条内容
				export HADOOP_HOME=/usr/local/hadoop
			修改了一条内容
				export PATH=.$HADOOP_HOME/bin:$JAVA_HOME/bin:$PATH

			保存退出	
		执行命令 source /etc/profile 让该设置立即生效

	<4>修改hadoop的配置文件，位于$HADOOP_HOME/conf目录下

		修改4个配置文件，分别是
			hadoop-env.sh
			core-site.xml
			hdfs-sixe.xml
			mapred-site.xml
		具体修改内容见PPT(1)Orientation
			【hadoop-env.sh修改第9行】
				export JAVA_HOME=/usr/local/jdk
			【core-site.xml的修改内容如下】
				<configuration>
				     <property>
					<name>fs.default.name</name>
					<value>hdfs://hadoop:9000</value>
					<description>change your own hostname</description>
				    </property>
				    <property>
					<name>hadoop.tmp.dir</name>
					<value>/usr/local/hadoop/tmp</value>
				    </property>  
				</configuration>
			【hdfs-sixe.xml的修改内容】
				<configuration>
				    <property>
					<name>dfs.replication</name>
					<value>1</value>
				    </property>
				    <property>
					<name>dfs.permissions</name>
					<value>false</value>
				    </property>
				</configuration>
			【mapred-site.xml的修改内容】
				<configuration>
				    <property>
					<name>mapred.job.tracker</name>
					<value>hadoop:9001</value>
					<description>change your own hostname</description>
				    </property>
				</configuration>

	<5>执行命令 hadoop namenode -format 对hadoop进行格式化

	<6>执行命令 start-all.sh

		(1)验证：执行命令jps，会发现5个java进程
			分别是
				NameNode
				DataNode
				SecondaryNameNode
				JobTracker
				TaskTracker
		(2)通过Linux浏览器访问
			hadoop:50070
			hadoop:50030
		   可以修改Windows的C:\Windows\System32\drivers\etc\hosts文件
		   添加192.168.235.100 hadoop
		   可以在windows内浏览器中访问

8. 在Windows浏览器无法访问到资源，是由于NameNode进程没有启动成功

	(1)没有对hadoop格式化

	(2)配置文件只拷贝未修改

	(3)hostname与ip没有绑定

	(4)SSH的免密码登录没有配置成功

	(5)多次格式化hadoop也会导致错误

		方法：删除/usr/local/hadoop/tmp文件夹，重新格式化

9. 关闭start-all.sh命令使用时的warning警告

        vi /etc/profile
        添加 HADOOP_HOME_WARN_SUPRESS=123 备注：赋值为任意值
        source /etc/profile
        验证：启动start-all.sh，不会再产生warning

