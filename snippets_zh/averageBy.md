### averageBy

Returns the average of an array, after mapping each element to a value using the provided function.

Use `Array.map()` to map each element to the value returned by `fn`, `Array.reduce()` to add each value to an accumulator, initialized with a value of `0`, divide by the `length` of the array.

```js
const averageBy = (arr, fn) =>
  arr.map(typeof fn === 'function' ? fn : val => val[fn]).reduce((acc, val) => acc + val, 0) /
  arr.length;
```

```js
averageBy([{ n: 4 }, { n: 2 }, { n: 8 }, { n: 6 }], o => o.n); // 5
averageBy([{ n: 4 }, { n: 2 }, { n: 8 }, { n: 6 }], 'n'); // 5
```

^^^^ADD

是 `average` 的升级版，第二个参数用来指定如何处理参数1这个数组，是一个函数或者数组元素的成员属性名。

1. 第一步，利用 `Array.prototype.map()` 处理数组。
  1. 如果是函数，就执行这个处理函数。
  2. 否则，处理函数就变成返回成员属性名对应的值。
2. 利用 `Array.prototype.reduce()` 计算出平均值。
