
# Praktikum 6 -- PHP Dasar

**Nama** : Rafli Dhiya Fadhaly\
**NIM** : 312410251\
**Kelas** : TI 24 A2\
**Dosen** : Agung Nugroho, S.Kom., M.Kom.\
**Mata Kuliah** : Pemrograman Web 1

------------------------------------------------------------------------

## Tujuan Praktikum

1.  Memahami konsep dasar *Server Side Scripting*
2.  Memahami dasar pemrograman PHP
3.  Memahami variabel dan tipe data pada PHP
4.  Memahami struktur kondisi dan perulangan
5.  Membuat program PHP sederhana

------------------------------------------------------------------------

## Langkah Praktikum

------------------------------------------------------------------------

### **Step 1 -- Hello World**

``` php
<!DOCTYPE html>
<html lang="en">
<head><meta charset="UTF-8"><title>PHP Dasar</title></head>
<body>
  <h1>Belajar PHP Dasar</h1>
  <?php echo "Hello World"; ?>
</body>
</html>
```

**Tujuan:** Memastikan Apache + PHP berjalan.\
`echo "Hello World";` hanya akan tampil jika PHP berhasil dieksekusi
oleh server.

<img width="1920" height="1080" alt="Screenshot (154)" src="https://github.com/user-attachments/assets/761ec147-0835-48f2-a353-4559fe25e41a" />
------------------------------------------------------------------------

### **Step 2 -- Form Input Nama**

``` php
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

**Tujuan:** Membuat form input nama dan menampilkan hasil input.

<img width="1920" height="1080" alt="Screenshot (155)" src="https://github.com/user-attachments/assets/15df392e-4155-4631-9f0c-4313155c4fa3" />
------------------------------------------------------------------------

### **Step 3 -- Menampilkan Nama Setelah Submit**

``` php
<?php
if(isset($_POST['kirim'])) {
  $nama = htmlspecialchars($_POST['nama']);
  echo "<hr>Selamat Datang, <b>$nama</b>";
}
?>
```

**Tujuan:** Menampilkan nama hanya setelah tombol submit ditekan
(`isset`).

<img width="1920" height="1080" alt="Screenshot (156)" src="https://github.com/user-attachments/assets/314dcb65-1e5f-4323-b4ce-a38c77ceb951" />
------------------------------------------------------------------------

### **Step 4 -- Input Tanggal Lahir**

``` php
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

**Tujuan:** Menambahkan input tanggal dengan format `YYYY-MM-DD`.

<img width="1920" height="1080" alt="Screenshot (157)" src="https://github.com/user-attachments/assets/76b8db57-b0cf-402c-b58c-42ea1668d858" />
------------------------------------------------------------------------

### **Step 5 -- Input Pekerjaan (Dropdown)**

``` php
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

**Tujuan:** Mengambil data dari dropdown menggunakan `$_POST`.

<img width="1920" height="1080" alt="Screenshot (158)" src="https://github.com/user-attachments/assets/06cba89a-03f0-4e92-bdf6-b244693a7d7b" />
------------------------------------------------------------------------

### **Step 6 -- Menghitung Umur**

``` php
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

**Tujuan:** Menghitung usia dengan `DateTime()` dan `diff()`.

<img width="1920" height="1080" alt="Screenshot (161)" src="https://github.com/user-attachments/assets/401c407f-908e-4a3d-aa7b-66c6e485133d" />
------------------------------------------------------------------------

### **Step 7 -- Menentukan Gaji Berdasarkan Pekerjaan**

``` php
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
    case "Guru": $gaji = "Rp 3.000.000"; break;
    case "Programmer": $gaji = "Rp 7.000.000"; break;
    case "Desainer": $gaji = "Rp 5.000.000"; break;
    case "Dokter": $gaji = "Rp 10.000.000"; break;
    default: $gaji = "Tidak diketahui";
  }

  echo "<hr>Gaji untuk <b>" . htmlspecialchars($pekerjaan) . "</b> adalah: <b>$gaji</b>";
}
?>
```

**Tujuan:** Menentukan gaji menggunakan `switch case`.

<img width="1920" height="1080" alt="Screenshot (161)" src="https://github.com/user-attachments/assets/3fd988c3-5ce8-4a24-9172-e0e704b32440" />
------------------------------------------------------------------------

## Kesimpulan

-   PHP mampu memproses data form menggunakan `$_POST`
-   `DateTime()` memudahkan perhitungan waktu seperti umur
-   `switch case` efektif untuk menentukan output berdasarkan kondisi
-   `htmlspecialchars()` penting untuk keamanan input pengguna
