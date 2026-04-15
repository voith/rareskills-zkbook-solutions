# Chapter 2: Arithmetic Circuits for ZK

## Notes
- One disadvantage of using a Boolean circuit to represent a solution to a problem is that it can be verbose when representing arithmetic operations, such as addition or multiplication.
- An arithmetic circuit is a system of equations using only addition, multiplication, and equality. Like a Boolean circuit, it checks that a proposed set of inputs is valid, but doesn’t compute a solution.
- Variables in an arithmetic circuit are referred to as signals.
- To express equality, we will use the === operator.

### 3-Coloring a Map

Encode the three colors as `1`, `2`, and `3`. Let `X_i` be the signal for region `i`, where `i` indexes the regions of the map.

To force every region to take one of the three allowed colors, add the constraint

`∀ i, (X_i - 1)(X_i - 2)(X_i - 3) === 0`

This works because the product is zero only when `X_i ∈ {1, 2, 3}`.

Now consider two adjacent regions with signals `X_i` and `X_j`. We want `X_i ≠ X_j`. Using the encoding `{1, 2, 3}`, the valid products are exactly `2`, `3`, and `6`.

| `X_i` | `X_j` | `X_i * X_j` | Adjacent colors valid? |
|------:|------:|------------:|------------------------|
| 1 | 1 | 1 | No |
| 1 | 2 | 2 | Yes |
| 1 | 3 | 3 | Yes |
| 2 | 1 | 2 | Yes |
| 2 | 2 | 4 | No |
| 2 | 3 | 6 | Yes |
| 3 | 1 | 3 | Yes |
| 3 | 2 | 6 | Yes |
| 3 | 3 | 9 | No |

From the table, whenever adjacent regions have different colors, `X_i * X_j ∈ {2, 3, 6}`. That gives the edge constraint

`∀ (i, j) where regions i and j are adjacent, (X_i * X_j - 2)(X_i * X_j - 3)(X_i * X_j - 6) === 0`

This equation is satisfied only when the product is `2`, `3`, or `6`, so it rules out the invalid same-color cases `(1,1)`, `(2,2)`, and `(3,3)`.

### Proving `u ≥ v`

To prove `u ≥ v`, we reduce comparison to a bit-decomposition problem. Assume `u` and `v` are at most `(n - 1)`-bit numbers. We represent `u`, `v`, and $$2^{n-1} + (u - v)$$ using Boolean signals.

First, decompose `u` and `v` into binary:

$$
\sum_{i=0}^{n-2} 2^i a_i \;===\; u
$$

$$
\sum_{i=0}^{n-2} 2^i b_i \;===\; v
$$

where each bit is constrained to be Boolean:

$$
\forall i \in \{0, \dots, n-2\}, \quad a_i(a_i - 1) \;===\; 0
$$

$$
\forall i \in \{0, \dots, n-2\}, \quad b_i(b_i - 1) \;===\; 0
$$

Next, encode

$$
2^{n-1} + (u - v)
$$

as an `n`-bit number:

$$
2^{n-1} + (u - v) \;===\; \sum_{i=0}^{n-1} 2^i c_i
$$

with Boolean constraints on the `c_i` bits:

$$
\forall i \in \{0, \dots, n-1\}, \quad c_i(c_i - 1) \;===\; 0
$$

Finally, require the most significant bit to be `1`:

$$
c_{n-1} \;===\; 1
$$

This works because $$2^{n-1} + (u - v)$$ has most significant bit `1` exactly when $$u - v \ge 0$$, which is equivalent to $$u \ge v$$

### Converting Boolean Expressions to Arithmetic Circuits

Boolean gates can be translated into arithmetic constraints by forcing the input signals to be Boolean, then writing an equation for the output signal.

#### AND Gate

To translate the Boolean expression `t = u ∧ v`, use:

```text
u(u - 1) === 0
v(v - 1) === 0
t === uv
```

Since `u` and `v` are Boolean, multiplication matches Boolean AND.

#### NOT Gate

To translate the Boolean expression `t = ¬u`, use:

```text
u(u - 1) === 0
t === 1 - u
```

If `u = 1`, then `t = 0`, and if `u = 0`, then `t = 1`.

#### OR Gate

To translate the Boolean expression `t = u ∨ v`, use:

```text
u(u - 1) === 0
v(v - 1) === 0
t === u + v - uv
```

This works because the expression `u + v - uv` has the same truth table as Boolean OR when `u` and `v` are restricted to `0` or `1`.

#### Example: Transforming `out = (x ∧ ¬y) ∨ z`

Now that we have arithmetic versions of `AND`, `NOT`, and `OR`, we can translate a larger Boolean expression by substitution.

Start with Boolean constraints on the inputs:

```text
x(x - 1) === 0
y(y - 1) === 0
z(z - 1) === 0
```

Then rewrite the expression step by step:

```text
out = (x ∧ ¬y) ∨ z
out = (x ∧ (1 - y)) ∨ z
out = (x(1 - y)) ∨ z
out = (x(1 - y)) + z - (x(1 - y))z
```

So one valid arithmetic circuit is:

```text
x(x - 1) === 0
y(y - 1) === 0
z(z - 1) === 0
out === (x(1 - y)) + z - (x(1 - y))z
```

If we expand the last equation, we get an equivalent form:

```text
out === x - xy + z - xz + xyz
```

Using the identity `x² === x` for Boolean variables, the same circuit can also be written as:

```text
x² === x
y² === y
z² === z
out === x - xy + z - xz + xyz
```

## Practice Problems
Coming soon
