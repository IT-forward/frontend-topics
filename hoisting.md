# JavaScript Hoisting

## Declaration

Javascriptda declaration bu - o'zgaruvchilarni e'lon qilinishi.

O'zgaruvchi e'lon qilindi degani kompyuter xotirasidan unga joy ajratildi degani.

#### Variable Declaration

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

#### Function Declaration

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

## Temporal Dead Zone

Tasavvur qiling sizda bir bo'sh quti bor. Siz shu qutiga bir dona olma solib, do'stingizga olib bordingiz. So'ng do'stingizdan qutini ochib, uni ichidagi narsalarni qutidan tashqariga chiqarishini so'radingiz. Tabiiyki do'stingiz quti ichidan bir dona olma olib chiqaradi.

Siz ertasi kuni ham do'stingizga quti olib bordingiz. Bu safar quti ichiga hech narsa solmadingiz. Va do'stingizdan yana uni ichini ochib, uni ichidagi narsalarni undan tashqariga chiqarishini so'radingiz. Shunda do'stingiz quti ichidan hech narsa olib chiqara olmaydi.

Biz yuqorida o'zgaruvchi e'lon qilinganda unga xotiradan ma'lum joy ajratilishi haqida aytgan edik. Bu joyni biz xuddi qutiga o'xshatsak bo'ladi. O'zgaruvchiga biror qiymat berganimizda qiymat o'sha quti ichiga solib qo'yiladi.

Endi tasavvur qiling siz o'zgaruvchi yaratdingiz-u, lekin unga qiymat bermasdan turib, `console.log(..)` orqali js engine'dan o'zgaruvchi qiymatini konsolga chiqarishini so'radingiz. JS engine xuddi do'stingiz tushgan holatga tushadi va bechora konsolga nima chiqarishini bilmay, oxiri error chiqarib yuboradi.

Siz aytishingiz mumkin bunday holatlarda engine konsolga `undefined` yoki bo'sh matn (`''`) chiqarsa bo'lmaydimi deb. Yo'q, engine unday qila olmaydi. Sababi javascript'da `undefined` ham bo'sh matn (`''`) ham qiymatni bir turi hisoblanadi.

Bunday o'zgaruvchilar **Temporal Dead Zone** o'zgaruvchilar deyiladi. JS engine bu o'zgaruvchilarni xotirada bor - yo'qligini ko'rish, ularga yangi qiymat yozish huquqlariga ega, lekin ularni o'qish huquqiga ega emas.

> Eslatma: bu maqolada javascript kodimizni o'qiydigan engine web borwoser deb qaraladi.

## Hoisting

Hoisting bu - javascript engine kodni o'qishidan oldin bajariladigan jarayon bo'lib, bunda har bir declaration o'z scope(aniqlanish sohasi)ini yuqorisiga joylashtiriladi.

Ya'ni js engine avval har bir scope'da uning barcha o'zgaruvchilari uchun xotiradan joy ajratib oladi. Bu jarayon tugagandan so'ng engine qaytib declaration kodlarga qaramaydi va kodni tepadan pastga qarab o'qiy boshlaydi.

Keling endi hoisting'ni har bir declaration turlari uchun ko'rib chiqamiz.

#### Hoisting var kalit so'zi bilan

