## 3.1 Theorem

Any nondeterministic TM that uses $f(n)$ space can be converted to a deterministic TM that uses only $f^2(n)$ space.

$\forall f:\mathbb{N} \to \mathbb{R}^+,\ \forall n \in \mathbb{N},\ f(n) \geq n: NSPACE(f(n)) \subseteq SPACE(f^2(n))$

## 3.2 Proof

Let N be an NTM deciding a language A in space f(n). We construct a DTM M deciding A.

Machine M uses the procedure `CANYIELD`, which tests whether one of N’s configurations can yield another within a specified number of steps. Let w be a string considered as input to N.

For configurations $c_1$ and $c_2$ of N, and integer t, `CANYIELD(c1,c2,t)` outputs accept if N can go from configuration c1 to configuration $c_2$ in t or fewer steps along some nondeterministic path. If not, `CANYIELD` outputs reject. For convenience, we assume that t is a power of 2.

Function `CANYIELD(c1, c2, t)` is defined as follows:

```plaintext
CANYIELD(c1, c2, t):
if t = 1:
    if c1 = c2 or c1 yields c2 in one step:
        accept
    else:
        reject
else:
    for each configuration cm of N using space f(n):
        if CANYIELD(c1, cm, t/2) and CANYIELD(cm, c2, t/2):
            accept
    reject
```

Now we define M to simulate N as follows:

- We first modify N so that when it accepts, it clears its tape and moves the head to the leftmost cell, thereby entering a configuration called $c_accept$.
- We let $c_start$ be the start configuration of N on w. We select a constant $d$ so that N has no more than $2d f (n)$ configurations using f(n) tape, where n is the length of w. Then we know that $2df (n)$ provides an upper bound on the running time of any branch of N on w.

M = On input w: Output the result of CANYIELD(c_start, c_accept, 2^{df(n)}).

Algorithm CANYIELD obviously solves the yieldability problem, and hence M correctly simulates N. We need to analyze it to verify that M works within
$O(f^2(n))$ space.

Whenever CANYIELD invokes itself recursively, it stores the current stage number and the values of c1, c2, and t on a stack so that these values may be restored upon return from the recursive invocation. Each level of the recursion thus uses O(f(n)) additional space. Furthermore, each level of the recursion divides the size of t in half. Initially t starts out equal to 2df (n), so the depth of the recursion is O(log 2df (n)) or O(f(n)). Therefore, the total space used is O(f2(n)), as claimed.

One technical difficulty arises in this argument because algorithm M needs to
know the value of f(n) when it calls CANYIELD. We can handle this difficulty
by modifying M so that it tries f(n) = 1,2,3,.... For each value f(n) = i, the
modified algorithm uses CANYIELD to determine whether the accept configu-
ration is reachable. In addition, it uses CANYIELD to determine whether N uses
at least space i+ 1 by testing whether N can reach any of the configurations of
length i+1 from the start configuration. If the accept configuration is reachable,
M accepts; if no configuration of length i+ 1 is reachable, M rejects; and other-
wise, M continues with f(n) = i+ 1.

---

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
   - Use `CANYIELD(c_{\text{start}}, c_{\text{accept}}, 2^{d \cdot i})` to check if $c_{\text{accept}}$ is reachable.
   - Use `CANYIELD` to check if any configuration using space $i+1$ is reachable from $c_{\text{start}}$ in $2^{d \cdot i}$ steps.
   - **Decision**:
     - If $c_{\text{accept}}$ is reachable, accept.
     - If no configuration using space $i+1$ is reachable, reject.
     - Otherwise, continue with $i \gets i + 1$.

This ensures $M$ correctly identifies the space used by $N$ and simulates it appropriately.

## 3.4 Correctness Analysis

- **Simulation**: The `CANYIELD` procedure correctly determines if there exists a nondeterministic path from $c_1$ to $c_2$ in at most $t$ steps by exploring all possible intermediate configurations recursively.
- **Acceptance**: Since $N$ accepts $w$ if and only if $c_{\text{accept}}$ is reachable from $c_{\text{start}}$ in at most $2^{d \cdot f(n)}$ steps, $M$ accepts $w$ if and only if $N$ does, correctly deciding $A$.

## 3.5 Space Complexity Analysis

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

## 3.6 Conclusion

The DTM $M$ correctly simulates the NTM $N$ and decides the same language $A$ using $O(f^2(n))$ space. Therefore:

$$
\text{NSPACE}(f(n)) \subseteq \text{SPACE}(f^2(n)).
$$

$$
\boxed{\text{Q.E.D.}}
$$
