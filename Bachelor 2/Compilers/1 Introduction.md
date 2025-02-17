## 1.1 Foundations of Language Theory

### Natural vs. Formal Languages

- **Natural Languages**: Defined by vocabulary, syntax, and semantics (e.g., English). Syntax governs structure, while semantics gives meaning.
- **Formal Languages**: Abstract systems with strict syntax rules (e.g., programming languages). Focus on unambiguous structure for automated processing.

### Syntax vs. Semantics

- **Syntax**: Rules for valid sentence formation. Example: Missing semicolons in C cause syntax errors.
- **Semantics**: Meaning of syntactically valid constructs. Example: Chomsky’s nonsensical sentence _"Colorless green ideas sleep furiously"_ is syntactically correct but semantically invalid.

### Basic Definitions

- **Alphabet (Σ)**: Finite set of symbols (e.g., `{a, b}`, `{0, 1}`).
- **Word**: Finite sequence of symbols from Σ (e.g., `abba`, `101`). The empty word is denoted `ε`.
- **Language**: Set of words over Σ. Examples:
  - `L_Cid`: Valid C identifiers (e.g., `sum`, not starting with digits).
  - `L_odd`: Binary numbers ending with `1` (odd numbers).
  - **Dyck Language**: Well-parenthesized strings (e.g., `(())`, but not `)(`).

### The Membership Problem

- **Problem**: Determine if a word `w` belongs to a language `L`.
- **Applications**:
  - Validate C identifiers (`L_Cid`).
  - Check syntax of expressions (`L_alg`).
  - Detect terminating programs (`L_Cterm` – proven undecidable via the Halting Problem).

## 1.2 Formal Languages and Automata

### Language Classes

- **Regular Languages**: Recognizable by finite automata with limited memory. Examples: `L_Cid`, `L_odd`.
- **Context-Free Languages**: Require unbounded memory (e.g., stacks). Example: Dyck language (`L_()`).

### Lexical Analysis (Scanning)

- **Purpose**: Split input into lexemes (basic units) and generate tokens.
- **Token**: Pair `(id, att)` where `id` identifies the lexical unit (e.g., keyword, identifier) and `att` stores attributes (e.g., symbol table index).
- **Symbol Table**: Tracks identifiers and keywords. Handles scoping in later phases.

### Parsing

- **Abstract Syntax Tree (AST)**: Hierarchical representation of code structure.
- **Scoping**: Managed via nested symbol tables. Example:
  - Global variable `i` vs. local `i` in a function.
- **Grammar**: Specifies syntax rules (e.g., BNF for expressions).

## 1.3 Compiler Design Phases

### Lexical Analysis (Scanner)

- **Tasks**:
  - Ignore whitespace/comments.
  - Identify lexemes (e.g., `int`, `printf`).
  - Populate symbol table with identifiers.

### Syntax Analysis (Parser)

- **Tasks**:
  - Validate syntax against grammar.
  - Build AST.
  - Manage nested symbol tables for scoping.

### Semantic Analysis

- **Key Checks**:
  - **Type Consistency**: Ensure operations match operand types (e.g., `int + float`).
  - **Control Flow**: Detect unreachable code or invalid jumps (e.g., `goto` bypassing variable declarations).
  - **Scoping**: Resolve variable references across symbol tables.
- **Output**: Decorated AST with type annotations.

### Synthesis (Code Generation)

- **Optimizations**:
  - **Constant Propagation**: Replace variables with known values.
  - **Loop Unrolling**: Reduce loop overhead.
- **Intermediate Languages**:
  - **LLVM IR**: Architecture-agnostic code for portability.
  - Example: C code `if (a > b) c=1;` → LLVM intermediate representation.

## 1.4 Operations on Words and Languages

### Word Operations

- **Concatenation**: `w · v` (e.g., `aa · bb = aabb`).
- **Exponentiation**: `w^n` (e.g., `a^3 = aaa`).

### Language Operations

- **Concatenation**: `L₁ · L₂ = {w₁w₂ | w₁ ∈ L₁, w₂ ∈ L₂}`.
- **Kleene Closure**: `L*` (all concatenations of 0+ words from `L`).
  - Example: `{a}* = {ε, a, aa, ...}`.
- **Positive Closure**: `L+` (excludes `ε` unless `L` contains it).

---

## Key Points to Remember

- **Syntax vs. Semantics**: Syntax is structure; semantics is meaning.
- **Alphabet/Word/Language**: Alphabet (finite symbols), Word (symbol sequence), Language (set of words).
- **Regular vs. Context-Free**: Regular (finite memory), Context-Free (unbounded memory, e.g., stacks).
- **Compiler Phases**:
  - **Scanner**: Tokenizes input.
  - **Parser**: Validates syntax, builds AST.
  - **Semantic Analysis**: Type/scope checks.
  - **Synthesis**: Optimizes and generates code.
- **Membership Problem**: Undecidable for semantic criteria (e.g., program termination).
- **Language Operations**: Concatenation, Kleene star (`L*`), and closures.
- **Intermediate Languages**: Simplify code generation (e.g., LLVM IR).
