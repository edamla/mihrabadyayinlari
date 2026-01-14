# Mihrabad Yayınları - Stil ve Tasarım Dokümantasyonu

Bu dokümantasyon, Mihrabad Yayınları web sitesinin CSS sınıflarını, renk paletini ve tasarım sistemini detaylı olarak açıklamaktadır.

---

## 🎨 Renk Paleti

### Ana Renkler

| Renk Adı | Hex Kodu | RGB | Kullanım Alanı |
|----------|----------|-----|----------------|
| **Primary Green** | `#03a87c` | rgb(3, 168, 124) | Linkler, butonlar, vurgu |
| **Accent Red** | `#ff0002` | rgb(255, 0, 2) | Tab alt çizgi, footer başlıklar |
| **Navy Blue** | `#032957` | rgb(3, 41, 87) | Footer arka plan, carousel butonları |
| **Humayun Gold** | `#ffc107` | rgb(255, 193, 7) | Özel vurgu sınıfı |

### Yardımcı Renkler

| Renk Adı | Hex Kodu | Kullanım |
|----------|----------|----------|
| Secondary | `#7832e2` | İkincil vurgu |
| Success | `#03a87c` | Başarı durumları |
| Info | `#09ebaf` | Bilgi mesajları |
| Warning | `#ffde03` | Uyarı mesajları |
| Danger | `#ea2f65` | Hata durumları |
| Light | `#f8f9fa` | Açık arka plan |
| Dark | `#212529` | Koyu metin |
| Purple | `#ad6edd` | Dekoratif |
| Salmon | `#ff977a` | Dekoratif |
| Cyan | `#35bdff` | Dekoratif |
| Gray | `#ced4da` | Kenarlıklar |
| Indigo | `#502c6c` | Dekoratif |
| Orange | `#fbb500` | Vurgu |
| Lightblue | `#e8f3ec` | Açık arka plan |

### Renk Kullanım Örnekleri

```css
/* Ana link rengi */
a {
    color: #03a87c;
}

/* Footer arka plan */
footer {
    background-color: #032957;
}

/* Vurgu çizgisi */
.tabs-link.active {
    border-bottom-color: #ff0002;
}
```

---

## 📝 Tipografi

### Font Stratejisi

Site iki farklı font ailesi kullanmaktadır:

| Font | Kullanım Alanı |
|------|----------------|
| **Vogun** | Başlıklar, menüler, butonlar, arayüz elementleri |
| **Minion Pro** | Paragraflar, uzun metinler, kitap içerikleri, biyografiler |

### Font Dosyaları Konumu

```
assets/font/
├── vogun/
│   ├── Vogun-Medium.woff
│   ├── Vogun-Medium.ttf
│   └── style.css
│
└── minion-pro/
    ├── MinionPro-Regular.woff
    ├── MinionPro-It.woff
    ├── MinionPro-Medium.woff
    ├── MinionPro-Bold.woff
    └── style.css
```

#### CSS Değişkenleri

```css
:root {
    --font-vogun: 'Vogun', Georgia, 'Times New Roman', Times, serif;
    --font-minion: 'Minion Pro', Georgia, 'Times New Roman', Times, serif;
}
```

### Font Kullanımı

```css
/* Başlıklar - Vogun */
h1, h2, h3, h4, h5, h6 {
    font-family: 'Vogun', Georgia, 'Times New Roman', serif;
}

/* Menüler ve UI - Vogun */
.btn, .nav-link, .dropdown-item, .badge, label {
    font-family: 'Vogun', Georgia, serif;
}

/* Paragraflar ve içerik - Minion Pro */
p, .content-text, .biography, .book-description, .excerpt {
    font-family: 'Minion Pro', Lora, Georgia, serif;
}

/* Makale içeriği - Minion Pro */
article {
    font-family: 'Minion Pro', Lora, Georgia, serif;
    font-size: 1.1rem;
    line-height: 1.86;
}

/* Makale başlığı - Vogun */
.article-headline {
    font-family: 'Vogun', Georgia, Times, 'Times New Roman', serif;
    font-size: 3.2rem;
    font-weight: 400;
    line-height: 1.15;
}
```

### Font Ağırlıkları

#### Vogun
| Ağırlık | Değer | Kullanım |
|---------|-------|----------|
| Medium | 500 | Tüm kullanımlar |

