# Chapter 3: Finite Fields and Modular Arithmetic for ZK Proofs

## Prerequisites

Let $$p$$ be a prime. In modular arithmetic modulo $$p$$, we work in the finite field $$\mathbb{F}_p$$, where values wrap around after division by $$p$$.

- Congruence: $$a \equiv b \pmod p$$ means $$a$$ and $$b$$ have the same remainder when divided by $$p$$, or equivalently, $$p$$ divides $$a - b$$.
- Addition: $$(a + b) \bmod p$$ is computed by adding first and then reducing modulo $$p$$.
- Subtraction: $$(a - b) \bmod p$$ is computed by subtracting first and then reducing modulo $$p$$.
- Multiplication: $$(ab) \bmod p$$ is computed by multiplying first and then reducing modulo $$p$$.
- Reduction distributes over addition and multiplication:
  $$((a \bmod p) + (b \bmod p)) \bmod p \equiv (a + b) \bmod p$$
  $$((a \bmod p)(b \bmod p)) \bmod p \equiv (ab) \bmod p$$
- Additive identity: $$a + 0 \equiv a \pmod p$$.
- Multiplicative identity: $$a \cdot 1 \equiv a \pmod p$$.
- Additive inverse: for every $$a$$, there exists $$-a$$ such that $$a + (-a) \equiv 0 \pmod p$$.
- Multiplicative inverse: for every nonzero $$a$$, there exists $$a^{-1}$$ such that $$a \cdot a^{-1} \equiv 1 \pmod p$$.
- Division: $$a / b \pmod p$$ means $$a \cdot b^{-1} \pmod p$$, so division is only defined when $$b \not\equiv 0 \pmod p$$.
- Cancellation: if $$ac \equiv bc \pmod p$$ and $$c \not\equiv 0 \pmod p$$, then $$a \equiv b \pmod p$$.
- Fermat's Little Theorem: if $$a \not\equiv 0 \pmod p$$, then $$a^{p-1} \equiv 1 \pmod p$$.
- Inverse from Fermat's Little Theorem: if $$a \not\equiv 0 \pmod p$$, then $$a^{-1} \equiv a^{p-2} \pmod p$$.
- Powers remain in the field: $$a^k \bmod p$$ is always another element of $$\mathbb{F}_p$$.
- Since $$p$$ is prime, every nonzero element has a multiplicative inverse, which is why $$\mathbb{F}_p$$ is a field.

## Notes

Coming soon.

## Practice Problems

Coming soon.
