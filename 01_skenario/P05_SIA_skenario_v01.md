## TABEL 5.14 INDEKS TUGAS SKENARIO SIA
1. **SIA-UC07:** Lihat Kalender Akademik (Aktor: Civitas Akademika)
2. **SIA-UC08:** Input Nilai Mata Kuliah (Aktor: Dosen)
3. **SIA-UC09:** Lihat KHS (Aktor: Mahasiswa)
4. **SIA-UC10:** Kelola Data Mahasiswa (Aktor: Admin Akademik)
5. **SIA-UC11:** Tambah Data Mahasiswa (Aktor: Admin Akademik)
6. **SIA-UC12:** Ubah Data Mahasiswa (Aktor: Admin Akademik)
7. **SIA-UC13:** Hapus Data Mahasiswa (Aktor: Admin Akademik)

---

### TABEL SKENARIO SIA-UC07
| **Field** | **Deskripsi / Isi** |
| :--- | :--- |
| **Nama use case** | SIA-UC07 Lihat Kalender Akademik |
| **Aktor** | Civitas Akademika (berlaku untuk Mahasiswa dan Dosen) |
| **Tujuan** | Civitas akademika dapat melihat jadwal kegiatan akademik kampus |
| **Deskripsi** | Civitas akademika mengakses fungsi kalender akademik dan sistem menampilkan daftar kegiatan akademik beserta tanggal pelaksanaannya. |

| Kegiatan | Respon sistem |
| :--- | :--- |
| **Skenario Normal** | |
| 1. Civitas Akademika membuka fungsi Lihat Kalender Akademik | 2. Sistem menampilkan daftar kegiatan dan jadwal kalender akademik |
| **Skenario Alternative** | |
| 3. Tidak ada data kalender akademik yang dipublikasikan (cabang dari langkah 2) | 4. Sistem menampilkan pesan bahwa kalender akademik belum tersedia |
| **Skenario Akhir** | Use case selesai jika daftar kalender akademik berhasil ditampilkan; jika data belum tersedia, use case selesai dengan pesan pemberitahuan. |

---

### TABEL SKENARIO SIA-UC08
| **Field** | **Deskripsi / Isi** |
| :--- | :--- |
| **Nama use case** | SIA-UC08 Input Nilai Mata Kuliah |
| **Aktor** | Dosen |
| **Tujuan** | Dosen pengampu dapat memasukkan dan menyimpan nilai mata kuliah mahasiswa |
| **Deskripsi** | Dosen pengampu memilih kelas mata kuliah, memasukkan daftar nilai mahasiswa, dan menyimpan data nilai tersebut ke dalam sistem. Prasyarat: Dosen merupakan pengampu mata kuliah tersebut. |

| Kegiatan | Respon sistem |
| :--- | :--- |
| **Skenario Normal** | |
| 1. Dosen memilih kelas mata kuliah yang diampu | 2. Sistem memeriksa hak akses dosen pengampu dan menampilkan daftar mahasiswa serta formulir input nilai |
| 3. Dosen memasukkan nilai tugas, UTS, dan UAS mahasiswa | 4. Sistem memeriksa keabsahan dan rentang nilai yang dimasukkan (0 - 100) |
| 5. Dosen menyimpan data nilai | 6. Sistem menyimpan data nilai dan mengubah status menjadi Terimpan |
| **Skenario Alternative** | |
| 7. Dosen bukan pengampu mata kuliah tersebut (cabang dari langkah 2) | 8. Sistem menolak akses dan menampilkan pesan bahwa dosen tidak berhak menginput nilai |
| 9. Nilai di luar rentang sah / format tidak valid (cabang dari langkah 4) | 10. Sistem menolak penyimpanan dan meminta dosen memperbaiki isian nilai |
| **Skenario Akhir** | Use case selesai jika data nilai berhasil disimpan; jika dosen bukan pengampu atau nilai tidak valid, data nilai tidak tersimpan. |

*Keterangan tabel:* Use case ini direalisasikan oleh collaboration **SIA-CO01 Input Nilai Mata Kuliah**. Collaboration tidak mempunyai langkah kegiatan pada tabel ini.

---