#### Minion Pro
| Ağırlık | Değer | Kullanım |
|---------|-------|----------|
| Regular | 400 | Normal metin |
| Medium | 500 | Orta vurgu |
| Semibold | 600 | Alt başlıklar |
| Bold | 700 | Güçlü vurgu |

### Font Boyutları

| Element | Boyut | Satır Yüksekliği |
|---------|-------|------------------|
| Body | 16px (1rem) | 1.5 |
| Article | 1.1rem | 1.86 |
| Article Headline | 3.2rem | 1.15 |
| Navbar Link | 0.93rem | - |
| Display-3 | 4.5rem | - |
| Display-4 | 3.5rem | - |
| H6 | 1rem | - |

### Responsive Font Boyutları

```css
/* Büyük ekranlar (1920px+) */
@media (min-width: 1920px) {
    html { font-size: 17px; }
    article { font-size: 1.24rem; }
    h6, .h6 { font-size: 1.1rem; }
}

/* Tablet (max 991px) */
@media (max-width: 991.98px) {
    .display-3 { font-size: 3.5rem; }
    .display-4 { font-size: 3rem; }
}

/* Mobil (max 767px) */
@media (max-width: 767.98px) {
    .display-3 { font-size: 2rem; }
}
```

---

## 🧱 Layout Sınıfları

### Container Sistemi

```css
/* Bootstrap container genişletmesi */
@media (min-width: 1920px) {
    .container, .container-lg {
        width: 1280px;
        max-width: 1280px;
    }
}
```

### Özel Layout Sınıfları

| Sınıf | Açıklama |
|-------|----------|
| `.tofront` | `z-index: 1` ile öne çıkarma |
| `.full-width` | Tam genişlik (viewport) |
| `.site-content` | Ana içerik alanı (`margin-top: 50px`) |
| `.remove-site-content-margin` | Üst margin'i kaldır |
| `.add-site-content-margin` | Üst margin ekle |

### Spacing Sınıfları

```css
.mb-2rem { margin-bottom: 2rem; }
.mt-neg5 { margin-top: -5rem; }
.ml-neg5 { margin-left: -5rem; }
.sticky-top-offset { top: 70px; }
```

### Yükseklik Sınıfları

```css
@media (min-width: 768px) {
    .h-md-100-v { height: 100vh; }
    .h-md-100 { height: 100vh; }
}

@media (min-width: 1200px) {
    .h-xl-300 { height: 300px; }
    .h-max-380 { max-height: 380px; }
}
```

---

## 🔘 Buton Stilleri

### Temel Buton

```css
.btn {
    padding: 0.35rem 1.1rem;
    font-size: 1rem;
    line-height: 1.6;
    border-radius: 0.25rem;
    position: relative;
}

.btn:hover, .btn:focus {
    outline: 0 !important;
}
```

### Buton Boyutları

| Sınıf | Padding | Font Size |
|-------|---------|-----------|
| `.btn` | 0.35rem 1.1rem | 1rem |
| `.btn-lg` | 0.65rem 2rem | 1.15rem |
| `.btn-sm` | 0.15rem 0.7rem | 0.875rem |

### Yuvarlak Buton

```css
.btn-round {
    border-radius: 30px !important;
}
```

### Renk Varyantları

```css
/* Link butonları */
.btn-link.btn-primary { color: #03a87c; }
.btn-link.btn-secondary { color: #7832e2; }
.btn-link.btn-success { color: #03a87c; }
.btn-link.btn-info { color: #09ebaf; }
.btn-link.btn-warning { color: #ffde03; }
.btn-link.btn-danger { color: #ea2f65; }
.btn-link.btn-dark { color: #212529; }
.btn-link.btn-purple { color: #ad6edd; }
.btn-link.btn-orange { color: #fbb500; }

/* Beyaz buton */
.btn-white {
    background-color: #fff;
}
```

---

## 🧭 Navbar Stilleri

### Ana Navbar

```css
.navbar {
    transition: top 0.2s ease-in-out;
    font-weight: 400;
}

.navbar-brand {
    margin-right: 2rem;
    font-size: 1.55rem;
    font-family: Georgia, "Times New Roman", serif;
}

.navbar-light .navbar-nav .nav-link {
    color: rgba(0, 0, 0, 0.5);
    font-size: 0.93rem;
}

.nav-link {
    font-weight: bold;
}
```

