# AMPLab Camp 5 Self Study

## Online Resources
- [Slide, Video](http://ampcamp.berkeley.edu/5/)
- [Getting Started With Your USB Stick](http://ampcamp.berkeley.edu/5/exercises/getting-started.html)

### Compare Hadoop Distribution
Possible use this vm as base:

- [Compare Hortonworks, Cloudera and MapR](http://www.experfy.com/blog/cloudera-vs-hortonworks-comparing-hadoop-distributions/), Hortonworks is free, Cloudera has 60 days free trial. MapR uses its own file system to replace HDFS.
- [What are the core differences between Cloudera's hadoop distro and HortonWorks distro?](http://www.quora.com/What-are-the-core-differences-between-Clouderas-hadoop-distro-and-HortonWorks-distro)
- [Hortonworks vagrant](http://hortonworks.com/blog/building-hadoop-vm-quickly-ambari-vagrant/) based on the verson Feb 2014, Works.

## Test Labs Installation
- Add a note file `amplab_camp_5_self_study.md` (this file)

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