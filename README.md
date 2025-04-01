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


## 5. Controller dan View
### a. Membuat Controller
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
Edit file `.env`:
```
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=nama_database
DB_USERNAME=root
DB_PASSWORD=
```

### b. Membuat Model dan Migrasi
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

Edit `resources/views/hello.blade.php`:
```html
@foreach($posts as $post)
    <h2>{{ $post->title }}</h2>
    <p>{{ $post->content }}</p>
@endforeach
```
