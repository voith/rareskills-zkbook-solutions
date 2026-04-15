# Chapter 1: P vs NP and Its Application to Zero Knowledge Proofs

## Notes

- A zero-knowledge system lets a prover convince a verifier that a statement is true without revealing the underlying secret or witness.
- Only NP problems can be used for zero-knowledge systems, meaning problems where a proposed solution is easy to verify but hard to find.
- A boolean circuit is an NP problem.
- All problems in P and NP can be verified by transforming them into boolean formulas and showing a solution to the formula.
- To express a Boolean formula, we use `¬` for Boolean NOT, `∧` for Boolean AND, and `∨` for Boolean OR.
- For one-bit values, `A > B` can be derived from this truth table:
  
  | A | B | A > B |
  |---|---|-------|
  | 0 | 0 | 0     |
  | 0 | 1 | 0     |
  | 1 | 0 | 1     |
  | 1 | 1 | 0     |
  
  Since the output is `1` only when `A = 1` and `B = 0`, the formula is `A ∧ ¬B`.
- For one-bit values, `A = B` can be derived from this truth table:
  
  | A | B | A = B |
  |---|---|-------|
  | 0 | 0 | 1     |
  | 0 | 1 | 0     |
  | 1 | 0 | 0     |
  | 1 | 1 | 1     |
  
  Since the output is `1` when both bits are `1` or both bits are `0`, the formula is `(A ∧ B) ∨ ¬(A ∨ B)`.
- The zk-book also explored a boolean formula for the 3-coloring a map problem.

## Practice Problems

There are no problems in this chapter.
