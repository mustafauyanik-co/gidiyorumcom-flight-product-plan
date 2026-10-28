# Kullanıcı hikâyesi kataloğu

Bu klasör, ürün iş listesindeki iki ayrıntılı kullanıcı hikâyesi örneğini içerir. Belgeler başlangıç taslağıdır; uygulama öncesinde API sözleşmesi, tasarım ve ürün kararları doğrulanmalıdır.

## Hikâyeler

| Kimlik | Hikâye | İş paketi | Öncelik | Tahmin |
|---|---|---|---|---:|
| [STORY-FLT-001](STORY-FLT-001-flight-results-filters.md) | Uçuş sonuçlarını filtreleme | E2 — Arama ve sonuçlar | Zorunlu | 5 puan |
| [STORY-FLT-002](STORY-FLT-002-price-change-confirmation.md) | Ödeme öncesi fiyat değişikliğini onaylama | E3 — Fiyat doğruluğu | Zorunlu | 8 puan |

## Yazım standardı

Her hikâyede şu bilgiler bulunmalıdır:

- Benzersiz kimlik, durum, iş paketi, öncelik, tahmin ve sorumlu.
- Kullanıcı problemi, beklenen değer ve kapsam.
- Numaralandırılmış, test edilebilir kabul ölçütleri.
- İş kuralları, ölçüm olayları ve veri gizliliği.
- Bağımlılıklar, riskler, test senaryoları ve ilgili belgeler.

Kabul ölçütlerinde Given / When / Then biçimi kullanılabilir; belgelerde ön koşul, olay ve beklenen sonuç açıkça yazılmalıdır.

Yeni hikâye açmak için [GitHub kullanıcı hikâyesi şablonunu](../../../.github/ISSUE_TEMPLATE/product-story.md) kullanın. Şablon boş formdur; bu klasördeki dosyalar doldurulmuş örneklerdir.
