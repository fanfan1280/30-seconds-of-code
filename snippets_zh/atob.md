### atob

Decodes a string of data which has been encoded using base-64 encoding.

Create a `Buffer` for the given string with base-64 encoding and use `Buffer.toString('binary')` to return the decoded string.

```js
const atob = str => new Buffer(str, 'base64').toString('binary');
```

```js
atob('Zm9vYmFy'); // 'foobar'
```

^^^^ADD

1. 浏览器环境：
  - 不存在 `Buffer` 方法
  - `window` 对象有 `atob`、`btoa` 方法
2. `node.js` 环境：
  - 有 `Buffer` 对象
  - `new Buffer()` 的写法已经被反对了，现在官方推荐 `Buffer.form()`