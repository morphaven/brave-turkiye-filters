# Brave Türkiye Filtreleri

Türk web sitelerindeki rahatsız edici reklamlar, popup'lar, "uygulamayı indir" katmanları ve benzeri can sıkıcı öğeler için topluluk tarafından sürdürülen filtre listesi.

EasyList gibi uluslararası listeler Türk sitelerinin yerel reklam panellerini (r10.net iyzico paneli, çeşitli haber sitelerinin sticky reklamları, KVKK çerez bantları vb.) çoğunlukla yakalayamıyor. Bu liste o boşluğu doldurmayı amaçlıyor.

## Listeyi Brave'e ekleme

1. Brave'de şu adrese git: `brave://settings/shields/filters`
2. **Geliştirici modu**'nu aç.
3. **Özel filtre listesi ekle** kısmına şu URL'yi yapıştır:

```
https://raw.githubusercontent.com/morphaven/brave-turkiye-filters/main/filters.txt
```

4. **Ekle**'ye bas. Brave listeyi günde bir kez otomatik günceller.

## Listeyi uBlock Origin'e ekleme

1. uBlock Origin **Pano**'yu aç (uzantı simgesine tıkla → dişli ikonu).
2. **Filtre Listeleri** sekmesine git.
3. En alttaki **İçe Aktar...** kutusunu işaretle.
4. Yukarıdaki raw URL'yi yapıştır → **Değişiklikleri Uygula**.

## Tek bir filtreyi denemek istersen

Tüm listeyi eklemeden, sadece tek bir kuralı denemek için:

1. `brave://settings/shields/filters`
2. **Özel filtreler oluştur** kutusuna kuralı yapıştır, örneğin:

```
r10.net##a[href*="iyzico.com/partner"]
```

3. **Değişiklikleri kaydet**.

## Katkıda bulunmak istiyorsan

Bir Türk sitesinde rahatsız edici bir reklam/popup gördüysen ve bu liste yakalamıyorsa, **Issue aç**:

→ [Yeni Issue](https://github.com/morphaven/brave-turkiye-filters/issues/new/choose)

Şunları yazman yeterli:
- Sitenin URL'si (örn. `r10.net`)
- Reklamın ne olduğu (kısaca)
- Mümkünse reklamın HTML'i (sağ tık → İncele → ilgili `<div>` üzerinde sağ tık → Copy → Copy outerHTML) veya ekran görüntüsü

Pull Request de yapabilirsin — bkz. [CONTRIBUTING.md](CONTRIBUTING.md).

## Filtre yazım kuralları

Bu liste **Adblock Plus / uBlock Origin sözdizimini** kullanır. Hızlı referans:

| Sözdizimi | Anlamı |
|-----------|--------|
| `r10.net##.adsbox` | r10.net'te `.adsbox` class'ına sahip elementi sakla |
| `r10.net###reklam` | r10.net'te `id="reklam"` olan elementi sakla |
| `r10.net##a[href*="x.com"]` | href'inde `x.com` geçen linkleri sakla |
| `r10.net##.kutu:has(.reklam)` | İçinde `.reklam` olan `.kutu`'yu sakla |
| `||example.com/ads.js` | İstek engelle (script/img yüklenmesin) |
| `! yorum` | Yorum satırı |

Random/değişken class isimleri varsa, **sabit kalan** kısmı (link, img src, parent yapı) hedeflemeye çalış.

Tam dökümantasyon: [uBlock Origin Wiki — Static filter syntax](https://github.com/gorhill/uBlock/wiki/Static-filter-syntax).

## Lisans

[GPL-3.0](LICENSE) — EasyList ekosistemi ile uyumlu olması için.
