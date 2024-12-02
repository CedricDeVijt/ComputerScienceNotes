## 6.1 Boolean Expressions and Functions

### Definition of Boolean Variables

- **Boolean Variable**: Can only take values **0** or **1**.
- **Boolean Expression**: Consists of Boolean variables combined using the following operators:

  - **Complement (̅x)**: Converts 0 to 1 and 1 to 0.
  - **Sum (x + y)**: Results defined by:
    | x | y | x+y |
    | --- | --- | --- |
    | 0 | 0 | 0 |
    | 0 | 1 | 1 |
    | 1 | 0 | 1 |
    | 1 | 1 | 1 |

- **Product (x · y)**: Results defined by:
  | x | y | x · y |
  |---|---|---|
  | 0 | 0 | 0 |
  | 0 | 1 | 0 |
  | 1 | 0 | 0 |
  | 1 | 1 | 1 |

### Boolean Functions

- A **Boolean function** maps tuples of Boolean variables to a single Boolean value.
  - Example:
    - Function: F(x, y, z) = x + y + x · z.
    - Truth Table:
      | x | y | z | x + y | x · z | F(x, y, z) |
      |---|---|---|-------|-------|-------------|
      | 1 | 1 | 1 | 1 | 1 | 1 |
      | 1 | 1 | 0 | 1 | 0 | 1 |
      | 1 | 0 | 1 | 1 | 1 | 1 |
      | 0 | 0 | 0 | 0 | 0 | 0 |

### Key Properties

- **Number of Functions**: For n variables, there are $2^{2^n}$ possible Boolean functions.

### Fundamental Identities

| Identity                   | Name            |
| -------------------------- | --------------- |
| x + x = x                  | Idempotent Law  |
| x · x = x                  | Idempotent Law  |
| x + 0 = x                  | Identity Law    |
| x · 1 = x                  | Identity Law    |
| x + 1 = 1                  | Dominance Law   |
| x · 0 = 0                  | Dominance Law   |
| x + y = y + x              | Commutativity   |
| x · y = y · x              | Commutativity   |
| x + (y + z) = (x + y) + z  | Associativity   |
| x(yz) = (xy)z              | Associativity   |
| x + y · z = (x + y)(x + z) | Distributivity  |
| x · (y + z) = xy + xz      | Distributivity  |
| ̅(x · y) = ̅x + ̅y         | De Morgan's Law |
| ̅(x + y) = ̅x · ̅y         | De Morgan's Law |
| x(x + y) = x               | Absorption      |
| x + x̅ = 1                 | Complementarity |
| x · x̅ = 0                 | Complementarity |

## 6.2 Representing Boolean Functions

### Normal Forms

- **Disjunctive Normal Form (DNF)**: Sum of minterms. Example:
  - F(x, y, z) = x̅y̅z + xy̅z + x̅yz
- **Conjunctive Normal Form (CNF)**: Product of maxterms. Example:
  - F(x, y, z) = (x + y + z)(x + y̅ + z)(x̅ + y + z)

### Karnaugh Maps

- A tool to simplify Boolean expressions by grouping adjacent terms in truth tables into rectangles.
  - Example:
    | x̅y̅ | x̅y | xy | xy̅ |
    |---------|-----|----|-----|
    | X | X | | X |
    | X | | X | |
  - Simplified Expression: F(x, y, z) = xz + y.

## 6.3 Logical Circuits

- Represent Boolean expressions using **NOT**, **AND**, and **OR** gates:
  - NOT: Outputs the complement of the input.
  - AND: Outputs the product.
  - OR: Outputs the sum.
- Example Circuit:
  - Expression: ((x + y) · z) + u.
  - Circuit Representation:
    - Combine OR and AND gates accordingly.

## Key Points to Remember

- **Boolean Variables**: Values are either 0 or 1.
- **Operators**:
  - Complement (̅x): Negates the value.
  - Sum (x + y): Logical OR.
  - Product (x · y): Logical AND.
- **Truth Tables**: Define the behavior of expressions or functions.
- **Simplification**: Use identities or Karnaugh maps to reduce expressions.
- **Normal Forms**:
  - DNF: Sum of minterms.
  - CNF: Product of maxterms.
- **Circuit Representation**: Logical gates represent Boolean functions visually.
- **Key Laws**: Master De Morgan's and distributive laws for simplifications.
