# Changelog — Jejakawan Exam Client

## v1.1.9 (2026-11-26)
- **Override Password Keluar & PIN Buka Blokir dari Exambro Admin:** Password Keluar (*Exit Password*) dan PIN Buka Blokir (*Unlock PIN*) yang diubah di Exambro Admin kini otomatis tertanam terenkripsi di QR & file `.ja`, serta langsung menimpa kode bawaan di perangkat peserta (kode bawaan otomatis ditolak jika Admin sudah menetapkan kode khusus).
- **Galeri Bukti Pelanggaran Pengawas di Exambro Client (Terkunci PIN Pengawas):**
  - Saat terjadi pelanggaran wajah, pengawas kini dapat langsung mengetuk **Lihat Bukti** di layar blokir (memerlukan PIN Pengawas) untuk melihat seluruh foto bukti terenkripsi beserta waktu kejadian.
  - Pasca ujian selesai, pengawas juga tetap dapat meninjau atau menghapus bukti pelanggaran melalui menu **Bantuan → Galeri Bukti Pengawas** (tetap terkunci PIN Pengawas).

## v1.1.8 (2026-11-26)
- **Kalibrasi Proctoring Suara & Kamera (Anti False-Trigger):**
  - Penambahan masa pemanasan (*warm-up grace*) **8 detik** untuk audio dan **6 detik** untuk kamera saat masuk halaman ujian/login agar lonjakan inisialisasi mikrofon maupun waktu muat halaman tidak langsung memicu pelanggaran.
  - Deteksi kebisingan kini membutuhkan **3 detik suara keras berturut-turut** di atas ambang batas (tidak lagi terpicu oleh batuk singkat atau sentuhan layar), dengan default lebih realistis **78 dB** (rentang `40–120 dB`).
  - Perbaikan kolom input ambang suara di **Exambro Admin** agar angka dapat dihapus dan diketik ulang dengan bebas tanpa tersangkut digit terakhir.

## v1.1.7 (2026-11-26)
- **Perbaikan Import/Export File `.ja` (termasuk dari WhatsApp & File Manager):**
  - Penulisan file `.ja` dari Admin kini menggunakan mode truncate (`"wt"`) + `flush()` dan format tidak terkompresi agar kompatibel 100% di semua versi Exambro Client.
  - Pembacaan URI file `.ja` dilengkapi fallback `ParcelFileDescriptor` & `file://` untuk kompatibilitas maksimal pada folder *WhatsApp Documents* dan file manager OEM (Xiaomi/Samsung/Oppo/Vivo).
  - Decoder `.ja` kini toleran terhadap BOM, newline/spasi di tengah payload, mendukung `ACTION_SEND` & `onNewIntent` (buka/kirim langsung dari WhatsApp), menaikkan batas logo kustom hingga 4 MB, dan menampilkan alasan diagnostik spesifik bila file rusak/kosong.

## v1.1.6 (2026-11-26)
- **QR Lebih Ringkas & Mudah Dipindai (Admin & Client):**
  - Kompresi DEFLATE + penghapusan duplikasi field pada payload QR Ruang Ujian (ukuran data QR menyusut drastis hingga ~60%, modul jauh lebih renggang dan cepat terbaca kamera).
  - Perbaikan generator QR Admin: modul kotak tajam presisi piksel tanpa *finder eye* ganda dan tanpa lubang logo di tengah matriks QR (logo dipindah rapi ke header kartu), *quiet zone* standar 4 modul, dan *error correction* adaptif.
  - Upgrade scanner kamera Client dari 480p ke **HD 720p (`1280×720`)** dengan *autofocus* kontinyu, *tap-to-focus*, dan tombol **Senter (Flash)** untuk ruangan redup.

## v1.1.5 (2026-11-26)
- **In-App Auto-Update (Tanpa Uninstall):** Deteksi versi terbaru otomatis saat aplikasi dibuka maupun dari menu *Bantuan → App & Updates*, lengkap dengan unduh APK sesuai arsitektur perangkat, verifikasi integritas **SHA-256**, dan pembaruan langsung via Android Package Installer tanpa menghapus data atau PIN.
- Perbaikan tampilan info versi & tanggal rilis pada halaman *Bantuan* agar membaca data aplikasi terpasang secara langsung.

## v1.1.4 (2026-11-26)
- **Sinkronisasi Penuh Aturan Proteksi Admin → Client:** Seluruh kebijakan keamanan & proctoring (kamera, audio, ambang kebisingan, deteksi multi-wajah, dsb.) kini tertanam penuh di QR Ruang Ujian dan langsung aktif setelah dipindai di perangkat peserta.
- **Perbaikan Proctoring Kamera & Audio (Android 14+):** Penambahan dukungan *foreground service* mikrofon (`camera|microphone`), aktifnya monitoring kamera maupun audio-only, serta *cooldown* otomatis setelah *unlock*.
- **Dukungan Import/Export File `.ja`:** Perbaikan pemilih file (`OpenDocument`) dan dukungan buka langsung file `.ja` dari WhatsApp / File Manager ke Jejakawan Exam Client.
- **Perbaikan Race Penggantian PIN Login Pertama (Admin):** Validasi dan penyimpanan seluruh PIN/Password dilakukan secara atomik agar tidak terjadi loop penggantian password bawaan.

## v1.1.3 (2026-11-26)
- Dukungan aktivasi lisensi langsung melalui scan **QR Pairing SME (Moodle)** pada **Jejakawan Exam Admin**, serta penyimpanan kredensial SME saat membuat QR Ruang Ujian.

## v1.1.2 (2026-11-25)
- Pembaruan konfigurasi kode bawaan (*default*) buka blokir pelanggaran (*Unlock PIN*) — lihat [GUIDE.md](./GUIDE.md).
- Pembaruan dokumentasi publik: penambahan **Panduan Penggunaan (`GUIDE.md`)** dan **Kebijakan Privasi & Kepatuhan (`PRIVACY.md`)**.

## v1.1.1 (2026-11-25)
- Peningkatan stabilitas koneksi & sinkronisasi konfigurasi ruang ujian.
- Pembaruan penamaan paket rilis publik menjadi `ja-exambro-client-v<versi>-<abi>.apk`.

## v1.1.0 (2026-11-24)
- Rilis produksi perdana dengan sertifikat penandatanganan rilis permanen (RSA-4096).
- Perbaikan pemilihan ruang pada Daftar Ruang agar URL server & konfigurasi SME terisi otomatis.
- Verifikasi lisensi server SME pra-sesi (*preflight handshake*) agar mode ujian aktif sejak sesi pertama.
- Peningkatan **Jejakawan Keyboard** (stabilitas input esai, dukungan simbol lengkap, auto-adjust layar).
- Penguatan proteksi anti-kecurangan Android 14–16 (blokir floating action mode, translate, autofill, assist/Circle-to-Search, drag & drop, clipboard, dan split-screen).
