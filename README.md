# Mihrabad Yayınları Web Sitesi

<p align="center">
  <img src="assets/images/logo.png" alt="Mihrabad Yayınları Logo" width="200">
</p>

<p align="center">
  <em>"Medeniyetimizin izinde!"</em>
</p>

<p align="center">
  <a href="https://mihrabadyayinlari.com">Web Sitesi</a> •
  <a href="https://www.facebook.com/mihrabadyayin">Facebook</a> •
  <a href="https://twitter.com/mihrabadyayin">Twitter</a> •
  <a href="https://instagram.com/mihrabadyayin">Instagram</a>
</p>

---

## 📖 Proje Hakkında

Mihrabad Yayınları, kültür, sanat, tarih ve edebiyat alanlarında medeniyet eksenli yayıncılık yapan bir kuruluşun kurumsal web sitesidir. Jekyll statik site üreticisi kullanılarak geliştirilmiştir.

### Özellikler

- 📚 **Kitap Kataloğu**: 75+ kitap ile zengin bir katalog
- ✍️ **Yazar Profilleri**: Detaylı yazar biyografileri ve eserleri
- 🎵 **Kültür Mirası**: Hafızların sesli eserleri ve biyografileri
- 📰 **Blog/Haberler**: Yayın günlüğü ve haberler
- 🔍 **Arama**: Lunr.js ile istemci taraflı tam metin arama
- 📱 **Responsive Tasarım**: Mobil uyumlu arayüz
- 🛒 **E-Ticaret Entegrasyonu**: Damla Yayınevi ve diğer platformlara satın alma linkleri

---

## 🛠️ Teknoloji Yığını

| Teknoloji | Kullanım Amacı |
|-----------|----------------|
| **Jekyll** | Statik site üreticisi |
| **Liquid** | Şablon motoru |
| **Bootstrap 4.6** | CSS framework |
| **jQuery 3.6** | JavaScript kütüphanesi |
| **Lunr.js** | İstemci taraflı arama |
| **Tiny Slider** | Carousel/Slider bileşeni |
| **Plyr.js** | Ses oynatıcı |
| **Font Awesome 5** | İkon kütüphanesi (lokal) |
| **Lora Font** | Tipografi (lokal) |

---

## 📁 Proje Yapısı

```
mihrabadyayinlari/
├── _authors/          # Yazar profilleri (Markdown)
├── _books/            # Kitap içerikleri (Markdown)
├── _data/             # Veri dosyaları (JSON)
├── _includes/         # Yeniden kullanılabilir HTML parçaları
├── _layouts/          # Sayfa şablonları
├── _pages/            # Statik sayfalar
├── _persons/          # Şahsiyet profilleri (Kültür Mirası)
├── _posts/            # Blog yazıları
├── assets/
│   ├── css/           # Stil dosyaları
│   ├── images/        # Görseller
│   ├── js/            # JavaScript dosyaları
│   └── musics/        # Ses dosyaları (MP3)
├── _config.yml        # Jekyll yapılandırması
├── Gemfile            # Ruby bağımlılıkları
└── index.html         # Ana sayfa
```

---

## 🚀 Kurulum

### Gereksinimler

- Ruby >= 2.5.0
- Bundler gem
- Jekyll >= 4.0

### Adımlar

1. **Depoyu klonlayın:**
   ```bash
   git clone https://github.com/username/mihrabadyayinlari.git
   cd mihrabadyayinlari
   ```

2. **Bağımlılıkları yükleyin:**
   ```bash
   bundle install
   ```

3. **Geliştirme sunucusunu başlatın:**
   ```bash
   bundle exec jekyll serve
   ```

4. **Tarayıcıda açın:**
   ```
   http://localhost:4000
   ```

### Windows için Hızlı Kurulum

```powershell
# install.sh dosyasını çalıştırın
.\install.sh

# veya start.sh ile sunucuyu başlatın
.\start.sh
```

---

## 📝 İçerik Yönetimi

### Yeni Kitap Ekleme

`_books/` klasörüne aşağıdaki formatta bir Markdown dosyası ekleyin:

```yaml
---
layout: book
title: "Kitap Adı"
authors: ["yazar-key"]
image: assets/images/ean/BARCODE.jpg
categories: ["Kategori1", "Kategori2"]
tags: ["etiket1", "etiket2"]
previewpage: true
featured: true

# Kitap özellikleri
ean: 9786056725180
languages: ["Türkçe"]
page: 200
size: "13,5x21cm"
publishnumber: 28
cover: "Karton"

# Satın alma linkleri
damlayayinevi: "https://..."
---

Kitap açıklaması buraya yazılır.
```

