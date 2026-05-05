# Chapter 4: Elementary Set Theory for Programmers

## Notes

## Practice Problems

1. Assume you have a proper definition for integers. Create a well-defined set of rational numbers.

   Solution:

   $$
   S = (\mathbb{Z} \times \mathbb{Z}) \cap \{(a,b) \mid b \neq 0\}
   $$

   $$
   \mathbb{Q} = S / \sim,\quad
   (a,b) \sim (c,d) \iff ad = bc
   $$

   Reasoning:

   - The denominator cannot be zero.
   - Different pairs \((a,b)\) can represent the same rational number. For example, \(1/2 = 2/4 = 3/6\).

   $$
   \frac{a}{b} = \frac{c}{d}
   $$

   The above idea can be captured by:

   $$
   (a,b) \sim (c,d) \quad \text{iff} \quad ad = bc
   $$
