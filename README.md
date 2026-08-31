📘 HYDROSMART PRO   


⚠️ Bu kılavuzdaki tüm teknik terimler endüstriyel standartları ifade eder.
   Cihaz, akıllı karar katmanı ve güvenli PLC mimarisi ile çalışır.
   

![HYDROSMART PRO](WhatsApp%20Image%202026-03-12%20at%2021.13.44.jpeg)


# 🌿 8-ÇIKIŞLI ENDÜSTRİYEL HİDROPONİK OTOMASYON SİSTEMİ
> **Sürüm:** v2.4 Industrial | **Model:** SSR-HYDRA-8

Tebrikler! Endüstriyel standartlarda tasarlanmış, tam otomatik topraksız tarım (hidroponik) dozaj ve kontrol ünitesini satın aldınız. Bu cihaz, besin eriyiğinizi (EC) ve asit/alkali (pH) dengenizi tam otomatik olarak yönetir.

---

## 🚀 1. HIZLI BAŞLANGIÇ (TAK-ÇALIŞTIR)

1. **Güç Bağlantısı:** Cihazı 220V prize takın. İçindeki 24V master güç sistemi 1.5 saniye sonra gürültüsüz şekilde güvenle devreye girecektir.
2. **Saha Sensörlerini Bağlayın:** 
   * RS485 Modbus pH/EC prob soketini takın.
   * Güvenlik için Akış Anahtarı (Flow Switch) ve Seviye Şalterini ilgili klemenslere bağlayın.
3. **Sıvı Hortumlarını Bağlayın:** Peristaltik pompalarınıza besin (A, B, C) ve pH düşürücü/yükseltici şişelerinden gelen hortumları bağlayın.
4. **Wi-Fi Ağında Bağlanın:**
   * Cihaz ilk açıldığında kendi Wi-Fi yayınını yapar: `Ssr Fallback Hotspot` (Şifre: `73HioKPEWDHB`).
   * Telefonunuzla bağlanıp kendi Wi-Fi ağınızı seçin veya cihazın IP adresi üzerinden Home Assistant / Web Arayüzüne erişin.

---

## 🔌 2. KLEMENS VE RÖLE ÇIKIŞ HARİTASI

| Röle No | Çıkış Adı | İşlevi |
| :--- | :--- | :--- |
| **R1** | Micro Pompa (NPK-A) | A Grubu Mikro Besin Dozajlama |
| **R2** | Grow Pompa (NPK-B) | B Grubu Vejetatif Besin Dozajlama |
| **R3** | Bloom Pompa (NPK-C) | C Grubu Çiçeklenme Besini Dozajlama |
| **R4** | Asit Pompası | pH Düşürücü (Asit) Dozajlama |
| **R5** | Karıştırıcı Motor | Tank İçi Homojen Karıştırma Motoru |
| **R6** | Sulama / Sirkülasyon | Depo Sirkülasyon ve Bypass Pompası |
| **R7** | Alkali Pompası | pH Yükseltici Dozajlama |
| **R8** | Alarm & Siren | Kritik Durum Sesli/Işıklı İkaz Çıkışı |

---

## ⚙️ 3. ÇALIŞMA MODLARI HAKKINDA

Cihazınız **iki farklı çalışma mantığına** sahiptir. Arayüzden dilediğiniz zaman değiştirebilirsiniz:

### 🌱 A) Standart Mod (Zamansal Reçete Modu)
* **Nasıl Çalışır?** Sensör okumasına bağımlı olmadan, belirlediğiniz saniye/ml sürelerine göre gübre ve asit basar.
* **Ne Zaman Kullanılır?** Sensörlerin olmadığı, bakımda olduğu veya sadece zaman ayarlı sabit gübreleme istenen durumlar için **en güvenli mekanik yedek moddur.**
* **İşlem Sırası:** Micro Dozaj -> Karıştırma -> Grow Dozaj -> Karıştırma -> Bloom Dozaj -> Karıştırma -> Asit Dozaj -> Final Karıştırma -> Bitiş.

