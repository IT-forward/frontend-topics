# JavaScript funksiyalari

#### Funksiya nima?

**Funksiya** - bu aniq vazifalarni bajaradigan va asosiy dasturda saqlanishi mumkin bo'lgan kodlar bloki. Funksiyalarni ishlatishning ba'zi afzalliklari:

<ul>
    <li>
       <b>Funksiyalar dastur ichida kodning takrorlanishini kamaytiradi</b> - Funksiya sizga tez-tez ishlatiladigan kodlar blokini bitta komponentdan ajratib olish imkonini beradi. Endi siz bir xil koddan qayta-qayta nusxa ko'chirmasdan, skriptingizda xohlagan joyga ushbu funksiyani chaqirib, xuddi shu vazifani bajarishingiz mumkin.
        </li>
    <li>
         <b>Funksiyalar kodni saqlashni ancha osonlashtiradi</b> - Bir marta yaratilgan funksiyani ko'p marta ishlatish mumkin. Shuning uchun funksiyaga kiritilgan har qanday o'zgarishlar bir nechta fayllarga tegmasdan, avtomatik ravishda hamma joyda amalga oshiriladi.
    </li>
    <li>
        <b>Funksiyalar xatolarni bartaraf etishni osonlashtiradi</b> - Agar dastur funksiyalarga bo'linsa, xato yuzaga kelsa, siz qaysi funksiyani va nima uchun qayerdan topishni bilasiz. Shunday qilib, xatolarni tuzatish ancha osonlashadi.
    </li>
</ul>

#### Funksiyani aniqlash va chaqirish

Funksiyani e'lon qilish funksiya kalit so'zidan boshlanadi, keyin siz yaratmoqchi bo'lgan funksiyaning nomi, so'ngra qavs, ya'ni **( )** va oxirigacha o'z funksiyangiz kodini figurali qavslar orasiga qo'ying **{ }**. Bu yerda funksiyani e'lon qilishning asosiy sintaksisi:

```js
    function functionName() {
    // Amalga oshiriladigan kod
}
```
Hello World xabarini ko'rsatadigan funksiyaning oddiy misoli:

```js
    // Funksiyani aniqlash (Defining function)
function sayHello() {
    alert("Hello, welcome to this website!");
}
 
// Funksiyani chaqirish (Calling function)
sayHello(); // Natija: Hello, welcome to this website!
```

Funksiya aniqlangandan so'ng, uni hujjatning istalgan joyidan chaqirish  mumkin, uning nomini yozib, yuqoridagi misolda sayHello () kabi qavslar to'plamini yozish orqali.

**ESLATMA:** Funksiya nomi raqamdan emas, balki harfdan yoki pastki chiziqdan boshlanishi kerak. Ixtiyoriy ravishda undan ko'p harflar, raqamlar yoki pastki chiziqlar qo'yiladi. 

#### Funksiyalarga parametrlarni qo'shish

 Parametrlar funksiyadagi to'ldiruvchi o'zgaruvchilar kabi ishlaydi. Ular chaqiruv vaqtida funksiyaga berilgan qiymatlar (argument sifatida tanilgan) bilan almashtiriladi.

Parametrlar qavslar ichidagi funksiyaning birinchi qatoriga o'rnatiladi, masalan:

```js
    function functionName(parameter1, parameter2, parameter3) {
    // Amalga oshiriladigan kod
}
```

Quyidagi misolda displaySum () funksiyasi ikkita raqamni argument sifatida qabul qiladi. Ushbu misolni brauzeringiz console lida sinab ko'rishingiz mumkin.

```js
// Funksiyani e'lon qilish
function displaySum(num1, num2) {
    var total = num1 + num2;
    alert(total);
}
 
// Funksiyani chaqirish
displaySum(6, 20); // Natija: 26
displaySum(-5, 17); // Natija: 12
```

Siz xohlaganingizcha parametrlarni belgilashingiz mumkin. Ammo siz ko'rsatgan har bir parametr uchun funksiyani chaqirganda unga tegishli argument yuborilishi kerak, aks holda uning qiymati aniqlanmagan bo'ladi. Keling, quyidagi misolni ko'rib chiqaylik:

```js
    // Funksiyani e'lon qilish
function showFullname(firstName, lastName) {
    alert(firstName + " " + lastName);
}
 
// Funksiyani chaqirish
showFullname("Clark", "Kent"); // Natija: Clark Kent
showFullname("John"); // Natija: John undefined
```

#### Funksiya parametrlari uchun standart qiymatlar (ES6)

ES6 yordamida endi siz funksiya parametrlariga standart qiymatlarni belgilashingiz mumkin. Bu JavaScript da eng ko'p kutilgan xususiyatlardan biri. Mana bir misol:

```js
    function sayHello(name = 'Guest') {
    alert('Hello, ' + name);
}

sayHello(); // Natija: Hello, Guest
sayHello('John'); // Natija: Hello, John
```
ES6 dan oldin, bunga erishish uchun biz shunday yozishimiz kerak edi:

```js
    function sayHello(name) {
    var name = name || 'Guest'; 
    alert('Hello, ' + name);
}

sayHello(); // Natija: Hello, Guest
sayHello('John'); // Natija: Hello, John
```
Boshqa ES6 xususiyatlari haqida bilish uchun <a href="https://www.tutorialrepublic.com/javascript-tutorial/javascript-es6-features.php"> JavaScript ES6 xususiyatlari </a> bo'limiga qarang.

#### Funksiyadan qiymatlarni qaytarish

Return buyrug'i yordamida funksiya natijada funksiyani chaqirgan skriptga qiymatni qaytarishi mumkin. Qiymat har qanday turga ega bo'lishi mumkin, shu jumladan massivlar va obyektlar.

Return odatda funksiyaning oxirgi satri sifatida figurali qavs yopilishidan oldin qo'yiladi va uni quyidagi misolda ko'rsatilgandek nuqta vergul bilan tugatadi.

```js
    // Funksiyani e'lon qilish
function getSum(num1, num2) {
    var total = num1 + num2;
    return total;
}
 
// Qaytgan qiymatni ekranda ko'rsatish
alert(getSum(6, 20)); // Natija: 26
alert(getSum(-5, 17)); // Natija: 12
```
Funksiya bir nechta qiymatlarni qaytarib bera olmaydi. Biroq, siz quyidagi misolda ko'rsatilgandek, bir qator qiymatlarni qaytarish orqali shunga o'xshash natijalarga erishishingiz mumkin.

```js
    // Funksiyani e'lon qilish
function divideNumbers(dividend, divisor){
    var quotient = dividend / divisor;
    var arr = [dividend, divisor, quotient];
    return arr;
}
 
// Qaytgan qiymatni o'zgaruvchida saqlash
var all = divideNumbers(10, 2);
 
// Alohida qiymatlarni ekranda ko'rsatish
alert(all[0]); // Natija: 10
alert(all[1]); // Natija: 2
alert(all[2]); // Natija: 5
```

### Xulosa
    
    Ushbu maqolada quyidagilar haqida ma'lumot oldik:
    - Funksiya nimaligi?
    - Funksiyani aniqlash va chaqirish
    - Funksiya parametrlarini qo'shish
    - Funksiya parametrlari uchun standart qiymatlar (ES6)
    - Funksiyadan qiymatlarni qaytarish

