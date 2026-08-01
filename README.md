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
