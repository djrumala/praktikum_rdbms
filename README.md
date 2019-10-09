# praktikum_rdbms

1. Menampilkan daftar matakuliah dan nilai yang di ambil oleh seorang mahasiswa

```
SELECT  b.nrp, b.nama, a.idk, a.kdmatkul, c.nmmatkul, a.nilai FROM tb_kelas a 
INNER JOIN tb_mhs b ON b.nrp=a.nrp 
INNER JOIN tb_matkul c ON c.kdmatkul=a.kdmatkul
WHERE b.nama="Yohanes Redi"
```

2.
