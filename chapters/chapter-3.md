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

Coming soon.

## Practice Problems

1. Find the multiplicative inverse of 3 modulo 5. There are only 5 possibilities, so try all of them and see which ones work.

   Solution:

   Try values modulo `5` until the product is congruent to `1`:

   - $$3 \cdot 0 = 0 \not\equiv 1 \pmod 5$$
   - $$3 \cdot 1 = 3 \not\equiv 1 \pmod 5$$
   - $$3 \cdot 2 = 6 \equiv 1 \pmod 5$$

   So,

   $$
   3^{-1} \equiv 2 \pmod 5
   $$

2. What is the multiplicative inverse of 50 in the finite field p=51? You do not need Python to compute this, see the principles described in “General rules of multiplicative inverses.”

   Solution:

   We need to find the multiplicative inverse of

   $$
   50 \pmod{51}
   $$

   Notice that this is of the form $$(p - 1) \pmod p$$. The inverse of $$(p - 1) \pmod p$$ is $$p - 1$$.

   Hence, $$50$$ is the inverse of $$50 \pmod{51}$$.


3. Use Python to compute the multiplicative inverse of 288 in the finite field of p = 311. You can check your work by validating that (288 * answer) % 311 == 1

    ```python
    p = 311
    inverse = pow(288, -1, p)
    print(f"inverse of 288 mod {p} = {inverse}")
    assert (288 * inverse) % 311 == 1
    ```
