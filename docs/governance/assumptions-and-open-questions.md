# 8. Varsayımlar ve ilk hafta soruları

## Varsayımlar

1. İlk sürümde mevcut ödeme sağlayıcısı korunacak.
2. TourVisio API'si, test ortamı ve biletleme testleri için erişilebilir olacak.
3. Eski tedarikçi geçiş ve açık işlemleri tamamlama süresince kullanılabilir kalacak.
4. Mevcut SEO adresleri mümkün olduğunca korunacak; zorunlu değişiklikler bire bir 301 yönlendirmeyle yapılacak.
5. Ekip kapasitesi iki backend geliştiricisi, bir arayüz geliştiricisi, QA ve yarı zamanlı tasarımcı olarak varsayılıyor.
6. GA4, GTM ve PostHog erişimleri ve sorumluları belirlenecek.
7. Başarı hedefleri varsayımsal; başlangıç ölçümü ve sezon etkisi görüldükten sonra onaylanacak.
8. Tedarikçi karşılaştırma istekleri sözleşme ve hız sınırları açısından izinli olmalı.
9. Fiyat karşılaştırması aynı para birimi, yolcu, bagaj, vergi ve zorunlu ücret kapsamıyla yapılabilmeli.
10. Veri gizliliği, KVKK ve ticari ileti izinleri ilgili sorumlularla doğrulanacak.

## İlk hafta cevaplanacak sorular

### SAN TSG ve API

- Arama, fiyat/uygunluk doğrulama, rezervasyon ve biletleme adımları ile ilgili API uçları hangileri?
- Teklifin geçerlilik süresi nasıl bildirilir; süresi dolduğunda beklenen davranış nedir?
- Zaman aşımı, yeniden deneme, hız sınırı, eş zamanlı istek ve hizmet seviyesi koşulları nelerdir?
- Havayolu kapsamı, bagaj/ücret detayları, vergi ve para birimi alanları nasıl döner?
- Rezervasyon ve biletleme eş zamanlı mı, yoksa sonradan mı tamamlanır? Bildirim, sorgulama, tekilleştirme ve mutabakat yöntemi nedir?
- Test ortamı gerçekçi hata senaryolarını ve test biletini destekliyor mu?
- Paralel arama veya gölge karşılaştırma sözleşmeyle izinli mi?
- Eskalasyon saatleri, iletişim kişileri ve kritik olaya yanıt hedefi nedir?

### Ürün, operasyon ve finans

- Mevcut aramadan satışa dönüşüm, sonuçsuz arama, p95, fiyat farkı, ödeme terk ve iptal başlangıç değerleri nedir?
- Fiyat hangi adımlarda yeniden doğrulanıyor? Gösterilen toplam vergi, bagaj ve zorunlu ücretleri kapsıyor mu?
- Ödeme başarılı ama bilet kesilmedi durumunda mevcut kurtarma ve mutabakat süreci nedir?
- İptal/iade işlemleri tedarikçi bazında nasıl izleniyor?
- Kampanya takviminde tedarikçi kapasitesini zorlayabilecek dönemler hangileri?

### SEO, pazarlama, analitik ve hukuk

- Organik trafiğin en büyük bölümünü getiren rota/havayolu adresleri hangileri?
- Adres, canonical ve site haritası sahipliği kimde?
- GA4/GTM/PostHog olayları ne kadar güvenilir; izin banner'ı ve etiket davranışı nasıl?
- PostHog erişim, saklama, maskeleme ve yedekleme kuralları nedir?
- İYS izinleri ve kanal bazlı ticari ileti tercihleri nerede yönetiliyor?
- Uçuş karşılaştırma sitesi sözleşmeleri, fiyat güncelleme süresi ve komisyon mutabakatı nedir?

## İlk hafta tamamlanma ölçütleri

- API soru listesi, yanıt sahibi ve hedef tarihi hazır.
- Mevcut tedarikçi başlangıç ölçümü için veri kaynağı ve sorumlular belirlendi.
- SEO adres envanteri ve önemli açılış sayfaları listelendi.
- Trafik yönlendirme ve geri dönüş taslağı hazır.
- İlk sürüm kapsamı ve ekip kapasitesi gözden geçirildi.
- Risk kaydı ve canlıya geçiş karar ölçütleri onaylandı.
