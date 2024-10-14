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
    - **Efficiency**: Time complexity: O(b^m), Space: O(b^m), where `b` is branching factor and `m` is depth.
    - **Challenge**: Full-tree search impractical in large games like chess.

## 2.4: Alpha-Beta Pruning
- **Alpha-Beta Pruning**: Improves the efficiency of minimax by cutting off branches that won't affect the final decision.
    - **Best Case**: Time complexity can reduce to O(b^(m/2)) with perfect move ordering.

## 2.5: Resource Limits and Evaluation Functions
- **Depth-Limited Search**: When the search tree is too large, cut off after a limited depth and use an evaluation function.
- **Evaluation Function**: Scores non-terminal nodes, typically as a **weighted sum** of game features.

## 2.6: Expectimax Search
- **Expectimax Search**: Used when there’s randomness (e.g., dice rolls). Instead of minimax's worst-case strategy, **expectimax** calculates the **average** expected utility.
    - Includes **chance nodes** representing random events.
    - **Efficiency**: More expensive than minimax, as it needs to evaluate all possible outcomes probabilistically.

## 2.7: Mixed and Multi-Agent Games
- **Expectiminimax**: A combination of minimax and expectimax, where one layer of the tree involves chance events.
- **Multi-Agent Utilities**: Used in games with more than two players where the game may not be zero-sum. Each agent tries to maximize its own utility, which can lead to dynamic cooperation or competition.

---

# **Key Points to Remember**
- **Minimax Algorithm**: Alternates between players who maximize or minimize outcomes in a **zero-sum game**.
- **Alpha-Beta Pruning** can drastically reduce the number of nodes evaluated in minimax without affecting the final result.
- **Evaluation Functions** replace terminal values in depth-limited search, allowing for approximate game evaluations.
- **Expectimax Search**: Used for games with uncertainty (e.g., dice rolls or unpredictable opponents).
- **Resource Limits**: Limit the depth of search trees to fit within real-time constraints (common in chess, Go, etc.).

---

# **Highlighted Concepts for Quick Review**
- **Minimax Algorithm**: A core concept in adversarial search.
- **Alpha-Beta Pruning**: Essential for optimizing search in complex games.
- **Expectimax Search**: Deals with random elements in game outcomes.
- **Evaluation Function**: Used when a full game tree search isn't feasible due to depth limits.
