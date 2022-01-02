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

## Map

This function will map $x$, with a range of $[a, b]$, to the range $[c, d]$.

```glsl
float map(float x, float start1, float stop1, float start2, float stop2) {
    return start2 + (stop2 - start2) * ((value - start1) / (stop1 - start1));
}