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

Coming soon.
