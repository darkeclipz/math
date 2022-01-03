# Rendering

## Camera

```glsl
vec3 ro = vec3(0,0,-1.);
vec3 ta = vec3(0,0,0);
vec3 ww = normalize(ta-ro);
vec3 uu = normalize(cross(ww, vec3(0,1,0)));
vec3 vv = normalize(cross(uu,ww));
vec3 rd = normalize(uv.x*uu + uv.y*vv + 1.0*ww);
```

## Raymarcher

### Description

A raymarching algorithm will intersect the scene by stepping a ray into the scene. 
At each step the distance, $d$, to the nearest object is calculated with a signed distance function, which is then used as the distance to safely step forward. 
An object is hit when the distance is smaller than some $\epsilon$, for example: $d < 0.001$. 
This illustration visualizes this process.

<figure>
  <img src="https://adrianb.io/img/2016-10-01-raymarching/figure3.png" width="600" />
  <figcaption>Image by https://adrianb.io</figcaption>
</figure>

The algorithm requires a ray origin `ro`, and a ray direction `rd` as input.
The output of the algorithm is a value `t`, which is the distance from the origin to the intersection point.
This intersection point $P$ is then calculated with $P = \textrm{ro} + t\cdot \textrm{rd}.$ 

The algorithm has the following global parameters:

|Variable|Description|
|--|--|
|`MIN_MARCH_DISTANCE`|The minimum distance to the object to qualify as a hit. Lower values will increase the detail, but slow down the algorithm.|
|`MAX_MARCH_DISTANCE`|The maximum distance that a ray is allowed to travel. Larger values will render the scene further, but slow down the algorithm.|
|`MAX_MARCH_STEP`|The maximum amount of steps the algorithm is allowed to take. Increase this if the detail between complex objects is poor. Higher values will slow down the algorithm.|

### Code

```glsl
#define MIN_MARCH_DIST 0.001
#define MAX_MARCH_DIST 20.
#define MAX_MARCH_STEPS 60.
float march(in vec3 ro, in vec3 rd) {
    float t = 0.;
    float i = 0.;
    for(i=0.; i < MAX_MARCH_STEPS; i++) {
        vec3 p = ro + t*rd;
        float d = map(p);
        if(d < MIN_MARCH_DIST)
            break;
        t += d;
        if(t > MAX_MARCH_DIST)
            break;
    }
    if(i >= MAX_MARCH_STEPS) {
        t = MAX_MARCH_DIST;
    }
    return t;
}
```

[See demo](https://www.shadertoy.com/view/3tyyWm){: .md-button }

!!! info

    The algorithm requires a `map(vec3 point)` function (line 9), which is the output of a [3D SDF](#), for example:

    ```glsl
    float map(vec3 p) {
        return length(p) - 0.5; // Circle SDF
    }
    ```

### Credits

|Author|License|
|--|--|
|Lars Rotgers|Public Domain|

## Normals

A normal vector is the vector $\nabla f(\mathbf{X})$. 
This can be calculated numerically with the central differences method.

```glsl
vec3 normal(in vec3 p) {
    float eps = MIN_MARCH_DIST;
    vec2 h = vec2(eps, 0);
    return normalize(vec3(map(p+h.xyy) - map(p-h.xyy),
                          map(p+h.yxy) - map(p-h.yxy),
                          map(p+h.yyx) - map(p-h.yyx)));
}
```