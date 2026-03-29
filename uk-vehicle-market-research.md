# Ingiltere Arac Pazari Arastirma Rehberi

Bu dokuman, Ingiltere'deki tum arac modelleri ve yaslarini kapsayan pazar arastirmasi icin veri kaynaklarini icerir.

---

## 1. Resmi Hukumet Veri Kaynaklari

### 1.1 DVLA Arac Lisans Istatistikleri (VEH Serisi)

DVLA (Driver and Vehicle Licensing Agency), Ingiltere'deki ~40 milyon lisansli araci kapsayan istatistikleri ucretsiz olarak yayinlar. Veriler CSV/ODS formatinda indirilebilir.

**Ana portal:** https://www.gov.uk/government/collections/vehicles-statistics

| Tablo Kodu | Icerik | Guncelleme |
|---|---|---|
| VEH0101 | Govde tipine gore lisansli araclar | Ucaylik |
| VEH0105 | Marka ve modele gore lisansli araclar | Yillik |
| VEH0120 | Yakit turune gore lisansli araclar | Ucaylik |
| VEH0124 | Marka/modele gore ultra dusuk emisyonlu araclar (ULEV) | Ucaylik |
| VEH0130 | Ilk kayit yilina gore araclar (yas dagilimi) | Yillik |
| VEH0131 | Araclarin ortalama yasi | Yillik |
| VEH0142 | Bolge/yerel yonetime gore lisansli araclar | Ucaylik |
| VEH0250 | Yeni kayitlar: marka, model, yakit turu | Ucaylik |
| VEH0253 | Yeni kayitlar: govde tipi ve yakit turu | Ucaylik |

**Onemli tablolar:**
- **VEH0105** — Marka/model bazinda tum lisansli araclar (en kapsamli tablo)
- **VEH0130** — Arac yas dagilimi icin temel kaynak
- **VEH0250** — Yeni arac kayitlari icin detayli veri

**Lisans:** Open Government Licence (ucretsiz, ticari kullanim dahil)

### 1.2 DfT (Ulastirma Bakanligi)

- **Transport Statistics Great Britain (TSGB):** Yillik kapsamli ulasim istatistikleri
  - https://www.gov.uk/government/collections/transport-statistics-great-britain
- **Yol Trafigi Istatistikleri (TRA serisi):** Arac turune gore kat edilen mesafeler
  - https://www.gov.uk/government/collections/road-traffic-statistics
  - Interaktif harita: https://roadtraffic.dft.gov.uk

### 1.3 data.gov.uk Acik Veri Portali

Ingiltere hukumetinin acik veri portali. "Vehicle" veya "DVLA" anahtar kelimeleriyle arama yapilabilir.

- https://www.data.gov.uk

---

## 2. Ucretsiz API'ler

### 2.1 DVLA Vehicle Enquiry Service (VES) API

Plaka numarasiyla tekil arac sorgulama. Donen veriler:
- Marka, model, renk, yakit turu
- CO2 emisyonu, motor hacmi
- Vergi durumu, MOT durumu
- Uretim yili, ilk kayit tarihi

**Erisim:**
- Portal: https://developer-portal.driver-vehicle-licensing.api.gov.uk/
- Dokumantasyon: https://developer-portal.driver-vehicle-licensing.api.gov.uk/apis/vehicle-enquiry-service/vehicle-enquiry-service-description.html
- Ucret: Ucretsiz (hiz sinirli)
- Kayit olup API anahtari alinmasi gerekir

**Sinirlamalar:**
- Tek tek arac sorgulama (toplu indirme yok)
- Yalnizca mevcut arac durumunu dondurur (gecmis sahiplik bilgisi yok)

### 2.2 DVSA MOT History API

Plaka veya V5C referansiyla MOT test gecmisini sorgulama. Donen veriler:
- Test tarihi ve sonucu (gecti/kaldi)
- Test sirasindaki kilometre
- Ariza ve uyari kalemleri
- Test merkezi bilgisi

**Erisim:**
- Dokumantasyon: https://dvsa.github.io/mot-history-api-documentation/
- Hiz siniri: Dakikada 150 istek (standart katman)

### 2.3 MOT Toplu Veri Indirme (Bulk Data)

DVSA, yillik anonimlestirilmis MOT test verilerini toplu olarak yayinlar. On milyonlarca test kaydini icerir.

**Indirme:** https://www.data.gov.uk/dataset/e3939ef8-30c7-4ca8-9c7c-ad9475cc9b2f/anonymised-mot-tests-and-results

**Icerdigi alanlar:**
- Test tarihi, sonuc, arac sinifi
- Marka, model, renk, yakit turu
- Motor hacmi, ilk kullanim tarihi
- Kilometre, ariza/uyari nedenleri

**Format:** Buyuk CSV dosyalari (multi-GB)

> **Not:** Bu veri seti, arac yasi ve marka/model bazinda kapsamli analiz icin son derece degerlidir.

---

## 3. Endustri Veri Kaynaklari

### 3.1 SMMT (Society of Motor Manufacturers and Traders)

**Ucretsiz veriler:**
- Aylik basin bultenleri: yeni arac kayit rakamlari
- Yakit turune gore dagilim (benzin/dizel/BEV/PHEV/HEV)
- En cok satan 10 model
- Pazar segmenti bazinda veriler
- https://www.smmt.co.uk/vehicle-data/car-registrations/

**Ucretli veriler:**
- Tekil marka/model bazinda detayli veri
- Bolgesel dagilim
- Tarihsel zaman serileri
- Ticari arac verileri
- Uretim/ihracat verileri

