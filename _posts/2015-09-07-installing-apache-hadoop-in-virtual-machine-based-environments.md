---
layout: post
title: Installing Apache Hadoop in virtual-machine-based environments
tags: [analysis, apache, bigdata, computation, computing, data, distributed, hadoop, parallel, spark, ubuntu, ubuntu14]
comments: true
---

![](https://s3-eu-west-1.amazonaws.com/wopcontent/uploads/2015/08/665075ab-f29a-4937-9e95-f23f1316dd01image8-e1441022077395-300x209.png)
{:style="float: left; margin-right: 15px;margin-top: 20px;"}

Big data not only refers to machine learning, artificial intelligence, statistics and
programming. It also refers to the computing infrastructure and software
frameworks that make things happen. Regardless of the positive and negative
aspects of any technology, Apache Hadoop is the state of the art in big data
analytics. One of its several features consists in relying on off-the-shelf
computers, connected in a networked environment and equipped with very minimal
hardware. Unreliability, crashes, reboots and failures are not really a
problem for Hadoop, provided a number of nodes is up and running and a good
amount of redundancy by replication has been guaranteed by the administrator.



## Installing Apache Hadoop.

If the idea is to start Apache Hadoop at the earliest, downloading the binary
will save a lot of time. A good start is the [official
website](https://hadoop.apache.org/#Download+Hadoop). Unzip the binaries in a
directory of choice. We are installing Hadoop in _/opt/hadoop_

    
    
    wget http://apache.belnet.be/hadoop/core/hadoop-2.6.0/hadoop-2.6.0.tar.gz
    sudo tar xvf hadoop-2.6.0.tar.gz -C /opt/
    cd /opt
    sudo mv hadoop-2.6.0/ hadoop

Allow your user (in this case _frag_) to access the _hadoop_ directory

    
    
    sudo chown -R frag hadoop

Let your Hadoop user (if any) know where things are. In this case _java_ has
been installed at the path indicated by JAVA_HOME env variable. Check yours
before applying changes to ~/.bashrc

    
    
    export JAVA_HOME=/usr/lib/jvm/java-7-openjdk-amd64
    export HADOOP_HOME=/usr/local/hadoop
    export PATH=$HADOOP_HOME/bin:$PATH

A problem I found when launching Hadoop is about the JAVA_HOME. Apparently, it
is required to add JAVA_HOME also to /opt/hadoop/etc/hadoop/hadoop-env.sh
which will look like this

    
    
    # The java implementation to use.
    #export JAVA_HOME=${JAVA_HOME}
    export JAVA_HOME=/usr/lib/jvm/java-7-openjdk-amd64

At this point, the command launched from the console

    
    
    $hadoop

should return the instructions to run and usage for some sub-commands. If this
fails, do not continue, since there is already something wrong.  


## Configuring Hadoop

Now we configure the directory where Hadoop will store its data files, network
settings, and some other configuration options that might come useful later.
In my case, _frag_ is the user, and I decided to store the local file system
at the path _/usr/local/hadoop/tmp_ Therefore, I create this directory

    
    
    sudo mkdir -p /usr/local/hadoop/tmp

and set permissions as before

    
    
    sudo chown frag /usr/local/hadoop/tmp/

Do this with your username and for all other users who are allowed to access
Also restrict a bit the security policy with

    
    
    sudo chmod 750 /usr/local/hadoop/tmp/

The most important part comes now, with the configuration of some fundamental
files of the Hadoop platform.  

##### core-site.xml

    
    
    cd /opt/hadoop/etc/hadoop/
    sudo vi core-site.xml
    sudo cp mapred-site.xml.template mapred-site.xml
    
    
    <configuration>
     <property>
     <name>hadoop.tmp.dir</name>
     <value>/usr/local/hadoop/tmp</value>
     <description>A base for other temporary directories.</description>
     </property> 
    <property>
     <name>fs.default.name</name>
     <value>hdfs://localhost:9000</value>
     <description>The name of the default file system. A URI whose
     scheme and authority determine the FileSystem implementation. The uri's scheme determines the config property (fs.SCHEME.impl) naming the FileSystem implementation class. The uri's authority is used to determine the host, port, etc. for a filesystem.</description>
     </property>
    </configuration>
    

##### mapred-site.xml

    
    
    sudo vi mapred-site.xml
    
    
     <configuration>
     <property>
     <name>mapred.job.tracker</name>
     <value>localhost:9001</value>
     <description>The host and port that the MapReduce job tracker runs
     at. If "local", then jobs are run in-process as a single map
     and reduce task.
     </description>
     </property>
     </configuration>

##### hdfs-site.xml

    
    
    sudo vi hdfs-site.xml
    
    
     <configuration>
     <property>
     <name>dfs.replication</name>
     <value>2</value>
     <description>Default block replication.
     The actual number of replications can be specified when the file is created.
     The default is used if replication is not specified in create time.
     </description>
     </property>
     </configuration>

The replication value determines how many times a chunk of the RDD should be
replicated across the nodes. For a testing environment 2 is more than enough.
In production, however, a much higher replication value should be considered
to increase the reliability of the overall cluster.  

#### Format the HDFS filesystem

In general, a new file system must be formatted. This holds for HDFS too. The
command below does the job.

    
    
     $ /opt/hadoop/bin/hadoop namenode -format

This should not be done while the cluster is running, or all data will
suddenly be deleted.   It's time to start the machine. From the master node

    
    
    /opt/hadoop/sbin/start-dfs.sh

At this point some _ssh_ connections are performed by the master towards the
slaves (those are pseudo nodes, since they run on the same machine, just for
the sake of the tutorial). _ssh_ will ask for authentication three times, for
DataNode, SecondaryNameNode and NameNode (in reverse order). For production
systems this is not ideal. Hence, a _ssh key_ should be provided for the user
who's going to work with Hadoop. In order to configure _ssh_ not to ask for a
password every time, type this in all machines that belong to the cluster

    
    
    cat .ssh/id_rsa.pub | ssh b@B 'cat >> .ssh/authorized_keys2'
    chmod 700 .ssh
    chmod 640 .ssh/authorized_keys2
    

##### Playing with the filesystem

In order to create a virtual filesystem within Hadoop, a directory tree like
the traditional one should be created. In this example I will create the
_hadoop/data_ path.

    
    
    $hadoop fs -mkdir /hadoop
    $hadoop fs -mkdir /hadoop/data

Indeed, a list of the hadoop root directory returns what I expect.

    
    
    $ hadoop fs -ls /hadoop
      Found 1 items
      drwxr-xr-x - frag supergroup 0 2015-04-20 17:22 /hadoop/data

Seems to work! In order to make a local file visible in the Hadoop
infrastructure, it must be copied from local filesystem (or wherever it is) to
HDFS. In this case _localfile.txt_ is copies to the root directory of HDFS as
_file.txt_.

    
    
    $ bin/hadoop dfs -copyFromLocal ~/localfile.txt  /file.txt

##### Check up

The java utility _jps_ gives a print of the running Hadoop processes. It
should return something like this

    
    
    $ jps
     28130 DataNode
     28323 SecondaryNameNode
     27968 NameNode
     28471 Jps

Seems to work!

#### Monitoring

Once Hadoop is up and running, it is possible to point the browser to the
master node (_vlab1_ in my case) _http://vlab1:50070_ and monitor all
resources and the complete status of the infrastructure from the master node
_vlab1_. There is also a HDFS NameNode web interface at _http://vlab1:8042_
where, again, _vlab1_ is the hostname of the master node.

##### Stop Hadoop

In order to stop the cluster

    
    
    /opt/hadoop/sbin/stop-dfs.sh

The master node is stopping Hadoop from within each of the slave nodes. No ssh
password should be required though.  

#### Virtualization technology

At home I don't have thousands of physical machines to try this out. I do have
virtual machines though, as many as I want (until complete exhaustion of
computer memory). After setting one Ubuntu virtual machine in VirtualBox and
installing and configuring everything as explained above, I just cloned it to
get three running virtual machines in a matter of minutes. It's time for me to
enjoy my virtual Hadoop cluster. 

Happy Hadooping!