Hoisting jarayoni `var` kalit so'zi orqali hosil qilingan o'zgaruvchi bilan bo'lganda, js engine dastlab o'zgaruvchi uchun xotiradan joy ajratib oladi va unga default(boshlang'ich) `undefined` qiymat beradi. So'ng scope ichidagi kodlarni o'qishni boshlaydi.

Biz odatda kodni quyidagi tartibda yozib o'rganganmiz.

```js
var name;

console.log(name); // undefined
```

Hoisting bilan tanishganimiz uchun biz kodni quyidagicha ham yoza olamiz.

```js
console.log(name); // undefined

var name;
```

Yuqoridagi kodda hech qanday `ReferenceError` sodir bo'lmaydi. Sababi `console.log()` funktsiyasi xotirada `name` o'zgaruvchisi borligini ko'ra oladi.

ReferenceError odatda xotirada mavjud bo'lmagan o'zgaruvchiga murojaat qilinganda sodir bo'ladi.
Bizda esa hoisting jarayonida allaqachon `name` o'zgaruvchisi xotirada yaratilib bo'lingan bo'ladi.

Quyidagi kod ham hoisting ga bir misol bo'la oladi.

```js
name = "Husan";
console.log(name); // Husan

var name;
```

#### Hoisting let kalit so'zi bilan

Hoisting jarayoni `let` kalit so'zi orqali hosil qilingan o'zgaruvchi bilan bo'lganda, js engine dastlab o'zgaruvchi uchun xotiradan joy ajratib oladi, lekin unga hech qanday boshlang'ich qiymat bermaydi. Ya'ni xotira bo'sh qoldiriladi. So'ng scope ichidagi kodlarni o'qishni boshlaydi.

```js
console.log(name); // ReferenceError: Cannot access 'name' before initialization

let name;
```

Yuqoridagi kodda `ReferenceError` chiqishini sababi `name` o'zgaruvchisini xotirada qiymati mavjud emasligidadir. Yoqoridagi error'da ham aynan shu narsa aytilyapti.

To'liqroq qilib aytadigan bo'lsak, bu o'zgaruvchi yuqirida aytib o'tilgan **temporal dead zone** o'zgaruvchidir.

Quyida hoisting ga yana bir misol ko'rishingiz mumkin.

```js
console.log(name); // ReferenceError: Cannot access 'name' before initialization
name = "Husan"; // in the memory: name = "Husan"
console.log(name); // Husan

let name;
```

#### Hoisting const kalit so'zi bilan

`const` kalit so'zi bilan hoisting xuddi `let` kalit so'zi bilan bo'lgani kabi bo'ladi.

Ya'ni hoisting jarayoni `const` kalit so'zi orqali hosil qilingan o'zgaruvchi bilan bo'lganda, js engine dastlab o'zgaruvchi uchun xotiradan joy ajratib oladi, lekin unga hech qanday boshlang'ich qiymat bermaydi.

Shuning uchun ham quyidagi misolda yana ReferenceError chiqadi.

```js
console.log(name); // ReferenceError: Cannot access 'name' before initialization

const name = "Husan";
```

Yuqoridagi misolda qiziq bir holatni kuzatishimiz mumkin. Biz bilamiz `const` o'zgaruvchi har doim o'zining boshlang'ich qiymati bilan e'lon qilinadi. Lekin yuqoridagi misolda yana `ReferenceError` ko'rsatilmoqda. Buning sababi nimada?

Sababi shuki `var`, `let`, `const` kalit so'zlari bilan hoisting bo'lganda, o'zgaruvchi uchun faqat xotiradan joy ajratilishi, assignment(qiymat berish) operatorlar esa kodda o'z kelish tartibida bajarilishidadir.

Yuqoridagi kodda assignment statement conole.log() statement'dan keyin kelmoqda. Shuning ushun ham `name` o'zgaruvchisi hali temporal dead zone ichida.

### Hoisting function declaration bilan

Function declaration'lar bilan hoisting jarayoni xuddi `var` kalit so'zi bilan bo'lgani kabi bo'ladi.

Ya'ni js engine dastlab funktsiya uchun xotiradan joy ajratib oladi va unga default qiymat sifatida funktsiya qiymatini berib yuboradi. So'ng scope ichidagi kodlarni o'qishni boshlaydi.

```js
function greet() {
  console.log("Assalomu alaykum!");
}

greet(); // Assalomu alaykum!
```

Yoqoridagi kodda funktsiyani e'lon qilishimiz ham, funktsiyaga qiymat berishimiz ham funktsiyani chaqirishimizdan oldin bo'layapti. O'ylaymanki siz nima uchun yuqoridagi kodda `// Assalomu alaykum!` chiqayotgan ekanligini tushundingiz.

```js
console.log(greet); // ƒ greet() { console.log("Assalomu alaykum!"); }
greet(); // Assalomu alaykum!

function greet() {
  console.log("Assalomu alaykum!");
}
```

Yuqoridagi kodda `greet` o'zgaruvchisi qiymati chiqarilganda `undefined` chiqmaganligiga sabab, hoisting jarayonida bu o'zgaruvchiga boshlang'ich qiymat sifatida funktsiya qiymati berib yuborilganligidadir.

Bundan shuni anglash mumkinki function declaration orqali yaratilgan funktsiyani, unga tegishli scope ichida uni istalgan joyda chaqirish mumkin ekan.

### Hoisting function expression bilan

Keling hoisting haqida gaplashishdan oldin function expression nima ekanligini eslab olsak.

function expression bu - o'zgaruvchiga qiymat sifatida berilgan funktsiyadir.

Quyida function expression'ga misol keltirilgan.

```js
const greet = function () {
  console.log("Assalomu alaykum!");
};
```

function expression aslida `var`, `let`, `const` kalit so'zlaridan biri orqali yaratilgan o'zgaruvchi bo'lib, unga qiymat sifatida funktsiya berilgan ekanligini inobatga olsak, function expression bilan hoisting xuddi `var`, `let`, `const` bilan bo'lgani kabi bo'ladi.

Keling uchala halat uchun ham hoisting ni ko'rib chiqamiz.

`var` kalit so'zi bilan

```js
console.log(greet); // undefined
greet(); // TypeError: greet is not a function

var greet = function () {
  console.log("Assalomu alaykum!");
};
```

`let` kalit so'zi bilan

```js
console.log(greet); // ReferenceError: Cannot access 'greet' before initialization
greet(); // ReferenceError: Cannot access 'greet' before initialization

let greet = function () {
  console.log("Assalomu alaykum!");
};
```

`const` kalit so'zi bilan

```js
console.log(greet); // ReferenceError: Cannot access 'greet' before initialization
greet(); // ReferenceError: Cannot access 'greet' before initialization

const greet = function () {
  console.log("Assalomu alaykum!");
};
```

O'ylaymanki yuqoridagi na'munalar sizga tushunarli bo'ldi.

## Xulosa

- **temporal dead zone** bu shunday hudud ekanki bu hududdagi o'zgaruvchilar uchun xotiradan joy ajratilgan, lekin ularga hech qanday qiymat berilmagan ekan. Shu sababli js engine bu o'zgaruvchilarni o'qish huquqiga ega emas ekan.

- **hoisting** bu js engine kodimizni o'qishidan avval bo'ladigan jarayon bo'lib, bu jarayon o'zgaruvchilar uchun xotiradan joy ajratish jarayoni ekan.

- hoisting `var` kalit so'zi bilan bo'lganda, xotiradan ajratilgan o'zgaruvchiga boshlang'ich qiymat sifatida `undefined` qiymati berilar ekan.

- hoisting `let` va `const` kalit so'zlari bilan bo'lganda, xotiradan ajratilgan o'zgaruvchiga boshlang'ich qiymat sifatida hech narsa berilmas ekan va bu o'zgaruvchi temporal dead zone da bo'lar ekan.

- hoisting function declaration orqali bo'lganda, xotiradan ajratilgan o'zgaruvchiga boshlang'ich qiymat sifatida funktsiya qiymati berib yuborilar ekan. Shu tufayli bunday funktsiyalarni scope ni istalgan joyida chaqish mumkin ekan.

- hoisting function expression orqali bo'lganda jarayon xuddi `var`, `let`, `const` dan birida bo'lgani kabi kechar ekan. Bu shu funktsiya qaysi kalit so'z bilan e'lon qilinishiga bog'liq ekan.
