WA Kod Standardı
==========

Bu döküman workattack bünyesi altında yapılan projelerin ortak bir standart altında toplanması amacı ile hazırlanmıştır. 

Zend Framework Coding Standart dökümanını temel alır. Buna ek olarak workattack'ın ihtiyaçları doğrultusunda bazı değişiklikler içerir.

PHP Dosya Formatı
===

Genel
---
Sadece PHP kodu içeren dosyalar için kapama tag'i ("?>") asla kullanılmaz. PHP için gerekli değildir ve sunucu cevap verirken yanlışkla eklenen boşluk karakterlerini eklemeye yarar.

Ayrıca dosyalar UTF-8 kodlaması ile kodlanmış olup BOM içermemelidirler.

Girintiler (Indentation)
---
Girintiler 4 boşluk karakterinden oluşur. Tab asla kullanılmaz.

Maksimum Satır Uzunluğu
---
Hedef satır uzunluğu 80 karakterdir. Geliştiriciler kodun okunaklı olması için satır uzunluklarını 80 karakterle sınırlamaya çalışmalıdırlar. Bazı durumlarda daha uzun satırlar kabul edilebilir. Geliştirici 120 satırı geçmemeye özen göstermelidir.

Satır Sonları
---
Satır sonları Unix text dosyası formatını temel alır. Satırlar tek bir linefeed (LF) karakteri ile bitmelidir. Linefeed karakterleri ordinal 10, veya hexadecimal 0x0A olarak tanımlanır.

Dolayısı ile Apple OS satır sonları (CR) veya Windows satır sonu (CRLF) kullanılmamalıdır.

İsimlendirmeler
===
Sınıflar (Classes)
---
Eğer bir framework kullanılıyor ise (Zend FW, Laravel vs.). Burada kullanılan sınıf isimlerinin klasörlerle eşletirilmesini sağlayan konvansiyon kullanılıcaktır.

Sınıf isimleri büyük harfle başlar. Birden fazla kelimeden oluşan sınıf isimlerinde kelimeler büyük harfle başlar. Birden fazla büyük harf arka arkaya kullanılmaz.

Örneğin:
Base_Controller, Zend_Pdf geçerli isimlendir fakat Zend_PDF geçerli değildir.

Dosya isimleri
---
Kullanılan framework'ün dosya yapısı göz önünde bulundurulur. 

Diğer bütün dosyalar sadece alfanümerik karakterlerden, dash (-) veya underscore (_) karakterlerinden oluşurlar. Boşluklara kesinlikle izin verilmez.

PHP kodu içeren tüm dosyalar ".php" uzantısı ile bitmelidirler. Bu kurala istisna gene kullanılan framework'ün dosya yapısı ve "view" dosyalarıdır.

Fonksiyon ve Metodlar
---
Fonksiyon isimlerinde sadece alfanümerik karakterler kullanılır. Dash '_' karakteri kullanılmaz. Rakamlara izin verilir fakat kullanımı pek önerilmez.

Fonksiyon ve metod isimleri daima küçük harf ile başlar. İsim birden fazla karakterden oluştuğu zaman her kelimenin baş harfi büyük harf olarak yazılır. Buna genel olaral "camelCase" denir.

filterInput()
getElementById()
widgetFactory()

Nesne yönelimli programlamadai erişimciler veya statik değişkenler daima "get" veya "set" ile başlamalıdır. Singleton ve Factory gibi programlama kalıplarında metod ismi mümkün olduğunca bu kalıbında ismini içermelidir.

Nesneler içinde "private" veya "protected" olarak deklare edilen metodlar tek bir underscore _ karakteri ile başlar. Bu bir fonksiyon isminde underscore karakterinin kullanılmasının tek istisnasıdır. "public" metodlar underscore içermez.

Global alandaki fonksiyonlara ("floating functions") izin verilir ama kullanımları tasvip edilmez.

Bunları statik sınıflar içindek kullanmayı düşünün.

Sınıflar mümkün olduğu kadar yaptıkları işi anlatacak şekilde isimlendirilmelidirler.

Değişkenler
---
Değişken isimlerinde sadece alfanümerik karakterler kullanılır. Dash '_' karakteri kullanılmaz. Rakamlara izin verilir fakat kullanımı pek önerilmez.

"private" veya "protected" olarak deklare edilen sınıf değişkenler tek bir underscore _ karakteri ile başlar.

Bu bir fonksiyon isminde underscore karakterinin kullanılmasının tek istisnasıdır. "public" değişkenler underscore içermez.

Aynen fonksiyon isimleri gibi değişken isimleri de küçük harf ile başlar ve "camelCase" olarak devam eder.

Değişken isimleri mümkün olduğu kadar geliştiricinin değişkende tutmayı düşündüğü veriyi tanımlayacak şekilde olmalıdır. "$i" veya "$n" gibi değişkenler sadece çok kısa döngülerde kullanılır. Eğer bir dözgü 20 satırdan fazla ise index değişkenleri daha tanımlayıcı isimlere sahip olmalıdır.

Sabitler
---
Sabitler hem alfanümerik karakterler hem de underscore (`_`) karakteri içerebilir.

Sabit isimleri içinde kullanılan tüm harfler büyük harf olmalıdır. İsim içindeki her kelime bir underscore ile ayrılır.

Örneğin, EMBED_SUPPRESS_EMBED_EXCEPTION geçerliyken  EMBED_SUPPRESSEMBEDEXCEPTION'a izin verilmez.

Sabitler "const" belirteçi ile tanımlanmalı ve sınıf altında olmalıdırlar. "define" ile tanımlanan Global sabitlere izin verilir ama kullanımları önerilmez.

Kod Stili
===
PHP Sınırları 
---
PHP kodu her zaman tam php tag'leri ile çevrelenmelidir.
<?php
 
?>
String'ler
---
Bir sözcük dizgisi (değişken içermediği zaman) tek bir tırnak (apostrof) ile çevrelenir.

`$a = 'Example String';`

String Literals Containing Apostrophes
---

Bir sözcük dizgisi kendisi apostrof veya tek tırnak içerdiği zaman çift tırnakla çevrelenmesine izin verilir. Bu özellikle SQL ifadeleri için uygundur.

```$sql = "SELECT `id`, `name` from `people` "
     . "WHERE `name`='Fred' OR `name`='Susan'";```

Değişken değişimi
---
Değişken değişimi aşağıdaki iki şekilde yapılır.
`$greeting = "Hello $name, welcome back!";`
 
`$greeting = "Hello {$name}, welcome back!";`

Tutarlılık adına aşağıdaki biçim kullanılmaz
`$greeting = "Hello ${name}, welcome back!";`

String Yapıştırma (Concatenation)
---
Diziler "." işlemcisi ile yapıştırılmalıdırlar. Okunulabilirliği arttırmak için "." karakterinin başına ve sonuna bir boşluk konmalıdır. 

$company = 'Zend' . ' ' . 'Technologies

Dizgileri "." işlemcisi ile ayırırken okunabilirliği arttırmak için ifadeleri birden fazla satıra yaymak önerilen bir davranıştır. Bu durumlarda her satır "." karakteri "=" altına gelecek şekilde boşluk karakteri ile başlamalıdır.

```$sql = "SELECT `id`, `name` FROM `people` "
     . "WHERE `name` = 'Susan' "
     . "ORDER BY `name` ASC ";```
     
     
Array'ler
===
Numerik Indeksli Array
---