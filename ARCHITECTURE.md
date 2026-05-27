# The Cycle (Döngü) | Sistem Mimarisi ve Teknik Tasarım
### Thalanor Digital Civilization — Eir Platform

> Bu döküman, The Cycle ekosisteminin veri izolasyonu, katman geçişleri, ağ güvenliği ve makro-ekonomik devridaim mekanizmalarını açıklar. Tüm güvenlik ve kimlik katmanları Thalanor'un yerleşik platform altyapısıyla entegre çalışır.

---

## 1. Genel Mimari Şema

Sistem, geleneksel monolitik oyun sunucularının aksine **Katmanlı Mikroservisler** ve **Thalanor Merkeziyetsiz Yönetişimi (–0++ DAO)** hibrit yapısıyla çalışır.

```
+------------------------------------------------------------------------+
|              4. Katman: 51+ (Kadimler / The Legends)                   |
|   [MNEMOSYNE Arşivi — Salt Okunur / Re-Credits Pasif Gelir Havuzu]     |
+------------------------------------------------------------------------+
                         ^ (Pasif Gelir Akışı)
+------------------------------------------------------------------------+
|              3. Katman: 46-50 (Senato / The Syndicate)                 |
|   [Agora –0++ Motoru — Makro Ekonomi, Veto/Onay, BFT Konsensüsü]      |
+------------------------------------------------------------------------+
                   ^ (Onay Talepleri / Bütçe Kararları)
+------------------------------------------------------------------------+
|              2. Katman: 31-45 (Mimarlar / The Architects)              |
|   [Mirai Gear Ratio Engine — Fabrika, SDK, Altyapı Yönetimi]          |
+------------------------------------------------------------------------+
                       ^ (Araçlar / İstihdam / Quorum)
+------------------------------------------------------------------------+
|              1. Katman: 18-30 (Üreticiler / The Artisans)              |
|   [Techne Sandbox — Ham Üretim, Görev Motoru, Aktif Enerji]           |
+------------------------------------------------------------------------+
                              ^ (Kimlik Girişi)
+------------------------------------------------------------------------+
|              Temel Katman: Varlık ZKP + KIREK İmmün Sistemi            |
|   [–0NET Ağ Katmanı — Kimlik Doğrulama, Güvenlik, İzolasyon]          |
+------------------------------------------------------------------------+
```

---

## 2. Kimlik ve Yaş Doğrulama: Varlık ZKP Protokolü

The Cycle'da yaş segmentasyonu sistemin omurgasıdır. Kimlik ve yaş doğrulaması **Thalanor Varlık platformunun ZKP (Zero-Knowledge Proof) altyapısı** üzerinden gerçekleşir. Bu yapı GDPR/KVKK uyumludur.

### Çalışma Prensibi

```
Kullanıcı → e-Devlet / Biyometrik Pasaport → Varlık ZKP Oracle
                                                      ↓
                         Ana sisteme iletilen tek bilgi:
                  "User_A ∈ Segment_1 (18-30) = TRUE"
                         (Gerçek doğum tarihi asla kaydedilmez)
                                                      ↓
                    Akıllı sözleşmeye kriptografik kanıt teslimi
                    Thalanor Zeus kayıt defterine hash logu
```

### Güvenlik Garantileri

* Üst yaş grupları, alt yaş gruplarının kimlik bilgilerine **hiçbir koşulda** erişemez
* Yaş değişim olayları (doğum günü geçişleri) Varlık oracle'ı tarafından doğrulanır, kullanıcı beyanıyla değil
* ZKP kanıtları Thalanor –0NET üzerinde depolanır; merkezi sunucuda plaintext veri tutulmaz

---

## 3. Katmanlar Arası İzolasyon: KIREK İmmün Sistemi

Her yaş grubunun verileri ve işlem yetkisi KIREK'in namespace izolasyon katmanı tarafından yönetilir.

### Veri İzolasyonu (Database Partitioning)

1. Katmandaki bir üretici arama motorunu kullandığında, arka plandaki tüm sorgular otomatik olarak kendi yaş namespace'ine `SCOPE` edilir. Diğer katmanların iç operasyonları alt katmanlara **tamamen görünmezdir.**

KIREK paketleri bu izolasyon için aşağıdaki koruma düzeylerini sağlar:

```
Minimal  → Temel namespace ayırımı
Standard → Şifreli veri bölümleme + erişim logları
Advanced → Davranışsal anomali tespiti (Harmonik Profil)
Extreme  → Tam izolasyon + Silent Guardian pasif denetimi
```

### Dinamik Arayüz Değişimi (Runtime UI Scoping)

Kullanıcı bir üst katmana geçtiğinde, React/Next.js istemci motoru arayüzü **çalışma zamanında tamamen yeniden yapılandırır:**

| Önceki Katman Butonları | Sonraki Katman Panelleri |
|---|---|
| Yaz / Derle / Tasarla / Üret | Bütçe / İzleme / Lojistik / Fabrika |
| Görev Al / Teslim Et | Proje Onayla / Kaynak Ata / Ekip Kur |
| Sandbox Çalıştır | Altyapı Deploy Et / SDK Yayınla |

---

## 4. Otomatik Göç Protokolü (Auto-Migration Engine)

Kullanıcı 30, 45 veya 50 yaş sınırını geçtiği gün — doğum gününde — sistem insan müdahalesi olmaksızın otomatik veri göçü tetikler.

