# python_hive_connect
Download java jdk in version of 1.8
Download Hadoop version 2.8.0 https://hadoop.apache.org/release/2.8.0.html download the tar.gz file
and then we need to do some configuration in hadoop files.
# Hadoop installation
These files are list out in hadoop2.8.0/etc/hadoop/
1. coresite.xml
2. hdfssite.xml
3. yarnsite.xml
4. mapredsite.xml
5. hadoopenv.cmd

Do configuration like this:
# coresite.xml <h1>
     <property>
       <name>fs.defaultFS</name>
       <value>hdfs://localhost:9000</value>
   </property>
  
  ![image](https://user-images.githubusercontent.com/45985801/112506651-fc826b00-8db3-11eb-8c1e-61cc6c43becb.png)

# hdfssite.xml <h1>
To edit this file before You need to create one directory in hadoop-2.8.0 and named it as data:
  1. In that folder you need create two more folders one is namenode and datanode
     <property>
       <name>dfs.replication</name>
       <value>1</value>
   </property>
   <property>
       <name>dfs.namenode.name.dir</name>
       <value>/hadoop-2.8.0/data/namenode</value>
   </property>
   <property>
       <name>dfs.datanode.data.dir</name>
       <value>/hadoop-2.8.0/data/datanode</value>
   </property>
  
  ![image](https://user-images.githubusercontent.com/45985801/112506679-01dfb580-8db4-11eb-9c69-1d2d78402676.png)

  
# yarnsite.xml <h1>
     <property>
    	<name>yarn.nodemanager.aux-services</name>
    	<value>mapreduce_shuffle</value>
   </property>
   <property>
      	<name>yarn.nodemanager.auxservices.mapreduce.shuffle.class</name>  
	<value>org.apache.hadoop.mapred.ShuffleHandler</value>
   </property>
  
  ![image](https://user-images.githubusercontent.com/45985801/112506630-f7252080-8db3-11eb-93ea-3116bcc0115b.png)

  
# mapredsite.xml <h1>
     <property>
       <name>mapreduce.framework.name</name>
       <value>yarn</value>
   </property>
  
  ![image](https://user-images.githubusercontent.com/45985801/112506608-f2606c80-8db3-11eb-964e-2a2f94e1daa8.png)

# hadoopenv.cmd <h1>
  1. In this file you need put java path 
  set JAVA_HOME=C:\Java\jdk1.8.0_202
  
  ![image](https://user-images.githubusercontent.com/45985801/112506588-ebd1f500-8db3-11eb-94ee-d22c0bc1782b.png)
  
# After These you have to add some files in hadoop-2.8.0/bin/
1. Download the zip folder and extract it copy the bin folder and replace the bin in your hadoop-2.8.0/bin
http://backend.onstep.in/hadoopconfig/


# After All Doing this you need to add the path into the environment_variables
![image](https://user-images.githubusercontent.com/45985801/112507097-5edb6b80-8db4-11eb-89e0-95e59f6cc217.png)

![image](https://user-images.githubusercontent.com/45985801/112507136-6864d380-8db4-11eb-8f00-4f90218ae7a5.png)

# Atlast we come here to check hadoop is currently located in path
1. Open the Command promt in administrator mode.
2. ![image](https://user-images.githubusercontent.com/45985801/112507590-cabdd400-8db4-11eb-8b1b-5266f9e79600.png)
3. Here finally hadoop is currently located in path
4. The Next step you need to format your namenode in the comand promt
5. hdfs namenode -format
6. ![image](https://user-images.githubusercontent.com/45985801/112508078-3c961d80-8db5-11eb-8615-9c7bdf95af80.png)
7. ![image](https://user-images.githubusercontent.com/45985801/112508224-618a9080-8db5-11eb-8fdf-971b8005a2ab.png)
8. Atlast we have to start hadoop.
9. start-all.cmd
10. After this command four command prompt will be open namenode, datanode,nodemanager,yarnresoursemanager
# Namenode

![image](https://user-images.githubusercontent.com/45985801/112508596-b62e0b80-8db5-11eb-9755-0035057f70de.png)

# Datanode

![image](https://user-images.githubusercontent.com/45985801/112508801-e37ab980-8db5-11eb-82b6-cf4d62569919.png)

# Nodemanager

![image](https://user-images.githubusercontent.com/45985801/112508913-ff7e5b00-8db5-11eb-9d02-20bc8fa1472f.png)

# YarnResourseManager

![image](https://user-images.githubusercontent.com/45985801/112508989-0efda400-8db6-11eb-9f33-1b101e6d1edb.png)







  


