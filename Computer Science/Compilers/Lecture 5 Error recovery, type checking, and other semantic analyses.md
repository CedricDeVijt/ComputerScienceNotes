### Required and Target Competences
- **Tools Required**:
	* Formal language theory (languages and machines, machines and computability)
	* Graph algorithms
- **Skills Acquired**:
	* Theory: type systems, reachability analysis, etc.
	* Practice: how to automatically check some semantical properties of the input program
- **Utility**:
	* Understanding the limits of what a compiler can do.
### Error Recovery and Repair
- *Error recovery*: The process of ignoring the current error and having the parser reach a configuration from which it can read the rest of the input.
- *Error repair*: The parser attempts to fix the input so as to obtain a valid input prefix and then continue.
- *Panic mode*: The parser skips input tokens until it finds a frequently occurring delimiter (e.g. a semicolon).
### Errors in LL(1) Parsers
- *Detection*: If no entry in the action table is enabled by the look-ahead, we have an error.
- *Recovery in recursive descent*: Every call to a non-terminal-function is given as argument some set of potential end-of-block lexical units. If an error occurs, then the function discards tokens until one such token is matched (e.g. semicolon).
### Semantic Analysis
- *Type checking*: Traversing the AST to verify that the types of all components at every node conform to the expected type for the programming language.
- *Reachability and termination*: Checking for instructions that can never be reached and verifying that constructs terminate normally.
- *Exceptions*: Verifying that thrown exceptions must be caught or listed in the construct’s throw list.
### Type Checking
- *Types as invariants*: Assigning a type to a variable is an invariant that the variable will only hold values of that type throughout the execution of the program.
- *Turing-complete, hence undecidable*: Most modern programming languages are Turing complete, so type checking is undecidable.
### Static Type Checking
- *Static type checking*: Applying inference rules to deduce types of expressions without caring about reachability of instructions.
- *Type consistency*: A single bottom-up traversal of an expression tree should allow us to determine the type of the expression and check whether the constants, variables, and operators are used consistently with their types.
### Operators
- *Checking operators*: We can check whether the types of the provided arguments are correct and the return type gives the type of the operator application.
- *Overloading and implicit casting*: Some languages support operators whose return type depends on the types of the arguments or automatic casting of certain types.
### Language-specific Subtleties
- *Implicit casting*: Some languages support automatic casting of certain types, requiring a hierarchy of types to be kept in memory during type-analysis traversal.
- *Overloaded operators*: Some languages support operators whose return type depends on the types of the arguments, requiring all overloaded versions of the operator to be tried during type checking.
### Typechecker Implementation
- *Tasks*: The checker must verify the validity of the expression given the types of the descendants and derive the type of parent expressions.
- *Implementation*: It is typically implemented as a bottom-up traversal of the AST using the symbol table.
### Reachability and Termination
- *General reachability is undecidable*: For Turing-powerful programming languages, deciding reachability amounts to deciding the halting problem.
- *Statements are the focus*: In this semantical analysis, we focus on whether (lists of) statements are reachable and terminate normally.
### Rules for Reachability and Termination
- *For a simple analysis, follow these rules*: A set of rules is provided to determine the reachability and termination of statements in a simple analysis.
### Analyzing Control-Flow Instructions
- *Remark*: Functions should never terminate normally and should always return a value.
- *If-then-else*: Both branches of a conditional statement are reachable and should be checked for reachability and termination.
### LLVM CFG
- *A control-flow graph*: Maximal statement-lists with the same reachability status are nodes of an adequate CFG for LLVM IR.
- *Tip*: Distinguish between reachability via the previous statement and reachability because of special reasons.
### Analyzing Loops
- *While loop*: The AST for a while loop should have (at least) two sub-trees: the condition expression and the block/statement-list to execute if the expression is true.
- *Constant conditions*: If the condition evaluates to a constant, the loop can be marked as abnormally terminating or the statement-list can be marked as unreachable.
### Continue, Break, Return
- *Continue, break*: We must verify that they are contained in the body of a loop.
- *Break*: It marks the immediately containing loop statement as normally terminating if it is an infinite loop.
- *Continue, break, return*: All three terminate abnormally.
### Exception-Handling
- *First thing*: Extend your symbol table so that functions and procedures have a list of possible exceptions they can throw as type information.
- *Try-catch statements (for Java)*: All catch-clause statement-lists should be reachable, exception types in catch-clauses should not "hide" each other, and the subset of checked exceptions should be covered by all catch-clauses and the type of the enclosing procedure.
### Checking Procedure Calls
- *The simple case*: For procedure calls, we must consider whether the language allows overloading and match the types of the arguments and the name of the procedure.
- *Matching formal and actual parameters*: The number of parameters should match, and the parameters should be bindable.
### Calling the Most Specific Possibility
- *Examples*: Examples are given to illustrate how the most specific procedure should be called in cases of inheritance and overloading.
### Conclusions
- Static type checking is the main task carried out during semantic analysis.
- Reachability of instructions and their effect on the control flow is also something that can be approximated.
- Correct exception handling and function-call matching is a complicated task required to compile modern OO languages.
- Many of these tasks are treated in more detail in the field of formal verification.