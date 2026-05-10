# Katkıda Bulunma Rehberi

Teşekkürler! Bu liste topluluk katkılarıyla büyüyor.

## En kolay yol: Issue aç

Filtre yazmayı bilmiyorsan, sadece şunu yap:

1. [Yeni Issue](https://github.com/morphaven/brave-turkiye-filters/issues/new/choose) aç.
2. Sitenin URL'sini ve reklamın ne olduğunu yaz.
3. Reklamın HTML'ini ekle (sağ tık → İncele → ilgili element üzerinde sağ tık → Copy → **Copy outerHTML**).
4. Ekran görüntüsü çok yardımcı olur.

Filtreyi biri yazıp listeye ekler.

## Pull Request açıyorsan

### 1. Filtreni doğru yere ekle

`filters.txt` dosyası alan adına göre bölümlere ayrılmıştır. Yeni bir site ekliyorsan alfabetik sırayla yeni bir bölüm aç:

```
! ====== siteadi.com ======
!
! Açıklama (hangi reklamı hedefliyor)
siteadi.com##.reklam-class
```

### 2. Mümkün olduğunca dar hedefle

Yanlış: `siteadi.com##div` (her şeyi siler)
Doğru: `siteadi.com##div.belirli-reklam-class`

Random/değişken class isimleri varsa **sabit** kısımları hedefle:
- Reklam linkinin domain'i (`a[href*="reklamveren.com"]`)
- Resmin CDN yolu (`img[src*="cdn.site.com/ads"]`)
- Parent yapı + `:has()`

### 3. Yorum ekle

Her filtrenin üstüne kısa bir yorum:

```
! Sticky alt banner — "Uygulamayı indir" katmanı
```

İleride biri filtreyi gördüğünde ne işe yaradığını anlayabilsin.

### 4. Test et

PR açmadan önce filtreyi Brave'de **özel filtre** olarak ekleyip dene:

1. `brave://settings/shields/filters`
2. **Özel filtreler oluştur** kutusuna yapıştır.
3. Siteyi aç, reklam gerçekten gitti mi? Sayfanın başka bir yeri bozuldu mu?

### 5. Versiyonu artır

PR'ında `filters.txt`'in başındaki `! Version:` satırını güncelle (örn. `1.0.0` → `1.0.1`).

## Sözdizimi yardımı

[README'deki tabloya bak](README.md#filtre-yazım-kuralları), tam dökümantasyon: [uBlock Origin Wiki](https://github.com/gorhill/uBlock/wiki/Static-filter-syntax).
