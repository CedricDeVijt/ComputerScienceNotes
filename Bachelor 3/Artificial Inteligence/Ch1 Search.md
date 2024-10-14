## 1.1 Agents that Plan

### Reflex Agents
- **Reflex agents** make decisions based on the **current percept** (and maybe memory).
- **Do not** consider future consequences of actions.
- Reflex agents are limited to **how the world *is*** rather than how it could be.

### Planning Agents
- Planning agents use a model to ask "**what if**" and make decisions based on hypothesized outcomes.
- Require a model of the world and a defined **goal**.
- Key concept: **Planning vs. Replanning**.

## 1.2 Search Problems

### Defining a Search Problem
- **Components**:
  - **State Space**: Set of all possible states.
  - **Successor Function**: Defines possible actions and their costs.
  - **Start State** and **Goal Test**.
- A **solution** is a sequence of actions leading from the start state to a goal state.

### State Space Representation
- The **world state** includes every last detail of the environment
- In **search state**, include only the details needed for planning (abstraction).

## 1.3 Search Trees and State Space Graphs

### State Space Graphs
- Represent a **mathematical model** of a search problem.
- **Nodes**: Represent states; **Arcs**: Represent actions.
### Search Trees
- A **search tree** represents "what if" scenarios.
- The **root node** is the start state, and **children** are the successors.
- Each **node** represents a **plan**, not just a state.
- For most problems, we can never actually build the whole tree
- Cyclic graphs from infinitely big search trees
![[Pasted image 20241002133435.png]]
## 1.4 Search Strategies
### Searching with a Search tree
- Expand out potential plans (tree nodes)
- Maintain a **fringe** (collection of all nodes that are generated but not yet expanded) of partial plans under consideration
- Try to expand as few nodes as possible
### Depth-First Search (DFS)
- Expands the **deepest node** first.
- Fringe is managed as a **LIFO stack**.
- **Properties**:
  - Space complexity: **O(bm)**.
  - **Not optimal**: Finds leftmost solution regardless of cost.
![[Pasted image 20241002142152.png]]

### Breadth-First Search (BFS)
- Expands the **shallowest node** first.
- Fringe is managed as a **FIFO queue**.
- **Properties**:
  - **Complete** if a solution exists.
  - **Optimal** if all step costs are equal.
![[Screenshot 2024-10-02 at 14.23.18.png]]

![[Screenshot 2024-10-02 at 14.22.47.png]]
### Iterative Deepening
- **Combines** advantages of DFS (space efficiency) and BFS (finding the shallowest solution).
- Expands DFS to increasing depths until a solution is found.

![[Pasted image 20241014094908.png]]

## 1.5 Cost-Sensitive Search

### Uniform Cost Search (UCS)
- Expands nodes based on **cumulative cost** using a **priority queue**.
- Guarantees finding the **least-cost path** if costs are positive.
- **Issues**: May expand in **all directions** without guidance towards the goal.
![[Screenshot 2024-10-02 at 14.24.35.png]] ![[Screenshot 2024-10-02 at 14.24.12.png]]
## 1.6 Informed Search

### Heuristics
- A **heuristic** estimates the cost from the current state to the goal.
- Examples include **Manhattan distance** for grid-based pathfinding.

### Greedy Search
- Expands the node that **seems closest** to the goal.
- May fail as it doesn't account for the actual cost to reach the goal.

![[Pasted image 20241014101442.png |300]] ![[Pasted image 20241014101454.png |300 ]]
### A* Search
- **Combines** UCS and Greedy Search:
  - **f(n) = g(n) + h(n)**: Total cost (g) + estimated cost to goal (h).
- **Optimal** if the heuristic is **admissible** (never overestimates the true cost).

## 1.7 Optimality and Heuristics

### Admissible and Consistent Heuristics
- **Admissible Heuristic**: Always underestimates the true cost to the goal.
- **Consistent Heuristic**: Ensures that the **f-value** along a path does not decrease.
- A* is **optimal** with consistent heuristics.

### Graph Search and Tree Search
- **Graph Search** avoids expanding the same state multiple times by keeping a **closed set**.
- Important to use **graph search** to maintain **completeness** and **optimality**.

## 1.8 Heuristics in Practice

### Creating Heuristics
- Often, heuristics come from solving a **relaxed version** of the problem.
- Example: In the **8-puzzle**, two heuristics are:
  - **Number of misplaced tiles**.
  - **Manhattan distance** for each tile.

### Semi-Lattice of Heuristics
- The **max of admissible heuristics** is also admissible.
- Use of heuristics involves balancing **computation cost** and **accuracy**.

## 1.9 Summary of A*

### Properties of A*
- **Combines** backward (cost to state) and forward (estimate to goal) costs.
- The **key** to A* efficiency is a **well-designed heuristic**.
- **Graph Search** version of A* is optimal if heuristics are consistent.


## 1.10 Complexity of Search Algorithm

| **Algorithm**            | **Time Complexity**         | **Space Complexity**        | **Complete** | **Optimal**              |
| ------------------------ | --------------------------- | --------------------------- | ------------ | ------------------------ |
| **Depth-First Search**   | $O(b^m)$                    | $O(bm)$                     | No           | No                       |
| **Breadth-First Search** | $O(b^s)$                    | $O(b^s)$                    | Yes          | Yes (if costs are equal) |
| **Uniform Cost Search**  | $O(b^{(C*/ε)})$             | $O(b^{(C*/ε)})$             | Yes          | Yes                      |
| **Iterative Deepening**  | $O(b^s)$                    | $O(bs)$                     | Yes          | Yes                      |
| **Greedy Search**        | $O(b^m)$                    | $O(b^m)$                    | No           | No                       |
| **A* Search**            | $O(b^m)$ or $O(b^{(C*/ε)})$ | $O(b^m)$ or $O(b^{(C*/ε)})$ | Yes          | Yes                      |

- **b**: branching factor (average number of successors per state)
- **m**: maximum depth of the search space
- **s**: depth of the shallowest solution
- **C***: cost of the optimal solution
- **ε**: smallest arc cost

![[Pasted image 20241014092213.png]]