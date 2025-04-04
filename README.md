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

## 4. Routing Dasar
Routing di Laravel diatur dalam file `routes/web.php`. Tambahkan route berikut:
```php
Route::get('/hello', function () {
    return 'Hello, Laravel!';
});
```
Jalankan server:
```sh
php artisan serve
```
Akses `http://127.0.0.1:8000/hello` di browser untuk melihat hasilnya.

## 5. Controller dan View
### a. Membuat Controller
Untuk membuat controller, jalankan perintah:
```sh
php artisan make:controller HelloController
```

### b. Definisi Method di Controller
Edit `app/Http/Controllers/HelloController.php`:
```php
namespace App\Http\Controllers;
use Illuminate\Http\Request;

class HelloController extends Controller {
    public function index() {
        return view('hello');
    }
}
```

### c. Routing Controller
Tambahkan route di `routes/web.php`:
```php
use App\Http\Controllers\HelloController;
Route::get('/hello', [HelloController::class, 'index']);
```

### d. Membuat View
Buat file `resources/views/hello.blade.php`:
```html
<!DOCTYPE html>
<html>
<head>
    <title>Hello Laravel</title>
</head>
<body>
    <h1>Selamat datang di Laravel!</h1>
</body>
</html>
```

## 6. Database dan Eloquent ORM
### a. Konfigurasi Database
Edit file `.env` untuk mengatur koneksi database:
```
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=nama_database
DB_USERNAME=root
DB_PASSWORD=
```

### b. Membuat Model dan Migrasi
Buat model dengan migrasi:
```sh
php artisan make:model Post -m
```

Edit file migrasi di `database/migrations/`:
```php
public function up() {
    Schema::create('posts', function (Blueprint $table) {
        $table->id();
        $table->string('title');
        $table->text('content');
        $table->timestamps();
    });
}
```
Jalankan migrasi:
```sh
php artisan migrate
```

### c. Menggunakan Model
Edit `app/Models/Post.php`:
```php
namespace App\Models;
use Illuminate\Database\Eloquent\Factories\HasFactory;
use Illuminate\Database\Eloquent\Model;

class Post extends Model {
    use HasFactory;
    protected $fillable = ['title', 'content'];
}
```

### d. Menampilkan Data di Controller
Edit `HelloController.php`:
```php
use App\Models\Post;

public function index() {
    $posts = Post::all();
    return view('hello', compact('posts'));
}
```

Edit `resources/views/hello.blade.php` untuk menampilkan data:
```html
@foreach($posts as $post)
    <h2>{{ $post->title }}</h2>
    <p>{{ $post->content }}</p>
@endforeach
```

