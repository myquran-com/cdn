# CDN myQuran.com

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
    └── /page/
        └── [nomor_page].mp3
    └── /surah/
        └── [nomor_surah].mp3
```

- Direktori `/img/ayah/` berisi gambar-gambar ayat Al-Qur'an dengan format nama file `[nomor_surah]_[nomor_ayat].png`
- Direktori `/img/page/` berisi gambar-gambar halaman Al-Qur'an dengan format nama file `[nomor_halaman].png`
- Direktori `/audio/ayah/` berisi file audio ayat Al-Qur'an dengan format nama file `[nomor_surah_3digit][nomor_ayat_3digit].mp3`
- Direktori `/audio/page/` berisi file audio ayat Al-Qur'an dengan format nama file `[nomor_surah].mp3`
- Direktori `/audio/surah/` berisi file audio ayat Al-Qur'an dengan format nama file `[nomor_surah].mp3`


## Contoh URL Akses
- Gambar Ayat: `https://cdn.myquran.com/img/ayah/1_1.png`
- Gambar Halaman: `https://cdn.myquran.com/img/page/1.png`
- Audio Ayat: `https://cdn.myquran.com/audio/ayah/001001.mp3`
- Audio Page: `https://cdn.myquran.com/audio/page/1.mp3`
- Audio Surat: `https://cdn.myquran.com/audio/surah/1.mp3`

## Surat
- Nomor surat atau surah, bernilai `1` sampai dengan `114`
- Nomor page dari `1` sampai dengan `604`
