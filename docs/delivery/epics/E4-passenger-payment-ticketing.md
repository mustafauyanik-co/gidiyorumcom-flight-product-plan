# E4 — Yolcu, ödeme ve biletleme

- **Durum:** Taslak; ödeme sağlayıcısı ve TourVisio işlem sözleşmesiyle doğrulanacak.
- **Öncelik:** Zorunlu
- **Sorumlu:** Backend 1 (ödeme/sipariş), Backend 2 (rezervasyon/biletleme), arayüz ve QA.
- **Hedef:** İlk canlı sürüm.

## Amaç ve beklenen sonuç

Yolcu bilgisinden bilet kesimine kadar her işlemin durumu güvenilir biçimde izlenmelidir. Ödeme alındığı hâlde bilet kesilmemesi, yinelenen bildirimler ve belirsiz durumlar güvenli biçimde ele alınmalıdır.

## Kapsam

- Yolcu formu doğrulama ve güvenli veri işleme.
- Mevcut ödeme sağlayıcısı.
- Sipariş, rezervasyon ve biletleme durum yönetimi.
- Callback doğrulama ve yinelenen istek koruması.
- Bekleyen/başarısız biletleme için kurtarma ve eskalasyon.
- Ödeme–rezervasyon–biletleme mutabakatı.

**Kapsam dışında:** Hassas veriyi loglamak; aynı işlem için çift ödeme/rezervasyon; bilet doğrulanmadan başarı göstermek.

## Başlangıç iş listesi

| Story | İş | Öncelik |
|---|---|---|
| STORY-BKG-001 | Yolcu bilgilerini doğrulayıp rezervasyon isteği oluşturma | Zorunlu |
| STORY-PAY-001 | Ödeme bildirimlerini doğrulama ve tekilleştirme | Zorunlu |
| STORY-TKT-001 | Biletleme durumunu izleme | Zorunlu |
| STORY-OPS-001 | Ödeme alınıp bilet bekleyen işlemi kurtarma | Zorunlu |

## Kabul ölçütleri

1. Yolcu bilgileri sunucuda doğrulanmalı; hassas bilgiler loglara veya analitik olaylarına yazılmamalı.
2. Ödeme durumu yalnızca güvenilir sağlayıcı bildirimi doğrulandıktan sonra güncellenmeli.
3. Rezervasyon ve biletleme durumları tanımlı geçiş kurallarına uymalı; bilet kesilmeden başarı mesajı gösterilmemeli.
4. Ödeme alınmış ancak bilet kesilmemiş işlem referansla bulunabilmeli; kurtarma adımları çift tahsilat/rezervasyon oluşturmamalı.
5. Ödeme, rezervasyon ve bilet kayıtları ortak işlem referansıyla karşılaştırılabilmeli; farklar raporlanmalı.

## Bağımlılıklar ve riskler

E3 fiyat onayı, ödeme sağlayıcısı belgeleri, TourVisio rezervasyon/biletleme API'si, finans ve müşteri hizmetleri yönergeleri. Belirsiz callback sırası, kesinti ve kurtarma ihtiyacı test edilmelidir.

## Başarı ölçümü

Ödeme ve biletleme başarı oranı, biletleme gecikmesi, ödeme alınıp biletlenmeyen işlem sayısı, yinelenen işlem sayısı (**hedef: 0**) ve mutabakat farkı.

## Tamamlanma koşulu

Başarılı, başarısız, bekleyen, yinelenen bildirim ve kurtarma senaryoları test edilmiş; finans/operasyon yönergeleri ve ölçüm doğrulanmış olmalı. [Yol haritası](../epics-and-roadmap.md) ve [ekip kalite kapıları](../team-and-quality.md) uygulanır.


## Story → Görevler

Bu Epic altındaki Story görevleri [Epic → Story → Görev kataloğunda](../tasks/README.md#e4-yolcu-ödeme-ve-biletleme). Görevler sprint planlamasında API sözleşmesi, bağımlılıklar ve ekip kapasitesiyle doğrulanmalıdır.