### 3.2 Diger Endustri Kaynaklari

| Kaynak | Icerik | Ucret |
|---|---|---|
| ACEA | AB geneli kayit verileri | Basin bultenleri ucretsiz, detay ucretli |
| Auto Trader | Perakende fiyat endeksleri, pazar raporlari | Ozet ucretsiz, detay ucretli |
| Cap HPI / Glass's Guide | Arac degerleme verileri | Tamamen ucretli |
| Indicata / Autorola | Ikinci el pazar analitikleri | Tamamen ucretli |

**Auto Trader basin merkezi:** https://plc.autotrader.co.uk/press-centre/

---

## 4. Web Scraping

### 4.1 Baslica Siteler

| Site | URL | Aciklama |
|---|---|---|
| Auto Trader UK | https://www.autotrader.co.uk | En buyuk UK arac pazari (~500bin ilan) |
| Motors.co.uk | https://www.motors.co.uk | Onemli ilan hacmi |
| CarGurus UK | https://www.cargurus.co.uk | Fiyat analizi ve bayi ilanlari |
| Gumtree Motors | https://www.gumtree.com/cars | Ozel ve ticari saticilar |
| heycar | https://www.heycar.co.uk | Kuratorlu bayi ilanlari |
| Cazoo | https://www.cazoo.co.uk | Online perakendeci (kendi stogu) |
| eBay Motors UK | https://www.ebay.co.uk/motors | Acik artirma ve satin al formati |
| PistonHeads | https://www.pistonheads.com | Merakli pazari, ikinci el ve klasik |

### 4.2 Elde Edilebilecek Veriler

- Ilan fiyati, marka, model, donanim
- Uretim yili, kilometre, yakit turu
- Sanziman, govde tipi, motor hacmi
- Renk, sahip sayisi
- Bayi/ozel satici ayrimi
- Konum, ilan tarihi

### 4.3 Yasal Uyarilar (UK Hukuku)

1. **Kullanim Kosullari (Terms of Service):** Buyuk sitelerin cogu (Auto Trader, CarGurus vb.) otomatik veri cekmeyi acikca yasaklar. Ihlal, sozlesme ihlali ve yasal islem riski tasir.

2. **Computer Misuse Act 1990:** Yetkili erisimi asan sekilde bir bilgisayar sistemine erismek bu yasayi ihlal edebilir. Anti-bot onlemlerini (CAPTCHA, hiz siniri) atlatmak bu riski arttirir.

3. **UK GDPR ve Data Protection Act 2018:** Cekilen veriler kisisel veri iceriyorsa (ozel satici adlari, telefon numaralari, posta kodlari), yasal bir dayanagi olmadan islenmesi UK GDPR'i ihlal eder.

4. **Telif Hakki ve Veritabani Haklari:** Copyright, Designs and Patents Act 1988 ve veritabani hakki hukumleri kapsaminda, bir veritabaninin iceriginin onemli bir kisminin cikarilmasi, site isletmecisinin sui generis veritabani hakkini ihlal edebilir.

5. **Pratik Tavsiyeler:**
   - Akademik veya kisisel kucuk olcekli arastirma icin yasal risk dusuktur ancak sifir degildir
   - Ticari kullanim icin veri lisanslama anlasmas aranmalidir
   - Her zaman resmi API'ler ve acik veriyi scraping'e tercih edin
   - robots.txt'ye uyulmasi temel bir baslangiç noktasidir

---

## 5. Hizli Referans Tablosu

| Ihtiyac | En Iyi Kaynak | Ucret |
|---|---|---|
| Marka/model bazinda arac stogu | DVLA VEH0105 | Ucretsiz |
| Arac yas dagilimi | DVLA VEH0130 | Ucretsiz |
| Araclarin ortalama yasi | DVLA VEH0131 | Ucretsiz |
| Yeni arac kayitlari (detayli) | DVLA VEH0250 | Ucretsiz |
| Aylik yeni arac kayit ozetleri | SMMT basin bultenleri | Ucretsiz |
| Tekil arac sorgulama (plaka ile) | DVLA VES API | Ucretsiz |
| MOT gecmisi (tekil) | DVSA MOT History API | Ucretsiz |
| MOT verileri (toplu analiz) | DVSA Bulk Data (data.gov.uk) | Ucretsiz |
| Yakit turune gore dagilim | DVLA VEH0120 | Ucretsiz |
| Bolgesel dagilim | DVLA VEH0142 | Ucretsiz |
| Ikinci el pazar fiyatlari | Auto Trader / scraping | Karma |
| Detayli marka/model satis verileri | SMMT abonelik | Ucretli |
| Arac degerleme | Cap HPI / Glass's | Ucretli |

---

## 6. Onerilen Baslangic Adimlar

1. **DVLA VEH serisi tablolari indirin** — Marka/model, yas dagilimi ve yakit turu icin en kapsamli ucretsiz kaynak
2. **MOT bulk verisini indirin** — Milyonlarca arac kaydi ile detayli analiz imkani
3. **DVLA VES API'ye kaydolun** — Tekil arac sorgulama icin API anahtari alin
4. **SMMT aylik bultenleri takip edin** — Guncel pazar trendleri icin
5. **Auto Trader raporlarini inceleyin** — Ikinci el pazar trendleri icin

---

*Bu dokuman Mart 2026 itibariyle hazirlanmistir. Veri kaynaklarinin erisilebilirligi ve icerigi zaman icinde degisebilir.*
