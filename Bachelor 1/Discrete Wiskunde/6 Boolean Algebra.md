# Chapter 6: Boolean Algebra

## 6.1 Boolean Expressions and Functions

### Definition of Boolean Variables

- **Boolean Variable**: A discrete variable constrained to the binary values **0** or **1**.
- **Boolean Expression**: A formal combination of Boolean variables interconnected by the following operators:
  - **Complement ($\overline{x}$)**: The unary operation yielding **1** when the input is **0**, and vice versa.
  - **Sum ($x + y$)**: Defined by the following truth table:
    | $x$ | $y$ | $x + y$ |
    |-----|-----|---------|
    | 0 | 0 | 0 |
    | 0 | 1 | 1 |
    | 1 | 0 | 1 |
    | 1 | 1 | 1 |
  - **Product ($x \cdot y$)**: Defined by the following truth table:
    | $x$ | $y$ | $x \cdot y$ |
    | ----- | ----- | ------------- |
    | 0 | 0 | 0 |
    | 0 | 1 | 0 |
    | 1 | 0 | 0 |
    | 1 | 1 | 1 |

### Boolean Functions

- A **Boolean function** is a mapping from an $n$-dimensional Boolean vector space to a single Boolean value.
  - Example: - Function: $F(x, y, z) = x + y + x \cdot z$. - Truth Table:
    | $x$ | $y$ | $z$ | $x + y$ | $x \cdot z$ | $F(x, y, z)$ |
    |-----|-----|-----|---------|-------------|-------------|
    | 1 | 1 | 1 | 1 | 1 | 1 |
    | 1 | 1 | 0 | 1 | 0 | 1 |
    | 1 | 0 | 1 | 1 | 1 | 1 |
    | 0 | 0 | 0 | 0 | 0 | 0 |

### Key Properties

- **Number of Functions**: The total number of unique Boolean functions for $n$ variables is $2^{2^n}$.

### Fundamental Identities

| Identity                                             | Name            |
| ---------------------------------------------------- | --------------- |
| $x + x = x$                                          | Idempotent Law  |
| $x \cdot x = x$                                      | Idempotent Law  |
| $x + 0 = x$                                          | Identity Law    |
| $x \cdot 1 = x$                                      | Identity Law    |
| $x + 1 = 1$                                          | Dominance Law   |
| $x \cdot 0 = 0$                                      | Dominance Law   |
| $x + y = y + x$                                      | Commutativity   |
| $x \cdot y = y \cdot x$                              | Commutativity   |
| $x + (y + z) = (x + y) + z$                          | Associativity   |
| $x(yz) = (xy)z$                                      | Associativity   |
| $x + y \cdot z = (x + y)(x + z)$                     | Distributivity  |
| $x \cdot (y + z) = xy + xz$                          | Distributivity  |
| $\overline{x \cdot y} = \overline{x} + \overline{y}$ | De Morgan's Law |
| $\overline{x + y} = \overline{x} \cdot \overline{y}$ | De Morgan's Law |
| $x(x + y) = x$                                       | Absorption      |
| $x + \overline{x} = 1$                               | Complementarity |
| $x \cdot \overline{x} = 0$                           | Complementarity |

## 6.2 Representing Boolean Functions

### Normal Forms

- **Disjunctive Normal Form (DNF)**: A canonical representation expressed as a disjunction of minterms. Example:
  - $F(x, y, z) = \overline{x}y\overline{z} + xy\overline{z} + \overline{x}yz$.
- **Conjunctive Normal Form (CNF)**: A canonical representation expressed as a conjunction of maxterms. Example:
  - $F(x, y, z) = (x + y + z)(x + \overline{y} + z)(\overline{x} + y + z)$.

### Karnaugh Maps

- A systematic method for simplifying Boolean expressions by spatially organizing truth table outputs into adjacent groupings, facilitating term elimination.
  - Example:
    | $\overline{x}y\overline{z}$ | $\overline{x}y$ | $xy$ | $xy\overline{z}$ |
    |-------------------------------|-----------------|------|------------------|
    | X | X | | X |
    | X | | X | |
  - Simplified Expression: $F(x, y, z) = xz + y$.

## 6.3 Logical Circuits

- Boolean expressions can be directly translated into logical gate diagrams employing the following basic components:
  - **NOT Gate**: Computes the complement of a Boolean variable.
  - **AND Gate**: Computes the product of two variables.
  - **OR Gate**: Computes the sum of two variables.
- Example Circuit:
  - Expression: $((x + y) \cdot z) + u$.
  - Circuit Representation:
    - The expression is mapped to interconnected OR and AND gates.

## Key Points to Remember

- **Boolean Variables**: Defined by binary values 0 and 1.
- **Operators**:
  - Complement ($\overline{x}$): Produces the negation of a value.
  - Sum ($x + y$): Logical OR operation.
  - Product ($x \cdot y$): Logical AND operation.
- **Truth Tables**: Fundamental in defining and analyzing the behavior of Boolean functions.
- **Simplification Techniques**: Utilize fundamental identities or Karnaugh maps for optimal reduction of expressions.
- **Normal Forms**:
  - DNF: Represents functions as sums of minterms.
  - CNF: Represents functions as products of maxterms.
- **Circuit Representations**: Provide visual implementations of Boolean functions using logical gates.
- **Key Theorems**: Proficiency in De Morgan's laws, distributive properties, and absorption principles is critical for advanced simplifications.
