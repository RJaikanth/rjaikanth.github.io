---
layout: single
title: Groups and Vector Spaces

mathjax: true

header:
   overlay_image: /assets/images/posts/2021-06-10-vector-spaces/header.jpg
   teaser: /assets/images/posts/2021-06-10-vector-spaces/header.jpg
   overlay_filter: 0.5

categories:
   - Maths
   - Linear Algebra
   - Vector Spaces

---

# Groups
Consider a set $$A$$ and any operation $$*: A \times A \to A$$,
then
    
$$
G := (A, *)
$$

is a group if the following holds - 
- **Closure** of $$A$$ on $$*$$

$$
\forall x, y \in A: x * y \in A
$$

- **Associative**

$$
\forall x, y, z \in A: (x * y)*z = s * (y * z)
$$

- **Neutral Element**

$$
\exists e \in A: x * e = x \quad\forall x \in A
$$

- **Inverse Element**

$$
\exists y \in A: x * y = e \quad\forall x \in A
$$

## NOTE- 
- If a group is comnutative group, then it is called a **Albelian Group**
- The set of regular matrices, $$ A \in \mathbb{R}^{n \times n} $$ is a group with respect to matrix nultiplication and is called **General Linear Group**


# Vector Spaces
A real values vector space $$V = (\nu, +, .)$$ is a a set $$\nu$$ wit h2 operations - 

$$
+: \nu \times \nu \to \nu \quad\quad Inner Operation \\
.: \mathbb{R} \times \nu \to \nu \quad\quad Outer Operation
$$

where,
- $$(\nu, +)$$ is an **albelian group**
- **Distributivity**

$$
\forall \lambda \in \mathbb{R}, x, y \in \nu: \quad \lambda(x + y) = x\lambda + y\lambda \\
\forall \lambda, \phi \in \mathbb{R}, x \in \nu: \quad x(\lambda + \phi) = x\lambda + x\phi
$$

- **Associativity** (only for outer operation)

$$
\forall \lambda, \phi \in \mathbb{R}, x \in \nu: \quad \lambda(\phi x) = (\lambda\phi)x 
$$
 
- **Neutral Element** with respect to outer operation

$$
\forall x \in \nu: \quad 1x = x
$$

- Here, inner operation $$\implies$$ Vector addition and <br/>outer operation $$\implies$$ scalar multiplication

# Vector Subspaces
Let $$V = (\nu, +, .)$$ be a vector space and $$ \exists \upsilon \subseteq \nu: \upsilon \neq \phi$$, then 

$$
U = (\upsilon, +, .)
$$

is a vector space with + and . operations limited to $$\nu \times \nu$$ and $$\mathbb{R} \times \upsilon$$ respectively.

We write $$U \subseteq V$$ to denote this space.

To prove that U is subspace of V, we need to show
- $U \neq \phi$
- Closure of U under both operations.

# Why learn these concepts?
- Vector spaces are structured spaces in which vectors live.
- A group is a set of elements and operation odefined on these elements, that keeps some of their structures intact.
- Vector spaces are aplplied through maths, science and engineering. They are the appropriate linear-algebraic notion to deal with systems of linear equations.
- Vector space model makes it easy to compute similarity between 2 objects.
- Used in Least squares eleimination, circuit theory and computer graphics, as well as Singular Value Decomposition which is very useful technique in machine learning algorithms