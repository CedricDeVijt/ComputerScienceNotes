### Required and Target Competences
- **What tools do we need?**:
  - Graph and tree algorithms (data structures and graph algorithms).
- **What skills will we obtain?**:
  - Theory: the limits of optimal-code generation.
  - Practice: code-generation data structures, algorithms, and heuristics.
- **How will these skills be useful?**:
  - These will allow you to understand what gcc and other compilers are doing with your code.
### How Do We Compare Generated Code?
- **Program and instruction costs**:
  - Compiling and running a program are associated with costs based on the size of the generated program, its power consumption, and its running time.
### Cost Model
- **A simple cost recipe**:
  - Every instruction costs 1 unit plus the cost associated with addressing modes of the operands.
  - Operations on registers have additional cost 0.
    - Example: `addi $t0, $t1, $a2`.
  - Operations with constants or memory locations have additional cost 1.
    - Example: `addi $t0, 5, $a2`.
  - Operations with memory locations and offsets have additional cost 2.
    - Example: `lw $t2, 20($a1)`.
### Good-Code Generation
- **Minimal-cost programs**:
  - Generate the target program with minimal cost for the input program. The cost is the sum of the costs of its instructions.
- **Good code**:
  - Use basic blocks, control-flow graph, next-use information for variables, and focus on locally-good code.
### Next-Use Information
- **Next usage**:
  - Basic information for optimisations: when will a variable's contents next be used?

- **Definition (Usage)**:
  - If instruction `i` assigns to `x` and `x` is used in instruction `j`, the value of `x` at `i` is used at `j`.

- **Definition (Liveness)**:
  - If the value of `x` computed at `i` is used at `k`, then `x` is live at all `i ≤ j < k`.
### Usage and Liveness Information
- **Data structure**:
  - Associate usage and liveness information for variables with individual instructions. Temporary information can be kept in the symbol table or in a table per basic block.
- **Algorithm**:
  - Process instructions in a block from last to first.
  - For every instruction `i: x := y op z`:
    1. Attach usage and liveness information of `x, y, z` to instruction `i`.
    2. Set `x` to not live and no next use.
    3. Set `y, z` to live and their next uses to `i`.
### Example
- **Instructions**:
  - `y := 1 + 2`
  - `x := 5`
  - `w := x + y`
  - `z := x - w`
### Data Flow in a Basic Block
- **Local optimization**:
  - Construct a structure representing how information flows between variables via an in-order pass.
- **Basic block directed acyclic graph (DAG)**:
  1. A node for each initial value of variables.
  2. A node for each instruction; its children are the nodes where the operands were last defined. Nodes with the same children are merged.
  3. Nodes labeled by the operator and list of variables it defines.
  4. Nodes with values usable by successor blocks are marked live on exit.
### Example: Local Common Sub-Expressions
- **Example**:
  - Construct the DAG for:
    - `a := b + c`
    - `b := a - d`
    - `c := b + c`
    - `d := a - d`
  - Assume initial definitions `a0, b0, c0, d0`.
  - Determine nodes labeled by more than one variable.
### Using the DAG of a Basic Block
- **Code-improving transformations**:
  - Eliminate local common sub-expressions.
  - Dead-code elimination.
  - Instruction reordering.
  - Reorder operands of instruction using algebraic laws.
### Example: Dead-Code Elimination
- **Example**:
  - Construct the DAG for:
    - `a := b + c`
    - `b := b - d`
    - `c := c + d`
    - `e := b + c`
    - `return a * b`
  - Remove roots in the DAG not labeled with live variables.
### Simple, Not-Too-Bad Code-Generation
- **Data structure**:
  - Keep track of registers to minimize store/load sequences:
    1. Register descriptors: variables in registers.
    2. Address descriptors: locations of variable values.
- **Algorithm**:
  - For every instruction `i: x = y op z`:
    1. Select registers `Rx, Ry, Rz` using `getReg(x := y op z)`.
    2. Load `y` into `Ry` if necessary.
    3. Load `z` into `Rz` if necessary.
    4. Issue the instruction `Rx := Ry op Rz`.
### Notes on the Algorithm
- **Copy instructions**:
  - Copy instructions `x := y` result in no machine instruction if `Rx = Ry`.
- **End of block**:
  - Issue store instructions for live-on-exit variables currently only in registers.
- **Descriptor management**:
  - Update descriptor information following the semantics of issued machine instructions.
### Register Allocation
- **Registers for operands**:
  - `Ry` given by `getReg(x := y op z)`:
    1. If `y` in a register `r`, then `Ry = r`.
    2. If `y` not in a register and `r` is empty, then `Ry = r`.
    3. If neither, select a candidate register `r`:
      3.1. If variables in `r` have another location, return `r`.
      3.2. If only `x` is in `r` and `x ∉ {y, z}`, return `r`.
      3.3. If variables in `r` are not live, return `r`.
      3.4. Otherwise, spill variables into memory.

- **Registers for result**:
  - If `x` is being computed, a register `r` holding `x` is safe.
  - If `y` or `z` are not live after the current instruction, `Ry` or `Rz` can be safely used.
### Peephole Optimisations
- **A sliding window or peephole**:
  - Examines a sliding window over target instructions for possible replacements by shorter or faster sequences.

- **Common optimisations**:
  - Redundant-instruction elimination.
  - Flow-of-control optimisations.
  - Algebraic simplifications.
  - Use of machine idioms (e.g., auto-increments for addresses).
### Redundant Instructions: Load and Store
- **Naively-generated code**:
  - Load and store all computed values:
    - `lw $t0, ($t2)`
    - `sw $t0, ($t2)`
- **Eliminating some load-store sequences**:
  - Remove store instruction if it has no label (not a target of a jump).
### Unreachable Code Elimination
- **Constant-condition jumps**:
  - Debug information removal example:
    - `if 0 != q goto L2`
    - `print debugging information`
    - `L2:`
  - Replace conditional jump with unconditional jump and remove unreachable debugging code.
### Flow-of-Control Optimisations
- **Conditionals and jumps**:
  - Conditional statements are translated into jumps:
    - `goto L1`
    - `L1: goto L2`
  - Inline double jumps and remove unnecessary jumps if possible.
### Algebraic Simplification
- **A finer cost model**:
  - Consider the cost of arithmetic operations.
  - Example optimizations:
    - Multiplication and division by powers of 2 via shifts.
    - Division by a constant via multiplication with a magic number.
- **Identities**:
  - Eliminate instructions like `x = x + 0` or `x = x * 1`.
### Global Allocation of Registers
- **From basic blocks to programs**:
  - Store final register values used in subsequent blocks in memory.
  - Focus on keeping variable values used in loops in registers.
### Systematic Spilling via Graph Colouring
- **Two-pass algorithm**:
  - First, assume an infinite number of registers and generate code.
 - Second, allocate registers via a priority-based graph-colouring algorithm.
- **Priority**:
  - Assign priorities based on variables' appearance frequency in loops and live ranges.
- **Graph colouring**:
  - Model register allocation as a graph-colouring problem.
  - Use spill-code heuristics to minimise register spills while maintaining program correctness.