### Highlight Link

```css
.navbar .highlight .nav-link {
    color: #03a87c !important;
    border: 1px solid #03a87c;
    padding: 0.3rem 1rem;
    border-radius: 3px;
    font-size: 0.93rem;
}

.navbar .highlight .nav-link:hover {
    background: #03a87c;
    color: #fff !important;
}
```

### Scroll Davranışı

```css
/* Navbar gizleme/gösterme animasyonu */
.nav-up {
    top: -70px; /* Navbar yüksekliği kadar yukarı */
}

.nav-down {
    top: 0px;
}
```

---

## 🃏 Kart Stilleri

### Temel Kart

```css
.card a:hover {
    text-decoration: none;
    color: #03a87c;
}
```

### Tarih Badge

```css
.card .date {
    position: absolute;
    top: 20px;
    right: 20px;
    z-index: 1;
    background: #ea2f65;
    width: 55px;
    height: 55px;
    padding: 12.5px 0;
    border-radius: 100%;
    color: #FFFFFF;
    font-weight: 700;
    text-align: center;
}

.card .date .day {
    font-size: 16px;
    line-height: 1;
}

.card .date .month {
    font-size: 11px;
    text-transform: uppercase;
}
```

### Kitap Kutusu

```css
.kitap-kutu {
    background: #f5f5f5;
    margin-bottom: 4vh;
}
```

---

## 📖 Kitap Görselleri

### Kitap Gölgesi

```css
.book img {
    filter: drop-shadow(2px 2px 7px gray);
}

.cover-shadow {
    filter: drop-shadow(0px 0px 4px rgba(0, 0, 0, 0.597));
}
```

### Kapak Görselleri

```css
.cover-images {
    width: 75%;
    margin-bottom: 2vh;
}

.slider-image {
    max-height: 30vh;
}
```

---

## 🎠 Carousel Stilleri

### Ana Carousel

```css
.carousel-item {
    height: 50vh;
}

.carousel-item img {
    position: absolute;
    top: 0;
    left: 0;
    min-height: 50vh;
}

.carousel-indicators li {
    width: 40px;
    height: 8px;
}

.carousel-control-prev-icon,
.carousel-control-next-icon {
    width: 40px;
    height: 40px;
}

.slider {
    padding-left: 0 !important;
    padding-right: 0 !important;
}
```

### Tabbed Carousel (Hachette Style)

```css
.tabbed-carousel-section {
    padding: 4rem 0;
    background: #fff;
    overflow: hidden;
}

/* Tab navigasyonu */
.tabs-list {
    display: flex;
    justify-content: center;
    list-style: none;
    padding: 0;
    margin: 0 0 3rem 0;
    border-bottom: 1px solid #eee;
    gap: 2rem;
}

.tabs-link {
    display: block;
    padding: 0 0 1rem 0;
    font-size: 1.1rem;
    font-weight: 700;
    color: #999;
    text-decoration: none;
    border-bottom: 3px solid transparent;
    margin-bottom: -1px;
    transition: all 0.3s ease;
    text-transform: uppercase;
    letter-spacing: 0.5px;
}

.tabs-link.active {
    color: #032957;
    border-bottom-color: #ff0002;
}

/* Grid tabanlı carousel */
.carousel-track {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-template-rows: repeat(2, auto);
    gap: 1.5rem;
}

/* Carousel öğesi */
.carousel-item {
    background: #f3f3f3;
    border-radius: 12px;
    height: 280px;
    display: flex;
    justify-content: center;
    align-items: center;
    transition: all 0.3s ease;
    padding: 20px;
}

.carousel-item:hover {
    transform: translateY(-5px);
    box-shadow: 0 10px 25px rgba(0, 0, 0, 0.05);
}

/* Carousel butonları */
.carousel-btn {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    width: 50px;
    height: 50px;
    border: none;
    background: #fff;
    color: #032957;
    border-radius: 50%;
    cursor: pointer;
    box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
    z-index: 20;
}

.carousel-btn:hover:not(:disabled) {
    background: #032957;
    color: #fff;
    transform: translateY(-50%) scale(1.1);
}

/* Pagination noktaları */
.pagination-btn {
    width: 10px;
    height: 10px;
    border: none;
    border-radius: 50%;
    background: #ccc;
    cursor: pointer;
    transition: all 0.3s ease;
}

.pagination-btn.active {
    background: #333;
    transform: scale(1.2);
}
```

