# Epic → Story → Görev kataloğu

Bu doküman, dokuz Epic altında listelenen Story'leri uygulanabilir, test edilebilir görevlere ayırır. Görevlerin burada tanımlanması tamamlandıkları anlamına gelmez; sprint öncesinde ekip tahmini, gerçek API sözleşmesi, tasarım ve kapasite doğrulanmalıdır.

**Görev standardı:** Her görev benzersiz `TASK-<STORY-ID>-NN` kimliği, sorumlu rol, bağımlılık, somut çıktı ve doğrulama koşulu taşır. Sağlayıcı sözleşmesinde doğrulanmamış davranış varsayılmaz. Hassas yolcu/ödeme verisi loglara veya analitik olaylarına yazılmaz.

## E1 — TourVisio bağlantısı ve tedarikçi soyutlama
Epic: [E1](../epics/E1-tourvisio-integration.md). Ön koşul: SAN TSG API belgeleri ve test ortamı.

### STORY-INT-001 — API sözleşmesi ve hata davranışlarını doğrulama
- **TASK-STORY-INT-001-01 | Backend 1 + SAN TSG:** Arama/fiyat/rezervasyon/biletleme uçları, kimlik doğrulama, zorunlu alanlar, ortam ve destek sürecini envanterle. **Çıktı:** Sözleşme kontrol listesi ve açık soruların sahibi.
- **TASK-STORY-INT-001-02 | Backend 1 + QA:** Hata kodu, hız sınırı, timeout, retry ve idempotency matrisi. **Çıktı:** Sağlayıcı tarafından teyit edilen ve edilmeyen davranışlar ayrılmış.
- **TASK-STORY-INT-001-03 | Backend 1:** Başarılı/başarısız örnek istek-yanıt ve güvenli test verisi hazırla. **Çıktı:** Gizli anahtar veya gerçek kişisel veri repoda yok.
- **TASK-STORY-INT-001-04 | QA:** Başarılı yanıt, boş sonuç, yetki hatası, rate limit, 5xx ve timeout sözleşme testleri. **Çıktı:** Test kanıtı kayıtlı.

### STORY-INT-002 — Ortak model üzerinden arama sonucu alma
- **TASK-STORY-INT-002-01 | Backend 1 + 2:** Ortak uçuş/teklif alanları, para birimi, süre ve aktarma anlamlarını kararlaştır. **Çıktı:** Alan eşleme belgesi.
- **TASK-STORY-INT-002-02 | Backend 1:** TourVisio bağdaştırıcısını ortak modele dönüştür. **Doğrulama:** Arayüz tedarikçiye özgü alan kullanmıyor.
- **TASK-STORY-INT-002-03 | Backend 2:** Mevcut tedarikçiyi aynı ortak modele eşle. **Doğrulama:** Desteklenmeyen alan tahmin edilmiyor.
- **TASK-STORY-INT-002-04 | QA:** İki tedarikçi için zorunlu alan, eksik veri, fiyat ve para birimi regresyon testleri.

### STORY-INT-003 — Zaman aşımı ve yeniden deneme kuralları
- **TASK-STORY-INT-003-01 | Backend 1 + teknik lider:** İşlem türüne göre timeout/retry politikası; satın alma yan etkileri ayrıca değerlendirilir.
- **TASK-STORY-INT-003-02 | Backend 1:** Sınırlı retry, timeout ve devre kesici davranışını uygula; ayarları belgele.
- **TASK-STORY-INT-003-03 | QA:** Gecikme, timeout, rate limit ve sağlayıcı kesintisi testleri; kontrolsüz tekrar yok.

### STORY-INT-004 — İstekleri korelasyon kimliğiyle izleme
- **TASK-STORY-INT-004-01 | Backend 2:** İstek/işlem boyunca korelasyon kimliği üret veya güvenli biçimde aktar.
- **TASK-STORY-INT-004-02 | Backend 2:** Süre, tedarikçi ve hata sınıfı loglarını ekle; token, yolcu ve kart bilgilerini dışarıda bırak.
- **TASK-STORY-INT-004-03 | QA:** Bir test isteğini uçtan uca izle ve log gizlilik kontrolünü doğrula.

