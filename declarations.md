# Declarations

![declarations](https://i.ibb.co/Y3BmyPX/declarations.png)

Javascriptda declaration bu - o'zgaruvchilarni e'lon qilinishi.

O'zgaruvchi e'lon qilindi degani kompyuter xotirasidan unga joy ajratildi degani. O'zgaruvchi xotirada mavjud degani uning qiymatini javascript kodda qayta - qayta ishlatsa bo'ladi degani.

```js
let foo = 5;

console.log(foo); // 1 - marta ishlatilishi
console.log(7 + foo); // 2 - marta ishlatilishi
...
```

## Variable Declarations

Variable declaration bu - o'zgaruvchilarni e'lon qilinishi.

O'zgaruvchilar `var`, `let`, `const` kalit so'zlari yordamida e'lon qilinadi. Shulardan `let` va `const` ES6 standartida qo'shilgan bo'lib, ES6 dagi katta o'zgarishlardan biri hisoblanadi.

`var` va `let` o'zgaruvchan o'zgaruvchilarni e'lon qilish uchun ishlatiladi. Agar e'lon qilish jarayonida ularga qiymat berilmasa, boshlang'ich qiymat sifatida _undefined_ qiymati beriladi.

O'zgarmas o'zgaruvchilarni e'lon qilishda `const` kalit so'zidan foydalaniladi.

```js
var foo = 2;
let bar; // let bar = undefined;
const pi = 3.14;
```

## Function Declarations

Function declaration bu - funktsiyalarni e'lon qilinishi.

JavaScript'da funktsiyalarni 2 xil usulda e'lon qilishimiz mumkin. **function declaration** va **function expression**

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

_function declaration_'da funktsiyani uni e'lon qilinishidan yuqorida ham chaqirsa bo'ladi. Lekin, _function expression_'da bunday qilib bo'lmaydi.

```js
foo(); // foo
bar(); // ReferenceError
function foo() {
  console.log("foo");
}

const bar = function () {
  console.log("bar");
};
```

## Xulosa

- JavaScript'da o'zgaruvchilar `var`, `let`, `const` kalit so'zlari yordamida e'lon qilinadi.

- _function declaration_ orqali e'lon qilingan o'zgaruvchini declaration'dan yuqorida ham pastda ham chaqirsa bo'ladi.

- _function expression_ orqali e'lon qilingan o'zgaruvchini faqatgina declaration'dan pastda chaqirib bo'ladi.
