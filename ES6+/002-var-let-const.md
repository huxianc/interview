- var 声明的变量会挂载在 window 上，而 let 和 const 声明的变量不会

```js
var a = 100;
console.log(a, window.a); // 100 100

let b = 10;
console.log(b, window.b); // 10 undefined

const c = 1;
console.log(c, window.c); // 1 undefined
```

- var 声明变量存在变量提升，let 和 const 不存在变量提升

```js
console.log(a); // undefined  ===>  a已声明还没赋值，默认得到undefined值
var a = 100;

console.log(b); // 报错：b is not defined  ===> 找不到b这个变量
let b = 10;

console.log(c); // 报错：c is not defined  ===> 找不到c这个变量
const c = 10;
```

- let 和 const 声明形成块作用域

```js

if(1){
  var a = 100;
  let b = 10;
}

console.log(a); // 100
console.log(b)  // 报错：b is not defined  ===> 找不到b这个变量

-------------------------------------------------------------

if(1){
  var a = 100;
  const c = 1;
}
console.log(a); // 100
console.log(c)  // 报错：c is not defined  ===> 找不到c这个变量
```

- 同一作用域下 let 和 const 不能声明同名变量，而 var 可以

```js
var a = 100;
console.log(a); // 100

var a = 10;
console.log(a); // 10
-------------------------------------
let a = 100;
let a = 10;

//  控制台报错：Identifier 'a' has already been declared  ===> 标识符a已经被声明了。
```

- 暂存死区

```js
var a = 100;

if (1) {
  a = 10;
  //在当前块作用域中存在a使用let/const声明的情况下，给a赋值10时，只会在当前作用域找变量a，
  // 而这时，还未到声明时候，所以控制台Error:a is not defined
  let a = 1;
}
```

```js
/*
 * 　　1、一旦声明必须赋值,不能使用null占位。
 *
 * 　　2、声明后不能再修改
 *
 * 　　3、如果声明的是复合类型数据，可以修改其属性
 *
 * */

const a = 100;

const list = [];
list[0] = 10;
console.log(list); // [10]
const obj = { a: 100 };
obj.name = "apple";
obj.a = 10000;
console.log(obj); // {a:10000,name:'apple'}
```
