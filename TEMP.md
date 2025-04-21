Here’s the intuition behind the “splicing” argument via crossing‐sequences:

1. Definitions  
   - Let M be a (one‐tape) Turing machine, and fix an input $z$.  
   - Number the “gaps” between tape‐cells by 0,1,2,…; the gap just to the left of the first (leftmost) cell is gap 0, between cell 1 and 2 is gap 1, etc.  
   - Whenever M’s head crosses gap $g$, note the state it’s in.  The (finite) sequence of states seen on successive crossings of gap $g$ is called the **crossing sequence** $C_g(z)$.

2. Setup  
   - Suppose we have two accepted inputs  
     $$
       x = u \;||\; v
       \quad\text{and}\quad
       y = u' \;||\; v',
    $$  
     where “$\,\|$” marks some boundary—say, between cell $i$ and $i+1$ in $x$, and between cell $j$ and $j+1$ in $y$.  
   - We know  
     $$
       C_i(x) \;=\; C_j(y)
    $$  
     as sequences of states.

3. Splicing to get a new input  
   Form
     $$
       x' \;=\; u \;||\; v'.
    $$
   In words: take the prefix $u$ of $x$ (up to gap $i$) and then glue on the suffix $v'$ of $y$ (from gap $j$ onward).

4. Why $x'$ is accepted  
   - Run M on $x'$.  Over the prefix $u$, the head behaves exactly as it did on $x$, so when it first reaches gap $i$ it will enter in exactly the same state and with the same tape‐contents around the boundary.  
   - From that point on, the behavior of M only depends on  
     1. the sequence of states it sees whenever it crosses that boundary, and  
     2. the tape‐contents to the right of gap $i$.  
   - But by hypothesis, the crossing‐sequence at gap $i$ on $x$ **equals** the crossing‐sequence at gap $j$ on $y$, and the tape‐contents of $v'$ are exactly those seen by M on $y$ after gap $j$.  
   - Therefore M “does the same moves” on the suffix $v'$ here that it did on $y$, eventually reaching the accepting configuration.

5. Conclusion  
   Because the two half‐computations (prefix of $x$, suffix of $y$) stitch together perfectly—thanks to the matching crossing sequences—$x'$ must also be accepted by M.

▸ **Key insight:** matching crossing sequences guarantee “local compatibility” at the splice point, so the Turing machine can’t tell you’ve switched from one accepted computation to another.