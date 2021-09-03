# JavaScript Hoisting

## Declaration Nima?

Javascriptda declaration bu - o'zgaruvchilarni e'lon qilinishi.

O'zgaruvchi e'lon qilindi degani kompyuter xotirasidan unga joy ajratildi degani.

### Variable Declaration

Variable declaration bu - o'zgaruvchilarni e'lon qilinishi.

Hozirgi paytda o'zgaruvchilarni 3 xil e'lon qilsa bo'ladi.

```js
// with var keyword. Since ES1
var name;

// with let keyword. Since ES6
let name;

// with const keyword. Since ES6
const name;
```

### Function Declaration

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

## Hoisting Nima?

Hoisting bu - javascript engine kodni o'qishidan oldin bajariladigan jarayon bo'lib, bunda har bir declaration o'z scope(aniqlanish sohasi)ini yuqorisiga joylashtiriladi.

Ya'ni js engine avval har bir scope'da uning barcha o'zgaruvchilari uchun xotiradan joy ajratib oladi va boshlang'ich qiymat (`var` uchun `undefined`) beradi. Bu jarayon tugagandan so'ng engine qaytib declaration kodlarga qaramaydi va kodni tepadan pastga qarab o'qiy boshlaydi.

Hozircha biz hoistingni faqat `var` kalit so'zi bilan ko'rib chiqaydik.

Biz odatda kodimizni quyidagi tartibda yozib o'rganganmiz.

```js
var name;

console.log(name); // undefined
```

Hoisting bilan tanishganimizdan so'ng biz kodni quyidagicha ham yoza olamiz.

```js
console.log(name); // undefined

var name;
```

Yuqoridagi kodda hech qanday `ReferenceError` bo'lmaydi, chunki `console.log()` funktsiyasiga `name` o'zgaruvchisi uchun access(ruxsat) bor.

ReferenceError odatda xotirada mavjud bo'lmagan o'zgaruvchiga murojaat qilinganda sodir bo'ladi.
Bizda esa hoisting jarayonida allaqachon `name` o'zgaruvchisi xotirada yaratilib bo'lingan.

Quyidagi kod ham hoisting ga bir misol bo'la oladi.

```js
name = "Husan";
console.log(name); // Husan

var name;
```

## Temporal Dead Zone

Tasavvur qiling sizda bir bo'sh quti bor. Siz shu qutiga bir dona olma solib, do'stingizga olib bordingiz. So'ng do'stingizdan qutini ochib, uni ichidagi narsalarni qutidan tashqariga chiqarishini so'radingiz. Tabiiyki do'stingiz quti ichidan bir dona olib chiqaradi.

Siz ertasi kuni ham do'stingizga quti olib bordingiz. Bu safar quti ichiga hech narsa solmadingiz. Va do'stingizdan yana uni ichini ochib, uni ichidagi narsalarni undan tashqariga chiqarishini so'radingiz. Shunda do'stingiz quti ichidan hech narsa olib chiqara olmaydi.

Biz yuqorida o'zgaruvchi e'lon qilinganda, unga xotiradan ma'lum joy ajratilishi haqida aytgan edik. Bu joyni biz xuddi qutiga o'xshatsak bo'ladi. O'zgaruvchiga biror qiymat berganimizda, qiymat o'sha quti ichiga solib qo'yiladi.

Endi tasavvur qiling siz o'zgaruvchi yaratdingiz-u, lekin unga qiymat bermasdan turib, `console.log(..)` orqali js engine'dan o'zgaruvchi qiymatini konsolga chiqarishini so'radingiz. JS engine xuddi do'stingiz tushgan holatga tushadi va bechora konsolga nima chiqarishini bilmay, oxiri error chiqarib yuboradi.

Siz aytishingiz mumkin bunday holatlarda engine konsolga `undefined` yoki bo'sh matn `''` chiqarsa bo'lmaydimi deb. Yo'q engine unday qila olmaydi. Sababi javascript'da `undefined` ham bo'sh matn `''` ham qiymat hisoblanadi.

Bunday o'zgaruvchilar **Temporal Dead Zone** o'zgaruvchilar deyiladi. JS engine bu o'zgaruvchilarni ko'rish huquqiga ega bo'ladi, lekin ular ustida amal bajarish huquqiga ega bo'lmaydi.
