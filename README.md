# IleriPython_Hafta8
# Hafta 8 Laboratuvarı – Karakter Dizileri ve Özel Metotlar

**Ders:** Python ile Programlama  
**Öğrenci:** [Bedirhan Ündoğdu Yiğit]  
**Öğrenci numarası:** [20244029085]  
**Tarih:** [22/11/2026]

## Proje hakkında

Bu laboratuvar çalışmasında Python karakter dizisi metotlarını, fonksiyon yazmayı ve sınıflardaki özel metotları uyguladım. Görevlerde yönergeye uygun olarak **liste ve sözlük kullanmadım**. Sayı tabanı dönüşümlerinde `int(s, 16)`, `bin` ve `hex` gibi hazır dönüşümler yerine algoritmayı kendim kurdum.

## Çalıştırma

Python 3 kurulu bir bilgisayarda ZIP dosyasını açıp terminalden sırasıyla aşağıdaki komutları çalıştırabilirsiniz:

```bash
python hafta8_gorev1.py
python hafta8_gorev2.py
python hafta8_gorev3.py
python hafta8_gorev4.py
python hafta8_gorev5.py
python hafta8_bonus.py
```

## Görev 1 – E-posta doğrulayıcı (15 puan)

**Ne yaptım?** `eposta_denetle(adres)` fonksiyonunda `count` ile `@` sayısını kontrol ettim. `find` ve dilimleme ile kullanıcı adı ve alan adını ayırdım. Kullanıcı adındaki karakterlerin harf, sayı, nokta, alt çizgi ya da tire olmasına izin verdim. Noktayla başlama/bitme, alan adında nokta olmaması ve yan yana iki nokta bulunması durumlarında hata mesajı döndürdüm.

**Neden?** Adresin farklı kurallarını belirli sırayla denetlemek ve ilk hatayı anlaşılır şekilde göstermek için.

**Örnek:** `ece.yilmaz@nisantasi.edu.tr` → `Geçerli`; `ece@@mail.com` → `Tam olarak bir @ olmalı`.

## Görev 2 – Taban dönüştürücü (20 puan)

**Ne yaptım?** `onluktan(n, taban)` sayıyı hedef tabana çevirmek için tekrar tekrar kalan alıyor ve elde ettiği rakamı metnin başına ekliyor. `onluga(metin, taban)` ise Horner yöntemiyle mevcut sonucu tabanla çarpıp yeni basamağı ekliyor. `RAKAM.find()` karakteri sayısal basamağa dönüştürüyor.

**Neden?** Hazır dönüşüm fonksiyonlarının içindeki mantığı anlamak için.

**Örnek:** 2026 → `11111101010` (2), `3752` (8), `7EA` (16).

## Görev 3 – Vigenère şifresi (20 puan)

**Ne yaptım?** `vigenere(metin, anahtar, yon=1)` fonksiyonunda harflerin alfabedeki sırasını bulup anahtardaki harf kadar kaydırdım. Anahtarı `j % len(anahtar)` ile döngüsel kullandım; boşluk ve noktalama işaretleri anahtarın konumunu ilerletmiyor. `yon=-1` girilince kaydırma tersine dönüyor.

**Neden?** Modüler aritmetik ile aynı fonksiyonun hem şifreleme hem çözmede kullanılmasını göstermek için.

**Örnek:** `Attack at dawn` + `LEMON` → `Lxfopv ef rnhr`.

## Görev 4 – Kesir sınıfı v2 (20 puan)

**Ne yaptım?** `Kesir` sınıfında paydanın sıfır olmasını engelledim ve `gcd` ile kesri sadeleştirdim. `__add__`, `__sub__`, `__mul__`, `__truediv__` yeni Kesir nesneleri döndürüyor. `__eq__`, `__lt__`, `__le__` değerleri çapraz çarpımla karşılaştırıyor. `__str__` ekrana yazdırılacak metni, `__float__` ondalık karşılığı veriyor.

**Neden?** Matematiksel operatörlerin sınıf nesneleriyle de doğal bir biçimde kullanılabilmesini sağlamak için.

**Örnek:** Çarpım `1/10`, en büyük kesir `4/9`; `Kesir(6,8) == Kesir(3,4)` → `True`.

## Görev 5 – Türkçe kelime sınıfı (25 puan)

**Ne yaptım?** `TrKelime` sınıfında `I` harfini `ı`, `İ` harfini `i` yaparak Türkçeye uygun küçültme yaptım. `__str__`, `__len__`, `__getitem__`, `__contains__`, `__eq__` metotlarını yazdım. `__lt__` içinde harfleri Unicode kodları yerine `ALFABE.find` konumlarına göre karşılaştırdım. `buyuk()` ise Türkçeye uygun büyütme yapıyor.

**Neden?** Python'un varsayılan karakter sıralamasının Türkçe alfabetik sıralamadan farklı olabilmesi nedeniyle.

**Örnek:** `çay < dağ` → Türkçede `True`; `TrKelime("İSTANBUL").buyuk()` → `İSTANBUL`.

**UML:** `TrKelime_UML.png` ve `TrKelime_UML.dot` dosyalarında sınıfın alanı ve metotları gösterildi.

## Bonus – Roma rakamları (+10 puan)

**Ne yaptım?** `romaya(sayi)` ile sayılardan Roma rakamlarına, `onluga(roma)` ile Roma rakamlarından sayılara dönüşüm yaptım. Çıkarma kurallarını `IV`, `IX`, `XL`, `XC`, `CD`, `CM` çiftleriyle ele aldım.

**Örnek:** 2026 → `MMXXVI`; 1994 → `MCMXCIV`; `XLII` → 42.

## Kendi değerlendirmem ve kontrol

PDF'deki örnekleri ve farklı girdileri test ettim. Özellikle geçersiz e-posta adresleri, geçersiz taban rakamları, boş anahtar, sıfır payda ve Türkçe I/İ ayrımını kontrol ettim. Her Python dosyasının başındaki öğrenci bilgilerini teslimden önce doldurmalıyım.

**Not:** Bu açıklamaları ve kaynak kodları teslim etmeden önce kendi çalışmamla karşılaştırıp her satırını anlayarak düzenlemem gerekiyor; ders yönergesi yapay zekâ kullanımını yalnızca konuyu anlamak için kabul ediyor.
