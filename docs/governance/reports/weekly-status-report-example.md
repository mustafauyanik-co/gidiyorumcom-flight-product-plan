# Örnek haftalık durum raporu — TourVisio geçişi

> **KURGUSAL VERİ:** Tarih, metrik ve durumlar yalnızca rapor biçimini göstermek içindir; gerçek proje performansı değildir.

- **Rapor tarihi:** 6 Kasım 2026
- **Dönem:** 2–6 Kasım 2026 (1. hafta)
- **Genel durum:** Sarı — plan doğrulaması ve dış bağımlılıklar açık
- **Proje sahibi:** Ürün yöneticisi
- **Karar ihtiyacı:** SAN TSG fiyat doğrulama hizmet seviyesinin yazılı teyidi

## 1. Yönetici özeti

Keşif başladı. Mevcut dönüşüm hunisi ve SEO başlangıç ölçümü için veri kaynakları belirlendi. TourVisio fiyat doğrulama, teklif geçerliliği ve hız sınırı henüz yazılı teyit edilmediğinden tarihler planlama varsayımıdır.

## 2. Bu hafta tamamlananlar

- Mevcut tedarikçinin arama → teklif → ödeme → biletleme akışı çıkarıldı.
- Başarı ölçütleri ve olay sözlüğü için veri sahipleri belirlendi.
- SEO adres envanteri için tarama kapsamı belirlendi.
- Teknik bağımlılıklar ve geri dönüş sorumlusu taslak olarak kaydedildi.

## 3. Ölçüt ve koruyucu sınırlar

| Ölçüt | Başlangıç değeri | Bu hafta | Hedef / eşik | Durum |
|---|---:|---:|---|---|
| Aramadan satışa dönüşüm | %4,0 | %4,1 | Sonraki aşamada %5 göreli artış | İzleniyor |
| Sonuçsuz arama | %7,5 | %7,3 | %8 veya altı ya da başlangıçtan iyileşme | Uygun |
| Arama p95 süresi | 5,8 sn | 5,7 sn | 6 sn veya altı | Uygun |
| Liste–ödeme fiyat farkı | %2,8 | %2,9 | %3 veya altı | İzleniyor |
| Biletleme başarı oranı | %98,8 | %98,9 | Başlangıca göre 5 yüzde puan kötüleşme olmamalı | Uygun |
| SEO sayfası 404 oranı | %0,4 | %0,4 | Anlamlı artış olmamalı | Uygun |

Örnek değerlerdir. Her raporda hacim, tarih aralığı, izin oranı, cihaz/kanal dağılımı ve kaynak yazılmalıdır. Başlangıç ve dönem ölçümü aynı tanımı kullanmalıdır.

## 4. Trafik ve yayın durumu

- **TourVisio canlı trafik:** %0; test ortamı aşamasında.
- **Mevcut tedarikçi:** %100.
- **Karar:** Canlı pilot başlamadı. API sözleşmesi, fiyat doğrulama ve uçtan uca biletleme testleri tamamlanmalı.

## 5. Riskler ve aksiyonlar

| Risk / engel | Etki | Sorumlu | Hedef tarih | Sonraki adım |
|---|---|---|---|---|
| Fiyat doğrulama/teklif süresi belirsiz | Eski fiyatla ödeme riski | Backend 1 + SAN TSG | 10 Kasım | Alan ve hata kodu matrisi için yazılı yanıt |
| SEO adres envanteri eksik | Organik trafik kaybı | SEO | 9 Kasım | Tarama çıktısını başlangıç kaydı olarak sakla |
| Biletleme kurtarma testi tamamlanmadı | Tahsilat olup bilet kesilmemesi | Backend 2 + QA | 12 Kasım | Bekleyen/başarısız işlem testleri |

## 6. Gelecek hafta

1. SAN TSG soru listesini kapatmak veya her açık maddeye sorumlu atamak.
2. Dönüşüm hunisi, SEO ve tedarikçi başlangıç değerlerini doğrulamak.
3. Fiyat doğrulama ve biletleme durum akışını teknik incelemeye sunmak.
4. İşleri geliştirmeye hazır olma ölçütlerine göre gözden geçirmek.

## 7. Yönetimden beklenen kararlar

- Fiyat doğrulama hizmet seviyesi için tedarikçi eskalasyon sorumlusu.
- İlk iki haftada başlangıç ölçümü için analitik/finans veri sahiplerinin zamanı.
- Başlangıç ve dış bağımlılıklar doğrulanmadan kesin canlıya çıkış tarihi taahhüt edilmemesi.

## 8. İlgili belgeler

- [Ürün hedefi ve başarı ölçütleri](../../product/overview-and-kpis.md)
- [İş planı ve yol haritası](../../delivery/epics-and-roadmap.md)
- [Teknik geçiş ve riskler](../../technical/migration-and-risks.md)
- [Paydaşlar ve raporlama](../stakeholders-and-reporting.md)
