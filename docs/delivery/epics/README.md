# İş paketi kataloğu

Bu klasör, gidiyorum.com uçak bileti planındaki dokuz iş paketini (Epic) tanımlar. İş paketi bir problemi ve beklenen sonucu açıklar; altındaki kullanıcı hikâyeleri geliştirilebilir ve test edilebilir iş parçalarını oluşturur.

## İş paketleri

| ID | İş paketi | Öncelik | Belge |
|---|---|---|---|
| E1 | TourVisio bağlantısı ve tedarikçi soyutlama | Zorunlu | [E1](./E1-tourvisio-integration.md) |
| E2 | Arama, sonuç listesi ve filtreler | Zorunlu | [E2](./E2-flight-search-results-filters.md) |
| E3 | Fiyat doğruluğu ve teklif geçerliliği | Zorunlu | [E3](./E3-price-consistency-offer-validity.md) |
| E4 | Yolcu, ödeme ve biletleme | Zorunlu | [E4](./E4-passenger-payment-ticketing.md) |
| E5 | SEO sürekliliği | Zorunlu | [E5](./E5-seo-continuity.md) |
| E6 | Trafik yönlendirme, izleme ve geri dönüş | Zorunlu | [E6](./E6-feature-flags-rollout-observability.md) |
| E7 | Analitik ve başarı ölçümü | Zorunlu | [E7](./E7-analytics-funnel-experimentation.md) |
| E8 | Operasyon ve canlıya geçiş hazırlığı | Zorunlu | [E8](./E8-operations-support-launch-readiness.md) |
| E9 | Dönüşüm iyileştirmeleri | İlk sürüm sonrası | [E9](./E9-conversion-optimization.md) |

## Görev katmanı

Her Epic'in Story bazlı uygulanabilir görevleri [görev kataloğunda](../tasks/README.md) yer alır. Görevler sorumlu rol, bağımlılık, çıktı ve doğrulama koşuluyla tanımlanmıştır.

## Kullanım kuralları

- Story listeleri başlangıç iş listesidir; ekip değerlendirmesi ve bağımlılık kontrolü yapılmadan tamamlanmış iş sayılmaz.
- Story kabul ölçütleri kendi belgelerinde tutulur; aynı ayrıntılar burada tekrarlanmaz.
- Story kimlikleri benzersiz olmalıdır.
- Başarı ölçütlerinin tanımı [ürün KPI belgesindeki](../../product/overview-and-kpis.md) tanımlarla aynı olmalıdır.
- Tarihler ve tahminler, API sözleşmesi ve gerçek ekip kapasitesi doğrulanmadan kesin taahhüt değildir.

Yeni iş paketi oluştururken [iş paketi şablonunu](EPIC-TEMPLATE.md) kullanın.
