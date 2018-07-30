### attempt

Attempts to invoke a function with the provided arguments, returning either the result or the caught error object.

Use a `try... catch` block to return either the result of the function or an appropriate error.

```js
const attempt = (fn, ...args) => {
  try {
    return fn(...args);
  } catch (e) {
    return e instanceof Error ? e : new Error(e);
  }
};
```

```js
var elements = attempt(function(selector) {
  return document.querySelectorAll(selector);
}, '>_>');
if (elements instanceof Error) elements = []; // elements = []

console.log(attempt())  // TypeError: fn is not a function
```

^^^^ADD

日常中我们可能使用比较多的就是 `func && func()` 这样的写法。
但是 `attempt` 这个方法在内部帮我们 `try..catch` 了错误。

1. 使用 `try..catch` 捕捉错误
2. `catch` 中判断捕获的如果不是 `Error` 对象，就显式返回一个 `Error` 对象。
  这里这样做，可能是为了防止 `throw 'this is a error message'` 这种骚操作而做了统一返回 `Error` 的处理。
3. 请注意：该方法只能捕获同步错误
