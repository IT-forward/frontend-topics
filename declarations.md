# Declarations

![declarations](https://i.ibb.co/Y3BmyPX/declarations.png)

Javascriptda declaration bu - o'zgaruvchilarni e'lon qilinishi.

O'zgaruvchi e'lon qilindi degani kompyuter xotirasidan unga joy ajratildi degani.

## Variable Declaration

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

## Function Declaration

Function declaration bu - funktsiyalarni e'lon qilinishi.

Funktsiyalarni esa 2 xil usulda e'lon qilishimiz mumkin.

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

# Temporal Dead Zone

Tasavvur qiling sizda bir bo'sh quti bor. Siz shu qutiga bir dona olma solib, do'stingizga olib bordingiz. So'ng do'stingizdan qutini ochib, uni ichidagi narsalarni qutidan tashqariga chiqarishini so'radingiz. Tabiiyki do'stingiz quti ichidan bir dona olma olib chiqaradi.

Siz ertasi kuni ham do'stingizga quti olib bordingiz. Bu safar quti ichiga hech narsa solmadingiz. Va do'stingizdan yana uni ichini ochib, uni ichidagi narsalarni undan tashqariga chiqarishini so'radingiz. Shunda do'stingiz quti ichidan hech narsa olib chiqara olmaydi.

Biz yuqorida o'zgaruvchi e'lon qilinganda unga xotiradan ma'lum joy ajratilishi haqida aytgan edik. Bu joyni biz xuddi qutiga o'xshatsak bo'ladi. O'zgaruvchiga biror qiymat berganimizda qiymat o'sha quti ichiga solib qo'yiladi.

Endi tasavvur qiling siz o'zgaruvchi yaratdingiz-u, lekin unga qiymat bermasdan turib, `console.log(..)` orqali js engine'dan o'zgaruvchi qiymatini console'ga chiqarishini so'radingiz. Shunda JS engine xuddi do'stingiz tushgan holatga tushadi va bechora console'ga nima chiqarishini bilmay, oxiri error chiqarib yuboradi.

Siz aytishingiz mumkin bunday holatlarda engine console'ga `undefined` yoki bo'sh matn (`''`) chiqarsa bo'lmaydimi deb. Yo'q, engine unday qila olmaydi. Sababi javascript'da `undefined` ham bo'sh matn (`''`) ham qiymatni bir turi hisoblanadi.

Bunday o'zgaruvchilar **Temporal Dead Zone** o'zgaruvchilar deyiladi. JS engine bu o'zgaruvchilarni xotirada bor - yo'qligini ko'rish, ularga yangi qiymat yozish huquqlariga ega, lekin ularni o'qish huquqiga ega emas.

> Eslatma: bu maqolada javascript kodimizni o'qiydigan engine web browser deb qaraladi.
