# lab8web
<h2>Langkah 1: Membuat Koneksi ke Database</h2>
<img src="" width="300" height="auto">
<p>File ini digunakan untuk membuat koneksi ke database MySQL. Berikut langkah-langkahnya:</p>
<ol>
    <li>Buat file <code>koneksi.php</code> di direktori proyek Anda.</li>
    <li>Tambahkan kode berikut ke dalam file <code>koneksi.php</code>:</li>
</ol>

```php
<?php
$host = "localhost";
$user = "root";
$pass = "";
$db = "latihan1";

$conn = mysqli_connect($host, $user, $pass, $db);

if ($conn == false) {
    echo "Koneksi ke server gagal.";
    die();
} else {
    echo "Koneksi berhasil";
}
?>

<h2>Langkah 2: Membuat Halaman Utama untuk Menampilkan Data</h2>
<img src="" width="300" height="auto">
<p>File ini digunakan untuk menampilkan data dari database. Berikut langkah-langkahnya:</p>
<ol>
    <li>Buat file <code>index.php</code> di direktori proyek Anda.</li>
    <li>Tambahkan kode berikut ke dalam file <code>index.php</code>:</li>
</ol>

```php
<?php
include("koneksi.php");
// Query untuk menampilkan data
$sql = 'SELECT * FROM data_barang';
$result = mysqli_query($conn, $sql);
?>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <link href="style.css" rel="stylesheet" type="text/css" />
    <title>Data Barang</title>
</head>
<body>
<div class="container">
    <h1>Data Barang</h1>
    <div class="main">
        <table>
            <tr>
                <th>Gambar</th>
                <th>Nama Barang</th>
                <th>Kategori</th>
                <th>Harga Jual</th>
                <th>Harga Beli</th>
                <th>Stok</th>
                <th>Aksi</th>
            </tr>
            <?php if($result): ?>
            <?php while($row = mysqli_fetch_array($result)): ?>
            <tr>
                <td><img src="gambar/<?= $row['gambar'];?>" alt="<?= $row['nama'];?>"></td>
                <td><?= $row['nama'];?></td>
                <td><?= $row['kategori'];?></td>
                <td><?= $row['harga_beli'];?></td>
                <td><?= $row['harga_jual'];?></td>
                <td><?= $row['stok'];?></td>
                <td><?= $row['id_barang'];?></td>
            </tr>
            <?php endwhile; else: ?>
            <tr>
                <td colspan="7">Belum ada data</td>
            </tr>
            <?php endif; ?>
        </table>
    </div>
</div>
</body>
</html>
