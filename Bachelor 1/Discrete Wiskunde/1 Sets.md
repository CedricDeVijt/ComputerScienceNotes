## 1.1 Definitions and Notations
### Basic Definitions

- **Set**: A collection of objects, called **elements**.
  - Notation: Sets are represented by **uppercase letters**; elements by **lowercase letters**.
  - Example: If $a$ is in set $A$, we write **$a \in A$**. If not, **$a \notin A$**.

### Subset
- **Subset**: A set $B$ is a subset of $A$ if every element in $B$ is also in $A$.
  - Notation: **$B \subseteq A$** if every element of $B$ is in $A$.
  - **Extensionality Principle**: Two sets are equal if they contain the same elements.
    - **Equality**: $A = B$ if $A \subseteq B$ and $B \subseteq A$.

### Set Representation
- **Listing Elements**: If a set has finite elements, list them as $\{ a_1, a_2, \ldots, a_n \}$.
- **Describing by Properties**: If a set contains elements satisfying a property $P$, represent it as **$\{ x \mid x \text{ satisfies } P \}$**.

### Set Operations
1. **Union** ($A \cup B$): Elements in $A$ or $B$.
2. **Intersection** ($A \cap B$): Elements in both $A$ and $B$.
3. **Difference** ($A \setminus B$): Elements in $A$ but not in $B$.
4. **Symmetric Difference** ($A \Delta B$): Elements in either $A$ or $B$, but not in both.

### Properties of Set Operations
- **Associative**: $(A \cup B) \cup C = A \cup (B \cup C)$
- **Commutative**: $A \cup B = B \cup A$
- **Distributive**: $A \cap (B \cup C) = (A \cap B) \cup (A \cap C)$

## 1.2 Important Set Types
- **Empty Set** ($\emptyset$): The unique set with no elements.
- **Singleton**: A set with only one element.
- **Universal Set** ($V$): The fixed larger set within which all sets are considered.
- **Complement**: For a set $A$ in the universal set $V$, the complement $\overline{A} = V \setminus A$.

### Complement Properties
- **Identity**: $A \cup \emptyset = A$, $A \cap V = A$
- **Double Complement**: $(\overline{A}) = A$
- **De Morgan’s Laws**:
  - $\overline{A \cup B} = \overline{A} \cap \overline{B}$
  - $\overline{A \cap B} = \overline{A} \cup \overline{B}$

## 1.3 Families of Sets
- **Definition**: A collection of sets, often noted as $\mathcal{A}, \mathcal{B}$, etc.
- **Union of Families**: **$\bigcup \mathcal{A} = \{ x \mid \exists A \in \mathcal{A} : x \in A \}$**
- **Intersection of Families**: **$\bigcap \mathcal{A} = \{ x \mid \forall A \in \mathcal{A} : x \in A \}$**

## 1.4 Power Set
- **Definition**: The set of all subsets of a set $A$, including $\emptyset$ and $A$ itself.
  - Notation: **$2^A$** or **$\mathcal{P}(A)$**
  - **Example**: For $A = \{0,1\}$, **$\mathcal{P}(A) = \{\emptyset, \{0\}, \{1\}, \{0,1\}\}$**

## 1.5 Cartesian Product
- **Definition**: An ordered pair where order matters, denoted as $(a, b)$.
  - For sets $A_1, \ldots, A_n$, the **Cartesian product** is **$A_1 \times \cdots \times A_n = \{ (a_1, \ldots, a_n) \mid a_i \in A_i \}$**.
  - **Example**: If $A = \{1,2\}$ and $B = \{x, y\}$, **$A \times B = \{(1, x), (1, y), (2, x), (2, y)\}$**

---

**Key Points to Remember**

- **Set**: A collection of elements denoted with uppercase letters.
- **Subset**: $B \subseteq A$ means all elements in $B$ are in $A$.
- **Empty Set** ($\emptyset$): Unique set with no elements.
- **Union** ($\cup$) and **Intersection** ($\cap$): Basic operations to combine sets.
- **Complement**: For set $A$, $\overline{A} = V \setminus A$.
- **Power Set**: Set of all subsets of $A$.
- **Cartesian Product**: Ordered pairs from multiple sets.