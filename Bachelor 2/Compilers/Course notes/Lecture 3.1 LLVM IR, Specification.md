### Required and target competences
- **Tools needed**:
  - Familiarity with assembler (computer systems and architecture).
- **Skills obtained**:
  - Theory: Understanding Static Single Assignment (SSA) IR and control flow graph
  - Practice: Coding in LLVM IR
- **Utility**:
  - Building a compiler with LLVM IR as the target language.
## 3.1.1 LLVM IR Overview
- **LLVM IR**: 
  - The intermediate representation of LLVM, which is an assembly-like language with infinitely many registers.
- **Characteristics**:
  - Unlimited single-assignment register machine instruction set.
  - Strongly typed.
- **Representations**:
  - Human-readable assembly (.ll files).
  - Dense “bitcode” assembly (.bc files).
  - C++ classes.
### How is LLVM IR different from assembly?
- **Unlimited registers**:
  - Real CPUs have a fixed number, while LLVM IR has an infinite number.
- **Translation to real assembly**:
  - Register allocator maps infinite registers to a finite physical set.
  - Type legalisation maps LLVM types to machine types.
## 3.1.2 Static single assignment (SSA)
- **Definition**:
  - Every register can be assigned at most once, simplifying and improving optimisation results.
- **Advantages**:
  - Simplifies optimisation by making the flow of data explicit.
  - Enables easy identification of unused values.
## 3.1.3 Basic blocks and terminators
- **Basic block**: 
  - A sequence of instructions executed in order, ending with a terminator.
- **Terminator**: 
  - An intraprocedural flow-control instruction.  
### Branches and control flow
- **Branches in assembly**:
  - Manage program control flow using jumps or branches.
- **Branches in LLVM IR**:
  - Includes conditional and unconditional jumps/branches targeting blocks within the same procedure.
## 3.1.4 The control flow graph (CFG)
- **Definition**:
  - Graph-based representation of program execution paths.
  - Nodes correspond to basic blocks, edges represent control flow.
### The Phi function
- **Definition**:
  - Assigns a value depending on the predecessor of the current block in LLVM IR.
- **Usage**:
  - Selects values based on branch conditions.
### Assigning constants
- **Challenge**:
  - No direct LLVM IR instruction for assigning constants to registers.
- **Solution**:
  - Utilize select instruction to assign constants without jumps.
### Further questions
- **Minimising Phi usage**:
  - Using node dominance and dominance frontier to characterise when Phi instructions are needed.
- **Minimising register usage**:
  - Register allocation strategies, including Chaitin's algorithm and Sethi-Ullman algorithm.
