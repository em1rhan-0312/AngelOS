# Derleme

Bu repoda Telegram'ın kendi kodu yok, sadece değişiklikleri içeren `angelgram-telegram.patch` var.
GitHub Actions her derlemede resmi Telegram kodunu sabit bir sürümden (`3de37c8`) indirir, yamayı uygular ve APK üretir.

```
.github/workflows/build.yml   derleme tarifi
angelgram-telegram.patch      tüm değişiklikler
preview/                      logo, yazı logosu ve ekran görüntüleri
```

## APK üretmek

1. Repo → **Actions** → **Angelgram APK** → **Run workflow**
2. Derleme ~30-40 dk sürer. Bitince çalıştırmanın altındaki **Artifacts** bölümünden `angelgram-apk-...` dosyasını indir (zip içinden APK çıkar).
3. Telefonda "bilinmeyen kaynaklardan yüklemeye izin ver" açıkken APK'yı kur.

`hizli` ve `standart` iki derleme birbirinin yedeği, ikisi de arm64 telefonlar içindir. Hangisi kurulursa onu kullan.

## Önemli

- **Repo özel (private) kalmalı.** Yama, kendi `api_id` / `api_hash` değerlerini içerir. `api_hash` gizlidir, herkese açık repoya konmamalı.
- Yama sabit Telegram sürümüne göre hazırlandı. Sürümü değiştirmek yamanın uymamasına yol açabilir.
