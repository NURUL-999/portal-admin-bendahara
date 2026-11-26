# Portal Registrasi Admin | Alfatih - Bendahara

Portal web khusus yang digunakan oleh pengurus inti untuk membuat, mengelola, dan menghapus akun **Admin Bendahara**. Aplikasi ini terhubung langsung ke **Firebase Realtime Database** milik sistem utama **Alfatih - Bendahara**, sehingga setiap akun Admin yang dibuat di portal ini otomatis tersinkronisasi dan dapat langsung digunakan untuk *login* di aplikasi utama dari perangkat mana pun.

---

## Fitur Utama

* **Keamanan Gerbang Master PIN:** Halaman dilindungi oleh PIN khusus pengurus sebelum dapat mengakses formulir pembuatan akun Admin.
* **Sinkronisasi Cloud Real-Time:** Terhubung langsung ke Firebase Realtime Database (`alfatih_bendahara_store/users`) tanpa mengganggu data santri maupun laporan keuangan yang sudah ada.
* **Validasi Username Admin:** Memastikan setiap *username* Admin memenuhi standar keamanan (wajib mengandung kombinasi angka dan simbol, seperti `galih_01` atau `admin#2`).
* **Salin Kredensial Cepat:** Tersedia tombol **Salin Akun** untuk menyalin pesan berisi *Username* dan *Kata Sandi* agar mudah dibagikan kepada pengurus baru.
* **Manajemen Akun Admin:** Melihat daftar seluruh akun Admin yang aktif serta menghapus akses Admin yang sudah tidak bertugas.

---

## Struktur Proyek

```text
portal-admin-alfatih/
├── index.html      # Halaman utama portal (UI Tailwind CSS + Logika Firebase)
└── README.md       # Dokumentasi penggunaan dan konfigurasi
```

---

## Konfigurasi Sebelum Deploy

Buka file `index.html` dan sesuaikan dua variabel konfigurasi pada bagian `<script>` jika diperlukan:

1. **URL Firebase Realtime Database:**
   Pastikan URL database sudah sesuai dengan proyek Firebase aplikasi utama Anda:
   ```javascript
   const CLOUD_DB_URL = 'https://bendahara-alfatih-pnb-default-rtdb.asia-southeast1.firebasedatabase.app';
   ```

2. **Master PIN Keamanan:**
   Ubah PIN bawaan (`123456`) menjadi kombinasi angka rahasia milik pengurus:
   ```javascript
   const MASTER_PIN = '123456';
   ```

---

## Cara Deploy ke Vercel

1. Unggah file `index.html` dan `README.md` ke repository GitHub baru (misalnya `portal-admin-alfatih`).
2. Masuk ke dasbor [Vercel](https://vercel.com/), klik **Add New... > Project**.
3. Pilih repository `portal-admin-alfatih`, lalu klik **Deploy** (tidak perlu pengaturan *build command* karena menggunakan HTML statis).
4. Setelah proses *deploy* selesai, simpan tautan URL Vercel tersebut khusus untuk pengurus inti.

---

## Alur Penggunaan

1. **Buka Portal:** Akses tautan website Portal Registrasi Admin dan masukkan **Master PIN**.
2. **Buat Akun Admin:** Isi **Nama Lengkap**, **Username** (mengandung angka & simbol), dan **Kata Sandi** (minimal 6 karakter), lalu klik **Simpan Akun Admin ke Cloud**.
3. **Bagikan Akses:** Klik tombol **Salin Akun** pada daftar akun di sebelah kanan untuk mengirimkan *Username* dan *Kata Sandi* ke pengurus yang bersangkutan.
4. **Login di Aplikasi Utama:** Pengurus tersebut dapat langsung membuka website utama **Alfatih - Bendahara** dan masuk menggunakan *Username* serta *Kata Sandi* yang baru dibuat.

---

## Catatan Keamanan

* Jangan membagikan tautan portal ini maupun **Master PIN** kepada Wali Santri atau pihak luar.
* Pastikan aturan (*Rules*) pada **Firebase Realtime Database** sudah mengizinkan operasi baca/tulis (`.read` dan `.write`) agar proses sinkronisasi berjalan lancar.