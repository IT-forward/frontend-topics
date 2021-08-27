# Backwards & Forwards

## Compatibility Nima?

[**Compatibility**](https://en.wikipedia.org/wiki/Compatibility) deganda ikkita narsani bir - biriga mos kelishi, birga to'g'ri ishlashi tushuniladi.

Bu so'zni inglizchadan o'zbekchaga tarjima qilganda ham aynan "muvofiqlik", "moslik" degan ma'nolarni bildiradi.

Agar siz kompyuteringiz orqali printerdan pechat chiqara olayotgan bo'lsangiz, sizning komputeringiz va printeringiz bir - biriga compatible(mos) bo'ladi. Yoki siz televizoringizni pult orqali boshqara olyapsizmi demak, bu ikki qurilma bir - biriga mos hisoblanadi.

Bu tushunchani JavaScript'ga talqin qiladigan bo'lsak, JavaScript kodlari va Web Browser'lar bir - biriga compatible'dir.

Shunday qilib compatibility bu - ikkita narsani qanchalik bir - biriga mosligi ekan.

Compatibility o'z navbatida biror kutubxona yoki dasturlash tiliga nisbatan qo'llanilganda u ikkiga ya'ni **backward compatibility** va **forward compatibility**'larga bo'linadi.

## Backward Compatibility

Yuqorida compatibility'lar ikki guruhga bo'linishi aytildi. Tabiiyki sizda javascript dasturlash tili qaysi guruhga kiradi degan savol tug'iladi.

JavaScript dasturlash tili [**backward compatible**](https://en.wikipedia.org/wiki/Backward_compatibility) dasturlash tilidir.

Backward compatible nima degani? Nomidan sezilib turganidek "ortga moslashgan" degan ma'noni bildiradi. Ya'ni siz 1997 - yilda javascript yordamida yozilgan saytni bemalol 2021 - yildagi browser'larda ishlata olsasiz degani. Bunda sizga hech qanday muammolar uchramaydi. Bu sayt 1997 - yilda browser'larda qanday ochilgan bo'lsa, zamonaviy browser'larda ham xuddi o'shanday ochiladi.

Tushunib turganizdek 1997 - yilda yozilgan javascript kodi, 2021 - yilga kelib yaroqsiz kodga aylanib qolmas ekan.

![backwards](https://i.ibb.co/4j0bxKb/2021-08-25-11-14.png)

JavaScript dasturlash tilida hech qachon eskirgan texnologiya o'chirib yuborilmaydi yoki boshqasi bilan almashtirilmaydi. Bu esa javascript tilini backward compatibility bo'lishini ta'minlaydi.

## Forward Compatibility

Backward compatibility'ga teskari bo'lgan compatibility bu [**forward compatibility**](https://en.wikipedia.org/wiki/Forward_compatibility) hisoblanib, tarjimada "oldinga moslashgan" degan ma'noni bildiradi.

JavaScript dasturlash tili forward compatible bo'lishi uchun hozirda biz ishlatib turgan web browser'lar kelajakda javascript yordamida yaratiladigan web saytlarni muammosiz o'qiy olishi kerak bo'ladi. Bu esa amaliy imkonsizdir. Chunki biz kelajakda EcmaScript standartlari qay ko'rinishda bo'lishini oldindan ayta olmaymiz. Shuning uchun biz hozirgi browser'larni kelajakka moslay olmaymiz.

![not forward](https://i.ibb.co/pWHtw7c/2021-08-25-16-07.png)

Forward compatible tillarga markerlash va stillash tillarini, shu jumladan HTML va CSS tillarini keltirshimiz mumkin. Kelajakda bu tillar yordamida yozilgan kodni bemalol hozirgi browserlar orqali ochsa bo'ladi. Bunda browser yuklanishida muammolar kuzatilmaydi. Lekin kelajakda javascript yordamida yozilgan kodni hozirgi browserlarda ochsak katta ehtimol bilan browser yuklanishida muammolar yuzaga keladi. Bu shu tilda yangi texnologiya qo'shilgan yoki qo'shilmaganligiga bog'liqdir.

HTML va CSS nima uchun forward compatible ekanligini aytadigan bo'lsak, sababi bu tillar dasturlash tillari hisoblanmaydi.

Agar kelajakda CSS tiliga qandaydur yangi stil qo'shiladigan bo'lsa, hozirgi browser elementdagi shu stilni tashlab ketib, o'zi tushunadigan stillarini o'qiyveradi. Bunda sayt ko'rinishida muammolar bo'lishi mumkin, lekin browser yuklanishida muammo bo'lmaydi.

Xuddi shu holatni HTML tilida ham kuzatshimiz mumkin. Shu xusiyatga ko'ra bu tillar forward compatible tillar hisolanadi.

## Xulosa

- Compatibility bu ikkita narsani qanchalik bir - biriga mosligi ekan.
- Compatibility backward va forward compatibility'larga bo'linar ekan.
- Ko'pchilik dasturlash tillari backward compatible, ko'pchilik markerlash va stillash tillari forward compatible hisoblanar ekan.