---

## 📰 Blog/Post Stilleri

### Post Thumbnail

```css
.post-thumb-container {
    display: block;
    width: 180px;
    height: 140px;
    min-width: 180px;
    min-height: 140px;
    overflow: hidden;
    border-radius: 4px;
}

.post-thumb-container img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    object-position: center top;
}
```

### Post Kart Düzeni

```css
.post-card-row {
    display: flex;
    align-items: flex-start;
}

.post-card-row .post-thumb-col {
    flex: 0 0 180px;
    width: 180px;
}

.post-card-row .post-content-col {
    flex: 1;
    padding-left: 15px;
}
```

---

## 📝 Makale Stilleri

### Makale İçeriği

```css
article {
    font-size: 1.1rem;
    line-height: 1.86;
    font-family: Lora;
}

article p, article pre, article figure, 
article img, article blockquote, 
article iframe, article embed {
    margin-bottom: 2rem;
}

/* İlk harf büyütme (Drop Cap) */
article:first-letter {
    float: left;
    font-size: 5em;
    line-height: 1;
    margin: 0 0.2em 0 0;
    vertical-align: top;
}
```

### Alıntı (Blockquote)

```css
article blockquote {
    padding-left: 40px;
    margin-left: 0px;
    font-style: italic;
    position: relative;
}

article blockquote:before {
    content: """;
    font-family: Georgia;
    font-size: 8rem;
    margin: -1rem 2rem 0 -3.9rem;
    position: absolute;
    opacity: 1;
    float: left;
    line-height: 1;
}
```

### Başlıklar

```css
article h1, article h2, article h3, 
article h4, article h5, article h6 {
    margin-bottom: 2rem;
    margin-top: 2rem;
    font-weight: 600;
}

.article-headline {
    font-family: Georgia, Times, "Times New Roman", serif;
    font-size: 3.2rem;
    font-weight: 400;
    line-height: 1.15;
    color: #222222;
}
```

---

## 🔔 Alert Stilleri

### Temel Alert

```css
.alert-primary {
    color: #fff;
    background-color: #03a87c;
    border-color: #03a87c;
}

.alert-danger {
    color: #fff;
    background-color: #ea2f65;
    border-color: #ea2f65;
}

.alert-warning {
    color: #fff;
    background-color: #ffde03;
    border-color: #ffde03;
}
```

### Alertbar (Alt Bildirim)

```css
.alertbar {
    box-shadow: 0 -3px 10px 0 rgba(0, 0, 0, 0.0785);
    position: fixed;
    bottom: 0;
    left: 0;
    background-color: #fff;
    width: 100%;
    padding: 20px 0;
    z-index: 1021;
    display: none;
}

/* Tablet ve altında gizle */
@media (max-width: 991.98px) {
    .alertbar {
        display: none !important;
    }
}
```

---

## 🎯 Icon Box Stilleri

```css
.iconbox {
    border: 1px solid;
    text-align: center;
    display: inline-block;
}

.iconbox.iconsmall {
    width: 40px;
    height: 40px;
    line-height: 40px;
    font-size: 1rem;
}

.iconbox.iconmedium {
    width: 60px;
    height: 60px;
    line-height: 60px;
    font-size: 1.8rem;
}

.iconbox.iconlarge {
    width: 80px;
    height: 80px;
    line-height: 80px;
    font-size: 2.2rem;
}
```

---

## 🔲 Overlay Stilleri

```css
.overlay {
    position: relative;
}

.overlay .container {
    position: relative;
}

.overlay:before {
    content: "";
    display: block;
    height: 100%;
    left: 0;
    top: 0;
    position: absolute;
    width: 100%;
}

.overlay-black:before {
    background-color: rgba(0, 0, 0, 0.5);
}

.overlay-blue:before {
    background-color: rgba(23, 29, 90, 0.5);
}

.overlay-red:before {
    background: linear-gradient(0deg, rgba(44, 44, 44, 0.2), rgba(224, 23, 3, 0.6));
}
```

---

## 📋 Liste Stilleri

### Numaralı Liste (Featured)

