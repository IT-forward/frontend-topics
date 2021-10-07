# Temporal Dead Zone

![dead](https://i.ibb.co/hg4cQ55/dead-zone.png)

O'tgan maqolamizda o'zgaruvchilarni e'lon qilish ([declarations](https://github.com/IT-forward/frontend-topics/blob/main/declarations.md)) haqida gaplashgan edik. Va maqolada ES6 da o'zgaruvchilarni e'lon qilish uchun `var` kalit so'ziga qo'shimcha `let` va `const` kalit so'zlari qo'shilganligini takidlagan edik.

Bu maqolada ularni asosiy farqlaridan birini ko'rib chiqamiz.

`let` va `const` o'zgaruvchilari uchun shunday maydon borki, bu maydonda ularning qiymatlari mavjud bo'lmaydi. Bu maydon **Temporal Dead Zone** (TDZ) deb ataladi.

Bu maydonda o'zgaruvchining qiymatini o'qib bo'lmaydi. Shunday bo'lsa `ReferenceError` qaytariladi.

O'zgaruvchi uchun bu maydon [scope](https://github.com/IT-forward/frontend-topics/blob/main/scope.md) boshlanishidan unga qiymat berilgunga qadar davom etadi.

```js
{
  // TDZ maydon boshlanishi
  console.log(foo); // ReferenceError
  let foo = 2; // foo o'zgaruvchi uchun TDZ maydon tugashi
}
```

TDZ ga namunalar:

1 - namuna

```js
{
  // TDZ maydon boshlanishi
  console.log(foo); // ReferenceError
  let foo; // let foo = undefined; -> foo o'zgaruvchi uchun TDZ maydon tugashi
}
```

2 - namuna

```js
{
  // TDZ boshlanishi
  const func = () => console.log(letVar); // OK

  // func(); -> `ReferenceError`

  let letVar = 3; // letVar uchun TDZ ni tugashi
  func(); // 3 -> sababi letVar TDZ dan tashqarida chaqirildi
}
```

3 - namuna

```js
function test() {
  var foo = 33;
  if (foo) {
    // if ichidagi foo uchun TDZ boshlandi
    let foo = foo + 55; // ReferenceError -> hali ham foo TDZ da
  }
}
test();
```

4 - namuna

```js
function go(n) {
  console.log(n); // Object {a: [1,2,3]}

  for (let n of n.a) {
    // ReferenceError
    console.log(n);
  }
}

go({ a: [1, 2, 3] });
```

Yuqoridagi misolda `n` o'zgaruvchisi `for` sikli uchun qayta yaratilayapti `let n = undefined;` va `n.a` orqali yaratilgan `n` o'zgaruvchisining `a` property'siga murojaat qilinayapti. Xolbuki, `n` o'zgaruvchisining `a` property'si mavjud emas. Shuning uchun `ReferenceError` qaytarayapti.

Yuqorida `let` o'zgaruvchisi haqida aytilgan barcha fikrlar `const` o'zgaruvchisi uchun ham o'rinlidir.

> Eslatma: `var` o'zgaruvchisi uchun TDZ mavjud emas. Agar unga qiymat berilmasa, qiymati _undefined_ ga teng bo'ladi.

## Xulosa

- `let` va `const` o'zgaruvchilar uchun ES6 da Temporal Dead Zone tushunchasi kiritilgan.
- Bu maydonda o'zgaruvchining qiymati mavjud bo'lmaydi.
- O'zgaruvchi uchun bu maydon unga tegishli scope boshlanishidan, o'zgaruvchiga qiymat berilgunga qadar davom etadi.