**E1 çıkış kapısı:** Sözleşme ve ortak model doğrulanmış; kritik hata testleri ve log gizlilik kontrolleri geçmiş.

## E2 — Arama, sonuç listesi ve filtreler
Epic: [E2](../epics/E2-flight-search-results-filters.md). Ön koşul: E1 ortak model ve tasarım akışı.

### STORY-FLT-001 — Uçuş sonuçlarını filtreleme
Ayrıntılı kabul ölçütleri: [STORY-FLT-001](../stories/STORY-FLT-001-flight-results-filters.md).
- **TASK-STORY-FLT-001-01 | Ürün + tasarım:** Fiyat, aktarma, kalkış saati ve havayolu filtrelerinin kurallarını/durumlarını tanımla.
- **TASK-STORY-FLT-001-02 | Backend 2:** Filtre alanlarının ortak modeldeki anlamını ve eksik alan davranışını doğrula.
- **TASK-STORY-FLT-001-03 | Arayüz:** Filtre seçimi, çoklu seçim, tekil kaldırma ve tümünü temizlemeyi uygula. Farklı türler AND, aynı tür çoklu değer OR.
- **TASK-STORY-FLT-001-04 | Arayüz:** URL parametrelerinde filtre durumunu koru; yenileme ve geri/ileri gezinmeyi destekle; geçersiz parametreleri güvenle yok say.
- **TASK-STORY-FLT-001-05 | Arayüz + analitik:** `flight_filter_applied` olayını tekil ve kişisel verisiz gönder.
- **TASK-STORY-FLT-001-06 | QA:** Kombinasyon, sıfır sonuç, eksik alan, URL, mobil, klavye ve olay tekilleştirme testleri.

### STORY-FLT-003 — Yüklenme, boş sonuç ve hata durumları
- **TASK-STORY-FLT-003-01 | Ürün + tasarım:** Yükleniyor, boş sonuç, timeout ve teknik hata için ayrı kullanıcı durumlarını tasarla.
- **TASK-STORY-FLT-003-02 | Backend 2:** Boş sonuç ile API hatasını ayıran yanıt/hata sözleşmesini uygula.
- **TASK-STORY-FLT-003-03 | Arayüz:** Duruma uygun mesaj ve tekrar deneme/filtre temizleme eylemi sun.
- **TASK-STORY-FLT-003-04 | QA:** Boş sonuç, timeout, 4xx/5xx, tekrar deneme ve erişilebilirlik testleri.

### STORY-FLT-004 — Sonuçları seçilen ölçüte göre sıralama
- **TASK-STORY-FLT-004-01 | Ürün:** İlk sürüm sıralama seçeneklerini ve eşitlik kurallarını onayla.
- **TASK-STORY-FLT-004-02 | Arayüz + Backend 2:** Ortak model alanlarıyla tutarlı sıralamayı uygula; eksik değer uydurma.
- **TASK-STORY-FLT-004-03 | QA:** Fiyat/süre/kalkış, eşitlik, eksik alan ve filtrelerle birlikte çalışma testleri.

### STORY-FLT-005 — Arama parametrelerini gezinmede koruma
- **TASK-STORY-FLT-005-01 | Ürün + SEO + arayüz:** Rota/tarih/yolcu parametrelerini ve mevcut URL kurallarını netleştir.
- **TASK-STORY-FLT-005-02 | Arayüz:** Yenileme ve geri/ileri gezinmede arama durumunu geri yükle.
- **TASK-STORY-FLT-005-03 | QA:** Eksik/geçersiz parametre ve mevcut SEO URL regresyon testleri.

**E2 çıkış kapısı:** Arama, filtre ve hata durumları ortak modele uygun; mobil/klavye ve analitik kontrolleri geçilmiş.

