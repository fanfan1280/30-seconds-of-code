### arrayToHtmlList

Converts the given array elements into `<li>` tags and appends them to the list of the given id.

Use `Array.map()`, `document.querySelector()`, and an anonymous inner closure to create a list of html tags.

```js
const arrayToHtmlList = (arr, listID) =>
  (el => (
    (el = document.querySelector('#' + listID)),
    (el.innerHTML += arr.map(item => `<li>${item}</li>`).join(''))
  ))();
```

```js
arrayToHtmlList(['item 1', 'item 2'], 'myListID');
```

^^^^ADD

1. `arrayToHtmlList()` 执行之后返回父元素最终的 `innerHTML`
2. 利用[逗号运算符](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/Comma_Operator)对父元素 `el` 操作 `innerHTML` 并返回此 `innerHTML`，又因为逗号运算符只支持表达式，所以利用匿名函数变相声明 `el`

```javascript
// 普通版
const arrayToHtmlList = (arr, listID) => {
  let el = document.querySelector('#' + listID)),
      html
  html = el.innerHTML + arr.map(item => `<li>${item}</li>`).join('')
  el.innerHTML = html
  return html
}

// 私改
const arrayToHtmlList = (arr, selector) =>
  (el => (
    (el = document.querySelector(selector)),
    (el.innerHTML += arr.map(item => `<li>${item}</li>`).join(''))
  ))();
```

从普通版可以看出来，写法上确实精简了很多。

**私改**：既然是利用 `querySelector()` 那就直接传个选择符就好了 =。=