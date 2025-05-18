# Gratika
1. int i = 1, j = 10;
do {
  if (i++ > --j){
    continue;
  }
} while(i < 5);
System.out.println("i = " + i + " and j = " + j);

•	Iterasi 1: i=1, j=9 → i++ (i=2), 1 > 9 → false
•	Iterasi 2: i=2, j=8 → i++ (i=3), 2 > 8 → false
•	Iterasi 3: i=3, j=7 → i++ (i=4), 3 > 7 → false
•	Iterasi 4: i=4, j=6 → i++ (i=5), 4 > 6 → false
•	Iterasi 5: loop berhenti (karena i=5 tidak < 5)
Jawaban: B. i = 5 and j = 6

2. void start() {
  d = new Demo();
  this.takeDemo(d);
}
void takeDemo(Demo demo) {
  demo = null;
  demo = new Demo();
}

Objek d masih direferensikan oleh variabel instance. Tidak eligible untuk GC.
Jawaban: E. When the instance running this code is made eligible for garbage collection.

3. new Alpha1().get("veggie").soundOff();
Alpha1.get() mengembalikan Animal, soundOff() valid.
Jawaban: D. new Alpha1().get(“veggie”).soundOff();

4. class A {
  A() { }
}
class B extends A { }
B secara otomatis punya constructor tanpa argumen.
Constructor B memanggil super().
Jawaban: B dan D

5. int x = 3;
int y = 1;
if (x = y) {
  System.out.println("x = " + x);
}
if(x = y) salah → = bukan ==. Compilation error.
Jawaban: C. Compilation fails.

6. Method: Fungsi atau prosedur dalam class.
Attribute: Variabel dalam class yang menyimpan data.

7. Encapsulation: Menyembunyikan data dan hanya bisa diakses lewat method tertentu.
Inheritance: Pewarisan atribut dan method dari parent class ke subclass.

SQL

1. INNER JOIN: Tampilkan data yang match di kedua tabel.
SELECT * FROM A INNER JOIN B ON A.id = B.a_id;

LEFT JOIN: Tampilkan semua data dari tabel kiri.
SELECT * FROM A LEFT JOIN B ON A.id = B.a_id;

RIGHT JOIN: Tampilkan semua dari tabel kanan.
SELECT * FROM A RIGHT JOIN B ON A.id = B.a_id;

FULL OUTER JOIN: Semua data dari dua tabel.
MySQL tidak langsung mendukung; bisa pakai UNION.

2. Query tampilkan semua data dari tabel:
SELECT * FROM nama_tabel;

PHP
1. Fungsi dan cara memanggilnya:
function salam($nama) {
  return "Halo, $nama";
}
echo salam("Budi");

2. Koneksi PHP dan MySQL + tampilkan data:
$conn = new mysqli("localhost", "root", "", "dbku");
$result = $conn->query("SELECT * FROM pelanggan");
while($row = $result->fetch_assoc()) {
  echo $row['nama'] . "<br>";
}
3. Framework PHP dan kelebihannya:
Laravel: Mudah, modern, banyak dokumentasi.
CodeIgniter: Ringan, cocok untuk pemula.
Symfony: Modular, fleksibel.
Yii: Cepat, cocok untuk aplikasi kompleks.

4. Framework/frontend selain PHP:
HTML/CSS/JavaScript: Untuk tampilan.
React / Vue / Angular: Komponen interaktif.
Bootstrap / Tailwind: Styling cepat dan konsisten.
Untuk pengalaman pengguna yang lebih baik (UI/UX).

Studi Kasus
1. LRS (Logical Record Structure) (asumsi nota):
Pelanggan: id, nama, umur, kelamin
Dokter: id, nama
Obat: id, nama, harga
Transaksi: id, id_pelanggan, id_dokter, tanggal
Detail_Obat: id_transaksi, id_obat, jumlah

2. Tampilan Program (Desain sederhana):
Form input pelanggan
Form transaksi (pilih dokter, tanggal)
Tambah obat (checkbox atau dropdown)
Tabel riwayat transaksi

3. Query berdasarkan LRS:

a. Pelanggan perempuan umur 19–30 di Agustus 2015:
SELECT * FROM pelanggan p
JOIN transaksi t ON p.id = t.id_pelanggan
WHERE p.kelamin = 'Perempuan'
AND p.umur BETWEEN 19 AND 30
AND MONTH(t.tanggal) = 8
AND YEAR(t.tanggal) = 2015;

b. Semua dokter dengan atau tanpa transaksi:
SELECT * FROM dokter d
LEFT JOIN transaksi t ON d.id = t.id_dokter
WHERE YEAR(t.tanggal) = 2015 OR t.id IS NULL;

c. Jumlah dan total uang per-obat (Ags–Des 2015):
SELECT o.nama, SUM(d.jumlah) AS total_jumlah, SUM(d.jumlah * o.harga) AS total_uang
FROM detail_obat d
JOIN obat o ON d.id_obat = o.id
JOIN transaksi t ON d.id_transaksi = t.id
WHERE MONTH(t.tanggal) BETWEEN 8 AND 12
AND YEAR(t.tanggal) = 2015
GROUP BY o.id;

d. 10 obat paling banyak digunakan 2015:
SELECT o.nama, SUM(d.jumlah) AS total
FROM detail_obat d
JOIN obat o ON d.id_obat = o.id
JOIN transaksi t ON d.id_transaksi = t.id
WHERE YEAR(t.tanggal) = 2015
GROUP BY o.id
ORDER BY total DESC
LIMIT 10;

e. Klasifikasi umur pelanggan:
SELECT nama,
CASE
  WHEN umur < 18 THEN 'Anak-anak'
  WHEN umur BETWEEN 18 AND 30 THEN 'Dewasa'
  ELSE 'Orang tua'
END AS kategori_umur
FROM pelanggan;



