# 3D SDF Shapes

## Sphere

A sphere has a single parameter `r`, which is the radius of the sphere.

<figure>
  <img src="../img/sphere.png" width="400"/>
</figure>

```glsl
float sdSphere(in vec3 p, float r) {
    return length(p) - r;
}
```

## Box

A box has three parameters, which are stored in a `vec3`. 
These are used to define the width, length, and height of the box.

<figure>
  <img src="../img/box.png" width="400"/>
</figure>

```glsl
float sdBox( vec3 p, vec3 b )
{
  vec3 q = abs(p) - b;
  return length(max(q,0.0)) + min(max(q.x,max(q.y,q.z)),0.0);
}
```

# Credits

 - https://www.iquilezles.org/www/articles/distfunctions/distfunctions.htm
