# CDN MyQuran.com

Repository ini berisi file-image yang digunakan sebagai CDN untuk domain `cdn.myquran.com`. Gambar-gambar ini digunakan untuk menyajikan ayat-ayat Al-Qur'an dalam bentuk gambar (image) dan halaman-halaman Al-Qur'an.

## Struktur Direktori

```
├── /img/
│   ├── /ayah/
│   │   └── [nomor_surah]_[nomor_ayat].png
│   └── /page/
│       └── [nomor_halaman].png
└── /audio/
    └── /ayah/
        └── [nomor_surah_3digit][nomor_ayat_3digit].mp3
```

- Direktori `/img/ayah/` berisi gambar-gambar ayat Al-Qur'an dengan format nama file `[nomor_surah]_[nomor_ayat].png`
- Direktori `/img/page/` berisi gambar-gambar halaman Al-Qur'an dengan format nama file `[nomor_halaman].png`
- Direktori `/audio/ayah/` berisi file audio ayat Al-Qur'an dengan format nama file `[nomor_surah_3digit][nomor_ayat_3digit].mp3`

## Konfigurasi CDN di Cloudflare

Untuk mengarahkan domain `cdn.myquran.com` ke repository ini sebagai CDN (Content Delivery Network), ikuti langkah-langkah berikut:

### 1. Akun Cloudflare
1. Buat akun di [cloudflare.com](https://www.cloudflare.com) jika belum memiliki akun.
2. Tambahkan domain `myquran.com` ke akun Cloudflare Anda (meskipun CDN hanya untuk subdomain).

### 2. Pengaturan DNS untuk Subdomain CDN
1. Masuk ke dashboard Cloudflare.
2. Pilih domain `myquran.com`.
3. Klik tab `DNS`.
4. Tambahkan record baru dengan konfigurasi berikut:
   - Type: `CNAME`
   - Name: `cdn`
   - Content/Target: `github-pages.example.com` atau alamat hosting static Anda (misalnya jika Anda menggunakan GitHub Pages)
   
   Jika Anda ingin menggunakan Cloudflare Pages:
   - Type: `CNAME`
   - Name: `cdn`
   - Content/Target: `[nama-proyek].pages.dev` (alamat Cloudflare Pages Anda)

### 3. Konfigurasi Cloudflare Pages (Opsional)
Jika Anda ingin menggunakan Cloudflare Pages sebagai hosting static, ikuti langkah-langkah berikut:

1. Hubungkan repository ini ke Cloudflare Pages.
2. Di Cloudflare Pages, pastikan konfigurasi berikut:
   - Framework Preset: None
   - Build Command: Biarkan kosong
   - Build Output Directory: `./` (root directory)
   - Root Directory: `./`

3. Tambahkan Custom Domain:
   - Pada halaman proyek Cloudflare Pages, klik "Custom Domain"
   - Tambahkan `cdn.myquran.com`
   - Cloudflare akan memberikan petunjuk untuk mengupdate DNS (biasanya CNAME ke `[panjang-hash].pages.dev`)

### 4. Pengaturan SSL/TLS
1. Di dashboard Cloudflare, pilih domain `myquran.com`.
2. Klik tab `SSL/TLS`.
3. Pilih mode SSL/TLS:
   - Jika menggunakan Cloudflare Pages: `Flexible` sudah cukup
   - Jika hosting sendiri: gunakan `Full` atau `Full (strict)`

### 5. Optimasi Lainnya
1. Di menu Speed, aktifkan:
   - Auto Minify
   - Rocket Loader
   - Mirage (untuk optimasi gambar)

2. Di menu Caching:
   - Set Browser Cache TTL: 1 year untuk file statis seperti gambar
   - Aktifkan "Always Online"

3. Atur Page Rules untuk file gambar:
   - `/img/*` → Cache Level: Cache Everything, Browser Cache TTL: 1 year
   - `/audio/*` → Cache Level: Cache Everything, Browser Cache TTL: 1 year

## Contoh URL Akses
- Gambar Ayat: `https://cdn.myquran.com/img/ayah/1_1.png`
- Gambar Halaman: `https://cdn.myquran.com/img/page/1.png`
- Audio Ayat: `https://cdn.myquran.com/audio/ayah/001001.mp3`

## Penyelesaian Masalah
1. Pastikan semua file gambar dan audio telah diupload dengan benar.
2. Tunggu proses propagasi DNS (biasanya 1-24 jam).
3. Gunakan tools seperti [DNS Checker](https://dnschecker.org/) untuk memastikan record DNS telah terupdate.
4. Periksa apakah Cloudflare Pages telah berhasil build semua file.
5. Uji akses langsung ke CDN untuk memastikan gambar dan audio dapat diakses.

## Hak Cipta
Gambar-gambar dan audio dalam repository ini adalah milik pengguna dan harus digunakan sesuai dengan ketentuan hak cipta yang berlaku.