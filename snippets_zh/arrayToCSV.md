### arrayToCSV

Converts a 2D array to a comma-separated values (CSV) string.

Use `Array.map()` and `Array.join(delimiter)` to combine individual 1D arrays (rows) into strings.
Use `Array.join('\n')` to combine all rows into a CSV string, separating each row with a newline.
Omit the second argument, `delimiter`, to use a default delimiter of `,`.

```js
const arrayToCSV = (arr, delimiter = ',') =>
  arr.map(v => v.map(x => `"${x}"`).join(delimiter)).join('\n');
```

```js
arrayToCSV([['a', 'b'], ['c', 'd']]); // '"a","b"\n"c","d"'
arrayToCSV([['a', 'b'], ['c', 'd']], ';'); // '"a";"b"\n"c";"d"'
```

^^^^ADD

1. [CSV是什么？](https://zh.wikipedia.org/wiki/%E9%80%97%E5%8F%B7%E5%88%86%E9%9A%94%E5%80%BC)
  - 纯文本
  - 一行就是一条记录。所以需要分隔符 `\n`
  - 每条记录被分隔符分割

2. 利用 `map()` 将二维数组中的元素（数组）转成字符串，得到新数组
3. 利用 `join()` 将新数组拼接成字符串
