## Give a context free grammar for the language of JSON documents.

## Give an example of a context-free grammar that is not LR(1).

## Give an example of an LL(1) grammar that is not strongly LL(1).

## Give an example of an LL(2) grammar that is not strongly LL(2).

## Give an example of an LL(k+1) language that is not LL(k). You may choose the value of k to suit your example.

## Give an example of an LR(0) language that is not LL(1).

## Give an example of an LR(1) grammar that is not LALR(1)

## Let T= {id, +}be a set of terminals. Is the following grammar LL(1)? Does it define an LL(2) language?

(1) S → E
(2) E → E + E
(3) E → id

## Let T= {cst,id,+,∗}be a set of terminals. Is the following grammar LALR(1)?

(1) Exp → Exp + Exp
(2) → Exp ∗Exp
(3) → (Exp)
(4) → id
(5) → cst

## Give an example of a grammar and a word from its language which can be deterministically parsed by an LALR(1) parser and which cannot be done by an SLR(1) parser.

## Give an example of a grammar and a word from its language which can be deterministically parsed by an LALR(1) parser thanks to ItemFollow and which cannot be done using Follow only.

## Let T= {id, assign, num}be a set of terminals. Consider the following grammar G and the language Lit defines.

(1) S → id
(2) S → V assign E
(3) V → id
(4) E → V
(5) E → num

Which of the following are true? (Several may be true!)

- G is LL(1)
- G is SLR(1)
- G is LALR(1)
- L is LL(3)