### ⚡ B) Prof Mod (Akıllı Nöbetçi Modu)
* **Nasıl Çalışır?** 7/24 Modbus sensörler üzerinden tankı sürekli izler. EC veya pH hedef değerden kaydığında **darbeli (pulse) dozajlama** yapar, karıştırır, bekler ve hedef yakalanana kadar otomatik müdahale eder.
* **Önemli Güvenlik:** Günlük maksimum dozaj süreleri aşıldığında kimyasal taşmasını önlemek için kendini otomatik korumaya alır.

---

## 🧪 4. KALİBRASYON VE POMPA TESTLERİ

Cihazınızın hassas çalışması için ilk kurulumda kalibrasyon önerilir:

### 🎯 pH Sensör Kalibrasyonu:
1. Probu **pH 7.00** kalibrasyon sıvısına batırın -> Arayüzden `pH 7.0 Kalibrasyon` butonuna basın.
2. Probu yıkayıp **pH 4.00** sıvısına batırın -> `pH 4.0 Kalibrasyon` butonuna basın.

### 🎯 EC Sensör Kalibrasyonu:
1. Probu **1413 µS/cm** sıvısına batırın -> `EC 1413 Kalibrasyon` butonuna basın.

### 💧 Pompa Debi (Flow Rate) Ölçümü:
1. Arayüzden ilgili pompanın `60sn Akış Testi` butonuna basın.
2. Pompanın 60 saniyede dereceli silindire bastığı mililitre (ml) miktarını ölçün.
3. Çıkan sonucu arayüzdeki `Pompa Debisi (ml/dk)` kutusuna girin. Cihaz artık reçete sürelerini mililitre bazında otomatik hesaplayacaktır!

---

## 🚨 5. GÜVENLİK VE ACİL DURUM

* **🔴 Acil Durdurma Butonu (Mekanik):** Panodaki fiziksel acil durum butonuna basıldığında tüm pompalar, röleler ve güç hatları **anında kesilir.**
* **🔕 Alarm Sıfırlama:** Arayüzden veya Telegram üzerinden `/stop` yazarak alarmları ve sirenleri kapatabilirsiniz.
* **🛠️ Hortum Bakım İkazı:** Cihaz peristaltik hortum çalışma sürelerini arka planda kaydeder. Hortum ömrü dolduğunda arayüzde bakım ikazı belirir. Bakım yaptıktan sonra `Sayaçları Sıfırla` butonuna basabilirsiniz.

---

## 🤖 6. TELEGRAM BOTU İLE UZAKTAN KONTROL

Cihazınızı Telegram üzerinden uzaktan izleyip yönetebilirsiniz. Bot komutları:
* `/status` - Anlık pH, EC, Sıcaklık ve Mod bilgisini gösterir.
* `/start` - Otomatik dozaj döngüsünü başlatır.
* `/stop` - Tüm pompaları ve döngüyü anında durdurur.
* `/reboot` - Kontrolcüyü uzaktan yeniden başlatır.

---

📞 **Teknik Destek ve Servis:**  
Her türlü soru ve teknik destek talebiniz için cihaz üzerindeki seri numarası ile firmamızla iletişime geçebilirsiniz.




Master SCADA Platformu; orta ve büyük ölçekli ticari seralarda su hazırlama, NPK besin ve asit dozajlama ile sulama süreçlerini tek bir merkezden yönetmek üzere geliştirilmiş otomasyon sistemidir. Modüler genişleme mimarisi sayesinde sadece gübreleme ve sulama fonksiyonlarıyla sınırlı kalmayıp; ilerleyen süreçlerde iklimlendirme, havalandırma, aydınlatma ve karbondioksit kontrolü gibi ek otomasyon modüllerinin entegre edilebileceği merkezi bir kontrol omurgası sağlar.

GELENEKSEL PLC SİSTEMLERİ İLE KARŞILAŞTIRMA VE DONANIMSAL MİMARİ