## E3 — Fiyat doğruluğu ve teklif geçerliliği
Epic: [E3](../epics/E3-price-consistency-offer-validity.md). Ön koşul: E1 fiyat/teklif sözleşmesi.

### STORY-FLT-002 — Ödeme öncesi fiyat değişikliğini onaylama
Ayrıntılı kabul ölçütleri: [STORY-FLT-002](../stories/STORY-FLT-002-price-change-confirmation.md).
- **TASK-STORY-FLT-002-01 | Backend 1 + SAN TSG:** Teklif kimliği, fiyat doğrulama, geçerlilik ve timeout davranışlarını teyit et.
- **TASK-STORY-FLT-002-02 | Backend 1:** Sunucu tarafında fiyat/uygunluk kontrolü; doğrulanmış teklif ve tutarı işlem bağlamına bağla.
- **TASK-STORY-FLT-002-03 | Arayüz + tasarım:** Fiyat aynı/arttı/azaldı, ret ve hata durumlarını; eski/yeni toplam, para birimi ve farkı göster.
- **TASK-STORY-FLT-002-04 | Backend 1:** Açık onay olmadan ödeme çağrısını engelle; teklif kimliği, onay zamanı ve kabul edilen tutarı kaydet.
- **TASK-STORY-FLT-002-05 | Backend 1 + 2:** Yinelenen istekleri tekilleştir; çift ödeme/rezervasyonu engelle.
- **TASK-STORY-FLT-002-06 | Arayüz + analitik:** `price_change_detected`, `price_change_accepted`, `price_change_rejected` olaylarını tekil ve hassas verisiz gönder.
- **TASK-STORY-FLT-002-07 | QA:** Fiyat değişmedi/arttı/azaldı, ret, timeout, süresi dolan teklif, çift tıklama, para birimi ve ödeme tutarı eşleşmesi testleri.

### STORY-PRICE-003 — Süresi dolan teklif için yeniden arama yolu
- **TASK-STORY-PRICE-003-01 | Backend 1:** Sağlayıcı sözleşmesinde doğrulanan geçerlilik bilgisini sunucuda kontrol et.
- **TASK-STORY-PRICE-003-02 | Backend 1 + arayüz:** Süresi dolan teklifi ödeme dışı bırak ve yeniden arama/teklif seçme yolu sun.
- **TASK-STORY-PRICE-003-03 | QA:** Sınır zaman, gecikmiş yanıt ve eski ekrandan ödeme denemesi testleri.

### STORY-PRICE-004 — Doğrulama hatasında ödeme akışını durdurma
- **TASK-STORY-PRICE-004-01 | Backend 1:** Timeout, sağlayıcı hatası ve doğrulanamayan teklif için güvenli hata sözleşmesi.
- **TASK-STORY-PRICE-004-02 | Backend 1 + arayüz:** Doğrulanmamış tutarla ödemeyi engelle; tekrar deneme/yeniden arama yolu sun.
- **TASK-STORY-PRICE-004-03 | QA:** Her doğrulama hatasında ödeme çağrısı oluşmadığını kanıtlayan entegrasyon testleri.

**E3 çıkış kapısı:** Onaysız tutarla ödeme hedefi sıfır; fiyat/teklif hata senaryoları kanıtla doğrulanmış.

## E4 — Yolcu, ödeme ve biletleme
Epic: [E4](../epics/E4-passenger-payment-ticketing.md). Ön koşul: E3 fiyat onayı ve sağlayıcı sözleşmeleri.

### STORY-BKG-001 — Yolcu bilgilerini doğrulayıp rezervasyon isteği oluşturma
- **TASK-STORY-BKG-001-01 | Ürün + tasarım:** Yolcu formu alanları, zorunluluklar, hata metinleri ve gizlilik kuralları.
- **TASK-STORY-BKG-001-02 | Arayüz:** Form doğrulaması; hassas değerleri analitik/loglardan dışarıda tut.
- **TASK-STORY-BKG-001-03 | Backend 2:** Sunucu doğrulaması, rezervasyon isteği ve ortak işlem referansı.
- **TASK-STORY-BKG-001-04 | QA:** Eksik/geçersiz alan, tekrar gönderim, sağlayıcı hatası ve kişisel veri kontrolleri.

