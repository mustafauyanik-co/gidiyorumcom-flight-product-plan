# 7. Paydaşlar ve iletişim planı

## İletişim düzeni

| Paydaş | Sıklık | Gündem ve çıktı |
|---|---|---|
| Ürün, geliştirme ve QA | Günlük 15 dakika; iki haftalık sprint toplantıları | İlerleme, engeller, test ve yayın planı |
| SAN TSG teknik ekip | Haftalık 30 dakika; kritik olayda anlık | API sözleşmesi, hata kodları, fiyat doğrulama, hız sınırı ve biletleme hizmet seviyesi |
| Müşteri hizmetleri | Haftalık; pilotta her gün kısa kontrol | Fiyat farkı, bilet durumu ve müşteri geri bildirimi |
| Operasyon | Haftalık ve her trafik artışı öncesi | Tedarikçi performansı, açık işlemler, kapasite ve devam/durdur önerisi |
| Finans | Haftalık | Tahsilat–bilet mutabakatı, iptal/iade ve komisyon |
| Pazarlama/SEO | Haftalık; lansmanda günlük izleme | Organik adresler, kampanyalar, UTM ve reklam getirisi |
| Yönetim | Haftalık tek sayfalık rapor ve karar toplantıları | Başarı ölçütleri, riskler, tarih, bütçe ve karar ihtiyacı |

## Olay önceliği ve eskalasyon

- **Seviye 1 — Kritik:** Çift tahsilat, tahsilat olduğu hâlde bilet kesilmemesi, kişisel veri sızıntısı veya geniş çaplı satış kesintisi. Derhal trafik geri alınır; teknik sorumlu ve operasyon bilgilendirilir.
- **Seviye 2 — Yüksek:** Belirli rota/tedarikçide bozulma, yüksek fiyat farkı veya artan zaman aşımı. 30 dakika içinde ilk inceleme yapılır; gerekirse trafik azaltılır.
- **Seviye 3 — Normal:** Sınırlı arayüz veya ölçüm sorunu. İş listesine alınır; temel ölçütleri etkiliyorsa önceliği yükseltilir.

Her olay için zaman çizelgesi, etki, geçici çözüm, neden ve önleyici aksiyon kaydedilir.

## Haftalık durum raporu şablonu

- **Proje / hafta:**
- **Genel durum:** Yeşil / Sarı / Kırmızı
- **Sprint hedefi:**
- **Tamamlanan işler:**
- **Gelecek hafta:**
- **Başarı ölçütleri:** aramadan satışa dönüşüm, sonuçsuz arama, arama p95, fiyat farkı, ödeme terk/biletleme başarısı, organik trafik/404.
- **Trafik dağılımı:** eski tedarikçi __% / TourVisio __%.
- **En önemli riskler:** etki — sorumlu — hedef tarih.
- **SAN TSG aksiyonları:**
- **Karar bekleyen konular:** karar — karar sahibi — son tarih.
- **Bütçe ve kapasite etkisi:**
- **Devam/durdur önerisi:**
- **Kanıtlar:** iş listesi, ölçüm panosu, olay kaydı ve karar günlüğü.

## Örnek raporlar

- [Haftalık durum raporu](reports/weekly-status-report-example.md)
- [Başarı ölçütleri raporu](reports/kpi-dashboard-example.md)
- [Trafik artırma kararı raporu](reports/rollout-go-no-go-example.md)

## Raporlama ilkeleri

- Baz çizgi, önceki dönem, hedef, trend, hacim ve koruyucu ölçütler birlikte gösterilir.
- İzin oranı ve ölçüm dışında kalan trafik belirtilir.
- Satış sayısı sunucu tarafındaki kesilmiş bilet kayıtlarıyla karşılaştırılır.
- Yeşil: ölçütler uygun; Sarı: izleme veya aksiyon gerekli; Kırmızı: trafiği geri alma ya da yönetim kararı gerekli.