Endüstriyel tarım tesislerinde kullanılan standart PLC sistemlerine kıyasla Drelitegrow platformu şu donanımsal ve yazılımsal üstünlükleri barındırır:

Sera ortamlarında çalışan yüksek güçlü motorların ve frekans konvertörlerinin oluşturduğu elektromanyetik gürültüler, hassas analog sensör hatlarında ölçüm sapmalarına yol açabilir. Drelitegrow; pH ve EC transmitter hatlarında çift galvanik yalıtımlı güç modülleri ve izole RS485 haberleşme altyapısını donanım mimarisine doğrudan entegre ederek, sinyal parazitlerini ve ölçüm sapmalarını donanım seviyesinde minimize edecek endüstriyel izolasyon standartlarında tasarlanmıştır. (Dijital Veri)

Yerleşik SCADA ve Bilişsel İşlem Kapasitesi

Klasik PLC altyapıları yalnızca sıralı sayısal komutları yürütürken; Drelitegrow pano bünyesindeki endüstriyel sunucu üzerinde SCADA yazılımını, yerel veritabanını, görsel yapay zeka analiz servislerini ve metinden sese dönüştürme modüllerini eş zamanlı olarak çalıştırır.

Lisanssız, Güvenli ve Sıfır Port Uzaktan Erişim Mimarisi:

Uzaktan izleme ve kontrol için harici bulut servislerine veya yıllık abonelik ücretlerine ihtiyaç duymaz.

Sıfır Port (Stealth / Görünmez Düğüm) Güvenliği: Modemde dışarıya açık hiçbir port (Port 80, 443, 8123 vb.) bırakılmaz. Dışarıdan yapılan siber port taramalarında sistem tamamen görünmez ve tepkisizdir.

Askeri Düzeyde Kriptografi: Sistem çekirdeğinde modern WireGuard (ChaCha20-Poly1305) protokolü çalışır. Veri akışı uçtan uca askeri standartlarda şifrelenir.

Sürekli Nöbetçi İzleme Mimarisi

Statik zamanlı döngülerin aksine, su parametrelerini 24 saat boyunca kesintisiz analiz eder. Hedef değerlerden sapma algılandığında Sıralı Durum Makinesi algoritmasını otomatik olarak devreye alır.

Beş Yıllık Veri Saklama ve Çok Eksenli Çapraz Analiz

Klasik sistemler yalnızca anlık veriyi gösterip kısıtlı geçmiş sunabilirken; Drelitegrow, yüksek performanslı zaman serisi veritabanı altyapısı sayesinde tüm sensör verilerini 5 yıl boyunca kayıpsız saklar. Farklı yıllara ait iklim ve gübreleme verilerini anlık karşılaştırma ve korelasyon analizi yapma imkanı verir.

ÇİFT REJİMLİ ÇALIŞMA VE KİMYASAL DOZAJLAMA GÜVENLİĞİ

Sistem, saha koşullarına ve işletme tercihlerine göre iki farklı operasyonel modda çalıştırılabilir:

Prof Mod (Gerçek Zamanlı Sensör Tabanlı Otomasyon)

pH ve EC sensör verilerini canlı işler. PT100 sıcaklık sensöründen alınan veriyle Otomatik Sıcaklık Kompanzasyonu gerçekleştirerek ölçümleri 25 derece standardında normalize eder. Belirlenen hedef EC ve pH değerleri dahilinde mikro-dozajlama yürütür. Hedef değerlere ulaşıldığında sistemi Nöbetçi İzleme moduna alır.

Standart Mod (Sensörsüz Reçete ve Zaman Tabanlı Dozajlama)

Sensör kullanılmayan alanlarda, bakım periyotlarında veya sabit hacim bazlı besleme senaryolarında tercih edilir. Sistem bünyesinde 1. Hafta Adaptasyon aşamasından 10. Hafta Flush dönemine kadar tanımlanmış hazır gelişim reçeteleri yer alır. Seçilen haftaya göre NPK oranları otomatik hesaplanır ve sistem her 7 günde bir gelişim takvimini sonraki haftaya otomatik günceller.

