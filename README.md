# Gambar ke Video — Studio Montase Lokal di Browser

Alat satu-halaman (`index.html`) untuk menyusun gambar dan video jadi satu video montase — lengkap dengan animasi kemunculan, gerakan kamera (Ken Burns), transisi, latar, dan audio. **Semua diproses langsung di browser** (client-side), tidak ada berkas yang diunggah ke server mana pun.

Dibuat oleh: **Zie**

---

## Cara Menjalankan

Tidak perlu instalasi atau server. Cukup buka `index.html` langsung di browser modern (disarankan Chrome/Edge terbaru untuk dukungan MediaRecorder & format MP4 terbaik).

---

## Fitur Utama

### 1. Unggah (Panel 01)
- Dua kategori: **Gambar** dan **Video** (bisa dicampur dalam satu urutan/timeline).
- Bisa unggah banyak berkas sekaligus.
- Urutan thumbnail = urutan tampil di video. Gunakan tombol ◀ ▶ pada tiap thumbnail untuk mengubah urutan, atau tombol × untuk menghapus.
- Berkas video ditandai ikon 🎬 pada thumbnail-nya dan diputar **tanpa suara** di dalam hasil video (gunakan panel Audio jika ingin menambahkan suara).

### 2. Latar Belakang (Panel 02)
Pilihan mode:
- **Tidak Ada (Transparan)** — *default*. Tidak menggambar latar apa pun. Catatan: kebanyakan format video tidak mendukung transparansi, jadi area kosong bisa tampil hitam saat direkam jadi berkas video.
- **Warna Polos**
- **Gradasi** (2 warna, 5 arah: atas-bawah, kiri-kanan, diagonal ↘, diagonal ↙, radial)
- **Unggah Gambar** — pakai gambar sendiri sebagai latar.

Juga ada **Mode Tampilan Gambar Utama**: Contain (latar terlihat di sisi) atau Cover (gambar dipotong mengisi layar).

### 3. Animasi Kemunculan (Panel 03)
12 jenis animasi: Fade, Fly In, Float In, Split, Wipe, Shape, Wheel, Random Bars, Grow & Turn, Zoom, Swivel, Bounce.
- Bisa centang lebih dari satu — akan digabung jadi satu gerakan kemunculan.
- **Default: tidak ada yang dicentang** → gambar/video langsung muncul tanpa animasi (instan).

### 4. Kamera & Transisi (Panel 04)
- **Mode Video**:
  - **Gabung (Satu per Satu)** — perilaku standar: gambar/video berikutnya menggantikan yang sebelumnya, dengan efek transisi di antaranya.
  - **Satu Frame (Semua Tetap Tampil)** — tiap item muncul satu per satu memakai animasi kemunculan yang dipilih, tapi **tidak tergantikan** oleh item berikutnya. Semua tetap ada di layar sampai akhir video, sementara kamera bergerak sebagai satu kesatuan di atas seluruh scene. Atur ukuran/posisi tiap item lewat panel Pratinjau agar tidak saling menumpuk penuh.
- **Gerakan Kamera (Ken Burns)**: Diam, Zoom In, Zoom Out, Pan kiri/kanan/atas/bawah, Putar Halus, atau Acak (beda tiap gambar).
- **Efek Transisi** (hanya untuk Mode "Gabung"): Potong Langsung, Fade, Slide, Wipe.
- **Durasi Tiap Gambar Muncul** (detik, bisa diatur).
- **Resolusi Video**: 1280×720, 1920×1080, 720×1280 (*default*, portrait/story), 1080×1080.

### 5. Audio (Panel 05)
- **Tanpa Audio**
- **Unggah Audio** — pakai berkas audio sendiri.
- **Teks ke Suara (TTS)** — tulis teks, pilih suara/pitch/kecepatan, dengarkan pratinjau, lalu rekam suaranya ke video lewat berbagi tab audio browser (klik "Rekam Suara untuk Video", pilih **Tab Ini**, centang **Bagikan audio tab**).

### 6. Pratinjau & Pengaturan Ukuran/Posisi
- Panel kanan menampilkan pratinjau langsung (live) tanpa perlu merender ulang.
- Pilih gambar/video dari deretan thumbnail pratinjau, lalu atur:
  - **Ukuran** (40%–220%, lewat slider atau tombol +/−)
  - **Posisi X/Y** (lewat tombol arah atau tombol tengahkan)
- Tombol **↺ Kembalikan ke Semula** mengembalikan ukuran & posisi item terpilih ke default.
- Tombol **Buat Video** berada tepat di bawah tombol reset tersebut.

### 7. Unduh Hasil
- Setelah render selesai, video bisa langsung diputar di pratinjau dan diunduh.
- Format otomatis MP4 jika didukung browser, atau WebM sebagai fallback (dengan catatan bisa dikonversi ke MP4 lewat alat lain).
- Nama file bisa diatur manual sebelum diunduh.

---

## Catatan Teknis

- Semua render dilakukan dengan Canvas 2D + `MediaRecorder` API (merekam `canvas.captureStream()`), berjalan real-time di browser saat tombol render ditekan — jangan pindah tab/menutup halaman selama proses berlangsung.
- Video yang diunggah tidak membawa audionya sendiri ke hasil akhir (gunakan panel Audio secara terpisah).
- Transparansi latar ("Tidak Ada") berfungsi normal di pratinjau canvas, tapi umumnya tidak terekam sebagai transparan pada file video akhir (tergantung dukungan encoder browser).
- Tidak ada data yang dikirim ke server — seluruh proses (baca berkas, animasi, render, TTS, ekspor) terjadi di perangkat pengguna.

---

## Struktur Berkas

```
index.html   # Seluruh aplikasi (HTML + CSS + JS) dalam satu berkas, tanpa dependensi eksternal
README.md    # Dokumentasi ini
```
