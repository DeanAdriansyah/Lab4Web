# PEMOGRAMAAN WEB
Dean Adriansyah Asy'ari (312110286)

Teknik Informatika - UNIVERSITAS PELITA BANGSA

---
# <p align="center">Praktikum 4: PHP Modular</p>

### Tujuan
* Mampu memahami konsep dasar Modularisasi Program.
* Mampu memahami konsep dasar Fungsi pada PHP.
* Mampu membuat program Modular sederhana menggunakan PHP.
* Mampu mengimplementasikan penggunaan fungsi pada PHP

### Instruksi Praktikum
* Persiapkan text editor misalnya VSCode.
* Buat folder baru dengan nama lab4_php_database pada docroot webserver (htdocs)
* Ikuti langkah-langkah praktikum yang akan dijelaskan berikutnya.


---
# <p align="center">Langkah-langkah Praktikum</p>
### Buat file baru dengan nama _header.php_
```
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>Contoh Modularisasi</title>
    <link href="style.css" rel="stylesheet" type="text/stylesheet" media="screen" />
    <style>
        body {
            margin: 0;
            background-color:mintcream;
        }

        nav {
            display: flex;
            justify-content:space-around;
            align-items: center;
            background-color: darkcyan;
            padding: 10px;
            box-shadow:2px 2px 5px 1px;
        }

        .nav-links a {
            color: #fff;
            text-decoration: none;
            margin: 0 10px;
        }


        @media screen and (max-width: 768px) {
            .nav-links {
                display: none;
            }
        }

    </style>
</head>

<body>
    <div>
        <header>
            <h1 align="center">Modularisasi Menggunakan Require</h1>
        </header>
        <nav>
            <div class="nav-links">
                <a href="home.php">Home</a>
                <a href="about.php">About</a>
                <a href="kontak.php">Contact</a>
            </div>
        </nav>
```

### Buat file baru dengan nama _footer.php_
```
<footer align="center" style="background-color:darkcyan; color:white; width:100%; padding:10px; position:absolute; bottom:0px; ">
    <p>&copy; 2023, Informatika, Universitas Pelita Bangsa</p>
</footer>
</div>
</body>

</html>
```

### Buat file baru dengan nama _home.php_
```
<?php require('header.php'); ?>
<div class="content" style="margin-left:20px;">
    <h2>Ini Halaman Home</h2>
    <p>Ini adalah bagian content dari halaman.</p>
</div>
<?php require('footer.php'); ?>
```

### Buat file baru dengan nama _about.php_
```
<?php require('header.php'); ?>
<div class="content" style="margin-left:20px;">
    <h2>Ini Halaman About</h2>
    <p>Ini adalah bagian content dari halaman.</p>
</div>
<?php require('footer.php'); ?>
```

## Membuat Routing
Routing digunakan untuk mempermudah akses halaman web agar SEO Friendly.

Langkah awal adalah menyiapkan file utama (index.php) yang berisi routing untuk mengakses banyak
halaman.

Contohnya:

• Halaman Home ( http://localhost/lab4/index.php?mod=home )

• Halaman About ( http://localhost/lab4/index.php?mod=about )

### Buat file baru dengan nama _index.php_
```
<?php

$mod = isset($_REQUEST['mod']) ? $_REQUEST['mod'] : "home";

switch ($mod) {
    case "home":
        require("home.php");
        break;
    case "about":
        require("about.php");
        break;
    default:
        require("home.php");
}
?>
```

## Aktivasi mod_rewrite (.htaccess)
Mod_rewrite digunakan untuk mengubah URL dari query string menjadi SEO Friendly.

Langkah awal yang harus disiapkan adalah aktivasi mod_rewrite pada webserver Apache2 pada
configurasi httpd.conf.


