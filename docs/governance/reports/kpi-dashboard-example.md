# Örnek başarı ölçütleri raporu — Uçak bileti

> **KURGUSAL VERİ:** Değerler yalnızca rapor biçimini göstermek içindir. Gerçek karar öncesinde sunucu biletleme kayıtları ve analitik kaynaklarıyla doğrulanmalıdır.

- **Dönem:** 2–8 Kasım 2026
- **Karşılaştırma:** Önceki 7 gün
- **Kapsam:** Tüm trafik; tedarikçi, kanal ve cihaz bazında ayrıca incelenmeli
- **Kaynaklar:** Sunucu sipariş/bilet kayıtları, GA4, PostHog, Search Console
- **İzin notu:** Analitik izin oranı belirtilmeli; web analitiği ve sunucu toplamları doğrudan eşit kabul edilmemeli.

## 1. Yönetici özeti

Örnek dönemde arama hacmi hafif artarken kesilmiş biletle sonuçlanan oturum oranı yatay kalıyor. Fiyat değişikliği oranı hedefe yakın olsa da kullanıcıya gösterilen fiyat farkı ve kabul/ret sonrasındaki davranış incelenmeli. Bu örnek veriler trafik artırma kararı için yeterli değildir.

## 2. Başarı ölçütleri

| Ölçüt | Tanım | Örnek sonuç | Hedef | Yorum |
|---|---|---:|---|---|
| Arama oturumu başına kesilen bilet | Kesilen bilet / uçuş araması yapılan oturum | 0,041 | Başlangıç değerine göre %5 göreli artış | Başlangıç değeriyle karşılaştır |
| Aramadan satışa dönüşüm | Biletli arama oturumu / arama oturumu | %4,1 | %5 göreli artış | Tedarikçi ve kanal ayrıştırılmalı |
| Sonuçsuz arama | Sonuç gösterilmeyen arama / tüm aramalar | %7,3 | %8 veya altı ya da başlangıç değerinden %20 azalma | Rota ve tarih kümelerini incele |
| Arama p95 süresi | Arama başlangıcından kullanılabilir sonuca kadar 95. yüzdelik süre | 5,7 sn | 6 sn veya altı | Sunucu yanıtı ve ekran gösterimi ayrı ölçülmeli |
| Fiyat değişikliği | Fiyatı değişen doğrulanmış teklif / tüm yeniden doğrulamalar | %2,9 | %3 veya altı | Tedarikçi ve teklif örneklemini incele |
| Ödeme terk | Ödeme başlatılıp bilet kesilmeyen işlem / ödeme başlatılan işlem | %18 | Başlangıç değerinden %10 göreli azalma | Ödeme hatası ve biletleme beklemesi ayrıştırılmalı |
| Bilet iptali | İptal edilen bilet / kesilen bilet | %1,6 | Başlangıç değeri kötüleşmemeli | İptal nedeni ve havayolu kırılımı |

## 3. Veri kalitesi

- [ ] Bilet kesimi olayı sunucudaki kesin biletleme durumuyla eşleşiyor.
- [ ] Ödeme başarısı olayı doğrulanmış ödeme bildiriminden geliyor.
- [ ] Yinelenen bildirimler ve test siparişleri satış sayısını artırmıyor.
- [ ] Tarih aralığı, saat dilimi ve payda tanımı tüm kaynaklarda aynı.
- [ ] İzin oranı ve ölçüm dışında kalan trafik belirtilmiş.
- [ ] Analitik olaylarında kişisel veya kart bilgisi bulunmuyor.

## 4. Örnek segment incelemesi

| Segment | Arama p95 | Sonuçsuz arama | Dönüşüm | Aksiyon |
|---|---:|---:|---:|---|
| Mobil / iç hat | 5,9 sn | %8,4 | %3,8 | Mobil ekran ve rota kapsamını incele |
| Masaüstü / iç hat | 4,8 sn | %6,5 | %4,5 | Karşılaştırma grubu olarak izle |
| Mobil / dış hat | 6,8 sn | %9,2 | %3,0 | Tedarikçi yanıt süresi ve zaman aşımını incele |

Segmentler örnektir. Örneklem hacmi ve belirsizlik değerlendirilmeden farklar neden-sonuç ilişkisi olarak sunulmamalıdır.

## 5. Önerilen aksiyonlar

1. Fiyat değişikliği olaylarını tedarikçi ve teklif türüne göre incele.
2. Sonuçsuz aramanın yoğunlaştığı rota/tarih kombinasyonlarını çıkar.
3. Arama süresini sunucu yanıtı ve ekranda gösterim olarak ayır.
4. Ödeme terkini ödeme hatası, fiyat reddi ve biletleme beklemesi olarak ayrıştır.
5. Her aksiyona sorumlu, hedef tarih ve beklenen etki ekle.
