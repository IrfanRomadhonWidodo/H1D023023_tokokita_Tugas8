# 📱 Praktikum Pemrograman Mobile: Aplikasi TokoKita CRUD Produk

---

## 🧑‍💻 Identitas Mahasiswa

| Keterangan | Data |
| :--- | :--- |
| **Nama** | Irfan Romadhon Widodo |
| **NIM** | H1D023023 |
| **Kelas / Shift** | Shift D (Awal) / Shift F (Baru) |
| **Mata Kuliah** | Praktikum Pemrograman Mobile |

---

## 📝 Deskripsi Aplikasi

Aplikasi ini merupakan implementasi UI **CRUD (Create, Read, Update, Delete) Produk** sesuai dengan Modul Pertemuan 10.

Seluruh **Action Bar (AppBar)** pada setiap halaman menggunakan nama panggilan **"Irfan"** sebagai penanda personalisasi:

* `Login`
* `Registrasi`
* `List Produk Irfan`
* `Tambah Produk Irfan`
* `Ubah Produk Irfan`
* `Detail Produk Irfan`

**Repository Project:**
`https://github.com/IrfanRomadhonWidodo/H1D023023_tokokita`

---

## 📂 Struktur Folder

Struktur folder utama proyek:
```bash
.
├── lib/
│   ├── main.dart
│   ├── model/
│   │   ├── produk.dart
│   │   ├── login.dart
│   │   └── registrasi.dart
│   └── ui/
│       ├── login_page.dart
│       ├── registrasi_page.dart
│       ├── produk_page.dart
│       ├── produk_form.dart
│       └── produk_detail.dart
└── assets/
```
---

## 🧠 Penjelasan Halaman UI

Berikut adalah penjelasan singkat mengenai setiap halaman UI, termasuk detail `AppBar`:

### 1. `login_page.dart`
* **Tujuan:** Input email & password, serta navigasi ke halaman registrasi.
* **AppBar:**
    ```dart
    title: const Text("Login")
    ```

### 2. `registrasi_page.dart`
* **AppBar:**
    ```dart
    title: const Text("Registrasi")
    ```

### 3. `produk_page.dart`
* **Tujuan:** Menampilkan daftar produk.
* **AppBar:**
    ```dart
    title: const Text("List Produk Irfan")
    ```

### 4. `produk_form.dart`
* **Tujuan:** Digunakan untuk menambah atau mengubah data produk.
* **Logika Judul (Conditional AppBar):**
    ```dart
    if (edit) "Ubah Produk Irfan";
    else "Tambah Produk Irfan";
    ```

### 5. `produk_detail.dart`
* **Tujuan:** Menampilkan detail produk yang dipilih.
* **AppBar:**
    ```dart
    title: const Text("Detail Produk Irfan")
    ```

---

## 🖼️ Tampilan Aplikasi (Screenshot)

Screenshot aplikasi ditempatkan di folder `assets/images/`.

| Image 1 | Image 2 | Image 3 |
| :---: | :---: | :---: |
| ![](/assets/images/image1.jpeg) | ![](/assets/images/image2.jpeg) | ![](/assets/images/image3.jpeg) |
| **Image 4** | **Image 5** | **Image 6** |
| ![](/assets/images/image4.jpeg) | ![](/assets/images/image5.jpeg) | ![](/assets/images/image6.jpeg) |
---

## ▶️ Cara Menjalankan Aplikasi

1.  **Install Dependency:**
    ```bash
    flutter pub get
    ```
2.  **Jalankan Aplikasi:**
    ```bash
    flutter run
    ```

---

## 📌 Catatan Tambahan

* **Data produk** yang digunakan dalam aplikasi ini masih **dummy / statis**.
* **User Interface (UI)** dikembangkan sepenuhnya sesuai dengan panduan **Modul Pertemuan 10**.
* Semua **AppBar** konsisten menggunakan nama panggilan **"Irfan"**.
* File-file **Screenshot** aplikasi berada di direktori `assets/`.


---
# 📱 Praktikum Pemrograman Mobile: Aplikasi TokoKita CRUD Produk Pertemuan 11

