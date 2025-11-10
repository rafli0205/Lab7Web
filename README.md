# Praktikum 6: PHP Dasar

- **Nama**  : Rafli Dhiya Fadhaly
- **NIM**   : 312410251
- **Kelas** : TI 24 A2
- **Dosen** : Agung Nugroho, S.Kom., M.Kom.
- **Mata Kuliah** : Pemrograman Web 1

Tujuan
1. Mahasiswa mampu memahami konsep dasar Server Side Scripting.
2. Mahasiswa mampu memahami dasar Pemrograman PHP.
3. Mahasiswa mampu memahami Variable dan Tipe Data pada PHP
4. Mahasiswa mampu memahami konsep Struktur Kondisi dan Perulangan.
5. Mahasaswa mampu membuat program PHP sederhana.

## Langkah Pratikum
### Step 1 - Hello Word
```php
<!DOCTYPE html>
<html lang="en">
<head><meta charset="UTF-8"><title>PHP Dasar</title></head>
<body>
  <h1>Belajar PHP Dasar</h1>
  <?php echo "Hello World"; ?>
</body>
</html>
```
Tujuan: Pastikan Apache + PHP berjalan.
echo "Hello World"; menampilkan teks yang hanya bisa diproses kalau server PHP aktif.

<img width="1920" height="1080" alt="Screenshot (154)" src="https://github.com/user-attachments/assets/761ec147-0835-48f2-a353-4559fe25e41a" />

### Step 2 - Form Nama
```php
<form method="post">
  <label>Nama: </label>
  <input type="text" name="nama" required>
  <input type="submit" value="Kirim">
</form>

<?php
if(isset($_POST['nama'])) {
  echo 'Selamat Datang ' . htmlspecialchars($_POST['nama']);
}
?>
```
Tujuan: Membuat form input nama dan menerima data dari user.
method="post" dipakai agar data dikirim tanpa muncul di URL.
$_POST['nama'] menangkap input yang dikirim dari form.
htmlspecialchars() dipakai agar input aman dari karakter berbahaya (keamanan).

<img width="1920" height="1080" alt="Screenshot (155)" src="https://github.com/user-attachments/assets/15df392e-4155-4631-9f0c-4313155c4fa3" />

### Step 3 - Tampillkan Nama
```php
<?php
if(isset($_POST['kirim'])) {
    $nama = htmlspecialchars($_POST['nama']);
    echo "<hr>Selamat Datang, <b>$nama</b>";
}
?>
```
Tujuan: Menampilkan kembali nama yang sudah dikirim oleh user.
isset($_POST['kirim']) mengecek apakah form sudah disubmit.
Jika true, maka nama akan dipanggil dan ditampilkan ke halaman browser.

<img width="1920" height="1080" alt="Screenshot (156)" src="https://github.com/user-attachments/assets/314dcb65-1e5f-4323-b4ce-a38c77ceb951" />

### Step 4 - Input tanggal lahir
```php
<form method="post">
  <label>Tanggal Lahir :</label><br>
  <input type="date" name="tanggal_lahir" required><br><br>
  <button type="submit" name="kirim">Kirim</button>
</form>

<?php
if(isset($_POST['kirim'])) {
    echo "<hr>Tanggal Lahir yang dikirim: " . $_POST['tanggal_lahir'];
}
?>
```
Tujuan: Menambahkan input tanggal lahir ke dalam form.
type="date" memberikan tampilan kalender agar user mudah memilih tanggal.
Value dikirim ke PHP dalam format YYYY-MM-DD dan ditampilkan kembali untuk memastikan input berhasil dikirim.

<img width="1920" height="1080" alt="Screenshot (157)" src="https://github.com/user-attachments/assets/76b8db57-b0cf-402c-b58c-42ea1668d858" />

### Step 5 - Input Pekerjaan
```php
<form method="post">
  <label>Pekerjaan :</label><br>
  <select name="pekerjaan" required>
    <option value="Guru">Guru</option>
    <option value="Programmer">Programmer</option>
    <option value="Desainer">Desainer</option>
    <option value="Dokter">Dokter</option>
  </select><br><br>
  <button type="submit" name="kirim">Kirim</button>
</form>

<?php
if(isset($_POST['kirim'])) {
    echo "<hr>Pekerjaan yang dipilih: " . htmlspecialchars($_POST['pekerjaan']);
}
?>
```
Tujuan: Menambahkan pilihan pekerjaan menggunakan dropdown (select).
<option value="..."> menentukan nilai yang dikirim ke server.
Saat submit, PHP menampilkan pekerjaan yang dipilih oleh user menggunakan $_POST['pekerjaan'].
  
<img width="1920" height="1080" alt="Screenshot (158)" src="https://github.com/user-attachments/assets/06cba89a-03f0-4e92-bdf6-b244693a7d7b" />

### Step 6 - Hitung Umur
```php
<form method="post">
  <label>Tanggal Lahir :</label><br>
  <input type="date" name="tanggal_lahir" required><br><br>
  <button type="submit" name="kirim">Kirim</button>
</form>

<?php
if(isset($_POST['kirim'])) {
    $tgl = $_POST['tanggal_lahir'];
    $lahir = new DateTime($tgl);
    $sekarang = new DateTime();
    $umur = $sekarang->diff($lahir)->y;

    echo "<hr>Umur berdasarkan tanggal $tgl adalah: <b>$umur tahun</b>";
}
?>
```
Tujuan: Menghitung umur berdasarkan tanggal lahir.
DateTime($tgl_lahir) mengubah input tanggal menjadi format objek waktu.
diff() digunakan untuk menghitung selisih waktu antara tanggal lahir dan tanggal sekarang.
->y mengambil hasil selisih dalam satuan tahun (umur).

<img width="1920" height="1080" alt="Screenshot (161)" src="https://github.com/user-attachments/assets/401c407f-908e-4a3d-aa7b-66c6e485133d" />

### Step 6 - Hitung Gaji
```php
<form method="post">
  <label>Pekerjaan :</label><br>
  <select name="pekerjaan" required>
    <option value="Guru">Guru</option>
    <option value="Programmer">Programmer</option>
    <option value="Desainer">Desainer</option>
    <option value="Dokter">Dokter</option>
  </select><br><br>
  <button type="submit" name="kirim">Kirim</button>
</form>

<?php
if(isset($_POST['kirim'])) {
    $pekerjaan = $_POST['pekerjaan'];
    switch($pekerjaan){
        case "Guru":
            $gaji = "Rp 3.000.000";
            break;
        case "Programmer":
            $gaji = "Rp 7.000.000";
            break;
        case "Desainer":
            $gaji = "Rp 5.000.000";
            break;
        case "Dokter":
            $gaji = "Rp 10.000.000";
            break;
        default:
            $gaji = "Tidak diketahui";
    }
    echo "<hr>Gaji untuk <b>" . htmlspecialchars($pekerjaan) . "</b> adalah: <b>$gaji</b>";
}
?>
```
Tujuan: Menentukan gaji berdasarkan pekerjaan yang dipilih menggunakan switch.
switch($pekerjaan) membandingkan nilai pekerjaan dan memberikan output gaji yang sesuai.
Jika pekerjaan tidak sesuai dengan data yang ada di case, maka masuk ke default.

<img width="1920" height="1080" alt="Screenshot (161)" src="https://github.com/user-attachments/assets/3fd988c3-5ce8-4a24-9172-e0e704b32440" />
