# JavaScript Hoisting

![hoisting](https://i.ibb.co/56h1fPZ/hoisting.jpg)

Bu maqolani o'qishdan oldin [declorations](https://github.com/IT-forward/frontend-topics/blob/main/declorations.md), [scope](https://github.com/IT-forward/frontend-topics/blob/main/scope.md), [temporal-dead-zone](https://github.com/IT-forward/frontend-topics/blob/husan/temporal_dead_zone/temporal_dead_zone.md) haqidagi oldingi maqolalarimizni o'qib chiqish tafsiya qilinadi.

> Eslatma: inglizchada declaration bu o'zgaruvchi e'lon qilinishi, initialization esa o'zgaruvchiga qiymat berilishi.

Hoisting bu - javascript engine kodni o'qishidan oldin bajariladigan jarayon bo'lib, bu jarayonda har bir _variable_ va _function decloration_ uchun kompyuter xotirasidan joy ajratiladi.

_Declaration_ jarayonida `var` o'zgaruvchisi boshlang'ich _undefined_ qiymat bilan initsializatsiya qilinsa, `let` va `const` o'zgaruvchilar bilan bu jarayon sodir bo'lmaydi, ular temporal dead zone da bo'lishadi.

Boshqacha qilib aytsak hoisting jarayonida barcha declaration'lar o'zlarining scope'lari yuqorisiga ko'chadi. Bu esa o'z navbatida o'zgaruvchini, uni define qilishdan oldin ham ko'rishga imkon yaratadi.

Bunga namuna sifatida _function declaration_ larni yaqqol misol qilib keltirish mumkin.

```js
catName("Tiger"); // My cat's name is Tiger

function catName(name) {
  console.log("My cat's name is " + name);
}
```

Garchi biz funktsiyamizni uni declare qilishdan oldin chaqirsakda, u to'g'ri ishlamoqda. Sababi hoisting jarayonida bu funktsiyamiz allaqachon xotirada yaratilib bo'lingan bo'ladi.

JavaScript'da hoisting faqat declaration'lar bilan bo'ladi, aslo initialization'lar bilan emas.

Agar o'zgaruvchi kodda oldin ishlatilib, so'ng declare qilinib, keyin initializatsiya qilinsa, uni qiymati sifatida uning boshlang'ich qiymati olinadi.

Bu qiymat `var` o'zgaruvchilar uchun _undefined_ ga, `let` va `const` uchun _temporal dead zone_ ga teng bo'ladi.

Masalan,

```js
console.log(num); // undefined -> bu qiymat hoistingdan keyingi qiymat
var num; // Declaration
num = 6; // Initialization
```

Quyidagi kodda o'zgaruvchi faqat initializatsiya qilinayapti, lekin declare qilinmayapti. Shu sababli bu o'zgaruvchi bilan hoisting jarayoni sodir bo'lmaydi.

```js
console.log(num); // ReferenceError: num is not defined
num = 6; // Initialization
```

Hoistingga namunalar:

1 - namuna

```js
// faqat y hoisting bo'ladi

x = 1; // x initsializatsiya qilinayapti, lekin declaration emas.
console.log(x + " " + y); // 1 undefined

var y = 2; // Declare and Initialize y
```

2 - namuna

```js
// kodda hoisting sodir bo'lmaydi, lekin o'zgaruvchilarga qiymat berilganligi sababli ularni ishlatsa bo'ladi.

a = "Cran"; // Initialize a
b = "berry"; // Initialize b

console.log(a + "" + b); // Cranberry
```

## Xulosa

- **hoisting** bu - js engine kodimizni o'qishidan avval sodir bo'ladigan jarayon bo'lib, bu jarayon o'zgaruvchilar uchun xotiradan joy ajratish jarayoni hisoblanadi.

- hoisting `var` kalit so'zi bilan bo'lganda, xotiradan ajratilgan o'zgaruvchiga boshlang'ich qiymat sifatida `undefined` qiymati beriladi.

- hoisting `let` va `const` kalit so'zlari bilan bo'lganda, xotiradan ajratilgan o'zgaruvchiga boshlang'ich qiymat sifatida hech narsa berilmaydi va bu o'zgaruvchi temporal dead zone da bo'ladi.

- hoisting function declaration orqali bo'lganda, xotiradan ajratilgan o'zgaruvchiga boshlang'ich qiymat sifatida funktsiya qiymati berib yuboriladi. Shu sababli bunday funktsiyalarni scope'ni istalgan joyida chaqish mumkin.

- hoisting function expression orqali bo'lganda, jarayon xuddi `var`, `let`, `const` dan birida bo'lgani kabi kechadi va bu shu funktsiya xususiyati u qaysi kalit so'z bilan e'lon qilinishiga bog'liq bo'ladi.
