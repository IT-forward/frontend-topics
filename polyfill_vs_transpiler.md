# Polyfilling va Transpilling

## Web Browser

Barchamizga ma'lumki biz internet orqali biror veb saytga tashrif buyurmoqchi bo'lsak, bizga qandaydur dastur kerak bo'ladi va u [__web browser__](https://en.wikipedia.org/wiki/Web_browser) deb ataladi.

Veb saytlar turli xil bo'ladi. Masalan, internet magazin saytlari, ijtimoiy tarmoq saytlari, qidiruv saytlari va boshqalar. 

Biz bu saytlarga o'sha web browser'lar yordamida kirib, ular taklif qilishayotgan biror xizmatdan foydalansak bo'ladi. 

Web browser'larni maqsadi internetda mavjud ma'lum veb saytlarni foydalanuvchiga ochib berishdan iborat.

Xo'p, hamma browser'larni maqsadi bitta bo'lsa, nimaga web browser'lar soni ko'p(Google Chrome, FireFox, MC Edge va h.k)? Web browser'lar bir - biridan nimasi bilan farq qiladi?

Hozirda web browser'lar bir - biridan UI(ko'rinish)i va taklif qilayotgan foydali xizmatlari bilan farq qiladi. 

Shu sababdan har bir browser foydalanuvchiga qulay UI va foydali xizmat yaratish maqsadida yangilanishlar(update) chiqarishadi. Har bitta yangilanish, shu browser'ning yangi versiyasi hisoblanadi.

# Polyfilling

[EcmaScript](https://en.wikipedia.org/wiki/ECMAScript) standartlari yildan - yilga yangilanib borgani sayin, web browser'lar ham ularga moslashib boradi. 

Sababi browser oxir - oqibat JavaScript kodni o'qiydi, JavaScript esa EcmaScript standartlari asosida quriladi. Shu sababdan browser'lar har doim ES ni qo'llab - quvvatlashlari kerak bo'ladi. Va bu browser yangilanishlari orqali amalga oshadi.

Tasavvur qiling siz JavaScript kodingizda arraylar uchun mo'ljallangan [`map()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map) metodidan foydalanayapsiz. Bu metod ES5 standartida qo'shilgan bo'lib, ES5 ni support qiladigan browser'larda ishlaydi. 

Lekin siz bilasizki hali ko'pchilik browser'lar ES5 standartiga o'tmagan. Endi siz kodingizda bu ajoyib metoddan foydalanmasligingiz kerakmi?

Bu muammoni hal qilishingiz uchun siz ES5 ni support qilmaydigan browserlar uchun alohida custom(qo'lbola) map metodini yozib qo'yishingiz kerak bo'ladi.

```js
if (!Array.prototype.map) {
    Array.protopype.map = function map(arr, func) {
        const len = arr.length;
        const res = [];

        for (let i = 0; i < len; i++) {
            // second argument is optional for func
            res.push(func(arr[i], i));
        }

        return res;
    }
}
```

Agar js kodingizni o'qiyotgan browser engine arraylar uchun mo'ljallangan map() metodini tushunsa uni o'z bilgandek, aks holda siz yozgan funksiyadek o'qiydi.

Mana shu narsa dasturlashda [__polyfilling__](https://developer.mozilla.org/en-US/docs/Glossary/Polyfill) deb ataladi.

## Transpilling

Endi bir o'ylab ko'ringchi siz yuqoridagi g'oya(polyfilling) orqali ES6 da qo'shilgan [_arrow function_](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions) imkoniyatidan qanday qilib ES5 ni support qiladigan browserlarda foydalansangiz bo'ladi.

Kutganinggizdek bu imkoniyatni polyfilling orqali qilib bo'lmaydi. Buning uchun bizga yangi "qurol" kerak bo'ladi. Ya'ni bizni arrow function uslubida yozgan sintaksisimizni odatiy funksiya sintaksisiga o'girib beradigan. Bu "qurol" transpiler deb ataladi.

```js
const func = () => {
    console.log('biror nima');
}
```

Yuqoridagi kodni transpiler quyidagi kodga o'giradi.

```js
function func() {
    console.log('bir nima');
}
```

[Transpilling](https://developer.mozilla.org/en-US/docs/Glossary/Compile) bu - browser tushunmaydigan biror feature(imkoniyat) sintaksisini, eski browser tushunadigan sintakga o'girib berishi ekan.

Bunaqa transpilerlardan eng keng tarqalgani bu [__babel__](https://babeljs.io/) transpiler'idir.

Bu ikkala texnologiya ham bir xil maqsadda ishlatiladigan texnologiya hisoblanadi. Ya'ni siz kodingizdan foydalanmoqchi bo'lgan muhitda, siz kodingizda foydalangan ba'zi feature'lar implementatsiya(aniqlangan) qilinmagan bo'lsa, bu texnologiyalar o'shani implementatsiya qilishga yordam beradi.

Sodda qilib aytadigan bo'lsak, bu texnologiyalar bizning kodimizni eski browser'larda ham ishlashini ta'minlab beruvchi texnologiyalar ekan.

Lekin bu ikkala texnologiya ikki xil yondashuvga ega ekan.

Polyfill siz ishlatayotgan feature'ni muhitda oldindan aniqlangan tayyor texnologiyalar bilan implementatsiya qilishga harakat qiladi.

Transpiler esa nomidan ma'lum bo'lgandek, sizni kodingizni boshqatdan yozib chiqadi. Agar muhitda aniqlanmagan biror feature bo'lsa, uni unga ekvivalent aniqlangan biror kodga o'girib yozadi.

To'g'ri hozir siz ikkalasini farqini bir - biridan ajrata olmayotgan bo'lishingiz mumkin. Quyida ikkalasini asosiy farqlari keltirilgan. Ularni yaxshilab tahlil qilish orqali siz bu texnologiyalarni bir - biridan ajratib olishingiz mumkin bo'ladi.

Tranpilation jarayonida kodingiz birinchi yangi formatga o'giriladi, so'ng shu format browser engine'ga o'qishga yuboriladi. Ya'ni transpilation jarayoni [__compile time__](https://en.wikipedia.org/wiki/Compile_time) jarayonidir.

Polyfilling jarayonida esa browser engine kodingizni tepadan o'qib kelaveradi, qachonki engine biror tushunarsiz feature'ga duch kelsa, uni siz o'ziz imlementatsiya qilgan joyga borib o'qib keladi va o'z ishini davom ettiraveradi. Ya'ni polyfilling jarayoni [__runtime__](https://en.wikipedia.org/wiki/Runtime_system) jarayon hisoblanadi.

>JavaScript dasturchilar orasida keng tarqalgan _babeljs_ bu ikkala texnologiyadan ham foydalanadi.

## Xulosa

Siz kodingizni turli davrlarda, turli browser'larda to'g'ri ishlashini istasangiz, siz kodingizni barcha browserlar uchun moslashingiz kerak bo'lar ekan. Bunday xizmatni sizga _babeljs_ taklif qilar ekan. Buning uchun siz loyihangizga babeljs paketini o'rnatib qo'yib, kodingizda istalgan ES standartida, istalgan texnologiyadan foydalansangiz bo'lar ekan. 