# Akış ve mimari diyagramları

Bu diyagramlar ürün akışını ve karar kapılarını özetler. Teknik ayrıntıların kaynağı API sözleşmesi ve ilgili Epic dokümanlarıdır.

## 1. Aramadan biletlemeye kullanıcı akışı

```mermaid
flowchart TD
    A[Arama formu] --> B[Arama isteği]
    B --> C{Kullanılabilir uçuş var mı?}
    C -->|Hayır| D[Boş sonuç veya hata mesajı]
    D --> A
    C -->|Evet| E[Uçuş sonuçları]
    E --> F[Uçuş ve teklif seçimi]
    F --> G[Fiyat ve uygunluğu yeniden doğrula]
    G --> H{Teklif geçerli mi?}
    H -->|Geçersiz veya süresi dolmuş| I[Yeniden arama veya teklif seçimi]
    I --> E
    H -->|Fiyat değişmedi| J[Yolcu bilgileri]
    H -->|Fiyat değişti| K[Eski ve yeni toplamı göster]
    K --> L{Kullanıcı yeni fiyatı kabul ediyor mu?}
    L -->|Hayır| I
    L -->|Evet| J
    J --> M[Ödemeyi başlat]
    M --> N{Ödeme sonucu doğrulandı mı?}
    N -->|Hayır| O[Ödeme durumunu kontrol et]
    O --> P[Destek veya güvenli yeniden deneme]
    N -->|Evet| Q[Biletleme isteği]
    Q --> R{Bilet kesildi mi?}
    R -->|Evet| S[Bilet ve onay bilgisi]
    R -->|Bekliyor veya başarısız| T[Durumu izle ve operasyon ekibine aktar]
```

## 2. Önerilen teknik sınırlar

```mermaid
flowchart LR
    UI[Web arayüzü] --> API[gidiyorum.com sunucu API'si]
    API --> ROUTER[Tedarikçi yönlendiricisi ve özellik anahtarı]
    ROUTER --> OLD[Mevcut tedarikçi bağdaştırıcısı]
    ROUTER --> TV[TourVisio bağdaştırıcısı]
    OLD --> MODEL[Ortak uçuş ve teklif modeli]
    TV --> MODEL
    MODEL --> API
    API --> ORDER[Sipariş ve rezervasyon durum yönetimi]
    ORDER --> PAY[Mevcut ödeme sağlayıcısı]
    ORDER --> TKT[Biletleme ve mutabakat]
    API --> OBS[Loglar, ölçümler ve alarmlar]
    UI --> WEBAN[İzinli web ölçümü]
    WEBAN --> GA4[GA4]
    WEBAN --> PH[PostHog]
    API --> SERVER[Sunucu tarafı işlem olayları]
    SERVER --> BI[İşlem mutabakatı ve raporlama]
```

Not: Analitik araçlarına veri gönderimi izin ve veri minimizasyonu kurallarına uymalıdır. Yolcu, ödeme kartı ve diğer hassas bilgiler analitik olaylarına veya loglara yazılmaz.

## 3. Kademeli canlıya geçiş ve geri dönüş

```mermaid
flowchart TD
    A[Canlıya geçiş kontrol listesi] --> B{Uçtan uca test, izleme ve geri dönüş hazır mı?}
    B -->|Hayır| C[Canlıya geçişi durdur]
    B -->|Evet| D[%1 trafik]
    D --> E[En az 24–48 saat izle]
    E --> F{Tüm koruyucu ölçütler uygun mu?}
    F -->|Hayır| G[Yeni tedarikçi trafiğini durdur ve incele]
    F -->|Evet| H[%5 trafik]
    H --> I[En az 48 saat izle]
    I --> J{Ölçütler uygun mu?}
    J -->|Hayır| G
    J -->|Evet| K[%10 trafik]
    K --> L[Her basamakta ölç ve karar kaydet]
    L --> M[%25, ardından %50]
    M --> N{Ürün, teknik ve operasyon onayı var mı?}
    N -->|Hayır| G
    N -->|Evet| O[%100 için ayrı karar]
    G --> P[Önceki tedarikçiye dönüş ve olay incelemesi]
```

Trafik yüzdesi tek başına ilerleme ölçütü değildir. Fiyat tutarlılığı, ödeme ve biletleme başarısı, hata oranı ve SEO sağlığı kabul aralığında olmalıdır. Her basamakta karar, kanıt ve sorumlu kaydedilir.

## 4. Ölçüm ve raporlama akışı

```mermaid
flowchart TD
    A[Kullanıcı etkileşimi] --> B[İzin ve veri minimizasyonu kontrolü]
    B -->|İzin varsa ve uygunsa| C[Web ölçüm olayları]
    C --> D[GA4: edinim ve web davranışı]
    C --> E[PostHog: ürün akışı ve huni]
    F[Sunucu tarafı sipariş ve biletleme durumu] --> G[İşlem kayıtları ve tekilleştirme]
    G --> H[İşlem–analitik mutabakatı]
    H --> I[KPI panosu ve karar raporu]
    J[Search Console] --> K[Organik arama ve teknik SEO takibi]
    K --> I
```

GA4/PostHog kullanıcı davranışını, sunucu kayıtları ise doğrulanmış ticari işlemleri ölçer. Sayılar arasındaki farklar; izin tercihleri, olay kaybı, yinelenen bildirimler ve ölçüm tanımları dikkate alınarak açıklanmalıdır.
