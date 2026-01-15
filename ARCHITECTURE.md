# Mihrabad Yayınları - Mimari Dokümantasyonu

Bu dokümantasyon, Mihrabad Yayınları web sitesinin teknik mimarisini, algoritma yapılarını ve veri akışını detaylı olarak açıklamaktadır.

---

## 📐 Genel Mimari

```
┌─────────────────────────────────────────────────────────────────┐
│                        KULLANICI KATMANI                        │
│                    (Web Tarayıcı / Mobil)                       │
└─────────────────────────────────────────────────────────────────┘
                                │
                                ▼
┌─────────────────────────────────────────────────────────────────┐
│                      SUNUM KATMANI (HTML/CSS/JS)                │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────────┐    │
│  │ Bootstrap│  │ jQuery   │  │ Lunr.js  │  │ Tiny Slider  │    │
│  │   4.6    │  │  3.6.0   │  │ (Arama)  │  │  (Carousel)  │    │
│  └──────────┘  └──────────┘  └──────────┘  └──────────────┘    │
└─────────────────────────────────────────────────────────────────┘
                                │
                                ▼
┌─────────────────────────────────────────────────────────────────┐
│                   ŞABLON MOTORU (Liquid)                        │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │  Layouts    │  Includes   │  Collections  │  Variables  │   │
│  └─────────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────────┘
                                │
                                ▼
┌─────────────────────────────────────────────────────────────────┐
│                    JEKYLL BUILD SİSTEMİ                         │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────────┐    │
│  │ Markdown │  │  YAML    │  │  Sass    │  │   Plugins    │    │
│  │ İşleme   │  │  Parse   │  │ Derleme  │  │   Sistem     │    │
│  └──────────┘  └──────────┘  └──────────┘  └──────────────┘    │
└─────────────────────────────────────────────────────────────────┘
                                │
                                ▼
┌─────────────────────────────────────────────────────────────────┐
│                       VERİ KATMANI                              │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │  _books/  │  _authors/  │  _persons/  │  _posts/        │   │
│  │   (75)    │    (27)     │    (48)     │    (35)         │   │
│  └─────────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────────┘
```

---

## 🔄 Veri Akış Diyagramı

### Build Süreci

```
                    ┌─────────────┐
                    │   Kaynak    │
                    │  Dosyalar   │
                    └──────┬──────┘
                           │
           ┌───────────────┼───────────────┐
           │               │               │
           ▼               ▼               ▼
    ┌─────────────┐ ┌─────────────┐ ┌─────────────┐
    │  Markdown   │ │    YAML     │ │    Sass     │
    │   (.md)     │ │ Front Matter│ │   (.scss)   │
    └──────┬──────┘ └──────┬──────┘ └──────┬──────┘
           │               │               │
           ▼               ▼               ▼
    ┌─────────────┐ ┌─────────────┐ ┌─────────────┐
    │  Kramdown   │ │   Jekyll    │ │    Sass     │
    │   Parser    │ │   Parser    │ │  Compiler   │
    └──────┬──────┘ └──────┬──────┘ └──────┬──────┘
           │               │               │
           └───────────────┼───────────────┘
                           │
                           ▼
                    ┌─────────────┐
                    │   Liquid    │
                    │  Rendering  │
                    └──────┬──────┘
                           │
                           ▼
                    ┌─────────────┐
                    │   _site/    │
                    │   (Output)  │
                    └─────────────┘
```

---

## 📊 Koleksiyon Mimarisi

### Koleksiyon İlişkileri

```
                    ┌──────────────┐
                    │    BOOKS     │
                    │   (Kitap)    │
                    └───────┬──────┘
                            │
        ┌───────────────────┼───────────────────┐
        │                   │                   │
        ▼                   ▼                   ▼
┌──────────────┐    ┌──────────────┐    ┌──────────────┐
│   AUTHORS    │    │ ILLUSTRATORS │    │ TRANSLATORS  │
│   (Yazar)    │    │   (Çizer)    │    │ (Çevirmen)   │
└──────────────┘    └──────────────┘    └──────────────┘

        │
        │ (İlişkili içerik)
        ▼
┌──────────────┐    ┌──────────────┐    ┌──────────────┐
│    POSTS     │    │   PERSONS    │    │   SLIDES     │
│   (Blog)     │    │ (Şahsiyet)   │    │  (Slider)    │
└──────────────┘    └──────────────┘    └──────────────┘
```

