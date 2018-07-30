### average

Returns the average of two or more numbers.

Use `Array.reduce()` to add each value to an accumulator, initialized with a value of `0`, divide by the `length` of the array.

```js
const average = (...nums) => [...nums].reduce((acc, val) => acc + val, 0) / nums.length;
```

```js
average(...[1, 2, 3]); // 2
average(1, 2, 3); // 2
```

^^^^ADD

1. 利用 `Array.prototype.reduce()` 累加传入参数，得到总和。
2. 设计接收多个参数，而非接收一个数组的方式。
  可以利用简洁的解构运算符传入数组，比 `average.apply(null, [1,2,3])` 的方式简便易读。

