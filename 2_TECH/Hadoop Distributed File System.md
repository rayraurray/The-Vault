The [[Hadoop]] Distributed File System (HDFS) is a distributed file system designed to run on commodity hardware. It has many similarities with existing distributed file systems. However, the differences from other distributed file systems are significant.

---

- HDFS is **highly fault-tolerant** and is designed to be deployed on **low-cost hardware**.
- HDFS provides **high throughput access to application data** and is suitable for applications that have large datasets.
- HDFS **relaxes a few POSIX requirements** to enable streaming access to file system data.
- HDFS was originally built as infrastructure for the **Apache Nutch web search engine** project. HDFS is **now an Apache Hadoop subproject**.
- HDFS is designed more for **batch processing rather than interactive use** by users.
- HDFS applications need a **write-once-read-many** access model for files.

---
# Assumptions and Goals
## 1. Hardware Failure
- Hardware failure is the norm rather than the exception.
- Large scale of components with non-trivial failure probability. 
- Detection of faults and quick, automatic recovery from them is a core architectural goal of HDFS.

## 2. Streaming Data Access
- HDFS is designed more for batch processing rather than interactive use by users.
- The emphasis is on high throughput and high latency of data access.

## 3. Large Data Sets
- A typical file in HDFS is gigabytes to terabytes in size. Thus, HDFS is tuned to support large files.
- It should provide high aggregate data bandwidth and scale to hundreds of nodes in a single cluster.
- It should support tens of millions of files in a single instance.

## 4. Large Data Sets
- A typical file in HDFS is **gigabytes to terabytes** in size. Thus, HDFS is tuned to support large files.
- It should provide **high aggregate data bandwidth** and scale to hundreds of nodes in a single cluster.
- It should support **tens of millions of files** in a single instance.

## 5. Simple Coherency Model
- HDFS applications need a **write-once-read-many access** model for files. A file once created, written, and closed need not be changed. This assumption simplifies data coherency issues and enables high throughput data access.
- A **MapReduce application** or a web crawler application fits perfectly with this model.
## 6. Moving Computation is Cheaper than Moving Data
- A computation requested by an application is much more efficient if it is executed near the data it operates on. This is especially true when the size of the data set is huge.
- This minimizes network congestion and increases the overall throughput of the system.
- The assumption is that it is often better to migrate the computation closer to where the data is located rather than moving the data to where the application is running.
- HDFS provides interfaces for applications to move themselves closer to where the data is located.

## 7. Portability Across Heterogeneous Hardware and Software Platforms
- HDFS has been designed to be easily portable from one platform to another. 
- This facilitates widespread adoption of HDFS as a platform of choice for a large set of applications.

---

# Different Modes of Operation
## 1. Standalone Mode
For testing purpose, only. Cannot be used to test real world applications.

- In _Standalone Mode_ none of the Daemon will run i.e. Namenode, Datanode, Secondary Name node, Job Tracker, and Task Tracker. 
- We use job-tracker and task-tracker for processing purposes in Hadoop1. For Hadoop2 we use Resource Manager and Node Manager. 
- Standalone Mode also means that we are installing Hadoop only in a single system. 

By default, Hadoop is made to run in this Standalone Mode or we can also call it as the _Local mode_. We mainly use Hadoop in this Mode for the Purpose of Learning, testing, and debugging.

## 2. Pseudo-Distributed Mode (Single-Node Cluster)
All demands run on a single server.

In *Pseudo-Distributed Mode* we also use only a single node, but the main thing is that the cluster is simulated, which means that all the processes inside the cluster will run independently to each other. 

All the daemons that are Namenode, Datanode, Secondary Name node, Resource Manager, Node Manager, etc. will be running as a separate process on separate JVM(Java Virtual Machine) or we can say run on different java processes that is why it is called a Pseudo-distributed.
## 3. Fully-Distributed mode
Multiple machines are used in the framework.

This is the most important one in which multiple nodes are used few of them run the Master Daemon’s that are Namenode and Resource Manager and the rest of them run the Slave Daemon’s that are DataNode and Node Manager. 

Here Hadoop will run on the clusters of Machine or nodes. Here the data that is used is distributed across different nodes. This is actually the _Production Mode_ of Hadoop let’s clarify or understand this Mode in a better way in Physical Terminology.

# Architecture
$\rightarrow$ [[HDFS Architecture]]