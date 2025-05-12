[[Hadoop Distributed File System]]

The word is ***Parallel Processing***
# Definition

Hadoop MapReduce is the processing component of Apache Hadoop. It processes data parallelly in distributed environment.

MapReduce is used for **processing and analyzing large volumes of data in a distributed and fault-tolerant manner**. Its strength lies in handling **batch-oriented, parallelizable** data processing tasks.

---

## 1. Core components
- HDFS for storage
- YARN (MapReduce v2) for resource management and job scheduling (NameNode/DataNode, ResourceManager/NodeManager)

## 2. Functions
- Map()
- Reduce()
😀

## 3. Design patterns
- Summarization (e.g. inverted index)
- Classification (top-$N$ records)
- Recommendation (sort)
- Analytics (joins, selections, etc.)

## 4. Advantages
- Parallel processing at data-locality (code moves to data) reduces network I/O
- Demonstrated via a financial-report case study comparing raw-data vs. local summarization approaches

---
# Common Use Cases

## 1. Log Analysis

Analyze web server logs (e.g., Apache or Nginx) to find:
- Most accessed URLs
- Peak traffic hours
- IP address frequency

**Why MapReduce?** Logs are often huge and distributed; MapReduce processes them in parallel.

## 2. Social Network Analysis

- Analyze relationships, connections, and influence metrics in social graphs.
- Compute metrics like PageRank or common friends or friend recommendations.

This is performed based on set operation. In set theory, a set is defined as a collection of some objects. For example: $M = \{a, b, c, f\}$ and $N = \{b, e\}$ .

| Union                                | Intersection                         |
| ------------------------------------ | ------------------------------------ |
| ![[Pasted image 20250512131723.png]] | ![[Pasted image 20250512131821.png]] |
| $M \cup N = \{a, b, c, e, f\}$       | $M \cap N = \{b\}$                   |
## 3. Data Warehousing & ETL (Extract, Transform, Load)

- Convert raw data into structured data.
- Clean, transform, and aggregate data from multiple sources.

**Example**: Cleaning and summarizing retail sales data before inserting into a data warehouse.
## 4. Search Indexing

Powering the backend of search engines by:
- Parsing large document sets
- Extracting keywords
- Building inverted indexes (word → list of documents)

## 5. Machine Learning Preprocessing

Preprocessing large datasets before training:
- Feature extraction
- Normalization
- Grouping and aggregating data points

Note: Actual ML model training is often handled by more specialized tools like Spark or TensorFlow.

## 6. Financial Risk Modeling

Analyze transaction data for:
- Fraud detection        
- Credit scoring
- Risk analysis    

## 7. Genomic and Scientific Data Processing

- Analyze DNA sequences, protein structure data, or climate models.
- Extremely large datasets make parallelism crucial.
# Anatomy

![[Pasted image 20250509174358.png]]

![[Pasted image 20250509174442.png]]

![[Pasted image 20250509183530.png]]

![[Pasted image 20250512125814.png]]
