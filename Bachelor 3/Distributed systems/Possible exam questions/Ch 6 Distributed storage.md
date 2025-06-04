## A) Directed Acyclic Graphs (DAGs) have been proposed as a good structure to handle disrtibuted storage and processing. Indicate how these DAG structures are defined in the context of disrtibuted storage and processing and what are the advantages of following this type of structure.

**Definition**: In distributed storage and processing, DAGs are graph structures where nodes represent data or tasks, and directed edges show dependencies without cycles, ensuring a clear execution order.
**Advantages**:

- Efficient task scheduling and parallel processing.
- Fault tolerance via lineage tracking.
- Optimized resource use and scalability.
- Simplified dependency management.

## B) Indicate the main difference between Narrow and Wide transformation in Resilient Distributed Datasets (RDDs). DataFrames.

**Narrow Transformation**: Operations where each input partition contributes to one output partition (e.g., map, filter). No data shuffling required, faster.
**Wide Transformation**: Operations requiring data shuffling across partitions (e.g., groupBy, join), as input partitions contribute to multiple output partitions. Slower due to network overhead.
Applies to both RDDs and DataFrames.
