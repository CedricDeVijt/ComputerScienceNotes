## 2.1: Introduction to Game Playing
- **Game Playing State-of-the-Art**
    - **Checkers**: 1950 - First computer player; 1994 - Chinook ended a 40-year reign of human champion Marion Tinsley; 2007 - Checkers solved.
    - **Chess**: 1997 - Deep Blue defeated Garry Kasparov in a six-game match.
    - **Go**: 2016 - AlphaGo defeated human champions using **Monte Carlo Tree Search**.
- **Axes of Games**:
    - **Deterministic** or **stochastic**
    - One, two, or more players
    - **Zero-sum** games
    - **Perfect information** or hidden information

## 2.2: Deterministic Games and Zero-Sum Games
- **Deterministic Games**: Players take turns, each state has actions leading to new states.
- **Zero-Sum Games**: Players have opposite utilities, where one player's gain is the other's loss.
- **General Games**: Can include cooperation or competition.

## 2.3: Adversarial Search
- **Adversarial Game Trees**: Players alternate turns in a search tree, attempting to maximize or minimize the outcome.
- **Minimax Search**: 
    - **Goal**: Find the best achievable utility against a rational opponent.
    - **Efficiency**: Time complexity: $O(b^m)$, Space: $O(b^m)$, where $b$ is branching factor and $m$ is depth.
    - **Challenge**: Full-tree search impractical in large games like chess.

![[Pasted image 20241017105228.png]]

![[Pasted image 20241017105127.png|400]]
## 2.4: Alpha-Beta Pruning
- **Alpha-Beta Pruning**: Improves the efficiency of minimax by cutting off branches that won't affect the final decision.
    - **Best Case**: Time complexity can reduce to $O(b^{(m/2)})$ with perfect move ordering.
    - Pruning has **no effect** on minimax value computed for the root

![[Pasted image 20241017105253.png]]

![[Pasted image 20241017105322.png]]

## 2.5: Resource Limits and Evaluation Functions
- **Depth-Limited Search**: When the search tree is too large, cut off after a limited depth and use an evaluation function.
- **Evaluation Function**: 
    - Ideal function: returns the actual minimax value of the position
    - In practice: typically weighted linear sum of features 
    - The deeper in the tree the evaluation function is buried, the less the quality of the evaluation function matters

## 2.6 Synergies Between Evaluation Function and Alpha-Beta
In the Alpha-Beta algorithm:
- Pruning occurs when a **Min-node's value** drops below the best value already found for **Max**.
### Pruning at Min-Nodes
- **Min nodes**' values keep going down as worse alternatives are explored.
- If the evaluation function estimates an upper bound at a Min-node, and this upper bound is already **lower** than the best option for Max, pruning can occur.
  - This is because further exploration of the Min-node won’t affect the final outcome for Max, making it safe to stop evaluating that branch.
### Combining Evaluation and Alpha-Beta
- **Evaluation function synergy** with Alpha-Beta pruning is based on:
  - **Good node ordering**: The evaluation function helps prioritize promising nodes, increasing the potential for pruning.
  - **Early discovery of better moves**: By evaluating promising nodes first, the algorithm is more likely to find alternatives that allow for aggressive pruning.
  
- The better the evaluation function at guiding node expansion, the **more efficient Alpha-Beta pruning** becomes, reducing the overall number of nodes to explore.

## 2.7: Expectimax Search
- **Expectimax Search**: Used when there’s randomness (e.g., dice rolls). Instead of minimax's worst-case strategy, **expectimax** calculates the **average** expected utility.
    - Includes **chance nodes** representing random events.
    - **Efficiency**: More expensive than minimax, as it needs to evaluate all possible outcomes probabilistically.

## 2.8: Mixed and Multi-Agent Games
- **Expectiminimax**: A combination of minimax and expectimax, where one layer of the tree involves chance events.
- **Multi-Agent Utilities**: Used in games with more than two players where the game may not be zero-sum. Each agent tries to maximize its own utility, which can lead to dynamic cooperation or competition.

---

# Key Points to Remember
- **Minimax Algorithm**: Alternates between players who maximize or minimize outcomes in a **zero-sum game**.
- **Alpha-Beta Pruning** can drastically reduce the number of nodes evaluated in minimax without affecting the final result.
- **Evaluation Functions** replace terminal values in depth-limited search, allowing for approximate game evaluations.
- **Expectimax Search**: Used for games with uncertainty (e.g., dice rolls or unpredictable opponents).
- **Resource Limits**: Limit the depth of search trees to fit within real-time constraints (common in chess, Go, etc.).

---

# Highlighted Concepts for Quick Review
- **Minimax Algorithm**: A core concept in adversarial search.
- **Alpha-Beta Pruning**: Essential for optimizing search in complex games.
- **Expectimax Search**: Deals with random elements in game outcomes.
- **Evaluation Function**: Used when a full game tree search isn't feasible due to depth limits.
