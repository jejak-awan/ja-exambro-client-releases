# Jejakawan Exam Client — Rilis Resmi Peserta (Android)

Repositori distribusi resmi aplikasi **Jejakawan Exam Client** (`com.jejakawan.platform.student`) untuk peserta ujian CBT dari [**JEJAKAWAN**](https://jejakawan.com).

> **Catatan Distribusi:** Repositori ini hanya memuat dokumentasi & rilis APK **Edisi Peserta (Client)**.  
> Untuk **Edisi Admin / Proktor** (`com.jejakawan.platform.admin`) beserta **QR Aktivasi Lisensi**, silakan masuk melalui **Member Area** di [https://k2net.id/member/billing](https://k2net.id/member/billing).

---

## Unduh Cepat (Versi Terbaru: `v1.1.9`)

- **Halaman Unduh CDN Resmi (Publik, tanpa login):** [https://cdn.jejakawan.com/exambro/](https://cdn.jejakawan.com/exambro/)
- **Mirror Cadangan (Jika CDN Gangguan):** unduh langsung dari GitHub Releases / Tag di [https://github.com/jejak-awan/ja-exambro-client-releases/releases/tag/v1.1.9](https://github.com/jejak-awan/ja-exambro-client-releases/releases/tag/v1.1.9) (atau daftar semua versi di [Tags](https://github.com/jejak-awan/ja-exambro-client-releases/tags)).
- **Manifest Versi Terbaru:** [https://cdn.jejakawan.com/exambro/latest.json](https://cdn.jejakawan.com/exambro/latest.json)

> **Rekomendasi Distribusi Sekolah (Hemat Kuota & Lebih Cepat):**  
> Agar tidak membebani koneksi internet sekolah maupun server CDN saat hari H ujian, **cukup 1 orang Panitia / Proktor per sekolah** yang mengunduh file APK, lalu bagikan file APK tersebut ke grup jejaring internal sekolah (WhatsApp, Telegram, LMS, atau server lokal sekolah).

### Memilih File APK yang Tepat

| Varian File | Target Perangkat | Rekomendasi |
| :--- | :--- | :--- |
| `ja-exambro-client-v1.1.9-arm64-v8a.apk` | HP Android modern 64-bit (2018+) | **Disarankan (paling ringan)** |
| `ja-exambro-client-v1.1.9-armeabi-v7a.apk` | HP Android 32-bit / lawas | Untuk perangkat lawas |
| `ja-exambro-client-v1.1.9-universal.apk` | Semua arsitektur Android | Pilih ini jika ragu |

**Kebutuhan Minimum:** Android 7.0 Nougat (`API 24`) atau lebih baru.

---

## Perbedaan Aplikasi (Client vs Admin)

| Edisi | Target Pengguna | Distribusi | Fungsi Utama |
| :--- | :--- | :--- | :--- |
| **Jejakawan Exam Client** (`com.jejakawan.platform.student`) | **Peserta / Siswa** | Publik (CDN & repo ini) | Mengerjakan ujian CBT dengan proteksi kiosk & anti-kecurangan; cukup Scan QR Ruang Ujian dari sekolah tanpa aktivasi akun di HP siswa. |
| **Jejakawan Exam Admin** (`com.jejakawan.platform.admin`) | **Pengawas / Proktor / Admin Sekolah** | Private ([Member Area k2net.id](https://k2net.id/member/billing)) | Mengatur kebijakan keamanan ujian, membuat & menandatangani QR Ruang Ujian, serta aktivasi lisensi instansi (mendukung **Scan QR Lisensi**). |

---

## Perbedaan Fitur & Tier Lisensi

Satu aplikasi **Jejakawan Exam Client** secara dinamis menyesuaikan tingkat proteksi berdasarkan tier lisensi aktif (baik dari server **Jejakawan SME** berlisensi maupun lisensi instansi di [k2net.id](https://k2net.id/member/register)):

| Kategori & Fitur | FREE | PRO | ORGANIZATION | ENTERPRISE |
| :--- | :---: | :---: | :---: | :---: |
| **Kiosk & Proteksi Dasar**: Lock Task (Pin Screen), Immersive Mode, blokir tombol sistem & panel notifikasi, Secure WebView, anti screenshot / copy-paste / translate / floating action mode, deteksi keluar aplikasi (*Lost Focus*) | ✅ | ✅ | ✅ | ✅ |
| **Kiosk Lanjutan & Anti-Cheat Modern**: **Jejakawan Keyboard** (keyboard internal anti-AI), deteksi overlay / floating app, split-screen / multi-window, layar eksternal, screen capture, monitor Bluetooth / Headset / Charger / SIM, biometrik admin | ❌ | ✅ | ✅ | ✅ |
| **Cek Integritas Perangkat**: Deteksi Root, USB Debugging (ADB), VPN, Accessibility Service, Virtual/Cloning App, & aplikasi asing | ❌ | ✅ | ✅ | ✅ |
| **Proctoring & Otomasi LMS**: Proctoring kamera & deteksi multi-wajah, proctoring audio, **Auto Login LMS**, serta **Sinkronisasi Konfigurasi Server** (Cloud / SME Sync) | ❌ | ❌ | ✅ | ✅ |
| **Keamanan & Kontrol Enterprise**: **Geofencing** (batas radius GPS lokasi ujian), verifikasi **Play Integrity**, serta **App Gate / Custom Branding** instansi | ❌ | ❌ | ❌ | ✅ |

### Mekanisme Lisensi
1. **Mode FREE (Gratis):** Dapat langsung digunakan pada URL/QR ujian umum dengan proteksi kiosk inti (Lock Task, Secure WebView, anti-screenshot, deteksi *Lost Focus*).
2. **Hybrid Server Jejakawan SME (Otomatis & Terisolasi Per-Server):** Apabila sekolah menggunakan **Jejakawan SME** berlisensi aktif, seluruh perangkat siswa otomatis memperoleh kapabilitas sesuai paket server SME (*Organization / Enterprise*) sejak sesi pertama melalui *preflight HMAC handshake* — **tanpa perlu aktivasi manual per perangkat siswa**. Bila aplikasi dipakai mengakses server lain yang tidak berlisensi, kapabilitas otomatis kembali ke mode **FREE**.
3. **Lisensi Instansi / Mandiri:** Pendaftaran dan pengelolaan lisensi instansi dilakukan melalui [**Member Area k2net.id**](https://k2net.id/member/register) (mendukung aktivasi sekali scan QR pada **Jejakawan Exam Admin** dengan masa tenggang offline 7 hari).

---

## Cara Instalasi & Penggunaan (Peserta)

1. Unduh file APK sesuai arsitektur perangkat (disarankan `arm64-v8a`).
2. Izinkan pemasangan aplikasi dari browser/file manager jika diminta Android.
3. Buka **Jejakawan Exam Client**, lalu **Scan QR Ruang Ujian** yang dibagikan pengawas/sekolah (atau masukkan URL ruang ujian pada mode mandiri).
4. Login menggunakan akun peserta sekolah Anda.

> **Panduan Lengkap (Keluar Sesi, Buka Blokir / Unblock & Pengaturan Pengawas):**  
> Informasi langkah operasional lengkap termasuk prosedur keluar ujian, penanganan layar terblokir (*unblock*), mode token dinamis, dan panduan pengawas dapat dibaca pada dokumen **[Panduan Penggunaan (GUIDE.md)](./GUIDE.md)** atau halaman web [https://cdn.jejakawan.com/exambro/guide.html](https://cdn.jejakawan.com/exambro/guide.html).

---

## Verifikasi Keaslian APK (Signing Certificate)

Seluruh rilis resmi **Jejakawan Exam Client** ditandatangani menggunakan sertifikat rilis permanen [**JEJAKAWAN**](https://jejakawan.com):

- **Package ID:** `com.jejakawan.platform.student`
- **Certificate SHA-256:** `6d:a9:7b:1a:9a:5c:9d:aa:38:86:dc:8f:e9:80:9f:22:f0:86:9a:f7:dc:ae:8d:08:97:74:57:84:a9:e2:4c:5c`
- **Certificate SHA-1:** `30:0d:f3:ee:95:c3:6b:35:b4:23:b4:fd:86:a7:5c:2e:f2:b3:37:c1`

Setiap rilis juga menyertakan file `SHA256SUMS.txt` untuk verifikasi integritas file APK.

---

## Privasi, Kepatuhan & Tanggung Jawab Data

- **Zero-Collection & Tanpa Pelacak:** Aplikasi tidak menyertakan SDK analitik, iklan, atau telemetri pihak ketiga. **JEJAKAWAN tidak mengumpulkan, menyimpan, maupun mengakses data pribadi peserta atau konten ujian.**
- **Pemrosesan Lokal (*On-Device*):** Izin keamanan Android (deteksi overlay, aplikasi asing, kamera/QR ML Kit, ambang audio, dan geofencing GPS) diproses lokal di perangkat dan hanya berkomunikasi langsung dengan server ujian/LMS yang dipilih sekolah.
- **Tanggung Jawab Penuh Pengguna & Institusi (*Shared Responsibility*):** Sesuai standar **UU PDP No. 27 Tahun 2022** dan **GDPR**, sekolah/institusi penyelenggara ujian (atau pengguna mandiri) bertindak penuh sebagai **Pengendali Data (*Data Controller*)** dan bertanggung jawab penuh atas keamanan server, konfigurasi ujian, persetujuan peserta, serta pengelolaan data ujiannya sendiri.

Baca dokumen kebijakan lengkap di **[PRIVACY.md](./PRIVACY.md)** atau halaman publik [https://cdn.jejakawan.com/exambro/privacy.html](https://cdn.jejakawan.com/exambro/privacy.html).

---

Dikembangkan oleh [**JEJAKAWAN**](https://jejakawan.com)
