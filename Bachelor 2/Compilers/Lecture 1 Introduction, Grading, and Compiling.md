### Required and Target Competences
- **Tools Needed**: 
 - Formal language theory including languages and machines, machines and computability.
- **Skills to Obtain**: 
 - Understanding regular languages, adding look-ahead, grasping context-free grammars, pushdown automata practice, generating scanners automatically using flex, and implementing parsers.
- **Utility**: 
 - Enables building a compiler without manual crafting of a scanner or parser.
# 1.1 Introduction
## What are Compilers?
- *Compiler*: a program that processes programs and translates a source program $P^s$ written in some source language $L^s$ into an equivalent target program $P^t$ written in some target language $L^t$.
- They translate one formal language into another.
## Bootstrapping
*Bootstrapping*: the process of creating a compiler for a programming language using an existing compiler

- **Necessity**: Every compiler must be initially written in some language before it can compile programs in its own language.
- **Question**: The key question in bootstrapping is determining what language the first compiler should be written in.
## 1.2 Compiler Components
### Front End
- *Function*: Translates source program into intermediate representation.
- *Components*: Lexical analysis (scanning), syntactic analysis (parsing), semantic analysis.
### Middle End (Optimiser)
- *Purpose*: Improving abstract representation of code.
- *Optional*: May not be present in every compiler.
### Back End
- *Function*: Translates intermediate representation into target program.
- *Includes*: Target-specific optimisations and transformations.

## 1.3 Other components

### Lexical Units
- **Definition**: These are the individual words or multi-word expressions in a text that carry meaning. They are the individual words and multi-word expressions in the input.
- *Role*: They are the fundamental building blocks of a programming language, forming the basis for further analysis.
### Lexemes
- **Definition**: These are the abstract units that represent a set of word forms that share the same core meaning. They are the abstract representations of the meanings of the lexical units.
- *Characteristics*: They are concrete instances of identifiers, keywords, literals, etc., identified during lexical analysis.
### Tokens
- **Definition**: Tokens are pairs consisting of an identifier (id) and an attribute (att). They are the actual instances of lexical units (words or multi-word expressions) in the text after it has been tokenised (split into smaller units).
- *Purpose*: They represent recognised lexemes along with additional information that aids in their interpretation and processing.
### Symbol Table
- *Definition*: A symbol table is a data structure used by compilers to store information about identifiers in a program.
- *Contents*: It typically includes the identifier name, its type, scope, and other relevant information.
- *Purpose*: Symbol tables facilitate semantic analysis by providing a centralised repository for identifier-related data.
- *Usage*: They are consulted during parsing and semantic analysis to ensure correct usage of identifiers within the program.
## 1.3 Scanning and Parsing

### Scanning Example
- *Input*: Source code snippet.
- *Process*: Scanner splits/group input, forming lexical units.
- *Components*: Lexical unit, lexeme, token.
### Parsing Example
- *Input*: Symbols from source program.
- *Example*: Parsing arithmetic expressions with parentheses and operators.
### Abstract Syntax Trees (AST)
- *Purpose*: Representing structure of parsed code.
- *Example*: Building AST for expressions and control flow statements.
## 1.4 Obstacles and Solutions
### Scanning Obstacles
- *Challenges*: Lexical unit specification, tokenisation.
- *Solution*: Utilize regular expressions and automata.
### Parsing Challenges
- *Issues*: Syntax specification, parsing grammar.
- *Solution*: Leverage grammars and pushdown automata for parsing.
## 1.5 Semantic Analysis and Synthesis
### Semantic Analysis
- *Tasks*: Scoping, type checking, control flow validation.
- *Facilitated by*: Symbol tables built during parsing.
### Synthesis (Output)
- *Objective*: Translate abstract representation into target program.
- *Includes*: Common optimisations, intermediate representation.
### Intermediate Representation (IR)
- *Purpose*: Simplify target-dependent optimisations.
- *Example*: LLVM IR, resembling almost-assembler instructions.
