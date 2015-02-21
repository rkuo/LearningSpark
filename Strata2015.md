# Strata + Hadoop World 
Feb 17–20, 2015 • San Jose, CA

## Day - 1 SparkCamp Training
* 9:00am–5:00pm Wednesday, 02/18/2015
Spark Camp: An Introduction to Apache Spark with Hands-on Tutorials

### Contents ##
 * spark - binary distribution
     * Spark Version: v1.1.0
     * Git Hash: 2f9b2bd7844ee8393dc9c319f4fefedf95f5e460
     * conf/log4j.properties - WARN used for default level, Snappy warnings silenced
 * data - example and lab data
     * graphx - graphx lab data
     * movielens - MLlib lab data
     * wiki_parquet - SparkSQL lab data
     * examples-data - examples directory from Spark src
     * join - example files for joins
 * sbt - a fresh copy of sbt (v. 0.13.5)
     * sbt-launcher-lib.bash - modified to understand non-default location of bin scripts
     * sbt.bat - modified to understand non-default location of bin scripts [Windows]
     * conf/sbtopts - modified to point to embeded ivy cache
     * conf/sbtconfig.txt - modified to point to embeded ivy cache for [Windows]
     * ivy/cache - a pre-populated cache, pointed to via conf/sbtopts
     * bin - removed and all files moved into sbt's home directory so users can run sbt/sbt similair to working with spark's source code 
 * simple-app - a simple example app to build (based on the Spark quick start docs)
 * streaming - a simple streaming application used for the SparkCamp streaming labs
 * machine-learning - the simple application used for the SparkCamp machine learning labs
 * website - the website contents for SparkCamp labs.

https://shard-class06.cloud.databricks.com/
student-195, a4c7690256b6, cluster-195

