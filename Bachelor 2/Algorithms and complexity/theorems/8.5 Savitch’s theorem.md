# Theorem: NTM to DTM Space Conversion

Any nondeterministic Turing machine (NTM) that uses $f(n)$ space can be converted to a deterministic Turing machine (DTM) that uses $O(f^2(n))$ space.

**Formal Statement:**

For all functions $f: \mathbb{N} \to \mathbb{R}^+$ such that $f(n) \geq n$ for all $n \in \mathbb{N}$,

$$
\text{NSPACE}(f(n)) \subseteq \text{SPACE}(f^2(n)).
$$

# Proof

We aim to show that any language $A$ decided by an NTM $N$ using $f(n)$ space can be decided by a DTM $M$ using $O(f^2(n))$ space.

## Construction of the Deterministic Turing Machine $M$

Let $N$ be an NTM that decides a language $A$ in space $f(n)$, where $n$ is the length of the input string $w$. We construct a DTM $M$ that simulates $N$ and decides $A$.

### Step 1: Modify NTM $N$

Modify $N$ so that when it accepts an input, it:

1. Clears its tape.
2. Moves its head to the leftmost cell.
3. Enters a unique accepting configuration, denoted $c_{\text{accept}}$.

Let $c_{\text{start}}$ be the starting configuration of $N$ on input $w$.

### Step 2: Configuration and Time Bounds

- **Space Bound**: Since $N$ uses $f(n)$ space, the number of possible configurations of $N$ is bounded by $2^{d \cdot f(n)}$ for some constant $d > 0$, accounting for the tape contents, head position, and state.
- **Time Bound**: The running time of any branch of $N$ on input $w$ is bounded by $2^{d \cdot f(n)}$, as exceeding this would imply revisiting a configuration (by the pigeonhole principle), leading to a loop, which we assume $N$ avoids in accepting paths.

### Step 3: Define the `CANYIELD` Procedure

We define a procedure `CANYIELD(c_1, c_2, t)` that determines whether $N$ can reach configuration $c_2$ from configuration $c_1$ in at most $t$ steps along some nondeterministic path, where $t$ is a power of 2. The procedure operates as follows:

**Algorithm: `CANYIELD(c_1, c_2, t)`**

- **Base Case**: If $t = 1$:
  - If $c_1 = c_2$ or $c_1$ yields $c_2$ in one step (according to $N$’s transition function), return _accept_.
  - Otherwise, return _reject_.
- **Recursive Case**: If $t > 1$:
  - For each configuration $c_m$ of $N$ using space $f(n)$:
    - If `CANYIELD(c_1, c_m, t/2)` returns _accept_ and `CANYIELD(c_m, c_2, t/2)` returns _accept_, return _accept_.
  - If no such $c_m$ exists, return _reject_.

### Step 4: Define DTM $M$

The DTM $M$ operates as follows:

**Algorithm: DTM $M$**

On input $w$:

1. Compute $t = 2^{d \cdot f(n)}$, where $d$ is the constant from the configuration bound.
2. Output the result of `CANYIELD(c_{\text{start}}, c_{\text{accept}}, t)`.

### Step 5: Handling Unknown $f(n)$

Since $M$ needs to know $f(n)$, but $f(n)$ may not be explicitly given, modify $M$ to try $f(n) = 1, 2, 3, \dots$ iteratively:

**Modified Algorithm: DTM $M$**

On input $w$:

1. For $i = 1, 2, 3, \dots$:
   - Assume $f(n) = i$.
   - Use `CANYIELD`($c_{\text{start}}, c_{\text{accept}}, 2^{d \cdot i}$) to check if $c_{\text{accept}}$ is reachable.
   - Use `CANYIELD` to check if any configuration using space $i+1$ is reachable from $c_{\text{start}}$ in $2^{d \cdot i}$ steps.
   - **Decision**:
     - If $c_{\text{accept}}$ is reachable, accept.
     - If no configuration using space $i+1$ is reachable, reject.
     - Otherwise, continue with $i \gets i + 1$.

This ensures $M$ correctly identifies the space used by $N$ and simulates it appropriately.

## Correctness Analysis

- **Simulation**: The `CANYIELD` procedure correctly determines if there exists a nondeterministic path from $c_1$ to $c_2$ in at most $t$ steps by exploring all possible intermediate configurations recursively.
- **Acceptance**: Since $N$ accepts $w$ if and only if $c_{\text{accept}}$ is reachable from $c_{\text{start}}$ in at most $2^{d \cdot f(n)}$ steps, $M$ accepts $w$ if and only if $N$ does, correctly deciding $A$.

## Space Complexity Analysis

- **Configuration Storage**: Each configuration ($c_1$, $c_2$, $c_m$) uses $O(f(n))$ space, as it includes the tape contents (of length $f(n)$), head position, and state.
- **Recursion Stack**:
  - Each recursive call to `CANYIELD` stores the current stage, $c_1$, $c_2$, and $t$, requiring $O(f(n))$ space per level (since $t$ can be represented in $O(f(n))$ bits when $t \leq 2^{d \cdot f(n)}$).
  - The recursion depth is determined by halving $t$ at each level. Since $t$ starts at $2^{d \cdot f(n)}$, the depth is:
    $$
    \log(2^{d \cdot f(n)}) = d \cdot f(n) = O(f(n)).
    $$
- **Total Space**: The total space is the recursion depth times the space per level:
  $$
  O(f(n)) \cdot O(f(n)) = O(f^2(n)).
  $$
- **Iterative $f(n)$ Search**: The modified $M$ tries $f(n) = i$, but each iteration reuses space (by resetting the computation), and the correct $i$ is at most $f(n)$. The space for each iteration is still $O(f^2(n))$, as it involves a single call to `CANYIELD`.

Thus, $M$ operates in $O(f^2(n))$ space.

## Conclusion

The DTM $M$ correctly simulates the NTM $N$ and decides the same language $A$ using $O(f^2(n))$ space. Therefore:

$$
\text{NSPACE}(f(n)) \subseteq \text{SPACE}(f^2(n)).
$$

$$
\boxed{\text{Q.E.D.}}
$$