### STORY-PAY-001 — Ödeme bildirimlerini doğrulama ve tekilleştirme
- **TASK-STORY-PAY-001-01 | Backend 1:** Sağlayıcı callback/webhook doğrulama yöntemini belgele.
- **TASK-STORY-PAY-001-02 | Backend 1:** Bildirim doğrulaması ve izinli ödeme durum geçişleri.
- **TASK-STORY-PAY-001-03 | Backend 1 + 2:** İdempotency/tekilleştirme; tekrar callback ikinci tahsilat veya rezervasyon üretmez.
- **TASK-STORY-PAY-001-04 | QA:** Geçersiz imza, tekrar bildirim, yanlış sıra, gecikme ve tutar uyuşmazlığı testleri.

### STORY-TKT-001 — Biletleme durumunu izleme
- **TASK-STORY-TKT-001-01 | Backend 2 + SAN TSG:** Sağlayıcı biletleme durumları ve izinli geçişlerini teyit et.
- **TASK-STORY-TKT-001-02 | Backend 2:** Biletleme isteği/yanıtını ortak işlem referansına bağla.
- **TASK-STORY-TKT-001-03 | Backend 2 + arayüz:** Başarılı/bekleyen/başarısız durumu doğru göster; bilet doğrulanmadan başarı gösterme.
- **TASK-STORY-TKT-001-04 | QA:** Başarı, bekleme, başarısızlık, timeout ve yinelenen durum bildirimi testleri.

### STORY-OPS-001 — Ödeme alınıp bilet bekleyen işlemi kurtarma
- **TASK-STORY-OPS-001-01 | Backend 2 + operasyon:** Bekleyen işlemi tespit ve yaşlandırma kuralı; eşik onaylı karar olmalı.
- **TASK-STORY-OPS-001-02 | Backend 2:** İşlem referansıyla güvenli sorgulama ve kurtarma; çift işlem riski engelli.
- **TASK-STORY-OPS-001-03 | Operasyon + finans:** Manuel inceleme, mutabakat, müşteri iletişimi ve SAN TSG eskalasyon adımları.
- **TASK-STORY-OPS-001-04 | QA + operasyon:** Ödeme var/bilet yok, belirsiz durum, tekrar callback ve kurtarma sonrası mutabakat provası.

**E4 çıkış kapısı:** İşlem referanslarıyla ödeme/rezervasyon/bilet izlenebilir; yinelenen işlem hedefi sıfır ve mutabakat testi geçer.

## E5 — SEO sürekliliği
Epic: [E5](../epics/E5-seo-continuity.md). Ön koşul: Mevcut URL envanteri ve Search Console erişimi.

### STORY-SEO-001 — Mevcut uçuş sayfası adreslerini koruma
- **TASK-STORY-SEO-001-01 | SEO:** URL, durum kodu, canonical, başlık, indeksleme ve organik performans başlangıç envanteri.
- **TASK-STORY-SEO-001-02 | SEO + arayüz:** Korunacak adresler ve parametre kuralları; değişiklik gerekçeleri/sahipleri kayıtlı.
- **TASK-STORY-SEO-001-03 | QA + SEO:** Kritik açılış sayfaları ve URL örnekleri regresyon testi.

### STORY-SEO-002 — Zorunlu değişiklikleri bire bir yönlendirme
- **TASK-STORY-SEO-002-01 | SEO:** Eski URL → eşdeğer hedef URL listesi; eşdeğer olmayan toplu yönlendirme yok.
- **TASK-STORY-SEO-002-02 | Teknik ekip:** Gerekli 301 yönlendirmeleri tek adımda uygula; döngü/zincir oluşturma.
- **TASK-STORY-SEO-002-03 | QA + SEO:** Hedef, durum kodu, yönlendirme zinciri ve 404 taraması.

