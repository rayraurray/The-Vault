[[Hadoop]]

The Hadoop Ecosystem is a collection of open-source tools that complement core Hadoop ([[Hadoop Distributed File System]] and [[MapReduce]]). It is designed to handle large-scale data storage, processing, integration, and analysis.

**Three Integration Models:**
- Built directly on HDFS.
- Built on HDFS + MapReduce.
- Integrates indirectly or supports Hadoop environments.

---

![[Pasted image 20250512133123.png]]

![[Pasted image 20250512133659.png]]

---

# Data Storage

It's ***HBase*** (Hadoop Database) time.

NoSQL, column-oriented distributed database.
**Ideal for:**
    - Random read/write access.
    - Very large, sparse datasets.
**Key Features:**    
    - High write throughput (scales to 100K+ inserts/sec).
    - Only the row key is indexed.
    - Limited operations (get/put/scan).


***HBase vs Relational Database***

| Features              | Relational DB                    | HBase                                |
| --------------------- | -------------------------------- | ------------------------------------ |
| Data Layout           | Row-oriented                     | Column-oriented                      |
| Transactions          | Yes                              | Single Row Only                      |
| Query Language        | SQL                              | Get/put/scan or using Hive or Impala |
| Security              | Authentication and Authorization | Kerberos Protocol                    |
| Indexing Method       | Any column                       | Row-key Only                         |
| Maximum Data Size     | Terabytes                        | Petabytes+                           |
| Read/Write Throughput | Thousands                        | Millions                             |

**When to Use What?**

- **HDFS**: Best for append-only, scan-heavy operations.
- **HBase**: Use when random access is needed.
- **RDBMS**: Ideal for complex transactions and real-time queries.

---

# Data Integration

## 1. Flume
***Apache Flume*** is a service that *moves large amounts of data in real-time.* 

Collects and transfers large volumes of streaming data to HDFS or HBase as it is generated after batch processing.

**Characteristics:** 
- Distributed
- Reliable and available
- Horizontally Scalable
- Extensible

**Architecture:**
- **Source** → **Channel** → **Sink**
- Supports custom sources and sinks (e.g., Twitter, log files).

![[Pasted image 20250512135425.png]]
*Apache Flume pulling logs from multiple sources and shipping them to Hadoop, Apache HBase and Apache Spark.*

![[Pasted image 20250512135534.png]]
**Important parts of flume:**
- Data generating sources.
- The Flume agent.
- The destination or target.

## 2. Kafka
An ***open source distributed, high-throughput messaging platform developed by [[LinkedIn]]*** to handle real-time data.

*Publisher-subscriber model*; stores streams as **topics** with multiple **partitions**.

Kafka stores, reads and analyses the streaming data where developers and users contribute the coding updates.

![[Pasted image 20250512135934.png]]
**Use Cases:**
- Activity tracking
- Stream processing
- Real-time analytics
- Log aggregation

![[Pasted image 20250512135853.png]]
*Kafka’s simple structure ensures its reliability, durability, and performance.*

| Features           | Flume                                                                                                                                                                                                                                                                                    | Kafka                                                                                                                                                                                                                                                                                                                                                                                        |
| ------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Meanings           | A tool to collect log data from distributed web servers.                                                                                                                                                                                                                                 | Runs as a cluster and handles incoming high volume data streams in real-time.                                                                                                                                                                                                                                                                                                                |
| Concepts           | - Capable of taking in streaming data from multiple sources for storage and analysis for use in HBase or Hadoop.<br>- Ensures guaranteed data delivery because both the receiver and sender agents evoke the transaction to ensure guaranteed semantics.<br>- It can scale horizontally. | - Treating each topic partition as an ordered set of messages.<br>- Based on publish-subscribe architecture and does not track the identity of subscriber/publisher.<br>- Retaining all messages or data as logs where subscribers are responsible to track the location in each log.<br>- Capable of supporting large number of publishers and subscribers and store large amounts of data. |
| Basic of Formation | Flume is a service or tool for<br>gathering data into<br>Hadoop/HBase/SPARK.                                                                                                                                                                                                             | Kafka is an efficient, faulttolerant and scalable<br>messaging system.                                                                                                                                                                                                                                                                                                                       |
| Application Areas  | - Process transaction logs in application servers, web servers, etc.<br>- For example, e-commerce, online retail portals, social media, etc.                                                                                                                                             | - Monitor data from distributed applications.<br>- Make data available to multiple subscribers based on their interests.<br>- Log aggregation service.                                                                                                                                                                                                                                       |
| Approach           | - Need to gather big data either in streaming or in batch mode from different sources. <br>- Efficient when working with logs.                                                                                                                                                           | - Kafka is required to efficiently process real-time data streams without data loss.<br>- Need to ensure data delivery even during machine failures, hence it is a fault-tolerant system.                                                                                                                                                                                                    |
# Bridging RDBMS with HDFS
It's le time for ***Sqoop*** - "SQL to Hadoop"

