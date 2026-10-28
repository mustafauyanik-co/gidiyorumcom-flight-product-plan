# E1 — TourVisio bağlantısı ve tedarikçi soyutlama

- **Durum:** Taslak; API sözleşmesi ve ekip değerlendirmesiyle doğrulanacak.
- **Öncelik:** Zorunlu
- **Sorumlu:** Backend 1 (lider), Backend 2; SAN TSG dış bağımlılık.
- **Hedef:** İlk canlı sürüm.

## Amaç ve beklenen sonuç

TourVisio'yu gidiyorum.com arayüzünü tedarikçiye bağımlı kılmadan entegre etmek. Eski ve yeni tedarikçi ortak bir veri modeli üzerinden çalışmalı; sorun halinde yeni aramalar güvenle eski tedarikçiye dönebilmelidir.

## Kapsam

- API, kimlik doğrulama, hata kodları, hız sınırları ve hizmet seviyesi sözleşmesini doğrulama.
- Ortak tedarikçi arayüzü ve normalize edilmiş uçuş/teklif modeli.
- Zaman aşımı, kontrollü yeniden deneme ve devre kesici davranışları.
- Test ortamı, sözleşme testleri, korelasyon kimliği ve hassas veri içermeyen loglama.

**Kapsam dışında:** Arayüzden tedarikçiye doğrudan çağrı; doğrulanmamış alanları tahmin etme; aynı satın alma işlemini iki tedarikçide oluşturma.

## Başlangıç iş listesi

| Story | İş | Öncelik |
|---|---|---|
| STORY-INT-001 | API sözleşmesi ve hata davranışlarını doğrulama | Zorunlu |
| STORY-INT-002 | Ortak model üzerinden arama sonucu alma | Zorunlu |
| STORY-INT-003 | Zaman aşımı ve yeniden deneme kuralları | Zorunlu |
| STORY-INT-004 | İstekleri korelasyon kimliğiyle izleme | Önemli |

## Kabul ölçütleri

1. API alanları, kimlik doğrulama, hata kodları, hız sınırları ve destek süreci yazılı olarak doğrulanmış; açık sorulara sorumlu ve tarih atanmış olmalı.
2. Eski ve yeni tedarikçi aynı ortak yanıt modelini üretmeli; arayüz tedarikçiye özgü alanlara doğrudan bağlanmamalı.
3. Boş sonuç, kimlik doğrulama hatası, hız sınırı, sunucu hatası ve zaman aşımı kontrollü biçimde ele alınmalı.
4. Gizli anahtarlar ve yolcu/ödeme bilgileri loglara yazılmamalı.
5. Arama isteği süresi ve hata sınıfı hassas veri olmadan izlenebilmeli.

## Bağımlılıklar ve riskler

SAN TSG test ortamı ve API belgeleri; mevcut tedarikçinin davranışı; teknik mimari kararı. Eksik sözleşme, hız sınırı ve alan farklılıkları geliştirme öncesi kayda alınmalıdır.

## Başarı ölçümü

Tedarikçi hata ve zaman aşımı oranı, arama p95 süresi, ortak modelde zorunlu alanların doluluk oranı ve entegrasyon kaynaklı olay sayısı. KPI tanımları [ürün ölçüm belgesindedir](../../product/overview-and-kpis.md).

## Tamamlanma koşulu

Zorunlu işler test edilmiş; kritik hata senaryoları, ölçüm, gizlilik kontrolleri ve ilgili belgeler tamamlanmış olmalı. [Yol haritası](../epics-and-roadmap.md) ve [ekip kalite kapıları](../team-and-quality.md) ile birlikte değerlendirilir.