### STORY-SEO-003 — Yayın öncesi teknik SEO kontrolü
- **TASK-STORY-SEO-003-01 | SEO + arayüz:** Title/description, canonical, robots/noindex ve site haritası kontrol listesi.
- **TASK-STORY-SEO-003-02 | QA:** Yayın adayı crawl; kritik 404, yanlış noindex ve canonical hataları.
- **TASK-STORY-SEO-003-03 | SEO:** İstisnalar için yazılı kabul; yayın sonrası Search Console/organik trend izleme planı.

**E5 çıkış kapısı:** Kritik URL'ler erişilebilir; yönlendirmeler tek adım ve eşdeğer; istisnalar yazılı onaylı.

## E6 — Trafik yönlendirme, izleme ve geri dönüş
Epic: [E6](../epics/E6-feature-flags-rollout-observability.md). Ön koşul: E1 entegrasyonu, E4 işlem güvenliği ve E7 ölçüm.

### STORY-ROL-001 — Trafiği tutarlı biçimde yeni tedarikçiye atama
- **TASK-STORY-ROL-001-01 | Backend 2 + teknik lider:** Trafik oranı, atama anahtarı, yetki ve varsayılan davranış kararı.
- **TASK-STORY-ROL-001-02 | Backend 2:** Sunucu tarafı özellik anahtarı/oran yönetimi; istemci sağlayıcıyı seçemez.
- **TASK-STORY-ROL-001-03 | Backend 2:** Oturum/açık işlem boyunca sabit atama ve ayar değişikliği denetim kaydı.
- **TASK-STORY-ROL-001-04 | QA:** %0/%1/%5 sınırları, atama tutarlılığı ve ayar değişikliği testleri.

### STORY-ROL-002 — Sorunda yeni trafik akışını eski tedarikçiye döndürme
- **TASK-STORY-ROL-002-01 | Backend 2 + operasyon:** Geri dönüş tetikleyicisi, karar yetkilisi ve iletişim adımları.
- **TASK-STORY-ROL-002-02 | Backend 2:** Yeni aramalar için geri dönüş anahtarı; açık siparişler mevcut işlem akışında kalır.
- **TASK-STORY-ROL-002-03 | QA + operasyon:** Geri dönüş provası, süre ölçümü ve açık sipariş güvenliği kanıtı.

### STORY-OBS-001 — Tedarikçi ve satın alma izleme panosu
- **TASK-STORY-OBS-001-01 | Ürün + teknik lider:** Arama p95, hata/timeout, fiyat farkı, ödeme/biletleme metriklerinin tanım/payda/kaynağı.
- **TASK-STORY-OBS-001-02 | Backend 2:** Tedarikçi/ortam bazında teknik metrik ve hassas verisiz log.
- **TASK-STORY-OBS-001-03 | Backend 2 + QA:** Pano ve alarm; başlangıç eşikleri varsayım olarak işaretli, baseline doğrulama sahibi atanmış.
- **TASK-STORY-OBS-001-04 | Operasyon:** Alarm alıcısı, ilk müdahale yönergesi ve eskalasyon testi.

**E6 çıkış kapısı:** Geri dönüş gerçekçi senaryoda kanıtlanır; alarm sahibi/aksiyonu belli olmadan trafik artırılmaz.

## E7 — Analitik ve başarı ölçümü
Epic: [E7](../epics/E7-analytics-funnel-experimentation.md). Ön koşul: Olay sözlüğü, izin yaklaşımı ve sunucu işlem kayıtları.

### STORY-ANA-001 — Arama–satın alma olaylarını uygulama
- **TASK-STORY-ANA-001-01 | Ürün + analitik:** Kritik olayların tetikleyicisi, gerekli alanı, sahibi ve kaynağını sözlükle eşleştir.
- **TASK-STORY-ANA-001-02 | Arayüz:** İzin/veri minimizasyonuna uygun web olayları; GA4/GTM/PostHog dağılımı belgeli.
- **TASK-STORY-ANA-001-03 | Backend 1/2:** Sunucu işlem olayları ve tekilleştirme; ticari gerçek kaynağı sunucu kaydı.
- **TASK-STORY-ANA-001-04 | QA + analitik:** Olay sırası, alan tipi, tekillik, izin ve hassas veri testleri.

