## LAB-UC11: Catat Pengembalian Peralatan

| Elemen | Isi |
|---|---|
| ID dan nama | LAB-UC11: Catat Pengembalian Peralatan |
| Sumber kebutuhan | LAB-R09 dan LAB-R10 |
| Tujuan | Pengembalian tercatat dan status peminjaman serta kondisi peralatan terbarui |
| Aktor utama | Petugas Laboratorium |
| Aktor pendukung | Tidak ada |
| Pemicu | Petugas memilih fungsi pencatatan pengembalian dan menentukan peminjaman yang akan dikembalikan |
| Prasyarat | Petugas telah terautentikasi; peminjaman terpilih berstatus Dipinjam |
| Pascakondisi berhasil | Pengembalian tercatat dengan tanggal kembali dan kondisi peralatan; status peminjaman menjadi Selesai |
| Pascakondisi gagal | Tidak ada pengembalian baru yang tercatat; status peminjaman tidak berubah |
| Include | LAB-UC12: Periksa Kondisi Peralatan |
| Generalization | Tidak ada (LAB-UC11 bukan bagian hierarki generalization) |
| Collaboration | LAB-CO02: Catat Pengembalian Peralatan |
| Aturan bisnis / asumsi | Pengembalian hanya untuk peminjaman berstatus Dipinjam (Menunggu Keputusan atau Ditolak tidak dapat). Kondisi dicatat salah satu dari: Baik, Rusak Ringan, Rusak Berat. Sistem hanya mencatat; perpindahan fisik alat di luar sistem. Keterlambatan dan denda belum dimodelkan (pertanyaan terbuka Q1 dan Q2). |

### Alur utama

| Langkah | Tindakan petugas | Respons sistem |
|---|---|---|
| 1 | Memilih peminjaman yang akan dikembalikan | Menampilkan data peminjaman terpilih dan statusnya |
| 2 | Mengonfirmasi alat yang kembali dan jumlahnya | Menampung konfirmasi petugas |
| 3 | Tidak ada | Memeriksa status peminjaman harus Dipinjam |
| 4 | Tidak ada | Menjalankan LAB-UC12: memeriksa dan mencatat kondisi peralatan |
| 5 | Menyimpan pencatatan pengembalian | Menyimpan tanggal kembali dan kondisi; mengubah status peminjaman menjadi Selesai |
| 6 | Melihat konfirmasi | Menampilkan ringkasan pengembalian |

### Alur alternatif atau pengecualian

- **A1: Status bukan Dipinjam (pada langkah 3).** Sistem menolak pencatatan dan menampilkan status peminjaman saat ini. Pascakondisi gagal berlaku; tidak ada data yang disimpan.
- **A2: Kondisi Rusak Ringan atau Rusak Berat (pada langkah 4).** Sistem tetap menyimpan pencatatan, menandai kondisi tersebut pada data peralatan, dan pengembalian tetap tercatat. Kerusakan tidak otomatis menimbulkan denda pada model ini.
- **A3: Jumlah alat yang kembali tidak sesuai (pada langkah 2).** Sistem meminta petugas memeriksa kembali isian sebelum penyimpanan; pencatatan tidak disimpan sampai jumlah sesuai atau dikoreksi.

## Konsistensi dengan diagram

- LAB-UC11 terhubung ke Petugas Laboratorium (asosiasi) dan menyertakan LAB-UC12 (include arah LAB-UC11 ke LAB-UC12), sesuai hubungan no. 8 dan no. 15.
- LAB-CO02 merealisasikan LAB-UC11 (hubungan no. 17). Collaboration disebut di deskripsi use case, bukan dibuatkan deskripsi sendiri.
