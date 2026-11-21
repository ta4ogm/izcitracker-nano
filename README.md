# İzci hymTR Tracker – Ayar Aracı

İzci hymTR APRS tracker'ın ayarlarını **tarayıcıdan, USB üzerinden** okuyup değiştiren araç. Yeniden yazılım yüklemeye gerek yok; ayarlar doğrudan Nano'nun EEPROM'una yazılır.

**Araç:** https://ta4ogm.github.io/izcitracker-nano/

> Bilgisayarda **Google Chrome** ya da **Microsoft Edge** gerekir (Web Serial). Firefox, Safari ve telefonlar desteklemez.

## Kullanım

1. Tracker'ı USB ile bilgisayara takın. Arduino IDE'nin Serial Monitor'ünü ve orijinal ayar programını kapatın.
2. **Tracker'a bağlan** → COM portunu seçin. Araç tracker'ı ayar moduna alıp mevcut ayarları okur.
3. Çağrı işareti, SSID, simge, açıklama ve beacon sıklığını değiştirip **Ayarları tracker'a yaz**'a basın. Araç yazdıktan sonra ayarları tekrar okuyup doğrular.
4. **Bağlantıyı kes** → tracker normal çalışmaya döner.

## Değiştirilebilen ayarlar

| Ayar | Açıklama |
|---|---|
| Çağrı işareti, SSID | 0–15 arası SSID |
| Harita simgesi | Araba, jip, kamyon, bisiklet, yürüyen kişi vb. |
| Açıklama | En fazla 29 karakter (başına yükseklik eklenir) |
| Beacon sıklığı | Hıza göre aralık: çarpan × 100 / 60 / 40 / 20 sn (≤10 / 10–50 / 50–100 / 100+ km/s) |

## Bilinen kısıtlar (orijinal yazılım 01012020a)

- Yol (path) ayarı kaydedilir ama yazılım paketleri her zaman **WIDE1-1,WIDE2-2** ile gönderir.
- Hedef (destination) ayarı kaydedilmez.
- Sembol tablosu her zaman birincil (`/`) tablodur.

## Seri protokol

115200 baud. `!` ayar moduna sokar (cihaz `#` yazar). `R` ayarları okur, `W` ardından `0x01` ve TAB ile ayrılmış alanları alıp EEPROM'a yazar (ilk alan yazılım sürümüdür), `D` fabrika ayarları, `Q` çıkış. Ayrıntılar `index.html` içindeki `HymProto` bölümündedir.

## Teşekkür

İzci hymTR tracker ve LibAPRS_Tracker kütüphanesi Barış Dinç (TA7W) tarafından geliştirilmiştir: [barisdinc/hymTR](https://github.com/barisdinc/hymTR). Bu araç, aynı seri ayar protokolünü kullanan bağımsız bir tarayıcı uygulamasıdır.

Çağrı işaretiyle yayın yapmak için geçerli bir amatör telsiz lisansı gerekir.
