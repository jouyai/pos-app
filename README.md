# Aplikasi POS (Point of Sale) Full-Stack

Selamat datang di proyek Aplikasi POS Full-Stack! Ini adalah aplikasi Point of Sale modern berbasis web yang dirancang untuk membantu bisnis kecil, terutama di bidang F&B, mengelola produk, kategori, dan mencatat transaksi penjualan dengan antarmuka yang bersih dan responsif.

**[Live Demo](https://fe-pos-gamma.vercel.app)**

---

## ✨ Fitur Utama

Aplikasi ini dibagi menjadi dua bagian utama: antarmuka pengguna (Frontend) dan API server (Backend).

#### **Fitur Frontend (Untuk Pengguna):**
* **Dashboard Interaktif**: Menampilkan ringkasan bisnis seperti pendapatan harian dan produk terlaris dengan grafik.
* **Halaman Kasir (POS)**: Antarmuka utama untuk melakukan transaksi, dengan filter kategori dan keranjang belanja yang dinamis.
* **Manajemen Produk**: Halaman khusus untuk menambah, mengedit (termasuk status ketersediaan), dan menghapus produk.
* **Riwayat Transaksi**: Tampilan daftar semua transaksi yang pernah terjadi, dengan kemampuan untuk melihat detail setiap penjualan.
* **Desain Responsif**: Tampilan dioptimalkan untuk berbagai ukuran layar, dari desktop hingga mobile (menggunakan layout kartu dan tab).
* **Notifikasi Modern**: Menggunakan `react-hot-toast` untuk feedback yang tidak mengganggu.

#### **Fitur Backend (API):**
* **Otentikasi Aman**: Sistem registrasi dan login menggunakan JSON Web Tokens (JWT).
* **REST API Lengkap**: Menyediakan endpoint untuk semua kebutuhan CRUD (Create, Read, Update, Delete) pada produk, kategori, dan transaksi.
* **Endpoint Teragregasi**: API khusus untuk dashboard yang melakukan kalkulasi data di server untuk efisiensi.
* **Proteksi Rute**: Middleware untuk memastikan hanya pengguna terotentikasi yang dapat mengakses data bisnis.

---

## 🛠️ Tech Stack

| Layer | Teknologi | Tujuan |
| :--- | :--- | :--- |
| **Frontend** | React.js (dengan Vite) | Membangun antarmuka pengguna yang interaktif. |
| | Tailwind CSS | Styling yang cepat dan responsif. |
| | React Query | Manajemen state server (fetching, caching). |
| | React Router | Navigasi antar halaman. |
| | Recharts | Visualisasi data dan pembuatan grafik. |
| | Axios | Klien HTTP untuk berkomunikasi dengan API. |
| | React Hot Toast | Notifikasi modern. |
| **Backend** | Node.js | Lingkungan eksekusi JavaScript di server. |
| | Express.js | Framework untuk membangun REST API. |
| | PostgreSQL | Database relasional untuk menyimpan semua data. |
| | JWT & bcrypt.js | Otentikasi dan hashing password. |
| **Deployment**| Vercel / Netlify | Hosting untuk Frontend. |
| | Railway | Hosting untuk Backend & Database. |

---

## 📁 Struktur Proyek

Proyek ini diorganisir dalam struktur monorepo sederhana:
/
├── client/     # Berisi semua kode Frontend (React)
└── server/     # Berisi semua kode Backend (Node.js/Express)
└── README.md   # Dokumentasi

---

## 🚀 Instalasi & Setup Lokal

Untuk menjalankan proyek ini secara lokal, Anda perlu menjalankan **backend** dan **frontend** secara bersamaan di dua terminal terpisah.

### **Setup Backend:**

1.  **Masuk ke direktori `server`:**
    ```bash
    cd server
    ```
2.  **Install dependensi:**
    ```bash
    npm install
    ```
3.  **Buat file `.env`** dan isi dengan variabel berikut:
    ```env
    DATABASE_URL="postgresql://user:password@host:port/database"
    PORT=3001
    JWT_SECRET="secret_key_anda_yang_panjang_dan_aman"
    ```
4.  **Jalankan server backend:**
    ```bash
    npm run dev
    ```
    Server akan berjalan di `http://localhost:3001`.

### **Setup Frontend:**

1.  **Buka terminal baru.** Masuk ke direktori `client`:
    ```bash
    cd client
    ```
2.  **Install dependensi:**
    ```bash
    npm install
    ```
3.  **Buat file `.env.local`** dan arahkan ke alamat backend lokal Anda:
    ```env
    VITE_API_URL="http://localhost:3001"
    ```
4.  **Jalankan server frontend:**
    ```bash
    npm run dev
    ```
    Aplikasi akan berjalan di `http://localhost:5173`.

Setelah kedua server berjalan, buka `http://localhost:5173` di browser Anda.

---

## 📝 Ringkasan API Endpoints

Semua endpoint API diawali dengan base URL (misal: `http://localhost:3001`). Semua endpoint yang ditandai "Ya" memerlukan token JWT pada `Authorization` header.

| Method | Endpoint | Deskripsi | Dilindungi? |
| :--- | :--- | :--- | :---: |
| `POST` | `/api/auth/register` | Mendaftarkan pengguna baru. | ❌ Tidak |
| `POST` | `/api/auth/login` | Login pengguna. | ❌ Tidak |
| `GET` | `/api/categories` | Mendapatkan semua kategori. | ✅ Ya |
| `POST` | `/api/categories` | Membuat kategori baru. | ✅ Ya |
| `GET` | `/api/products` | Mendapatkan semua produk. | ✅ Ya |
| `POST`| `/api/products` | Membuat produk baru. | ✅ Ya |
| `PUT` | `/api/products/:id` | Memperbarui produk. | ✅ Ya |
| `DELETE`| `/api/products/:id` | Menghapus produk. | ✅ Ya |
| `POST`| `/api/transactions` | Membuat transaksi baru. | ✅ Ya |
| `GET` | `/api/transactions` | Mendapatkan riwayat transaksi. | ✅ Ya |
| `GET` | `/api/transactions/:id`| Mendapatkan detail transaksi. | ✅ Ya |
| `GET` | `/api/dashboard/summary`| Mendapatkan ringkasan dashboard. | ✅ Ya |
