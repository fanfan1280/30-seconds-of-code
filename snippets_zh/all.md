### all

Returns `true` if the provided predicate function returns `true` for all elements in a collection, `false` otherwise.

Use `Array.every()` to test if all elements in the collection return `true` based on `fn`.
Omit the second argument, `fn`, to use `Boolean` as a default.

1. 利用 `Array.every()`
2. 指定默认断言函数 `Boolean`

```js
const all = (arr, fn = Boolean) => arr.every(fn);
// 私改版，数组为空返回 false
const all = (arr, fn = Boolean) => !!arr.length && arr.every(fn)
```

```js
all([4, 2, 3], x => x > 1); // true
all([1, 2, 3]); // true
```
