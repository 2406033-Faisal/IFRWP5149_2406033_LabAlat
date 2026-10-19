<!-- Tabel Kebutuhan -->

ID                          Kebutuhan
LAB-R01 s.d. LAB-R06        Kebutuhan Pertemuan 3 tetap berlaku dan tidak berubah arti (lihat Jobsheet Pertemuan 3).
LAB-R07                     Mahasiswa dan Dosen, sebagai Peminjam, dapat melihat ketersediaan peralatan dan mengajukan peminjaman.
LAB-R08                     Petugas laboratorium mengelola data peralatan dalam tiga bentuk khusus: tambah, ubah, dan hapus data peralatan.
LAB-R09                     Petugas laboratorium dapat mencatat pengembalian peralatan untuk peminjaman yang berstatus Dipinjam.
LAB-R10                     Sistem memeriksa dan mencatat kondisi peralatan sebagai bagian dari pencatatan pengembalian.
LAB-R11                     Model menunjukkan collaboration yang merealisasikan Ajukan Peminjaman dan Catat Pengembalian Peralatan.

## 1. Deskripsi
Sistem Peminjaman Peralatan Laboratorium digunakan untuk melihat ketersediaan peralatan, mengajukan peminjaman, mengelola data peralatan, memproses keputusan peminjaman, mencatat pengembalian, memeriksa kondisi peralatan, dan melihat laporan peminjaman.

Dokumen ini disusun berdasarkan skenario latihan Pertemuan 4 yang melanjutkan model Pertemuan 3.

## 2. Daftar Kebutuhan Fungsional

| ID | Nama Kebutuhan | Deskripsi Kebutuhan | Aktor Terkait |
|---|---|---|---|
| LAB-R01 | Lihat Ketersediaan Peralatan | Sistem menyediakan informasi ketersediaan peralatan laboratorium yang dapat dilihat oleh peminjam. | Peminjam |
| LAB-R02 | Kelola Data Peralatan | Sistem mendukung pengelolaan data peralatan laboratorium oleh petugas. | Petugas Laboratorium |
| LAB-R03 | Ajukan Peminjaman | Sistem memungkinkan peminjam mengajukan peminjaman peralatan dan memeriksa ketersediaan peralatan dalam proses pengajuan. | Peminjam |
| LAB-R04 | Cetak Bukti Pengajuan | Sistem menyediakan fasilitas pencetakan bukti pengajuan peminjaman apabila mahasiswa memilih untuk mencetaknya. | Mahasiswa |
| LAB-R05 | Proses Keputusan Peminjaman | Sistem mendukung petugas laboratorium dalam memproses keputusan atas pengajuan peminjaman. | Petugas Laboratorium |
| LAB-R06 | Lihat Laporan Peminjaman | Sistem menyediakan laporan peminjaman yang dapat dilihat oleh kepala laboratorium. | Kepala Laboratorium |
| LAB-R07 | Dukungan Peminjam Mahasiswa dan Dosen | Sistem mendukung mahasiswa dan dosen sebagai peminjam yang dapat melihat ketersediaan serta mengajukan peminjaman peralatan. | Mahasiswa, Dosen |
| LAB-R08 | Kelola Rincian Data Peralatan | Sistem mendukung penambahan peralatan baru, perubahan data peralatan, dan penghapusan data peralatan yang tidak lagi digunakan. | Petugas Laboratorium |
| LAB-R09 | Catat Pengembalian Peralatan | Sistem mendukung pencatatan pengembalian peralatan yang telah dipinjam, termasuk tanggal kembali dan pembaruan status peminjaman. | Petugas Laboratorium |
| LAB-R10 | Periksa Kondisi Peralatan | Sistem mendukung pemeriksaan dan pencatatan kondisi peralatan saat pengembalian. | Petugas Laboratorium |

## 3. Aturan dan Batasan
1. Mahasiswa dan dosen merupakan jenis peminjam yang dapat melihat ketersediaan dan mengajukan peminjaman.
2. Mahasiswa memiliki fungsi khusus untuk mencetak bukti pengajuan.
3. Petugas laboratorium bertanggung jawab mengelola data peralatan dan memproses keputusan peminjaman.
4. Petugas mencatat pengembalian setelah peralatan dipinjam dan dikembalikan.
5. Pemeriksaan kondisi peralatan dilakukan sebagai bagian dari pencatatan pengembalian.
6. Kepala laboratorium memiliki fungsi melihat laporan peminjaman.
7. Fungsi-fungsi dari Pertemuan 3 tetap dipertahankan pada model Pertemuan 4.

## 4. Keterkaitan Kebutuhan dengan Use Case

| ID Kebutuhan | Use Case Terkait |
|---|---|
| LAB-R01 | LAB-UC01 — Lihat Ketersediaan Peralatan |
| LAB-R02 | LAB-UC02 — Kelola Data Peralatan |
| LAB-R03 | LAB-UC03 — Ajukan Peminjaman; LAB-UC04 — Periksa Ketersediaan |
| LAB-R04 | LAB-UC05 — Cetak Bukti Pengajuan |
| LAB-R05 | LAB-UC06 — Proses Keputusan Peminjaman |
| LAB-R06 | LAB-UC07 — Lihat Laporan Peminjaman |
| LAB-R07 | LAB-UC01 — Lihat Ketersediaan Peralatan; LAB-UC03 — Ajukan Peminjaman |
| LAB-R08 | LAB-UC08 — Tambah Data Peralatan; LAB-UC09 — Ubah Data Peralatan; LAB-UC10 — Hapus Data Peralatan |
| LAB-R09 | LAB-UC11 — Catat Pengembalian Peralatan |
| LAB-R10 | LAB-UC12 — Periksa Kondisi Peralatan |


