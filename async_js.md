# Asynchronous JS

## Sinxron vs Asinxron

![image](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcThCrfImpbOmNHIL4VA6DUM3Wd9aXWfJIuCIw&usqp=CAU)

Dasturlashda **sinxron** va **asinxron** funksiya degan tushunchalar mavjud. Bu funksiyalarni tushunish va ularni to'g'ri ishlata olish dasturchi uchun muhim ko'nikma hisoblanadi. Hozir siz bilan shu tushunchalarni birga ko'rib chiqamiz.

Bu funksiyalar haqida gap boshlashdan oldin, keling quyidagi misolni qaraylik.

```js
console.log("1 - chiqadi");
setTimeout(() => console.log("2 - chiqadi"), 0);
console.log("3 - chiqadi");
```

Bu yerda [`setTimeout()`](https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/setTimeout) funksiyasi ma'lum vazifani, ma'lum vaqtdan so'ng bajaradigan funksiyadir. Bu funksiyada 1 - parametr sifatida berilgan vazifa, 2 - parametr sifatida vaqt (millisekund) keladi.

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

Siz aytishingiz mumkin `setTimeout()` funksiyaga vaqt sifatida nol berilganku. Bu degani bu funksiya hech qancha vaqt kutmasdan o'zini vazifasini bajarishi kerak deb. Ha aslida shunday. Lekin, bu yerda hammma gap **sinxron** va **asinxron** funksiyalarda. [`console.log()`](https://developer.mozilla.org/en-US/docs/Web/API/console/log) - sinxron, `setTimeout()` - asinxron funksiya hisoblanadi. Va asinxron funksiya sinxron funksiyadan so'ng bajariladi.

JavaScript Engine kodni o'qish jarayonida asinxron funksiyalarni [queue](<https://dmitripavlutin.com/javascript-queue/#:~:text=The%20queue%20data%20structure%20is,constant%20time%20O(1)%20.>)(navbat)ga yig'ib boradi va hamma sinxron funksiyalarni bararib bo'lgandan so'ng, navbati bilan queue'dagi asinxron funksiyalarni bajarishni boshlaydi.

Shuning uchun bizni misolimizda setTimeout funksiyaga nol argumenti berilgani bilan ham u oxirida bajarilyapti.

Quyidagi misolni o'zingiz tahlil qilib ko'ring va browser console'ida o'zingizni tekshirib ko'ring.

```js
console.log("1 - chiqadi");
setTimeout(() => console.log("2 - chiqadi"), 10);
setTimeout(() => console.log("3 - chiqadi"), 0);
console.log("4 - chiqadi");
```

## Promise

Biz yuqorida sinxron va asinxron funksiyalar bilan tanishdik. Endi **asinxron** funksiya ishlash prinsipi asosida qurilgan metodlardan biri [**Promise**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) lar bilan tanishamiz.

Tasavvur qiling siz media fayllarga boy biror saytga tashrif buyurayapsiz. Sizda u sayt quyidagi ikki xil ko'rinishda yuklanishi mumkin. **1 - ko'rinishi:** saytdagi media fayllar va context(matn)lar birinma - ketin yuklanishi yoki **2 - ko'rinishi:** oldin contextlar yuklanib keyin media fayllar yuklanishi mumkin. Bunda 1 - holatda sayt o'ziga ko'p foydalanuvchilarni jalb qila olmasligi mumkin. Sababi bunday saytlarda qotishlar bo'lishi mumkin. Chunki kattaroq media fayllarni browserga joylashtirish ko'proq vaqt oladi. Tabiiyki, foydalanuvchi noma'lum sayt yuklanishini uzoq vaqt kutishni yoqtirmaydi. 2 - holatda esa saytdagi matnli ma'lumotlar birinchi to'liq yuklanadi, so'ng media fayllar. Bu degani saytni to'liq yuklanishini kutmasdan turib, saytdagi mantlardan bu sayt sizga kerakli yoki yo'qligini aniqlashingiz mumkin degani. Xulosa qiladigan bo'lsak, siz saytingizni 2 - usul orqali yaratsangiz, sizning sayt birinchisiga nisbatan foydalanuvchiga qulay bo'ladi. Bunday saytlarni yaratishda esa siz _Promise_'lardan foydalanishingiz mumkin.

Siz o'zingizni promise'ingizni yaratayotganda **Promise()** konstruktor metodidan foydalanishingiz kerak.

```js
const myPromise = new Promise((resolve, reject) => {
    ...
});
```

bu yerda `new` kalit so'zi yangi obyekt yaratilayotganini bildiradi.

Promise ham sinxron funksiyalar kabi oddiy qiymat qaytaradigan funksiya hisoblanadi. Faqat qiymatni birdaniga emas kelajakdagi ma'lum vaziyatlarga nisbatan qaytaradi.

