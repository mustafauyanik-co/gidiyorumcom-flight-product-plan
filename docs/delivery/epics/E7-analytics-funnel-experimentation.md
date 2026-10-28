# E7 — Analitik ve başarı ölçümü

- **Durum:** Taslak; ürün, analitik ve teknik ekiplerle doğrulanacak.
- **Öncelik:** Zorunlu
- **Sorumlu:** Ürün yöneticisi (ölçütler), arayüz/backend (olaylar), pazarlama (edinim), QA (veri doğrulama).
- **Hedef:** İlk canlı sürüm; deneyler ölçüm yeterliliği sonrasında.

## Amaç ve beklenen sonuç

Arama, fiyat, ödeme ve biletleme adımlarını ortak ölçütlerle izlemek; ürün kararlarını güvenilir ticari sonuçlara dayandırmak. Kesilmiş bilet sayısı sunucu kayıtlarıyla karşılaştırılabilmelidir.

## Kapsam

- Ortak olay sözlüğü ve her olayın sahibi/kaynağı.
- GA4/GTM edinim ölçümü ve PostHog ürün akışı.
- İzin durumu ve veri minimizasyonu kontrolleri.
- Yinelenen işlem/olayların önlenmesi.
- Huni panosu, veri kalite kontrolleri ve deneylere hazırlık.

**Kapsam dışında:** Veri kalitesi ve örneklem yeterliliği doğrulanmadan deney sonucu ilan etmek; yolcu, kart veya diğer hassas verileri analitik olaylarına eklemek.

## Başlangıç iş listesi

| Story | İş | Öncelik |
|---|---|---|
| STORY-ANA-001 | Arama–satın alma olaylarını uygulama | Zorunlu |
| STORY-ANA-002 | Biletleme olaylarını sunucu kayıtlarıyla karşılaştırma | Zorunlu |
| STORY-ANA-003 | KPI panosu ve veri kalite kontrolleri | Zorunlu |
| STORY-EXP-001 | Ölçüm yeterliyse kontrollü deney hazırlığı | Olursa iyi olur |

## Kabul ölçütleri

1. Her kritik olayın adı, tetikleyicisi, gerekli alanları, kaynağı, sorumlusu ve gizlilik kuralı tanımlı olmalı.
2. Test araması ve satın alma akışında olaylar doğru sırada ve tekil olarak oluşmalı.
3. Kesilmiş bilet sayısı sunucu kayıtlarıyla karşılaştırılmalı; farklar açıklanmalı.
4. İzin kuralları uygulanmalı; hassas bilgiler olaylara sızmamalı.
5. KPI panosunda tanım, payda, dönem, segment, veri kaynağı ve veri güncelliği görünmeli.

## Bağımlılıklar ve riskler

E2/E3/E4 olay üretimi, izin yönetimi, sunucu sipariş kayıtları ve GA4/GTM/PostHog erişimleri. Olay kaybı, yinelenen bildirim, farklı paydalar ve kişisel veri sızıntısı izlenmelidir.

## Başarı ölçümü

Kritik olayların testten geçme oranı, analitik ile sunucu bilet sayısı farkı, yinelenen olay oranı, huni dönüşümü ve pano güncelliği.

## Tamamlanma koşulu

Kritik olaylar ve panolar test edilmiş; veri gizliliği kontrolü ve sunucu kayıtlarıyla mutabakat tamamlanmış olmalı. [Ölçüm planı](../../analytics/measurement-plan.md) ve [olay sözlüğü](../../analytics/event-dictionary.csv) ana kaynaklardır.


## Story → Görevler

Bu Epic altındaki Story görevleri [Epic → Story → Görev kataloğunda](../tasks/README.md). Görevler sprint planlamasında API sözleşmesi, bağımlılıklar ve ekip kapasitesiyle doğrulanmalıdır.
