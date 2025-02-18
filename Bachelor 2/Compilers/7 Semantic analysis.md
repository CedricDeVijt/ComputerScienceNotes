## 7.1 Declarations and Type Checking

### Simplified C Grammar

- **Terminals**: `char`, `int`, `identifier`.
- **Key Grammar Rules**:
  - `declaration → typeSpec identifier;`
  - `functionDecl → typeSpec identifier() compoundStatement`
  - Rules for variable and function declarations (e.g., parameter handling).

### Derivation Tree Traversal

- **Global Scope Initialization**: Start with an empty symbol table for the global scope.
- **Declaration Handling**:
  - Traverse left subtree for type, right subtree for variable name.
  - Add entries to the current symbol table.
- **Function Declarations**:
  - Create a new symbol table for parameters.
  - Link parameter table to the parent (global) scope.
  - Recurse on the function body with the new symbol table.

## 7.2 Symbol Tables

### Structure and Operations

- **Hierarchical Tables**: Tree-like structure with parent-child links for nested scopes.
- **Key Operations**:
  - **Open Scope**: Create a new table linked to the parent.
  - **Close Scope**: Return to the parent table.
  - **Insert Symbol**: Add entries (e.g., variable type, function parameters).
  - **Lookup Symbol**: Search current and parent tables for declarations.

### Type Descriptors

- **Built-in Types**: Predefined (e.g., `int`, `char`).
- **User-Defined Types**: Represented as nested symbol tables (e.g., structs/classes).
- **Efficiency**: Hash tables for fast symbol lookup.

## 7.3 Basic Blocks

### Definition and Construction

- **Normally Terminating Instructions**: Sequential execution (no jumps).
- **Abnormally Terminating Instructions**: Jump statements (e.g., `goto`, `return`).
- **Grammar for Statements**:
  - `statementList → statement statementList | statement`
- **Traversal Algorithm**:
  1. Group consecutive normally terminating instructions.
  2. Split at abnormally terminating instructions.
  3. Replace `statementList` nodes with `basicBlock` nodes.

### Example

- **Figure 7.2**: AST for a statement list with mixed termination types.
- **Figure 7.3**: Transformed AST with basic blocks.

## 7.4 Control Flow Graphs (CFG)

### Node and Edge Creation

- **Nodes**: Basic blocks.
- **Edges**: Determined by the last instruction in a block:
  - **Normally Terminating**: Edge to the next block.
  - **Abnormally Terminating**: Edges to target blocks (e.g., `if`/`else`, `switch`).

### Handling Complex Constructs

- **Switch Statements**: Multiple edges for `case` labels.
- **Loops**:
  - Replace with `goto` and conditional jumps.
  - Add edges for loop condition evaluation and body execution.

## 7.5 Three-Address Code (TAC) and SSA

### TAC Transformation

- **Simplification**:
  - Replace expressions with temporary variables (e.g., `t = i * i`).
  - Convert loops and conditionals to `goto` statements.
- **Example (Listing 7.2)**:
  - Original `for` loop vs. TAC with labels and jumps.

### Static Single Assignment (SSA)

- **Definition**: Variables assigned once per scope.
- **Φ Function**: Resolves conflicting assignments across control flow paths (e.g., `x = Φ(y_i, y_j)`.
- **Benefits**: Simplifies optimization and analysis by eliminating variable redefinition.

---

## Key Points to Remember

- **Symbol Tables**: Hierarchical structure with scope-specific tables; use hash tables for efficient lookups.
- **Basic Blocks**: Maximal sequences of normally terminating instructions; split at jumps.
- **Control Flow Graphs**: Nodes = basic blocks, edges = execution flow determined by jumps.
- **TAC**: Simplified code with temporary variables and `goto`; foundational for code optimization.
- **SSA**: Each variable assigned once; Φ functions handle merging values from different paths.
- **Tree Traversals**: Core technique for semantic analysis, symbol table construction, and CFG generation.
