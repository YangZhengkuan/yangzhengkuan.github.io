---
layout: post
title: HDFS常用操作命令
tags: Hadoop
---

1. 对HDFS的操作方式 hadoop fs xxx

        hadoop fs -ls /		查看hdfs根目录下内容
            hadoop fs -ls hafd://hadoop:9000/
                    hdfs根目录路径的完整写法
                    参看配置 core-site.xml
                    执行命令 cd /usr/local/hadoop/conf
                         more core-site.xml
        hadoop fs -ls /usr	查看usr目录
        hadoop fs -lsr /	递归查看hdsf所有目录下内容
        hadoop fs -mkdir /d1	创建新的文件夹d1
        hadoop fs -put /root/install.log /d1
                    上传文件到d1文件夹下
                    再次执行相同命令时，会提示已经存在，不会覆盖
        hadoop fs -put /root/install.log /d2
                    在-put命令中，目标路径类型默认为文件，不是一个文件夹
                    不会上传到d2目录成功，而会在hdfs根目录下复制该文件
        hadoop fs -put /root/install.log /d1/abc
                    上传同一个文件到d1目录下，被重命名为abc
        hadoop fs -put <linux source> <hdfs source>
        hadoop fs -get /d1/abc .
                    复制到当前目录
        hadoop fs -get <hdfs source> <linux destination>
                    把数据从hdfs下载到Linux的特定目录下
        hadoop fs -text <hdfs source>
                    直接查看hdfs的文件，没有分页【Linux中有分页显示】
        hadoop fs -rm /d1/abc	删除hdfs文件
        hadoop fs -rmr /d1	删除hdfs文件夹，同时删除文件夹下的文件
    
        hadoop			列出 hadoop 所有可用操作
        hadoop fs		列出 hadoop fs 所有可用操作
        hadoop fs -help		列出 hadoop fs 操作的帮助
                        【<path>以尖括号包括，表示可有可无】
        hadoop fs -help	cp	列出 hadoop fs cp 操作的帮助
        hadoop fs -ls		表示列出 user/<currentUser> 目录下内容
                    该文件夹默认不存在，需要手动创建 hadoop fs -mkdir /user/root
                    其他操作类似，也使该目录作为默认路径
                    为避免出现错误，可尽量使用绝对路径

2. HDFS的datanode在存储数据时，如果原始文件大小大于64M，按照64M大小切分，如果小于64M，则只有一个Block，占用磁盘空间是源文件的大小。

3. RPC（remote procedure call） 远程过程调用

        不同java进程间的对象方法的调用
        一方称作服务端（server），一方称作客户端（client）【C\S结构】
        server端提供对象，供客户端调用的，被调用的对象的方法的执行发生在server端
        RPC是hadoop框架运行的基础
    
        参看：Hadoop-test1 --> src --> hadoop.rpc 
        >> 为服务端提供的对象必须是一个接口[jdk反射代理要求的]，接口extends VersionedProtocal
        >> 客户端能够操作对象的方法必须位于对象的接口中		  
