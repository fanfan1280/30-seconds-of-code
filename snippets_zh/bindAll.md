### bindAll

Binds methods of an object to the object itself, overwriting the existing method.

Use `Array.forEach()` to return a `function` that uses `Function.apply()` to apply the given context (`obj`) to `fn` for each function specified.

```js
const bindAll = (obj, ...fns) =>
  fns.forEach(
    fn => (
      (f = obj[fn]),
      (obj[fn] = function() {
        return f.apply(obj);
      })
    )
  );
```

```js
var view = {
  label: 'docs',
  click: function() {
    console.log('clicked ' + this.label);
  }
};
bindAll(view, 'click');
jQuery(element).on('click', view.click); // Logs 'clicked docs' when clicked.
```

^^^^ADD

指定一个对象，和对象的一些函数名，将这些函数硬绑定到该对象上。

1. 利用解构运算符，将参数存为数组
2. 利用逗号运算符隐式声明变量，获取 `obj[fn]` 的地址是为了避免死循环
3. 最后将属性的硬绑定函数设置给对应属性
