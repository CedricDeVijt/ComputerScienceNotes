## Compute First2(Atom) and Follow2(Prod) based on the following grammar.

## The closure of {E →B + •U } includes:

(1) S → Exp$
(2) Exp → Prod Exp′
(3) Exp′ → +Prod Exp′
(4) → −Prod Exp′
(5) → ε
(6) Prod → Atom Prod′
(7) Prod′ → ∗Atom Prod′
(8) → /Atom Prod′
(9) → ε
(10) Atom → −Atom
(11) → cst
(12) → id
(13) → (Exp)

- X →•
- U →X•
- E →B + •U
- U →•X

Grammar:
(1) S → E
(2) E → B + U
(3) E → B ∗U
(4) E → U
(5) B → C
(6) C → D
(7) D → E
(8) U → X
(9) X → ε

## The closure of {S →•aA,S →a•B}includes:

Grammar:
(1) S → aA
(2) S → aB
(3) A → ε
(4) A → Aa
(5) B → b
(6) B → a

- S →•aA
- S →a•B
- A→•Aa
- B →•b
- B →•a
