Approach: 

* It is difficult to review something without reference point. I am taking advantage of knowing a little bit Hadoop and Spark and will use them as reference point for review. This report is more in comparison than just a overview. For overview only, please just read the first half of the report. 

Disclaimer:

* I have never used Flink before, so all information about Flink is based on web research. I currently use Spark, but not in production level.
* Biases: emphysize real-time streaming compute and ML analytics, usability and adaptation is just as important as computing speed and memory saving.  

# Apache Flink vs Spark
Date of study: April 14, 2015

* Both Flink and Spark use Hadoop's file distribution system for distributed file storage.
* Both systems use Scala as core development language.

## [Flink](https://flink.apache.org/) 

![Flink][3]

### Initial Development and License, 
Original name: Stratosphere 
Stratosphere was a research project whose goal is to develop the next generation Big Data Analytics platform. The project includes universities from the area of Berlin, namely, TU Berlin, Humboldt University and the Hasso Plattner Institute.

It has been renamed as Flink and under Apache 2 license now.

### Architecture
![Flink Architecture][4]

### Language Support
Java and Scala, no Python yet.

### Development Momentum
Contributor: 86
![github activity - Flink][2]

### Pros and Cons
#### Pros
* Fairly active development community.
* Flink optimizer inspects the data and cluster characteristics and makes many of memory tuning decisions automatically.

#### Cons
* only Java and Scala functional APIs at the moment.
* It has less library support than Spark.

## [Spark](https://spark.apache.org/)

![Spark logo][6]
### Initial Development and License 
It was developed at AMPLab at UC Berkerley, then few developers left Berkerly and started DataBrick Company. It is under Apache 2 license.

### Architecture
![Spark Architecture][5]

### Language Support
Java, Scala, Python and R

### Development Momentum
Contributor: 488
![github activity - Spark][1]

### Pros and Cons
#### Pros
* One of most active projects in github. Currently, Spark has 5 more times of contributors than Flink. Spark also has very strong support from business community. 
* Spark optimized index-based graph processing (GraphX), as well as a large library of machine learning algorithms (MLlib).
* Spark supports Java, Scala, Python, R (in development), SQL, and HiveQL. This is very big plus for Spark; there are very large amount of research has been done in Python and R. 
* It works with Mesos and leverage its resource scheduling system.
* Spark created very large ecosystem, which provides many productivity tools, visualization, notebook.

#### Cons
* Spark is not the fastest Big Data compute engine in the market; Dato (formally graphLab), developed in C++ is faster than Spark. In some batch mode use cases, Flink is faster than Spark.

## Summary Table

| Item 				| Flink			 		| Spark              |         
| :-------------- 	| :------------------ | :----------------- |
| License | Apache 2 | Apache 2 |
| API language | Java, Scala | Java, Scala, R, Python |
| Development | fairly good size | very big development community |
| Initial dev | a group universities at German | UC Berkerley |


[1]:http://note.io/1ysmhuW
[2]:http://note.io/1FRZbO6 
[3]:http://photos2.meetupstatic.com/photos/event/4/6/b/6/global_413778102.jpeg
[4]:http://note.io/1CY2a3k
[5]:http://note.io/1ypwR5H
[6]:https://encrypted-tbn3.gstatic.com/images?q=tbn:ANd9GcSp1jRzjxMnTaJf12g37SHUMsOxVC2UWeqK0zPh_uOUMR4D_2QM
