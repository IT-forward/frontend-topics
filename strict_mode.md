# Strict Mode

![image](https://i.ibb.co/CvBbqVs/Webp-net-resizeimage.png)

Hammamizga ma'lumki javascrit dasturlash tili qolgan tillarga qaraganda injiqligi, tushunarsizligi, kamchiliklarga boyligi bilan boshqa tillardan ajralib turadi.
Buning sababi javascript dasturlash tili yaratuvchisi **Brendan Eich** uni atigi 10 kun ichida yaratganligidadir.

JavaScript dasturlash tilining kamchiliklaridan biri unda o'zgaruvchini maxsus `let`, `const`, `var` kalit so'zisiz ham yaratsa bo'lishida.

```js
num = 123;
console.log(num); // 123
```

Tilning bu kamchiligi vaqti kelganda sizga yetarlicha muammo tug'dirishi mumkin.

ES5'dan boshlab tildagi bunday kamchiliklarni bartaraf etish uchun [**strict mode**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode) degan texnologiya kiritilgan.

Bu texnologiyadan foydalanish uchun siz kodingizda `'use strict';` statement'dan foydanshingiz kerak bo'ladi. Va uning tasiri shu kod ishlatilgan qatordan pastki qism uchun hisoblanadi.

```js
"use strict";

num = 123;
console.log(num); // ReferenceError: num is not defined
```

Ko'rib turganingizdek strict mode ishlatilganda yuqoridagi kamchilik bartaraf etiladi.

> Eslatma: strict mode scope element hisoblanadi. Ya'ni uni aniqlanish sohasi scope bilan chegaralanadi.

JavaScript tilining kamchiliklardan yana biri bu o'zgaruvchi nomi uchun unda oldindan band qilingan maxsus so'zlardan foydalanib bo'lishida.

```js
const NaN = 123;
const undefined = "book";
const interface = true;
const private = undefined;
```

Shu va shunga o'xshash ko'plab kamchiliklardan qutilish uchun strict mode juda asqotadi.

Strict Mode islatganimizda u beradigan ustunliklar:

- JavaScript'dagi silent error(bildirish bermaydigan xato) larni topib sizga bildiradi.

- JS engine'ga kodlarni optimallashtirishda yuzaga kelishi mumkin bo'lgan xatolarni topib, tuzatishga yordam beradi.

## Xulosa

- **Strict Mode** bu - javascript'dagi silent error(bildirish bermaydigan xato) larni oldini olish uchun ishlatilinadigan, ES5 da qo'shilgan yangi texnologiya.

- Bu rejimni yoqish uchun `'use strict';` kodidan foydalaniladi.
