# gidiyorum.com — Uçak Bileti Ürün Planı

Bu depo, gidiyorum.com uçak bileti ürününün TourVisio tedarikçisine kontrollü geçişini ve satın alma deneyiminin iyileştirilmesini planlar.

## Hedef

İlk 12 haftada arama, fiyat doğrulama, ödeme ve biletleme akışını güvenli biçimde canlıya almak. Mevcut SEO adreslerini ve organik trafiği korumak; ürün başarısını doğrulanmış bilet satışlarıyla ölçmek.

## Planı hızlıca inceleyin

- [Ürün hedefi ve başarı ölçütleri](docs/product/overview-and-kpis.md)
- [12 haftalık yol haritası ve iş kırılımı](docs/delivery/epics-and-roadmap.md)
- [9 iş paketi (Epic)](docs/delivery/epics/README.md)
- [Ekip rolleri ve kalite kapıları](docs/delivery/team-and-quality.md)
- [Örnek kullanıcı hikâyeleri](docs/delivery/stories/README.md)
- [Teknik geçiş ve riskler](docs/technical/migration-and-risks.md)
- [Akış ve mimari diyagramları](docs/architecture/diagrams.md)
- [Ölçüm planı ve olay sözlüğü](docs/analytics/measurement-plan.md) · [CSV sözlüğü](docs/analytics/event-dictionary.csv)
- [Pazarlama ve lansman planı](docs/launch/marketing-and-launch.md)
- [Paydaş iletişimi ve raporlama](docs/governance/stakeholders-and-reporting.md)
- [Rapor örnekleri](docs/governance/reports/README.md)
- [Varsayımlar ve açık sorular](docs/governance/assumptions-and-open-questions.md)

## Öncelikli riskler

1. Arama listesi ile ödeme öncesindeki toplam fiyatın farklılaşması.
2. Uçuş veya havayolu seçeneklerinin eksik gelmesi.
3. Arama süresi ve teklif geçerliliğinin kullanıcı deneyimini bozması.
4. Eski ve yeni tedarikçi birlikte çalışırken tutarsızlık oluşması.
5. Mevcut SEO adreslerinin ve organik trafiğin zarar görmesi.
6. Ödeme alındığı hâlde biletin kesilmemesi veya işlemin durumunun belirsiz kalması.

## Çalışma ilkeleri

- Fiyat ve uygunluk doğrulanmadan ödeme başlatılmaz.
- Trafik aşamalı artırılır; her artış öncesi ölçütler ve geri dönüş planı kontrol edilir.
- Her iş kaleminde beklenen değer, sorumlu, bağımlılık, kabul ölçütü ve ölçüm yöntemi görünür olur.
- Yolcu, ödeme ve diğer hassas bilgiler analitik olaylarına veya loglara yazılmaz.
- KPI hedefleri ve takvim, ilk iki haftadaki baz ölçüm ve tedarikçi doğrulaması sonrasında kesinleştirilir.

Klasörlerin amacı ve güncelleme ilkeleri için [dokümantasyon rehberine](docs/README.md) bakın.

Bu doküman 75 dakika da hazırlanmıştır.
**Hazırlanma aşamasında ChatGPT ve Codex desteği alınmıştır.**
