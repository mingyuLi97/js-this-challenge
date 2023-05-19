<h1 align='center'><samp>js-this-challenge</samp></h1>
<p align='center'>收集 js 中各种 this 指向相关的问题</p>

## 1

```js
var a = 10;
function foo() {
  console.log("this1", this);
  console.log(window.a);
  console.log(this.a);
}
console.log("this2", this);
foo();
```

<details>
<summary>查看答案/解析</summary>

<h4>答案：</h4>

```js
// this2 Window
// this1 Window
// 10
// 10
```

<h4>解析：</h4>

```js
// 全局的 this 指向 window
// 非严格模式下，全局调用的函数 this 指向 window
// var a = 10 会在 window 上挂载 window.a = 10, 因此 window.a => 10
// this 指向 window
```

</details>

## 2

```js
"use strict";
var a = 10;
function foo() {
  console.log("this1", this);
  console.log(window.a);
  console.log(this.a);
}
console.log("this2", this);
foo();
```

<details>
<summary>查看答案/解析</summary>

<h4>答案：</h4>

```js
// 'this2' Window
// 'this1' undefined
// 10
// Uncaught TypeError: Cannot read property 'a' of undefined
```

<h4>解析：</h4>

```js
// 严格模式下，全局的 this 不受影响，仍然指向 window
// 严格模式下，全局调用的函数 this 指向 undefined
// 严格模式下，var a = 10 仍然会在 window 上挂载, 因此依然输出 10
// 上面说到函数内的 this 是 undefined，因此访问 this.a 会报错
```