### STORY-ANA-002 — Biletleme olaylarını sunucu kayıtlarıyla karşılaştırma
- **TASK-STORY-ANA-002-01 | Backend 2 + finans:** Bilet sayısı kaynak sorgusu ve ortak işlem referansı.
- **TASK-STORY-ANA-002-02 | Analitik:** Aynı dönem/payda ile analitik olayları ve sunucu bilet kayıtları karşılaştırması.
- **TASK-STORY-ANA-002-03 | QA + finans:** Eksik, yinelenen, gecikmiş olay testleri; fark açıklama/eskalasyon sahibi belli.

### STORY-ANA-003 — KPI panosu ve veri kalite kontrolleri
- **TASK-STORY-ANA-003-01 | Ürün + analitik:** North Star ve destek KPI'larının tanım, payda, dönem, segment ve kaynakları.
- **TASK-STORY-ANA-003-02 | Analitik:** Huni, arama p95, boş sonuç, fiyat değişimi, ödeme ve biletleme panosu.
- **TASK-STORY-ANA-003-03 | QA + analitik:** Veri tazeliği, olay kaybı, yinelenme ve beklenmedik sıfır/sıçrama kontrolleri.
- **TASK-STORY-ANA-003-04 | Ürün:** Baseline ile hedefleri ayır; tahmini hedefleri gerçekleşmiş veri gibi gösterme.

### STORY-EXP-001 — Ölçüm yeterliyse kontrollü deney hazırlığı
- **TASK-STORY-EXP-001-01 | Ürün + analitik:** Hipotez, hedef kullanıcı, ana/koruyucu ölçüt ve karar kuralı şablonu.
- **TASK-STORY-EXP-001-02 | Analitik:** Örneklem/ölçüm süresi yaklaşımı; veri yetersizse deney başlatmama.
- **TASK-STORY-EXP-001-03 | QA + ürün:** Deney ataması ve fiyat, biletleme, SEO koruyucu kontrolleri.

**E7 çıkış kapısı:** Kritik olaylar tekil ve gizlilik uyumlu; bilet sayısı sunucu kayıtlarıyla karşılaştırılır; pano güncelliği görünür.

## E8 — Operasyon ve canlıya geçiş hazırlığı
Epic: [E8](../epics/E8-operations-support-launch-readiness.md). Ön koşul: E3/E4 işlem durumları ve E6 geri dönüş planı.

### STORY-OPS-002 — Fiyat farkı ve teklif süresi için destek yanıtları
- **TASK-STORY-OPS-002-01 | Müşteri hizmetleri + ürün:** Fiyat farkı, süresi dolan teklif ve yeniden arama mesajlarını onaylat.
- **TASK-STORY-OPS-002-02 | Operasyon:** Güvenli işlem referansı ve erişilmemesi gereken hassas verileri tanımla.
- **TASK-STORY-OPS-002-03 | QA + müşteri hizmetleri:** Yanlış fiyat veya kesinleşmemiş bilet bilgisi vermeyen destek senaryosu provası.

### STORY-OPS-003 — Ödeme alınıp bilet bekleyen işlemi kurtarma yönergesi
- **TASK-STORY-OPS-003-01 | Backend 2 + operasyon:** İşlem bulma, ödeme/bilet durumunu kontrol etme ve güvenli eylem ağacı.
- **TASK-STORY-OPS-003-02 | Finans + operasyon:** Mutabakat adımları, istisna sahibi ve eskalasyon zinciri.
- **TASK-STORY-OPS-003-03 | Müşteri hizmetleri:** Bekleyen/başarısız işlem için müşteri iletişimi ve güncelleme sorumluluğu.
- **TASK-STORY-OPS-003-04 | QA + operasyon:** Çift tahsilat/rezervasyon oluşturmadan kurtarma provası.

