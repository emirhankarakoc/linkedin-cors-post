ben bu problemleri cozmek icin linkedindeki sabitlenmis postlara surekli gittigim icin , buraya cekip linkedini biraz daha temiz gostermek istedim. o yuzden bu repo burada, herhangi bir farkli amaci yok. daha rahat bulmak icin, dostlarimin pclerinden de bulabilmek icin bu repo acildi.
# -

spring PROJELERİNİ DEPLOYLARKEN KARŞILAŞTIĞIM DÜMENDEN SIKINTILARA BULDUĞUM ŞİPŞAK ÇÖZÜMLER:

1- spring security olmadan corsu halletmek
bu hatanın niyesini çok iyi öğrendim. security ekleyince düzeltmesi kolay. sadece ben security'siz nasıl yapılacağını biraz kovaladım. GOOGLE COPILOT ile hallettik. basit bir config classı. herhangi bi security dependency'si yok.
kod: https://github.com/emirhankarakoc/project-betting/blob/main/src/main/java/com/betting/karakoc/utils/CorsConfig.java (importlar hariç 12 satır)

2- chrome console'da mixed content hatası
sizin backend url'niz https ://url.com ama isteği http ://url.com'a atıyorsanız bu hatayı alırsınız. (sonda s harfi yoksa veya tam tersiyse) yapmanız gereken basit. swagger üzerinden istek atıyorsanız openapiconfig yazmanız lazım.
normalden atıyorsanız postman , fetch vs. sonuna bi harf koyun düzeltin ama bana canlıdaki swagger da lazım şu anlık. o yüzden hata bu çözüm bu
kod: https://github.com/emirhankarakoc/project-betting/blob/main/src/main/java/com/betting/karakoc/utils/OpenApiConfig.java#L13 (importlar hariç 13 satır)


3- projeyi deploy etmeden cors varmı yok mu test etmek(deploy süresinin uzunluğu , 1 satır değiştirip 3-4 dk beklemek ve sonra 10 defa daha aynı şeyi yapmak)
intellij idea html kodlarını destekliyor. projenin alt tarafına bi folder oluşturup içerisine html kodu yazabiliyor ve live server(vscodedaki gibi) başlatabiliyorsunuz.

burada uzun bi paraagraf vardı eksik / yanlış şeyler yazıyordu.silindi ve alttaki DÜZELTME'leri ekledim. eğer başka YANLIŞ şey görürseniz. LÜTFEN yorumlarda belirtin. düzeltirim.

duzeltme:
Ömer Kocaoğlu'nun yorumunu okuduktan sonra , girip tek tek denedim.

CORS CONFIG OLMADAN:
-Tarayıcıdan , yani local8080 olmayan farklı bir porttan(localhost:63342) isteği atarsam cors dönüyor. 
-postmandan ORIGIN YOK. CORS YOK, response dönüyor..
-postmandan ORIGIN VAR local8080 harici (backendin çalıştığı port) bir origin verirsem , CORS alıyorum.

CORS CONFIG VARSA (herkese açık. public api)
-Tarayıcıdan , herhangi bi urlden isteği atın, response geliyor.
- postmandan originli veya originsiz isteği atın,response geliyor.

düzeltme2:
ben aslında bu corsu: frontta aldığım için böyle yazmıştım. eksik biliyormuşum. sağol ömer abi


intellij ideada bir html kodu çalıştırdığınız zaman , gene localhostten atıyor AMA portu :8080 değil. bendeki 63342. portlar aynı olmazsa cors alırsınız. biz corsu kaldırdık birinci paragrafta. benim corsu iptal etme çözümünden bağımsız burayı yazıyorum.

çalışmaya başlayan html sayfası , backendin portuyla aynı portta olmadığı için herhangi bir cors configi yapmadıysanız cors alacaksınız. projeyi deploy edip corsu kontrol etmekten %1000 daha hızlı.

 gcloud app deploy xx.jar yapıyorsunuz 5 sn bekletip y/n soruyor. (5 sn + upload file süresi)
renderdan deployluyorsunuz , lastest commiti alıyor , build alıyor , çalıştırıyor. ölme eşşşşşeğim ölme. 

velhasıl kelam.
farklı originden nasıl istek atarsınız?, alın en basit halinin kodu.
https://github.com/emirhankarakoc/project-betting/blob/main/xyz/simpleApiCall.html
(importlar hariç 11 satır)

hayırlı kodlamalar , hayırlı cumalar.
