# Ma'lumotlar turlari (Data types)
<img src="https://i.ibb.co/YkPGqK9/assja.jpg" />



  Dasturlashda data tiplari muhim tushuncha hisoblanadi. O'zgaruvchilar ustida ishlashni ta'minlash uchun uning turi haqida ma'lumotga ega bo'lishimiz muhimdir. Data tiplarisiz kompyuter buni xavfsiz hal qila olmaydi.

<img src="https://i.ibb.co/54h84xX/image.jpg" />


  Ko'rib turganingizdek data tiplari 2 turga bo'linadi : 
  
  
  1. **Primitive**  


  2. **Non-primitive**
  
  
  
  **Primitiv** tiplarga quyidagilar kiradi :
  `Number, String, Boolean, Null, Undefined, Symbol va BigInt`;
  
  
  
  **Non-primitive** tiplarga quyidagilar kiradi:
  `Object`;
  
  **Primitiv**
  tiplarning barchasi faqatgina yagona qiymatni qabul qiladi va ularga ikkinchi
  qiymatni qo’sha olmaymiz. 
  
  
  Keling bularni birin-ketinlik bilan ko'rib chiqamiz!

### Number

   Number -  64 bitli ikkilik formatdagi IEEE 754 ning qiymati (- (2 ^ 53 - 1) va 2 ^ 53 - 1 orasidagi sonlar).
       Sonlar turi quyidagi 3 ta ko'rinishga ega bo'ladi: `+ Infinity, -Infinity va NaN ("Raqam emas").`

### String

  JavaScriptda matnli ma'lumotlarni ko'rsatish uchun string turi ishlatilinadi. Stringni quyidagi ko'rinishda yozishimiz mumkin : `"Salom Dunyo", 'Hello World'`. Matnli ma'lumotlarni stringga aylantirishimiz uchun `''` va `""` dan foydalanamiz.String uzunligi bu undagi elementlar sonidir. Misol:
  ```JavaScript
  console.log('Hello World'.length);
  //11
  ```
 Berilgan stringni uzunligi 11 ga teng, ya'ni bunda elementlar soni hisoblanmoqda. `length` - mavjud stringni uzunligini qaytaradi.JavaScriptda string o'zgarmasdir. Bu shuni anglatadiki, bir marta yangi string yaratilsa uni o'zgartirish mumkin emas. 

### Boolean

   Ko'pincha, dasturlashda sizga ikkita qiymatdan bittasiga ega bo'lishi mumkin bo'lgan data tip kerak bo'ladi, masalan: 


```
  HA / YO'Q
  ON / OFF
  ROST / YOLG'ON
```

Buning uchun JavaScriptda mantiqiy data tip (Boolean) mavjud. Bu faqat `rost(true)` yoki `yolg'on(false)` qiymatlarni qabul qilishi mumkin .



