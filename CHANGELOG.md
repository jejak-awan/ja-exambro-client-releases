# Changelog — Jejakawan Exam Client

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
