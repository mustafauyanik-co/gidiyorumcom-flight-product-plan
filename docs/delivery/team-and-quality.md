# 3. Ekip, iş bölümü ve kalite kapıları

## Rol ve sorumluluklar

| Rol | Sorumluluk | Yakın çalıştığı kişiler |
|---|---|---|
| Ürün yöneticisi | Hedef, öncelik, iş listesi, KPI, kapsam ve paydaş kararları | Tüm ekip |
| Backend geliştirici 1 | TourVisio bağlantısı, arama ve fiyat doğrulama | Backend 2, QA, SAN TSG |
| Backend geliştirici 2 | Tedarikçi yönlendirme, işlem durumları, biletleme ve izleme | Backend 1, arayüz, QA |
| Arayüz geliştiricisi | Arama, sonuçlar, filtreler, yolcu/ödeme ekranları ve olay tetikleme | Tasarım, backend, QA |
| Kalite güvence (QA) | API sözleşmesi, entegrasyon, uçtan uca, regresyon ve yayın testleri | Tüm geliştiriciler |
| Tasarımcı (yarı zamanlı) | Akış, sonuç listesi, fiyat uyarısı, mobil ve hata durumları | Ürün yöneticisi, arayüz |
| Pazarlama ve SEO | Adres envanteri, arama motoru sağlığı, kampanya ve edinim ölçümü | Ürün yöneticisi, analitik |
| Operasyon ve müşteri hizmetleri | İşlem kurtarma, destek metinleri, eskalasyon ve kullanıcı geri bildirimi | Ürün, finans, SAN TSG |
| SAN TSG | API belgeleri, test ortamı, teknik destek, kapasite ve hizmet seviyesi | Backend, QA |

Backend görev paylaşımı teknik başlangıç toplantısında kesinleştirilmelidir. Tedarikçi veya API kaynaklı her blokaj için sorumlu ve hedef tarih belirlenir.

## Çalışma modeli

İki haftalık Scrum döngüsü, planlı geliştirme ve bağımlılıkları yönetmek için kullanılır. Canlı sorunlar ve destek talepleri ayrı bir Kanban akışında izlenir; acil olaylar önceliklendirilir, olağan iyileştirmeler iş listesine alınır.

- **Sprint planlama:** Hedef, öncelik ve ekip kapasitesi.
- **Günlük toplantı:** İlerleme ve engeller; en fazla 15 dakika.
- **İş listesi gözden geçirme:** Haftada 1–2 kez.
- **Teknik ve tasarım incelemesi:** Haftalık veya kritik karar öncesi.
- **Sprint değerlendirmesi:** Çalışan akış, ölçüm ve risklerin gösterimi.
- **Geriye dönük değerlendirme:** Her sprint sonunda.
- **Paydaş/tedarikçi toplantısı:** Haftalık; açık kararlar ve bağımlılıklar.
- **Canlıya geçiş değerlendirmesi:** Her trafik artışından önce.

## Bağımlılık yönetimi

1. Her iş kaleminde bağımlılık, dış ekip sorumlusu ve ihtiyaç tarihi yazılır.
2. SAN TSG soruları tek bir karar kaydında tutulur.
3. Gerçek test ortamı hazır olana kadar taklit servisle paralel geliştirme yapılabilir; sözleşme gerçek ortamda doğrulanır.
4. API sözleşmesi değişiklikleri sürümlenir ve arayüz ekibine önceden bildirilir.
5. Bir iş gününü aşan blokaj ürün yöneticisi ve teknik lidere aktarılır.
6. Sprint kapasitesinin %15–20'si entegrasyon belirsizliği ve hata düzeltmeye ayrılır; ilk sprintlerde gerçek ihtiyaca göre güncellenir.

## İşe başlama ölçütleri

Bir iş geliştirmeye alınmadan önce:
- Problem, beklenen değer ve kabul ölçütleri açıktır.
- Gerekli tasarım, API sözleşmesi ve hata durumları bellidir.
- Ölçüm etkisi, veri gizliliği ve bağımlılıklar tanımlıdır.
- Test verisi ve test ortamı hazırdır veya engel açıkça kayıtlıdır.
- İş, ekip tarafından tahmin edilebilecek büyüklüktedir.

## Tamamlanma ölçütleri

Bir iş tamamlandı sayılmadan önce:
- Kod incelenmiş ve ana dala alınmıştır.
- İlgili birim, sözleşme, entegrasyon ve uçtan uca testler geçmiştir.
- Hata, zaman aşımı, yeniden deneme ve yinelenen istek durumları ele alınmıştır.
- Analitik olayları doğrulanmış; hassas veri loglara veya ölçüm sistemlerine yazılmamıştır.
- Gerekliyse geri dönüş anahtarı, pano, alarm, SEO kontrolü ve işletim yönergesi güncellenmiştir.
- Ürün ve kalite güvence kabulü alınmıştır; açık kritik hata yoktur veya yazılı istisna kararı vardır.

## Örnek kullanıcı hikâyeleri

- [Uçuş sonuçlarını filtreleme](stories/STORY-FLT-001-flight-results-filters.md)
- [Ödeme öncesi fiyat değişikliğini onaylama](stories/STORY-FLT-002-price-change-confirmation.md)

Yeni hikâyeler için [GitHub iş talebi şablonunu](../../.github/ISSUE_TEMPLATE/product-story.md) kullanın.
