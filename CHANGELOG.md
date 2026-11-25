# Changelog — Jejakawan Exam Client

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
