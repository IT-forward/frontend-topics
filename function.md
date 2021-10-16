# JavaScript funktsiyalari

#### Funktsiya nima?

**Funktsiya** - bu aniq vazifalarni bajaradigan va asosiy dasturda saqlanishi mumkin bo'lgan kodlar bloki. Funktsiyalarni ishlatishning ba'zi afzalliklari:

<ul>
    <li>
        <b>Funksiyalar dastur ichida kodning takrorlanishini kamaytiradi</b> - Funktsiya sizga tez -tez ishlatiladigan kodlar blokini bitta komponentdan ajratib olish imkonini beradi. Endi siz bir xil koddan qayta-qayta nusxa ko'chirmasdan, skriptingizda xohlagan joyga ushbu funktsiyani chaqirib, xuddi shu vazifani bajarishingiz mumkin.
        </li>
    <li>
         <b>Funksiyalar kodni saqlashni ancha osonlashtiradi</b> - Bir marta yaratilgan funktsiyani ko'p marta ishlatish mumkin. Shuning uchun funktsiyaga kiritilgan har qanday o'zgarishlar bir nechta fayllarga tegmasdan, avtomatik ravishda hamma joyda amalga oshiriladi.
    </li>
    <li>
        <b>Funksiyalar xatolarni bartaraf etishni osonlashtiradi</b> - Agar dastur funktsiyalarga bo'linsa, xato yuzaga kelsa, siz qaysi funktsiyani va nima uchun qayerdan topishni bilasiz. Shunday qilib, xatolarni tuzatish ancha osonlashadi.
    </li>
</ul>

#### Funktsiyani aniqlash va chaqirish

Funktsiyaning deklaratsiyasi funktsiya kalit so'zidan boshlanadi, keyin siz yaratmoqchi bo'lgan funktsiyaning nomi, so'ngra qavs, ya'ni **( )** va oxirigacha o'z funktsiyangiz kodini jingalak qavslar orasiga qo'ying **{ }**. Bu yerda funktsiyani e'lon qilishning asosiy sintaksisi:

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
sayHello(); // 0utputs: Hello, welcome to this website!
```

Funktsiya aniqlangandan so'ng, uni hujjatning istalgan joyidan chaqirish  mumkin, uning nomini yozib, yuqoridagi misolda sayHello () kabi qavslar to'plamini yozish orqali.

**ESLATMA!:** Funktsiya nomi raqamdan emas, balki harfdan yoki pastki chiziqdan boshlanishi kerak. Ixtiyoriy ravishda undan ko'p harflar, raqamlar yoki pastki chiziqlar qo'yiladi. 

#### Funktsiyalarga parametrlarni qo'shish

 Parametrlar funktsiyadagi to'ldiruvchi o'zgaruvchilar kabi ishlaydi. Ular chaqiruv vaqtida funktsiyaga berilgan qiymatlar (argument sifatida tanilgan) bilan almashtiriladi.

Parametrlar qavslar ichidagi funktsiyaning birinchi qatoriga o'rnatiladi, masalan:

```js
    function functionName(parameter1, parameter2, parameter3) {
    // Amalga oshiriladigan kod
}
```

Quyidagi misolda displaySum () funktsiyasi ikkita raqamni argument sifatida qabul qiladi. Ushbu misolni brauzeringiz console lida sinab ko'rishingiz mumkin.

```js
// Defining function
function displaySum(num1, num2) {
    var total = num1 + num2;
    alert(total);
}
 
// Calling function
displaySum(6, 20); // 0utputs: 26
displaySum(-5, 17); // 0utputs: 12
```

Siz xohlaganingizcha parametrlarni belgilashingiz mumkin. Ammo siz ko'rsatgan har bir parametr uchun funktsiyani chaqirganda unga tegishli argument yuborilishi kerak, aks holda uning qiymati aniqlanmagan bo'ladi. Keling, quyidagi misolni ko'rib chiqaylik:

```js
    // Defining function
function showFullname(firstName, lastName) {
    alert(firstName + " " + lastName);
}
 
// Calling function
showFullname("Clark", "Kent"); // 0utputs: Clark Kent
showFullname("John"); // 0utputs: John undefined
```

#### Funktsiya parametrlari uchun standart qiymatlar (ES6)

ES6 yordamida endi siz funktsiya parametrlariga standart qiymatlarni belgilashingiz mumkin. Bu JavaScript da eng ko'p kutilgan xususiyatlardan biri. Mana bir misol:

```js
    function sayHello(name = 'Guest') {
    alert('Hello, ' + name);
}

sayHello(); // 0utputs: Hello, Guest
sayHello('John'); // 0utputs: Hello, John
```
ES6 dan oldin, bunga erishish uchun biz shunday yozishimiz kerak edi:

```js
    function sayHello(name) {
    var name = name || 'Guest'; 
    alert('Hello, ' + name);
}

sayHello(); // 0utputs: Hello, Guest
sayHello('John'); // 0utputs: Hello, John
```
Boshqa ES6 xususiyatlari haqida bilish uchun <a href="https://www.tutorialrepublic.com/javascript-tutorial/javascript-es6-features.php"> JavaScript ES6 xususiyatlari </a> bo'limiga qarang.

#### Funktsiyadan qiymatlarni qaytarish

Return buyrug'i yordamida funktsiya natijada funktsiyani chaqirgan skriptga qiymatni qaytarishi mumkin. Qiymat har qanday turga ega bo'lishi mumkin, shu jumladan massivlar va ob'ektlar.

Return odatda funktsiyaning oxirgi satri sifatida jingalak qavs yopilishidan oldin qo'yiladi va uni quyidagi misolda ko'rsatilgandek nuqta vergul bilan tugatadi.

```js
    // Defining function
function getSum(num1, num2) {
    var total = num1 + num2;
    return total;
}
 
// Displaying returned value
alert(getSum(6, 20)); // 0utputs: 26
alert(getSum(-5, 17)); // 0utputs: 12
```
Funktsiya bir nechta qiymatlarni qaytarib bera olmaydi. Biroq, siz quyidagi misolda ko'rsatilgandek, bir qator qiymatlarni qaytarish orqali shunga o'xshash natijalarga erishishingiz mumkin.

```js
    // Defining function
function divideNumbers(dividend, divisor){
    var quotient = dividend / divisor;
    var arr = [dividend, divisor, quotient];
    return arr;
}
 
// Store returned value in a variable
var all = divideNumbers(10, 2);
 
// Displaying individual values
alert(all[0]); // 0utputs: 10
alert(all[1]); // 0utputs: 2
alert(all[2]); // 0utputs: 5
```

### Xulosa
    
    Ushbu maqolada quyidagilar haqida ma'lumot oldik:
    - Funksiya nimaligi?
    - Funksiyani aniqlash va chaqirish
    - Funksiya parametrlarini qo'shish
    - Funksiya parametrlari uchun standart qiymatlar (ES6)
    - Funksiyadan qiymatlarni qaytarish