Sqoop facilitates import/export of structured data between RDBMS and HDFS. Supports JDBC, ODBC, and several specific databases. Commonly used with MySQL, Postgres, Oracle, etc.

**Custom connectors for:**
- MySQL
- Postgres
- Netezza
- Teradata
- Oracle (partnered with Quest Software)

Not open source, but free to use.

---
# Data Processing
Finally, we get to ***Apache Spark*** - *Cluster computing engine with in-memory processing.*

Spark is a fast, general engine for large-scale data processing on a cluster. Originally developed at UC Berkeley’s AMPLab, it is an open source Apache project that provides several benefits over MapReduce.

**Supports:**
- Batch processing
- Streaming
- Machine Learning
- Graph computations

**Languages:** Python, Scala, Java.

**Benefits over MapReduce:**
- Faster
- Better suited for iterative algorithms
- Can hold intermediate data in RAM, resulting in much better performance.
- Easier API 
- Supports real-time streaming data processing

| Feature   | Spark                            | MapReduce            |
| --------- | -------------------------------- | -------------------- |
| Execution | In-memory                        | Disk-based           |
| Latency   | Low                              | High                 |
| APIs      | Rich APIs (RDDs, Datasets)       | Basic Map and Reduce |
| Streaming | Native support (Spark Streaming) | Add-on tools needed  |
# Data Analysis
MapReduce is powerful but hard to master. To solve the mass skill issue, we have ***Hive and Pig*** - Languages for querying and manipulating data.

Both are open source Apache projects. (Hive is initially developed at Facebook, Pig is initially developed at Yahoo!) that leverage existing skillsets. The interpreter runs on a client machine.

> *i don't think anyone uses these anymore, even MapReduce became redundant, but it's good to know i guess.*

## 1. Apache Hive
SQL-like querying on Hadoop (HiveQL). Stores metadata in a **metastore** (e.g., MySQL).

**Example:**
```sql
SELECT * FROM users WHERE region_code > 2 ORDER BY UID;
```

## 2. Apache Pig

Dataflow scripting language - ***Pig Latin***. Great for ETL operations and transforming large datasets.

**Example:**
```pig
purchases = LOAD '/user/ret01/purchases' AS (itemID, price, storeID, purchaserID);

bigticket = FILTER purchases BY price > 1000;
```

| Features            | Hive                                        | Pig                                   |
| ------------------- | ------------------------------------------- | ------------------------------------- |
| Language            | HiveQL (SQL-like)                           | Apache Pig (Dataflow language)        |
| Schema              | Table definitions stored in a **metastore** | Schema optionally defined at runtime. |
| Programmatic Access | JDBC, ODBC                                  | PigServer (JavaAPI)                   |
## 3. Impala
***For high performance queries.*** Ideal for *real-time analytics on HDFS.*

High-performance SQL engine for vast amounts of data. Similar query language to HiveQL, but 10 to 50+ times faster than Hive, Pig, or MapReduce. SQL query engine runs on Hadoop Clusters. Data stored in HDFS, it does not use MapReduce 

Developed by **Cloudera**, 100% open source, released under the Apache software license.

## 4. When to Use What?
![[Pasted image 20250512154123.png]]
- **Impala**: Structured data + fast SQL queries.
- **Hive/Pig**: Semi-structured data, long batch jobs.

# Workflow and Machine Learning
## 1. Apache Oozie
***Workflow scheduler system*** to manage Hadoop jobs.  Supports dependency management and job coordination (MapReduce, Hive, Pig, etc.)

It defines the dependencies between jobs. The Oozie server submits the jobs to the server in the correct sequence.

![[Pasted image 20250512154548.png]]
## 2. Apache Mahout
***Scalable machine learning library*** written in Java..

**Includes algorithms for:**
- Collaborative filtering. (Recommendations)
- Clustering (Finding naturally occurring “groupings” in data).
- Classification (determining whether new data fits a category)