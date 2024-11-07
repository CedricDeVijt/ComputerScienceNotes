# 1.1 Definitions and Notations
## Basic Definitions

- **Set**: A collection of objects, called **elements**.
  - Notation: Sets are represented by **uppercase letters**; elements by **lowercase letters**.
  - Example: If $a$ is in set $A$, we write **$a ∈ A$**. If not, **$a ∉ A$**.

## Subset
- **Subset**: A set $B$ is a subset of $A$ if every element in $B$ is also in $A$.
  - Notation: **$B ⊆ A$** if every element of $B$ is in $A$.
  - **Extensionality Principle**: Two sets are equal if they contain the same elements.
    - **Equality**: $A = B$ if $A ⊆ B$ and $B ⊆ A$.

## Set Representation
- **Listing Elements**: If a set has finite elements, list them as ${a1, a2, ..., an}$.
- **Describing by Properties**: If a set contains elements satisfying a property $P$, represent it as **${x | x satisfies P}$**.

## Set Operations
1. **Union** ($A ∪ B$): Elements in $A$ or $B$.
2. **Intersection** ($A ∩ B$): Elements in both $A$ and $B$.
3. **Difference** ($A \ B$): Elements in $A$ but not in $B$.
4. **Symmetric Difference** ($A Δ B$): Elements in either $A$ or $B$, but not in both.

## Properties of Set Operations
- **Associative**: $(A ∪ B) ∪ C = A ∪ (B ∪ C)$
- **Commutative**: $A ∪ B = B ∪ A$
- **Distributive**: $A ∩ (B ∪ C) = (A ∩ B) ∪ (A ∩ C)$

# 1.2 Important Set Types
- **Empty Set ($∅$)**: The unique set with no elements.
- **Singleton**: A set with only one element.
- **Universal Set ($V$)**: The fixed larger set within which all sets are considered.
- **Complement**: For a set $A$ in the universal set $V$, the complement $A̅ = V \ A$.

## Complement Properties
- **Identity**: $A ∪ ∅ = A$, $A ∩ V = A$
- **Double Complement**: $(A̅)̅ = A$
- **De Morgan’s Laws**:
  - $(A ∪ B)̅ = A̅ ∩ B̅$
  - $(A ∩ B)̅ = A̅ ∪ B̅$

# 1.3 Families of Sets
- **Definition**: A collection of sets, often noted as $A$, $B$, etc.
- **Union of Families**: **$⋃A = {x | ∃A ∈ A : x ∈ A}$**
- **Intersection of Families**: **$⋂A = {x | ∀A ∈ A : x ∈ A}$**

# 1.4 Power Set
- **Definition**: The set of all subsets of a set $A$, including $∅$ and $A$ itself.
  - Notation: **$2^A$** or **$P(A)$**
  - **Example**: For $A = {0,1}$, **$P(A) = {∅, {0}, {1}, {0,1}}$**

# 1.5 Cartesian Product
- **Definition**: An ordered pair where order matters, denoted as $(a, b)$.
  - For sets $A1, ..., An$, the **Cartesian product** is **$A1 × ... × An = {(a1, ..., an) | ai ∈ Ai}$**.
  - **Example**: If $A = {1,2}$ and $B = {x, y}$, **$A × B = {(1, x), (1, y), (2, x), (2, y)}$**

---  
  
 Key Points to Remember

- **Set**: A collection of elements denoted with uppercase letters.
- **Subset**: $B ⊆ A$ means all elements in $B$ are in $A$.
- **Empty Set ($∅$)**: Unique set with no elements.
- **Union ($∪$)** and **Intersection ($∩$)**: Basic operations to combine sets.
- **Complement**: For set $A$, $A̅ = V \ A$.
- **Power Set**: Set of all subsets of $A$.
- **Cartesian Product**: Ordered pairs from multiple sets.