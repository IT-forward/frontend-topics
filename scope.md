# JS SCOPE

![scope](https://i.ibb.co/jhKJwm7/scope.jpg)

O'tgan maqolada sizlar bilan o'zgaruvchilarni e'lon qilish ([declarations]()) haqida gaplashgan edik.

Bu maqolada esa sizlar bilan bu o'zgaruvchilardan qayerlarda foydalanib bo'ladiyu, qayerlarda foydalanib bo'lmaydi, shu haqida gaplashamiz.

JavaScript faylda yaratilgan har bir o'zgaruvchining shu faylda ta'sir etish doirasi (maydoni) bo'ladi. Bu o'zgaruvchi shu maydon ichidagina yaroqli (available), undan tashqarida esa yaroqsiz (unavailable) hisoblanadi. Bu maydon kodda `{}` sintaksisi orqali aniqlanadi va [**scope**](https://developer.mozilla.org/en-US/docs/Glossary/Scope) deb yuritiladi.

```js
function greet() {
  const name = "Husan";
  console.log(`Assalomu alaykum ${name}!`);
}

greet(); // Assalomu alaykum Husan!

console.log(name); // ReferenceError: name is not defined
```