### Koleksiyon Yapılandırması (_config.yml)

```yaml
collections:
  books:
    output: true
    permalink: /kitaplar/:title
    sort_by: publishnumber
  authors:
    output: true
    permalink: /yazarlar/:title
  persons:
    output: true
    permalink: /sahsiyetler/:title
  slides:
    output: false
    sort_by: order
```

---

## 🧩 Layout Hiyerarşisi

```
                    ┌─────────────────┐
                    │    default.html │
                    │  (Ana Şablon)   │
                    └────────┬────────┘
                             │
        ┌────────────────────┼────────────────────┐
        │                    │                    │
        ▼                    ▼                    ▼
┌───────────────┐    ┌───────────────┐    ┌───────────────┐
│   book.html   │    │  author.html  │    │   post.html   │
│   (Kitap)     │    │   (Yazar)     │    │   (Blog)      │
└───────────────┘    └───────────────┘    └───────────────┘
        │                    │
        │                    │
        ▼                    ▼
┌───────────────┐    ┌───────────────┐
│  person.html  │    │   page.html   │
│  (Şahsiyet)   │    │   (Sayfa)     │
└───────────────┘    └───────────────┘
```

### Default Layout Yapısı

```html
<!DOCTYPE html>
<html>
<head>
    <!-- Meta bilgileri -->
    <!-- CSS dosyaları -->
    <!-- Tracking header -->
</head>
<body>
    <!-- Navbar -->
    <nav class="topnav navbar">
        {% include menu-header.html %}
        {% include search-lunr.html %}
    </nav>
    
    <!-- İçerik -->
    <main class="site-content">
        {{ content }}
    </main>
    
    <!-- Footer -->
    {% include footer.html %}
    
    <!-- Scripts -->
    {% include tracking-footer.html %}
</body>
</html>
```

---

## 🔍 Arama Algoritması (Lunr.js)

### İndeksleme Süreci

```javascript
// 1. Doküman oluşturma
var documents = [
    // Tüm sayfalar
    {% for page in site.pages %}
    {
        "id": {{ counter }},
        "url": "{{ page.url }}",
        "title": "{{ page.title }}",
        "body": "{{ page.content | strip_html }}"
    },
    {% endfor %}
    // Tüm postlar
    {% for page in site.posts %}
    {
        "id": {{ counter }},
        "url": "{{ page.url }}",
        "title": "{{ page.title }}",
        "body": "{{ page.content | strip_html }}"
    }
    {% endfor %}
];

// 2. Lunr indeksi oluşturma
var idx = lunr(function () {
    this.ref('id');
    this.field('title');  // Başlık alanı
    this.field('body');   // İçerik alanı
    
    documents.forEach(function (doc) {
        this.add(doc);
    }, this);
});

// 3. Arama fonksiyonu
function lunr_search(term) {
    var results = idx.search(term);
    // Sonuçları göster
}
```

### Arama Akışı

```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│  Kullanıcı  │────▶│   Arama     │────▶│   Lunr.js   │
│   Girişi    │     │   Formu     │     │   Index     │
└─────────────┘     └─────────────┘     └──────┬──────┘
                                               │
                                               ▼
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│   Modal     │◀────│   Sonuç     │◀────│   Eşleşme   │
│   Gösterim  │     │  Listesi    │     │  Algoritma  │
└─────────────┘     └─────────────┘     └─────────────┘
```

---

## 🎠 Carousel Algoritması

### Ana Sayfa Carousel (mainpage-carousel.html)

