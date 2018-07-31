### binomialCoefficient

Evaluates the binomial coefficient of two integers `n` and `k`.

Use `Number.isNaN()` to check if any of the two values is `NaN`.
Check if `k` is less than `0`, greater than or equal to `n`, equal to `1` or `n - 1` and return the appropriate result.
Check if `n - k` is less than `k` and switch their values accordingly.
Loop from `2` through `k` and calculate the binomial coefficient.
Use `Math.round()` to account for rounding errors in the calculation.

```js
const binomialCoefficient = (n, k) => {
  if (Number.isNaN(n) || Number.isNaN(k)) return NaN;
  if (k < 0 || k > n) return 0;
  if (k === 0 || k === n) return 1;
  if (k === 1 || k === n - 1) return n;
  if (n - k < k) k = n - k;
  let res = n;
  for (let j = 2; j <= k; j++) res *= (n - j + 1) / j;
  return Math.round(res);
};
```

```js
binomialCoefficient(8, 2); // 28
```

^^^^ADD

[二项式系数](https://baike.baidu.com/item/%E4%BA%8C%E9%A1%B9%E5%BC%8F%E7%B3%BB%E6%95%B0/6763242?fr=aladdin) 从组合数学上来讲的意义是：从 `n` 件物品中，不分先后选取 `k` 件方法的总数。

1. 在前面判断很多的临界条件
2. 用 `ES6` 的 `Number.isNaN()` 判断是否为 `NaN`，而非 `window.isNaN` 或者 `NaN !== NaN`