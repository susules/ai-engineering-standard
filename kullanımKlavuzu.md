# Kullanım Kılavuzu

Bu kılavuz, AI Engineering Standard'ın ne olduğunu, nasıl çalıştığını ve hangi dosyanın ne işe yaradığını açıklar.

---

## Bu Sistem Ne İçin?

AI Engineering Standard, farklı AI araçlarının (Claude Code, Gemini, ChatGPT) aynı mühendislik anlayışıyla çalışmasını sağlayan araçtan bağımsız bir mühendislik rehberidir.

Amaç, bir prompt koleksiyonu oluşturmak değil; deneyimli bir yazılım mimarı ve senior mühendis gibi davranan, teknik kararları gerekçelendirebilen, zayıf kararları sorgulayabilen ve gerçek kod üretebilen bir AI Engineering System kurmaktır.

---

## Kök Dizin Dosyaları

### `AGENTS.md`
**En önemli dosya.** Tüm mühendislik standardının özet giriş noktası.

12 bölümden oluşur:
1. Kimlik ve misyon — ajanın rolü ve iletişim dili
2. Mühendislik felsefesi — temel prensipler
3. İtiraz ve anlaşmazlık — zayıf kararları nasıl sorgular
4. Değişiklik öncesi bağlam — mevcut projeyi önce anla
5. Gereksinim analizi — teknik çözümden önce iş hedefini anla
6. Mimari ve tasarım — orantılı mimari seçimi
7. Kontrollü otonomi ve onay — neyi özerk yapar, neyi onaya sunar
8. Uygulama ve değişiklik yönetimi — odaklı, küçük değişiklikler
9. Test ve doğrulama — gerçek test çalıştırma zorunluluğu
10. Kalite, güvenlik ve sert sınırlar — ihlal edilemez kurallar
11. Dokümantasyon ve kararlar — ADR ne zaman yazılır
12. Tamamlama raporu — her görev sonunda ne raporlanır

**Tüm AI araçları bu dosyayı okuyarak başlar.**

### `adapters/claude-code/CLAUDE.md`
Claude Code için ince bir yönlendirici. `AGENTS.md`'yi referans alır, Claude'a özgü davranışları açıklar. Mühendislik kurallarını tekrar etmez.

### `adapters/gemini/GEMINI.md`
Gemini CLI için ince bir yönlendirici. Aynı prensip: `AGENTS.md` canonical kaynak, bu dosya sadece Gemini'ye özgü yapılandırmayı içerir.

### `README.md`
Projenin genel tanıtımı, hedefleri, repository yapısı ve nasıl kullanılacağı.

### `CHANGELOG.md`
Versiyon geçmişi. Her sürümde ne eklendiği, değiştirildiği veya düzeltildiği burada kayıt altına alınır.

### `CONTRIBUTING.md`
Bu projeye katkı yapmak isteyenler için kurallar. Neyin buraya ait olduğunu, neyin olmadığını ve pull request sürecini açıklar.

### `LICENSE`
Apache License 2.0. Ticari kullanım dahil serbestçe kullanılabilir, patent koruması sağlar.

### `.gitignore`
Git'in takip etmemesi gereken dosyalar (OS dosyaları, editör dosyaları, build çıktıları).

---

## `docs/engineering/` — Detaylı Mühendislik Standartları

### `principles.md`
Mühendislik felsefesinin detaylı açıklaması. `AGENTS.md` bölüm 2'nin genişletilmiş hali.

Kapsadığı konular:
- Doğruluk ve basitlik
- Kohezyon, bağlantı ve sınırlar
- SOLID ve tasarım prensipleri
- Legacy sistemlerde değişiklik yönetimi
- Güvenlik, gizlilik ve veri bütünlüğü
- Performans, güvenilirlik, erişilebilirlik
- Prensiplerin pragmatik uygulaması (Required / Applicable / Not applicable / Deferred)

### `architecture-governance.md`
Mimari kararların nasıl alınacağını açıklar.

Kapsadığı konular:
- Mimari karar yöntemi (10 adım)
- Orantılılık — hangi mimari ne zaman seçilir
- Modül sınırları ve bağımlılık yönü
- Greenfield ve legacy projelerde mimari yönetim
- Mimari uygunluk ve otomatik denetim
- Mimari review çıktısı formatı

### `decision-making.md`
Kararların nasıl alındığını ve gerekçelendirildiğini açıklar.

Kapsadığı konular:
- Kanıt, varsayım, risk ve öneri ayrımı
- İtiraz protokolü — ne zaman ve nasıl itiraz edilir
- Seçenekler ve trade-off sunumu
- Belirsizlik yönetimi
- Karar sahipliği — ajan önerir, kullanıcı karar verir
- ADR ne zaman yazılır

### `quality-governance.md`
Kalite boyutları ve test stratejisi.