`Boolean()` funktsiyadan ifodaning (yoki o'zgaruvchining) to'g'riligini bilish uchun  foydalanishingiz mumkin: `console.log(Boolean(6 > 5)) `. Natija `rost(true)` chiqadi.

### Null 


  `null` ikkita xususiyatni tushunishi kerak: 

```
- null bo'sh yoki mavjud bo'lmagan qiymatdir.
- null tayinlanishi kerak bo'lgan qiymatdir.
let a = null;
console.log(a);
// null
```

### Undefined 

  JavaScriptda qiymati bo'lmagan o'zgaruvchining qiymati `undefined` ga teng. Tipi ham undefined. Misol: 


```JavaScript
  let computer;
  console.log(computer);
  // Undefined
```

 Biz computer degan o'zgaruvchi yaratdik va bu o'zgaruvchining qiymati yo'q.Shuning uchun natija undefined ga teng bo'ladi.

### Symbol 

 Data tipi Symbol bo'lgan qiymatni "Symbol value" deb atash mumkin. JavaScriptning ishlash vaqti muhitida symbol value Symbol funksiyasini chaqirish orqali hosil bo'ladi va bu funksiya noma'lum, noyob qiymatni dinamik ravishda ishlab chiqaradi. Symbol - ob'ekt property'si sifatida ishlatilishi mumkin. 

```JavaScript
let Sym1 = Symbol("Sym")
let Sym2 = Symbol("Sym")
console.log(Sym1 === Sym2);
// false
```

### BigInt 

  BigInt turi JavaScriptdagi raqamli primitive bo'lib, u butun sonlarni aniqlik bilan ko'rsatishi mumkin. BigInt yordamida butun son chegarasidan tashqarida ham katta butun sonlarni ishlatishingiz mumkin.BigInt butun sonning oxiriga n qo'shib yoki konstruktorni chaqirish orqali hosil bo'ladi. Misol: 


  ```JavaScript
  const x = 2n ** 53n;
  console.log(x);
  // 9007199254740992n
```
BigInt bilan `+`,`*`,`-`,`**` va `%` operatorlaridan foydalanishingiz mumkin - xuddi Numbers kabi.BigInt Boolean shaklga o'tkaziladigan holatlarda o'zini number kabi tutadi: `if`, `||`, `&&`, `Boolean`,`!`.

### Null va Undefined orasidagi farq
JavaScriptda `undefined` o'zgaruvchining e'lon qilinganligini anglatadi, ammo hali unga qiymat berilmagan, masalan: 


```JavaScript
var testVar;
console.log(testVar);            // undefined
console.log(typeof testVar);     // undefined
```

`null` esa tayinlash qiymati. U o'zgaruvchiga bo'sh qiymatning ifodasi sifatida berilishi mumkin:  

```JavaScript
var testVar = null;
console.log(testVar);            // null
console.log(typeof testVar);     // object
```

```JavaScript
console.log(null === undefined)     // false
console.log(null == undefined)      // true
console.log(null === null)          // true
console.log(null = 'value')        // ReferenceError
console.log(undefined = 'value')     // 'value'
```

### Operator typeof

  `typeof` - JavaScript o'zgaruvchisining turini topish uchun foydalanishingiz mumkin. 



```JavaScript
    console.log(typeof "Alisher")                 // Natija "string"
    console.log(typeof 7.89)                      // Natija "number"
    console.log(typeof NaN)                       // Natija "number"
    console.log(typeof true)                      // Natija "boolean"
    console.log(typeof [5,6,7,4])                 // Natija "object"
    console.log(typeof {name:'Ali', age:25})      // Natija "object"
    console.log(typeof new Date())                // Natija "object"
    console.log(typeof function () {})            // Natija "function"
    console.log(typeof myCar)                     // Natija "undefined" 
    console.log(typeof null)                      // Natija "object";   
```

null o'zini tipiga mansub bo'lsada, JavaScript bu holatda "object" qaytaradi.
 
**Non-primitive**

Keling endi Non-primitive lar haqida so'z yuritsak, yuqorida ko'rsatilganidek Non-primitive type ga faqat `Object` kiradi. 

### Object 
 - o'zida bir qancha property ni saqlay olish xususiyatiga ega;
 - {} qavslar orqali objectlarni yozishimiz mumkin.
Bunga misol:
```JavaScript
let data = {
  name: "John",
  age: 25,
  isMarried: true,
  hello: function() {
    console.log('Assalomu aleykum');
  }
}

data.hello();
// Assalomu aleykum
```

data degan Object yaratdik va ushbu ob’ektda bir nechta tiplar joylashgan.Ob’ektlarning eng yaxshi tomonlaridan biri shundaki, biz funktsiyani uning qiymatlaridan biri sifatida saqlashimiz mumkin.

```JavaScript
  let person = { name: 'John Doe' , age: 25 , isMarried: true}
```
yoki
``` JavaScript
  let array = ['apelsen', null, undefined, false, 26]
```

Ko'rib turganimezdek Object tipi misolida `array` va `object` keltirilgan. Bu holatda, ikkala o'zgaruvchi ham bir qancha qiymatlarni o'zida saqlab qoldi. Aynan shu xususiyat ularni **Non-primitive** qiladi.

```JavaScript
Array, Function, Object bularning hammasining tipi object hisoblanadi.
````

### Array

Array - bu bir vaqtning o'zida bir nechta qiymatga ega bo'lishi mumkin bo'lgan o'zgaruvchidir.


Agar sizda avtomobillar nomlari ro'yxati mavjud bo'lsa, ularni o'zgaruvchilarga saqlash quyidagicha ko'rinishi mumkin:

```JavaScript
let avtomobil1 = 'Malibu';
let avtomobil2 = 'Damas';
let avtomobil3 = 'Nexia';
```

Hozir bu yerda bizlarga faqatgina 3 tagina avtomobil nomi keltirib o'tilgan, shular soni 300 ta bo'lsa, yuqoridagi ketma-ketlikda ularni e'lon qilishimiz umuman tushunarsiz holatga kelib qoladi. Sababi biz  `avtomobil1, avtomobil2, ........ avtomobil300` deb o'zgaruvchilarni e'lon qilsak, ularni oladigan qiymati baribir 1 xil ko'rinishdagi avtomobil nomlariga teng bo'ladi. Keling shu ishni `array` da qilib ko'ramiz:


```JavaScript
let avtomobil = ['Malibu','Damas','Nexia','Spark','Captiva'];
```

Array bitta nom ostida ko'plab qiymatlarni o'z ichiga olishi mumkin va siz indeks raqamiga murojaat qilib qiymatlarga kirishingiz mumkin.

```JavaScript
let avtomobil = ['Malibu','Damas','Nexia','Spark','Captiva'];
let avto = avtomobil[0];
console.log(avto);
// Malibu
```

>Massiv indekslari 0 dan boshlanadi. [0] - birinchi element, [1] -ikkinchi element


### Funksiya

Funksiya bu ma'lum bir vazifani bajarish uchun mo'ljallangan kod bloki.

```JavaScript
function myFunction(a,b) {
  return a * b;
}
```

JavaScript funksiyasi `function` kalit so'z bilan belgilanadi, so'ngra funksiya nomi, keyin argument qabul qiladigan `()`.
Funksiya nomlari harflar,raqamlar, `_` va `$` belgilaridan iborat bo'lishi mumkin.
`()` ichida vergul bilan ajratilgan bir nechta parametr nomlari bo'lishi mumkin.
Funksiya bo'yicha bajariladigan kod jingalak qavs ichiga yoziladi : `{}`.
Funksiya ichidagi kod biror hodisa yuz berganda(foydalanuvchi tugmani bosganda) bajariladi.

Misol:
```JavaScript
  function name(parametr_1, parametr_2, parametr_3) {
    return parametr_1 + parametr_2 * parametr_3
  }
```
  > return funksiya bajarilishini to'xtatadi.

  ### Xulosa
  
  - Agar bir xil tipdagi o'zgaruvchilar bilan ishlamoqchi bo'lsak **primitive** typedan foydalanishimiz kerak.
  - Bir nechta tiplardan foydalanmoqchi bo'lsak **Non-primitive**  typedan foydalanganimiz ma'qul
  - 