Promise 3 xil holatdan birida bo'lishi mumkin.

- pending (kutilayotgan holat)
- fulfilled (bajarilgan holat)
- rejected (rad etilgan holat)

Pending holat - promise'ning boshlang'ish holati hisoblanadi. Promise pending holatdan so'ng fulfilled yoki rejected holatlaridan biriga o'tadi.

Agar promise fulfilled holatiga o'tadigan bo'lsa, promise bu holatning qiymat(value)ini qaytaradi.

Agar promise rejected holatiga o'tadigan bo'lsa,
promise bu holatning nimaga rad etilganligi sabab(reason, error)ini qaytaradi.

![states](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/promises.png)

`Promise()` - konstruktor metodiga parametr sifatida executor(baholovchi) funksiya 2 ta parametr funksiyalar(odatda resolve va reject) bilan keladi.

Qachonki executor funksiya ichida `resolve()` funksiya chaqirilsa, promise _pending_ holatdan _fulfilled_ holatiga o'tadi. Va promise'ning fulfilled holati qiymatini biz resolve() funksiyaga argument sifatida berib qaytaramiz.

Qachonki executor funksiya ichida `reject()` funksiya chaqirilsa, promise _pending_ holatdan _rejected_ holatiga o'tadi. Va promise'ning rejected holati qiymati(holatni rad etilish sababi)ni biz reject() funksiyaga argument sifatida berib qaytaramiz.

Keling endi kichkina bir misol orqali yuqoridagi gaplarinizni tahlil qilib chiqamiz.

```js
const executorFunc = (resolve, reject) => {
    if (biror shart){
        resolve('muvoffiqiyatli_qiymat');
    }
    else {
        reject('rad_etilganlik_sababi');
    }
};

const meningPromise = new Promise(executorFunc);
```

Bu yerda `meningPromise` degan o'zgaruvchi Promise() konstruktor metodi yordamida qurilayapti. Va bu konstruktorga argument sifatida `executorFunc` funksiyasi berib yuborilayapti. Executor funksiya ichida shart tekshirilayapti. Agar shart rost baholansa promise qiymati sifatida 'muvoffiqiyatli_qiymat', aks holatda 'rad_etilganlik_sababi' matnlari qaytarilayapti.

Bizning misolda promise holati sinxron tarzda oddiy shart operatori orqali baholanayapti. Real loyihalarda bu asinxron operatsiyalar orqali amalga oshadi. Misol tariqasida database'dan media fayllarni olishni keltirish mumkin.

Biz promise hosil qilishni va unga qiymat berishni o'rgandik. Endi keling shu qiymatlardan qanday foydalanish mumkinligini ko'rib chiqamiz.