Kimyasal Dozajlama ve Sıralı Durum Makinesi Algoritması

Gübre bileşenlerinin ve asidin aynı anda suya verilmesi sonucu oluşan kimyasal çökelme ve bağlanma risklerini ortadan kaldırmak amacıyla sıralı durum makinesi algoritması uygulanır. Besin maddeleri suya sırayla enjekte edilir, homojen karıştırma sağlanır ve kimyasal denge oluştuktan sonra pH stabilizasyon adımına geçilir.

Yapay Zeka Destekli Görsel Teşhis ve Zaman Serisi Gelişim Analizi 

Üretim alanına konumlandırılan yüksek çözünürlüklü akıllı IP kameralar aracılığıyla bitki yatakları ve kritik vana/pompa hatları periyodik olarak taranır. Sistem, yalnızca anlık fotoğrafları yorumlamakla kalmaz; 15 günlük geriye dönük yüksek çözünürlüklü görsel arşivi hafızasında tutarak zaman serisi karşılaştırmalı gelişim analizi (Temporal Delta Analysis) yürütür.

Günlük biyokütle artışını, yaprak alanı büyüme hızını ve fenolojik evreleri piksel düzeyinde kıyaslayarak; gözle görülemeyen mikroskobik zararlıların (kırmızı örümcek, akar kolonileri) geometrik yayılma hızını, kök boğulmasına bağlı gelişim duraklamalarını (stagnation), külleme/mantar başlangıçlarını, boru sızıntılarını ve nozul tıkanıklıklarını kuluçka evresindeyken erken aşamada teşhis eder.

Türkçe Sesli Anons ve Mobil Bildirim Mimarisi

Sistem, sahadaki olayları önem derecesine göre iki farklı akustik katmanda yönetir:

1. Kritik Endüstriyel Acil Durum Sireni: Kimyasal dozaj kilitlenmeleri (aşırı asit/gübre sapması), boru patlağı/su sızıntısı, pompanın susuz kuru çalışması, faz anomalisi veya sıcaklık/VPD limitlerinin aşılması durumunda; sahada yüksek desibelli Endüstriyel Acil Durum Sireni anında devreye girerek saha personelini uyarır.

2. Akıllı Teşhis ve Sesli Anons: Görsel yapay zeka tarafından bitki anomalisi veya rutin bakım ihtiyacı tespit edildiğinde; serada çalan müzik/akustik yayın otomatik olarak kısılarak duraklatılır.  Türkçe teşhis yönergeleri ve analiz raporları hoparlörlerden sesli olarak anons edilir.

Anons veya acil durum protokolü tamamlandığında müzik yayını (Çalıyorsa) kesintiye uğramadan eski ses seviyesinde devam eder; eş zamanlı olarak fotoğraflı analiz raporu ve alarmları işletmecinin cep telefonuna anlık iletilir.

Kestirimci Bakım ve Donanımsal Koruma Sistemleri

Dozaj pompalarının çalışma süreleri kaydedilerek peristaltik pompa hortumlarının kalan kullanım ömrü yüzdesel olarak izlenir. Akış Sensörü ve Depo Seviye Sensörleri ile su varlığı doğrulanarak kuru çalışma engellenir. Tıkanma veya sensör arızasında kör dozaj limitleri devreye girerek acil durum alarmı oluşturulur. Ana işlemcide kilitlenme veya voltaj anomali algılandığında sistemi güvenli moda alan bağımsız harici donanımsal Watchdog denetleyicisi entegre edilmiştir. Tüm elektronik kartlar, nem ve korozif sera atmosferine karşı Electrolube APL konformal koruyucu kaplama ile korunmaktadır. "Sistemimiz sadece serayı yönetmekle kalmaz; kendi iç sağlığını, işlemci sıcaklığını ve donanım ömrünü de sürekli denetler. Dünyanın öbür ucundaki serada bile bir anormallik olduğunda merkez ofisimize anında telemetri bildirimi düşer."

