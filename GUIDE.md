# Panduan Penggunaan — Jejakawan Exam (Peserta & Pengawas)

Panduan resmi penggunaan **Jejakawan Exam Client** (Peserta) dan **Jejakawan Exam Admin** (Pengawas/Proktor) dari [**JEJAKAWAN**](https://jejakawan.com).  
Halaman web panduan: [https://cdn.jejakawan.com/exambro/guide.html](https://cdn.jejakawan.com/exambro/guide.html)

---

## 1. Panduan Peserta (Siswa)

### A. Instalasi & Persiapan Awal
1. Unduh file APK **Jejakawan Exam Client** dari [https://cdn.jejakawan.com/exambro/](https://cdn.jejakawan.com/exambro/) (disarankan `arm64-v8a` untuk HP Android modern, atau `universal` jika ragu).
2. Jika Android meminta izin instalasi dari browser/file manager, aktifkan **Izinkan dari sumber ini**.
3. Buka aplikasi dan selesaikan layar awal (*Onboarding*): baca ringkasan privasi, centang persetujuan, dan berikan izin yang diminta sistem.
4. *(Khusus sekolah dengan kebijakan Pro+ / SME berlisensi)* Jika diminta mengaktifkan **Jejakawan Keyboard**, ikuti tombol pintasan ke pengaturan keyboard Android dan pilih **Jejakawan Keyboard** sebelum memulai ujian.

### B. Masuk ke Ruang Ujian
- **Cara Utama (Disarankan): Scan QR Ruang Ujian** — ketuk tombol **Scan QR**, arahkan kamera ke QR yang diberikan pengawas/sekolah. Pengaturan keamanan dan alamat LMS akan terisi otomatis.
- **Cara Manual (Mode Mandiri / FREE):** Masukkan alamat URL ujian/LMS secara manual pada kolom URL lalu ketuk **Mulai Ujian**.
- **Reset Konfigurasi Peserta:** Jika ingin menghapus ruang ujian yang tersimpan atau membersihkan konfigurasi lokal, gunakan menu **Reset Konfigurasi** di halaman utama aplikasi.

### C. Keluar dari Sesi Ujian
1. Pastikan seluruh jawaban sudah dikirim (*Submit / Finish Attempt*) dan Anda sudah logout dari LMS ujian.
2. Ketuk tombol **Keluar** (atau tekan tombol kembali sesuai pengaturan ruang ujian) untuk memunculkan dialog konfirmasi keluar.
3. Masukkan **Password Keluar** atau **Token Keluar** yang diberikan oleh pengawas ruang ujian Anda.

### D. Jika Layar Terblokir (*Violation / Blocked Screen*)
Layar ujian akan otomatis terkunci/diblokir apabila sistem mendeteksi pelanggaran (misalnya keluar aplikasi/*Lost Focus*, membuka *split-screen*, overlay mengambang, tangkapan layar, atau mencopot perangkat yang dilarang):
1. **Jangan panik** dan **jangan menutup paksa** aplikasi sebelum melapor.
2. Laporkan ke **Pengawas Ruang Ujian** agar pengawas memeriksa kondisi perangkat Anda.
3. Pengawas akan memasukkan **PIN Buka Blokir (*Unlock PIN*)** atau **Token Dinamis** pada perangkat Anda untuk melanjutkan ujian, atau membuka kunci sesi dari panel pengawas (jika sekolah menggunakan *Session Lock* Jejakawan SME).

---

## 2. Panduan Pengawas / Proktor (Keamanan Keluar & Buka Blokir)

Untuk pelaksanaan ujian resmi di sekolah/instansi, tersedia **3 mekanisme kontrol keluar & buka blokir**:

| Mekanisme | Kapan Dipakai | Keamanan |
| :--- | :--- | :--- |
| **1. Mode Token Dinamis Offline** *(Paling Disarankan)* | Diaktifkan dari **Jejakawan Exam Admin** saat membuat QR Ruang Ujian | Token berubah otomatis setiap interval (default 15 menit, toleransi ±1 jendela waktu) dan hanya tampil di HP Pengawas (*Admin*). Siswa tidak dapat menebak atau menyebarkan kode. |
| **2. Password Keluar & PIN Unblock Kustom** | Diatur oleh Proktor di **Jejakawan Exam Admin** (tertanam di QR Ruang Ujian atau pengaturan server) | Menggantikan kode bawaan dengan kode unik khusus sesi/ruang ujian sekolah Anda. |
| **3. Kode Bawaan (*Default*)** | Uji coba mandiri atau Mode FREE tanpa QR kebijakan dari Admin | Sama untuk semua instalasi baru — **WAJIB diganti** pada ujian resmi sekolah. |

> **Penting untuk Sekolah / Proktor:**  
> Pada ujian resmi, **jangan menggunakan kode bawaan (*default*)**. Gunakan **Jejakawan Exam Admin** (unduh melalui [Member Area k2net.id](https://k2net.id/member/billing)) untuk membuat QR Ruang Ujian dengan **Password Keluar & PIN Unblock Kustom** atau aktifkan **Mode Token Dinamis Offline**.

---

## 3. Kode Bawaan (*Default*) — Khusus Pengawas & Uji Coba Mandiri

Kode di bawah ini **hanya berlaku** apabila ruang ujian **tidak** memakai QR kustom dari Admin, **tidak** memakai Token Dinamis Offline, dan PIN/Password belum diubah dari bawaan instalasi awal.

<details>
<summary><strong>Klik untuk melihat Kode Bawaan (Keluar, Buka Blokir & Admin Awal)</strong></summary>

<br>

| Fungsi | Kode Bawaan (*Default*) | Keterangan |
| :--- | :---: | :--- |
| **Password Keluar Sesi Ujian** (*Exit Password*) | `170845` | Dipakai untuk keluar dari mode ujian/kiosk jika tidak diatur password kustom atau token dinamis. |
| **PIN Buka Blokir / Pelanggaran** (*Unlock PIN*) | `100110` | Dipakai pengawas untuk membuka layar blokir (*Unblock*) saat terjadi pelanggaran atau meninjau log pelanggaran. |
| **PIN Pengaturan Admin** (*khusus Edisi Admin*) | `251145` | Dipakai pertama kali masuk menu Pengaturan Admin di **Jejakawan Exam Admin**; segera ubah setelah instalasi. |

**Catatan Penting:**
- Jika sekolah Anda membagikan **QR Ruang Ujian** dengan kebijakan kustom atau **Mode Token Dinamis Offline**, maka kode bawaan di atas digantikan oleh kode/token dari pengawas ruang ujian Anda.
- Jika sekolah menggunakan **Jejakawan SME** dengan fitur **Kunci Sesi (*Session Lock*)**, pembukaan blokir perangkat ganda dilakukan pengawas melalui menu **Pengawas Ujian** di dashboard Moodle SME.

</details>

---

## 4. Pertanyaan Umum (*Troubleshooting*)

- **Layar tidak mau keluar setelah ujian selesai?**  
  Minta **Password Keluar / Token** ke pengawas ruang. Jika sedang uji coba mandiri tanpa QR Admin, cek bagian *Kode Bawaan* di atas.
- **Muncul peringatan "Aplikasi Overlay / Split-Screen / Aksesibilitas Terdeteksi"?**  
  Matikan sementara fitur *floating ball / asisten sentuh / chat heads / screen recorder / VPN* di pengaturan Android, lalu buka ulang aplikasi.
- **Tidak bisa mengetik saat ujian (Jejakawan Keyboard)?**  
  Pastikan **Jejakawan Keyboard** sudah diaktifkan di *Pengaturan Android → Sistem → Bahasa & Masukan → Keyboard Virtual* dan dipilih sebagai keyboard aktif.
- **Butuh Edisi Admin & QR Aktivasi Lisensi?**  
  Tersedia khusus bagi member aktif melalui [https://k2net.id/member/billing](https://k2net.id/member/billing).

---

Dokumen terkait: [README.md](./README.md) · [Kebijakan Privasi & Kepatuhan (PRIVACY.md)](./PRIVACY.md) · [**JEJAKAWAN**](https://jejakawan.com)