### Yetki Matrisinin Dönüşümü

```
Akıllı Sözleşme Olayı: AGE_TRANSITION_TRIGGERED
   │
   ├─ Eski katman Write yetkileri → İPTAL
   ├─ Yeni katman rolü (Manager / Validator) → CÜZDANA TANIMLA
   ├─ Varlık kimlik kaydı → GÜNCELLE
   └─ Zeus kayıt defteri → TRANSITION LOGU YAZ
```

### Proje Devir-Teslim Mekaniği

30 yaşını dolduran bir üreticinin tamamlanmamış projeleri sistem tarafından **dondurulur.** Kullanıcı bu projeleri 1. Katmandaki bir çırağa devretmek için akıllı sözleşmeye imza atmak zorundadır:

```
Devredilen Proje → Çırak cüzdanına akıllı sözleşme transferi
Devredilmeyen Proje → Mirai sistem havuzuna (Quorum aktivasyonuna hazır)
Süresi dolan varlıklar → Zeus arşivine salt-okunur olarak aktarılır
```

---

## 5. Ekonomik Devridaim: Mirai Gear Ratio Engine

Sistemin sürdürülebilirliği Thalanor'un Mirai platformundaki **Gear Ratio Engine** üzerinden matematiksel dengeye bağlıdır:

$$Gelir_{Emekli} = \sum (Üretim_{Genç} \times Vergi_{Makro}) \times KatkıPuanı_{Kişisel}$$

### Katman Bazlı Çarpanlar (Gear Ratio)

```
Katman 1 → Katman 2 bağlantısı:   1:10   (10 üretici = 1 mimar finansmanı)
Katman 2 → Katman 3 bağlantısı:   1:50   (50 mimar kararı = 1 senato gündemine girer)
Katman 3 → Katman 4 bağlantısı:   1:100  (100 onay → emekli havuzuna makro vergi akışı)
Sistem Geneli Olgunluk:            1:1000 (Quorum Sensing %70 eşiği aşıldığında)
```

### Quorum Sensing Aktivasyonu

Mirai'nin Quorum Sensing mekanizması, tüm katmanlardaki sinyallerin %70 eşiğini geçtiği anda ekonomik protokolleri ve makro kural değişikliklerini otomatik olarak aktive eder. Hiçbir bireysel aktör bu eşiği tek başına aşamaz.

### Hak Ediş Dağılımı

* **Üretici Finansmanı:** 18-30 yaş üreticilerin görevlerinden elde ettiği gelir, 2. Katman fabrikalarının altyapı fonlarından karşılanır
* **Altyapı Royalty:** Mimarlar, ürettikleri araçların alt katmanlarda kullanım oranıyla orantılı kalıcı akıllı sözleşme payı alır
* **Dijital Emeklilik (MNEMOSYNE / Re-Credits):** 1. ve 2. Katman işlemlerinden kesilen makro vergiler, 51+ Kadimlerinin Zeus'taki KatkıPuanı kaydıyla orantılı biçimde pasif gelir olarak dağıtılır

---

## 6. Güvenlik ve Tehdit Modeli

### Sandbox İzolasyonu (KIREK No-Exec Ortamları)

18-30 yaş grubunun çalıştırdığı simüle kodlar ve test araçları, ana sunucu ağından tamamen izole, ağ erişimi kısıtlı güvenli konteynerlerde çalışır:

```
Network Namespaces + Noexec Mounts + KIREK Behavioral Monitor
```

### Senato Güvenliği: BFT Çoklu İmza

Agora'nın –0++ yönetişim motoru üzerinde çalışan Senato mekaniklerinde, tek bir yöneticinin manipülasyon yapmasını önlemek için **Bizans Hata Toleransı (BFT)** tabanlı çoklu imzalı onay zorunludur.

```
Senato Kararı Geçerlilik Koşulu:
  Toplam Üye Sayısı = N
  Geçerli Onay Eşiği = ⌊(2N/3)⌋ + 1
  Tek aktörün maksimum etkisi < %33
```

### –0NET Ağ Güvenliği

Tüm katmanlar arası iletişim Thalanor'un –0NET P2P ağı üzerinden şifreli olarak iletilir. Merkezi bir sunucu üzerindeki tek nokta arızası (SPOF) mimarisinden kaçınılmıştır.

---

## 7. Thalanor Platform Entegrasyon Şeması

```
The Cycle
    │
    ├── Varlık ─────────────── ZKP Kimlik & Yaş Doğrulama
    ├── KIREK ──────────────── İmmün Sistem & Namespace İzolasyonu
    ├── Zeus ───────────────── Katkı Hak Ediş Kaydı & Arşiv
    ├── Techne ─────────────── Üretici Sandbox & Araç Altyapısı
    ├── Mirai ──────────────── Gear Ratio Engine & Quorum Sensing
    ├── Agora ──────────────── –0++ Yönetişim & Senato Motoru
    ├── MNEMOSYNE ──────────── Kadimler Arşivi & Re-Credits
    ├── Zenith ─────────────── Yetenek Köprüsü & Excellence Awards
    └── Eir ────────────────── Ana Platform Evi (Gaming Layer)
```

---

*Bu döküman ZEL v1.0 lisansı altında sunulmaktadır — [LICENSE](./LICENSE)*
*Thalanor Digital Civilization · thalanor.io*
