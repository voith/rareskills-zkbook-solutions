# Chapter 3: Finite Fields and Modular Arithmetic for ZK Proofs

## Prerequisites

Let $$p$$ be a prime. In modular arithmetic modulo $$p$$, we work in the finite field $$\mathbb{F}_p$$, where values wrap around after division by $$p$$.

There are certain properties of modulo $$p$$ arithmetic that need to be remembered before working with finite fields and zero-knowledge proofs.

### Congruence

$$
a \equiv b \pmod p
$$

This means $$a$$ and $$b$$ leave the same remainder when divided by $$p$$. Equivalently, $$p$$ divides $$a - b$$.

### Addition

$$
(a + b) \bmod p
$$

This means we add first and then reduce modulo $$p$$.

### Subtraction

$$
(a - b) \bmod p
$$

This means we subtract first and then reduce modulo $$p$$.

### Multiplication

$$
(ab) \bmod p
$$

This means we multiply first and then reduce modulo $$p$$.

### Reduction Over Addition

$$
((a \bmod p) + (b \bmod p)) \bmod p \equiv (a + b) \bmod p
$$

This shows we can reduce intermediate values before or after addition.

### Reduction Over Multiplication

$$
((a \bmod p)(b \bmod p)) \bmod p \equiv (ab) \bmod p
$$

This shows we can reduce intermediate values before or after multiplication.

### Additive Identity

$$
a + 0 \equiv a \pmod p
$$

Zero does not change the value.

### Multiplicative Identity

$$
a \cdot 1 \equiv a \pmod p
$$

One does not change the value.

### Additive Inverse

$$
a + (-a) \equiv 0 \pmod p
$$

Every element has an additive inverse modulo $$p$$.

### Multiplicative Inverse

$$
a \cdot a^{-1} \equiv 1 \pmod p
$$

Every nonzero element has a multiplicative inverse modulo $$p$$ when $$p$$ is prime.

### Division

$$
\frac{a}{b} \pmod p \equiv a \cdot b^{-1} \pmod p
$$

Division modulo $$p$$ means multiplying by the inverse of $$b$$, so this is only defined when $$b \not\equiv 0 \pmod p$$.

### Cancellation

$$
ac \equiv bc \pmod p \quad \text{and} \quad c \not\equiv 0 \pmod p \Rightarrow a \equiv b \pmod p
$$

We can cancel the same nonzero factor from both sides.

### Fermat's Little Theorem

$$
a^{p-1} \equiv 1 \pmod p
$$

This holds for any $$a \not\equiv 0 \pmod p$$.

### Inverse from Fermat's Little Theorem

$$
a^{-1} \equiv a^{p-2} \pmod p
$$

This is useful for computing inverses in finite fields.

### Powers Stay in the Field

$$
a^k \bmod p \in \mathbb{F}_p
$$

Taking powers and reducing modulo $$p$$ always gives another field element.

### Why $$\mathbb{F}_p$$ Is a Field

Because $$p$$ is prime, every nonzero element has a multiplicative inverse. That is why arithmetic modulo $$p$$ forms a field rather than just a ring.

## Notes
- To find the additive inverse of $$a$$ compute $$p-a$$
- $$a^{p-2} \pmod p$$ is the multiplicative inverse of a, since $$a(a^{p-2})\equiv 1 \pmod p$$
- Code for finding the equivalent of a fraction in a modular finite field.
    ```python
    def compute_field_element_from_fraction(num, den, p):
        inv_den = pow(den, -1, p)
        return (num * inv_den) % p
    ```
- No two elements can be multiplied together to obtain zero in a finite field unless one of the elements is zero itself. This is also true of regular numbers.
-  The second square root is always the additive inverse of the first square root, just like real numbers.
 - Just because a linear system of equations over real numbers has zero, one, or infinite solutions it does not imply that the same linear system of equations over a finite field will also have zero, one or, p many solutions.
- the roots of a polynomial over real numbers does not necessarily have the same roots in a finite field.
- Polynomials in finite fields share many properties with polynomials over the real numbers:
  - A polynomial of degree $$d$$ has at most $$d$$ roots. The roots of a polynomial $$p(x)$$ are the values $$r$$ such that $$p(r) = 0$$.
  - If we add two polynomials $$p_1$$ and $$p_2$$, the degree of $$p_1 + p_2$$ is at most $$\max(\deg(p_1), \deg(p_2))$$. It can be smaller. For example, if $$p_1 = x^3 + 5x + 7$$ and $$p_2 = -x^3$$, then the cubic terms cancel.
  - Adding polynomials in a finite field follows the associative, commutative, and distributive laws.
  - If we multiply two polynomials $$p_1$$ and $$p_2$$, the roots of the product are the union of the roots of $$p_1$$ and $$p_2$$.
## Practice Problems

1. Find the multiplicative inverse of 3 modulo 5. There are only 5 possibilities, so try all of them and see which ones work.

   Solution:

   Try values modulo `5` until the product is congruent to `1`:

   - $$3 \cdot 0 = 0 \not\equiv 1 \pmod 5$$
   - $$3 \cdot 1 = 3 \not\equiv 1 \pmod 5$$
   - $$3 \cdot 2 = 6 \equiv 1 \pmod 5$$

   So,

   $$3^{-1} \equiv 2 \pmod 5$$

2. What is the multiplicative inverse of 50 in the finite field p=51? You do not need Python to compute this, see the principles described in “General rules of multiplicative inverses.”

   Solution:

   We need to find the multiplicative inverse of

   $$50 \pmod{51}$$

   Notice that this is of the form $$(p - 1) \pmod p$$. The inverse of $$(p - 1) \pmod p$$ is $$p - 1$$.

   Hence, $$50$$ is the inverse of $$50 \pmod{51}$$.


