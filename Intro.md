# What is RDD?
RDD stands for Resilient Distributed Dataset.
- **Resilient:** It auto-recovers if a node crashes.
- **Distributed:** Data is split across Node A, B, and C.
- **Dataset:** The actual data.

### Key Takeaway
RDDs are the "DNA" of Spark. Even when using DataFrames, RDDs run underneath..

# DAG and Lazy Evaluation
## 2. The Execution Flow
Spark operations are divided into two categories:

### A. Transformations (Lazy)
Operations that define a new RDD from an existing one. They are **lazy**, meaning they do not compute results immediately.
*   *Examples:* `map()`, `filter()`, `flatMap()`, `union()`
*   *Behavior:* Builds the DAG (execution plan) but executes nothing.

### B. Actions (Eager)
Operations that trigger computation and return results to the driver or storage.
*   *Examples:* `collect()`, `count()`, `saveAsTextFile()`, `show()`
*   *Behavior:* Triggers the DAG execution.

## 3. Optimization Concepts
*   **Lazy Evaluation:** Spark waits until an Action is called to execute the graph. This allows the engine to optimize the workflow (e.g., skipping loading unused columns).
*   **DAG (Directed Acyclic Graph):** A finite direct graph that represents the sequence of operations. Spark uses the DAG to determine the most efficient way to execute the job