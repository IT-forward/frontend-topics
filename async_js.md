# Synchronous vs Asynchronous JS

![image](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcThCrfImpbOmNHIL4VA6DUM3Wd9aXWfJIuCIw&usqp=CAU)

Dasturlashda __sinxron__ va __asinxron__ funksiya degan tushunchalar mavjud. Bu funksiyalarni tushunish va ularni to'g'ri ishlata olish dasturchi uchun muhim ko'nikma hisoblanadi. Hozir siz bilan shu tushunchalarni birga ko'rib chiqamiz. 

Bu funksiyalar haqida gap boshlashdan oldin, keling quyidagi misolni qaraylik.

```javascript
console.log('1 - chiqadi');
setTimeout(() => console.log('2 - chiqadi'), 0);
console.log('3 - chiqadi');
```

Bu yerda _setTimeout_ funksiyasi ma'lum vazifani, ma'lum vaqtdan so'ng bajaradigan funksiyadir. Bu funksiyada 1 - parametr sifatida berilgan vazifa, 2 - parametr sifatida vaqt (millisekund) keladi.

Endi bir o'ylab ko'ringchi console'ga qanday natija chiqadi.

Agar sizning natijangiz quyidagicha bo'lsa, siz ko'pchilik kabi xato o'ylagansiz va bu tabiiy holat.

```
1 - chiqadi
2 - chiqadi 
3 - chiqadi
```

To'g'ri javob quyidagicha bo'ladi

```
1 - chiqadi
3 - chiqadi 
2 - chiqadi
```

Siz aytishingiz mumkin _setTimeout_ funksiyaga vaqt sifatida nol berilganku. Bu degani bu funksiya hech qancha vaqt kutmasdan o'zini vazifasini bajarishi kerak deb. Ha aslida shunday. Bu yerda hammma gap __sinxron__ va __asinxron__ funksiyalarda. _console.log()_ - sinxron, _setTimeout_ - asinxron funksiya hisoblanadi. Va asinxron funksiya sinxron funksiyadan so'ng bajariladi.

JavaScript Engine kodni o'qish jarayonida asinxron funksiyalarni queue'ga yig'ib boradi va hamma sinxron funksiyalarni bararib bo'lgandan so'ng, navbat bilan queue'dagi asinxron funksiyalarni bajarishni boshlaydi.

Shuning uchun bizni misolimizda setTimeout funksiyaga nol argumenti berilgani bilan ham u oxirida bajarilyapti. 

Quyidagi misolni o'zingiz tahlil qilib ko'ring va browser console'ida o'zingizni tekshirib ko'ring. 

```javascript
console.log('1 - chiqadi');
setTimeout(() => console.log('2 - chiqadi'), 10);
setTimeout(() => console.log('3 - chiqadi'), 0);
console.log('4 - chiqadi');
```