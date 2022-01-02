# Multi variable derivatives

## Formal definition of the partial derivative of a two variable function

Let $f(x, y)$ be a function with two variables, then the formal definition of the partial derivative of $f$ with respect to $x$ is:

$$
\dfrac{\partial f}{\partial x} = \lim_{h \rightarrow 0} \dfrac{f(x + h, y) - f(x, y)}{h}
$$

Likewise for $f$ with respect to $y$, the partial derivative is:

$$
\dfrac{\partial f}{\partial y} = \lim_{h \rightarrow 0} \dfrac{f(x, y + h) - f(x, y)}{h}
$$

The main take away is that we give a small nudge to the variable we want to get the derivative of.