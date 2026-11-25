# Jejakawan Exam Client — Rilis Resmi Peserta (Android)

Repositori distribusi resmi aplikasi **Jejakawan Exam Client** (`com.jejakawan.platform.student`) untuk peserta ujian CBT berbasis **Jejakawan SME**.

> **Catatan:** Repositori ini hanya memuat dokumentasi & rilis APK **Edisi Peserta (Client)**.  
> Untuk **Edisi Admin / Proktor** serta **QR Aktivasi Lisensi**, silakan masuk melalui **Member Area** di [https://k2net.id/member/billing](https://k2net.id/member/billing).

---

## Unduh Cepat (Versi Terbaru: `v1.1.1`)

- **Halaman Unduh CDN Resmi (Publik, tanpa login):** [https://cdn.jejakawan.com/exambro/](https://cdn.jejakawan.com/exambro/)
- **Manifest Versi Terbaru:** [https://cdn.jejakawan.com/exambro/latest.json](https://cdn.jejakawan.com/exambro/latest.json)
- **Tab Releases Repositori Ini:** buka menu **Releases** untuk mengunduh file APK beserta `SHA256SUMS.txt`.

### Memilih File APK yang Tepat

| Varian File | Target Perangkat | Rekomendasi |
| :--- | :--- | :--- |
| `ja-exambro-client-v1.1.1-arm64-v8a.apk` | HP Android modern 64-bit (2018+) | **Disarankan (paling ringan)** |
| `ja-exambro-client-v1.1.1-armeabi-v7a.apk` | HP Android 32-bit / lawas | Untuk perangkat lawas |
| `ja-exambro-client-v1.1.1-universal.apk` | Semua arsitektur Android | Pilih ini jika ragu |

**Kebutuhan Minimum:** Android 7.0 Nougat (`API 24`) atau lebih baru.

---

## Cara Instalasi & Penggunaan (Peserta)

1. Unduh file APK sesuai arsitektur perangkat (disarankan `arm64-v8a`).
2. Izinkan pemasangan dari sumber aplikasi browser/file manager jika diminta Android.
3. Buka **Jejakawan Exam Client**, lalu **Scan QR Ruang Ujian** yang diberikan oleh pengawas/sekolah (atau pilih ruang ujian tersimpan).
4. Login menggunakan akun peserta sekolah Anda.

---

## Verifikasi Keaslian APK (Signing Certificate)

Seluruh rilis resmi **Jejakawan Exam Client** ditandatangani menggunakan sertifikat rilis permanen PT Jejak Awan Digital:

- **Package ID:** `com.jejakawan.platform.student`
- **Certificate SHA-256:** `6d:a9:7b:1a:9a:5c:9d:aa:38:86:dc:8f:e9:80:9f:22:f0:86:9a:f7:dc:ae:8d:08:97:74:57:84:a9:e2:4c:5c`
- **Certificate SHA-1:** `30:0d:f3:ee:95:c3:6b:35:b4:23:b4:fd:86:a7:5c:2e:f2:b3:37:c1`

Setiap rilis juga menyertakan file `SHA256SUMS.txt` untuk memverifikasi integritas file APK sebelum disebarkan ke perangkat sekolah.
