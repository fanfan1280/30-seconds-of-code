### call

Given a key and a set of arguments, call them when given a context. Primarily useful in composition.

Use a closure to call a stored key with stored arguments.

```js
const call = (key, ...args) => context => context[key](...args);
```

```js
Promise.resolve([1, 2, 3])
  .then(call('map', x => 2 * x))
  .then(console.log); //[ 2, 4, 6 ]
const map = call.bind(null, 'map');
Promise.resolve([1, 2, 3])
  .then(map(x => 2 * x))
  .then(console.log); //[ 2, 4, 6 ]
```

^^^^ADD

1. 利用柯里化接收属性方法名和其接收的参数
2. 柯里化返回的函数用来接收上下文对象。
