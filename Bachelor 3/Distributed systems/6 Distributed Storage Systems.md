## 6.1 Distributed Storage Systems

### HDFS Architecture

#### Core Components

- **NameNode**: Master server managing file system namespace and client access (tracking block locations)
- **DataNodes**: Slave nodes storing actual data blocks (typically 128MB size) with 3x replication
- **Block Management**: Files split into blocks distributed across cluster, with automatic re-replication when nodes fail

#### Fault Tolerance Mechanisms

- **Replication Strategy**: 3 copies of each block stored on different nodes/racks
- **Recovery Process**: Namenode detects dead DataNodes via heartbeat, triggers replication from surviving copies
- **Write Pipeline**: Client writes to first DataNode, which forwards to second, creating replication chain

### Storage Optimization Concepts

- **Tradeoffs in Algorithm Design**: Consider $O(n \log n)$ vs $O(n^2)$ operations alongside hardware factors (disk access = 10⁵ slower than RAM)
- **Paradigm Shift Drivers**: Physical limits (atomic scales, 3D layering constraints) forced move from clock speed increases to parallel processing

## 6.2 Distributed Processing Frameworks

### MapReduce Fundamentals

#### Execution Phases

1. **Map**: Processes <key,value> pairs (e.g., `(line_number, text) → (word, 1)`)
2. **Shuffle**: Sorts and groups intermediate results by key
3. **Reduce**: Aggregates values per key (e.g., word counts)

![[Bachelor 3/Distributed systems/images/mapreduce example.png]]
#### Limitations

- **Disk-Based Workflow**: Requires HDFS writes between phases (slow for iterative tasks)
- **Rigid Model**: Only map/shuffle/reduce operations, lacking joins/streaming support
- **Failure Handling**: JobTracker single point of failure in early implementations

### Hadoop Ecosystem Tools

- **YARN**: Resource negotiator separating cluster management (ResourceManager) from application logic (ApplicationMaster)
- **Pig/Hive**: Higher-level abstractions (SQL-like queries) converting to MapReduce jobs
- **Kafka**: Distributed commit log for real-time data streaming (foundation for Spark integration)

## 6.3 Spark: Evolution of Distributed Processing

### Architectural Advantages

#### In-Memory Computing

- **RDDs (Resilient Distributed Datasets)**: Immutable collections with lineage tracking for fault recovery
- **DAG Optimization**: Creates execution plans avoiding unnecessary shuffles (Page 65 DAG example)
- **Performance Gains**: 3x faster than Hadoop in 100TB sort benchmark using 10x fewer nodes (Page 56 metrics)

#### Expanded Operation Set

- **Transformations**: `map`, `filter`, `join`, `groupByKey` (40+ operations vs MapReduce's 2)
- **Actions**: `collect`, `count`, `save` triggering DAG execution
- **SQL Integration**: DataFrames API enabling relational operations on distributed data

### Real-World Implementations

- **Uber ETL Pipeline**: Kafka → Spark Streaming → HDFS for real-time ride analytics
- **Pinterest Recommendations**: Spark MLlib processing 20TB/day of pin engagement data
- **Logistic Regression Speed**: 110s/iteration (Hadoop) vs 1s/iteration (Spark) after initial run (Page 57 graph)

---

## Key Points to Remember

- **HDFS Reliability→Replication Strategy**: (3-Copy Rule) ★★★★★

  - Data durability through geographic block distribution and automatic recovery

- **MapReduce Limitation→Disk Bottleneck**: (Shuffle Phase Cost) ★★★★☆

  - Page 52 shows 53% cost reduction with SSD intermediate storage

- **Spark Advantage→In-Memory Caching**: (RDD Lineage) ★★★★☆

  - Enables iterative ML algorithms through memory persistence (vs Hadoop's disk writes)

- **Ecosystem Choice→Problem Fit**: (Batch vs Streaming) ★★★★☆

  - Hadoop for large-scale batch ETL, Spark for real-time analytics/ML

- **Performance Metric→Sort Benchmark**: (Cluster Efficiency) ★★★★

  - Spark achieved 4.27TB/min vs Hadoop's 1.42TB/min with better $/job metrics

- **Architecture Trend→Abstraction Layers**: (SQL-on-Hadoop) ★★★☆

  - Hive/Pig/SparkSQL demonstrate industry shift toward declarative programming

- **Failure Handling→Google Cluster Reality**: (Design for Faults) ★★★★☆
  - Page 10 notes 1000+ machine failures/day requiring distributed resilience