### STORY-LCH-001 — Canlıya geçiş kontrol listesini onaylama
- **TASK-STORY-LCH-001-01 | Ürün + QA:** Kritik uçtan uca testler, açık hatalar ve kabul kanıtları.
- **TASK-STORY-LCH-001-02 | Teknik lider + operasyon:** Alarm, nöbetçi, geri dönüş anahtarı ve prova doğrulaması.
- **TASK-STORY-LCH-001-03 | SEO + pazarlama:** URL/canonical/robots/site haritası ve yayın sonrası izleme hazırlığı.
- **TASK-STORY-LCH-001-04 | Finans + operasyon:** Ödeme–rezervasyon–bilet mutabakatı ve istisna yönetimi.
- **TASK-STORY-LCH-001-05 | Ürün + karar sahipleri:** Go/no-go kararı; kanıt, açık risk, risk sahibi ve tarih kayıtlı.

**E8 çıkış kapısı:** Eğitim, kurtarma, mutabakat, test, SEO, izleme ve geri dönüş hazır olmadan canlıya çıkış yok.

## E9 — Dönüşüm iyileştirmeleri
Epic: [E9](../epics/E9-conversion-optimization.md). Başlama koşulu: E2–E4 güvenilir, E7 ölçümü doğrulanmış ve yeterli başlangıç verisi var. İlk sürüm zorunluluğu değildir.

### STORY-CRO-001 — Arama formu için iyileştirme hipotezi oluşturma
- **TASK-STORY-CRO-001-01 | Ürün + analitik:** Rota/tarih/cihaz/kaynak kırılımında sürtünmeyi teşhis et; veri sınırlılıklarını belirt.
- **TASK-STORY-CRO-001-02 | Ürün + tasarım:** Kullanıcı problemi, hipotez, hedef kitle, ana ve koruyucu ölçüt.
- **TASK-STORY-CRO-001-03 | QA + analitik:** Olay doğrulama ve deney öncesi karar kaydı.

### STORY-CRO-002 — Mobil sonuç listesi ve filtreleri iyileştirme
- **TASK-STORY-CRO-002-01 | Analitik + tasarım:** Mobil sonuçtan teklif seçimine geçiş ve filtre kullanımını incele.
- **TASK-STORY-CRO-002-02 | Tasarım + arayüz:** Veriye dayalı mobil iyileştirme ve tasarım kararı.
- **TASK-STORY-CRO-002-03 | QA:** Cihaz/viewport, erişilebilirlik, filtre ve performans regresyonu.

### STORY-CRO-003 — Koruyucu ölçütlerle kontrollü deneme yapma
- **TASK-STORY-CRO-003-01 | Ürün + analitik:** Hipotez, atama, süre, örneklem yaklaşımı ve önceden belirlenmiş karar kuralı.
- **TASK-STORY-CRO-003-02 | Arayüz + analitik:** Deneme varyantı ve tutarlı olay/atama ölçümü.
- **TASK-STORY-CRO-003-03 | QA + teknik lider:** Fiyat, ödeme/biletleme, SEO ve hata oranı koruyucu ölçütleri; durdurma koşulları.
- **TASK-STORY-CRO-003-04 | Analitik + ürün:** Etki büyüklüğü, örneklem yeterliliği ve belirsizlik raporu; devam/geri al/tekrar kararı.

**E9 çıkış kapısı:** Yeterli veriyle karar verilir; fiyat doğruluğu, biletleme veya SEO bozulursa deney durdurulur.

## Genel tamamlanma kuralı

Görev, yalnızca dokümanda yazıldığı için Done sayılmaz. Kod incelemesi, ilgili birim/sözleşme/entegrasyon/uçtan uca test kanıtı, ürün/QA kabulü ve gereken pano, SEO, gizlilik veya işletim belgesi güncellemesi gerekir. Açık API soruları [varsayımlar ve açık sorular](../../governance/assumptions-and-open-questions.md) dosyasında sorumlusu ve hedef tarihiyle tutulur.
