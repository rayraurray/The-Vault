[[Big Data]]
[[Platforms for Storing Big Data]]

# Definition
*The Apache Hadoop software library* is a framework that allows for the distributed processing of large data sets across clusters of computers using simple programming models. It is designed to **scale up from single servers to thousands of machines**, each offering local computation and storage. Rather than rely on hardware to deliver high-availability, the library itself is designed to **detect and handle failures at the application layer**, so delivering a highly-available service on top of a cluster of computers, each of which may be prone to failures.
-[*Hadoop*](https://hadoop.apache.org/)

---

- Hadoop implements a computational paradigm named *Map/Reduce*, where the application is divided into many small fragments of work, each of which may be executed or re-executed on any node in the cluster.
- In addition, it provides a distributed file system (HDFS) that stores data on the compute nodes, providing very high aggregate bandwidth across the cluster.
- Both *MapReduce* and the [[Hadoop Distributed File System]] are designed so that node failures are automatically handled by the framework.

![[Pasted image 20250505170606.png]]