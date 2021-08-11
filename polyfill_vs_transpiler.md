# Polyfilling va Transpilling

## Web Browser

Barchamizga ma'lumki biz internet orqali biror veb saytga tashrif buyurmoqchi bo'lsak, bizga qandaydur dastur kerak bo'ladi va u __web browser__ deb ataladi.

Veb saytlar turli xil bo'ladi. Masalan, internet magazin saytlari, ijtimoiy tarmoq saytlari, qidiruv saytlari, ta'lim saytlari, davlat xizmatlari sayti, bank saytlari va boshqalar. 

Biz bu saytlarga o'sha web browser'lar yordamida kirib, ular taklif qilishayotgan biror xizmatdan foydalansak bo'ladi. 

Web browser'larni maqsadi internetda mavjud ma'lum veb saytlarni foydalanuvchiga ochib berishdan iborat.

Xo'p, hamma browser'larni maqsadi bitta bo'lsa, nimaga web browser'lar soni ko'p(Google Chrome, FireFox, MC Edge va h.k)? Web browser'lar bir - biridan nimasi bilan farq qiladi?

Hozirda web browser'lar bir - biridan UI(ko'rinish)i va taklif qilayotgan foydali xizmatlari bilan farq qiladi. 

Shu sababdan har bir browser foydalanuvchiga qulay UI va foydali xizmat yaratish maqsadida yangilanishlar(update) chiqarishadi. Va bu browser o'z - o'zidan versiyalanib boradi.

# Polyfilling

EcmaScript standartlari yildan - yilga yangilanib borgani sayin, web browser'lar ham unga moslashib boradi. 

Sababi browser oxir - oqibat JavaScript kodni o'qiydi, JavaScript esa EcmaScript standartlari asosida quriladi. Shu sababdan browserlar har doim ES ni qo'llab - quvvatlashlari kerak bo'ladi. Va bu browser yangilanishlari orqali amalga oshadi.

Tasavvur qiling siz JavaScript kodingizda arraylar uchun mo'ljallangan `map()` metodidan foydalanayapsiz. Bu metod ES5 standartida qo'shilgan bo'lib, ES5 ni support qiladigan browserlarda ishlaydi. 

Lekin siz bilasizki hali ko'pchilik browserlar ES5 standartiga o'tmagan. Endi siz kodingizda bu ajoyib metoddan foydalanmsaligiz kerakmi?

Bu muammoni hal qilishingiz uchun siz ES5 ni support qilmaydigan browserlar uchun alohida custom(qo'lbola) map metodini yozib qo'yishingiz kerak bo'ladi.

```js
...
```

Agar js kodimizni o'qiyotgan browser engine arraylar uchun mo'ljallangan map() metodini tushunsa uni o'z bilgandek, aks holda biz yozgan funksiyadek o'qiydi.

Mana shu narsa dasturlashda __polyfilling__ deb ataladi.

## Transpilling

Endi bir o'ylab ko'ringchi siz yuqoridagi g'oya(polyfilling) orqali ES6 da qo'shilgan _arrow function_ imkoniyatidan qanday qilib ES5 ni support qiladigan browserda foydalansangiz bo'ladi.

Kutganinggizdek bu imkoniyatni polyfilling orqali qilib bo'lmaydi. Buning uchun bizga yangi _qurol_ kerak bo'ladi. Ya'ni bizni arrow function uslubida yozgan sintaksisimizni odatiy funksiya sintaksisiga o'girib beradigan. Bu qurol transpiler deb ataladi.

Transpilling bu - browser tushunmaydigan featurerimizni, browser tushunadigan sintakga o'girib berishi ekan.

Bunaqa transpilerlardan eng keng tarqalgani bu __babel__ transpileridir.

