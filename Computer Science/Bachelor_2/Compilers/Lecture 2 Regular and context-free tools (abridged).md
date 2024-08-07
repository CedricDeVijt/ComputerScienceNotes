### Required and Target Competences
- **Tools Required**:
  - Formal language theory including regular languages, context-free grammars, and pushdown automata.
- **Skills Acquired**:
  - Understanding regular languages, implementing scanners and parsers, utilizing tools like flex.
- **Utility**:
  - Allows building compilers without manual creation of scanners or parsers.
## 2.1 Scanner Fundamentals
- **Scanner Definition**:
  - A scanner splits input into sub-strings and groups them into lexical units, providing a tokenised version of the input for parsing.
- **Grammar Explanation**:
  - A grammar specifies a formal language, crucial for defining the syntax of a programming language.
## 2.2 Building Scanners
- **Pre-DFA Era**:
  - Lexical analysers were hand-coded before scanner-generating tools based on DFAs emerged.

- **Advantages of Automatic Generation**:
  - DFAs can be automatically constructed from regular expressions, simplifying the process.
  - Automatic tools handle common prefix issues efficiently.
### Hand-built Scanners
- **Advantages**:
  - Capable of recognising beyond regular languages.
  - Hand-written scanners offer easier debugging and better efficiency.
- **Course Approach**:
  - Utilises DFA-based scanner-generating tools such as flex and ANTLR for efficiency and flexibility.
## 2.3 Recognising vs. Scanning
- **Difference**:
  - Recognition focuses on determining if a string is a lexeme, while scanning involves returning a sequence of tokens from a longer string.
### Munching Like the Best
- **Challenges**:
  - Identifying the longest match while ensuring potential extensions don't lead to stuck states.
- **Solution**:
  - Utilize look-ahead and simulate DFAs until rejection or input end to ensure maximal matches.
### Handling Multiple Matches
- **Problem**:
  - When multiple DFAs recognize the same string, prioritisation or unambiguous specifications are necessary.
- **Implementation**:
  - Techniques include ordered DFAs and language checking during scanner generation.
## 2.4 Fast Lexical Analyzer Generator
- **Flex**:
  - Generates scanners specified using regular expressions, utilizing DFAs for tokenising input strings.
## 2.5 Parsing
### The Limits of Regular Languages
- **Challenges**:
  - Regular languages may not suffice for specifying programming languages, especially for ensuring well-parenthesised expressions.
- **Counter Solution**:
  - Augment DFAs with counters or stacks for enhanced expressiveness.
### Grammars
- **Definition**:
  - A grammar is a tuple specifying variables, terminals, production rules, and start symbol, essential for formal language specification.
### Formalising Derivations
- **Definition**:
  - Derivation, sentential form, and language of a grammar concepts explained.
### Types of Grammars
- **Classes**:
  - Classified into four types: all grammars, context-sensitive, context-free, and regular, each with specific characteristics.
### A Language Hierarchy
- **Chomsky’s Hierarchy**:
  - Languages form a strict hierarchy: Regular ⊂ Context-Free ⊂ Context-Sensitive ⊂ Recursively Enumerable.
### Context-Free Languages
- **Definition**:
  - Languages defined by context-free grammars, crucial for specifying programming language syntax.
### Attribute Grammars
- **Integration with Syntax**:
  - Attribute grammars associate attributes to nonterminals, aiding in syntax and semantic analysis of programming languages.
## 2.6 Pushdown Automata
- **Definition**:
  - Nondeterministic and deterministic pushdown automata explained as models for recognising context-free languages.
### Deterministic Pushdown Automata
- **Characteristics**:
  - Defined constraints for deterministic PDAs and limitations compared to nondeterministic counterparts.
## 2.7 Conclusions
- **Key Takeaways**:
  - Grammars provide powerful tools for language specification, but challenges exist in automating recognition.
  - Attribute grammars offer a means of integrating semantics into syntax.
  - PDAs and CFGs define the same language class, but deterministic machines are preferred for efficiency.
  - Grammars can be simplified for parsing using automated tools.

# Next up
[[Lecture 3.1 LLVM IR, Specification]]

