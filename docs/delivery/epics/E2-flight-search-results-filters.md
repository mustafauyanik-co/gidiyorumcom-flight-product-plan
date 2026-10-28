# E2 — Arama, sonuç listesi ve filtreler

- **Durum:** Taslak; ürün ve tasarım değerlendirmesiyle doğrulanacak.
- **Öncelik:** Zorunlu
- **Sorumlu:** Arayüz geliştiricisi (lider), tasarımcı, Backend 2; ürün yöneticisi kabul sahibi.
- **Hedef:** İlk canlı sürüm.

## Amaç ve beklenen sonuç

Kullanıcının uçuş arayıp sonuçları karşılaştırmasını ve uygun teklifi seçmesini sağlayan hızlı, anlaşılır ve erişilebilir bir deneyim sunmak. Yüklenme, boş sonuç ve hata durumları da açıkça yönetilmelidir.

## Kapsam

- Arama formu ve alan doğrulama.
- Sonuçların gösterimi, sıralama ve fiyat/aktarma/kalkış saati/havayolu filtreleri.
- Mobil kullanım, erişilebilirlik, yüklenme ve boş/hata durumları.
- Arama ve filtre davranışının ölçülmesi.

**Kapsam dışında:** Kişiselleştirilmiş öneriler; doğrulanmamış uçuş bulunurluğu garantisi; ürün kararı olmadan yeni filtreler.

## Başlangıç iş listesi

| Story | İş | Öncelik |
|---|---|---|
| STORY-FLT-001 | Uçuş sonuçlarını filtreleme | Zorunlu |
| STORY-FLT-003 | Yüklenme, boş sonuç ve hata durumları | Zorunlu |
| STORY-FLT-004 | Sonuçları seçilen ölçüte göre sıralama | Önemli |
| STORY-FLT-005 | Arama parametrelerini gezinmede koruma | Önemli |

## Kabul ölçütleri

1. Eksik veya geçersiz rota/tarih bilgisi tedarikçiye gönderilmeden önce kullanıcıya açıklanmalı.
2. Fiyat, para birimi, kalkış/varış, süre, aktarma ve havayolu alanları ortak veri modeliyle tutarlı gösterilmeli.
3. Farklı filtre türleri birlikte uygulanmalı; sonuç sayısı ve liste aynı filtre durumunu yansıtmalı.
4. Boş sonuç, zaman aşımı ve API hatası birbirinden ayrılmalı; uygun yeniden deneme veya filtreleri temizleme yolu sunulmalı.
5. Mobil ve masaüstü kullanım test edilmeli; analitik olayları sözlüğe uygun ve hassas veriden arındırılmış olmalı.

## Bağımlılıklar ve riskler

E1 ortak sonuç modeli, tasarım sistemi, olay sözlüğü ve mevcut SEO adresleri. Eksik uçuş alanları, ücret kapsamı farklılıkları ve büyük listelerde performans riski izlenmelidir.

## Başarı ölçümü

Sonuçsuz arama oranı, arama p95 süresi, sonuçtan teklif seçimine geçiş, filtre kullanım oranı ve arayüz hata oranı. Tanımlar [ürün ölçüm belgesindedir](../../product/overview-and-kpis.md).

## Tamamlanma koşulu

Zorunlu filtre ve hata senaryoları test edilmiş; mobil kullanım, ölçüm ve kalite kontrolleri geçmiş olmalı. [Yol haritası](../epics-and-roadmap.md) ve [ekip kalite kapıları](../team-and-quality.md) uygulanır.
