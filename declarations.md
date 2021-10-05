# Declarations

![declarations](https://i.ibb.co/Y3BmyPX/declarations.png)

Javascriptda declaration bu - o'zgaruvchilarni e'lon qilinishi.

O'zgaruvchi e'lon qilindi degani kompyuter xotirasidan unga joy ajratildi degani. O'zgaruvchi xotirada mavjud degani uning qiymatini javascript kodda qayta - qayta ishlatsa bo'ladi degani.

```js
let name = 'Ali';

console.log(name); // 1 - marta ishlatilishi
console.log('Salom' + name); // 2 - marta ishlatilishi
...
```

## Variable Declarations

Variable declaration bu - o'zgaruvchilarni e'lon qilinishi.

Hozirgi paytda o'zgaruvchilarni 3 xil e'lon qilsa bo'ladi.

```js
// with var keyword since ES1
var name;
// with let keyword since ES6
let name;
// with const keyword since ES6
const name;
```

## Function Declarations

Function declaration bu - funktsiyalarni e'lon qilinishi.

JavaScript'da esa funktsiyalarni 2 xil usulda e'lon qilishimiz mumkin.

```js
// function declaration
function greet() {
  console.log("Assalomu alaykum!");
}

// function expression
const greet = function () {
  console.log("Assalomu alaykum!");
};
```

## Xulosa

- JavaScript'da o'zgaruvchilarni e'lon qilish `var`, `let`, `const` kalit so'zlaridan biri orqali amalga oshiriladi.

- JavaScript'da funktsiyalarni e'lon qilish 2 xil usulda amalga oshirilishi mumkin: **function declaration** va **function expression**.
