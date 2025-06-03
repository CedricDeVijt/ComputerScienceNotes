## Describe the data-centric and client-centric consistency models. Indicate what are the main advantages and disadvantages of using one over the other.

**Data-centric** consistency models focus on the state of the data itself, ensuring that all replicas reflect the same data at any given time.

Advantages:

- Strong guarantees about data visibility and consistency.
- Easier reasoning about the system's state, as all replicas are synchronized.

Disadvantages:

- Higher latency due to the need for coordination among replicas.
- Reduced availability, as replicas may be temporarily unavailable during synchronization.

**Client-centric** consistency models, on the other hand, focus on the client's view of the data, allowing for more flexibility and potentially higher performance.

Advantages:

- Improved performance and availability, as replicas can diverge temporarily.
- Reduced coordination overhead, allowing for faster operations.

Disadvantages:

- Potential inconsistencies in the client's view of the data.
- Harder to reason about the system's state, as replicas may not reflect the same data at all times.

## Describe the Pipelined Random Access Memory (PRAM) consistency model. Indicate and justify whether the processes below follow the PRAM consistency model.

### (a)

| Process | Operation 1 | Operation 2 | Operation 3 |
| ------- | ----------- | ----------- | ----------- |
| P1      | W(x)a       |             |             |
| P2      | W(x)c       | W(x)b       |             |
| P3      | R(x)b       | R(x)a       | R(x)c       |


### (b)

| Process | Operation 1 | Operation 2 | Operation 3 |
| ------- | ----------- | ----------- | ----------- |
| P1      | W(x)a       |             |             |
| P2      | R(x)a       | W(x)b       | W(x)c       |
| P3      | R(x)b       | R(x)a       | R(x)c       |
| P4      | R(x)a       | R(x)b       | R(x)c       |

