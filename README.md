# 🔍 Nesne Bul Oyunu

AI destekli "hidden object" (gizli nesne bulma) oyunu. Görsele tıklarsın, Claude Vision API tıklanan bölgeyi analiz eder ve doğrular.

## 🎮 Demo

Oyunu doğrudan GitHub Pages üzerinden oynayabilirsin:  
`https://<kullanici-adin>.github.io/hidden-object-game`

## ✨ Özellikler

- 🤖 **AI Nesne Tespiti** — Görsel otomatik analiz edilir, 8 nesne listelenir
- 🖱️ **Tıkla & Doğrula** — Tıklanan bölge kırpılıp Claude'a gönderilir, EVET/HAYIR yanıtı alınır
- 💡 **İpucu Sistemi** — Takıldığında AI sana yön gösterir
- 📁 **Kendi Görselini Yükle** — Herhangi bir resimle oynayabilirsin
- 📱 **Responsive** — Mobil uyumlu tasarım

## 🚀 Kurulum

### 1. Repoyu klonla
```bash
git clone https://github.com/<kullanici-adin>/hidden-object-game.git
cd hidden-object-game
```

### 2. Anthropic API anahtarı al
[console.anthropic.com](https://console.anthropic.com) adresinden ücretsiz hesap aç ve API anahtarı oluştur.

### 3. Çalıştır
Herhangi bir web sunucusu ile aç (CORS nedeniyle doğrudan `file://` açma):

```bash
# Python ile
python3 -m http.server 8080

# Node.js ile  
npx serve .
```

Tarayıcıda `http://localhost:8080` aç → API anahtarını gir → Oyna!

## 🌐 GitHub Pages ile Yayınlama

1. GitHub'da repo oluştur ve dosyaları push'la
2. **Settings → Pages → Source: main branch → / (root)**
3. Birkaç dakika sonra `https://<kullanici-adin>.github.io/hidden-object-game` canlı olur

> **Not:** API anahtarın tarayıcının `localStorage`'ına kaydedilir, hiçbir sunucuya gönderilmez.

## 🗂️ Dosya Yapısı

```
hidden-object-game/
├── index.html          # Oyunun tamamı (tek dosya)
├── sample-image.jpg    # Varsayılan oyun görseli
└── README.md
```

## 🔧 Nasıl Çalışır?

```
1. Görsel yükle
       ↓
2. Claude API → Görseli analiz et → 8 nesne JSON listesi döndür
       ↓
3. Kullanıcı görsele tıklar
       ↓
4. Tıklanan bölge canvas ile kırpılır
       ↓
5. Claude API → "Bu bölgede [nesne] var mı?" → EVET / HAYIR
       ↓
6. EVET → Puan ekle, marker koy, sıradaki nesneye geç
   HAYIR → "Burada yok, tekrar dene!"
```

## 🛠️ Özelleştirme

`index.html` içindeki sabitler:

```javascript
const API_MODEL = "claude-sonnet-4-20250514"; // Model değiştir
const cropSize = 0.25;  // Tıklama hassasiyeti (0.1 - 0.5 arası)
score += 100;           // Her nesne için puan
```

## 📋 Gereksinimler

- Modern tarayıcı (Chrome, Firefox, Safari, Edge)
- [Anthropic API anahtarı](https://console.anthropic.com) (ücretsiz tier yeterli)

## 📄 Lisans

MIT License
