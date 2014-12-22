# AMPLab Camp 5 Self Study

## Online Resources
- [Slide, Video]
- [Getting Started With Your USB Stick]

### Compare Hadoop Distributions
Possible use one of these vm as base:

- [Compare Hortonworks, Cloudera and MapR] Hortonworks consists all open source packages, Cloudera and MapR are better solutions if money is not an issue and you'd like to get some advanced features. 
Cloudera just introduced Impala which may be a killer feature for some. MapR has some unique HA attributes and uses a NFS compatible filesystem. MapR is supposedly the fastest Hadoop solution in the market. Also there is a short [video compare Hortonworks, Cloudera, MapR and Intel]
- [What are the core differences between Cloudera's hadoop distro and HortonWorks distro?] and some reasons [why use distros]
- Download the latest [Hortonworks Data Platform] and follow [startup sandbox] in slideshare, or follow this blog for [setting up Hortonworks with Vagrant], which also provides a link for getting Vagrant box image. There is a [Hortonworks good community] forum to follow.

## Test Labs Installation
- Add a note file `AMPlabCamp5SelfStudy.md` (this file)

```
~/Projects/ampcamp5-usb l
total 16
-rw-rw-r--@  1 rkuo  staff  1346 Oct 27 13:57 README.md
drwxrwxr-x@  7 rkuo  staff   238 Nov  3 11:59 SparkR
-rw-r--r--@  1 rkuo  staff   829 Dec 16 12:24 amplab_camp_5_self_study.md
drwxr-xr-x@  8 rkuo  staff   272 Oct 28 10:45 data
drwxr-xr-x@  8 rkuo  staff   272 Jun 19 16:50 sbt
drwxr-xr-x@  6 rkuo  staff   204 Jun 19 17:11 simple-app
drwxrwxr-x@ 14 rkuo  staff   476 Oct 28 10:57 spark
drwxr-xr-x@ 12 rkuo  staff   408 Oct 28 10:57 tachyon
~/Projects/ampcamp5-usb cd simple-app
~/Projects/ampcamp5-usb/simple-app ../spark/bin/spark-submit --class "SimpleApp" --master local[*] target/scala-2.10/simple-project_2.10-1.0.jar
zsh: no matches found: local[*]
~/Projects/ampcamp5-usb/simple-app bash
bash-3.2$ pwd
/Users/rkuo/Projects/ampcamp5-usb/simple-app
bash-3.2$ ../spark/bin/spark-submit --class "SimpleApp" --master local[*] target/scala-2.10/simple-project_2.10-1.0.jar
Using Spark's default log4j profile: org/apache/spark/log4j-defaults.properties
14/12/17 01:45:39 INFO SecurityManager: Changing view acls to: rkuo,
```
## Start spark-shell
http://ampcamp.berkeley.edu/5/exercises/data-exploration-using-spark.html

```
~/Projects/spark/ampcamp5/ampcamp5-usb ls
README.md  SparkR     data       sbt        simple-app spark      tachyon
~/Projects/spark/ampcamp5/ampcamp5-usb pwd
/Users/rkuo/Projects/spark/ampcamp5/ampcamp5-usb
~/Projects/spark/ampcamp5/ampcamp5-usb spark/bin/spark-shell
Using Spark's default log4j profile: org/apache/spark/log4j-defaults.properties
14/12/17 17:18:40 INFO SecurityManager: Changing view acls to: rkuo,
14/12/17 17:18:40 INFO SecurityManager: Changing modify acls to: rkuo,
14/12/17 17:18:40 INFO SecurityManager: SecurityManager: authentication disabled; ui acls disabled; users with view permissions: Set(rkuo, ); users with modify permissions: Set(rkuo, )
14/12/17 17:18:40 INFO HttpServer: Starting HTTP Server
14/12/17 17:18:41 INFO Utils: Successfully started service 'HTTP class server' on port 53726.
Welcome to
      ____              __
     / __/__  ___ _____/ /__
    _\ \/ _ \/ _ `/ __/  '_/
   /___/ .__/\_,_/_/ /_/\_\   version 1.1.0
      /_/
      
... [snip] ... 
14/12/17 17:18:51 INFO Utils: Successfully started service 'HTTP file server' on port 53729.
14/12/17 17:18:51 INFO Utils: Successfully started service 'SparkUI' on port 4040.
14/12/17 17:18:51 INFO SparkUI: Started SparkUI at http://waterlily:4040
2014-12-17 17:18:52.738 java[12046:270067] Unable to load realm info from SCDynamicStore
14/12/17 17:18:53 INFO Executor: Using REPL class URI: http://192.168.1.65:53726
14/12/17 17:18:53 INFO AkkaUtils: Connecting to HeartbeatReceiver: akka.tcp://sparkDriver@waterlily:53727/user/HeartbeatReceiver
14/12/17 17:18:53 INFO SparkILoop: Created spark context..
Spark context available as sc.     
```
A web based SparkUI is started and localhost:4040, and see [Monitoring and Instrumentation] for details. 

Create a RDD

```
scala> sc
res0: org.apache.spark.SparkContext = org.apache.spark.SparkContext@732891dd

scala> val pagecounts = sc.textFile("data/pagecounts")
14/12/17 18:07:46 INFO MemoryStore: ensureFreeSpace(32872) called with curMem=0, maxMem=280248975
14/12/17 18:07:46 INFO MemoryStore: Block broadcast_0 stored as values in memory (estimated size 32.1 KB, free 267.2 MB)
pagecounts: org.apache.spark.rdd.RDD[String] = data/pagecounts MappedRDD[1] at textFile at <console>:12
```
(ToDo) This is a good place to use Hadoop tool to inspect the file location. 
For now, we just list the directory,

```
~/Projects/spark/ampcamp5/ampcamp5-usb l
total 8
-rw-rw-r--@  1 rkuo  staff  1346 Oct 27 13:57 README.md
drwxrwxr-x@  7 rkuo  staff   238 Nov  3 11:59 SparkR
drwxr-xr-x@  8 rkuo  staff   272 Oct 28 10:45 data
drwxr-xr-x@  8 rkuo  staff   272 Jun 19 16:50 sbt
drwxr-xr-x@  6 rkuo  staff   204 Jun 19 17:11 simple-app
drwxrwxr-x@ 14 rkuo  staff   476 Oct 28 10:57 spark
drwxr-xr-x@ 12 rkuo  staff   408 Oct 28 10:57 tachyon
~/Projects/spark/ampcamp5/ampcamp5-usb ls -l spark
total 1152
-rw-rw-r--@  1 rkuo  staff  520123 Oct 27 12:53 CHANGES.txt
-rw-rw-r--@  1 rkuo  staff   30816 Oct 27 12:53 LICENSE
-rw-------@  1 rkuo  staff   22559 Oct 27 12:53 NOTICE
-rw-rw-r--@  1 rkuo  staff    4811 Oct 27 12:53 README.md
-rw-rw-r--@  1 rkuo  staff      58 Oct 27 12:53 RELEASE
drwx------@ 21 rkuo  staff     714 Oct 27 12:53 bin
drwxrwxr-x@  9 rkuo  staff     306 Oct 27 20:58 conf
drwx------@  7 rkuo  staff     238 Oct 27 12:53 ec2
drwxrwxr-x@  3 rkuo  staff     102 Oct 27 12:53 examples
drwxrwxr-x@  5 rkuo  staff     170 Oct 27 12:53 lib
drwx------@  9 rkuo  staff     306 Oct 27 12:53 python
drwx------@ 17 rkuo  staff     578 Oct 27 12:53 sbin
~/Projects/spark/ampcamp5/ampcamp5-usb ls -l data
total 0
drwxr-xr-x@  6 rkuo  staff  204 Jun 19 02:02 examples-data
drwxr-xr-x@  5 rkuo  staff  170 Jun 19 01:06 graphx
drwxr-xr-x@  4 rkuo  staff  136 Jun 19 16:55 join
drwxr-xr-x@  5 rkuo  staff  170 Jun 19 01:07 movielens
drwxrwxr-x@  2 rkuo  staff   68 Oct 28 10:56 tmp
drwxr-xr-x@ 24 rkuo  staff  816 Jun 19 03:06 wiki_parquet
```
Nothing happens, from we can see from here. 

**some problem here**

```
scala> val pagecounts = sc.textFile("data/pagecounts")
14/12/18 15:11:45 INFO MemoryStore: ensureFreeSpace(32872) called with curMem=0, maxMem=280248975
14/12/18 15:11:45 INFO MemoryStore: Block broadcast_0 stored as values in memory (estimated size 32.1 KB, free 267.2 MB)
pagecounts: org.apache.spark.rdd.RDD[String] = data/pagecounts MappedRDD[1] at textFile at <console>:12

scala> pagecounts.take(10)
java.lang.RuntimeException: java.lang.reflect.InvocationTargetException
	at org.apache.hadoop.util.ReflectionUtils.newInstance(ReflectionUtils.java:115)
	at org.apache.hadoop.fs.FileSystem.createFileSystem(FileSystem.java:1385)
```
Based on the website, I need to set working directory to data directory, before creating sc;

```
System.setProperty("user.dir", "xxx")
val sc = new SparkContext(...)
```

- Tried xxx = spark/data did not work. 
- Tried xxx = `/Users/rkuo/Projects/spark/ampcamp5/ampcamp5-usb/spark` did not work either

**Switch to [Quick Start], come back here later**

Read "README.md" from current directory,

```
scala> val textFile = sc.textFile("README.md")
14/12/20 03:40:00 INFO MemoryStore: ensureFreeSpace(32872) called with curMem=0, maxMem=280248975
14/12/20 03:40:00 INFO MemoryStore: Block broadcast_0 stored as values in memory (estimated size 32.1 KB, free 267.2 MB)
textFile: org.apache.spark.rdd.RDD[String] = README.md MappedRDD[1] at textFile at <console>:12
```
Count number of lines in the file,

```
scala> textFile.count()
14/12/20 03:40:34 WARN NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
...[snip]...
14/12/20 03:40:35 INFO SparkContext: Job finished: count at <console>:15, took 0.68776 s
res0: Long = 30
```
Get the first line of the file,

```
scala> textFile.first()
14/12/20 03:41:11 INFO SparkContext: Starting job: first at <console>:15
...[snip]...
14/12/20 03:41:11 INFO TaskSchedulerImpl: Removed TaskSet 1.0, whose tasks have all completed, from pool
14/12/20 03:41:11 INFO SparkContext: Job finished: first at <console>:15, took 0.015066 s
res1: String = # AMP Camp 5 Training USB #
```

Create a place to hold all lines with "Spark" in them, and count it.

```
scala> val linesWithSpark = textFile.filter(line => line.contains("Spark"))
linesWithSpark: org.apache.spark.rdd.RDD[String] = FilteredRDD[2] at filter at <console>:14

scala> textFile.filter(line => line.contains("Spark")).count()
14/12/20 12:30:22 INFO SparkContext: Starting job: count at <console>:15
...[snip]...
14/12/20 12:30:22 INFO TaskSchedulerImpl: Removed TaskSet 2.0, whose tasks have all completed, from pool
14/12/20 12:30:22 INFO SparkContext: Job finished: count at <console>:15, took 0.037409 s
res2: Long = 5
```

## About RDD (Resilient Distributed Dataset)

Create RDD,

```
scala> textFile.map(line => line.split(" ").size)
res3: org.apache.spark.rdd.RDD[Int] = MappedRDD[4] at map at <console>:15
```
Find out what we can do with a RDD by type `res3.` in console, then hit 'tab` key for code completion;

```
scala> res3.
++                         aggregate                  asInstanceOf               cache                      cartesian
checkpoint                 coalesce                   collect                    compute                    context
count                      countApprox                countApproxDistinct        countByValue               countByValueApprox
dependencies               distinct                   filter                     filterWith                 first
flatMap                    flatMapWith                fold                       foreach                    foreachPartition
foreachWith                getCheckpointFile          getStorageLevel            glom                       groupBy
id                         intersection               isCheckpointed             isInstanceOf               iterator
keyBy                      map                        mapPartitions              mapPartitionsWithContext   mapPartitionsWithIndex
mapPartitionsWithSplit     mapWith                    max                        min                        name
name_=                     partitioner                partitions                 persist                    pipe
preferredLocations         randomSplit                reduce                     repartition                sample
saveAsObjectFile           saveAsTextFile             setName                    sortBy                     sparkContext
subtract                   take                       takeOrdered                takeSample                 toArray
toDebugString              toJavaRDD                  toLocalIterator            toString                   top
union                      unpersist                  zip                        zipPartitions              zipWithIndex
zipWithUniqueId
```

Find out the number of words in the longest line in the file,

```
scala> res3.reduce((a, b) => if (a > b) a else b)
14/12/20 13:33:20 INFO SparkContext: Starting job: reduce at <console>:17
14/12/20 13:33:20 INFO DAGScheduler: Got job 4 (reduce at <console>:17) with 2 output partitions (allowLocal=false)
14/12/20 13:33:20 INFO DAGScheduler: Final stage: Stage 4(reduce at <console>:17)
14/12/20 13:33:20 INFO DAGScheduler: Parents of final stage: List()
14/12/20 13:33:20 INFO DAGScheduler: Missing parents: List()
14/12/20 13:33:20 INFO DAGScheduler: Submitting Stage 4 (MappedRDD[4] at map at <console>:15), which has no missing parents
14/12/20 13:33:20 INFO MemoryStore: ensureFreeSpace(2712) called with curMem=32872, maxMem=280248975
14/12/20 13:33:20 INFO MemoryStore: Block broadcast_5 stored as values in memory (estimated size 2.6 KB, free 267.2 MB)
14/12/20 13:33:20 INFO DAGScheduler: Submitting 2 missing tasks from Stage 4 (MappedRDD[4] at map at <console>:15)
14/12/20 13:33:20 INFO TaskSchedulerImpl: Adding task set 4.0 with 2 tasks
14/12/20 13:33:20 INFO TaskSetManager: Starting task 0.0 in stage 4.0 (TID 7, localhost, PROCESS_LOCAL, 1220 bytes)
14/12/20 13:33:20 INFO TaskSetManager: Starting task 1.0 in stage 4.0 (TID 8, localhost, PROCESS_LOCAL, 1220 bytes)
14/12/20 13:33:20 INFO Executor: Running task 0.0 in stage 4.0 (TID 7)
14/12/20 13:33:20 INFO Executor: Running task 1.0 in stage 4.0 (TID 8)
14/12/20 13:33:20 INFO HadoopRDD: Input split: file:/Users/rkuo/Projects/spark/ampcamp5/ampcamp5-usb/README.md:0+673
14/12/20 13:33:20 INFO HadoopRDD: Input split: file:/Users/rkuo/Projects/spark/ampcamp5/ampcamp5-usb/README.md:673+673
14/12/20 13:33:21 INFO Executor: Finished task 1.0 in stage 4.0 (TID 8). 1809 bytes result sent to driver
14/12/20 13:33:21 INFO Executor: Finished task 0.0 in stage 4.0 (TID 7). 1809 bytes result sent to driver
14/12/20 13:33:21 INFO TaskSetManager: Finished task 1.0 in stage 4.0 (TID 8) in 62 ms on localhost (1/2)
14/12/20 13:33:21 INFO TaskSetManager: Finished task 0.0 in stage 4.0 (TID 7) in 63 ms on localhost (2/2)
14/12/20 13:33:21 INFO DAGScheduler: Stage 4 (reduce at <console>:17) finished in 0.064 s
14/12/20 13:33:21 INFO TaskSchedulerImpl: Removed TaskSet 4.0, whose tasks have all completed, from pool
14/12/20 13:33:21 INFO SparkContext: Job finished: reduce at <console>:17, took 0.090007 s
res7: Int = 29
```

### Basic  


## Spark Streaming

[difference streaming sources]: https://spark.apache.org/docs/1.2.0/img/streaming-arch.png

Spark Streaming can take different streaming sources. 
![difference streaming sources]

### Use NC

### Use Kafka 

### Use Twitter


[Slide, Video]: http://ampcamp.berkeley.edu/5/
[Getting Started With Your USB Stick]: http://ampcamp.berkeley.edu/5/exercises/getting-started.html
[Compare Hortonworks, Cloudera and MapR]: http://www.experfy.com/blog/cloudera-vs-hortonworks-comparing-hadoop-distributions/
[video compare Hortonworks, Cloudera, MapR and Intel]: https://www.youtube.com/watch?v=IvtyruO4dN4
[What are the core differences between Cloudera's hadoop distro and HortonWorks distro?]: http://www.quora.com/What-are-the-core-differences-between-Clouderas-hadoop-distro-and-HortonWorks-distro
[why use distros]: http://www.quora.com/Are-there-any-reasons-for-using-vendor-specific-Hadoop-distributions-like-Cloudera-Hortonworks-instead-of-vanilla-Apache-Hadoop-if-Im-not-using-their-support-services
[Hortonworks Data Platform]: http://hortonworks.com/hdp/downloads/
[setting up Hortonworks with Vagrant]: (http://hortonworks.com/blog/building-hadoop-vm-quickly-ambari-vagrant/
[Hortonworks good community]: http://hortonworks.com/community/forums/
[startup sandbox]: http://www.slideshare.net/hortonworks/sandbox-startup
[Monitoring and Instrumentation]: http://spark.apache.org/docs/1.1.1/monitoring.html
[Quick Start]: http://spark.apache.org/docs/latest/quick-start.html

[spark streaming doc]: https://spark.apache.org/docs/1.2.0/streaming-programming-guide.html

