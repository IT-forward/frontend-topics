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

JavaScript Engine kodni o'qish jarayonida asinxron funksiyalarni [queue](<https://dmitripavlutin.com/javascript-queue/#:~:text=The%20queue%20data%20structure%20is,constant%20time%20O(1)%20.>)(navbat)ga yig'ib boradi va hamma sinxron funksiyalarni bajarib bo'lgandan so'ng, navbati bilan queue'dagi asinxron funksiyalarni bajarishni boshlaydi.

Shuning uchun bizni misolimizda setTimeout funksiyaga nol argumenti berilgani bilan ham u oxirida bajarilyapti.

Quyidagi misolni o'zingiz tahlil qilib, browser console'ida javobingiz tekshirib ko'ring.

```js
console.log("1 - chiqadi");
setTimeout(() => console.log("2 - chiqadi"), 10);
setTimeout(() => console.log("3 - chiqadi"), 0);
console.log("4 - chiqadi");
```

> Shunday qilib bir amalni to'liq bajarilib bo'lishini kutib, keyin boshqa amal bajarilishi **sinxron** amal deyiladi. Bir amalni to'liq bajarilib bo'lishini kutmasdan turib, boshqa amalni bajarilishi **asinxron** amal deyiladi.

## Promise

Biz yuqorida sinxron va asinxron funksiyalar bilan tanishdik. Endi **asinxron** funksiya ishlash prinsipi asosida qurilgan metodlardan biri [**Promise**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) lar bilan tanishamiz.

Tasavvur qiling siz sherigingiz bilan restoranga kirdingiz va biror bo'sh joyga o'tirdingiz. Keyin ofitsiant sizdan buyurtma olish uchun keldi. Siz biror taom buyurtma berdingiz. Ofitsiant sizning buyurtmangizni o'z daftarchasiga yozdi va oshxona tomon yo'l oldi. Endi siz buyurtmangiz kelmagungacha joyingizdan turmay, hech kimga gapirmay, faqat oshxona tomonga qarab, ofitsiantni kutib o'tirasizmi? Albatta yo'q. Siz sherigingiz bilan suhbatlashib, derazadan ko'chaga qarab o'tirasiz. Ma'lum muddatdan so'ng ofitsiant buyurtmangizni olib keladi. Va sizga yoqimli ishtaxa tilab, o'z ishini davom ettiradi.

Sizni buyurtma kelgunigacha sherigingiz bilan suhbatlashgan va derazadan ko'chaga qaragan amallaringiz **sinxron** amallar hisoblanadi. Sizni ofitsiantga taom buyurtma qilishingiz esa **asinxron** amal hisoblanadi va u **promise** deb nomlanadi.
Ofitsiant sizga olib kelib bergan _taom_ esa promise _qiymat_ i hisoblanadi.

Endi tasavvur qiling sizni ofitsiantga buyurtma qilgan taomingiz har doim ham oshxonada mavjud bo'lmasligi mumkin. Shunda ofitsiant nima qiladi? Ofitsiant kelib sizga oshxonada bu taom qolmaganligi sabab buyurtmangizni olib kela olmaganini aytadi va sizga boshqa biror taom buyurtma qilishingizni taklif qiladi.

Biz yuqoridagi misolda promise qaysi amal ekanligini aytdik. Bundan ko'rinib turibdiki promise uch xil holatdan birida bo'lar ekan.
1 - holat: ofitsiant sizdan buyurtmani olib, oshxonaga borib, yana qaytib kelish holati.
2 - holat: ofitsiant sizga taomingizni olib kelishi mumkin bo'lgan holat.
3 - holat: oshxonada siz buyurtma qilgan taom bo'lmaganligi sababli, ofitsiant buyurmangizni olib kela olmagan holat.

Shunday qilib promise __uch xil holat__ dan birida bo'lar ekan. Bular:

- pending (kutilayotgan holat)
- fulfilled (bajarilgan holat)
- rejected (rad etilgan holat)

Siz o'z promise'ingizni yaratayotganda **Promise()** konstruktor metodidan foydalanishingiz kerak bo'ladi.

```js
const myPromise = new Promise((resolve, reject) => {
    ...
});
```

bu yerda `new` kalit so'zi yangi obyekt yaratilayotganini bildiradi.

Promise ham sinxron funksiyalar kabi oddiy qiymat qaytaradigan funksiya hisoblanadi. Faqat qiymatni birdaniga emas, kelajakdagi ma'lum vaziyatlarga nisbatan qaytaradi.

