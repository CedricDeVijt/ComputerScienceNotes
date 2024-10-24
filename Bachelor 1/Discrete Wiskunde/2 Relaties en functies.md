# 2.1 Relations and Functions
## 2.1.1 Relation
- **Definition**: A relation between two sets $A$ and $B$ is a subset of their Cartesian product $A \times B$. Denoted as $R \subseteq A \times B$.
- **Notation**: If $(a, b) \in R$, write it as $a R b$.
- **Example**: A relation from the set of integers to the set of natural numbers.

### Domain and Range
- **Domain**: Set of all elements in $A$ that relate to some element in $B$.
- **Range**: Set of all elements in $B$ related to at least one element in $A$.

### Inverse Relation
- **Definition**: For a relation $R \subseteq A \times B$, its inverse is $R^{-1} \subseteq B \times A$.

## 2.1.2 Properties of Relations
- **Compositional Relations**: If $R \subseteq A \times B$ and $S \subseteq B \times C$, then the composition is $S \circ R \subseteq A \times C$.
- **Key Properties**:
  - **Reflexive**: $aRa$ for all $a \in A$.
  - **Symmetric**: $aRb$ implies $bRa$.
  - **Transitive**: $aRb$ and $bRc$ imply $aRc$.
  - **Antisymmetric**: $aRb$ and $bRa$ imply $a = b$.

## 2.1.3 Functions
- **Definition**: A relation $F \subseteq A \times B$ is a function if for every $a \in A$, there exists a unique $b \in B$.
- **Types of Functions**:
  - **Injective (One-to-one)**: $F(a) = F(a')$ implies $a = a'$.
  - **Surjective (Onto)**: For every $b \in B$, there is some $a \in A$ such that $F(a) = b$.
  - **Bijective**: Both injective and surjective.

# 2.2 Equivalence Relations
## 2.2.1 Definition
An **equivalence relation** on a set $X$ is a relation that is:
1. **Reflexive**: $x R x$ for all $x \in X$.
2. **Symmetric**: $x R y$ implies $y R x$.
3. **Transitive**: $x R y$ and $y R z$ imply $x R z$.

### Equivalence Class
- The set of all elements related to $a \in A$ is called the **equivalence class** of $a$, denoted $[a]$.
  
## 2.2.2 Partitioning
- A set can be partitioned into equivalence classes based on an equivalence relation.

# 2.3 Partial and Total Orderings

## 2.3.1 Partial Order
- A **partial order** is a relation $R \subseteq A \times A$ that is **reflexive**, **transitive**, and **antisymmetric**.
- **Hasse Diagrams**: A visual representation of partial orders where elements are connected by arrows to show relationships.

## 2.3.2 Total Order
- A **total order** requires that for every pair of elements $x, y \in A$, either $x R y$ or $y R x$.

# 2.4 Special Functions
## 2.4.1 Characteristic Function
- Denoted as $1_X(a)$, it equals 1 if $a \in X$, and 0 otherwise.

## 2.4.2 Absolute Value Function
- Defined by $f(x) = |x|$, rewritten using characteristic functions.

---

# Key Points to Remember

- A **relation** between two sets is a subset of their Cartesian product.
- The **domain** of a relation is the set of elements in $A$ that have a relation to $B$.
- A **function** is a special type of relation where each element in $A$ maps to exactly one element in $B$.
- **Equivalence relations** partition sets into equivalence classes.
- **Partial orders** are reflexive, transitive, and antisymmetric. **Total orders** additionally require that every pair of elements is comparable.
- **Hasse diagrams** visually represent partial orders, helping identify minimal and maximal elements.