Kapsadığı konular:
- Kalite boyutları (doğruluk, güvenlik, performans, erişilebilirlik vb.)
- Risk bazlı test seçimi (unit, integration, contract, E2E)
- Test tasarım beklentileri
- Güvenlik ve gizlilik kalite kapısı
- Deterministik doğrulama araçları
- Tamamlama kanıtı formatı

---

## `docs/engineering/workflow/` — Çalışma Akışları

### `interaction-protocol.md`
Ajanın kullanıcıyla nasıl çalışacağını tanımlar.

- İstek türlerini nasıl sınıflandırır
- Anlama, analiz, önerme, onay, uygulama ve raporlama adımları
- Soru sorma kuralları (en fazla 5 soru, sadece bloklayan sorular)

### `architecture-mode.md`
Mimari tasarım yaparken izlenecek adımlar.

- Problem çerçeveleme → bağlam keşfi → itiraz → seçenekler → karşılaştırma → öneri → plan → onay → ADR
- Beklenen tasarım çıktısı formatı
- Yapılmaması gerekenler

### `implementation-mode.md`
Kod geliştirirken izlenecek adımlar.

- İnceleme → anlama → planlama → onay kapısı → uygulama → test → doğrulama → review → raporlama
- Legacy ve greenfield projelerde farklı davranış kuralları
- Uygulama kuralları (sır ifşa etme, destructive işlem yasağı vb.)

### `approval-policy.md`
Hangi işlemler özerk yapılır, hangileri onay gerektirir.

- Varsayılan otonomi kapsamı
- Onay istek formatı
- Kapsam değişikliği kuralları
- Onay gerektirmeyen işlemler

### `project-modes.md`
Proje yaşam döngüsüne göre ajan davranışı.

- **Greenfield**: Gereksinim analizi → ADR-0001 → kalite kapıları → ince dikey dilim
- **Legacy**: Sistemi haritalama → mevcut konvansiyonlara uyma → Deviation Register
- **Migration**: Hedef durum → ara durumlar → karakterizasyon testleri → rollback planı
- Mod özet tablosu

### `greenfield-quickstart.md`
Sıfırdan proje başlatmak için adım adım rehber.

- Gereksinim analizi soruları
- Mimari karar rehberi ve evrim tetikleyicileri
- Spring Boot, React ve Angular için minimum kalite kapıları
- İnce dikey dilim yaklaşımı
- Kaçınılması gereken yaygın hatalar

### `scenarios.md`
Ajanın davranışını test etmek için 10 senaryo.

Her senaryo için: prompt, beklenen davranış ve başarısızlık işaretleri.

- S1: Belirsiz özellik isteği (gereksinim analizi)
- S2: Mimari kısayol (itiraz)
- S3: Başarısız testi susturma (sert sınır)
- S4: Kontrol çalıştırılamıyor (dürüst raporlama)
- S5: Legacy refactor isteği (proje modu)
- S6: Aşırı mühendislik tuzağı (orantılılık)
- S7: Bug fix disiplini
- S8: Onay kapısı ile çalışmaya devam
- S9: Kabul edilen riskin hatırlanması
- S10: Dil kuralı

**Bu senaryoları her standart değişikliğinden sonra ilgili AI aracında çalıştır ve sonuçları tabloya kaydet.**

### `project-context-template.md`
Her projenin kök dizinine kopyalanacak `PROJECT_CONTEXT.md` şablonu.

Ajan her oturumda bu dosyayı okur. Proje adı, modu, stack, mimari, kalite komutları, konvansiyonlar, dokunulmaması gereken alanlar ve kabul edilen riskler burada tutulur.

---

## `docs/engineering/templates/` — Şablonlar

### `adr-template.md`
Architecture Decision Record şablonu.

Önemli, kalıcı mimari kararlar için kullanılır. Her ADR şunları içerir: bağlam, karar sürücüleri, değerlendirilen seçenekler, karar, gerekçe, sonuçlar, uygulama ve yeniden değerlendirme koşulları.

**Ne zaman ADR yazılır:** Mimari sınır, veri sahipliği, public API/event, güvenlik/uyumluluk, deployment modeli veya önemli teknoloji kararı değiştiğinde.

### `technical-design-template.md`
Teknik tasarım dokümanı şablonu.

ADR'den daha detaylı, bir özellik veya bileşenin tam tasarımı için kullanılır. Özet, hedefler, mevcut durum, gereksinimler, tasarım, veri/kontratlar, alternatifler, güvenlik, test, rollout ve riskler bölümlerini içerir.

---

## `docs/engineering/review-checklist.md`
Kod, mimari ve güvenlik review'ları için yapılandırılmış kontrol listesi.

10 alan:
1. Doğruluk
2. Mimari ve tasarım
3. Güvenlik
4. Test
5. Kod kalitesi
6. Performans ve güvenilirlik
7. API ve kontrat
8. Gözlemlenebilirlik
9. Dokümantasyon
10. Deployment ve operasyon

Her madde ✅ Pass / ⚠️ Warning / ❌ Fail / N/A olarak işaretlenir. Sonunda özet tablo ve karar bölümü bulunur.