## Day - 2
### 8:45am–8:55am Thursday, 02/19/2015
Thursday Keynote Welcome, Roger Magoulas (O'Reilly Media), Doug Cutting (Cloudera), Alistair Croll (Solve For Interesting)

Learn more -> $ money

Data is everywhere, start from web search, grows into everywhere. 
Device collecting data from equipment, send data back, IoT, 

### 8:55am–9:10am Thursday, 02/19/2015
Hadoop's Impact on the Future of Data Management, Amr Awadallah (Cloudera, Inc.)

Hadoop started at 2006
We can treat it like a [Enterprise Data Hub] (process, discover, model, serve), is a smart phone for the data. Multiple in, multiple out (consume different ways). Security should be by default, Governance, Management the resource config, consumed, availibility, predicate the problem ahead...

mini-data center (hub)
[xplain] helps inferring, and help writes query
[Cask], improve images process

### 9:10am–9:15am Thursday, 02/19/2015
Close Encounters with the Third Kind of Database, Eric Frenkiel (MemSQL)

MemSQL CEO Eric Frenkiel will discuss the need for simplicity in enterprise data architecture, the convergence of transactions and analytics, and what is required to operationalize Spark and Hadoop in the enterprise.pipelines by [integrating their technology with Hadoop, and Spark] real-time transaction, more sensor, more connectivity, and more demands.
Problems: data loading, dirty, partial data.

In memory, immutable.
Spark <-> memsql
Model is in real-time, see/query data in real-time.
**Continuous Analysis and Adaptive to new situation**

### 9:15am–9:25am Thursday, 02/19/2015
Intelligence in the Age of Plethora, Lisa Hammitt (Salesforce)

Wearables/fasions contribute to Big Data and the insights are already realizing significant gains in key industries.

75 Billion devices are going online, need digest the data fast. Devices are connected, need to personalize. Phone is a extension of a person. The data between Sensors and users generate the information which was not available before. The new type of engagement will emerge. Data science helps facilitate the progress.

### 9:25am–9:35am Thursday, 02/19/2015
Impacting Business **AS it Happens**

Data drives compute
not silo
continuous ingest and go

[Myriad Project]: "Running YARN in Mesos Framework"
Batch and real-time converges -> global view in realtime

[Drill] self-service data, SQL, low barrier
MapR offers free online training. << act on this

### 9:35am–9:40am Thursday, 02/19/2015
A Bigger Lens Through which to View the World, Adam Kocoloski (IBM)

Combining advances in analytics, cloud and cognitive computing in a manner that has the potential to transform how institutions understand customers, markets and trends. 

Actionable is the key.

### 9:40am–9:50am Thursday, 02/19/2015
Data Science: Where are We Going?, DJ Patil (US Chief of Data Science)
imperical innovative way of viewing health data

Open government data as source. (http://www.data.gov/). Data scienist demand is growing. Big data report, competitiveness.
CTO, CIO, CDO important
President has a dashboard to see IT expense.

Unleash the data, max the return, share data, recruit the best the engineers.
Priority: Precision medicine, data products, responsible data scientist

[we need you, U.S. digital service] whitehouse.gov/usds

### 9:50am–10:00am Thursday, 02/19/2015
The Emerging Age of** Data-Driven Policy Design**: Examples from Trying to Manage the Global Climate, Solomon Hsiang (UC Berkeley)

Technology contribute the policy formulation. 
The public response the climate change, data science contribute the understanding of our surrendings and formulates the policy.

### 10:00am–10:10am Thursday, 02/19/2015
Data-driven Sensory Intelligence – Optimizing Our Perceptual Capabilities, Poppy Crum (Dolby Laboratories | Stanford University)

Our brain interprets the input, based on our physical limitation. When we focus too much, we miss the globel information. 
Understanding the process, so we can optimize our limitation.

environment awareness,
important of context 
feedback loop

### 10:40am–11:20am Thursday, 02/19/2015
Lessons from Running Large Scale Spark Workloads
Spark in Action, Reynold Xin (Databricks), Matei Zaharia (Databricks)

100TB sorting, 
Ten cent (8000+ nodes) largest node
use SQL for BI and ETL

Alibaba (1 week on 1PB+ data) 
extract feature
use a lot graphX
collpratove filtering
clustering
believe propogation

Understand brain, experimental data pipe into analytics and present the result to web, and use laser to kill a cell and run the experiment again. 
30min = 1TB for fish scan.
1 hour = 100TB for a mouse 

DataFrame: easier high performance as scale (v1.3)

Elastic scaling
at beginning, it is a fix resource allocation. 
Later, allocation can be reduced. (dynamic=true , max =3)

Shuffle at Scale,
Make less file openning for R, one active stream at a time.

Netty-based Network Transport

DataFrames make it easy to leverage structured data, compact, colum-oriented storage, Rich optimiztion via Spark SQL

Domain-specific function.
R and Panda, 
Read/fwrite to Hive, JSon, Parquet, ORC, Pandas,

performance DF > Scala > Python
end 2 end optimization

### 11:30am–12:10pm Thursday, 02/19/2015
From Source to Solution: Building A System for Machine and Event-Oriented Data, Eric Sammer (ScalingData)

Glue, How to handle terabytes an hour of event-oriented data, providing real time streaming, search, and SQL access to data?

 >1TB per hour, end to end latency, sub-second
Quality of Service - transaction is fast enough
Fraud detection - 
forensic diagnostic
Security

Flow from input to UI/impala,
avro event (use kafka) a general topic to allow user to select.

spark download
http://www.apache.org/dyn/closer.cgi/spark/spark-1.2.1/spark-1.2.1-bin-hadoop2.4.tgz
Dockerfile for spark,
https://github.com/beniyama/sparkr-docker/blob/master/Dockerfile

### 1:30pm–2:10pm Thursday, 02/19/2015
Using Multiple Persistence Layers in Spark to Build a Scalable Prediction Engine, Richard Williamson (Silicon Valley Data Science)

Experimental Science, 
cluster with low cost hardware, try new Raspberry Pi,

Volume-longer period history
Velocity-streaming
Variety-additional features
search github for example-build a scalable predictable engine

investigate Parquet in impala interactively.

Load Cassandra from Kafka,
MADlib or Spark MLlib 
PMML for predict modeling, 

### 2:20pm–3:00pm Thursday, 02/19/2015
Building Adaptive Apps with APIs and Data
Machine Data / IoT, Anant Jhingran (Apigee)

Analyze the API use/traffic for better design the application.

### 4:00pm–4:40pm Thursday, 02/19/2015
Spark Streaming - The State of the Union, and Beyond. Tathagata Das (Databricks)

"Streaming" Data applications
High level API, Unified API, Ease to operate, Fault Telerent, Integration
for real-time, 

Steps:

1. DStream
2. set up how to be done
3. Start(), triggers the action

any language, interface with other Spark component, take data off to shell then process it.

-> ML

-> SQL

Target for performance, there is no order guarranttee, use time-stamp to ensure order for now.
	* Development
		* python in 1.2, support Karfa, continues learn-Streaming MLlib, Streaming kmean, 
		* infrastructure, driver, graceful shut down (1.0), write ahead log for zero data loss (1.2), core uplefting other components, central package site.
	* Adoption-40% using Spark Streaming in production. 80+ deployment, Intel, Pearson learning (using Kafka for input), sharethrough (Kinesis -> Spark + Meson + Marathon), Netflix, Pinterest, Neuroscience,...responsive to failure (crazy monkey for ensure agile)
	* Roadmap
		* Libraries,
			* ML
			* better flow control 
			* elastic scaling
			* Cross-version
			* improve non-hadoop system

### 4:50pm–5:30pm Thursday, 02/19/2015
Visualization
online serive- [manyeyes](http://www-969.ibm.com/software/analytics/manyeyes/#/), 
www.vizipedia.com

book: visualization financila data from wiley.

**Patterns**

* Comparison: Attributes, Time, Rank
* Connection: Drill down, Flow, Grouping, Network,
* Conclusion: Calculation, Correlation and Predication

Attributes: Understanding the characteristics of an object
Break the face into various attributes, eyes, ears, ...
Use fish as way to profile the market

Question: I need to see what has occurred. 
Time: Tracking events as they unforld over time

Question: I need to see who is landed on top
Rank: Establishing relationships of great, less

Connections:
Question: I need to see both aggregate and details
Drill Down: shifting form summary to detial information

Question: I need to see the influence and impact
Flow: Transforming data from one stage to another.

Question: I need to see major themes
Grouping: Based on performance then aggregate into another dimension

Network:Connecting the dots between discrete location

Question: I need to see the level of correlation
Correlations: Discovering congruency between data sets.

Question: I need to foresee the possibilities
Prediction: Predicating ouputs based on learned inputs

## Day 3

### 8:50am–9:00am Friday, 02/20/2015
Data: Open for Good and Secure by Default, Eddie Garcia (Cloudera)

More data sources create more opportunity for risk.
Securing all data, including open source data, e.g. opendata,...
Data self-contains properties that allows system to secure its condentiallity and integrity. 

We need to consider performance, technology exists.

### 9:00am–9:05am Friday, 02/20/2015
Year Zero: How We’ll Run Our Lives in Ten Years’ Time
Alistair Croll (Solve For Interesting)

Noun Project
No boby should know about you than you.
It is land grab now. 
Agent: unticipate search.

Roughly every decade, some kind of military or enterprise technology makes its way into the mainstream: the personal computer; the consumer Internet; the mobile phone; the Internet of Things. What happens when Big Data turns into a consumer product? Strata chair Alistair Croll offers some speculation about what data will do to the way we live, love, work, and play. Read more.

### 9:05am–9:10am Friday, 02/20/2015
Intel and the Role of Open Source in Delivering on the Promise of Big Data, Michael Greene (Intel)

Secure and need to be analyze it, silicon chip provides some assistance to power.
Intel provides some $ to Amplab and Databrick. 

### 9:10am–9:25am Friday, 02/20/2015
Big Data Lessons from Our Cybernetic Past, Eden Medina (Indiana University, Bloomington)

Stafford Beer provided assistance to the system design.

Learning from the past, older technologies can provide the inspiration.
Design a system to sense the industry.
Sybersyn from Chile, socialist to manage society resources. An early form of Algorithm ??

be vigilant about bias in system design.

### 9:25am–9:35am Friday, 02/20/2015
New Directions for Spark in 2015, Matei Zaharia (Databricks)

grow from 150-500 contributors
lines 190k-370k

sort 100TB
2013 use 2100 machine in 72 min
2014 use 207 machines in 23 minutes in public cloud

Data Science, high level interfaces > dataFrames (R and Pandas), automatically optimizaed, 
Platform interface

1.4 (June) R interface, directly from R

External data source, can combine different types of data.
Sources, workloads, environments.

### 9:35am–9:40am Friday, 02/20/2015
Agile Data in the Cloud Era: A New Approach, Roman Shaposhnik (Pivotal)

Open Source << check these 
ASF
ODP
- between vendors,
- focus on developoing platform, rather than projects

### 9:40am–9:50am Friday, 02/20/2015
Charting a Path Forward: The Future of Data Visualization, Jeffrey Heer (**Trifacta** | University of Washington)

Rethink UI for data, consider explode is part of function.
Automatic choose the data 
Data Voyager << investigate

From Specification Exploration
From Designers to Decision Makers
From Design variation to Data variation.

May be we need to ask question differently.

### 9:50am–10:00am Friday, 02/20/2015
Cow? Joseph Sirosh from Microsoft

**Every company is a data company.**
monitor cow from behavior to predict the diaseater.
IoT is not just from Machine.

Strataconf.com event.

### 10:40am–11:20am Friday, 02/20/2015
Architecting Interfaces that Learn, Tye Rattenbury (Trifacta), Jeffrey Heer (Trifacta | University of Washington)

auto complete
info card,
statistic of language,

share objective

good IDE, feedback loop, understand the world you live in.
action space is very big, correctness depend on context, coordination is context-dependent.

-> Learn the situations (people, data, contexts) where actions are predicatble.
-> Learn the evolution of these situration. 

example: read json, understand it and parse it, to get structure.
understand the type of data per field.

allow user to intercept/add the SQL tool to parse differently.

Approach:
- start with good set of rules and priors
- track as much user history and context as possible
- train ML models that connect history & context with user input to improve action predictions
- design the presentation of predictions
- desing mchanism to modify/overrule predications.

Architecture Supports

interface - user event logs - ML - 
Multi-Views to Multi-Model
Learning Coordinator to generate common context.

Action constructs help the users too. 
Listen for predication triggers
Allow users to collect the data with online tools. cache the data for analysis
Do not block UI thread
track user selection, so it can be analyze again.
Log user events, so we can rebuild user state

intelligent software that incorporates learning to make the process of transforming data more intuitive and efficient.

Boot the truth initially, use proxy objectives as partial truth.
Observe User Actions over time.
We can use both implicit/explicit query from user

Distingusihg epistermic form proagmatic action
User events are not created equal.
Context Matters

Ultimate objective is user success.
requires qualitative, and well as quantitative data

give bad recommendation is ok too, so user can correct it
proactive wrangling (shared objectives and coordinations)

### 1:50pm–2:10pm Friday, 02/20/2015
Velox: The Missing Piece in the Predictive Analytics Stack, Daniel Crankshaw (UC Berkeley)

Why? Spark lacks of Model to serving connection
Rating vs Song for forecast
Training data, (CastD, song, rating)
 -> HDFS + Techyon -> mySQL for webservices
 
Model and mySQL is not connected. Problem:Staleness of model, which is not design for serving.
Velox consists of Model manager + predication 

Frontend.js interfaces with Velox, and personalized. 
 
There are APIs to interface web UI.

Personalized split model
- shared model (batch)
- personalized model (online)

Mathematic model <- linear

### 2:20pm–3:00pm Friday, 02/20/2015
YARN vs. MESOS: Can’t We All Just Get Along? Ted Dunning (MapR)

YARN 
Monolithic scheduling,
Pre-defined resources

Mesos
- Two level scheduling
	- bottom levle is app specific
	- frameworks to ease complecity
	- offer, return
- Actor based, 
	- fast
- Marathon, Chronos
- User define resources
- native support 

Myriad intergrate the needs
- Mesos can start X cluster (X can be YARN, Webservice, ..)
- YARN is cluster and Hadoop to do persistance
- Data localization, universal name space
- YARN can not do versioning,
- Resource slosh

 


