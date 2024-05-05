## 3.2.1 Abstract syntax tree (AST)
- **Definition**:
  - Tree representation of abstract syntactic structure, focusing on semantic details.
  - It does not represent every detail in the real syntax (grammar), only structural semantically-important details.
### L-value, R-values
- *R-value*: the value of the variable (i.e. appears on the RHS of an assignment) 
- *L-value*: the location of its contents (i.e. appears on the LHS of an assignment).

**Tip**: We can modify the grammar to recognize left and right expressions and apply the correct de-referencing, based on the above ideas, using semantic actions in the assignment production rules.
## 3.2.2 Symbol table creation
- **Purpose**:
  - Record symbol declarations (type, name, scope, accessibility) for type-checking.
- **Data structure and functions**:
  - Scoping and symbol entry management.
### Scoping
To deal with variable scoping, we need
- Either a tree of symbol tables, one per block, linked bottom-up to enable symbol searches 
- or a single table with scope attributes
Every individual scope will reference their table and every table will reference tables from enclosing scopes!
### While creating the tables
Top-down traversal of the AST to create the symbol tables makes a single pass sufficient. 
- Going from top to bottom, scopes are traversed in the natural order
- Note that scopes are opened and closed in a LIFO fashion
- Hence: a stack of tables is an ideal data structure
### Search-efficient tables
- Use of hash tables for efficient symbol lookup.


# Next up
[[Lecture 4 Top-down parsing and parser generators]]