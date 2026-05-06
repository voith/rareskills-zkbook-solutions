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
- A relation can be defined from the Cartesian product of a set with itself or from the Cartesian product of one set with another. If we have two sets $A$ and $B$, and take a subset of $A \times B$, then we say an element $a \in A$ is related to an element $b \in B$ if the ordered pair $(a,b)$ is in that subset.
- In other words, any subset of $A \times B$ defines a relation between elements of $A$ and elements of $B$.
- For example, if the relation is given by $y = x^2$, then $2$ from $X$ is related to $4$ from $Y$ because $(2,4)$ satisfies the rule. But $3$ from $X$ is not related to $6$ from $Y$ because $(3,6)$ does not satisfy $y = x^2$.
- Functions are a map that takes an element from one set and returns an element in another set.

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

4. Define a mapping (function) from integers 
{1, 2, 3, 4, 5, 6} to the set {even, odd}.

   Solution:

   Let:

   $$
   A = \{1,2,3,4,5,6\}
   $$

   $$
   B = \{\text{even}, \text{odd}\}
   $$

   $$
   A \times B = \{(a,b) \mid a \in A,\ b \in B\}
   $$

   Define the mapping as a subset:

   $$
   f = \{
   (1,\text{odd}),
   (2,\text{even}),
   (3,\text{odd}),
   (4,\text{even}),
   (5,\text{odd}),
   (6,\text{even})
   \}
   \subseteq A \times B
   $$

5. Take the Cartesian product of the polygons {triangle,square,pentagon,hexagon,heptagon,octagon} and the set of integers {0,1,2,…,8}. Define a mapping such that the polygon maps to an integer representing the number of sides. For example, the ordered pair (□,4) should be in the subset, but (△,7) should not be in the subset of the Cartesian product.

   Solution:

   Let:

   $$
   P = \{\text{triangle}, \text{square}, \text{pentagon}, \text{hexagon}, \text{heptagon}, \text{octagon}\}
   $$

   $$
   I = \{0,1,2,\dots,8\}
   $$

   Then the Cartesian product is:

   $$
   P \times I = \{(p,n) \mid p \in P,\ n \in I\}
   $$

   Define the mapping as a subset:

   $$
   f = \{
   (\text{triangle},3),
   (\text{square},4),
   (\text{pentagon},5),
   (\text{hexagon},6),
   (\text{heptagon},7),
   (\text{octagon},8)
   \}
   \subseteq P \times I
   $$

6. Define a mapping between positive integers and positive rational numbers (not the whole thing, obviously). It is possible to perfectly map the integers to rational numbers. Hint: draw a table to construct rational numbers where the columns are the numerators and the rows are the denominators. Struggle with this for at least 15 minutes before looking up the answer.


   Solution:

   Put the positive rational numbers in a table where the column is the numerator and the row is the denominator.

   |   | 1   | 2   | 3   | 4   | 5   |
   |---|-----|-----|-----|-----|-----|
   | 1 | 1/1 | 2/1 | 3/1 | 4/1 | 5/1 |
   | 2 | 1/2 | 2/2 | 3/2 | 4/2 | 5/2 |
   | 3 | 1/3 | 2/3 | 3/3 | 4/3 | 5/3 |
   | 4 | 1/4 | 2/4 | 3/4 | 4/4 | 5/4 |
   | 5 | 1/5 | 2/5 | 3/5 | 4/5 | 5/5 |

   Then traverse the table diagonally, as shown in the image: ![image](../static/counting-positive-rationals.png)

   $$
   \frac{1}{1},
   \frac{2}{1},
   \frac{1}{2},
   \frac{1}{3},
   \frac{2}{2},
   \frac{3}{1},
   \frac{4}{1},
   \frac{3}{2},
   \frac{2}{3},
   \frac{1}{4},
   \dots
   $$

   This walk eventually reaches every position in the infinite table, so every positive rational number appears somewhere in the traversal.

   However, many entries are duplicates as rational numbers:

   $$
   \frac{2}{2} = \frac{1}{1}, \quad
   \frac{2}{4} = \frac{1}{2}, \quad
   \frac{3}{3} = \frac{1}{1}
   $$

   So to create a one-to-one mapping from the positive integers to the positive rational numbers, keep a fraction only when it is in lowest terms, meaning the numerator and denominator have no common factor other than 1.

   The beginning of the mapping is:

   $$
   1 \mapsto \frac{1}{1}
   $$

   $$
   2 \mapsto \frac{2}{1}
   $$

   $$
   3 \mapsto \frac{1}{2}
   $$

   $$
   4 \mapsto \frac{1}{3}
   $$

   $$
   5 \mapsto \frac{3}{1}
   $$

   $$
   6 \mapsto \frac{4}{1}
   $$

   $$
   7 \mapsto \frac{3}{2}
   $$

   $$
   8 \mapsto \frac{2}{3}
   $$

   $$
   9 \mapsto \frac{1}{4}
   $$

   and so on.

   Note on how to traverse the table:

   Start at $1/1$. Move across one diagonal, then switch direction on the next diagonal. Equivalently, visit all fractions whose numerator plus denominator is the same before moving to the next sum. For each visited fraction $a/b$, include it in the mapping only if $\gcd(a,b)=1$. That rule removes duplicates and assigns each positive rational number to exactly one positive integer.
