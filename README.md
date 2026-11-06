# Qrame

Premiere Pro için iki panel. Bu depoda kaynak kod yok, yalnızca imzalı kurulum paketleri var.

| Panel | Ne yapar |
|---|---|
| **Qrame** | Aktif sekansı zaman koduna göre yeniden keser ve kalan parçaları boşluksuz, yeni bir sekansta birleştirir. Özgün zaman çizgisine hiç dokunmaz. Üç yolu var: hazır bir SRT bırakmak; Sessizlik Kesme ile duraklamaları ölçüp kesmek; ya da sesi deşifre eden (yerelde Whisper ile ya da Gladia ile) ve tutulacak bölümleri sizin yazdığınız talimata göre bir modele seçtiren Otomatik Kurgu. Altyazıları da zaman çizgisine yerleştirir. |
| **Qrame Cont** | Toplu MOGRT parametre düzenleme, klip klip altyazı metni düzenleme, toplu keyframe yumuşatma ve kadraj araçları (QZoom, QPan, QStep). |

## İndir

**[Qrame_0.1.3_Cont_0.2.2.dmg](https://github.com/menestopal/Qrame-releases/releases/download/qrame-0.1.3-cont-0.2.2/Qrame_0.1.3_Cont_0.2.2.dmg)** — Qrame 0.1.3 ve Qrame Cont 0.2.2, altyazı şablonlarıyla birlikte.

Her zaman en son sürüme giden bağlantı: https://github.com/menestopal/Qrame-releases/releases/latest

Önceki sürümler: [Sürümler](https://github.com/menestopal/Qrame-releases/releases). Sürüm sayfasında yalnızca `.dmg` dosyasını indirin;
"Source code" arşivlerini GitHub kendiliğinden ekler, kurulum için gerekmez.

## Qrame 0.1.3 ve Qrame Cont 0.2.2 — Kurulum

Qrame ve Qrame Cont, Premiere Pro için iki paneldir. Kurulum bir dakika sürer.

Gereksinimler: macOS ve Premiere Pro 25.0 ya da üstü (26.3'te denendi). Bu
kurulum Windows'ta çalışmaz.

### 1. Diski açın

`Qrame_0.1.3_Cont_0.2.2.dmg` dosyasını çift tıklayın. Finder'da **Qrame 0.1.3 + Cont 0.2.2** adlı bir disk
açılır:

| | |
|---|---|
| `Install.command` | Kurulum. Çalıştıracağınız dosya bu. |
| `INSTALL.html` | Bu talimatlar. |
| `Qrame_0.1.3.zxp` | Qrame paneli, imzalı. Elle açmanız gerekmez. |
| `QrameCont_0.2.2.zxp` | Qrame Cont paneli, imzalı. Elle açmanız gerekmez. |
| `Templates` | Panellerin hazırlandığı altyazı şablonları (`.mogrt`). |

### 2. Kurun

Premiere Pro'yu kapatın, sonra `Install.command` dosyasını çift tıklayın.
Terminal açılır ve her adımı yazar.

macOS ilk seferde "Apple doğrulayamadı" ya da "tanımlanamayan geliştirici"
diyerek dosyayı açmayabilir. Bu beklenen bir durum: dosya App Store'dan değil,
doğrudan Fokus Plus'tan geliyor. İki yol var:

- Uyarıda **Bitti**'ye basın. **Sistem Ayarları › Gizlilik ve Güvenlik**'i
  açın, sayfanın altındaki `Install.command` satırında **Yine de Aç**'a basın.
  Parolanızı girin, çıkan pencerede **Aç**'a basın.
- Ya da Terminal'i açın (**Uygulamalar › İzlenceler › Terminal**), `bash `
  yazın (sonunda bir boşlukla), `Install.command` dosyasını Terminal
  penceresine sürükleyip bırakın ve Enter'a basın.

Kurulum yalnızca şu klasörlere yazar, başka hiçbir yere dokunmaz:

```
~/Library/Application Support/Adobe/CEP/extensions/net.fokusplus.qrame.bundle/       Qrame
~/Library/Application Support/Adobe/CEP/extensions/net.fokusplus.qrame.cont.bundle/  Qrame Cont
~/Library/Application Support/Adobe/Common/Motion Graphics Templates/                şablonlar
```

Paneller imzalı olduğu için herhangi bir geliştirici ayarını açmanız gerekmez.
Panellerden birinin başka bir yerde kurulu bir kopyası varsa kurulum hiçbir
şeyi değiştirmeden durur ve o kopyayı kaldıracak komutu yazar.

Kurulum bitince diski çıkarabilirsiniz (Finder'da diskin yanındaki ⏏ işareti)
ve `.dmg` dosyasını silebilirsiniz.

### 3. Panelleri açın

Premiere Pro'yu başlatın, bir proje açın ve **Window › Extensions › Qrame** ya
da **Window › Extensions › Qrame Cont**'u seçin.

### 4. Altyazı şablonları

Şablonlar artık Premiere'in yerel şablon klasöründe. Bu yüzden **Essential
Graphics** panelinde görünürler; Qrame Cont da bu şablonlardan yapılmış
klipleri düzenlerken onları kendiliğinden bulur.

Qrame'de altyazı için panelin alt çubuğundaki **MOGRT** düğmesine basıp bir
şablon seçin. Bu klasör dosya penceresinde gizlidir: **⌘⇧G**'ye basın ve
`~/Library/Application Support/Adobe/Common/Motion Graphics Templates` yolunu
yapıştırın.

Şablonlar **Barlow** yazı tipi ailesini kullanır. Premiere eksik yazı tipi
uyarısı verirse Barlow'u Adobe Fonts'ta etkinleştirin (Creative Cloud'a dahil)
ya da Google Fonts'tan kurun. İkisi de ücretsiz.

### 5. Otomatik kurgu için ek kurulum

Hazır bir SRT'den kesmek ve Qrame Cont'taki her şey kurulumdan hemen sonra
çalışır. **Sessizlik Kesme** (Silence Cut) ve **Otomatik Kurgu** (Automatic
Build) birkaç komut satırı aracına (Homebrew'dan ffmpeg ve whisper-cpp, bir
Whisper modeli) ve tutulacak bölümleri seçen model için bir API anahtarına
ihtiyaç duyar. Qrame panelinin **Hakkında** (About) bölümü makineyi denetler,
eksikleri listeler ve her biri için komutu verir.

### Güncelleme

Yeni `.dmg` dosyasını indirin ve içindeki `Install.command`'ı aynı şekilde
çalıştırın. Kurulu panellerin ve şablonların yerine geçer.

### Panel görünmüyorsa

- **Window › Extensions** altında listeleniyor ama açılmıyorsa, genellikle
  kayıtlı çalışma alanında ekranın dışında açıktır. **Window › Workspaces ›
  Reset to Saved Layout**'u seçin.
- Hiç listelenmiyorsa Premiere Pro'yu bir kez daha yeniden başlatın. Hâlâ
  yoksa `Install.command`'ı yeniden çalıştırın ve ne yazdığını okuyun.
