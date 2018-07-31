### bottomVisible

Returns `true` if the bottom of the page is visible, `false` otherwise.

Use `scrollY`, `scrollHeight` and `clientHeight` to determine if the bottom of the page is visible.

```js
const bottomVisible = () =>
  document.documentElement.clientHeight + window.scrollY >=
  (document.documentElement.scrollHeight || document.documentElement.clientHeight);
```

```js
bottomVisible(); // true
```

^^^^ADD

判断显示区域是否包含页面最底部区域。

判断依据：文档垂直滚出的长度 + 文档在视窗里的高度 >= 文档的可滚动长度

**私改：**

```js
const bottomVisible = () =>
  document.documentElement.clientHeight + window.scrollY >=
  (document.documentElement.scrollHeight || document.documentElement.offsetHeight || document.documentElement.clientHeight);
```
