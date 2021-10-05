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

Ko'rib turganingizdek `name` o'zgaruvchi faqat o'zini scope'i (`{}`) ichidagina yaroqli bo'lib, scope'dan tashqarida esa javascript uni tanimaydi.

JavaScript'da scope'lar ta'sir maydoniga ko'ra ikkiga bo'linadi.

- Ichki scope
- Tashqi scope

Agar berilgan o'zgaruvchi biror scope ichida e'lon qilingan bo'lsa, bu scope berilgan o'zgaruvchi uchun ichki scope hisoblanadi.

Agar berilgan o'zgaruvchi biror scope tashqarisida e'lon qilingan bo'lsa, bu scope berilgan o'zgaruvchi uchun tashqi scope hisoblanadi.

```js
function login(parol) {
  const password = "12345";
  if (parol === password) {
    const successMessage = "Muvaffaqiyatli!";
    console.log(successMessage);
  } else {
    const failMessage = "Muvaffaqiyatsiz!";
    console.log(failMessage);
  }
}

login("871"); // Muvaffaqiyatsiz!
login("12345"); // Muvaffaqiyatli!
```

Yuqoridagi misolda `password` o'zgaruvchisi `if` va `else` statement larning har biri uchun tashqi scope o'zgaruvchi hisoblanadi. Sababi `password` o'zgaruvchisi `if` va `else` scope laridan tashqarida e'lon qilinayapti.

`successMessage` o'zgaruvchisi esa `if` statement uchun ichki scope o'zgaruvchi hisoblanadi. Shuningdek, `failMessage` o'zgaruvchisi `else` statement uchun ichki scope o'zgaruvchi hisoblanadi. Sababi bu o'zgaruvchilar o'zlarining statement lari ichida e'lon qilingan.

Inglizchada ichki scope `local scope`, tashqi scope esa `global scop` deb yuritiladi.

JavaScript'da scope'lar ichma - ich qo'llanila olishini inobatga olsak, bu atamalar (local va global scope) aslida nisbiy atamalar ekanligini payqashimiz mumkin.

Umuman olganda butun boshli javascript kodni bitta scope ichida joylashgan deb qarash mumkin. Bu scope js koddagi qolgan barcha scope'lar uchun qat'iy global scope hisoblanadi.

Shunga ko'ra yuqoridagi misolni quyidagicha ham yozish mumkin.

```js
{
  const password = "12345";

  function login(parol) {
    if (parol === password) {
      const successMessage = "Muvaffaqiyatli!";
      console.log(successMessage);
    } else {
      const failMessage = "Muvaffaqiyatsiz!";
      console.log(failMessage);
    }
  }

  login("871"); // Muvaffaqiyatsiz!
  login("12345"); // Muvaffaqiyatli!
}
```

Qulaylik uchun dasturchilar orasida bu scope'ni yozmasdan, tashlab ketish qabul qilingan.

## Xulosa

- JavaScript'da scope bu - o'zgaruvchilarni ta'sir maydoni hisoblanadi.
- JavaScript'da scope'lar `local` va `global` scope'larga bo'linadi.
- Local scope'da o'zgaruvchilar scope ichida e'lon qilinadi.
- Global scope'da o'zgaruvchilar scope tashqarisida e'lon qilnadi.
