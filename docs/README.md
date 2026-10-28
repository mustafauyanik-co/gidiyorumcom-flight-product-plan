# Dokümantasyon rehberi

Bu klasör ürün planını konu alanlarına ayırır. Her konuda tek bir ana kaynak tutulur; diğer belgeler bu kaynağa bağlantı verir.

| Alan / belge | İçerik | Ne zaman güncellenir? |
|---|---|---|
| [Ürün hedefi ve ölçütler](product/overview-and-kpis.md) | Ürün hedefi ve başarı ölçümü | Hedef veya ölçüm tanımı değiştiğinde |
| [İş planı ve yol haritası](delivery/epics-and-roadmap.md) | Öncelikler, bağımlılıklar ve 12 haftalık plan | Kapsam, bağımlılık veya tarih değiştiğinde |
| [İş paketi kataloğu](delivery/epics/README.md) | Dokuz iş paketi ve şablon | Kapsam veya kabul ölçütü değiştiğinde |
| [Ekip ve kalite](delivery/team-and-quality.md) | Sorumluluklar, çalışma modeli ve kalite kapıları | Ekip veya işleyiş değiştiğinde |
| [Kullanıcı hikâyeleri](delivery/stories/README.md) | Ayrıntılı hikâye örnekleri | Hikâye kapsamı değiştiğinde |
| [Teknik geçiş](technical/migration-and-risks.md) | Trafik artışı, geri dönüş ve riskler | Teknik karar veya eşik değiştiğinde |
| [Diyagramlar](architecture/diagrams.md) | Kullanıcı akışı ve teknik sınırlar | Akış/mimari değiştiğinde |
| [Ölçüm planı](analytics/measurement-plan.md) | GA4, GTM, PostHog ve huni ölçümü | Olay veya ölçüt değiştiğinde |
| [Olay sözlüğü](analytics/event-dictionary.csv) | Olay adı, tetikleyici, alanlar ve sahip | Olay eklendiğinde/değiştiğinde |
| [Pazarlama ve canlıya geçiş](launch/marketing-and-launch.md) | Kanal planı, ölçüm ve yayın kapıları | Lansman planı değiştiğinde |
| [Paydaş ve raporlama](governance/stakeholders-and-reporting.md) | İletişim, eskalasyon ve raporlama | Sorumluluk veya ritim değiştiğinde |
| [Varsayımlar ve açık sorular](governance/assumptions-and-open-questions.md) | Doğrulanacak konular | Yeni bilgi geldikçe |
| [Rapor örnekleri](governance/reports/README.md) | Haftalık durum, ölçüt ve yayın kararı raporları | Rapor biçimi değiştiğinde |

## Düzenleme ilkeleri

- Aynı içeriği birden fazla belgede yinelemeyin; ana kaynağa bağlantı verin.
- Her ölçütte tanım, payda, veri kaynağı, segment ve dönem açık olsun.
- Tarihleri varsayım veya onaylanmış plan olarak ayırın.
- Karar değişikliklerinde gerekçe, etki ve geri dönüş yolu kaydedilsin.
- CSV dosyasında UTF-8, sabit sütunlar ve başlık satırı korunsun.
