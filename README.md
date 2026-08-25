# MP4 Converter — Studio Video

Aplikasi web lokal untuk membuat video dari gambar dan video langsung di browser.

## Fitur

- Menggabungkan beberapa gambar/video menjadi satu video.
- Mode **Gabung** dan **Satu Frame**.
- Pilihan latar belakang:
  - Tanpa latar
  - Warna polos
  - Gradasi
  - Gambar
- Pengaturan ukuran dan posisi media.
- Animasi masuk dan efek kamera.
- Transisi antar media.
- Dukungan audio/TTS sesuai fitur yang tersedia di aplikasi.
- Preview sebelum hasil disimpan.
- Export video ke **MP4** yang dioptimalkan untuk kompatibilitas editor video.
- Penyimpanan dan pembukaan **Project** agar pengaturan proyek dapat diedit kembali di aplikasi.

## Format Video Hasil

Video hasil export ditujukan agar lebih mudah digunakan pada aplikasi editor seperti CapCut, VN, Alight Motion, KineMaster, dan editor video lain yang mendukung MP4.

Proses kompatibilitas menggunakan:

- MP4
- H.264 / AVC
- AAC
- Pixel format `yuv420p`
- `faststart` untuk struktur MP4 yang lebih kompatibel

> **Catatan:** MP4 hasil export adalah video final/flattened. Elemen seperti gambar, background, animasi, dan transisi tidak menjadi layer terpisah di CapCut atau editor lain.

## Project yang Bisa Diedit Kembali

Untuk mempertahankan struktur proyek, gunakan fitur **Simpan Project**.

File project menyimpan pengaturan yang diperlukan aplikasi untuk membuka kembali proyek, termasuk pengaturan media, posisi, ukuran, durasi, animasi, transisi, background, dan pengaturan proyek lainnya yang didukung aplikasi.

Alurnya:

```text
Project
   ↓
Simpan Project
   ↓
video-project.json
   ↓
Buka Project
   ↓
Edit kembali di aplikasi
   ↓
Export MP4
```

Jadi:

- **MP4** → untuk dibagikan atau diedit sebagai video di aplikasi lain.
- **Project JSON** → untuk melanjutkan pengeditan proyek di aplikasi ini.

## Cara Menggunakan

### 1. Menjalankan aplikasi

Aplikasi dapat dijalankan sebagai halaman web dengan membuka:

```text
index.html
```

Tidak membutuhkan instalasi server khusus untuk penggunaan dasar.

### 2. Memasukkan media

Klik tombol:

```text
+ Pilih Gambar
```

Kemudian pilih gambar atau video yang ingin digunakan.

Format media yang didukung aplikasi mencakup format gambar dan video yang dapat dibaca browser.

### 3. Atur proyek

Sesuaikan:

- urutan media
- durasi
- posisi
- ukuran
- background
- animasi
- efek kamera
- transisi
- audio

### 4. Export

Klik tombol **Buat Video**.

Aplikasi akan merender proyek melalui Canvas dan kemudian memproses hasilnya menjadi MP4 yang lebih kompatibel.

## Struktur File

Struktur sederhana repository:

```text
/
├── index.html
└── README.md
```

Jika nantinya terdapat aset eksternal, struktur dapat dikembangkan menjadi:

```text
/
├── index.html
├── README.md
└── assets/
    ├── images/
    ├── audio/
    └── video/
```

## Kompatibilitas

Aplikasi menggunakan kemampuan browser seperti:

- Canvas
- MediaRecorder
- Web Audio API
- FFmpeg WebAssembly untuk kompatibilitas MP4

Karena proses render dilakukan di browser, performa sangat bergantung pada perangkat dan browser yang digunakan.

Pada perangkat Android dengan RAM atau CPU terbatas, proses export video yang panjang atau beresolusi tinggi dapat membutuhkan waktu lebih lama.

## FFmpeg WebAssembly

Untuk proses kompatibilitas MP4, aplikasi menggunakan FFmpeg WebAssembly yang dimuat melalui CDN.

Saat proses ini digunakan, browser perlu memiliki akses internet untuk mengambil komponen FFmpeg jika komponen tersebut belum tersedia di cache.

## Catatan Penting

### MP4 bukan project editing

File MP4 hanya menyimpan hasil akhir video. MP4 tidak mempertahankan:

- layer gambar
- layer background
- keyframe aplikasi
- pengaturan animasi asli
- pengaturan transisi asli

Karena itu, selalu simpan file **Project JSON** jika proyek masih ingin diedit kembali.

### Keamanan

Aplikasi dirancang untuk melakukan proses utama di browser. File media yang dipilih digunakan oleh aplikasi untuk proses preview dan rendering.

Tetap periksa izin browser dan sumber file yang digunakan.

## Pengembangan

Repository ini dapat digunakan sebagai dasar untuk pengembangan lebih lanjut, misalnya:

- timeline video
- layer editor
- keyframe
- crop
- rotate
- filter
- subtitle
- pengaturan volume
- fade audio
- pilihan FPS
- pilihan bitrate
- template video
- undo/redo
- autosave project

## Lisensi

Tambahkan informasi lisensi sesuai kebutuhan proyek.
