# E8 — Operasyon ve canlıya geçiş hazırlığı

- **Durum:** Taslak; operasyon, finans ve müşteri hizmetleriyle doğrulanacak.
- **Öncelik:** Zorunlu
- **Sorumlu:** Ürün yöneticisi, operasyon ve müşteri hizmetleri.
- **Hedef:** İlk canlı sürüm.

## Amaç ve beklenen sonuç

Teknik akışa ek olarak müşteri hizmetleri, operasyon ve finans ekiplerinin fiyat farkı, ödeme ve biletleme sorunlarını doğru ve hızlı yönetmesini sağlamak.

## Kapsam

- Fiyat değişikliği ve süresi dolan teklif için hazır yanıtlar.
- Ödeme alınmış ancak bilet bekleyen/başarısız işlem için kurtarma yönergesi.
- SAN TSG iletişim ve eskalasyon zinciri.
- Ödeme–rezervasyon–biletleme mutabakatı ve istisna yönetimi.
- Ekip eğitimi, olay iletişim şablonu ve canlıya geçiş kontrol listesi.

**Kapsam dışında:** Biletleme doğrulanmadan başarı mesajı; gereğinden fazla hassas veriye erişim; yalnızca sözlü bilgiyle yürütülen destek süreci.

## Başlangıç iş listesi

| Hikâye | İş | Öncelik |
|---|---|---|
| STORY-OPS-002 | Fiyat farkı ve teklif süresi için destek yanıtları | Zorunlu |
| STORY-OPS-003 | Ödeme alınıp bilet bekleyen işlemi kurtarma yönergesi | Zorunlu |
| STORY-LCH-001 | Canlıya geçiş kontrol listesini onaylama | Zorunlu |

## Kabul ölçütleri

1. Fiyat değişikliği, teklif süresi dolması ve biletleme gecikmesi için ürün/operasyon onaylı müşteri mesajları hazır olmalı.
2. Kurtarma yönergesinde kontrol adımları, işlem sahibi, eskalasyon süresi ve müşteri iletişimi tanımlı olmalı.
3. SAN TSG iletişim kişileri, hizmet seviyesi ve anonimleştirilmiş teknik referanslar erişilebilir olmalı.
4. Finans, ödeme/rezervasyon/bilet kayıtlarını karşılaştırma yöntemini ve istisna sahibini onaylamalı.
5. Canlıya geçiş kararı test kanıtları, açık riskler, karar sahibi ve sonuçla kaydedilmeli.

## Bağımlılıklar ve riskler

E3 fiyat doğrulama, E4 işlem durumları, E6 geri dönüş planı, SAN TSG, finans ve müşteri hizmetleri katılımı. Belirsiz sahiplik ve yanlış müşteri bilgilendirmesi eğitim ve senaryo testleriyle azaltılır.

## Başarı ölçümü

Biletleme kaynaklı destek başvuruları, ilk yanıt/çözüm süresi, tekrar başvuru oranı ve hazırlık kontrol listesinin tamamlanma oranı. Doğrulanmamış bilet durumu bildirimi ve sahipsiz kritik olay hedefi sıfırdır.

## Tamamlanma koşulu

Destek ve operasyon yönergeleri onaylanmış, eğitim tamamlanmış, mutabakat yöntemi test edilmiş ve canlıya geçiş kontrol listesi kapatılmış olmalı.


## Story → Görevler

Bu Epic altındaki Story görevleri [Epic → Story → Görev kataloğunda](../tasks/README.md). Görevler sprint planlamasında API sözleşmesi, bağımlılıklar ve ekip kapasitesiyle doğrulanmalıdır.
