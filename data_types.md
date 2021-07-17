# Ma'lumotlar turlari (Data types)
<img src="https://i.ibb.co/YkPGqK9/assja.jpg" />



  Dasturlashda ma'lumotlar turlari muhim tushuncha hisoblanadi. O'zgaruvchilar ustida ishlashni ta'minlash uchun uning turi haqida ma'lumotga ega bo'lishimiz muhimdir. Ma'lumotlar turlarisiz kompyuter buni xavfsiz hal qila olmaydi.

<img src="https://i.ibb.co/54h84xX/image.jpg" />


  Ko'rib turganingizdek ma'lumot turlari(data type) 2 turga bo'linadi : 
  
  
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

  JavaScriptda matnli ma'lumotlarni ko'rsatish uchun string turi ishlatilinadi. Stringni quyidagi ko'rinishda yozishimiz mumkin : `"Salom Dunyo", 'Hello World'`. Matnli ma'lumotlarni stringga aylantirishimiz uchun `''` va `""` dan foydalanamiz.String uzunligi bu undagi elementlar sonidir. Misol `console.log('Hello World'.length)` mana shu string ning uzunligi 11 ga teng, ya'ni bunda elementlar soni hisoblanmoqda. `length` - mavjud stringni uzunligini qaytaradi.JavaScriptda string o'zgarmasdir. Bu shuni anglatadiki, bir marta yangi string yaratilsa uni o'zgartirish mumkin emas. 

### Boolean

   Ko'pincha, dasturlashda sizga ikkita qiymatdan bittasiga ega bo'lishi mumkin bo'lgan ma'lumotlar turi kerak bo'ladi, masalan: 


```
  HA / YO'Q
  ON / OFF
  ROST / YOLG'ON
```

Buning uchun JavaScriptda mantiqiy ma'lumotlar(Boolean) turi mavjud. Bu faqat rost(true) yoki yolg'on(false) qiymatlarni qabul qilishi mumkin .



`Boolean()` funktsiyadan ifodaning (yoki o'zgaruvchining) to'g'riligini bilish uchun  foydalanishingiz mumkin: `console.log(Boolean(6 > 5)) `. Natija `rost(true)` chiqadi.

### Null 

  Null turi to'liq bitta qiymatga ega: null. 


  `null` ikkita xususiyatni tushunishi kerak: 

```
- null bo'sh yoki mavjud bo'lmagan qiymatdir.
- null tayinlanishi kerak bo'lgan qiymatdir.
let a = null;
console.log(a);
// null
```

### Undefined 

  JavaScriptda qiymati bo'lmagan o'zgaruvchining qiymati `undefined` ga teng. Turi ham undefined. Misol: 


```JavaScript
  let computer;
  console.log(computer);
  // Undefined
```

 Biz computer degan o'zgaruvchi yaratdik va bu o'zgaruvchining qiymati yo'q.Shuning uchun natija undefined ga teng bo'ladi.

### Symbol 

  Ma'lumotlar turi Belgi (Symbol) bo'lgan qiymatni "Belgi qiymat(Symbol value)" deb atash mumkin. JavaScriptning ishlash vaqti muhitida belgi qiymati Symbol funktsiyasini chaqirish orqali hosil bo'ladi, va bu funksiya noma'lum, noyob qiymatni dinamik ravishda ishlab chiqaradi. Belgi(Symbol)- ob'ekt xususiyati sifatida ishlatilishi mumkin.
Belgi ixtiyoriy tavsifga ega bo'lishi mumkin, lekin faqat dasturdagi xatoliklarni bartaraf etish maqsadida.Belgi qiymati noyob identifikatorni ifodalaydi. 

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
BigInt bilan `+`,`*`,`-`,`**` va `%` operatorlaridan foydalanishingiz mumkin - xuddi Sonlar(Numbers) kabi.BigInt mantiqiy(boolean) shaklga o'tkaziladigan holatlarda o'zini raqam(number) kabi tutadi: `if`, `||`, `&&`, `Boolean`,`!`.
Null va Undefined orasidagi farq
JavaScriptda `undefined` o'zgaruvchining e'lon qilinganligini anglatadi, ammo hali unga qiymat berilmagan, masalan: 


<pre>
var testVar;
console.log(testVar);            // undefined
console.log(typeof testVar);     // undefined
</pre>
`null` esa tayinlash qiymati. U o'zgaruvchiga bo'sh qiymatning ifodasi sifatida berilishi mumkin:  

```JavaScript
var testVar = null;
console.log(testVar);            // null
console.log(typeof testVar);     // object
```

Oldingi misollardan ko'rinib turibdiki undefined a null lar ikki xil turga ega: undefined bu tip o'zi (aniqlanmagan) esa null ob'ektdir.


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
 
