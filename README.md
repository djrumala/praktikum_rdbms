# praktikum_rdbms

1. Menampilkan daftar mahasiswa dari suatu angkatan dan dosen walinya
```
SELECT a.nrp as "NRP", a.nama as "Nama", a.tgl as "Tanggal Lahir", b.dosen as "Dosen Wali" FROM tb_mhs a
INNER JOIN tb_dosen b ON b.nip = a.nip
WHERE a.thmasuk=2014
```

2. Menampilkan matakuliah dan nilai
```
SELECT  b.nrp, b.nama, a.kdmatkul, c.nmmatkul, c.sks, a.nilai FROM tb_kelas a 
INNER JOIN tb_mhs b ON b.nrp=a.nrp 
INNER JOIN tb_matkul c ON c.kdmatkul=a.kdmatkul
WHERE b.nama="Yohanes Redi";
```

3.	 Menghitung jumlah SKS dari daftar matakuliah yang diambil oleh seoarang mahasiswa
```
SELECT sum(c.sks)as "Total SKS" FROM tb_kelas a 
INNER JOIN tb_mhs b ON b.nrp=a.nrp 
INNER JOIN tb_matkul c ON c.kdmatkul=a.kdmatkul
WHERE b.nama="Yohanes Redi";
```
 
4.	Daftar mahasiswa pada suatu mata kuliah di semester tertentu pada tahun tertentu
```
SELECT b.nrp, b.nama, a.kdmatkul, c.nmmatkul, c.sks, a.nilai FROM tb_kelas a 
INNER JOIN tb_mhs b ON b.nrp=a.nrp 
INNER JOIN tb_matkul c ON c.kdmatkul=a.kdmatkul
WHERE c.nmmatkul="Sejarah Musik" AND a.tahun=2015 AND a.periode=1;
```
 
5.	Menampilkan nilai angka dari mahasiswa
```
SELECT  b.nrp, b.nama, a.kdmatkul, c.nmmatkul, c.sks,
a.nilai, 
    (
    CASE 
        WHEN a.nilai = 'A' THEN 4*c.sks
        WHEN a.nilai = 'AB' THEN 3.5*c.sks
        WHEN a.nilai = 'B' THEN 3*c.sks
        WHEN a.nilai = 'BC' THEN 2.5*c.sks
        WHEN a.nilai = 'C' THEN 2*c.sks
        WHEN a.nilai = 'D' THEN 1*c.sks
        ELSE 0
    END) AS "S*N"


FROM tb_kelas a 
INNER JOIN tb_mhs b ON b.nrp=a.nrp 
INNER JOIN tb_matkul c ON c.kdmatkul=a.kdmatkul
WHERE b.nama="Yohanes Redi";
```
 


