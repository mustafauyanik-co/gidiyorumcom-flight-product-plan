# 6. Pazarlama ve canlıya geçiş planı

## Yaklaşım

Canlıya geçiş yalnızca yeni arayüzü yayımlamak değildir. Fiyat doğruluğu, uçuş kapsamı, ödeme ve biletleme güvenilirliği, organik görünürlük ve pazarlama ölçümü birlikte doğrulanmalıdır. İlk pilotta reklam harcaması sınırlı tutulur; tedarikçi kapasitesi doğrulanmadan kampanya hacmi artırılmaz.

## Kanal planı

| Kanal | Yapılacaklar | Başarı ölçümü | Kontrol noktası |
|---|---|---|---|
| Organik arama (SEO) | Mevcut adresleri koru; başlık, açıklama, canonical, site haritası ve 404 kontrolü yap | Search Console tıklama/gösterim; GA4 açılış sayfası oturumları | Gereksiz adres değişikliği ve yönlendirme zincirinden kaçın |
| Arama motoru reklamları | Marka ve yüksek satın alma niyetli rota kampanyalarını küçük bütçeyle dene | UTM, bilet satışı, edinme maliyeti, reklam getirisi | Reklamdaki fiyat ile sayfadaki toplam fiyat uyumlu olmalı |
| Uçuş karşılaştırma siteleri | Fiyat ve uygunluk akışını, yönlendirme ve tıklama ölçümünü doğrula | Tıklama, kesilmiş bilet, iptal ve komisyon sonrası katkı | Güncel olmayan veya zorunlu ücretleri içermeyen fiyatı yayımlama |
| E-posta, bildirim ve SMS | Yalnızca izinli terk hatırlatma ve bilgilendirme senaryoları | Gönderim, tıklama, satış, abonelikten çıkma ve şikâyet | İYS ve kanal izinlerini ayrı kontrol et |
| Kampanya ve taksit | Koşulları açık göster; ödeme ve finans onayı al | Kampanya kullanımı, net gelir, biletleme başarısı | Toplam tutar ve uygunluk koşulları açık olmalı |
| Müşteri hizmetleri | Fiyat farkı, ödeme ve biletleme durumu için hazır yanıtlar | Temas oranı, çözüm süresi, tekrar başvuru | Teknik ve tedarikçi kaynaklı olayları ayır |

## Kampanya ölçümü

- UTM alanları: utm_source, utm_medium, utm_campaign; gerektiğinde utm_content ve utm_term. Değerler küçük harfli, kontrollü sözlükten seçilmiş olmalıdır.
- Kampanya tanımlayıcısı kişisel bilgi içermemeli; ilişkilendirme süresi analitik ve finans ekiplerince onaylanmalıdır.
- **Reklam harcaması getirisi (ROAS):** Kampanyaya atfedilen gelir / reklam harcaması. Mümkünse iptal, iade, komisyon ve değişken maliyet sonrası katkı da raporlanır.
- **Edinme maliyeti (CPA):** Kampanya harcaması / tanımı önceden belirlenmiş yeni müşteri veya sipariş sayısı.
- Kanal başarısı ödeme başlatmayla değil, kesilmiş bilet ve satış sonrası iptal/iade sonuçlarıyla değerlendirilir.
- Test siparişleri ve yinelenen bildirimler dışarıda tutulur; analitik satış sayısı sunucu sipariş kayıtlarıyla haftalık karşılaştırılır.

## Canlıya geçiş kapıları

1. Vergi ve zorunlu ücretler toplam fiyata dahil; fiyat değişikliğinde kullanıcıdan açık onay alınıyor.
2. Ödeme ve biletleme uçtan uca testleri ile geri dönüş provası başarılı.
3. SEO adresleri, canonical, site haritası ve 404 kontrolleri tamam.
4. Olay ölçümü, izin ve veri gizliliği testleri tamam.
5. Müşteri hizmetleri, operasyon ve finans yönergeleri onaylı.
6. SAN TSG kapasite, istek sınırı ve eskalasyon sürecini doğrulamış.
7. %1–%5 pilot sonuçları değerlendirilene kadar pazarlama bütçesi kontrollü.

## İlk 30 gün

- **Her gün:** Arama p95, sonuçsuz arama, fiyat değişikliği, ödeme/biletleme başarısı ve hata alarmları.
- **Her hafta:** Organik trafik ve 404, kanal dönüşümü, iptal, destek başvuruları, edinme maliyeti ve reklam getirisi.
- **7. ve 14. gün:** Trafik artırma ve pazarlama bütçesi kararı.
- **30. gün:** Öğrenimler, iyileştirme iş listesi ve sonraki altı aylık plan.