Biz promise qaytarayotgan qiymatni ishlatimishiz uchun bizga [`then()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/then) metodi kerak bo'ladi.

`then()` funksiyasi ikkita parametr oladi. Birinchi parametr promise fulfilled bo'lganda, ikkinchi parametr esa promise rejected bo'lganda bajariladigan funksiyalardir.

```js
const promise = new Promise((resolve, reject) => {
  const num = Math.random();
  if (num < 0.5) {
    resolve("Muvoffiqiyatli!");
  } else {
    reject("Muvoffiqiyatsiz!");
  }
});

const handleSuccess = (qiymat) => {
  console.log(qiymat);
};

const handleFailure = (sabab) => {
  console.log(sabab);
};

promise.then(handleSuccess, handleFailure);
```

Yuqoridagi misolda natija `num` o'zgaruvchisi oladigan qiymatga bog'liqdir. Agar num o'zgaruvchisi qiymati 0.5 dan kichik bo'lsa promise'ning resolved holatdagi qiymati aks holda rejected qaytadi.

Ko'rib turganizdek `then()` metodi ikkata funksiya olayapti. Va bu funksiyalar tartibi muhim.

Qulaylik yaratish maqsadida bu ikkala paramertni ajratib yozish usuli kiritilgan. Buning uchun bizga _then_ ga o'xshash boshqa metod kerak bo'ladi. Bu metod nomini `catch()` deb nomlashgan. catch() metodi rejected qiymatlar bilan ishlash uchun mo'ljallangan.

Shunday qilib biz promise qiymatidan foydalanmoqchi bo'lsak, bizga `then()` va `catch()` metodlari kerak bo'lar ekan. _then_ resolved, _catch_ rejected qiymatlar bilan ishlar ekan.

```js
const promise = new Promise((resolve, reject) => {
  const num = Math.random();
  if (num < 0.5) {
    resolve("Muvoffiqiyatli!");
  } else {
    reject("Muvoffiqiyatsiz!");
  }
});

const handleSuccess = (qiymat) => {
  console.log(qiymat);
};

const handleFailure = (sabab) => {
  console.log(sabab);
};

promise.then(handleSuccess).catch(handleFailure);
```

## async \ await

JavaScriptda asinxron amallarni handle qilish uchun [**callback**](https://developer.mozilla.org/en-US/docs/Glossary/Callback_function) funksiyalardan foydalaniladi. Bir martalik amallar uchun callback'lardan foydalanishni yomon tarafi yo'q. Lekin callback'lar soni ko'paygan sayin, kodimiz shunchalik qiyinlashib boradi. Ya'ni bitta callback ichida boshqa callback va uning ichida yana boshqasi kelib kod murakkablashadi. Bunday kodlarni o'qish va tahlil qilish qiyin bo'ladi.

Shu sababdan [ES8](https://en.wikipedia.org/wiki/ECMAScript#8th_Edition_-_ECMAScript_2017)da bunday ishlarni qulaylashtirish uchun yangi tushuncha kiritilgan bo'lib, u [`async...await`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function) tushunchasidir.

JavaScriptda async\await yangi texnologiya hisoblanmaydi. U shunchaki promise'lar uchun yangi sintaksis holosdir. async\await'dan foydalanish bizga kodimiz o'qimishli va uni tahlil qilishga qulaylik yaratadi.

Biz bu sintaksisdan foydalanishimiz uchun yaratayotgan funksiyamiz oldiga `async` kalit so'zini qo'ysak yetarli.

```js
async function myFunc() {
  ...
}

myFunc();
```

Bunday usulda yaratilgan funksiyalar har doim promise qaytaradi. Bu degani biz oddiy promise'da bo'lgani kabi `then()` va `catch()` metodlaridan foydalansak bo'ladi degani.

```js
async function myFunc() {
  return "biror qiymat";
}

myFunc().then((qiymat) => console.log(qiymat));
```

Yuqoridagi misolda biz async kalit so'zidan foydalandiku lekin await kalit so'zidan foydalanmadik. Aslida async har doim await kalit so'zi bilan birga keladi. Ya'ni async orqali funksiya yaratayapmizmi uni ichida await'dan ham foydalanishimiz kerak.

`await` - ham o'zi bir operator hisoblanadi. Bu operator bizga promise'ning resolved qiymatini qaytarib beradi.

```js
async function myFunc() {
  const qiymat = await "biror qiymat";
  return qiymat;
}

myFunc().then((qiymat) => console.log(qiymat));
```

Bundan tashqari await operatori promise holati pending holatdan boshqa holatga o'tgangacha jarayonni to'xtatib turish vazifasini bajaradi. Shuning uchun ham async funksiyalarda await kalit so'zidan foydalanishni esdan chiqmaslik muhimdir.

```js
const meningPromise = () => {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve("Muvoffiqiyatli qiymat");
    }, 1000);
  });
};

async function awaitBilan() {
  const natija = await meningPromise();
  console.log(natija);
}

async function awaitSiz() {
  const natija = meningPromise();
  console.log(natija);
}

awaitBilan();
awaitSiz();
```

Quyidagi na'munaviy misolda siz async \ await sintaksisini qulayligini ko'rishingiz mumkin.

```js
function odatiySintaks() {
  birinchiPromise()
    .then((birinchiQiymat) => {
      ...
      return ikkinchiPromise(birinchiQiymat);
    })
    .then((ikkinchiQiymat) => {
      ...
      return uchinchiPromise(ikkinchiQiymat);
    })
    .then((uchinchiQiymat) => {
      ...
    });
}
```

```js
async function maxsusHolat() {
  const birinchiQiymat = await birinchiPromise();
  ...
  const ikkinchiQiymat = await ikkinchiPromise(birinchiQiymat);
  ...
  const uchinchiQiymat = await uchinchiPromise(ikkinchiQiymat);
}
```

Ko'rib turganizdek 2 - usulda kod yozish ancha qulaylik yaratadi.

async funksiyasi ham oddiy bir promise qaytarib beruvchi funksiya ekanligini hisobga olsak, biz promise rad etilish sabablarini o'sha odatiy `catch()` metodi orqali tutsak ham bo'ladi.

```js
async function xatoniTutish() {
  const qiymat = await birorPromise();
  ...
  return qiymat;
}

const ozgaruvchi = xatoniTutish();
ozgaruvchi.catch((xato) => console.log(xato));
```

Bundan tashqari promise'ning rad etilish sababini `try...catch` sintaksisi orqali ham tutsak bo'ladi.

```js
async function xatoniTutish() {
  try {
    const qiymat = await birorPromise();
    ...
  } catch (xato) {
    console.log(xato);
  }
}
```

Yuqoridagi ikkala yo'l ham xatoni tutish uchun to'g'ri yo'l hisoblanadi. Lekin `async...await` sintaksisi bilan `try...catch` sintaksisi ishlatilishi keng dasturchilar orasida keng tarqalgan.