Pending holat - promise'ning boshlang'ish holati hisoblanadi. Promise pending holatdan so'ng fulfilled yoki rejected holatlaridan biriga o'tadi.

Agar promise fulfilled holatiga o'tadigan bo'lsa, promise bu holatning qiymat(value)ini qaytaradi.

Agar promise rejected holatiga o'tadigan bo'lsa,
promise bu holatning nimaga rad etilganligi sabab(reason, error)ini qaytaradi.

![states](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/promises.png)

`Promise()` - konstruktor metodiga parametr sifatida executor(bajaruvchi) funksiya 2 ta parametr funksiyalar(odatda resolve va reject) bilan keladi.

Qachonki executor funksiya ichida `resolve()` funksiya chaqirilsa, promise _pending_ holatdan _fulfilled_ holatiga o'tadi. Va promise'ning fulfilled holati qiymatini biz resolve() funksiyaga argument sifatida berib qaytaramiz.

Qachonki executor funksiya ichida `reject()` funksiya chaqirilsa, promise _pending_ holatdan _rejected_ holatiga o'tadi. Va promise'ning rejected holati qiymati(holatni rad etilish sababi)ni biz reject() funksiyaga argument sifatida berib qaytaramiz.

Keling endi kichkina bir misol orqali yuqoridagi gaplarinizni tahlil qilib chiqamiz.

```js
const executorFunc = (resolve, reject) => {
    if (biror shart){
        resolve('muvaffaqiyatli_qiymat');
    }
    else {
        reject('rad_etilganlik_sababi');
    }
};

const myPromise = new Promise(executorFunc);
```

Bu yerda `myPromise` degan o'zgaruvchi Promise() konstruktor metodi yordamida qurilayapti. Va bu konstruktorga argument sifatida `executorFunc` funksiyasi berib yuborilayapti. Executor funksiyasi ichida shart tekshirilayapti. Agar shart rost baholansa promise qiymati sifatida _'muvaffaqiyatli_qiymat'_, aks holatda _'rad_etilganlik_sababi'_ matnlari qaytarilayapti.

Bizning misolda promise'ning pending holati sinxron tarzda oddiy shart operatori orqali baholanayapti. Real loyihalarda bu asinxron operatsiyalar orqali amalga oshadi. Misol tariqasida database'dan biror ma'lumotlarni olishni keltirish mumkin.

Biz promise hosil qilishni va unga qiymat berishni o'rgandik. Endi keling shu qiymatlardan qanday foydalanish mumkinligini ko'rib chiqamiz.