### TABEL SKENARIO SIA-UC09
| **Field** | **Deskripsi / Isi** |
| :--- | :--- |
| **Nama use case** | SIA-UC09 Lihat KHS |
| **Aktor** | Mahasiswa |
| **Tujuan** | Mahasiswa dapat melihat Kartu Hasil Studi (KHS) semester yang telah dipublikasikan |
| **Deskripsi** | Mahasiswa memilih semester dan melihat nilai mata kuliah serta Indeks Prestasi (IP) semester. Hanya nilai yang sudah dipublikasikan yang ditampilkan. |

| Kegiatan | Respon sistem |
| :--- | :--- |
| **Skenario Normal** | |
| 1. Mahasiswa memilih semester yang ingin dilihat KHS-nya | 2. Sistem memeriksa status publikasi nilai semester tersebut |
| 3. Mahasiswa meminta tampilkan KHS | 4. Sistem menampilkan daftar nilai mata kuliah yang sudah dipublikasikan beserta IP Semester |
| **Skenario Alternative** | |
| 5. Nilai semester belum dipublikasikan (cabang dari langkah 2) | 6. Sistem menampilkan pesan bahwa KHS semester terpilih belum dipublikasikan |
| **Skenario Akhir** | Use case selesai jika KHS dengan nilai terpublikasi ditampilkan; jika belum dipublikasikan, KHS tidak ditampilkan. |

*Keterangan tabel:* Use case ini direalisasikan oleh collaboration **SIA-CO02 Lihat KHS**. Collaboration tidak mempunyai langkah kegiatan pada tabel ini.

---

### TABEL SKENARIO SIA-UC10
| **Field** | **Deskripsi / Isi** |
| :--- | :--- |
| **Nama use case** | SIA-UC10 Kelola Data Mahasiswa |
| **Aktor** | Admin Akademik |
| **Tujuan** | Data mahasiswa terkelola melalui satu fungsi pengelolaan bersama |
| **Deskripsi** | Admin Akademik membuka fungsi kelola data mahasiswa, memilih bentuk pengelolaan, dan menyimpan perubahan. Bentuk tambah, ubah, dan hapus dijabarkan pada tabel khususnya masing-masing. |

| Kegiatan | Respon sistem |
| :--- | :--- |
| **Skenario Normal** | |
| 1. Admin Akademik membuka fungsi Kelola Data Mahasiswa | 2. Sistem menampilkan daftar data mahasiswa |
| 3. Admin Akademik memilih bentuk pengelolaan (tambah, ubah, atau hapus) | 4. Sistem menampilkan formulir/tampilan sesuai pilihan pengelolaan |
| 5. Admin Akademik mengisi atau mengonfirmasi data mahasiswa | 6. Sistem memeriksa kelengkapan dan keabsahan data |
| 7. Admin Akademik menyimpan perubahan data | 8. Sistem menyimpan perubahan dan menampilkan pesan konfirmasi |
| **Skenario Alternative** | |
| 9. Data tidak lengkap atau tidak sah (cabang dari langkah 6) | 10. Sistem menolak penyimpanan dan menampilkan pesan kesalahan data |
| **Skenario Akhir** | Use case selesai jika perubahan data mahasiswa tersimpan; jika data tidak sah/lengkap, perubahan tidak tersimpan. |

---

### TABEL SKENARIO SIA-UC11
| **Field** | **Deskripsi / Isi** |
| :--- | :--- |
| **Nama use case** | SIA-UC11 Tambah Data Mahasiswa |
| **Aktor** | Admin Akademik |
| **Tujuan** | Data mahasiswa baru tersimpan sebagai bentuk khusus dari pengelolaan data mahasiswa |
| **Deskripsi** | Admin Akademik mengisi data mahasiswa baru dan menyimpan data tersebut; langkah bersama mengikuti Tabel skenario SIA-UC10. |

