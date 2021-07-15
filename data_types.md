# Ma'lumotlar turlari (Data types)
<img src="https://i.ibb.co/YkPGqK9/assja.jpg" />
<pre>
  Dasturlashda ma'lumotlar turlari muhim tushuncha hisoblanadi. O'zgaruvchilar
  ustida ishlashni ta'minlash uchun uning turi haqida ma'lumotga ega bo'lishimiz
  muhimdir.Ma'lumotlar turlarisiz kompyuter buni xavfsiz hal qila olmaydi.
</pre>
<img src="https://i.ibb.co/54h84xX/image.jpg" />
  Ko'rib turganingizdek ma'lumot turlari(data type) 2 turga bo'linadi : <br/>
  1.<b>Primitive</b>  <br/>
  2.<b>Non-primitive</b>
  <br />
  <b>Primitiv</b> tiplarga quyidagilar kiradi :
  <code>Number, String, Boolean, Null, Undefined, Symbol va BigInt</code>;
  <br />
  <b>Non-primitive</b> tiplarga quyidagilar kiradi:
  <code>Object</code>;
  <br />
  <b>Primitiv</b>
  tiplarning barchasi faqatgina yagona qiymatni qabul qiladi va ularga ikkinchi
  qiymatni qo’sha olmaymiz. <br> 
  Keling bularni birin-ketinlik bilan ko'rib chiqamiz!

<h3>Number</h3>
   Number -  64 bitli ikkilik formatdagi IEEE 754 ning qiymati (- (2 ^ 53 - 1) va 2 ^ 53 - 1 orasidagi sonlar).
       Sonlar turi quyidagi 3 ta ko'rinishga ega bo'ladi: <code>+ Infinity, -Infinity va NaN ("Raqam emas").</code>
       <h3>String</h3> 
      JavaScriptda matnli ma'lumotlarni ko'rsatish uchun string turi ishlatilinadi. Stringni quyidagi ko'rinishda yozishimiz mumkin : <code>"Salom Dunyo", 'Hello World'</code>. Matnli ma'lumotlarni stringga aylantirishimiz uchun <code>''</code> va <code>""</code> dan foydalanamiz.String uzunligi bu undagi elementlar sonidir. Misol <code>console.log('Hello World'.length)</code> mana shu string ning uzunligi 11 ga teng, ya'ni bunda elementlar soni hisoblanmoqda. <code>length</code> - mavjud stringni uzunligini qaytaradi.JavaScriptda string o'zgarmasdir. Bu shuni anglatadiki, bir marta yangi string yaratilsa uni o'zgartirish mumkin emas. 
           <h3>Boolean</h3> 
   Ko'pincha, dasturlashda sizga ikkita qiymatdan bittasiga ega bo'lishi mumkin bo'lgan ma'lumotlar turi kerak bo'ladi, masalan: <br/>
<pre>
  HA / YO'Q
  ON / OFF
  ROST / YOLG'ON
</pre>
Buning uchun JavaScriptda mantiqiy ma'lumotlar(Boolean) turi mavjud. Bu faqat rost(true) yoki yolg'on(false) qiymatlarni qabul qilishi mumkin .
<br/>
<code>Boolean()</code> funktsiyadan ifodaning (yoki o'zgaruvchining) to'g'riligini bilish uchun  foydalanishingiz mumkin: <code>console.log(Boolean(6 > 5)) </code>. Natija <code>rost(true)</code> chiqadi.
       <h3>Null</h3> 
   Lorem ipsum dolor sit amet, consectetur adipisicing elit. Excepturi natus corrupti temporibus, saepe ratione eius libero tenetur non numquam totam.
       <h3>Undefined</h3> 
   Lorem, ipsum dolor sit amet consectetur adipisicing elit. Rem aspernatur reiciendis suscipit voluptates! Ea, eius quod quibusdam sequi doloribus voluptas!
   <h3>Symbol</h3> 
   Lorem, ipsum dolor sit amet consectetur adipisicing elit. Rem aspernatur reiciendis suscipit voluptates! Ea, eius quod quibusdam sequi doloribus voluptas!
   <h3>BigInt</h3> 
   Lorem, ipsum dolor sit amet consectetur adipisicing elit. Rem aspernatur reiciendis suscipit voluptates! Ea, eius quod quibusdam sequi doloribus voluptas!
       <h3>Operator typeof</h3>
  <code>typeof</code> - JavaScript o'zgaruvchisining turini topish uchun foydalanishingiz mumkin. </br>
<pre>
    console.log(typeof "Alisher")                 // Natija "string"
    console.log(typeof 7.89)                      // Natija "number"
    console.log(typeof NaN)                       // Natija "number"
    console.log(typeof true)                      // Natija "boolean"
    console.log(typeof [5,6,7,4])                 // Natija "object"
    console.log(typeof {name:'Ali', age:25})      // Natija "object"
    console.log(typeof new Date())                // Natija "object"
    console.log(typeof function () {})            // Natija "function"
    console.log(typeof myCar)                     // Natija "undefined" 
    console.log(typeof null)                      // Natija "object"
</pre>

 
