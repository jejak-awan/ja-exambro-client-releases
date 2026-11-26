# Kebijakan Privasi, Kepatuhan & Tanggung Jawab Data — Jejakawan Exam

**Berlaku efektif:** 27 November 2026  
**Pengembang Perangkat Lunak:** [JEJAKAWAN](https://jejakawan.com)  
**Cakupan Aplikasi:** Jejakawan Exam Client (`com.jejakawan.platform.student`) & Jejakawan Exam Admin (`com.jejakawan.platform.admin`)  
**Halaman Web Resmi:** [https://cdn.jejakawan.com/exambro/privacy.html](https://cdn.jejakawan.com/exambro/privacy.html)

---

## 1. Prinsip Utama: *Zero-Collection*, Transparansi & Arsitektur Mandiri

**JEJAKAWAN tidak mengumpulkan, menyimpan, menjual, memprofilkan, maupun memiliki akses terhadap data pribadi peserta didik, jawaban ujian, rekaman proctoring, atau isi sesi ujian.**

Jejakawan Exam dirancang sebagai **perangkat lunak klien ujian mandiri (*standalone exam browser*)** yang berjalan langsung di perangkat Android pengguna dan berkomunikasi langsung dengan **server ujian / LMS milik sekolah atau institusi penyelenggara ujian**.

- **Tanpa SDK Pelacak:** Aplikasi tidak menyertakan Firebase Analytics, Crashlytics, Sentry, SDK iklan (AdMob/Meta), atau telemetri perilaku pihak ketiga mana pun.
- **Tanpa Database Peserta di JEJAKAWAN:** Seluruh kredensial login LMS, soal, jawaban, nilai, dan log ujian berada sepenuhnya di infrastruktur server sekolah/institusi atau lokal di perangkat pengguna.
- **Pengawasan Transparan (Tidak Pernah Diam-Diam):** Apabila sekolah mengaktifkan pengawasan kamera atau audio, aplikasi selalu menampilkan **indikator langsung di layar peserta** (`Kamera Pengawas Aktif` / `Audio Pengawas Aktif — diproses lokal`) agar peserta mengetahui secara terbuka bahwa pengawasan sedang berjalan.
- **Bukti Pelanggaran Terenkripsi Lokal (*Zero Auto-Upload*):** Foto bukti pelanggaran (bila diaktifkan kebijakan sekolah) disimpan **terenkripsi secara lokal** di perangkat peserta dan **tidak pernah diunggah otomatis**. Bukti hanya dapat ditinjau, dibagikan secara lokal sementara (*cache* otomatis bersih), atau dikirim secara manual ke server Moodle SME milik sekolah oleh pengawas berwenang dengan memasukkan **PIN Pengawas**.

---

## 2. Peran Hukum & Kepatuhan Standar Industri (UU PDP & GDPR)

Mengacu pada **UU No. 27 Tahun 2022 tentang Pelindungan Data Pribadi (UU PDP)** dan prinsip **General Data Protection Regulation (GDPR — EU 2016/679)** serta standar **Google Play Data Safety**:

| Peran | Pihak | Kedudukan & Kewajiban |
| :--- | :--- | :--- |
| **Penyedia Perangkat Lunak Mandiri** (*Independent Tool Provider*) | [**JEJAKAWAN**](https://jejakawan.com) | Menyediakan aplikasi klien Android terverifikasi (*signed production release*). **Bukan** Pengendali Data (*Data Controller*) dan **bukan** penyimpan data ujian/peserta. |
| **Pengendali Data Pribadi** (*Data Controller*) | **Sekolah / Institusi Penyelenggara Ujian** (atau pengguna mandiri) | Menentukan tujuan, dasar hukum, konfigurasi fitur keamanan/proctoring, retensi, keamanan server, dan pemenuhan hak subjek data peserta ujian. |

---

## 3. Model Tanggung Jawab Bersama (*Shared Responsibility Model*)

### A. Tanggung Jawab JEJAKAWAN
1. Menjaga integritas kode sumber, proses build, dan penandatanganan APK rilis resmi.
2. Menerapkan prinsip *data minimization* dan pemrosesan lokal (*on-device processing*) untuk fitur keamanan dan anti-kecurangan.
3. Memberikan transparansi penuh atas seluruh izin Android dan koneksi jaringan yang dilakukan aplikasi.

### B. Tanggung Jawab Penuh Pengguna & Institusi Penyelenggara Ujian
Pengguna akhir dan/atau sekolah/institusi penyelenggara ujian **bertanggung jawab penuh** atas:
1. **Keamanan Data & Infrastruktur Server Sendiri:** Pengamanan server LMS/CBT (HTTPS/TLS, firewall, kontrol akses, backup, dan pencegahan kebocoran database).
2. **Konfigurasi Kebijakan & Pengelolaan Kredensial:** Pembuatan QR Ruang Ujian, penyimpanan PIN Admin, token API server sekolah, dan pengelolaan kunci lisensi.
3. **Kepatuhan Hukum & Persetujuan Peserta (*Informed Consent*):** Pemberitahuan privasi kepada siswa/orang tua serta pelaksanaan penilaian dampak privasi (DPIA) apabila institusi mengaktifkan fitur opsional seperti proctoring kamera, audio, geofencing GPS, atau sinkronisasi log server.
4. **Retensi & Penghapusan Data:** Menentukan masa simpan dan menghapus data ujian di server sekolah sesuai ketentuan institusi dan peraturan perundang-undangan yang berlaku.
5. **Keamanan Perangkat Fisik:** Memastikan perangkat peserta/pengawas bebas dari malware, modifikasi sistem ilegal, atau akses pihak tidak berwenang.

---

## 4. Transparansi Lalu Lintas Jaringan (Audit Kode Sumber)

Secara teknis, aplikasi hanya melakukan koneksi jaringan terbatas berikut:

| Tujuan Koneksi | Edisi | Data yang Dikirim | Keterangan |
| :--- | :--- | :--- | :--- |
| **Server Ujian / LMS Sekolah** (URL dari QR / pengaturan sekolah, mis. `/local/jejakawan/exambro_api.php`) | Client & Admin | Lalu lintas WebView LMS, *handshake* keamanan HMAC-SHA256 (token perangkat acak non-hardware), laporan pelanggaran (`report_event`), *heartbeat* status/buka-kunci proktor (`heartbeat`, `proctor_local_unlock`), sinkronisasi aturan (`push_policy`/`pull_policy`), serta kirim bukti foto **khusus atas aksi manual Pengawas via PIN (`upload_evidence`)** **hanya jika dikonfigurasi sekolah** | Langsung antara perangkat dan server sekolah — **tidak melewati server JEJAKAWAN**. |
| **Manifest Update Publik** (`GET https://cdn.jejakawan.com/exambro/latest.json`) | Client & Admin | Permintaan `GET` statis untuk mengecek nomor versi terbaru | **Tidak mengirim** data pribadi, ID siswa, atau informasi ujian. |
| **Verifikasi Lisensi Instansi** (`POST https://cp.k2net.id/api/v1/license/verify`) | **Admin saja** (saat aktivasi) | `domain` sekolah, `license_key`, kode produk, ID instalasi anonim, dan versi aplikasi | Hanya untuk validasi lisensi instansi pada aplikasi Admin; **tanpa data siswa**. |

### Catatan Formulir Unduh Halaman Web CDN (`cdn.jejakawan.com/exambro/`)
Berbeda dari **aplikasi Android** yang 100% *Zero-Collection*, halaman web unduh publik di `cdn.jejakawan.com/exambro/` meminta input **Nama**, **Nama Sekolah/Instansi**, dan **Peran** sebelum mengunduh APK semata-mata untuk **penghitung agregat jumlah unduhan dan jumlah sekolah/instansi pengguna**. Data formulir web ini:
- **Tidak pernah ditampilkan per-individu ke publik** (halaman web hanya menampilkan angka total agregat).
- **Tidak dijual atau dibagikan ke pihak ketiga.**
- **Terpisah sepenuhnya** dan tidak pernah dihubungkan dengan aktivitas maupun jawaban ujian di dalam aplikasi Android.

---

## 5. Penggunaan Izin Sensitif Android & Pemrosesan Lokal (*On-Device*)

Seluruh izin sensitif hanya digunakan secara lokal saat sesi ujian berlangsung untuk menjaga integritas ujian, dan **tidak pernah dikirim atau dijual ke JEJAKAWAN**:

| Izin / Kemampuan | Tujuan Fungsional | Pemrosesan |
| :--- | :--- | :--- |
| **`QUERY_ALL_PACKAGES` & `PACKAGE_USAGE_STATS`** | Mendeteksi aplikasi terlarang, *cloning/virtual app*, atau aplikasi mengambang (*overlay*) selama ujian | 100% lokal di perangkat; daftar aplikasi tidak dikirim ke JEJAKAWAN. |
| **`HIDE_OVERLAY_WINDOWS` & `SYSTEM_ALERT_WINDOW`** | Memblokir jendela mengambang pihak ketiga di atas layar ujian (Android 12+) | 100% lokal di sistem Android. |
| **`DETECT_SCREEN_CAPTURE`** | Mendeteksi upaya tangkapan layar (*screenshot*) atau perekaman layar saat ujian | 100% lokal di perangkat. |
| **`CAMERA` (ML Kit Face Detection & Barcode)** | Scan QR Ruang Ujian dan (opsional tier *Organization/Enterprise*) hitung jumlah wajah untuk proctoring | Deteksi wajah & QR berjalan **on-device** via Google ML Kit tanpa profil biometrik, dengan indikator aktif transparan di layar. Foto bukti (bila diaktifkan) tersimpan terenkripsi lokal (tanpa *auto-upload*) dan tidak pernah dikirim ke server JEJAKAWAN. |
| **`RECORD_AUDIO`** | (Opsional tier *Organization/Enterprise*) Mengukur ambang kebisingan suara (desibel) selama ujian | Hanya memantau amplitudo/desibel lokal di cache sementara perangkat (otomatis jeda saat alarm blokir berbunyi) dengan indikator transparan di layar; tidak dikirim ke JEJAKAWAN. |
| **`ACCESS_FINE_LOCATION` / `COARSE_LOCATION`** | (Opsional tier *Enterprise*) Memverifikasi radius lokasi ujian (*Geofencing*) | Perhitungan jarak (*Haversine*) dilakukan lokal di perangkat terhadap koordinat yang diatur sekolah. |
| **`BLUETOOTH`, `READ_PHONE_STATE`** | (Opsional tier *Pro+*) Mendeteksi perangkat audio Bluetooth/headset dan status kartu SIM selama sesi ujian | Status diperiksa lokal; tidak mengambil nomor telepon/IMEI untuk JEJAKAWAN. |
| **Google Play Integrity API** | (Opsional tier *Enterprise*) Memastikan keaslian aplikasi & integritas perangkat | Token integritas diverifikasi hanya terhadap server ujian yang dikonfigurasi sekolah. |

> **Catatan Token Perangkat:** Untuk fitur *Session Lock* pada server Jejakawan SME, aplikasi membuat token acak 64-karakter (`SecureRandom`) khusus lingkup aplikasi — **bukan IMEI, bukan MAC address, dan bukan nomor seri perangkat keras**. Token terhapus otomatis saat data aplikasi dibersihkan atau aplikasi di-uninstall.

---

## 6. Kontrol Data Lokal & Hak Subjek Data

- **Kontrol di Perangkat:** Pengguna dapat menghapus seluruh konfigurasi ruang ujian, foto bukti terenkripsi lokal, cache WebView, cookie, dan data lokal kapan saja melalui menu **Reset Konfigurasi** di dalam aplikasi, melalui *Settings → Apps → Clear Storage/Data* Android, atau dengan mencopot (*uninstall*) aplikasi.
- **Permintaan Akses, Koreksi, atau Penghapusan Data Ujian:** Karena JEJAKAWAN tidak menyimpan data peserta maupun hasil ujian, segala permintaan terkait hak subjek data (sesuai UU PDP / GDPR — termasuk penghapusan log integritas dan foto bukti `exambro_evidence` yang dikirim manual pengawas melalui Moodle Privacy API) harus disampaikan langsung kepada **Sekolah / Institusi Penyelenggara Ujian** selaku Pengendali Data.

---

## 7. Batasan Tanggung Jawab (*Limitation of Liability & Disclaimer*)

1. Perangkat lunak Jejakawan Exam disediakan **"sebagaimana adanya" (*as-is*)** sebagai sarana pendukung pelaksanaan ujian berbasis komputer (CBT).
2. **JEJAKAWAN tidak bertanggung jawab** atas kehilangan data, kebocoran data, gangguan layanan, salah konfigurasi kebijakan keamanan, pelanggaran privasi, atau sengketa hasil ujian yang timbul pada server LMS, jaringan, maupun perangkat yang dikelola oleh sekolah, institusi, atau pengguna akhir.
3. Kebijakan ini dapat diperbarui sewaktu-waktu seiring pembaruan versi aplikasi atau regulasi yang berlaku; versi terbaru selalu tersedia di [https://cdn.jejakawan.com/exambro/privacy.html](https://cdn.jejakawan.com/exambro/privacy.html) dan repositori ini.

---

## 8. Kontak & Pelaporan Keamanan

Untuk pertanyaan terkait kebijakan privasi perangkat lunak atau pelaporan celah keamanan (*security disclosure*), silakan hubungi [**JEJAKAWAN**](https://jejakawan.com) melalui situs resmi [https://jejakawan.com](https://jejakawan.com) atau portal pelanggan [https://k2net.id](https://k2net.id).