| Kegiatan | Respon sistem |
| :--- | :--- |
| **Skenario Normal** | |
| 1. Admin Akademik membuka fungsi Tambah Data Mahasiswa | 2. Sistem menampilkan formulir data mahasiswa baru |
| 3. Admin Akademik mengisi data mahasiswa baru (NIM, Nama, Prodi, dll) | 4. Sistem memeriksa kelengkapan dan keunikan NIM |
| 5. Admin Akademik menyimpan data | 6. Sistem menyimpan data mahasiswa baru dan menampilkan konfirmasi |
| **Skenario Alternative** | |
| 7. Data tidak lengkap atau NIM sudah terdaftar (cabang dari langkah 4) | 8. Sistem menolak penyimpanan dan menampilkan pesan kesalahan |
| **Skenario Akhir** | Use case selesai jika data mahasiswa baru tersimpan; jika data tidak valid/NIM duplikat, data tidak tersimpan. |

*Keterangan tabel:* Use case khusus dari **SIA-UC10 Kelola Data Mahasiswa**. Perilaku pembeda: data mahasiswa baru tersimpan. Langkah bersama mengikuti Tabel skenario SIA-UC10.

---

### TABEL SKENARIO SIA-UC12
| **Field** | **Deskripsi / Isi** |
| :--- | :--- |
| **Nama use case** | SIA-UC12 Ubah Data Mahasiswa |
| **Aktor** | Admin Akademik |
| **Tujuan** | Data mahasiswa berubah sebagai bentuk khusus dari pengelolaan data mahasiswa |
| **Deskripsi** | Admin Akademik memilih data mahasiswa, mengubah datanya, dan menyimpan perubahan; langkah bersama mengikuti Tabel skenario SIA-UC10. |

| Kegiatan | Respon sistem |
| :--- | :--- |
| **Skenario Normal** | |
| 1. Admin Akademik memilih data mahasiswa yang akan diubah | 2. Sistem menampilkan data mahasiswa saat ini |
| 3. Admin Akademik mengubah data mahasiswa | 4. Sistem memeriksa validitas perubahan data |
| 5. Admin Akademik menyimpan perubahan | 6. Sistem menyimpan data yang diubah dan menampilkan konfirmasi |
| **Skenario Alternative** | |
| 7. Data mahasiswa tidak ditemukan (cabang dari langkah 2) | 8. Sistem menampilkan pesan bahwa data mahasiswa tidak ditemukan |
| **Skenario Akhir** | Use case selesai jika perubahan data mahasiswa tersimpan; jika data tidak ditemukan, perubahan tidak tersimpan. |

*Keterangan tabel:* Use case khusus dari **SIA-UC10 Kelola Data Mahasiswa**. Perilaku pembeda: data mahasiswa berubah. Langkah bersama mengikuti Tabel skenario SIA-UC10.

---

### TABEL SKENARIO SIA-UC13
| **Field** | **Deskripsi / Isi** |
| :--- | :--- |
| **Nama use case** | SIA-UC13 Hapus Data Mahasiswa |
| **Aktor** | Admin Akademik |
| **Tujuan** | Data mahasiswa terhapus sebagai bentuk khusus dari pengelolaan data mahasiswa |
| **Deskripsi** | Admin Akademik memilih data mahasiswa, mengonfirmasi penghapusan, dan sistem menghapus data tersebut; langkah bersama mengikuti Tabel skenario SIA-UC10. |

| Kegiatan | Respon sistem |
| :--- | :--- |
| **Skenario Normal** | |
| 1. Admin Akademik memilih data mahasiswa yang akan dihapus | 2. Sistem memeriksa bahwa mahasiswa tidak memiliki data akademik aktif |
| 3. Admin Akademik mengonfirmasi penghapusan data | 4. Sistem menghapus data mahasiswa dan menampilkan konfirmasi |
| **Skenario Alternative** | |
| 5. Mahasiswa memiliki data akademik aktif (cabang dari langkah 2) | 6. Sistem menolak penghapusan dan menampilkan pesan bahwa mahasiswa masih memiliki data akademik aktif |
| **Skenario Akhir** | Use case selesai jika data mahasiswa berhasil dihapus; jika memiliki data akademik aktif, data tidak terhapus. |

*Keterangan tabel:* Use case khusus dari **SIA-UC10 Kelola Data Mahasiswa**. Perilaku pembeda: data mahasiswa terhapus, dengan syarat tidak ada data akademik aktif. Langkah bersama mengikuti Tabel skenario SIA-UC10.
