# E3 — Fiyat doğruluğu ve teklif geçerliliği

- **Durum:** Taslak; TourVisio sözleşmesi ve ödeme akışıyla doğrulanacak.
- **Öncelik:** Zorunlu
- **Sorumlu:** Backend 1/2; arayüzde onay deneyimi; QA testleri; SAN TSG bağımlılığı.
- **Hedef:** İlk canlı sürüm.

## Amaç ve beklenen sonuç

Kullanıcı ödeme öncesinde güncel toplam fiyatı ve teklif uygunluğunu görmelidir. Fiyat değişirse açık onay alınmalı; teklif doğrulanamıyorsa eski fiyatla ödeme başlatılmamalıdır.

## Kapsam

- Teklif kimliği ve geçerlilik süresi.
- Ödeme öncesi sunucu tarafında fiyat/uygunluk doğrulaması.
- Eski ve yeni toplam, para birimi ve farkın açıklanması.
- Kabul/ret kaydı, zaman aşımı ve teklif süresinin dolması.
- Fiyat değişikliği ölçümü ve işlem izleme.

**Kapsam dışında:** Tedarikçinin desteklemediği fiyat garantisi; kullanıcı onayı olmadan yeni fiyatla devam; yeni ödeme sağlayıcısı.

## Başlangıç iş listesi

| Story | İş | Öncelik |
|---|---|---|
| STORY-FLT-002 | Fiyat değişikliğini ödeme öncesi onaylatma | Zorunlu |
| STORY-PRICE-003 | Süresi dolan teklif için yeniden arama yolu | Zorunlu |
| STORY-PRICE-004 | Doğrulama hatasında ödeme akışını durdurma | Zorunlu |

## Kabul ölçütleri

1. Ödeme tutarı istemciden değil, sunucuda doğrulanmış teklif kaydından alınmalı.
2. Fiyat değişmediyse akış doğrulanmış tutarla devam etmeli.
3. Fiyat değiştiyse eski/yeni toplam, para birimi ve fark gösterilmeli; açık onay olmadan ödeme isteği gönderilmemeli.
4. Kullanıcı reddederse, teklif süresi dolarsa veya doğrulama başarısız olursa eski fiyatla ödeme yapılmamalı; yeniden arama yolu sunulmalı.
5. Onay zamanı, teklif kimliği ve kabul edilen tutar kaydedilmeli; yinelenen istekler çift ödeme veya rezervasyon oluşturmamalı.

## Bağımlılıklar ve riskler

E1 fiyat/teklif sözleşmesi, E4 işlem durumları, para birimi ve zorunlu ücret kuralları. Teklif geçerlilik süresi ve zaman aşımı bütçesi SAN TSG ile doğrulanmalıdır.

## Başarı ölçümü

Yeniden doğrulamada fiyat değişikliği oranı, kabul/ret oranı, doğrulama zaman aşımı ve onaysız tutarla ödeme sayısı (**hedef: 0**). KPI tanımları [ürün ölçüm belgesindedir](../../product/overview-and-kpis.md).

## Tamamlanma koşulu

Fiyat değişimi, ret, süresi dolan teklif, zaman aşımı ve yinelenen istek senaryoları test edilmiş olmalı. [Yol haritası](../epics-and-roadmap.md) ve [ekip kalite kapıları](../team-and-quality.md) uygulanır.
