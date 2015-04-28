![sqrrl icon]

Sqrrl Data, Inc. is an American enterprise software company specializing in Big Data analytics and cyber security founded in 2012. Headquartered in Cambridge, MA. 

Sqrrl was founded by former computer scientists from the U.S. National Security Agency.[[1]]. At college job fair’s, which is where Adam Fuchs, 32, discovered the agency and joined at 21. He now is the chief technology officer at Sqrrl, a NoSQL secure data base startup powered by Apache Accumulo, an open source platform Fuch’s worked on while it was being hatched at the NSA. Accumulo was an NSA in-house database constructed as an open source platform to serve certain sectors of the agency. Work on Accumulo at NSA began in 2008, and today it is the backbone of Sqrrl. Another Sqrrl’s co-founder Ely Khan, who worked closely with NSA teams during his stint as a National Security adviser at the White House[[2]]. 

They are serious. 

**sqrrl Enterprise** (commercial) is built on top **Apache Accumulo** (free and open source); we will use two separate terms to refer these two packages in this report.

## Accumulo
[Apache Accumulo] is sorted, distributed key/value store with cell-based access control and customizable server-side processing. It is based on [Google's BigTable design] and is built on top of Apache Hadoop, Zookeeper, and Thrift. 

Apache Accumulo features a few novel improvements on the BigTable design in the form of cell-based access control and a server-side programming mechanism that can modify key/value pairs at various points in the data management process.

Features:

* Cell-based (combining column and row) access control, 
* Large Rows: When reading rows, there is no requirement that an entire row fits into memory.
* Namespaces: The concept of table "namespaces" was created to allow for logical grouping and configuration of Accumulo tables.
* Volume support: Accumulo 1.6.0 migrated away from configuration of HDFS by using a single HDFS host and directory, to a collection of HDFS URIs (host and path) which allows Accumulo to operate over multiple disjoint HDFS instances. 
* Master fail over: Multiple masters can be configured. 
* Isolation: Scans will not see data inserted into a row after the scan of that row begins.
* ... [long version of Accumulo features]

### Architecture

![Accumulo architecture]

### Data Model
Its logic column composed mulitple physical columns.

![Accumulo data model]

### Performance
From [Accumulo Summit 2014: Benchmarking]
![Accumulo performance - read]
![Accumulo performance - write]

### Platform and Inter-Operatiblity

* [Apache Accumulo], with its cell-level security, is used in high-security NoSQL use cases, which is supported by both Hortonwork and Cloudra big data platforms. 

![hortonworks platform]

* Apache Spark support Accumulo and can transform its data to form RDD (Resilent Distributed Dataset), which is very critical factor. 

* Mesos can deploy Yarn, Cloudera, and Accumulo, which can make Accumulo as part of enterprise data eco-systems.

## Sqrrl Enterprise 
Since sqrrl enhanced Apached Accumulo and it is part of more complete solution, its architecture is depicted below.

### Architecture

![sqrrl architecture]

### Property Graph 
It uses property graph for linked data approach, which increases its flexibility.

![sqrrl linked property]

### Workflow
It supports full life cycle data analytics.

![sqrrl flow]

## Links
[sqrrl icon]:http://insidebigdata.com/wp-content/uploads/2013/10/sqrrl_logo.jpg
[sqrrl architecture]:http://sqrrl.com/media/SQR_Diagrams-03.jpg
[1]:http://en.wikipedia.org/wiki/Sqrrl
[2]:http://venturebeat.com/2014/05/01/born-in-the-nsa-former-spies-are-starting-companies-all-over/
[Google's BigTable design]:http://static.googleusercontent.com/media/research.google.com/en/us/archive/bigtable-osdi06.pdf
[Apache Accumulo]:https://accumulo.apache.org/
[hortonworks platform]:http://hortonworks.com/wp-content/uploads/2014/03/11.png
[long version of Accumulo features]:https://accumulo.apache.org/notable_features.html
[Accumulo Summit 2014: Benchmarking]:http://www.slideshare.net/AccumuloSummit/10-30-drob?qid=c2004d6b-b2af-4dc4-9e83-4509d7e16ca3&v=qf1&b=&from_search=5
[Accumulo performance - read]:http://note.io/1JxXZU2
[Accumulo performance - write]:http://note.io/1GsTWCe
[Accumulo architecture]:http://www.rosebt.com/uploads/8/1/8/1/8181762/501368_orig.png
[Accumulo data model]:http://accumulo.apache.org/user_manual_1.3-incubating/img1.png
[sqrrl linked property]:http://sqrrl.com/media/OutSolution-copy-1024x569.png
[sqrrl flow]:http://sqrrl.com/media/SQR_Diagrams_2-01.png
