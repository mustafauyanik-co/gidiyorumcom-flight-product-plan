# E6 — Trafik yönlendirme, izleme ve geri dönüş

- **Durum:** Taslak; teknik lider ve operasyonla doğrulanacak.
- **Öncelik:** Zorunlu
- **Sorumlu:** Backend 2 + ürün yöneticisi; QA yayın testleri; operasyon nöbeti.
- **Hedef:** İlk canlı sürüm.

## Amaç ve beklenen sonuç

Yeni tedarikçiyi küçük trafik dilimleriyle açmak, ölçütleri izlemek ve sorun olduğunda yeni aramaları eski tedarikçiye güvenle döndürmek.

## Kapsam

- Sunucu tarafında trafik anahtarı ve oran yönetimi.
- Oturum/işlem boyunca sabit tedarikçi ataması.
- Hata, arama süresi ve biletleme panoları ile alarmlar.
- Geri dönüş anahtarı, yönergesi ve denemesi.
- Her trafik artışı için kanıta dayalı karar kaydı.

**Kapsam dışında:** İstemciden tedarikçi anahtarı yönetimi, açık işlem ortasında tedarikçi değiştirme ve ölçütsüz trafik artırımı.

## Başlangıç iş listesi

| Story | İş | Öncelik |
|---|---|---|
| STORY-ROL-001 | Trafiği tutarlı biçimde yeni tedarikçiye atama | Zorunlu |
| STORY-ROL-002 | Sorunda yeni trafik akışını eski tedarikçiye döndürme | Zorunlu |
| STORY-OBS-001 | Tedarikçi ve satın alma izleme panosu | Zorunlu |

## Kabul ölçütleri

1. Aynı oturum ve açık işlem boyunca tedarikçi ataması değişmemeli.
2. Trafik oranı değişiklikleri yetkili kullanıcı, zaman ve değer bilgisiyle kaydedilmeli.
3. Kritik ölçüt aşıldığında alarm doğru sorumluya ulaşmalı ve ilk müdahale yönergesini göstermeli.
4. Geri dönüş denemesinde yeni aramalar eski tedarikçiye yönlenmeli; açık siparişler kendi işlem akışında kalmalı.
5. Her aşama kararı gözlem süresi, ölçütler, kanıt ve onaylayanlarla kaydedilmeli.

## Bağımlılıklar ve riskler

E1 tedarikçi bağlantısı, E4 işlem durumları, ölçüm panosu ve nöbetçi sorumlulukları. Yanlış trafik ataması, test edilmemiş geri dönüş ve alarm gürültüsü riskleri yayın öncesi ele alınmalıdır.

## Başarı ölçümü

Tedarikçi bazında hata/p95/biletleme başarısı, trafik oranı, geri dönüş süresi ve koruyucu ölçüt ihlali sayısı.

## Tamamlanma koşulu

Trafik anahtarı, alarmlar ve geri dönüş gerçekçi test senaryosunda doğrulanmış olmalı. [Geçiş ve risk yönetimi](../../technical/migration-and-risks.md) ile birlikte değerlendirilir.
