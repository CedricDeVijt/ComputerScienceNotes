# Proof: If $A \leq_L B$ and $B \in L$, then $A \in L$

## Theorem Statement

Let $A$ and $B$ be languages. If $A \leq_L B$ (i.e., $A$ is log space reducible to $B$) and $B \in L$ (i.e., $B$ is in the complexity class $L$, decidable in logarithmic space), then $A \in L$.

## Definitions

- **Log Space Reducibility ($\leq_L$)**: A language $A$ is log space reducible to a language $B$ if there exists a function $f: \Sigma^* \to \Sigma^*$, computable by a deterministic Turing machine in logarithmic space, such that for any input $w$, $w \in A$ if and only if $f(w) \in B$.
- **Complexity Class $L$**: The class of languages decidable by a deterministic Turing machine using $O(\log n)$ space, where $n$ is the input length.

## Proof Strategy

A naive approach might mimic the proof for polynomial-time reducibility (e.g., Theorem 7.31), where a machine for $A$ computes $f(w)$ using the reduction and then runs the algorithm for $B$ on $f(w)$. However, in log space, storing the entire output $f(w)$ may exceed the $O(\log n)$ space bound. Instead, we design a log space algorithm for $A$ that computes symbols of $f(w)$ on demand, trading time efficiency for space efficiency.

## Proof

We construct a deterministic Turing machine $M_A$ that decides $A$ in logarithmic space, given that $A \leq_L B$ and $B \in L$.

1. **Setup**:

   - Since $A \leq_L B$, there exists a log space computable function $f$ such that $w \in A$ if and only if $f(w) \in B$.
   - Since $B \in L$, there exists a deterministic Turing machine $M_B$ that decides $B$ using $O(\log |f(w)|)$ space.

2. **Algorithm for $M_A$**:

   - **Input**: String $w$.
   - **Simulation**:
     - $M_A$ simulates $M_B$ on input $f(w)$, but does not compute and store $f(w)$ explicitly, as it may require more than logarithmic space.
     - Instead, $M_A$ keeps track of the position of $M_B$'s input head on the virtual input tape containing $f(w)$. This position can be stored in $O(\log |f(w)|)$ space, as it is a pointer to a position in $f(w)$.
     - Whenever $M_B$ requests the symbol at position $i$ of $f(w)$, $M_A$ recomputes the $i$-th symbol of $f(w)$ by running the log space reduction $f$ on input $w$. To do so:
       - $M_A$ restarts the computation of $f(w)$ from the beginning.
       - It counts output symbols until the $i$-th symbol is reached, outputting only that symbol and discarding others.
     - $M_A$ stores only the current symbol of $f(w)$ (constant space) and the head position (logarithmic space).

3. **Space Analysis**:

   - **Reduction $f$**: The function $f$ is computable in $O(\log |w|)$ space.
   - **Simulation of $M_B$**: Since $M_B$ uses $O(\log |f(w)|)$ space and $|f(w)|$ is polynomial in $|w|$ (as $f$ is computable in log space), $\log |f(w)| = O(\log |w|)$.
   - **Additional Storage**:
     - The head position on $f(w)$ requires $O(\log |f(w)|) = O(\log |w|)$ space.
     - A single symbol of $f(w)$ requires constant space.
     - Any additional counters or state information for $f$ or $M_B$ are within the log space bound.
   - **Total Space**: The total space used by $M_A$ is $O(\log |w|)$, as all components operate within logarithmic space.

4. **Correctness**:

   - For each symbol requested by $M_B$, $M_A$ correctly computes the $i$-th symbol of $f(w)$ using the log space reduction $f$.
   - Thus, $M_A$ accurately simulates $M_B$ on $f(w)$.
   - Since $w \in A \iff f(w) \in B$, and $M_B$ correctly decides $B$, $M_A$ correctly decides $A$.

5. **Time Trade-off**:
   - Recomputing symbols of $f(w)$ for each request by $M_B$ is time-inefficient, as $f$ may be recomputed multiple times.
   - However, this approach ensures that only logarithmic space is used, satisfying the requirements of $L$.

## Conclusion

The machine $M_A$ decides $A$ using $O(\log |w|)$ space, so $A \in L$. Thus, if $A \leq_L B$ and $B \in L$, then $A \in L$.