### Yeni Yazar Ekleme

`_authors/` klasörüne aşağıdaki formatta bir dosya ekleyin:

```yaml
---
layout: author
title: Yazar Adı
key: yazar-key
image: assets/images/avatar/yazar-key.jpg
---

Yazar biyografisi buraya yazılır.
```

### Yeni Blog Yazısı Ekleme

`_posts/` klasörüne `YYYY-MM-DD-baslik.md` formatında dosya ekleyin:

```yaml
---
layout: post
title: "Yazı Başlığı"
authors: []
categories: [Kategori]
image: assets/images/posts/gorsel.jpg
tags: []
featured: false
---

Yazı içeriği buraya yazılır.
```

---

## ⚙️ Yapılandırma

`_config.yml` dosyasındaki önemli ayarlar:

```yaml
# Site bilgileri
name: 'Mihrabad Yayınları'
language: "tr"

# Sosyal medya
twitter: 'https://twitter.com/mihrabadyayin'
facebook: 'https://www.facebook.com/mihrabadyayin'
instagram: 'https://instagram.com/mihrabadyayin'

# E-ticaret
buyout:
  enabled: true
  damlayayinevi: true

# Ön okuma özelliği
pagepreview:
  enabled: true
  prefix: 'https://cdn.e-damla.com.tr/...'

# Analitik
google_analytics: 'G-TH2P889EDC'
```

---

## 🎨 Özelleştirme

### Tema Renkleri

Ana renkler `assets/css/theme.css` dosyasında tanımlıdır:

- **Ana Renk (Primary)**: `#03a87c` (Yeşil)
- **Vurgu Rengi**: `#ff0002` (Kırmızı)
- **Footer Arka Plan**: `#032957` (Koyu Mavi)

### Slider Düzenleme

`_data/slider.yml` dosyasını düzenleyerek ana sayfa slider'ını özelleştirebilirsiniz.

```yaml
- title: "Slide Başlığı"
  img: "assets/images/slides/1.jpg"
  mobile-img: "assets/images/slides/1m.jpg"
  href: "kitaplar/"
  target: ""
```

---

## 📊 Jekyll Koleksiyonları

| Koleksiyon | Klasör | URL Yapısı |
|------------|--------|------------|
| Kitaplar | `_books/` | `/kitaplar/:title` |
| Yazarlar | `_authors/` | `/yazarlar/:title` |
| Şahsiyetler | `_persons/` | `/sahsiyetler/:title` |
| Çizerler | `_illustrators/` | `/cizerler/:title` |
| Çevirmenler | `_translators/` | `/cevirmenler/:title` |
| Blog | `_posts/` | `/:title/` |

---

## 🔌 Eklentiler

Projede kullanılan Jekyll eklentileri:

- `jekyll-feed` - RSS feed oluşturma
- `jekyll-sitemap` - Sitemap.xml oluşturma
- `jekyll-paginate` - Sayfalama
- `jekyll-seo-tag` - SEO meta etiketleri
- `jekyll-archives` - Arşiv sayfaları
- `jekyll-figure` - Resim figürleri
- `jekyll-gist` - GitHub Gist entegrasyonu

---

## 🌐 Dağıtım

Site, GitHub Pages veya herhangi bir statik hosting servisinde yayınlanabilir.

### GitHub Pages

1. Depoyu GitHub'a push edin
2. Repository Settings > Pages bölümünden kaynağı seçin
3. CNAME dosyasında özel domain tanımlayın

### Manuel Derleme

```bash
JEKYLL_ENV=production bundle exec jekyll build
```

Derlenen dosyalar `_site/` klasöründe oluşturulur.

---

## 📞 İletişim

**Mihrabad Yayınları**

- 📍 Prof. Kazım İsmail Gürkan Cad. No:8, Cağaloğlu - Fatih / İstanbul
- 📞 (0212) 514 28 28
- 📧 iletisim@mihrabadyayinlari.com

---

## 📄 Lisans

Bu proje Mihrabad Yayınları'na aittir. Damla Yayınevi'nin tescilli markasıdır.

---

<p align="center">
  <sub>Kültür, sanat, tarih ve edebiyat alanlarında medeniyet eksenli yayıncılık.</sub>
</p>
