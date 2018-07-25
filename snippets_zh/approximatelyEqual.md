### approximatelyEqual

Checks if two numbers are approximately equal to each other.

Use `Math.abs()` to compare the absolute difference of the two values to `epsilon`.
Omit the third parameter, `epsilon`, to use a default value of `0.001`.

1. 利用一个误差值判断约等
2. `.1 + .2 = .3` 问题
  - 判断数字相等，一般解决 `.1+.2=.3` 的问题
  - 利用一个最小误差值进行判断。JS 中一般取 `2^52`，即 `Number.EPSILON`

```js
const approximatelyEqual = (v1, v2, epsilon = 0.001) => Math.abs(v1 - v2) < epsilon;

// 引申
const numbersCloseEnoughToEqual = (v1, v2) => Math.abs(v1 - v2) < Number.EPSILON
```

```js
approximatelyEqual(Math.PI / 2.0, 1.5708); // true

numbersCloseEnoughToEqual(.1+.2, .3)  // true
```
