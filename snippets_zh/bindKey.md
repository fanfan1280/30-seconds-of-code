### bindKey

Creates a function that invokes the method at a given key of an object, optionally adding any additional supplied parameters to the beginning of the arguments.

Return a `function` that uses `Function.apply()` to bind `context[fn]` to `context`.
Use `Array.concat()` to prepend any additional supplied parameters to the arguments.

```js
const bindKey = (context, fn, ...args) =>
  function() {
    return context[fn].apply(context, args.concat(...arguments));
  };
```

```js
const freddy = {
  user: 'fred',
  greet: function(greeting, punctuation) {
    return greeting + ' ' + this.user + punctuation;
  }
};
const freddyBound = bindKey(freddy, 'greet');
console.log(freddyBound('hi', '!')); // 'hi fred!'
```

^^^^ADD

1. 用解构运算符处理多个参数
2. 利用柯里化，返回一个硬绑定函数，接收剩余的参数