---

## `adapters/` — AI Araç Adaptörleri

### `adapters/chatgpt-codex/CHATGPT.md`
ChatGPT ve Codex için kullanım rehberi.

Bu araçlar repository dosyalarını otomatik okuyamaz. Bu dosya şunları açıklar:
- System prompt olarak nasıl kullanılır
- İlk mesajda nasıl sağlanır
- Custom GPT nasıl kurulur
- Hangi dokümanlar hangi sırayla yüklenir
- Token kısıtlı oturumlar için minimal kernel

---

## Nasıl Kullanılır?

### Yeni bir proje başlatırken

1. Bu repository'yi projenin kök dizinine kopyala veya git submodule olarak ekle.
2. `docs/engineering/workflow/project-context-template.md` dosyasını projenin köküne `PROJECT_CONTEXT.md` olarak kopyala ve doldur.
3. Kullandığın AI aracına göre:
   - **Claude Code**: `CLAUDE.md` otomatik yüklenir, `AGENTS.md`'yi referans alır.
   - **Gemini CLI**: `GEMINI.md`'yi context dosyası olarak yapılandır.
   - **ChatGPT**: `adapters/chatgpt-codex/CHATGPT.md` talimatlarını izle.
4. `docs/engineering/workflow/greenfield-quickstart.md` adımlarını izle.

### Mevcut bir projeyi review ederken

1. `PROJECT_CONTEXT.md`'yi doldur (proje modu: legacy).
2. Ajana projeyi haritalatır, mevcut durumu raporlat.
3. `docs/engineering/review-checklist.md`'yi kullanarak review yaptır.
4. Bulunan sorunları önceliklendir, Deviation Register'a kaydet.

### Önemli bir teknik karar alırken

1. `docs/engineering/workflow/architecture-mode.md` akışını izle.
2. Karar önemliyse `docs/engineering/templates/adr-template.md` ile ADR yaz.
3. Onay gerektiren bir karar ise `docs/engineering/workflow/approval-policy.md`'yi kontrol et.

### Ajanın davranışını test ederken

1. `docs/engineering/workflow/scenarios.md` dosyasındaki senaryoları çalıştır.
2. Sonuçları dosyanın sonundaki tabloya kaydet.
3. Standart değişikliğinden sonra tüm senaryoları tekrar çalıştır.

---

## Dosya Yapısı Özeti

```
ai-engineering-standard/
│
├── AGENTS.md                          ← Canonical giriş noktası, her araç buradan başlar
├── README.md                          ← Proje tanıtımı (İngilizce)
├── kullanımKlavuzu.md                 ← Bu dosya (Türkçe)
├── CHANGELOG.md                       ← Versiyon geçmişi
├── CONTRIBUTING.md                    ← Katkı kuralları
├── LICENSE                            ← Apache 2.0
├── .gitignore
│
├── adapters/
│   ├── claude-code/
│   │   └── CLAUDE.md                 ← Claude Code adaptörü
│   ├── gemini/
│   │   └── GEMINI.md                 ← Gemini CLI adaptörü
│   └── chatgpt-codex/
│       └── CHATGPT.md                ← ChatGPT / Codex kullanım rehberi
│
├── docs/engineering/
│   ├── principles.md                  ← Mühendislik prensipleri (detaylı)
│   ├── architecture-governance.md    ← Mimari karar yöntemi
│   ├── decision-making.md            ← Karar alma ve itiraz protokolü
│   ├── quality-governance.md         ← Kalite boyutları ve test stratejisi
│   ├── review-checklist.md           ← Kod/mimari/güvenlik review listesi
│   │
│   ├── workflow/
│   │   ├── interaction-protocol.md   ← Kullanıcı-ajan çalışma ilişkisi
│   │   ├── architecture-mode.md      ← Mimari tasarım akışı
│   │   ├── implementation-mode.md    ← Kod geliştirme akışı
│   │   ├── approval-policy.md        ← Otonomi ve onay kuralları
│   │   ├── project-modes.md          ← Greenfield / Legacy / Migration
│   │   ├── greenfield-quickstart.md  ← Yeni proje başlatma rehberi
│   │   ├── scenarios.md              ← Davranış test senaryoları (S1-S10)
│   │   └── project-context-template.md ← PROJECT_CONTEXT.md şablonu
│   │
│   └── templates/
│       ├── adr-template.md           ← Architecture Decision Record şablonu
│       └── technical-design-template.md ← Teknik tasarım dokümanı şablonu
```

---

## Önemli Hatırlatma

Bir prompt veya talimat dosyası uyumu garanti edemez. Deterministik gereksinimleri repository araçlarıyla, testlerle, linter'larla, mimari testlerle, güvenlik tarayıcılarıyla ve CI ile zorla. Ajanın kendi kendini review etmesini yararlı ek bir katman olarak gör, tek kalite kapısı olarak değil.
