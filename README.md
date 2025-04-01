# Belajar Laravel

## 1. Pendahuluan
Laravel adalah framework PHP yang populer dan digunakan untuk membangun aplikasi web dengan sintaks yang elegan dan efisien.

### Kelebihan Laravel:
- Sintaks yang elegan dan mudah dipahami.
- Memiliki ORM (Eloquent) yang kuat untuk database.
- Routing yang fleksibel.
- Middleware dan Authentication bawaan.
- Dukungan penuh untuk API development.

## 2. Instalasi Laravel

### a. Persyaratan Sistem
Sebelum menginstal Laravel, pastikan sistem Anda memiliki:
- PHP >= 8.0
- Composer
- MySQL atau database lain yang didukung
- Node.js (Opsional untuk frontend build)

### b. Instalasi dengan Composer
```sh
composer create-project --prefer-dist laravel/laravel nama_proyek
```
Atau dengan perintah global:
```sh
laravel new nama_proyek
```

## 3. Struktur Direktori Laravel
- **app/** → Berisi logika aplikasi (Models, Controllers, Middleware, dll.)
- **routes/** → Berisi definisi routing
- **resources/views/** → Berisi tampilan berbasis Blade
- **database/migrations/** → Berisi file migrasi database
- **config/** → Berisi konfigurasi aplikasi

## 4. Routing Dasar
Buka file `routes/web.php` dan tambahkan route berikut:
```php
Route::get('/hello', function () {
    return 'Hello, Laravel!';
});
```

Jalankan server dengan perintah:
```sh
php artisan serve
```
Akses `http://127.0.0.1:8000/hello`

