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
```
<configuration>
   <property>
       <name>fs.defaultFS</name>
       <value>hdfs://localhost:9000</value>
   </property>
</configuration>
```

  ![image](https://user-images.githubusercontent.com/45985801/112506651-fc826b00-8db3-11eb-8c1e-61cc6c43becb.png)

# hdfssite.xml <h1>
To edit this file before You need to create one directory in hadoop-2.8.0 and named it as data:
  1. In that folder you need create two more folders one is namenode and datanode
```
<configuration>
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
</configuration>
```
  
  ![image](https://user-images.githubusercontent.com/45985801/112506679-01dfb580-8db4-11eb-9c69-1d2d78402676.png)

  
# yarnsite.xml <h1>
```
<configuration>
<!-- Site specific YARN configuration properties -->
   <property>
    	<name>yarn.nodemanager.aux-services</name>
    	<value>mapreduce_shuffle</value>
   </property>
   <property>
      	<name>yarn.nodemanager.auxservices.mapreduce.shuffle.class</name>  
	<value>org.apache.hadoop.mapred.ShuffleHandler</value>
   </property>
</configuration>
```
  
  ![image](https://user-images.githubusercontent.com/45985801/112506630-f7252080-8db3-11eb-93ea-3116bcc0115b.png)

  
# mapredsite.xml <h1>
```
<configuration>
   <property>
       <name>mapreduce.framework.name</name>
       <value>yarn</value>
   </property>
</configuration>
```
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

# Next Thing is Hive Installation <h1>

1.Download hive 2.1.1 https://archive.apache.org/dist/hive/hive-2.1.1/ download the tar.gz file
2.Download derby 10.12.1.1 https://archive.apache.org/dist/db/derby/db-derby-10.12.1.1/ download the tar.gz file

# Next Step
Extrat those download files.
> Go to derby folder copy the lib folder and paste it in the hive folder
> Go to hive folder in that hive folder go to conf folder create new file with the name of  `hive-site.xml`
> And then pase these data into that file
```
<?xml version="1.0"?>
<?xml-stylesheet type="text/xsl" href="configuration.xsl"?>
<configuration><property> <name>javax.jdo.option.ConnectionURL</name> 
<value>jdbc:derby://localhost:1527/metastore_db;create=true</value> 
<description>JDBC connect string for a JDBC metastore</description>
</property><property> 
<name>javax.jdo.option.ConnectionDriverName</name> 
<value>org.apache.derby.jdbc.ClientDriver</value> 
<description>Driver class name for a JDBC metastore</description>
</property>
<property> 
<name>hive.server2.enable.impersonation</name> 
<description>Enable user impersonation for HiveServer2</description>
<value>false</value>
</property>
<property> 
<name>hive.server2.enable.doAs</name> 
<description>Enable user impersonation for HiveServer2</description>
<value>false</value>
</property>
<property>
<name>hive.server2.authentication</name> 
<value>NOSASL</value>
<description> Client authentication types. NONE: no authentication check LDAP: LDAP/AD based authentication KERBEROS: Kerberos/GSSAPI authentication CUSTOM: Custom authentication provider (Use with property hive.server2.custom.authentication.class) </description>
</property>
<property>
<name>datanucleus.autoCreateTables</name>
<value>True</value>
</property>
<property>
<name>hive.server2.thrift.port</name>
<value>10000</value>
</property>
<property>
<name>hive.server2.webui.port</name>
<value>10002</value>
</property>
</configuration>
```
# And then add path to environment variable

1.Add derby path and hive path in environment varibles

![image](https://user-images.githubusercontent.com/45985801/112519010-f4c8c380-8dbf-11eb-90df-d080a4dd8f5d.png)
![image](https://user-images.githubusercontent.com/45985801/112519045-fdb99500-8dbf-11eb-89f1-b4f889be7c71.png)

# After finishing these step we can able to run hive 
> First Ensure that you hadoop is running or not, if you not run the hadoop means run the hadoop
> Second Thing you need start the derby server using this comman startNetworkServer -h 0.0.0.0
![image](https://user-images.githubusercontent.com/45985801/112519568-81738180-8dc0-11eb-84ba-d261654844f2.png)
# Now you are ready to start hive 

![image](https://user-images.githubusercontent.com/45985801/112519748-ad8f0280-8dc0-11eb-87dc-888f50447d1d.png)






  


