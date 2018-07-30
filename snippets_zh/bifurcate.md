### bifurcate

Splits values into two groups. If an element in `filter` is truthy, the corresponding element in the collection belongs to the first group; otherwise, it belongs to the second group.

Use `Array.reduce()` and `Array.push()` to add elements to groups, based on `filter`.

```js
const bifurcate = (arr, filter) =>
  arr.reduce((acc, val, i) => (acc[filter[i] ? 0 : 1].push(val), acc), [[], []]);
```

```js
bifurcate(['beep', 'boop', 'foo', 'bar'], [true, true, false, true]); // [ ['beep', 'boop', 'bar'], ['foo'] ]
```

^^^^ADD

我们可以再一次感受到 `Array.prototype.reduce()` 的方便之处，从写法上自动隐式声明一个变量，每次遍历都操作该变量，并最终返回该变量的值。
在写法上，这是一个优雅的提升。

例如：

```js
const sum = arr => arr.reduce( (acc,val) => acc+=val, 0 )
console.log(sum([1,2,3,4,5]))

// 普通版
const sum0 = arr => {
  let result = 0
  arr.forEach(val => result += val)
  return result
}
console.log(sum0([1,2,3,4,5]))
```

这个函数，应用场景不够强有力。因为两个参数都是数组，并且没有强有力的对应关系。
不过对于 `Array.prototype.reduce()` 的使用值得我们学习。