```css
ol.list-featured {
    counter-reset: my-awesome-counter;
    list-style: none;
    padding-left: 0;
}

ol.list-featured li {
    counter-increment: my-awesome-counter;
    display: flex;
    font-size: 0.8rem;
}

ol.list-featured li:before {
    content: "0" counter(my-awesome-counter);
    font-weight: bold;
    font-size: 2rem;
    margin-right: 0.5rem;
    font-family: Arial;
    line-height: 1;
    opacity: 0.1;
}
```

### Span Border

```css
.spanborder {
    border-bottom: 1px solid #e8f3ec;
    margin-bottom: 2rem;
}

.spanborder span {
    border-bottom: 1px solid rgba(0, 0, 0, 0.44);
    display: inline-block;
    padding-bottom: 20px;
    margin-bottom: -1px;
}
```

---

## 🎵 Müzik Oynatıcı Stilleri

```css
.audio-container {
    background-color: #c7c7c7;
    padding: 5vh;
    margin-bottom: 1vh;
    border-radius: 1vh;
}

.plItem {
    display: flex;
    font-size: x-large;
    padding: 1.5vh;
    color: #013b38;
}

.plTitle {
    margin-left: 2vh;
    text-transform: capitalize !important;
}

.plLength {
    margin-left: auto;
}

#plList li:hover {
    background-color: rgba(0, 0, 0, 0.1);
}

.plSel, .plSel:hover {
    background-color: rgba(0, 0, 0, 0.1);
    color: #fff;
    cursor: default !important;
}

#tracks a {
    border-radius: 3px;
    color: #013b38;
    cursor: pointer;
    display: inline-block;
    font-size: 2.3rem;
    height: 40px;
    line-height: 0.2;
    margin: 0 5px 30px;
    padding: 12px;
    text-decoration: none;
    transition: background 0.3s ease;
}

#tracks a:hover, #tracks a:active {
    background-color: rgba(0, 0, 0, 0.1);
    color: #fff;
}

#nowPlay {
    display: flex;
    font-size: x-large;
    margin: 2vh;
    color: #013b38;
}
```

---

## 🛒 Buyout (E-Ticaret) Stilleri

```css
.buyout {
    width: 100%;
    background: #E5E5E5;
    z-index: 3;
    border-radius: 0 0 3px 3px;
    float: left;
    position: relative;
    display: flex;
    flex-direction: row;
}

.buyout li {
    padding-left: 0.2vw;
    padding-right: 0.2vw;
    width: auto;
    height: 5vw;
    line-height: 5vw;
    font-size: 1.15vw;
    list-style: none;
}

.buyout li:nth-child(1) {
    margin-right: 0.5vw;
    padding-left: 0.5vw;
    padding-right: 0.5vw;
    background: #005e85;
    color: #FFF;
    border-radius: 0 0 0 2px;
}

.buyout li img {
    width: auto;
    height: 1.60vw;
    -webkit-filter: grayscale(100%);
    filter: grayscale(100%);
    opacity: 0.5;
}

.buyout li img:hover {
    -webkit-filter: none;
    filter: none;
    opacity: 1;
}
```

---

## 🦶 Footer Stilleri

```css
footer {
    margin-top: 50px;
    z-index: 1022;
    position: relative;
    background-color: #032957;
}

.footer-link {
    transition: all 0.3s ease;
}

.footer-link:hover {
    color: #ff0002 !important;
    padding-left: 5px;
}

.social-icon {
    transition: all 0.3s ease;
    display: inline-block;
}

.social-icon:hover {
    color: #ff0002 !important;
    transform: translateY(-3px);
}

footer a:hover {
    text-decoration: none;
}
```

---

## 🔍 Arama Stilleri

```css
.bd-search .form-control {
    font-size: 0.85rem;
    color: #999;
    border-radius: 30px;
    height: 35px;
    border: 3px solid #eee;
}

.lunrsearchresult .title {
    color: #d9230f;
}

.lunrsearchresult .url {
    color: silver;
}

.lunrsearchresult a {
    display: block;
    color: #777;
}

.lunrsearchresult a:hover,
.lunrsearchresult a:focus {
    text-decoration: none;
}

.lunrsearchresult a:hover .title {
    text-decoration: underline;
}
```

---

## 📱 Responsive Breakpoints

