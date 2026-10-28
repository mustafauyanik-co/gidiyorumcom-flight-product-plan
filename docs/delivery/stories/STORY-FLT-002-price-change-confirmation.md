# STORY-FLT-002 — Ödeme öncesi fiyat değişikliğini onaylama

- **Durum:** Taslak; SAN TSG API sözleşmesi ve ödeme akışıyla doğrulanacak.
- **İş paketi:** E3 — Fiyat doğruluğu
- **Öncelik / tahmin:** Zorunlu / 8 puan
- **Sorumlular:** Backend 1, arayüz geliştiricisi, QA
- **Başarı ölçütleri:** Fiyat değişikliği oranı, kabul/ret oranı, ödeme ve biletleme başarısı
- **Ölçüm olayları:** price_change_detected, price_change_accepted, price_change_rejected

## Problem ve kullanıcı ihtiyacı

Arama sırasında görülen fiyat veya uçuş uygunluğu ödeme öncesinde değişebilir. Kullanıcı yeni toplamı görüp açıkça karar vermeli; onaylamadığı tutar tahsil edilmemelidir.

## Kapsam

**Dahil:** Sunucu tarafında fiyat/uygunluk doğrulama; eski ve yeni toplam ile farkı gösterme; kabul/ret; teklif süresinin dolması ve tedarikçi hataları; onay kaydı; yinelenen isteklerin önlenmesi.

**Dahil değil:** Yeni ödeme sağlayıcısı, tedarikçinin desteklemediği fiyat garantisi ve kullanıcıya özel dinamik fiyatlama.

## Kabul ölçütleri

1. **Fiyat değişmedi:** Sunucu doğrulaması fiyatın değişmediğini gösterirse ödeme doğrulanmış teklif ve tutarla devam eder.
2. **Fiyat değişti:** Eski toplam, yeni toplam, para birimi ve fark kullanıcıya gösterilir. Açık onay olmadan ödeme isteği gönderilmez.
3. **Kabul:** Kullanıcı yeni fiyatı kabul ederse sunucu teklif kimliğini, onay zamanını ve kabul edilen tutarı kaydeder; ödeme bu tutarla başlar.
4. **Ret:** Kullanıcı reddeder veya geri dönerse ödeme başlamaz; yeniden arama ya da başka teklif seçme yolu sunulur.
5. **Teklif geçersiz:** Teklifin süresi dolmuşsa veya artık satın alınamıyorsa eski fiyatla ödeme yapılmaz.
6. **Doğrulama hatası:** Zaman aşımı veya tedarikçi hatasında sistem doğrulanmamış tutarla ödeme başlatmaz; kullanıcıya kontrollü hata ve tekrar deneme yolu sunar.
7. **Yinelenen istek:** Çift tıklama veya yinelenen bildirim çift ödeme/rezervasyon oluşturmamalıdır.
8. **Ölçüm:** Fiyat değişikliği ve kullanıcı kararı olayları tekil gönderilir; olaylarda yolcu, iletişim, kimlik veya kart bilgisi bulunmaz.

## İş kuralları

- İstemcideki tutar tek doğruluk kaynağı değildir; fiyat sunucu tarafında doğrulanır.
- Eski ve yeni tutar aynı para birimi ve ücret kapsamıyla karşılaştırılır.
- Onaylanan tutar ile ödeme isteği eşleşmelidir.
- Teklif referansı ve geçerlilik bilgisi işlem kaydına bağlanır.
- Zaman aşımı ve yeniden deneme kuralları SAN TSG sözleşmesiyle kararlaştırılır.

## Bağımlılıklar ve test kapsamı

E1 fiyat API'si, E4 ödeme/işlem durumları, ödeme sağlayıcısı ve olay sözlüğü. Testler fiyat değişmemesi/artması/azalması, ret, süresi dolan teklif, zaman aşımı, yinelenen istek, para birimi ve kişisel veri kontrolünü kapsamalıdır.

## Başarı ve koruyucu ölçütler

Fiyat değişikliği oranı, değişen fiyatı kabul/ret oranı ve ödeme/biletleme başarısı izlenir. **Onaysız tutarla ödeme ve çift ödeme hedefi sıfırdır.**

- [İş paketi ve yol haritası](../epics-and-roadmap.md)
- [Teknik geçiş ve riskler](../../technical/migration-and-risks.md)
- [Analitik ölçüm planı](../../analytics/measurement-plan.md)
- [Olay sözlüğü](../../analytics/event-dictionary.csv)
