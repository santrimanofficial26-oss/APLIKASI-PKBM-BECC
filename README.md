# PKBM BECC — iframe untuk Vercel

Website statis yang hanya menampilkan Apps Script dalam iframe layar penuh. Tidak ada JavaScript wrapper, spinner, splash screen, timer, tombol pembuka, atau animasi loading. Iframe langsung dimuat melalui atribut `src` dan `loading="eager"`.

## Struktur

```text
index.html         Halaman iframe
vercel.json        Konfigurasi hosting statis
```

Folder lokal `vercel-iframe` adalah checkout Git tersendiri. Isinya berada di root repository GitHub; source Apps Script, data demo, dan alat pengembangan proyek induk tidak ikut di-push.

## Deploy ke Vercel

1. Import repository `santrimanofficial26-oss/APLIKASI-PKBM-BECC` melalui Add New → Project.
2. Gunakan Root Directory `.` (root repository), **bukan** `vercel-iframe`.
3. Framework Preset: **Other**. Build dan Install Command kosong; Output Directory: biarkan kosong (root). Nilai ini sudah ditetapkan di `vercel.json`.
4. Deploy. Jika repository sudah terhubung ke Vercel dengan auto-deployment, push berikutnya dapat memicu deployment otomatis.

Tidak memerlukan npm install, API key, environment variable, atau backend Vercel.

## Target iframe

https://script.google.com/macros/s/AKfycbz9X7hiPktw4eBXtKCygDWm_OKdwDVUxNT3vMySLeX2E9YNNcFmhtPjiWCCmCrGW82nJA/exec

Untuk mengganti deployment tujuan, edit atribut `src` pada `index.html`, commit, lalu push.

## Perilaku

- Iframe mengisi viewport desktop dan ponsel, tanpa border, margin, atau scrollbar tambahan pada wrapper.
- Reload wrapper langsung meminta halaman Apps Script. Beranda, login, dan perilaku aplikasi di dalamnya tetap ditentukan oleh deployment Apps Script.
- Wrapper tidak menambahkan loading, tetapi tidak dapat menghilangkan waktu respons jaringan/Google maupun notifikasi yang ditampilkan Google di dalam iframe.
- Deployment Apps Script harus dapat diakses oleh pengunjung yang dituju dan mengizinkan embedding. Backend proyek saat ini menggunakan `HtmlService.XFrameOptionsMode.ALLOWALL`.
- Perubahan aplikasi dilakukan di Apps Script; repository ini hanya wrapper.

Referensi konfigurasi: https://vercel.com/docs/project-configuration
