# Color functions

## HSV2RGB

<figure>
  <img src="https://doc.qt.io/archives/qq/qq26-hsv-space.png" />
  <figcaption>Image by https://doc.qt.io</figcaption>
</figure>

```glsl
vec3 hsv2rgb(vec3 c) {
    vec4 K = vec4(1.0, 2.0 / 3.0, 1.0 / 3.0, 3.0);
    vec3 p = abs(fract(c.xxx + K.xyz) * 6.0 - K.www);
    return c.z * mix(K.xxx, clamp(p - K.xxx, 0.0, 1.0), c.y);
}
```