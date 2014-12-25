# AMPLab Camp 5 Self Study

## Online Resources
- From AMP camp site [Slide, Video] and [Getting Started With Your USB Stick]
- There are some additional slides and videos from [Spark Summit 2014 Training].

[Slide, Video]: http://ampcamp.berkeley.edu/5/
[Getting Started With Your USB Stick]: http://ampcamp.berkeley.edu/5/exercises/getting-started.html
[How to light your 'Spark on a stick']: http://blueplastic.gitbooks.io/how-to-light-your-spark-on-a-stick/content/

[Spark Summit 2014 Training]: http://spark-summit.org/2014/training#news-page

### Compare Hadoop Distributions
If you like to use/view HDFS, you can use one of following platform as base and add Spark to it:

- [Compare Hortonworks, Cloudera and MapR] Hortonworks consists all open source packages, Cloudera and MapR are better solutions if money is not an issue and you'd like to get some advanced features. 
Cloudera just introduced Impala which may be a killer feature for some. MapR has some unique HA attributes and uses a NFS compatible filesystem. MapR is supposedly the fastest Hadoop solution in the market. Also there is a short [video compare Hortonworks, Cloudera, MapR and Intel]
- [What are the core differences between Cloudera's hadoop distro and HortonWorks distro?] and some reasons [why use distros]
- Download the latest [Hortonworks Data Platform] and follow [startup sandbox] in slideshare, or follow this blog for [setting up Hortonworks with Vagrant], which also provides a link for getting Vagrant box image. There is a [Hortonworks good community] forum to follow.

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

Try the following command, which should return 1000:

```
scala> sc.parallelize(1 to 1000).count()
```
We should see it returns 1000.

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

I think it just could not find file:
unzip `training-downloads.zip` and merge files in data directory to existing `ampcamp5-usb/data` and modified file location to `../data/pagecounts`, worked.

```
scala> sc
res0: org.apache.spark.SparkContext = org.apache.spark.SparkContext@7ea0788

scala> val pagecounts = sc.textFile("../data/pagecounts")
14/12/22 11:36:08 INFO MemoryStore: ensureFreeSpace(32872) called with curMem=0, maxMem=280248975
14/12/22 11:36:08 INFO MemoryStore: Block broadcast_0 stored as values in memory (estimated size 32.1 KB, free 267.2 MB)
pagecounts: org.apache.spark.rdd.RDD[String] = ../data/pagecounts MappedRDD[1] at textFile at <console>:12

scala> pagecounts.take(10)
14/12/22 11:36:33 WARN NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
14/12/22 11:36:33 WARN LoadSnappy: Snappy native library not loaded
14/12/22 11:36:33 INFO FileInputFormat: Total input paths to process : 2
14/12/22 11:36:33 INFO SparkContext: Starting job: take at <console>:15
14/12/22 11:36:33 INFO DAGScheduler: Got job 0 (take at <console>:15) with 1 output partitions 
...[snip]...
14/12/22 11:36:33 INFO DAGScheduler: Stage 0 (take at <console>:15) finished in 0.085 s
14/12/22 11:36:33 INFO TaskSchedulerImpl: Removed TaskSet 0.0, whose tasks have all completed, from pool
14/12/22 11:36:33 INFO SparkContext: Job finished: take at <console>:15, took 0.125963 s
res1: Array[String] = Array(20090505-000000 aa Main_Page 2 9980, 20090505-000000 ab %D0%90%D0%B8%D0%BD%D1%82%D0%B5%D1%80%D0%BD%D0%B5%D1%82 1 465, 20090505-000000 ab %D0%98%D1%85%D0%B0%D0%B4%D0%BE%D1%83_%D0%B0%D0%B4%D0%B0%D2%9F%D1%8C%D0%B0 1 16086, 20090505-000000 af.b Tuisblad 1 36236, 20090505-000000 af.d Tuisblad 4 189738, 20090505-000000 af.q Tuisblad 2 56143, 20090505-000000 af Afrika 1 46833, 20090505-000000 af Afrikaans 2 53577, 20090505-000000 af Australi%C3%AB 1 132432, 20090505-000000 af Barack_Obama 1 23368)
```
Make it prints better,

```
scala> pagecounts.take(10).foreach(println)
14/12/22 11:42:11 INFO SparkContext: Starting job: take at <console>:15
14/12/22 11:42:11 INFO DAGScheduler: Got job 1 (take at <console>:15) with 1 output partitions (allowLocal=true)
...[snip]...
14/12/22 11:42:11 INFO TaskSchedulerImpl: Removed TaskSet 1.0, whose tasks have all completed, from pool
14/12/22 11:42:11 INFO SparkContext: Job finished: take at <console>:15, took 0.016597 s
20090505-000000 aa Main_Page 2 9980
20090505-000000 ab %D0%90%D0%B8%D0%BD%D1%82%D0%B5%D1%80%D0%BD%D0%B5%D1%82 1 465
20090505-000000 ab %D0%98%D1%85%D0%B0%D0%B4%D0%BE%D1%83_%D0%B0%D0%B4%D0%B0%D2%9F%D1%8C%D0%B0 1 16086
20090505-000000 af.b Tuisblad 1 36236
20090505-000000 af.d Tuisblad 4 189738
20090505-000000 af.q Tuisblad 2 56143
20090505-000000 af Afrika 1 46833
20090505-000000 af Afrikaans 2 53577
20090505-000000 af Australi%C3%AB 1 132432
20090505-000000 af Barack_Obama 1 23368
```

It looks like, it automatic split the work into multiple job/tasks,

```
scala> pagecounts.count
14/12/22 11:56:10 INFO SparkContext: Starting job: count at <console>:15
14/12/22 11:56:10 INFO DAGScheduler: Got job 2 (count at <console>:15) with 2 output partitions (allowLocal=false)
14/12/22 11:56:10 INFO DAGScheduler: Final stage: Stage 2(count at <console>:15)
14/12/22 11:56:10 INFO DAGScheduler: Parents of final stage: List()
14/12/22 11:56:10 INFO DAGScheduler: Missing parents: List()
14/12/22 11:56:10 INFO DAGScheduler: Submitting Stage 2 (../data/pagecounts MappedRDD[1] at textFile at <console>:12), which has no missing parents
14/12/22 11:56:10 INFO MemoryStore: ensureFreeSpace(2392) called with curMem=37704, maxMem=280248975
14/12/22 11:56:10 INFO MemoryStore: Block broadcast_3 stored as values in memory (estimated size 2.3 KB, free 267.2 MB)
14/12/22 11:56:10 INFO DAGScheduler: Submitting 2 missing tasks from Stage 2 (../data/pagecounts MappedRDD[1] at textFile at <console>:12)
14/12/22 11:56:10 INFO TaskSchedulerImpl: Adding task set 2.0 with 2 tasks
14/12/22 11:56:10 INFO TaskSetManager: Starting task 0.0 in stage 2.0 (TID 2, localhost, PROCESS_LOCAL, 1237 bytes)
14/12/22 11:56:10 INFO TaskSetManager: Starting task 1.0 in stage 2.0 (TID 3, localhost, PROCESS_LOCAL, 1237 bytes)
14/12/22 11:56:10 INFO Executor: Running task 0.0 in stage 2.0 (TID 2)
14/12/22 11:56:10 INFO Executor: Running task 1.0 in stage 2.0 (TID 3)
14/12/22 11:56:10 INFO HadoopRDD: Input split: file:/Users/rkuo/Projects/spark/ampcamp5/ampcamp5-usb/data/pagecounts/part-00053:0+35495920
14/12/22 11:56:10 INFO HadoopRDD: Input split: file:/Users/rkuo/Projects/spark/ampcamp5/ampcamp5-usb/data/pagecounts/part-00001:0+35926685
14/12/22 11:56:10 INFO BlockManager: Removing broadcast 1
14/12/22 11:56:10 INFO BlockManager: Removing block broadcast_1
14/12/22 11:56:10 INFO MemoryStore: Block broadcast_1 of size 2416 dropped from memory (free 280211295)
14/12/22 11:56:10 INFO ContextCleaner: Cleaned broadcast 1
14/12/22 11:56:10 INFO BlockManager: Removing broadcast 2
14/12/22 11:56:10 INFO BlockManager: Removing block broadcast_2
14/12/22 11:56:10 INFO MemoryStore: Block broadcast_2 of size 2416 dropped from memory (free 280213711)
14/12/22 11:56:10 INFO ContextCleaner: Cleaned broadcast 2
14/12/22 11:56:11 INFO Executor: Finished task 0.0 in stage 2.0 (TID 2). 1731 bytes result sent to driver
14/12/22 11:56:11 INFO Executor: Finished task 1.0 in stage 2.0 (TID 3). 1731 bytes result sent to driver
14/12/22 11:56:11 INFO TaskSetManager: Finished task 0.0 in stage 2.0 (TID 2) in 934 ms on localhost (1/2)
14/12/22 11:56:11 INFO TaskSetManager: Finished task 1.0 in stage 2.0 (TID 3) in 933 ms on localhost (2/2)
14/12/22 11:56:11 INFO DAGScheduler: Stage 2 (count at <console>:15) finished in 0.934 s
14/12/22 11:56:11 INFO TaskSchedulerImpl: Removed TaskSet 2.0, whose tasks have all completed, from pool
14/12/22 11:56:11 INFO SparkContext: Job finished: count at <console>:15, took 0.940089 s
res3: Long = 1398882
```

We can watch the operation from web gui, `http://127.0.0.1:4040` ![Spark web gui stage]

[Spark web gui stage]: https://www.evernote.com/shard/s302/sh/6b012314-b7ed-480c-b626-8cb14a994e34/c87bc6b7fb168173a018f81508ebac69/deep/0/Spark-shell---Spark-Stages.png

[continue from here later](http://ampcamp.berkeley.edu/5/exercises/data-exploration-using-spark.html) I have some problem before, it is due to file does not exist and path is not correct, `val pagecounts = sc.textFile("../data/pagecounts")` works now.

```
scala> pagecounts.count
14/12/24 11:34:45 INFO SparkContext: Starting job: count at <console>:15
14/12/24 11:34:45 INFO DAGScheduler: Got job 1 (count at <console>:15) with 2 output partitions (allowLocal=false)
14/12/24 11:34:45 INFO DAGScheduler: Final stage: Stage 1(count at <console>:15)
14/12/24 11:34:45 INFO DAGScheduler: Parents of final stage: List()
14/12/24 11:34:45 INFO DAGScheduler: Missing parents: List()
14/12/24 11:34:45 INFO DAGScheduler: Submitting Stage 1 (../data/pagecounts MappedRDD[3] at textFile at <console>:12), which has no missing parents
14/12/24 11:34:45 INFO MemoryStore: ensureFreeSpace(2392) called with curMem=68184, maxMem=280248975
14/12/24 11:34:45 INFO MemoryStore: Block broadcast_3 stored as values in memory (estimated size 2.3 KB, free 267.2 MB)
14/12/24 11:34:45 INFO DAGScheduler: Submitting 2 missing tasks from Stage 1 (../data/pagecounts MappedRDD[3] at textFile at <console>:12)
14/12/24 11:34:45 INFO TaskSchedulerImpl: Adding task set 1.0 with 2 tasks
14/12/24 11:34:45 INFO TaskSetManager: Starting task 0.0 in stage 1.0 (TID 1, localhost, PROCESS_LOCAL, 1237 bytes)
14/12/24 11:34:45 INFO TaskSetManager: Starting task 1.0 in stage 1.0 (TID 2, localhost, PROCESS_LOCAL, 1237 bytes)
14/12/24 11:34:45 INFO Executor: Running task 0.0 in stage 1.0 (TID 1)
14/12/24 11:34:45 INFO Executor: Running task 1.0 in stage 1.0 (TID 2)
14/12/24 11:34:45 INFO HadoopRDD: Input split: file:/Users/rkuo/Projects/spark/ampcamp5/ampcamp5-usb/data/pagecounts/part-00001:0+35926685
14/12/24 11:34:45 INFO HadoopRDD: Input split: file:/Users/rkuo/Projects/spark/ampcamp5/ampcamp5-usb/data/pagecounts/part-00053:0+35495920
14/12/24 11:34:45 INFO BlockManager: Removing broadcast 2
14/12/24 11:34:45 INFO BlockManager: Removing block broadcast_2
14/12/24 11:34:45 INFO MemoryStore: Block broadcast_2 of size 2416 dropped from memory (free 280180815)
14/12/24 11:34:46 INFO ContextCleaner: Cleaned broadcast 2
14/12/24 11:34:46 INFO Executor: Finished task 1.0 in stage 1.0 (TID 2). 1922 bytes result sent to driver
14/12/24 11:34:46 INFO Executor: Finished task 0.0 in stage 1.0 (TID 1). 1922 bytes result sent to driver
14/12/24 11:34:46 INFO TaskSetManager: Finished task 1.0 in stage 1.0 (TID 2) in 972 ms on localhost (1/2)
14/12/24 11:34:46 INFO TaskSetManager: Finished task 0.0 in stage 1.0 (TID 1) in 975 ms on localhost (2/2)
14/12/24 11:34:46 INFO DAGScheduler: Stage 1 (count at <console>:15) finished in 0.976 s
14/12/24 11:34:46 INFO TaskSchedulerImpl: Removed TaskSet 1.0, whose tasks have all completed, from pool
14/12/24 11:34:46 INFO SparkContext: Job finished: count at <console>:15, took 0.983447 s
res2: Long = 1398882
```

**Switch to [Quick Start]**

Read "README.md" from current directory-spark,

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

### About RDD (Resilient Distributed Dataset)
[good RDD transformation diagram for word count example]: http://www.slideshare.net/cloudera/spark-devwebinarslides-final?related=1

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

Use a different example:

```
scala> sc
res0: org.apache.spark.SparkContext = org.apache.spark.SparkContext@61c54dc1

scala> val lines = sc.textFile("../hamlet.txt")
14/12/22 15:15:01 INFO MemoryStore: ensureFreeSpace(32872) called with curMem=0, maxMem=280248975
14/12/22 15:15:01 INFO MemoryStore: Block broadcast_0 stored as values in memory (estimated size 32.1 KB, free 267.2 MB)
lines: org.apache.spark.rdd.RDD[String] = ../hamlet.txt MappedRDD[1] at textFile at <console>:12
scala> lines.count()
14/12/22 15:15:51 WARN NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
...[snip]...
14/12/22 15:15:51 INFO TaskSchedulerImpl: Removed TaskSet 0.0, whose tasks have all completed, from pool
14/12/22 15:15:51 INFO SparkContext: Job finished: count at <console>:15, took 0.149683 s
res1: Long = 2
```

lines is a group of lines, which can be parsed further with " " to words,

```
scala> lines.map(line => line.split(" "))

...[snip]...
14/12/22 16:17:25 INFO DAGScheduler: Stage 2 (take at <console>:17) finished in 0.009 s
14/12/22 16:17:25 INFO TaskSchedulerImpl: Removed TaskSet 2.0, whose tasks have all completed, from pool
14/12/22 16:17:25 INFO SparkContext: Job finished: take at <console>:17, took 0.013589 s
res3: Array[Array[String]] = Array(Array(to, be, or), Array(not, to, be))
```

Since we know we only have two lines, so take the first two lines, this produces array of array, each line is one array. 

```
scala> res2.take(2)
14/12/22 16:17:24 INFO SparkContext: Starting job: take at <console>:17
14/12/22 16:17:24 INFO DAGScheduler: Got job 1 (take at <console>:17) with 1 output partitions (allowLocal=true)
...[snip]...
14/12/22 11:01:43 INFO SparkContext: Job finished: take at <console>:17, took 0.013306 s
res6: Array[Array[String]] = Array(Array(to, be, or), Array(not, to, be))
```	
flatMap, this produces one flat array of all elements,
since we know there are 6 elements, so we can ask for display first 6 elements.
```
scala> lines.flatMap(line => line.split(" "))
res4: org.apache.spark.rdd.RDD[String] = FlatMappedRDD[3] at flatMap at <console>:15
scala> res4.take(6)
14/12/22 16:23:03 INFO SparkContext: Starting job: take at <console>:17
14/12/22 16:23:03 INFO DAGScheduler: Got job 4 (take at <console>:17) with 1 output partitions (allowLocal=true)
...[snip]...
14/12/22 16:23:03 INFO TaskSchedulerImpl: Removed TaskSet 5.0, whose tasks have all completed, from pool
14/12/22 16:23:03 INFO SparkContext: Job finished: take at <console>:17, took 0.014058 s
res6: Array[String] = Array(to, be, or, not, to, be)
```
create pairs,

```
scala> res6.map(word => (word,1))
res7: Array[(String, Int)] = Array((to,1), (be,1), (or,1), (not,1), (to,1), (be,1))
```
since it is (k,v) pair, we can group them by their key,


```
scala> val wordCounts = lines.flatMap(line => line.split(" ")).map(word => (word, 1)).reduceByKey((a, b) => a + b)
14/12/22 18:14:12 WARN NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
14/12/22 18:14:12 WARN LoadSnappy: Snappy native library not loaded
14/12/22 18:14:12 INFO FileInputFormat: Total input paths to process : 1
wordCounts: org.apache.spark.rdd.RDD[(String, Int)] = ShuffledRDD[4] at reduceByKey at <console>:14

scala> wordCounts.collect()
14/12/22 18:14:47 INFO SparkContext: Starting job: collect at <console>:17
14/12/22 18:14:47 INFO DAGScheduler: Registering RDD 3 (map at <console>:14)
...[snip]...
14/12/22 18:14:48 INFO TaskSchedulerImpl: Removed TaskSet 0.0, whose tasks have all completed, from pool
14/12/22 18:14:48 INFO SparkContext: Job finished: collect at <console>:17, took 0.555674 s
res2: Array[(String, Int)] = Array((or,1), (not,1), (be,2), (to,2))
scala> res2.foreach(println)
(or,1)
(not,1)
(be,2)
(to,2)
```

### Standalone App  
[Spark Programming Guide]: http://spark.apache.org/docs/latest/programming-guide.html
[Quick Start]: http://spark.apache.org/docs/latest/quick-start.html#a-standalone-job-in-scala

[Getting Started with Big Data Genomics Using Scala and IntelliJ]: https://www.youtube.com/watch?v=BCoIXqUfFkU
[Setting Up IntelliJ and sbt for Scala development]: http://hanxue-it.blogspot.com/2014/06/setting-up-intellij-and-sbt-for-scala.html
[Set up a spark application development environment in Fedora]: http://blog.gluster.org/2014/07/set-up-a-spark-application-devleopment-environment-in-fedora-2/

Follow the instruction in [Quick Start],

```
~/Projects/spark/ampcamp5/ampcamp5-usb/simple-app nano simple.sbt
~/Projects/spark/ampcamp5/ampcamp5-usb/simple-app sbt package       # this will take a while
[info] Set current project to Simple Project (in build file:/Users/rkuo/Projects/spark/ampcamp5/ampcamp5-usb/simple-app/)
[info] Updating {file:/Users/rkuo/Projects/spark/ampcamp5/ampcamp5-usb/simple-app/}simple-app...
...[snip]...
info] Done updating.
[info] Compiling 1 Scala source to /Users/rkuo/Projects/spark/ampcamp5/ampcamp5-usb/simple-app/target/scala-2.10/classes...
[info] Packaging /Users/rkuo/Projects/spark/ampcamp5/ampcamp5-usb/simple-app/target/scala-2.10/simple-project_2.10-1.0.jar ...
[info] Done packaging.
[success] Total time: 332 s, completed Dec 23, 2014 12:58:49 AM
```

I don't know why, local[2] does not work under zsh; **it needs `bash` shell**, 

YOUR_SPARK_HOME = ~/Projects/spark/ampcamp5/ampcamp5-usb/spark

```
bash-3.2$ pwd
/Users/rkuo/Projects/spark/ampcamp5/ampcamp5-usb/simple-app
bash-3.2$ ls
project		simple.sbt	src		target
bash-3.2$ ~/Projects/spark/ampcamp5/ampcamp5-usb/spark/bin/spark-submit --class "SimpleApp" --master local[*] target/scala-2.10/simple-project_2.10-1.0.jar
Using Spark's default log4j profile: org/apache/spark/log4j-defaults.properties
...[snip]...
14/12/23 01:36:01 INFO TaskSchedulerImpl: Removed TaskSet 1.0, whose tasks have all completed, from pool
14/12/23 01:36:01 INFO SparkContext: Job finished: count at SimpleApp.scala:13, took 0.02046 s
Lines with a: 83, Lines with b: 38
bash-3.2$
```

## Spark Streaming

[difference streaming sources]: https://spark.apache.org/docs/1.2.0/img/streaming-arch.png
[Discretized Streams: A Fault-Tolerant Model for Scalable Stream Processing]: http://www.eecs.berkeley.edu/Pubs/TechRpts/2012/EECS-2012-259.pdf

Spark Streaming can take different streaming sources. [spark streaming doc]
![difference streaming sources]

### Use NC

### Use Kafka 

### Use Twitter
[Deep Dive with Spark Streaming - Tathagata Das - Spark Meetup 2013-06-17]: http://www.slideshare.net/spark-project/deep-divewithsparkstreaming-tathagatadassparkmeetup20130617
[Video]: http://youtu.be/D1knCQZQQnw­
[Spark Submmit 2014 Data Streaming]: https://databricks-training.s3.amazonaws.com/slides/Spark%20Summit%202014%20-%20Spark%20Streaming.pdf
[twitter stream set up]: http://ampcamp.berkeley.edu/3/exercises/realtime-processing-with-spark-streaming.html
[spark streaming doc]: https://spark.apache.org/docs/1.2.0/streaming-programming-guide.html

