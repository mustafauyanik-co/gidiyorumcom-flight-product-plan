# Rapor örnekleri ve kullanım rehberi

Bu klasördeki tarih, metrik ve kararlar **örnek amaçlı kurgulanmıştır**. Gerçek raporlarda veri kaynağı ve tarih aralığı doğrulanmalı; örnek değerler kopyalanmamalıdır.

## Rapor kataloğu

| Rapor | Kullanım zamanı | Hedef kitle |
|---|---|---|
| [Haftalık durum raporu](weekly-status-report-example.md) | Haftalık proje ve yönetim toplantısı | Yönetim, ürün, geliştirme, operasyon |
| [Başarı ölçütleri raporu](kpi-dashboard-example.md) | Ürün performansı ve dönüşüm hunisi incelemesi | Ürün, analitik, pazarlama, finans |
| [Trafik artırma kararı raporu](rollout-go-no-go-example.md) | Her trafik artışı öncesi | Ürün, teknik lider, QA, operasyon, finans |

## Gerçek rapor için kontrol listesi

- [ ] Örnek değerler doğrulanmış gerçek verilerle değiştirildi.
- [ ] Dönem, saat dilimi, payda, segment ve veri kaynağı belirtildi.
- [ ] Sunucu sipariş/biletleme kayıtlarıyla analitik farkları incelendi.
- [ ] İzin oranı ve ölçüm dışında kalan trafik açıklandı.
- [ ] Her risk ve aksiyona sorumlu ve hedef tarih atandı.
- [ ] Trafik artırma kararı test kanıtı, ölçüm panosu ve açık risklere dayanıyor.
- [ ] Yolcu, ödeme veya diğer kişisel bilgiler rapora eklenmedi.

## Raporlama ilkesi

Tek bir anlık değer yerine başlangıç değeri, önceki dönem, hedef, eğilim, örneklem hacmi ve koruyucu ölçütler birlikte sunulmalıdır. Veri hacmi veya istatistiksel güven yeterli değilse sonuç kesinmiş gibi yazılmamalıdır.
