# Chapter 4: Elementary Set Theory for Programmers

## Notes

- A set is a collection of distinct objects, usually called elements.
- Sets do not care about order. For example, $\{1,2,3\}$ is the same set as $\{3,2,1\}$.
- Sets also do not count duplicates. For example, $\{1,1,2\} = \{1,2\}$.
- We write $a \in S$ to mean "a is an element of set S" and $a \notin S$ to mean it is not.
- If every element of a set $A$ is also in a set $B$, then $A$ is a subset of $B$, written $A \subseteq B$. In that case, $B$ is a superset of $A$, written $B \supseteq A$.
- If $A \subseteq B$ and $A \neq B$, then $A$ is a proper subset of $B$, written $A \subset B$.
- Two sets are equal if they contain exactly the same elements. For example, $\{1,2,3\} = \{3,2,1\}$.
- The cardinality of a set means how many elements it has. We often write this as $|S|$. For example, if $S = \{a,b,c\}$, then $|S| = 3$.
- Common number sets:
  - $\mathbb{N}$: natural numbers
  - $\mathbb{Z}$: integers
  - $\mathbb{Q}$: rational numbers
  - $\mathbb{R}$: real numbers
  - $\mathbb{C}$: complex numbers
  - $\mathbb{T}$: transcendental numbers
- An ordered pair is a pair of elements where position matters. We write it as $(a,b)$. In general, $(a,b) \neq (b,a)$ unless $a=b$.
- The Cartesian product of two sets $A$ and $B$, written $A \times B$, is the set of all ordered pairs whose first element comes from $A$ and second element comes from $B$:

  $$
  A \times B = \{(a,b) \mid a \in A,\ b \in B\}
  $$

- Example: if $A = \{1,2\}$ and $B = \{x,y\}$, then

  $$
  A \times B = \{(1,x),(1,y),(2,x),(2,y)\}
  $$

- A function can be viewed as a special subset of a Cartesian product. If $f$ is a function from $A$ to $B$, then

  $$
  f \subseteq A \times B
  $$

- The key property is that each input in $A$ is paired with exactly one output in $B$. So if $(a,b_1) \in f$ and $(a,b_2) \in f$, then $b_1 = b_2$.
- Example: if $A = \{1,2,3\}$ and $B = \{a,b\}$, then one possible function is

  $$
  f = \{(1,a),(2,b),(3,a)\}
  $$

- This is a function because every element of $A$ appears exactly once as the first coordinate of an ordered pair.

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
   - Different pairs $(a,b)$ can represent the same rational number. For example, $1/2 = 2/4 = 3/6$.

   $$
   \frac{a}{b} = \frac{c}{d}
   $$

   The above idea can be captured by:

   $$
   (a,b) \sim (c,d) \quad \text{iff} \quad ad = bc
   $$

2. Define the subset relationship between integers, rational numbers, real numbers, and complex numbers.

   Solution:

   $$
   \mathbb{Z} \subset \mathbb{Q} \subset \mathbb{R} \subset \mathbb{C}
   $$

3. Define the relationship between the set of transcendental numbers and the set of complex numbers in terms of subsets. Is it a proper subset?

   Solution:

   $$
   \mathbb{T} \subset \mathbb{C}
   $$

   Complex numbers contain all roots of polynomials. Hence, $\mathbb{T}$ is a proper subset of $\mathbb{C}$.
