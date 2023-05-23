# Praktikum3_SQL

```
Nama    : Nurul Akbar
NIM     : 312210413
Kelas   : TI.22.A.4
```

# SQL Constraint

- SQL Constraint digunakan untuk menentukan aturan untuk data dalam tabel.
- Constraint digunakan untuk membatasi jenis data yang bisa masuk ke tabel. Ini memastikan keakuratan dan keandalan data dalam tabel.
- Constraint dapat berupa level kolom atau level tabel.
- Constraint level kolom berlaku untuk kolom, dan batasan level tabel berlaku untuk seluruh tabel.

## Tugas Praktikum

1. Lakukan penambahan data pada tabel mahasiswa dengan mengisi kd_ds yang belum ada pada data dosen.
2. Hapus satu record data pada tabel dosen yang telah dirujuk pada tabel mahasiswa.
3. Ubah mode menjadi ON UPDATE CASCADE ON DELETE RESTRICT
4. Lakukan perubahan data pada tabel dosen (kd_ds)
5. Lakukan penghapusan data pada tabel dosen
6. Ubah mode menjadi ON UPDATE CASCADE ON DELETE SET NULL
7. Lakukan penghapusan data pada tabel dosen

### Evaluasi dan Pertanyaan

- tulis semua perintah-perintah SQL percobaan di atas beserta outputnya `laporan praktikum3 basis data.pdf`
- Apa bedanya penggunaan RESTRICT dan penggunaan CASCADE

  1. RESTRICT: Jika pengaturan RESTRICT diterapkan pada kunci asing, itu berarti ada pembatasan (restriction) yang diterapkan pada operasi penghapusan atau pembaruan yang mempengaruhi baris yang dirujuk oleh kunci asing tersebut. Jika ada upaya untuk menghapus atau memperbarui baris yang memiliki referensi kunci asing, maka operasi tersebut akan gagal dan tidak ada perubahan yang akan terjadi. Dengan kata lain, RESTRICT membatasi tindakan yang melanggar integritas referensial.

  2. CASCADE: Di sisi lain, pengaturan CASCADE menghasilkan perilaku yang berbeda. Ketika kunci asing dikonfigurasi dengan CASCADE, itu berarti operasi penghapusan atau pembaruan yang dilakukan pada baris yang dirujuk oleh kunci asing akan dijejalkan (cascaded) ke baris yang terkait di tabel lain. Misalnya, jika Anda menghapus baris dari tabel utama yang memiliki referensi kunci asing di tabel terkait dengan CASCADE, maka semua baris yang berkaitan dalam tabel terkait juga akan dihapus. Ini memungkinkan perubahan yang dijejalkan (cascaded) ke seluruh database terkait dengan kunci asing tersebut.

- Berikan kesimpulan anda!
  - kesimpulannya adalah RESTRICT membatasi (restrict) operasi tersebut, sehingga operasi gagal jika ada referensi kunci asing yang terlibat. CASCADE memicu (cascade) operasi tersebut, menjadikan perubahan pada baris yang terkait di tabel lain.
- Buat laporan praktikum yang berisi, langkah-langkah praktikum beserta screenshot yang sudah dilakukan dalam bentuk dokumen(laporan praktikum3 basis data.pdf)

### SQL

- Mengubah data
  ```sql
  UPDATE mahasiswa
  SET kd_ds = 'DS001' WHERE nim = 112233445;
  ```
  ```sql
  UPDATE dosen
  SET kd_ds = 'DS001' WHERE nama = 'Ujang Kurama';
  ```
- Menampilkan CREATE TABLE
  ```sql
  SHOW CREATE TABLE  mahasiswa;
  ```
- Mode ON UPDATE CASCADE ON DELETE CASCADE
  ```sql
  ALTER TABLE mahasiswa
  DROP FOREIGN KEY fk_mahasiswa_dosen,
  ADD CONSTRAINT fk_dosenwali FOREIGN KEY (kd_ds) REFERENCES dosen(kd_ds) ON UPDATE CASCADE ON DELETE CASCADE;
  ```
- Menghapus data
  ```sql
  DELETE FROM dosen WHERE kd_ds = 'DS001';
  ```
- Mode ON UPDATE CASCADE ON DELETE NOT NULL
  ```sql
  ALTER TABLE <table>
  DROP FOREIGN KEY fk_mahasiswa_dosen,
  ADD CONSTRAINT fk_dosenwali FOREIGN KEY (kd_ds) REFERENCES <dosen(kd_ds)> ON UPDATE CASCADE ON DELETE NOT NULL;
  ```

[def]: gambar/11.png
[def2]: gambar/11.png
