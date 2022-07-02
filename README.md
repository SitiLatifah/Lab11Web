# Lab11Web
**Nama	 : Siti Latifah** <br>
**NIM	   : 312010321** <br>
**Kelas	 : TI.20.A2** <br>
**Matkul : Pemrograman Web** <br>

# PHP FRAMEWORK (Codeigniter)

1. Untuk mengaktifkan ekstentsi tersebut, melalu XAMPP Control Panel, pada bagian
Apache klik Config -> PHP.ini. Pada bagian extention, hilangkan tanda ; (titik koma) pada ekstensi yang akan diaktifkan. Kemudian simpan kembali filenya dan restart Apache web server seperti dibawah ini :

![Screenshot (326)](https://user-images.githubusercontent.com/73010098/176989719-a4769691-5e4c-4a91-a0af-fa543ea838f0.png)

2. Instalasi Codeigniter 4
Untuk melakukan instalasi Codeigniter 4 dapat dilakukan dengan dua cara, yaitu cara
manual dan menggunakan composer. Pada praktikum ini kita menggunakan cara
manual.
• Unduh Codeigniter dari website https://codeigniter.com/download
• Extrak file zip Codeigniter ke direktori htdocs/lab11_ci.
• Ubah nama direktory framework-4.x.xx menjadi ci4.
• Buka browser dengan alamat http://localhost/lab11_ci/ci4/public/

![Screenshot (327)](https://user-images.githubusercontent.com/73010098/176989775-33bf6d5c-93a0-4e6b-890f-47dbd7ee6cbf.png)

3. Menjalankan CLI (Command Line Interface)
Codeigniter 4 menyediakan CLI untuk mempermudah proses development. Untuk
mengakses CLI buka terminal/command prompt.

![Screenshot (329)](https://user-images.githubusercontent.com/73010098/176989797-ebbfe611-d667-46f7-bc2a-155755b8ac9f.png)

4. Mengaktifkan Mode Debugging
Codeigniter 4 menyediakan fitur debugging untuk memudahkan developer untuk
mengetahui pesan error apabila terjadi kesalahan dalam membuat kode program.
Secara default fitur ini belum aktif. Ketika terjadi error pada aplikasi akan ditampilkan
pesan kesalahan seperti berikut.

![Screenshot (338)](https://user-images.githubusercontent.com/73010098/176989832-5497043a-4069-4984-ac90-8fe7be927cb9.png)

Semua jenis error akan ditampilkan sama. Untuk memudahkan mengetahui jenis
errornya, maka perlu diaktifkan mode debugging dengan mengubah nilai konfigurasi
pada environment variable CI_ENVIRINMENT menjadi development.

![Screenshot (336)](https://user-images.githubusercontent.com/73010098/176989870-f5ab2c4a-a9c3-49c1-a471-b118247c3ee1.png)

# Program Sederhana Menggunakan Framework Codeigneter 4

## Membuat Route Baru
Tambahkan kode berikut ini dalam file Routes.php
``` php
$routes->get('/about', 'Page::about');
$routes->get('/contact', 'Page::contact');
$routes->get('/faqs', 'Page::faqs');
```
Untuk mengetahui route yang ditambahkan sudah benar, buka CLI dan jalankan
perintah berikut. ``` php spark routes ```

![Screenshot (339)](https://user-images.githubusercontent.com/73010098/176989966-f65720dd-ee42-4957-ba4e-59a439a964d6.png)

Selanjutnya coba akses route yang telah dibuat dengan mengakses alamat url
http://localhost:8080/about

![Screenshot (340)](https://user-images.githubusercontent.com/73010098/176989996-408572fb-3c63-4303-9f33-bbc5f81076ca.png)

## Membuat Controller
Selanjutnya adalah membuat Controller Page. Buat file baru dengan nama page.php
pada direktori Controller kemudian isi kodenya seperti berikut.
``` php
<?php

namespace App\Controllers;

class Page extends BaseController
{
    public function about()
    {
       echo "Ini adalah halaman About";

    }

    public function contact()
    {
        echo "Ini adalah halaman Contact";

    }

    public function faqs()
    {
        echo "Ini adalah halaman FAQ";
    }
}
```
Selanjutnya akses dengan alamat url http://localhost:8080/about

![Screenshot (342)](https://user-images.githubusercontent.com/73010098/176990034-c9ad616b-a24a-486f-b584-201a26aed89f.png)

## Auto Routing
Secara default fitur autoroute pada Codeiginiter sudah aktif. Untuk mengubah status
autoroute dapat mengubah nilai variabelnya. Untuk menonaktifkan ubah nilai true
menjadi false.
``` $routes->setAutoRoute(true);```
Tambahkan method baru pada Controller Page seperti berikut.
``` php
public function tos()
{
echo "ini halaman Term of Services";
}
```
Method ini belum ada pada routing, sehingga cara mengaksesnya dengan menggunakan
alamat: http://localhost:8080/page/tos

![Screenshot (353)](https://user-images.githubusercontent.com/73010098/176990114-6255e013-90c2-4421-8b29-0d119e26bcf7.png)

## Membuat View
Selanjutnya adalam membuat view untuk tampilan web agar lebih menarik. Buat file
baru dengan nama about.php pada direktori view (app/view/about.php) kemudian isi
kodenya seperti berikut.
``` php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title><?= $title; ?></title>
</head>
<body>
    <h1><?= $title; ?></h1>
    <hr>
    <p><?= $content; ?></p>
</body>
</html>
```
Ubah method about pada class Controller Page menjadi seperti berikut:
``` php
public function about()
{
return view('about', [
'title' => 'Halaman Abot',
'content' => 'Ini adalah halaman abaut yang menjelaskan tentang isi
halaman ini.'
]);
}
```
Kemudian lakukan refresh pada halaman tersebut.

![Screenshot (343)](https://user-images.githubusercontent.com/73010098/176990159-af336a52-f244-4b7f-996a-0f3e06029194.png)

## Membuat Layout web dengan CSS
Buat file CSS baru dengan nama style.css yang terletak pada public
``` php
/* RESET CSS*/
* {
    margin: 0;
    padding: 0;
}

body {
    line-height: 1;
    font-size: 100%;
    font-family: 'Open Sans', sans-serif;
    color: #5a5a5a;
}

#container {
    width: 980px;
    margin: 0 auto;
    box-shadow: 0 0 1em #ccc;
}

/* HEADER*/
header {
    padding: 20px;
}

header h1 {
    margin: 20px 10px;
    color: #a0a0a0;
}

/* NAV */
nav {
    display: block;
    background-color: #bebebe;
}

nav a {
    padding: 15px 30px;
    display: inline-block;
    color: #fff;
    font-size: 14px;
    text-decoration: none;
    font-weight: bold;
}

nav a.active,
nav a:hover {
    background-color: #0ca878;
}

/* HERO PANEL */
#hero {
    background-color: #e4e4e5;
    padding: 50px 20px;
    margin-bottom: 20px;
}

#hero h1 {
    margin-bottom: 20px;
    font-size: 35px;
}

#hero p {
    margin-bottom: 20px;
    font-size: 18px;
    line-height: 25px;
}

/* MAIN CONTENT */
#wrapper {
    margin: 0;
}

#main {
    padding-top: 25px;
    float: left;
    width: 640px;
    padding: 20px;
}

.row {
    padding-top: 50px;
}

.divider {
    border: 0;
    border-top: 1px solid #eee;
    margin: 40px 0;
}

/* ENTRY */
.entry {
    margin: 15px 0px;
}

.entry h2 {
    margin-bottom: 20px;
}

.entry p {
    line-height: 25px;
}

.entry img {
    float: left;
    border-radius: 5px;
    margin-right: 15px;
}

.entry .right-img {
    float: right;
    margin-left: 15px;
}

/* SIDEBAR AREA */
#sidebar {
    float: right;
    width: 260px;
    padding: 20px;
}

/* WIDGET */
.widget-box {
    border: 1px solid #eee;
    margin-bottom: 20px;
}

.widget-box .title {
    padding: 10px 16px;
    background-color: #0ca878;
    color: #fff;
}

.widget-box ul {
    list-style-type: none;
}

.widget-box li {
    border-bottom: 1px solid #eee;
}

.widget-box li a {
    padding: 10px 16px;
    color: #333;
    display: block;
    text-decoration: none;
}

.widget-box list-style:hover a {
    background-color: #eee;
}

.widget-box p {
    padding: 15px;
    line-height: 25px;
}

/* FOOTER */
footer {
    clear: both;
    background-color: #1d1d1d;
    padding: 20px;
    color: #eee;
}

/* BOX */
.box {
    display: block;
    float: left;
    width: 33.333333%;
    box-sizing: border-box;
    -moz-box-sizing: border-box;
    -webkit-box-sizing: border-box;
    padding: 0px 10px;
    text-align: center;
}

.box h3 {
    margin: 15px 0px;
}

.box p {
    line-height: 20px;
    font-size: 14px;
    margin-bottom: 15px;
}

.box img {
    border: 0;
    vertical-align: middle;

}

.image-circle {
    border-radius: 50%;
}

.row {
    margin: 0 -10px;
    box-sizing: border-box;
    -moz-box-sizing: border-box;
    -webkit-box-sizing: border-box;
}

.row:after, .row:before,
.entry:after, .entry:before {
 content:'';
 display:table;
}
.row:after,
.entry:after {
 clear:both;
}
```
## Membuat file Header
File app/view/template/header.php
``` php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title><?= $title; ?></title>
    <link rel="stylesheet" href="<?= base_url('/style.css');?>">
</head>
<body>
    <div id="container">
    <header>
        <h1>Layout Sederhana</h1>
    </header>
    <nav>
        <a href="<?= base_url('/');?>" class="active">Home</a>
        <a href="<?= base_url('/artikel');?>">Artikel</a>
        <a href="<?= base_url('/about');?>">About</a>
        <a href="<?= base_url('/contact');?>">Contact</a>      
    </nav>
    <section id="wrapper">
        <section id="main">
   ```
   File app/view/template/footer.php
   ``` php
               </section>
            <aside id="sidebar">
                <div class="widget-box">
                    <h3 class="title">Widget Header</h3>
                    <ul>
                        <li><a href="#">Widget Link</a></li>
                        <li><a href="#">Widget Link</a></li>
                    </ul>
                </div>
                <div class="widget-box">
                    <h3 class="title">Widget Title</h3>
                    <p>Vestibulum lorem elit, iaculis in nisl volutpat, malesuada 
                        tincidunt arcu. Proin in leo fringilla, vestibulum mi porta, faucibus felis. 
                        Integer pharetra est nunc, nec pretium nunc pretium ac.</p>
                </div>
            </aside>
        </section>
        <footer>
            <p>&copy; 2022 - Universitas Pelita Bangsa</p>
        </footer>
    </div>
</body>
</html>
```
Kemudian ubah file app/view/about.php seperti berikut.
``` php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title><?= $title; ?></title>
</head>
<body>
    <?= $this->include('template/header'); ?>

    <h1><?= $title; ?></h1>
    <hr>
    <p><?= $content; ?></p>

    <?= $this->include('template/footer'); ?>
</body>
</html> 
```
Selanjutnya refresh tampilan pada alamat http://localhost:8080/about

![Screenshot (348)](https://user-images.githubusercontent.com/73010098/176990274-02bac019-dbf2-45fc-b446-108197b921a2.png)

# Pertanyaan dan Tugas
Lengkapi kode program untuk menu lainnya yang ada pada Controller Page, sehingga
semua link pada navigasi header dapat menampilkan tampilan dengan layout yang
sama.

## Membuat Controllers Page
Tambahkan Controllers untuk kontak dan artikel pada file ``` page.php ``` 
***app/Controllers/Page.php*** <br>

``` php
<?php

namespace App\Controllers;

class Page extends BaseController
{
    public function about()
    {
        return view('about', [
            'title' => 'Halaman About', 
            'content' => 'Ini adalah paragraf yang menjelaskan tentang halaman about.'
        ]);
    }

    public function artikel()
    {
        return view('artikel', [
            'title' => 'Halaman Artikel', 
            'content' => 'Ini adalah paragraf yang menjelaskan tentang halaman artikel.'
        ]);
    }

    public function contact()
    {
        return view('contact', [
            'title' => 'Halaman Contact', 
            'content' => 'Ini adalah paragraf yang menjelaskan tentang halaman contact.'
        ]);
    }

    public function faqs()
    {
        echo "Ini adalah halaman Faqs";
    }

    public function tos()
    {
        echo "Ini adalah Terms of Services";
    }
}
```
## Membuat Contollers Home
Mengubah sintaks pada file Home.php yang terletak pada app/Controllers/Home.php
``` php
<?php

namespace App\Controllers;

class Home extends BaseController
{
    public function home()
    {
        return view('home', [
            'title' => 'Halaman Home', 
            'content' => 'Ini adalah paragraf yang menjelaskan tentang halaman home.'
        ]);
    }
}
```

## Membuat File Artikel
Buatlah file PHP baru dengan nama artikel.php yang disimpan pada folder app/Views
``` php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title><?= $title; ?></title>
</head>
<body>
    <?= $this->include('template/header'); ?>

    <h1><?= $title; ?></h1>
    <hr>
    <p><?= $content; ?></p>

    <?= $this->include('template/footer'); ?>
</body>
</html>    
```
## Membuat File Contact
Buat file baru ``` contact.php ``` yang di simpan pada folder ``` app/Views ```
``` php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title><?= $title; ?></title>
</head>
<body>
    <?= $this->include('template/header'); ?>

    <h1><?= $title; ?></h1>
    <hr>
    <p><?= $content; ?></p>

    <?= $this->include('template/footer'); ?>
</body>
</html>    
```
## Membuat File Home
Buat file baru ``` home.php ``` yang di simpan pada folder ``` app/Views ```
``` php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title><?= $title; ?></title>
</head>
<body>
    <?= $this->include('template/header'); ?>

    <h1><?= $title; ?></h1>
    <hr>
    <p><?= $content; ?></p>

    <?= $this->include('template/footer'); ?>
</body>
</html>    
```
## Membuat isi Footer
Menambahkan footer pada file ``` footer.php ``` yang diterletak pada folder ``` app/Views/template ```
``` php
                <div class="row">
                    <div class="box">
                        <img src="https://dummyimage.com/120/e9967a/fff.png" alt="" class="image-circle">
                        <h3>Heading</h3>
                        <p>Donec sed odio dui. Etiam porta sem malesuada magna mollis 
                            euismod.</p>
                        <a href="#" class="btn btn-default">View Detail</a>
                    </div>
                    <div class="box">
                        <img src="https://dummyimage.com/120/98b3cd/fff.png" alt="" class="image-circle">
                        <h3>Heading</h3>
                        <p>Donec sed odio dui. Etiam porta sem malesuada magna mollis 
                            euismod.</p>
                        <a href="#" class="btn btn-default">View Detail</a>
                    </div>
                    <div class="box">
                        <img src="https://dummyimage.com/120/dddd88/fff.png"  alt="" class="image-circle">
                        <h3>Heading</h3>
                        <p>Donec sed odio dui. Etiam porta sem malesuada magna mollis 
                            euismod.</p>
                        <a href="#" class="btn btn-default">View Detail</a>
                    </div> 
                </div>
                <hr class="divider">
                    <article class="entry">
                        <h2>First Featurette Heading</h2>
                        <img src="https://dummyimage.com/150/94d194/fff.png" alt="">
                        <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vestibulum lorem 
                            elit, iaculis in nisl volutpat, malesuada tincidunt arcu. Proin in leo fringilla, 
                            vestibulum mi porta, faucibus felis. Integer pharetra est nunc, nec pretium nunc 
                            pretium ac.</p>
                    </article>
                <hr class="divider">
                    <article class="entry">
                        <h2>First Featurette Heading</h2>
                        <img src="https://dummyimage.com/150/94d194/fff.png" alt="" class="right-img">
                        <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vestibulum lorem 
                            elit, iaculis in nisl volutpat, malesuada tincidunt arcu. Proin in leo fringilla, 
                            vestibulum mi porta, faucibus felis. Integer pharetra est nunc, nec pretium nunc 
                            pretium ac.</p>
                    </article> 
 ```

## Mengubah Nav pada header
mengubah header pada file ``` header.php ``` yang diterletak pada folder ``` app/Views/template ```
``` php
    <nav>
        <a href="<?= base_url('/home');?>" class="active">Home</a>
        <a href="<?= base_url('/artikel');?>">Artikel</a>
        <a href="<?= base_url('/about');?>">About</a>
        <a href="<?= base_url('/contact');?>">Contact</a>      
    </nav>   
  ```
## Menambahkan Router
Menambahkan router pada file ``` router.php ``` yang terletak pada folder ``` app/Config ```
``` php
$routes->get('/', 'Home::home');
$routes->get('/home', 'Home::home');
$routes->get('/artikel', 'Page::artikel');
```
# OUTPUT
HALAMAN HOME
![Screenshot (351)](https://user-images.githubusercontent.com/73010098/176990587-fdc168bc-36db-4168-8c7a-1ac9875bcbd1.png)

HALAMAN ABOUT
![Screenshot (350)](https://user-images.githubusercontent.com/73010098/176990591-eb903014-3ef3-4ab5-85a4-718188a85be4.png)

HALAMAN CONTACT
![Screenshot (352)](https://user-images.githubusercontent.com/73010098/176990602-512d2f0e-0901-41b9-ab1b-974f3d614e9a.png)