```javascript
// Tab ve Carousel Yönetimi
document.addEventListener('DOMContentLoaded', function() {
    
    // 1. Tab Değişim Algoritması
    tabLinks.forEach(link => {
        link.addEventListener('click', function(e) {
            e.preventDefault();
            
            // Aktif tab'ı güncelle
            tabLinks.forEach(l => l.classList.remove('active'));
            this.classList.add('active');
            
            // Panel'i göster
            const targetPanel = document.getElementById(targetId);
            targetPanel.classList.add('active');
            
            // Carousel'i başlat
            initCarousel(targetPanel);
        });
    });
    
    // 2. Carousel Sayfalama Algoritması
    function initCarousel(panel) {
        const items = track.querySelectorAll('.carousel-item');
        const itemsPerPage = 8;  // 4 sütun x 2 satır
        const totalPages = Math.ceil(items.length / itemsPerPage);
        
        function showPage(page) {
            const start = page * itemsPerPage;
            const end = start + itemsPerPage;
            
            items.forEach((item, index) => {
                item.style.display = 
                    (index >= start && index < end) ? 'flex' : 'none';
            });
        }
    }
    
    // 3. Swipe Desteği
    track.addEventListener('touchstart', function(e) {
        touchStartX = e.changedTouches[0].screenX;
    });
    
    track.addEventListener('touchend', function(e) {
        touchEndX = e.changedTouches[0].screenX;
        handleSwipe();
    });
});
```

### Kitap Filtreleme Mantığı

```liquid
<!-- Yeni Çıkanlar: publishnumber'a göre sırala -->
{% assign sorted_books = site.books | sort: "publishnumber" | reverse %}

<!-- Yakında Çıkacaklar: soon: true olanlar -->
{% assign soon_books = site.books | where: "soon", true %}

<!-- Çok Satanlar: bestseller: true olanlar -->
{% for book in site.books %}
    {% if book.bestseller == true %}
        <!-- Göster -->
    {% endif %}
{% endfor %}
```

---

## 📚 Kitap-Yazar İlişki Algoritması

### Yazarın Kitaplarını Bulma

```liquid
<!-- book.html layout'unda -->
{% assign bookarray = "" | split: ',' %}

{% for book in site.books %}
    {% for bookauthor in page.authors %}
        {% if book.authors contains bookauthor %}
            {% assign bookarray = bookarray | push: book %}
        {% endif %}
    {% endfor %}
{% endfor %}

<!-- Duplicate'leri temizle -->
{% assign uniqbookArray = bookarray | uniq %}
```

### Yazar Bilgisini Çekme

```liquid
<!-- Kitap sayfasında yazar bilgisi -->
{% for bookauthor in book.authors %}
    {% assign siteauthor = site.authors | where:"key", bookauthor | first %}
    <a href="{{ siteauthor.url }}">{{ siteauthor.title }}</a>
{% endfor %}
```

---

## 🎵 Müzik Oynatıcı Mimarisi

### Veri Yapısı

```yaml
# _persons/ içindeki dosyada
music: true
musics: [
    ["Furkan suresi 21-32. ayetler", "05:19", "22-hafiz-kani-karaca/1"],
    ["Kadr suresi", "01:10", "22-hafiz-kani-karaca/2"]
]
```

### JavaScript Playlist Oluşturma

```javascript
var playlist = [
    {% for music in page.musics %}
    {
        "track": {{ forloop.index }},
        "name": "{{ music[0] }}",
        "duration": "{{ music[1] }}",
        "file": "{{ music[2] }}"
    },
    {% endfor %}
];

// Plyr.js ile oynatma
const player = plyr.setup('#audio1');
```

---

## 🖼️ Lazy Loading Algoritması

```javascript
// lazyload.js
document.addEventListener("DOMContentLoaded", function() {
    var lazyImages = [].slice.call(
        document.querySelectorAll("img.lazy")
    );

    if ("IntersectionObserver" in window) {
        let lazyImageObserver = new IntersectionObserver(
            function(entries, observer) {
                entries.forEach(function(entry) {
                    if (entry.isIntersecting) {
                        let lazyImage = entry.target;
                        lazyImage.src = lazyImage.dataset.src;
                        lazyImage.classList.remove("lazy");
                        lazyImageObserver.unobserve(lazyImage);
                    }
                });
            }
        );

        lazyImages.forEach(function(lazyImage) {
            lazyImageObserver.observe(lazyImage);
        });
    }
});
```

---

## 📜 Scroll Davranışı Algoritması

### Navbar Gizleme/Gösterme

