# ChronoGrid Nexus - Dicoding Story App

ChronoGrid Nexus (Dicoding Story App) adalah aplikasi web berbagi cerita terdesentralisasi dengan fitur pemetaan geografis interaktif yang dibuat untuk memenuhi standar kompetensi submission akhir kelas "Menjadi Front-End Web Developer Expert" di Dicoding.

Aplikasi ini didesain sebagai *Progressive Web App* (PWA) lengkap dengan dukungan *offline capabilities*, IndexedDB, *background sync*, dan *push notification*.

## Fitur Utama & Kriteria yang Terpenuhi

1. **SPA & Transisi Halaman (Kriteria Dasar Terpenuhi)**
   Aplikasi menggunakan pola *Single Page Application* dengan DOM manipulation murni. Dilengkapi dengan animasi transisi native `document.startViewTransition`.
   
2. **Push Notification (Advanced)**
   - Mendukung integrasi dengan Push Notification server VAPID dari API Dicoding.
   - Pendaftaran notifikasi fleksibel dengan toggle interaktif (Subscribe / Unsubscribe) yang langsung memodifikasi tombol antarmuka di _header_.
   - Notifikasi dinamis: Klik pada _Push Notification_ untuk cerita baru akan membawa pengguna masuk/mengarah (navigasi otomatis) ke detail cerita bersangkutan melalui _service worker_.
   
3. **PWA, Instalasi & Dukungan Offline (Advanced)**
   - Muncul prompt _installable_ / "Add to Home Screen".
   - `manifest.json` solid: Meliputi maskable icons, *screenshots* responsif (mobile dan desktop), dan App Shortcuts untuk "Add New Story". Tidak terdapat warning saat diperiksa lewat Lighthouse/Application tab Chrome.
   - *Network-First API Caching & Cache-First Assets*: Memastikan antarmuka tidak rusak saat kehilangan internet, serta sanggup memunculkan daftar (feed) cerita secara offline menggunakan *cache* otomatis.
   
4. **Penerapan IndexedDB (Advanced)**
   - Aplikasi menggunakan IndexedDB untuk menyimpan daftar *Archives* / Favorit secara luring. 
   - Halaman Favorit mendukung interaksi: bisa melakukan *Searching* teks dan *Sorting* berdasarkan nama atau waktu.
   - Mendukung **Background Sync**: Saat internet putus, operasi pembuatan *Story* dialihkan untuk disimpan pada antrean IndexedDB (`queued-transmissions`). Saat internet hidup kembali (`online` event atau sinkronisasi _service worker_), data di *queue* akan secara otomatis dipos ke server API, dan _toast/alert_ kesuksesan akan muncul.

5. **Deploy Publik**
   Otomatis ter-deploy di [GitHub Pages](https://FIRMAN1975.github.io/dicoding) melalui serangkaian GitHub Actions Pipeline.

## Stack & Teknologi

- **Core**: Vanilla JavaScript (ES6+), HTML5, CSS3.
- **Bundler**: Webpack 5 + Babel.
- **Peta Interaktif**: Leaflet.js
- **Database Lokal**: IndexedDB (Native `window.indexedDB`).
- **Service Worker**: Native API Service Worker, Push API, Sync API.

## Skrip Pengembangan

Jalankan perintah ini di terminal setelah mengunduh repo dan mengetikkan `npm install`:

- Build for Production:
  ```shell
  npm run build
  ```
- Start Development Server:
  ```shell
  npm run start-dev
  ```

---
*Dikembangkan oleh [FIRMAN1975](https://github.com/FIRMAN1975) untuk submission Dicoding Academy.*