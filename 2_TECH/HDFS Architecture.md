[[Hadoop]]
[[Hadoop Distributed File System]]

HDFS **splits big files** into **small chunks (blocks)** and **scatters** them across many computers. One computer (NameNode) **keeps track of everything**, while others (DataNodes) **store the real data**. 

If a computer storing your data dies, **no worries!** — HDFS has extra copies ready. It's **great for reading and processing very large files** in one go (not for fast random edits).

# Components of HDFS
***Master/Slave** architecture* - A single NameNode (NN) and a number of DataNodes (DN)
![[Pasted image 20250505174039.png]]
## 1. NameNode
*Master daemon.* 😈 
- Acts like the manager of the file system.
- Stores metadata (like filenames, directories, permissions, and block locations).
- Does not store actual data.
- Maintains and manages DataNodes. 
- Records [[Metadata]], e.g. location of blocks stored, the size of the files, permissions, hierarchy, etc. 
- Receives heartbeat and block report from all DataNodes
## 2. DataNode
*Slave daemons.* 🥲
- These are the workers that actually store the data in blocks.
- DataNodes regularly send a heartbeat to the NameNode to confirm they are alive and working.
- Stores actual data.
- Serves read and write requests from the clients.
![[Pasted image 20250505174120.png]]
# Data Storage
Files in HDFS are split into blocks (typically 128 MB per block). Each block is replicated across multiple DataNodes (default is 3 copies) for fault tolerance.

# Operations
## 1. Read Operation
- The client contacts the NameNode to find where blocks are stored.
- The client then directly reads data from the relevant DataNodes.

## 2. Write Operation
- The client contacts the NameNode for block allocation.
- Then, the client writes to one DataNode, which copies the block to the next DataNode, and so on (this is called pipelining).

# Fault Tolerance
- If a DataNode fails, the NameNode detects it via the missing heartbeat.
- The NameNode can re-replicate lost blocks on other healthy DataNodes to maintain the desired replication factor.

# Design Goals
- High throughput for large data sets (good for batch processing).
- Streaming data access (instead of random access).
- Fault tolerance is a priority.
- Simple coherence model (once written, a file is not typically modified).

---
# Cluster Architecture
A Hadoop cluster has **one Master node and many Worker nodes.** The Master _coordinates_ everything (storage + computation); the Workers _store data and do tasks_.

- Master Node:
	Runs the NameNode (for HDFS management).
	Runs the ResourceManager (for job and resource scheduling).
- Worker Nodes:
	Run DataNode (store actual data blocks).
	Run NodeManager (manage individual machine’s resources for computation).

![[Pasted image 20250505180143.png]]

---
# HDFS Blocks
In HDFS, **files are broken into fixed-size blocks** (default **128 MB** per block).

![[Pasted image 20250505180308.png]]

Each block is treated **independently** $\rightarrow$ makes **handling large files** easier, because Hadoop can store pieces of the file across many nodes.

![[Pasted image 20250505180416.png]]
- Each block is **replicated** to **multiple DataNodes** (default replication = **3 copies**).
- Replication improves **fault tolerance** (if one node fails, others have copies).
- Replicas are **placed intelligently**:
	One copy on the same rack.
	Another copy on a different rack.
	Third copy possibly elsewhere to balance storage.

---
# Pipelines

## 1. Write Mechanism
![[Pasted image 20250505180850.png]]
Before writing starts, the system **prepares a route** to send the data.

When a client wants to **write** a file:
- It contacts the **NameNode** to **get a list of DataNodes** where it should write the block.
- The **NameNode picks a pipeline**: e.g., DataNode1 → DataNode2 → DataNode3.

**Steps:**
1. Write Request – Block X.
2. IP Addresses: DN1, DN5, and DN7.
3. Sending instructions through the core switch.
4. The core switch distributes the instruction to the switches at the corresponding racks.
5. The main DataNode passes the signal to other listed DataNodes.
6. The DataNodes reply they are ready.

![[Pasted image 20250505181410.png]]

- The client sends **the block to the first DataNode**.
- The first DataNode **forwards** it to the second, and the second forwards to the third (like a **pipeline**).
- Once all copies are written, an **acknowledgment** flows back to the client.

**Steps:**
1. Write Request on DN1, DN5, and DN7.
2. Write Block X on the first DataNode.
3. Block X Replica 1 write request is sent to the second DataNode and the replica is created.
4. Block X Replica 2 write request is sent to the third DataNode and thereplica is created.
5. DataNodes send back the acknowledgement of block X copy tasks are completed.
6. Client send a “writing successful” message to NameNode for updating the metadata.

![[Pasted image 20250505182211.png]]
The pipeline itself is a sequential process. ◦ It can be parallel processes between pipelines.

## 2. Read Mechanism
When a client wants to **read** a file
- It asks the **NameNode**: "Where are my blocks?"
- The NameNode tells the client **the best DataNode** to read from (usually closest or least busy).
- The client **reads directly from the DataNode**.        

It reads **block by block**, and reassembles the full file.

![[Pasted image 20250505182523.png]]

**Steps:**
1. Read Request – Blocks X and Y. 
2. IP Addresses: DNs 2 and 3. 
3. Read from DN2 and DN3.