| Breakpoint | Min-Width | Açıklama |
|------------|-----------|----------|
| xs | 0 | Mobil (varsayılan) |
| sm | 576px | Küçük cihazlar |
| md | 768px | Tablet |
| lg | 992px | Masaüstü |
| xl | 1200px | Geniş ekran |
| xxl | 1920px | Çok geniş ekran |

### Responsive Örnekler

```css
/* Mobil (max 576px) */
@media (max-width: 576px) {
    .tabs-list { gap: 1rem; }
    .tabs-link { font-size: 0.9rem; }
    .carousel-item { padding: 15px; height: 200px; }
}

/* Tablet (max 768px) */
@media (max-width: 768px) {
    .carousel-track { grid-template-columns: repeat(2, 1fr); }
    .carousel-item { height: 240px; }
}

/* Masaüstü (max 992px) */
@media (max-width: 992px) {
    .carousel-track { grid-template-columns: repeat(3, 1fr); }
}

/* Geniş ekran (min 1920px) */
@media (min-width: 1920px) {
    html { font-size: 17px; }
    .container { width: 1280px; max-width: 1280px; }
}
```

---

## 🎭 Animasyonlar

### Fade In Animasyonu

```css
@keyframes fadeIn {
    from { 
        opacity: 0; 
        transform: translateY(10px); 
    }
    to { 
        opacity: 1; 
        transform: translateY(0); 
    }
}

.tabs-panel {
    animation: fadeIn 0.5s ease;
}
```

### Geçiş Efektleri

```css
/* Genel geçiş */
a, a:hover {
    transition: all 0.2s;
}

/* Navbar geçişi */
.navbar {
    transition: top 0.2s ease-in-out;
}

/* Carousel öğesi */
.carousel-item {
    transition: all 0.3s ease;
}

/* Buton hover */
.carousel-btn:hover:not(:disabled) {
    transform: translateY(-50%) scale(1.1);
}
```

---

## 🔧 Utility Sınıfları

### Display

```css
.d-inline-grid {
    display: inline-grid !important;
}
```

### Z-Index

```css
.z-index-1 { z-index: 1; }
.tofront { position: relative; z-index: 1; }
```

### Cursor

```css
.c-pointer:hover {
    cursor: pointer;
}
```

### Text

```css
.text-humayun {
    color: #ffc107 !important;
}

.baslik-link {
    display: block;
    text-align: center;
}
```

---

## 📊 CSS Dosya Yapısı

| Dosya | Boyut | İçerik |
|-------|-------|--------|
| `main.css` | ~10KB | Bootstrap özelleştirmeleri |
| `theme.css` | ~8KB | Tema stilleri |
| `tiny-slider.css` | ~3KB | Slider stilleri |
| `buyout.css` | ~2KB | E-ticaret stilleri |
| `music.css` | ~2KB | Müzik oynatıcı |
| `plyr.css` | CDN | Video/Audio player |

---

## 🎨 Renk Şeması Özeti

```
┌─────────────────────────────────────────────────────┐
│                    RENK ŞEMASI                      │
├─────────────────────────────────────────────────────┤
│                                                     │
│  ████████  Primary     #03a87c  (Yeşil)            │
│  ████████  Accent      #ff0002  (Kırmızı)          │
│  ████████  Navy        #032957  (Koyu Mavi)        │
│  ████████  Dark        #212529  (Siyah)            │
│  ████████  Light       #f8f9fa  (Açık Gri)         │
│  ████████  Background  #e8f3ec  (Açık Yeşil)       │
│  ████████  Border      #ced4da  (Gri)              │
│  ████████  Danger      #ea2f65  (Pembe)            │
│                                                     │
└─────────────────────────────────────────────────────┘
```

---

## 📝 Sonuç

Mihrabad Yayınları web sitesi, Bootstrap 4.6 temelinde özelleştirilmiş bir tasarım sistemi kullanmaktadır. Ana tasarım prensipleri:

- **Tutarlı Renk Paleti**: Yeşil (#03a87c) ana renk, kırmızı (#ff0002) vurgu
- **Serif Tipografi**: Başlıklarda Georgia, içerikte Lora
- **Responsive Tasarım**: 6 farklı breakpoint ile tam uyumluluk
- **Animasyonlar**: Yumuşak geçişler ve hover efektleri
- **Modüler CSS**: Ayrı dosyalarda organize edilmiş stiller