Biz promise qaytarayotgan qiymatni ishlatimishiz uchun bizga [`then()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/then) metodi kerak bo'ladi.

`then()` funksiyasi ikkita parametr oladi. Birinchi parametr promise _fulfilled_ bo'lganda, ikkinchi parametr esa promise _rejected_ bo'lganda bajariladigan funksiyalardir.

```js
const promise = new Promise((resolve, reject) => {
  const num = Math.random();
  if (num < 0.5) {
    resolve("Muvaffaqiyatli!");
  } else {
    reject("Muvaffaqiyatsiz!");
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

Yuqoridagi misolda natija `num` o'zgaruvchisi oladigan qiymatga bog'liqdir.

Agar num o'zgaruvchisi qiymati 0.5 dan kichik bo'lsa, `if` operatori bajariladi va uning ichidagi `resolve()` funksiyasi chaqiriladi. _resolve()_ funksiya chaqirildi degani, promise'ning holati o'zgardi deganidir. Ya'ni _pending_ holatdan _fulfilled_ holatga o'tdi degani. Va bu holatning qiymati _resolve()_ funkiyasiga argument sifatida berib qaytarilyapti.

Agar num o'zgaruvchisi 0.5 dan kichik bo'lmagan qiymat olsa, u holda `else` operatori bajariladi va uning ichidagi `reject()` funksiyasi chaqiriladi. Bunda ham _reject()_ funksiya chaqirildi degani, promise'ning holati o'zgardi deganidir. Ya'ni _pending_ holatdan _rejected_ holatiga o'tdi degani. Va bu holatning qiymati(rad etilganlik sababi) _reject()_ funksiyaga argument sifatida berib qaytarilyapti.

Bizning misolda ikkala resolve() va reject() funksiyalari qaytaradigan qiymat, promise'ning qiymati ham bo'ladi.

Yuqoridagi misolda ko'rib turganinggizdek `then()` metodi ikkata funksiya olayapti. Va bu funksiyalar tartibi muhimdir.

_then()_ metodidagi 1 - parametr funksiya qachonki promise holati fulfilled holatga o'tganda bajariladi. 2 - parametr funksiya esa promise holati rejected holatga o'tganda bajariladi.

Shu sababli bu funksiyalar tartibi muhim hisoblanadi.

Qulaylik yaratish maqsadida bu ikkala paramertlarni ajratib yozish usuli kiritilgan. Buning uchun bizga _then_ ga o'xshash boshqa metod kerak bo'ladi. Bu metod nomini `catch()` deb nomlashgan. catch() metodi rejected qiymatlar bilan ishlash uchun mo'ljallangan.

```js
  ...

promise.then(handleSuccess).catch(handleFailure);
```

Tasavvur qiling siz biror promise ishlatdingiz va bu promise'ning qiymati sifatida sizga boshqa bir yangi promise qaytmoqda. Bunday holatlarda siz birinchi promise qiymatini then() orqali ishlatib, undan qaytayotgan qiymatni yana then() metodi bilan ishlatshingiz mumkin bo'ladi.

`promise.then(handleSuccess).then(handleSuccess_2);`

Bunday korinishdagi bog'lanishlarni inglizchada **promise chaining** ya'ni zanjir bog'lanish deb atashadi.

```js
const promise = new Promise((resolve, reject) => {
  if (biror_shart) {
    const yangiPromise = new Promise((resolve2, reject2) => {
      if (yana_biror_shart) {
          ...
        resolve2(qiymat);
      } else {
          ...
        reject2(sabab);
      }
    });

    resolve(yangiPromise);
  } else {
    reject(sabab);
  }
});

promise
  .then((natija) => console.log(natija))
  .then((natija2) => console.log(natija2))
  .catch((sabab) => console.log(sabab));
```

JavaScriptda promise chaining'larni tagma - tag yozish imkoniyati kiritilgan va u yuqorida ham ishlatildi.

> Yuqoridagi misolda catch() metodi, har ikkala promise'ning birortasi rejected holatga o'tganda chaqiriladi va shu promise'dan keyingi then() metodlarning bajarilishi to'xtatiladi.

Shunday qilib biz promise qiymatidan foydalanmoqchi bo'lsak, bizga `then()` va `catch()` metodlari kerak bo'lar ekan. _then_ resolved, _catch_ rejected qiymatlar bilan ishlar ekan.

## async \ await

JavaScriptda asinxron ifodalar bilan ishlash uchun [**callback**](https://developer.mozilla.org/en-US/docs/Glossary/Callback_function) funksiyalardan foydalaniladi. Bir martalik amallar uchun callback'lardan foydalanishni yomon tarafi yo'q. Lekin callback'lar soni ko'paygan sayin, kodimiz shunchalik qiyinlashib boradi. Ya'ni bitta callback ichida boshqa callback va uning ichida yana boshqasi kelib kod murakkablashadi. Bunday kodlarni o'qish va tahlil qilish qiyin bo'ladi.

Shu sababdan [ES8](https://en.wikipedia.org/wiki/ECMAScript#8th_Edition_-_ECMAScript_2017)da bunday ishlarni qulaylashtirish uchun yangi tushuncha kiritilgan bo'lib, u [`async...await`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function) tushunchasidir.

JavaScriptda async\await yangi texnologiya hisoblanmaydi. U shunchaki promise'lar uchun yangi sintaksis xolosdir. async\await'dan foydalanish bizga kodimizni o'qimishli bo'lishiga va uni tahlil qilishga qulaylik yaratadi.

Biz bu sintaksisdan foydalanishimiz uchun yaratayotgan asinxron funksiyamiz oldiga `async` kalit so'zini qo'ysak yetarli.

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

myFunc().then((qiymat) => console.log(qiymat)); // biror qiymat
```

Yuqoridagi misolda biz async kalit so'zidan foydalandik-u, lekin await kalit so'zidan foydalanmadik. Aslida async har doim await kalit so'zi bilan birga keladi. Ya'ni foydali ish qiladigan asinxron funksiya yaratayapmizmi, bu funksiya oldiga async kalit so'zini qo'yishimiz va uni ichda await'dan foydalanishimiz kerak bo'ladi.

`await` - ham o'zi bir operator hisoblanadi. Bu operator odatda promise'lar bilan ishlatiladi va shu promise'ning resolved qiymatini qaytaradi.

Quyida ma'lum vazifani 2 xil yo'l orqali bajarish ko'rsatilgan.

```js
// 1 - yo'l

fetch('url').then((response) => console.log(response));

console.log('keyingi amallar'); // bu amal har doim bajariladi
 ...
```

```js
// 2 - yo'l

const response = await fetch('url');
console.log(response);

console.log('keyingi amallar'); // bu amalni bajarilishi response o'zgaruvchisi qiymatiga bog'liq 
 ...
```

2 - holatning o'ziga xosligi shundaki, await operatoridan keyin kelayotgan amallar await operatori qaytaradigan qiymatga bog'liqligidadir. Agar await _error_ qaytarmasa, await'dan keyingi amallar bajariladi aks holda bajarilmaydi.

Boshqacha aytganda await operatori promise holati pending holatdan boshqa holatga o'tgungacha jarayonni to'xtatib turish vazifasini ham bajaradi. Shuning uchun ham async funksiyalarda await kalit so'zidan foydalanishni esdan chiqmaslik muhimdir.

```js
const myPromise = () => {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve("Muvaffaqiyatli qiymat");
    }, 1000);
  });
};

async function awaitBilan() {
  const natija = await myPromise();
  console.log(natija);
}

async function awaitSiz() {
  const natija = myPromise();
  console.log(natija);
}

awaitBilan(); // Muvaffaqiyatli qiymat
awaitSiz(); // Promise(...)
```

To'g'riroq qilib aytganda await operatoridan keyin keladigan amallar aslida _then chaining_'dagi ikkinchi then() ichidagi amallardir.

```js
const promise = new Promise((resolve, reject) => {
  if (biror_shart) {
    const yangiPromise = new Promise((resolve2, reject2) => {
      if (yana_biror_shart) {
          ...
        resolve2(qiymat);
      } else {
          ...
        reject2(sabab);
      }
    });

    resolve(yangiPromise);
  } else {
    reject(sabab);
  }
});

promise
  .then((natija) => console.log(natija))
  .then((natija2) => console.log(natija2))
  .catch((sabab) => console.log(sabab));
```

```js
 ...

 async function awaitFunc() {
   const yangiPromise = await promise;
   console.log(yangiPromise);
   const natija2 = await yangiPromise;
   console.log(natija2);
 }

 awaitFunc().catch((sabab) => console.log(sabab));
```

> Yuqoridagi misolni o'zingiz yaxshilab tahlil qilib o'rganing!

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
async function maxsusSintaks() {
  const birinchiQiymat = await birinchiPromise();
  ...
  const ikkinchiQiymat = await ikkinchiPromise(birinchiQiymat);
  ...
  const uchinchiQiymat = await uchinchiPromise(ikkinchiQiymat);
}
```

Ko'rib turganizdek 2 - usulda kod yozish ancha qulaylik yaratadi.

async funksiyasi ham oddiy bir promise qaytarib beruvchi funksiya ekanligini inobatga olsak, biz promise rad etilish sabablarini o'sha odatiy `catch()` metodi orqali tutsak ham bo'ladi.

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

Yuqoridagi ikkala yo'l ham xatoni tutish uchun to'g'ri yo'l hisoblanadi. Lekin `async...await` sintaksisi bilan `try...catch` sintaksisi ishlatilishi dasturchilar orasida keng tarqalgan.

## Xulosa 

- Shunday qilib JavaScript'da __asinxron__ amallar __sinxon__ amallardan so'ng bajarilar ekan.

- JavaScript'da asinxron amallarni to'g'ri boshqarish uchun __Promise__ objecti kiritilgan ekan.

- Promise 3 xil holatdan birida bo'lar ekan (pending, fulfilled, rejected).

- Promise'ning qiymatidan foydalanish uchun `then()`, rad etilganlik sababidan foydalanish uchun `catch()` metodlaridan foydalanar ekanmiz.

- Promise'dagi _promise chaining_ larni yozishni qulaylashtirish maqsadida JavaScrip'da yangi sintaksis kiritilgan bo'lib, u `async \ await` sintaksisi deb nomlanar ekan.

- async \ await sintaksisini qulayligi u bizga asinxron kodimizni xuddi sinxron kod ko'rinishida yozishimizga imkon berishida ekan.

- async \ await sintaksisi bilan ishlaganda xatolarni tutish uchun `try...catch` sintaksisidan foydalanish keng tarqalgan ekan.
