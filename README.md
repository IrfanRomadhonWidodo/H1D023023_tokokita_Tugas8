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

---

## 🖼️ Tampilan Aplikasi (Screenshot)

Screenshot aplikasi ditempatkan di folder `assets/images/`.

| Image 1 | Image 2 | Image 3 |
| :---: | :---: | :---: |
| !(assets/image1.jpeg) | !(assets/image2.jpeg) | !(assets/image3.jpeg) |
| **Image 4** | **Image 5** | **Image 6** |
| !(assets/image4.jpeg) | !(assets/image5.jpeg) | !(assets/image6.jpeg) |

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
