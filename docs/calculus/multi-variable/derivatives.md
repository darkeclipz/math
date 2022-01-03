# Multi variable derivatives

## Formal definition

Let $f(x, y)$ be a function with two variables, then the formal definition of the partial derivative of $f$ with respect to $x$ is:

$$
\dfrac{\partial f}{\partial x} = \lim_{h \rightarrow 0} \dfrac{f(x + h, y) - f(x, y)}{h}
$$

Likewise for $f$ with respect to $y$, the partial derivative is:

$$
\dfrac{\partial f}{\partial y} = \lim_{h \rightarrow 0} \dfrac{f(x, y + h) - f(x, y)}{h}
$$

The main take away is that we give a small nudge to the variable we want to get the derivative of.

## Symmetry in higher order derivatives

A higher order derivative is when we take the derivative of function multiple times. This is denoted as

$$
\dfrac{\partial^2f}{\partial x^2}
$$

which means that we first take the derivative with respect to $x$, and then a second time with respect to $x$.

Likewise, we can also take the derivative with respect to $x$, and then with respect to $y$. A beautiful result of this, is that this is the same as taking the derivative first with respect to $y$, and then with respect to $x$, which means that:

$$
\dfrac{\partial^2f}{\partial x \partial y} = \dfrac{\partial^2f}{\partial y \partial x}.
$$

!!! note

    The notion of a higher order derivative is only applicable if the second derivative is continuous around a point $P$, e.g. the point we are evaluating.

## Simpler notation

If you get tired of writing $\dfrac{\partial^2f}{\partial x \partial y}$, this can be written simpler as $f_{xy}$.

## Gradient

Let $f(x_1, x_2, \ldots, x_n)$ be a multi-variable function with $n$ variables, then the gradient of $f$ is:

$$
\nabla f = \begin{bmatrix} \dfrac{\partial}{\partial x_1} \\ \dfrac{\partial}{\partial x_2} \\ \vdots \\ \dfrac{\partial}{\partial x_n}  \end{bmatrix} f = \begin{bmatrix} \dfrac{\partial f}{\partial x_1} \\ \dfrac{\partial f}{\partial x_2} \\ \vdots \\ \dfrac{\partial f}{\partial x_n}  \end{bmatrix}.
$$

The $\nabla$ (nabla) symbol denotes a vector of operators, so $\nabla f$, means that we apply the operator $\nabla$ to $f$.