```javascript
// theme.js
var didScroll;
var lastScrollTop = 0;
var delta = 5;
var navbarHeight = $('nav').outerHeight();

function hasScrolled() {
    var st = $(this).scrollTop();
    
    // Delta kontrolü
    if(Math.abs(lastScrollTop - st) <= delta)
        return;

    // Aşağı kaydırma - navbar'ı gizle
    if (st > lastScrollTop && st > navbarHeight) {
        $('nav').removeClass('nav-down').addClass('nav-up');
        $('.nav-up').css('top', -navbarHeight + 'px');
    } 
    // Yukarı kaydırma - navbar'ı göster
    else {
        $('nav').removeClass('nav-up').addClass('nav-down');
        $('.nav-down').css('top', '0px');
    }

    lastScrollTop = st;
}

setInterval(function() {
    if (didScroll) {
        hasScrolled();
        didScroll = false;
    }
}, 250);
```

---

## 🔗 URL Yapısı ve Routing

### Permalink Konfigürasyonu

```yaml
# _config.yml
permalink: /:title/

collections:
  books:
    permalink: /kitaplar/:title
  authors:
    permalink: /yazarlar/:title
  persons:
    permalink: /sahsiyetler/:title
```

### URL Örnekleri

| İçerik Tipi | Kaynak Dosya | Oluşan URL |
|-------------|--------------|------------|
| Kitap | `_books/2021-09-01-ismail-saib-sencer.md` | `/kitaplar/ismail-saib-sencer` |
| Yazar | `_authors/mehmet-ali-sari.md` | `/yazarlar/mehmet-ali-sari` |
| Blog | `_posts/2021-12-09-cin-kampinda.md` | `/cin-kampinda/` |
| Sayfa | `_pages/hakkimizda.md` | `/hakkimizda` |

---

## 📡 RSS Feed Yapısı

```yaml
# _config.yml
feed:
  collections:
    books:
      path: "/kitaplar/feed.xml"
    authors:
      path: "/yazarlar/feed.xml"
    persons:
      path: "/sahsiyetler/feed.xml"
```

---

## 🔐 SEO Optimizasyonu

### Jekyll SEO Tag Kullanımı

```html
<!-- default.html -->
{% seo %}

<!-- Oluşturulan çıktı -->
<title>Sayfa Başlığı | Mihrabad Yayınları</title>
<meta name="description" content="...">
<meta property="og:title" content="...">
<meta property="og:description" content="...">
<meta property="og:image" content="...">
<meta name="twitter:card" content="summary_large_image">
```

---

## 📊 Performans Optimizasyonları

### 1. CSS Sıkıştırma

```yaml
# _config.yml
sass:
  sass_dir: _sass
  style: compressed
```

### 2. Lazy Loading

```yaml
# _config.yml
lazyimages: "enabled"
```

### 3. CDN Kullanımı

```html
<!-- Harici kütüphaneler CDN'den yüklenir -->
<script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/bootstrap@4.6.0/dist/js/bootstrap.min.js"></script>
<link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.15.4/css/all.css">
```

---

## 🧪 Build ve Deploy Süreci

```
┌─────────────┐
│   Kaynak    │
│   Kod       │
└──────┬──────┘
       │
       ▼
┌─────────────┐     ┌─────────────┐
│   Jekyll    │────▶│   _site/    │
│   Build     │     │   Çıktı     │
└─────────────┘     └──────┬──────┘
                           │
       ┌───────────────────┼───────────────────┐
       │                   │                   │
       ▼                   ▼                   ▼
┌─────────────┐    ┌─────────────┐    ┌─────────────┐
│   GitHub    │    │   Netlify   │    │    FTP      │
│   Pages     │    │             │    │   Upload    │
└─────────────┘    └─────────────┘    └─────────────┘
```

---

## 📝 Sonuç

Mihrabad Yayınları web sitesi, Jekyll'in güçlü koleksiyon sistemi ve Liquid şablon motoru üzerine kurulu modüler bir mimari kullanmaktadır. Bu yapı:

- **Ölçeklenebilirlik**: Yeni içerik türleri kolayca eklenebilir
- **Bakım Kolaylığı**: Şablonlar ve içerikler ayrı tutulur
- **Performans**: Statik dosya çıktısı ile hızlı yükleme
- **SEO Dostu**: Temiz URL yapısı ve meta etiketleri

sağlamaktadır.