## 📂 Struktur Folder Proyek
Proyek ini menggunakan struktur folder yang memisahkan lapisan UI, Model, dan Logika Bisnis/API.
```bash
.
├── lib/
│   ├── main.dart
│   ├── helpers/                 # Lapisan API, UserInfo (SharedPreferences), dan Error Handling
│   │   ├── api.dart             # Klien HTTP (POST, GET, PUT, DELETE) dengan Auth Bearer Token
│   │   ├── api_url.dart         # Konfigurasi Endpoints API
│   │   ├── app_exception.dart   # Custom Exception untuk Error Handling
│   │   └── user_info.dart       # Manajemen sesi (SharedPreferences)
│   ├── model/                   # Lapisan Data Model (Parsing JSON)
│   │   ├── produk.dart
│   │   ├── login.dart
│   │   └── registrasi.dart
│   ├── bloc/                    # Lapisan Business Logic Component (BLOC) / Service Layer
│   │   ├── login_bloc.dart      # Logika Login
│   │   ├── produk_bloc.dart     # Logika CRUD Produk
│   │   ├── registrasi_bloc.dart # Logika Registrasi
│   │   └── logout_bloc.dart     # Logika Logout
│   └── ui/                      # Lapisan User Interface (Halaman)
│       ├── login_page.dart
│       ├── registrasi_page.dart
│       ├── produk_page.dart
│       ├── produk_form.dart
│       └── produk_detail.dart
└── assets/
```
---
## 🧠 Implementasi Pertemuan 11: BLOC & API
Pertemuan 11 berfokus pada implementasi arsitektur berlapis untuk menghubungkan UI dengan API backend.

### 1. `Arsitektur Aplikasi (BLOC/Service Layer)`
Aplikasi dibangun dengan memisahkan tiga lapisan utama:
- UI Layer (ui/): Hanya bertanggung jawab menampilkan antarmuka dan menerima input pengguna. Memanggil fungsi dari BLOC.
- Business Logic Layer (BLOC) (bloc/): Bertanggung jawab atas logika bisnis (misal: validasi, pemanggilan API, transformasi data). Memanggil fungsi di helpers/api.dart.
- Data Access Layer (API) (helpers/): Bertanggung jawab atas komunikasi jaringan (HTTP Requests) dan penyimpanan sesi lokal (user_info.dart).

### 2. `File Kunci dan Fungsinya`
| File                 | Kategori | Fungsi Utama                                                                                                                  |
| -------------------- | :------: | ----------------------------------------------------------------------------------------------------------------------------- |
| `api.dart`           |  Service | Mengirim semua permintaan HTTP (POST, GET, PUT, DELETE) dan otomatis menambahkan header `Authorization: Bearer <token>`       |
| `app_exception.dart` |  Service | Custom exception untuk handling error response seperti `401 Unauthorized`, `500 Server Error`, dll                            |
| `user_info.dart`     |  Service | Menyimpan & mengambil Token dan User ID menggunakan `SharedPreferences` agar sesi login tetap tersimpan                       |
| `produk_bloc.dart`   |   BLoC   | Menyediakan fungsi `getProduks()`, `addProduk()`, `updateProduk()`, `deleteProduk()` sebagai logic CRUD yang terhubung ke API |
| `login_bloc.dart`    |   BLoC   | Mengirim kredensial user ke API, menerima token jika login berhasil, lalu menyimpannya ke `SharedPreferences`                 |
| `produk.dart`        |   Model  | Mem-parsing JSON produk dari API menjadi objek Dart untuk memudahkan pengolahan data di UI                                    |

---

## 🖼️ Tampilan Aplikasi (Screenshot UI Pertemuan 11)
| Image 1 | Image 2 | Image 3 |
| :---: | :---: | :---: |
| ![](/assets/images/image7.jpeg) | ![](/assets/images/image8.jpeg) | ![](/assets/images/image3.jpeg) |
| **Image 4** | **Image 5** | **Image 6** |
| ![](/assets/images/image4.jpeg) | ![](/assets/images/image5.jpeg) | ![](/assets/images/image6.jpeg) |
---

## ▶️ Cara Menjalankan Aplikasi

1.  **Install Dependency:**
    ```bash
    flutter pub get
    ```
2.  **Jalankan Aplikasi:**
    ```bash
    flutter run
    ```

---