3. Use Python to compute the multiplicative inverse of 288 in the finite field of p = 311. You can check your work by validating that (288 * answer) % 311 == 1

    ```python
    p = 311
    inverse = pow(288, -1, p)
    print(f"inverse of 288 mod {p} = {inverse}")
    assert (288 * inverse) % 311 == 1
    ```

4. Verify the claimed square roots in the table are correct in the finite field modulo 11.
    | Element | 1st Square Root | 2nd Square Root  |
    |--------|------------------|------------------|
    | 0      | 0                | n/a              |
    | 1      | 1                | 10               |
    | 3      | 5                | 6                |
    | 4      | 2                | 9                |
    | 5      | 4                | 7                |
    | 9      | 3                | 8                |

    Solution:

    We are in the field:
    $$\mathbb{F}_{11} = \{0,1,2,\dots,10\}$$

    We need to calculate:
    $$x^2 \bmod 11 \quad \forall x \in \mathbb{F}_{11}$$

    | $$x$$ | $$x^2$$ | $$x^2 \bmod 11$$ |
    |---|---|---|
    | $$0$$ | $$0$$ | $$0$$ |
    | $$1$$ | $$1$$ | $$1$$ |
    | $$2$$ | $$4$$ | $$4$$ |
    | $$3$$ | $$9$$ | $$9$$ |
    | $$4$$ | $$16$$ | $$5$$ |
    | $$5$$ | $$25$$ | $$3$$ |
    | $$6$$ | $$36$$ | $$3$$ |
    | $$7$$ | $$49$$ | $$5$$ |
    | $$8$$ | $$64$$ | $$9$$ |
    | $$9$$ | $$81$$ | $$4$$ |
    | $$10$$ | $$100$$ | $$1$$ |

    Now group numbers that give the same result:

    - For element 0
        $$0^2 = 0$$
      only root is 0
    - For element 1
        $$1^2 = 1,\quad 10^2 = 1$$
      roots: 1, 10
    - For element 3
        $$5^2 = 3,\quad 6^2 = 3$$
      roots: 5, 6
    - For element 4
        $$2^2 = 4,\quad 9^2 = 4$$
      roots: 2, 9
    - For element 5
        $$4^2 = 5,\quad 7^2 = 5$$
      roots: 4, 7
    - For element 9
        $$3^2 = 9,\quad 8^2 = 9$$
      roots: 3, 8
5. Use the code snippet below to compute the modular square root of 5 in the finite field of p = 19. The code will only give you one of the answers. How can you compute the other?
    ```python
    def mod_sqrt(x, p):
	assert (p - 3) % 4 == 0, "prime not 4k + 3"
	exponent = (p + 1) // 4
	return pow(x, exponent, p) # x ^ e % p
    ```
    Solution: 
    The code for `mod_sqrt(5, 19)` returns 9.
    The second square will be $$19-9 = 10$$
6. Convert the two equations to their finite field representation and see they are the same for $$p = 11$$.
  $$x + 2y = 3$$, $$4x + 8y = 1$$
  Solution:
  Rearranging the terms, we get
  $$y = -\frac{1}{2}x + \frac{3}{2}$$
  The multiplicative inverse of 2 modulo 11 is 6, and $$-6 \equiv 5 \pmod{11}$$. Hence, $$\frac{3}{2} \bmod 11 = 3 \cdot 6 \bmod 11 = 7$$.
  Therefore, the above equation becomes
  $$y = 5x + 7$$
  Now let's rearrange $$4x + 8y = 1$$. We get:
  $$y = -\frac{1}{2}x + \frac{1}{8}$$
  $$\frac{1}{8} \bmod 11 = 7$$
  Therefore, the above equation becomes
  $$y = 5x + 7$$
  which is the same as the previous equation.

7. Use the finite field
   $$p = 21888242871839275222246405745257275088548364400416034343698204186575808495617$$
   for this problem.
   A developer creates an arithmetic circuit $$x \cdot y \cdot z = 0$$ and $$x + y + z = 0$$ with the intent of constraining all the signals to be zero. Find a counterexample where the constraints are satisfied, but not all of $$x$$, $$y$$, and $$z$$ are zero.

   Solution:

   The constraint
   $$x \cdot y \cdot z = 0$$
   is satisfied whenever at least one of $$x$$, $$y$$, or $$z$$ is zero.

   Let $$x = 0$$.

   Substituting this into
   $$x + y + z = 0$$
   gives
   $$y = -z$$

   So one possible counterexample is:

   $$x = 0$$
   $$y = 1$$
   $$z = -1 \equiv 21888242871839275222246405745257275088548364400416034343698204186575808495616 \pmod{21888242871839275222246405745257275088548364400416034343698204186575808495617}$$
8. A developer creates a circuit with the polynomial
   $$x^2 + 2x + 3 = 11$$
   and proves that $$2$$ is a solution. What is the other solution?
   Hint: rewrite the circuit as
   $$x^2 + 2x - 8 = 0$$
   then factor the polynomial by hand to find the roots. Finally, compute the congruent element of the root in the finite field to find the other solution. Use
   $$p = 21888242871839275222246405745257275088548364400416034343698204186575808495616$$

   Solution:

   Rewriting the equation gives
   $$x^2 + 2x - 8 = 0$$

   This has roots $$x = 2$$ and $$x = -4$$.

   Hence, the other solution is
   $$x = -4 \equiv 21888242871839275222246405745257275088548364400416034343698204186575808495613 \pmod{21888242871839275222246405745257275088548364400416034343698204186575808495616}$$
