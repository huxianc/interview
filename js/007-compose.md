`compose` 函数可以接收多个独立的函数作为参数，然后将这些函数进行组合串联，最终返回一个“组合函数”。

## es6

```js
function compose(...funcs) {
  const len = funcs.length;

  if (funcs.length === 0) {
    return arg => arg;
  }

  let index = len;
  while (--index) {
    if (typeof funcs[index] !== "function") {
      throw new TypeError("Expect a function");
    }
  }

  if (funcs.length === 1) {
    return funcs[0];
  }

  return funcs.reduce((a, b) => (...args) => a(b(...args)));
}
```

```js
function compose(funcs) {
  const len = funcs.length;
  let index = len;
  while (--index) {
    if (typeof funcs[index] !== "function") {
      throw new TypeError("Expected a function");
    }
  }

  return function (...args) {
    let index = 0;
    let result = len ? funcs[index].apply(this, args) : args[0];
    while (++index < len) {
      result = funcs[index].call(this, result);
    }

    return result;
  };
}
```

## 参考链接

- https://juejin.cn/post/6844903988647690254
