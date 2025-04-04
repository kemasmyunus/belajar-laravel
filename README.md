# Belajar Laravel

## 1. Pendahuluan
Laravel adalah framework PHP yang populer dan digunakan untuk membangun aplikasi web dengan sintaks yang elegan dan efisien. Laravel mengikuti pola arsitektur MVC (Model-View-Controller) yang membantu dalam pengembangan aplikasi yang terstruktur dan mudah dikelola.

### Kelebihan Laravel:
- **Sintaks yang elegan**: Laravel menawarkan kode yang bersih dan mudah dibaca.
- **ORM (Eloquent) yang kuat**: Memudahkan interaksi dengan database menggunakan sintaks yang sederhana.
- **Routing yang fleksibel**: Memungkinkan pengelolaan rute dengan cara yang mudah dipahami.
- **Middleware dan Authentication bawaan**: Laravel memiliki fitur keamanan yang sudah terintegrasi.
- **Dukungan penuh untuk API development**: Laravel mendukung pengembangan RESTful API dengan mudah.
- **Task scheduling**: Memungkinkan penjadwalan tugas dengan fitur `Laravel Scheduler`.
- **Testing yang kuat**: Laravel menyediakan fitur testing bawaan untuk memastikan aplikasi berjalan dengan baik.

## 2. Instalasi Laravel

### a. Persyaratan Sistem
Sebelum menginstal Laravel, pastikan sistem Anda memiliki:
- PHP >= 8.0
- Composer (Dependency Manager untuk PHP)
- Database (MySQL, PostgreSQL, SQLite, atau SQL Server)
- Node.js & npm (Opsional untuk frontend build dan asset bundling)

### b. Instalasi dengan Composer
Untuk menginstal Laravel, jalankan perintah berikut di terminal:
```sh
composer create-project --prefer-dist laravel/laravel nama_proyek
```
Atau dengan perintah global jika Laravel Installer sudah terpasang:
```sh
laravel new nama_proyek
```
Setelah instalasi selesai, masuk ke direktori proyek:
```sh
cd nama_proyek
```
Jalankan server pengembangan Laravel:
```sh
php artisan serve
```
Buka browser dan akses `http://127.0.0.1:8000/` untuk melihat tampilan default Laravel.

## 3. Struktur Direktori Laravel
Berikut adalah struktur utama direktori Laravel:
- **app/** → Berisi logika aplikasi (Models, Controllers, Middleware, dll.)
- **bootstrap/** → Berisi file bootstrapping untuk inisialisasi aplikasi
- **config/** → Berisi file konfigurasi aplikasi
- **database/** → Berisi file migrasi dan seeder database
- **public/** → Direktori publik untuk file statis dan entry point aplikasi (`index.php`)
- **resources/** → Berisi file view (Blade template), CSS, dan JavaScript
- **routes/** → Berisi definisi routing aplikasi
- **storage/** → Berisi log, cache, dan file sementara
- **tests/** → Direktori untuk pengujian aplikasi
