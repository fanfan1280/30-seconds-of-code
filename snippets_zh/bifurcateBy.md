### bifurcateBy

Splits values into two groups according to a predicate function, which specifies which group an element in the input collection belongs to. If the predicate function returns a truthy value, the collection element belongs to the first group; otherwise, it belongs to the second group.

Use `Array.reduce()` and `Array.push()` to add elements to groups, based on the value returned by `fn` for each element.

```js
const bifurcateBy = (arr, fn) =>
  arr.reduce((acc, val, i) => (acc[fn(val, i) ? 0 : 1].push(val), acc), [[], []]);
```

```js
bifurcateBy(['beep', 'boop', 'foo', 'bar'], x => x[0] === 'b'); // [ ['beep', 'boop', 'bar'], ['foo'] ]
```

^^^^ADD

这个函数相对于 `bifurcate`,适用性很高。第二个参数是一个判断函数，来定义元素的分组规则。

1. 利用 `Array.prototype.reduce()` 设置初始值存储分组结果，并最终输出该结果。
2. 将结果定义为长度为2的二维数组。第一个元素数组存储返回值为 `truthy` 的结果，第二个数组元素存储返回值为 `falsy` 的结果。
3. 三目运算符运算结果指定 `push` 到哪个数组

