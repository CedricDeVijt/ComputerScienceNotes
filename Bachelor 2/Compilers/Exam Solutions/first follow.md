## Compute First2(Atom) and Follow2(Prod) based on the following grammar.
(1) S     → Exp$
(2) Exp   → Prod Exp′
(3) Exp′  → +Prod Exp′
(4)       → −Prod Exp′
(5)       → ε
(6) Prod  → Atom Prod′
(7) Prod′ → ∗Atom Prod′
(8)       → /Atom Prod′
(9)       → ε
(10) Atom → −Atom
(11)      → cst
(12)      → id
(13)      → (Exp)