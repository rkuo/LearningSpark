# Presentation Notes for Spark Introduction  

## Describe the meeting intent
- share study notes
- to increase awareness, not to become an expert
- not a official report

## Introduce Hadoop and Hortonworks
- distribute data computing, two components; **Distributed data storage**, **MapReduce**, with many different layers and tools, ![Multi-layers and Tools of Hadoop Ecosystem], 
- and which can be classified as 

![Hadoop Ecosystem Classification]

[Hapdoop Ecosystem]: https://codemphasis.files.wordpress.com/2012/08/hadoop-architecture.jpg?w=595
[Hortonworks Components]: http://hortonworks.com/wp-content/uploads/2014/10/HDP2.2.Components-1024x443.png 
[Hadoop Ecosystem Classification]: https://www.evernote.com/shard/s302/sh/ccd6ccb1-18a8-47f3-9732-2abc8e6b7da3/2fe039abce28e561fe6460f6305d52fd/deep/0/PowerPoint-Slide-Show----hadoopecosystem-13355714879823-phpapp01-120427192449-phpapp01.ppsx-(Read-Only)-.png
[Multi-layers and Tools of Hadoop Ecosystem]: http://3.bp.blogspot.com/-5fGDsRurMlc/VCcLiujQ4TI/AAAAAAAAAew/r2qikUJXzyY/s1600/Hadoop%2BEcosystem.png

### Compare Hortonworks, Cloudera, MapR and Intel
Many tools ecosystems/distributions around Hadoop, from this diagram, you can see its complexity, Hadoop's ecosystem can be overwhelming, ![Hortonworks Components]

A comparison ![compare Hadoop data platform].
[compare Hadoop data platform]: http://images.techhive.com/images/article/2014/06/hadoop-distib-100341967-large.idge.gif

### Overview of Hadoop and its components, Open Hortonworks VM web,
*skip vm* use UI example - ![Hadoop Ambari screen shot]

[Hadoop Ambari screen shot]: http://hortonworks.com/wp-content/uploads/2013/03/ambari_dashboard.gif

## Overview of Spark

### History, Components, and relationship to Hadoop
- Started as a research project at the UC Berkeley AMPLab in 2009, and was open sourced in early 2010.
- After being released, Spark grew a developer community on GitHub and entered Apache in 2013 as its permanent home.

### Main Components


### why Spark?
- is a real-time data processing framework that runs in memory 
- can be set up on a Hadoop (YARN and HDFS) cluster or standalone,
- provides parallel, in-memory processing, whereas traditional Hadoop is focused on MapReduce and distributed storage. 
- can do map and reduce much faster than Hadoop can, other operations that are not in Hadoop.

[why Spark]: http://www.javaworld.com/article/2360185/big-data/straight-talk-on-apache-spark-and-why-you-should-care.html

### programming concept

#### RDD
- Resilient Distributed Datasets (RDDs) are basic building block.
Distributed collections of objects that can be cached in memory across cluster nodes.
Automatically rebuilt on failure.
- RDD operations
	- Transformations:  Creates new dataset from existing one. e.g. Map.
	- Actions:  Return a value to a driver program after running computation on the dataset. e.g. Reduce.

[Spark Architecture sequence diagram]: http://www.programering.com/a/MTO5QDNwATM.html
[Resilient Distributed Datasets: A Fault-Tolerant Abstraction for In-Memory Cluster Computing]: https://www.cs.berkeley.edu/~matei/papers/2012/nsdi_spark.pdf
[An Architecture for Fast and General Data  Processing on Large Clusters]: http://www.eecs.berkeley.edu/Pubs/TechRpts/2014/EECS-2014-12.pdf 

#### MapReduce
- Computation tree, use foldLeft example in ![foldLeft diagram] to describe reduce.  
- do `foldLef` command in CLI

[foldLeft diagram]: https://joelneely.files.wordpress.com/2008/04/foldlfoldr1.jpg?w=597&h=300

```
val l = List(1, 2, 3)    // List = constructor

println (l.foldLeft(1)(_ + _))    // (((1 + 1) + 2) + 3) = 7     <=== z = 1 op = +
println (l.foldLeft(1)(_ * _))    // (((1 * 1) * 2) * 3) = 6
println (l.foldLeft(2)(_ * _))    // (((2 * 1) * 2) * 3) = 12           <=== z = 2 op = *

def f1(x: Int, y: Int) = x + y

println (l.foldLeft(1)(f1))       // (((1 + 1) + 2) + 3)    <=== z = 1 op = f1

def f2(x: Int, y: Int) = 2 * (x + y)

println (l.foldLeft(1)(f2))       // (((1 + 1) * 2 + 2) * 2 + 3) * 2   <=== z = 1 op = f2
```

- a complex formula as example for the tree

- supporting languange, Scals, refering old slide in tech-talk 14. 

## Demo
- Word Count (file with two lines-"to be or not to be"), illustrates MapReduce ![RDD example-to be or not to be]

**switch to AMPCamp Self Study** 
In spark-shell, 

```
sc
val lines = sc.textFile("../hamlet.txt")
lines.count()
lines.flatMap(line => line.split(" "))
res6.map(word => (word,1))
val wordCounts = lines.flatMap(line => line.split(" ")).map(word => (word, 1)).reduceByKey((a, b) => a + b)
wordCounts.collect()
res2.foreach(println)
```


[RDD example-to be or not to be]: https://www.evernote.com/shard/s302/sh/4df5e6e7-2b4d-4718-a31f-766b12507f4d/498be907662449304875ee489d83489c/deep/0/win7--Running-.png

- Streaming

Spark Streaming can accept streaming from many different sources.

![Apache Spark Streaming]

then it breaks the stream into small batches, ![break a stream into small batches with time interval] the time interval is controllable. 

[Apache Spark Streaming]: https://spark.apache.org/docs/0.9.0/img/streaming-arch.png
[break a stream into small batches with time interval]: https://spark.apache.org/docs/latest/img/streaming-flow.png

Import library and create a ssc,

```
import org.apache.spark._
import org.apache.spark.streaming._
import org.apache.spark.streaming.StreamingContext._
val conf = new SparkConf().setMaster("local[2]").setAppName("NetworkWordCount")
val ssc = new StreamingContext(conf, Seconds(1))
```
Create RDD, 

```
val lines = ssc.socketTextStream("localhost", 9999)
```

Map,

```
val words = lines.flatMap(_.split(" "))
val pairs = words.map(word => (word, 1))
```
Reduce,

```
val wordCounts = pairs.reduceByKey(_ + _)
```
Print or display,

```
wordCounts.print()
```
To start the actual count,

```
ssc.start()             // Start the computation
ssc.awaitTermination()  // Wait for the computation to terminate
```
To run the program in `spark` directory,

```
./bin/run-example streaming.NetworkWordCount localhost 9999
```

Start another terminal-2 and enter data stream, 

```
~/Projects nc -lk 9999
hello world
this is richard
to be or not to be
```


## Architecture
- review realtime and batch
- layers, 
- container

