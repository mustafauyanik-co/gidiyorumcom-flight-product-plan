# E9 — Dönüşüm iyileştirmeleri

- **Durum:** İlk canlı sürüm sonrası; ölçüm ve başlangıç değerleri doğrulanınca başlatılır.
- **Öncelik:** İlk sürüm sonrası
- **Sorumlu:** Ürün yöneticisi; arayüz, tasarım, analitik ve pazarlama desteği.

## Amaç ve beklenen sonuç

Arama, fiyat, ödeme ve ölçüm altyapısı güvenilir hâle geldikten sonra kullanıcı deneyimini ve bilet satışını ölçülebilir denemelerle iyileştirmek.

## Kapsam

- Arama formu ve mobil deneyimde sürtünme analizi.
- Filtre ve sıralama kullanımını iyileştirme.
- Rota, cihaz ve kanal bazında düşük performans teşhisi.
- Yeterli örneklem varsa kontrollü A/B denemeleri.
- Her deneme için hipotez, başarı ölçütü, koruyucu ölçüt ve karar kaydı.

**Kapsam dışında:** Fiyat/biletleme güvenliğini riske atan denemeler; yetersiz veriyle kesin sonuç iddiası; kişiselleştirme ve dinamik fiyatlamayı ilk sürüm zorunluluğu saymak.

## Başlangıç iş listesi

| Hikâye | İş | Öncelik |
|---|---|---|
| STORY-CRO-001 | Arama formu için iyileştirme hipotezi oluşturma | Önemli |
| STORY-CRO-002 | Mobil sonuç listesi ve filtreleri iyileştirme | Önemli |
| STORY-CRO-003 | Koruyucu ölçütlerle kontrollü deneme yapma | Olursa iyi olur |

## Kabul ölçütleri

1. Her iyileştirme kullanıcı problemi, hipotez, hedef ölçüt ve ilgili kullanıcı grubu ile tanımlanmalı.
2. Deneme öncesinde başlangıç değeri, örneklem yaklaşımı, ölçüm süresi ve karar kuralı belirlenmeli.
3. Fiyat doğruluğu, ödeme/biletleme ve SEO ölçütleri kabul aralığında kalmalı; kritik bozulmada deneme durdurulmalı.
4. Sonuç raporu etki büyüklüğünü, örneklem yeterliliğini ve belirsizliği göstermeli.
5. Devam etme, geri alma veya yeniden deneme kararı gerekçesiyle kaydedilmeli.

## Bağımlılıklar ve riskler

E2 arama deneyimi, E3 fiyat güvenliği, E7 ölçüm altyapısı ve yeterli trafik. Trafik karması, yetersiz örneklem ve kısa vadeli dönüşüm artarken biletleme kalitesinin bozulması özellikle izlenmelidir.

## Başarı ölçümü

Arama oturumu başına kesilmiş bilet, aramadan satışa dönüşüm, mobil dönüşüm ve teklif seçimine geçiş. Koruyucu ölçütler: fiyat farkı, biletleme başarısı, ödeme hatası, iptal ve SEO sağlığı.

## Tamamlanma koşulu

Deneme ölçüm ve kalite kontrollerinden geçmiş, sonuçlar doğru yorumlanmış ve ürün kararı kayıt altına alınmış olmalı.
