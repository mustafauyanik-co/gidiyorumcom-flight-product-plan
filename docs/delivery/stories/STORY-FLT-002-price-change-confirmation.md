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

## Görevler

### TASK-STORY-FLT-002-01 — Fiyat doğrulama sözleşmesini teyit etme
- **Sorumlu:** Backend 1, SAN TSG
- **Bağımlılık:** E1 API sözleşmesi ve test ortamı
- **Görev:** Teklif kimliği, fiyat/uygunluk doğrulaması, geçerlilik, timeout ve sağlayıcı hata davranışlarını teyit etmek.
- **Tamamlanma ölçütü:** Doğrulanan davranışlar ve açık kalan sorular belgelenmiş; teyit edilmemiş davranış varsayılmamış.

### TASK-STORY-FLT-002-02 — Fiyatı sunucu tarafında doğrulama
- **Sorumlu:** Backend 1
- **Bağımlılık:** TASK-STORY-FLT-002-01
- **Görev:** Ödeme öncesinde teklifin fiyatını ve satın alınabilirliğini sunucuda doğrulamak; teklif referansını ve doğrulanan tutarı işlem bağlamına bağlamak.
- **Tamamlanma ölçütü:** İstemciden gelen tutar tek doğruluk kaynağı değil; doğrulama sonucu izlenebilir.

### TASK-STORY-FLT-002-03 — Fiyat farkı ve karar ekranlarını uygulama
- **Sorumlu:** Arayüz geliştiricisi, tasarım
- **Bağımlılık:** TASK-STORY-FLT-002-01; ürün onaylı durum tasarımları
- **Görev:** Fiyat aynı, arttı, azaldı, teklif geçersiz ve doğrulama hatası durumlarını; eski/yeni toplamı, para birimini ve farkı anlaşılır biçimde göstermek.
- **Tamamlanma ölçütü:** Her durum için kullanıcıya uygun eylem sunuluyor; onay gerektiren durumda ödeme henüz başlatılmıyor.

### TASK-STORY-FLT-002-04 — Açık onayı ve kabul edilen tutarı kaydetme
- **Sorumlu:** Backend 1
- **Bağımlılık:** TASK-STORY-FLT-002-02 ve TASK-STORY-FLT-002-03
- **Görev:** Kullanıcı yeni fiyatı açıkça kabul etmeden ödeme çağrısını engellemek; teklif kimliği, onay zamanı ve kabul edilen tutarı kaydetmek.
- **Tamamlanma ölçütü:** Ödeme tutarı onaylanan tutarla eşleşiyor; ret veya geri dönüşte ödeme başlamıyor.

### TASK-STORY-FLT-002-05 — Yinelenen işlem isteğini engelleme
- **Sorumlu:** Backend 1, Backend 2
- **Bağımlılık:** İşlem ve ödeme sağlayıcısı sözleşmeleri
- **Görev:** Çift tıklama ve yinelenen isteklerde idempotency/tekilleştirme uygulamak; çift ödeme veya çift rezervasyon riskini önlemek.
- **Tamamlanma ölçütü:** Aynı işlem tekrarlandığında ikinci bir ödeme/rezervasyon oluşmuyor.

### TASK-STORY-FLT-002-06 — Fiyat kararı olaylarını ölçme
- **Sorumlu:** Arayüz geliştiricisi, analitik sorumlusu
- **Bağımlılık:** Olay sözlüğü ve izin/veri minimizasyonu kuralları
- **Görev:** `price_change_detected`, `price_change_accepted` ve `price_change_rejected` olaylarını doğru adımda ve tekil göndermek.
- **Tamamlanma ölçütü:** Olaylar sözlükle uyumlu; yolcu, iletişim, kimlik veya kart bilgisi içermiyor.

### TASK-STORY-FLT-002-07 — Fiyat ve ödeme güvenliği testlerini tamamlama
- **Sorumlu:** QA
- **Bağımlılık:** TASK-STORY-FLT-002-02 ila TASK-STORY-FLT-002-06
- **Görev:** Fiyat değişmedi/arttı/azaldı, ret, süresi dolan teklif, timeout, yinelenen istek, para birimi ve ödeme tutarı eşleşmesini test etmek.
- **Tamamlanma ölçütü:** Doğrulama hatasında veya açık onay yokken ödeme çağrısı oluşmadığı test kanıtıyla doğrulanmış; çift ödeme testi geçmiş.


- [İş paketi ve yol haritası](../epics-and-roadmap.md)
- [Teknik geçiş ve riskler](../../technical/migration-and-risks.md)
- [Analitik ölçüm planı](../../analytics/measurement-plan.md)
- [Olay sözlüğü](../../analytics/event-dictionary.csv)
