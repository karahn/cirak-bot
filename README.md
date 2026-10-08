# çırak-bot 🤖

**Çırak** (oyunsitem.com/cirak) için otomatik oyun botu.
Karahan kişisel hesabı — 7/24 kesintisiz çalışma modu.

## Nasıl çalışır?

| Parça | Açıklama |
|---|---|
| `cirak/actions/cirak_kosu.py` | Koşucu — GitHub Actions üzerinde çalışır (Python 3.11) |
| `cirak/komut.json` | Görev listesi + süre (push edilince koşu tetiklenir) |
| `cirak/actions/bot_cekirdek.py` | Oyun çekirdeği: tezgâh grind, sokak olayları, günlük ödüller, oda, dükkân kiralama |
| `cirak/rapor/` | Her koşunun raporu (`son.json`, `son.md`) |
| `cirak/loglar/kosu.jsonl` | Koşu günlüğü |
| `cirak/kaynak/` | Oyun kaynak dosyaları (bootstrap, API uçları) |

## 7/24 Kesintisiz Mod

- ⏰ **Schedule:** Her 30 dakikada bir otomatik çalışır (UTC :05 ve :35)
- 🔁 **Zincir:** Her koşu bitince `repository_dispatch` ile kendini yeniden tetikler
- 🕐 **Timeout:** Her koşu en fazla ~6 saat çalışır
- ♾️ **Public repo:** Sınırsız GitHub Actions

## Kurulum

1. **Gizli anahtar ekle:** Settings → Secrets → Actions → New secret
   - Name: `TEZGAH_CEREZ`
   - Value: Oyun oturum çerezi (`tezgah_oturum` cookie değeri)
2. **Yazma izni ver:** Settings → Actions → Workflow permissions → Read and write
3. **Başlat:** Actions → Cirak Bot → Run workflow

🔐 **Kimlik bilgileri repoda YOKTUR** — oturum çerezi GitHub Actions gizli anahtarında tutulur.

## Ne yapar?

- 🛒 Seyyar tezgâhları çalıştırıp müşterilere servis yapar (bahşiş toplar)
- 🚶 Sokak olaylarını değerlendirir (cüzdan, kedi, sokak sanatçısı…)
- 🎁 Günlük bonus, görev ödülü, sezon ödülü, oda eğitimi (TP) toplar
- 📬 Oyun içi mesajlaşma
- 🏪 Para yettiğinde dükkân kiralar (kargo, oto yıkama, oto servis, emlakçı)
- 🔁 Koşu bitince kendini yeniden tetikler — kesintisiz döngü