BÜTÜNLEŞİK HİBRİT EKOSİSTEM (İklim ve Dozajın Tek Merkezde Birleşmesi)

Tesisinizde Drelitegrow İklim Kontrol Sistemi de kullanılıyorsa veya her iki sistemi birlikte sipariş ettiğinizde; ikinci bir ekrana veya ikinci bir sunucuya gerek kalmaz.

Tek Master SCADA Omurgası: pH, EC, Su Sıcaklığı, Dozajlama parametreleri ile Sera Sıcaklığı, Nem, VPD, CO₂ ve Havalandırma fanları tek bir 10.1" ekranda ve tek bir arayüzde birleşir.

Çapraz Otonom Karar Senaryoları: İklim ve besleme sistemleri birbirleriyle haberleşir. Örneğin; yaz sıcağında seradaki VPD (Buhar Basıncı Açığı) kritik seviyeye ulaşıp bitki terlemesi arttığında, sistem EC hedef değerini otomatik olarak hafifçe düşürür ve sulama periyodunu öne çekerek bitki köklerinin tuz stresine girmesini otonom olarak engeller.

Entegre Proje İndirimi: İki sistemi birlikte alan işletmelerde sunucu ve ekran maliyeti düşülerek özel paket bütçelendirmesi uygulanır.

DONANIM VE YAZILIM KAPSAMI

Pano kapağına entegre 10.1 inç Dokunmatik HMI Ekran Kiosk

Endüstriyel SCADA Sunucusu 

Hikvision Akıllı IP Kamera altyapısı 

Saha hoparlör ve siren entegrasyonu (Anomali durumunda Sesli Anons) 

Mobil bildirim ve fotoğraflı analiz raporlama altyapısı

Pano ve Şebeke Koruma Altyapısı

IP65 Endüstriyel Otomasyon Panosu

EMI Şebeke Gürültü Filtresi

Dijital ayarlı Faz/Voltaj İzleme Rölesi ve Veri Hattı Yıldırım Koruma Kiti

Anakart ve İzolasyon Teknolojisi

Harici Donanımsal Bekçi Denetleyici 

Galvanik İzoleli RS485 Haberleşme Hatları

Entegre HAOSHI H-101 pH Transmitteri ve Probu

Entegre EC Transmitteri ve Probu (Otomatik Sıcaklık Kompanzasyonlu)

Akış Sensörü ve Depo Seviye Sensörleri

Kontrol ve Uzaktan Erişim

8 Adet İzole Hibrit Mosfet 24VDC 5A Kontrol Çıkışı + 5 Amper Kuru Kontak Soketli Slim Röleler 

Esnek Bütçelendirme Mimarisi

Tesis bünyesinde yerel ağ altyapısının bulunmaması, dokunmatik ekran veya yerel sunucu ihtiyacının olmaması ya da kamera izleme sisteminin talep edilmediği durumlarda, ilgili donanım bileşenleri konfigürasyondan çıkarılabilir. Çıkarılan her bileşenin birim maliyeti paket fiyatından düşülerek projeye özel bütçelendirme yapılır.

Devreye Alma, Garanti ve SLA Taahhüdü

İlk kurulum sürecinde süpervizörlük ve kurulum ücreti talep edilmez. İşletme personeline sensör kalibrasyon yöntemleri ve kullanım senaryolarını içeren teknik eğitim ücretsiz verilir. Ana otomasyon ünitesi ve elektronik donanımlar 2 Yıl; pH ve EC sensör probları 1 Yıl süreyle resmi garanti kapsamındadır. Kurulumu takip eden 1 Yıl boyunca uzaktan teknik destek hizmeti ve yazılım güncellemeleri ücretsiz sağlanır. 

Geleceğin tarım teknolojisini bugünden tesisinize entegre etmek ve otonom üretim seviyesine ulaşmak için Drelitegrow mühendislik ekibi her zaman hizmetinizdedir.

Drelitegrow Teknoloji ve Sera Otomasyon Sistemleri

Üsküdar / İstanbul
