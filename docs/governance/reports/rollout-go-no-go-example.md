# Örnek trafik artırma kararı raporu

> **KURGUSAL RAPOR — GERÇEK CANLIYA GEÇİŞ KARARI DEĞİLDİR.** Gerçek karar, doğrulanmış ölçüm panosu, test kanıtı ve yetkili onaylarla alınmalıdır.

- **Karar aşaması:** TourVisio için %1 pilot öncesi
- **Örnek tarih:** 18 Ocak 2027
- **Karar sahipleri:** Ürün yöneticisi, teknik lider ve operasyon
- **Öneri:** **DURDUR** — fiyat doğrulama hizmet seviyesi yazılı olarak teyit edilmemiş.

## 1. Hazırlık kontrolü

| Kontrol | Örnek durum | Kanıt / açıklama | Sorumlu |
|---|---|---|---|
| Test ortamında arama → ödeme → biletleme | Geçti | Uçtan uca test raporu eklenmeli | QA |
| Fiyat değişikliğini kabul/ret | Geçti | Yeni fiyat ve onay tutarı test edildi | Arayüz + Backend 1 |
| Zaman aşımı, yeniden deneme ve tekilleştirme | Kısmen | Tedarikçi yanıt süresi sözleşmesi belirsiz | Backend 1 + SAN TSG |
| Geri dönüş provası | Geçti | Trafik anahtarı eski tedarikçiye döndü | Backend 2 + operasyon |
| Olay ölçümü ve kişisel veri kontrolü | Geçti | Test verileri incelendi | QA + ürün |
| SEO adresleri ve 404 kontrolü | Geçti | Tarama raporu eklenmeli | SEO |
| Finansal mutabakat | Bekliyor | Ödeme–bilet kayıt eşlemesi onayı gerekli | Finans |
| Tedarikçi kapasitesi ve hizmet seviyesi | Bekliyor | Yazılı onay bekleniyor | Teknik lider |

## 2. Örnek koruyucu ölçütler

| Ölçüt | Örnek değer | Eşik | Değerlendirme |
|---|---:|---|---|
| Fiyat değişikliği | %2,7 | Pilot hedefi %3 veya altı; geri dönüş eşiği %5 üzeri | Örneklem kontrol edilmeli |
| Arama p95 süresi | 5,8 sn | Geri dönüş eşiği 10 sn üzeri | Şimdilik uygun |
| Sonuçsuz arama farkı | Karşılaştırmaya göre +0,5 yüzde puan | +5 yüzde puandan kötüleşme | Şimdilik uygun |
| Biletleme başarı farkı | -0,5 yüzde puan | Başlangıç değerinden -5 yüzde puan | Şimdilik uygun |
| Kritik olay | 0 | 0 | Uygun |

## 3. Karar

**Örnek karar: DURDUR.** Teknik testlerin çoğu geçse bile fiyat doğrulama hizmet seviyesi ve finansal mutabakat onayı tamamlanmadan canlı trafik açılmamalıdır.

## 4. Devam kararı için gerekenler

1. SAN TSG fiyat doğrulama, teklif süresi, hız sınırı ve biletleme hizmet seviyesini yazılı teyit etmeli.
2. Finans ödeme–rezervasyon–bilet mutabakatını onaylamalı.
3. Açık konular kapandıktan sonra kontrol listesi güncel kanıtlarla yeniden değerlendirilmeli.
4. %1 pilot başladıktan sonra en az 24–48 saat gözlem yapılmadan %5'e geçilmemeli.
5. Kritik hata veya eşik aşımında geri dönüş sorumlusu ve iletişim zinciri hazır olmalı.

## 5. Karar kaydı

- **Karar:** Durdur (örnek)
- **Gerekçe:** Tedarikçi hizmet seviyesi ve finansal mutabakat teyidi eksik.
- **Yeniden değerlendirme:** Açık konular kapandıktan sonraki canlıya geçiş değerlendirmesi.
- **Onaylayanlar:** Ürün yöneticisi, teknik lider, operasyon ve finans.
- **Kanıtlar:** Uçtan uca test raporu, ölçüm panosu, geri dönüş provası ve SAN TSG teyidi.
