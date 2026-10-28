# STORY-FLT-001 — Uçuş sonuçlarını filtreleme

- **Durum:** Taslak; ürün ve tasarım onayı bekliyor.
- **İş paketi:** E2 — Arama ve sonuçlar
- **Öncelik / tahmin:** Zorunlu / 5 puan
- **Sorumlular:** Arayüz geliştiricisi, Backend 2, QA
- **Başarı ölçütleri:** Sonuçtan teklif seçimine geçiş, filtre kullanımı, arama oturumu başına kesilmiş bilet
- **Ölçüm olayı:** flight_filter_applied

## Problem ve kullanıcı ihtiyacı

Kullanıcı sonuçları fiyat, aktarma sayısı, kalkış saati ve havayoluna göre daraltabilmelidir. Böylece kendisine uygun uçuşu daha hızlı bulabilir.

## Kapsam

**Dahil:** Filtreler, aynı türde çoklu seçim, filtreleri kaldırma/temizleme, URL parametreleriyle durumu koruma, boş sonuç mesajı, mobil ve klavye erişimi, ölçüm olayı.

**Dahil değil:** Kişiselleştirilmiş sıralama, kalıcı kullanıcı tercihleri ve mevcut sonuçlarda desteklenemeyen yeni filtreler.

## Kabul ölçütleri

1. **Tek filtre:** Kullanıcı bir değer seçtiğinde yalnızca bu koşulu karşılayan uçuşlar kalır ve seçili filtre görünür.
2. **Filtreleri birleştirme:** Farklı filtre türleri birlikte uygulanır (AND); aynı türde birden fazla değer seçimi OR mantığıyla çalışır.
3. **Sıfır sonuç:** Hiçbir uçuş koşulları karşılamazsa açıklayıcı mesaj ve filtreleri temizleme seçeneği gösterilir.
4. **Filtreyi kaldırma:** Tek filtre kaldırıldığında diğer filtreler korunur; tüm filtreler temizlenirse liste filtresiz duruma döner.
5. **URL durumu:** Sayfa yenileme ve geri/ileri gezinmede geçerli filtreler korunur. Geçersiz parametreler uygulamayı bozmadan yok sayılır.
6. **Eksik veri:** Eksik aktarma veya kalkış alanı varsayılan bir değere dönüştürülmez; yanlış sınıflandırma yapılmaz ve sorun ölçüm/log için güvenli biçimde kaydedilir.
7. **Olay ölçümü:** Filtre başarıyla değiştiğinde olay bir kez gönderilir; filtre türü, seçili değer sayısı, arama kimliği ve tedarikçi gibi gerekli alanlar kullanılır. Kişisel veri gönderilmez.
8. **Erişilebilirlik:** Filtreler mobilde kullanılabilir ve klavyeyle erişilebilir olmalıdır.

## İş kuralları ve bağımlılıklar

- Fiyat filtresi gösterilen toplam fiyatla ve para birimiyle uyumlu olmalıdır.
- Filtre alanları ortak sonuç modelinde Backend 2 tarafından doğrulanmalıdır.
- URL parametrelerinin mevcut SEO adreslerine etkisi SEO sorumlusuyla kontrol edilmelidir.

## Test kapsamı

Farklı filtre kombinasyonları; sınır değerler; sıfır sonuç; filtre kaldırma/temizleme; URL ve gezinme; eksik alan; olay tekilleştirme; mobil ve klavye erişimi.

## Tamamlanma koşulu

Kabul ölçütleri test edilmiş; olay sözlüğü ve ölçüm planı güncellenmiş; kişisel veri kontrolü ve ürün/QA kabulü tamamlanmış olmalıdır.

## Görevler

### TASK-STORY-FLT-001-01 — Filtre kurallarını ve durumlarını tanımlama
- **Sorumlu:** Ürün yöneticisi, tasarım
- **Bağımlılık:** Ortak uçuş sonuç modeli
- **Görev:** Fiyat, aktarma, kalkış saati ve havayolu filtrelerinin seçim, çoklu seçim, temizleme ve boş sonuç davranışlarını tanımlamak.
- **Tamamlanma ölçütü:** Filtre kuralları ve temel/mobil durum tasarımları ürün tarafından onaylanmış.

### TASK-STORY-FLT-001-02 — Filtre alanlarını ortak modelde doğrulama
- **Sorumlu:** Backend 2
- **Bağımlılık:** E1 ortak sonuç modeli
- **Görev:** Filtre alanlarının anlamını, fiyat/para birimi tutarlılığını ve eksik alan davranışını doğrulamak.
- **Tamamlanma ölçütü:** Desteklenmeyen veya eksik alanlar varsayılan değerle doldurulmuyor; alan eşlemeleri belgelenmiş.

### TASK-STORY-FLT-001-03 — Filtreleme arayüzünü uygulama
- **Sorumlu:** Arayüz geliştiricisi
- **Bağımlılık:** TASK-STORY-FLT-001-01 ve TASK-STORY-FLT-001-02
- **Görev:** Tekli/çoklu seçim, filtreyi kaldırma ve tüm filtreleri temizleme davranışlarını uygulamak. Farklı filtre türleri AND, aynı türde birden fazla değer OR mantığıyla çalışmalı.
- **Tamamlanma ölçütü:** Sonuç listesi, seçili filtreler ve sonuç sayısı aynı filtre durumunu yansıtıyor.

### TASK-STORY-FLT-001-04 — Filtre durumunu URL ile eşleştirme
- **Sorumlu:** Arayüz geliştiricisi
- **Bağımlılık:** TASK-STORY-FLT-001-03; SEO kontrolü
- **Görev:** Geçerli filtreleri URL parametrelerinde korumak; yenileme ve geri/ileri gezinmede durumu geri yüklemek; geçersiz parametreleri güvenli biçimde yok saymak.
- **Tamamlanma ölçütü:** Mevcut SEO URL davranışı bozulmadan gezinme senaryoları çalışıyor.

### TASK-STORY-FLT-001-05 — Filtre analitik olayını ekleme
- **Sorumlu:** Arayüz geliştiricisi, analitik sorumlusu
- **Bağımlılık:** Olay sözlüğü ve izin/veri minimizasyonu kuralları
- **Görev:** Filtre başarıyla değiştiğinde `flight_filter_applied` olayını bir kez göndermek; yalnızca gerekli, kişisel veri içermeyen alanları kullanmak.
- **Tamamlanma ölçütü:** Olay sözlüğüyle alanlar eşleşiyor ve tekrar gönderim testi geçiyor.

### TASK-STORY-FLT-001-06 — Filtreleme ve erişilebilirlik testlerini tamamlama
- **Sorumlu:** QA
- **Bağımlılık:** TASK-STORY-FLT-001-03, TASK-STORY-FLT-001-04 ve TASK-STORY-FLT-001-05
- **Görev:** Filtre kombinasyonları, sınır değerler, sıfır sonuç, temizleme, URL gezinmesi, eksik veri, olay tekilleştirme, mobil ve klavye erişimini test etmek.
- **Tamamlanma ölçütü:** Kabul ölçütleri test kanıtlarıyla doğrulanmış; kritik hata kalmamış.


- [İş paketi ve yol haritası](../epics-and-roadmap.md)
- [Ekip ve kalite kapıları](../team-and-quality.md)
- [Analitik ölçüm planı](../../analytics/measurement-plan.md)
- [Olay sözlüğü](../../analytics/event-dictionary.csv)
