# The Cycle (Döngü) | Katkı Sağlama Kılavuzu
### Thalanor Digital Civilization — Eir Platform

> Hoş geldiniz. **The Cycle**, açık kaynaklı bir oyunun çok ötesinde; Thalanor ekosisteminin felsefi proof-of-concept'i ve –0++ etik çerçevesinin yaşayan uygulamasıdır. Projeye yapacağınız her katkı, gelecekteki dijital medeniyetin kurucu sermayesidir.
>
> *Bu projeye katkı sağlamak, ZEL v1.0 lisansını ve Topluluk Anayasasını (CODE_OF_CONDUCT) peşinen kabul etmek anlamına gelir.*

---

## 🏛️ Geliştirme Hiyerarşisi: Meta-Game Olarak Kod

The Cycle'ın geliştirme süreci, oyunun kendi katman mimarisini birebir yansıtır. Bu bir tesadüf değil; Thalanor'un "sistem kendi kendini öğretir" ilkesinin somut uygulamasıdır.

**Üretici Modu (Katman 1 Simülasyonu)**
Herkes — GitHub deneyiminden bağımsız olarak — hata çözebilir, özellik kodlayabilir veya döküman yazabilir. Bu, oyunun 18-30 yaş Artisan katmanının geliştirme ortamındaki karşılığıdır. Kabul edilen her katkı, ilerideki Thalanor akıllı sözleşme hak ediş puanlamasına dahil edilir.

**İncelemeci Modu (Katman 2 Simülasyonu)**
Kalıcı ve kaliteli katkı sağlayan geliştiriciler `Reviewer` statüsüne yükselir. Gelen kodları inceler, optimize eder ve Thalanor mimari bütünlüğünü korurlar. Mirai platformundaki Gear Ratio Engine bu statüdeki katkıları 1:50 çarpanla değerlendirir.

**Çekirdek Senato (Katman 3 Simülasyonu)**
Çekirdek geliştirici ekibi, onaylanan kodları `main` branch'e entegre eder ve –0++ makro dengeleri gözetir. Kararlar BFT konsensüsüyle alınır; hiçbir birey tek başına `main`'e doğrudan push yapamaz.

---

## 🚀 Katkı Türleri

### 1. Felsefi ve Mekanik Öneriler
Kodlama bilgisi gerekmez. Oyunun ekonomik dengesi, katman geçiş senaryoları veya –0++ uyumu hakkında önerileriniz varsa:
* **Issues** sekmesini açın
* `Feature Request` şablonunu seçin
* Fikrinizi matematiksel veya oyun teorisi temeline dayandırarak açın
* –0++ etik uyumu analizi ekleyin

### 2. Hata Bildirimi
* Önce mevcut Issues listesinde aynı hatanın açılıp açılmadığını kontrol edin
* `Bug Report` şablonunu kullanın
* Reproduction steps, hata mesajı ve etkilenen Thalanor platform modülünü belirtin

### 3. Kod Katkısı

Projeye doğrudan kod eklemek için şu adımları izleyin:

```bash
# 1. Depoyu fork edin, ardından yerel ortamınıza klonlayın
git clone https://github.com/KULLANICI_ADINIZ/the-cycle.git
cd the-cycle

# 2. Anlamlı ve açıklayıcı bir şube açın
git checkout -b feature/varlık-zkp-entegrasyonu
# veya
git checkout -b fix/kirek-namespace-izolasyon

# 3. Kodunuzu yazın — standartları aşağıda

# 4. Değişikliklerinizi taahhüt edin
git commit -m "Özellik: Varlık ZKP oracle bağlantısı eklendi (#42)"

# 5. Fork'unuza yükleyin
git push origin feature/varlık-zkp-entegrasyonu

# 6. Ana depoya Pull Request açın
```

---

## 📐 Kod Standartları ve –0++ İlkeleri

### Mimari Uyum
Yazdığınız her modül, etkilediği Thalanor platformunu açıkça belgelemelidir. Hangi katmanla (Varlık, KIREK, Mirai, Agora...) etkileşime girdiği `ARCHITECTURE.md` ile tutarlı olmalıdır.

### Maksimum İzolasyon
Kullanıcı verilerini ve yaş segmentlerini ilgilendiren tüm modüller KIREK namespace izolasyonu ilkesine uygun biçimde tasarlanmalıdır. Bir katmanın verisi, başka bir katmana sızdırılamaz — bu teknik bir kural, etik bir gerekliliktir.

### Yalınlık İlkesi
Gereksiz dependency'den kaçının. Kod ne kadar yalınsa, topluluk tarafından o kadar kolay denetlenir. Büyük üçüncü parti kütüphaneler PR incelemesinde gerekçe istenebilir.

### Commit Mesajı Formatı
```
Tür: Açıklama (#Issue_No)

Tür seçenekleri:
  Özellik   → Yeni işlevsellik
  Düzeltme  → Hata çözümü
  Mimari    → Yapısal değişiklik
  Belge     → Dökümentasyon güncellemesi
  Güvenlik  → KIREK veya ZKP katmanı değişikliği
  Ekonomi   → Tokenomics / Mirai Gear Ratio değişikliği
```

### Test Zorunluluğu
Eklenen veya değiştirilen her modül için birim testleri yazılmalıdır. Özellikle ZKP, yaş geçişi ve ekonomi mekanizmalarını etkileyen değişiklikler için sınır değer (edge case) testleri zorunludur.

---

## 💎 Hak Ediş ve Thalanor Kurucu Payı

Bu aşamada yapılan tüm katkılar GitHub geçmişinde kalıcı olarak loglanır. Thalanor akıllı sözleşmeleri ve Zeus kayıt defteri devreye girdiğinde, bu depodaki katkı ağırlıkları (çözülen kritik sorunlar, onaylanan mimariler, kabul edilen PR'lar) doğrudan **Kurucu Hak Ediş Payı (Founder Tokens)** olarak katkı sahiplerinin cüzdanlarına otomatik tanımlanacaktır.

Mirai'nin Gear Ratio Engine'i bu puanlamayı şu ağırlıklarla hesaplar:

```
Kritik güvenlik düzeltmesi     → 10x çarpan
Mimari katkı (onaylı)          → 5x çarpan
Özellik geliştirme (onaylı)    → 2x çarpan
Dokümantasyon / topluluk       → 1x çarpan
```

*Emeğiniz, bu dijital medeniyetin kurucu sermayesidir.*

---

## 📚 Başlamak İçin Kaynaklar

* [README.md](./README.md) — Projeye genel bakış ve Thalanor ekosistemi
* [ARCHITECTURE.md](./ARCHITECTURE.md) — Teknik mimari ve platform entegrasyonları
* [CODE_OF_CONDUCT.md](./CODE_OF_CONDUCT.md) — Topluluk anayasası ve –0++ ilkeleri
* [LICENSE](./LICENSE) — ZEL v1.0 lisansı
* [thalanor.io](https://thalanor.io) — Thalanor Digital Civilization ana ekosistemi

---

*ZEL v1.0 lisansı altında sunulmaktadır — [LICENSE](./LICENSE)*
*Thalanor Digital Civilization · thalanor.io*
