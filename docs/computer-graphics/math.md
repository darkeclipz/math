# Math functions

## Rotation matrix

This will set up a 2D rotation matrix. 
It requires an angle `a`, and returns a `mat2`.
Multiply the vector with the matrix to rotate it.

```glsl
mat2 rotate(float a) {
    float si = sin(a), co = cos(a);
    return mat2(co, si, -si, co);
}
```

!!! info
    This 2D rotation matrix can also be used for 3D rotations.
    For example, to rotate on the Y-axis:

    ```glsl
    p.xz *= rotate(angle); 
    ```

## Smoothstep

The smoothstep is, in basis, a linear interpolation of the following two functions:

 1. $f(x) = x^2$.
 2. $g(x) = 1 - (x - 1)^2$.

Which we then interpolate:

$$
h(x) = f(x)(1 -x) + g(x)x.
$$

With some algebra, clamping, and parametrizing the slope, we get the complete definition of the smoothstep function:

$$
\textrm{smoothstep}(x, t_1, t_2) := k^2(3-2k)
$$

where $k$ is

$$
\max\left\{0, \min\left\{1, \dfrac{x - t_1}{t_2 - t_1} \right\} \right\}.
$$

Implementing this in GLSL gives:

```glsl
float smoothstep(float x, float t1, float t2) {
    float k = max(0., min(1., (x - t1) / (t2 - t1)));
    return k * k * (3 - 2 * k);
}
```

## Map

This function will map $x$, with a range of $[a, b]$, to the range $[c, d]$.

```glsl
float map(float x, float start1, float stop1, float start2, float stop2) {
    return start2 + (stop2 - start2) * ((value - start1) / (stop1 - start1));
}
```