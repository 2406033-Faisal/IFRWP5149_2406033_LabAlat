# P04 SIA - Use Case Description (v01)

## SIA-UC08: Input Nilai Mata Kuliah

| Elemen | Isi |
|---|---|
| ID dan nama | SIA-UC08: Input Nilai Mata Kuliah |
| Sumber kebutuhan | SIA-R08 dan SIA-R12 |
| Tujuan | Nilai mata kuliah yang diampu dosen tersimpan di sistem dan siap dipublikasikan |
| Aktor utama | Dosen |
| Aktor pendukung | Tidak ada |
| Pemicu | Dosen memilih fungsi input nilai dan menentukan mata kuliah yang akan dinilai |
| Prasyarat | Dosen telah terautentikasi; dosen adalah pengampu mata kuliah tersebut; masa perkuliahan mata kuliah telah berakhir |
| Pascakondisi berhasil | Nilai setiap mahasiswa peserta tersimpan untuk mata kuliah tersebut dengan status belum dipublikasikan; nilai belum tampil pada KHS |
| Pascakondisi gagal | Tidak ada nilai baru yang tersimpan; nilai yang sudah ada tidak berubah |
| Include / Extend | Tidak ada |
| Generalization | Tidak ada (bukan bagian hierarki) |
| Collaboration | SIA-CO01: Input Nilai Mata Kuliah |
| Aturan bisnis / asumsi | Hanya dosen pengampu yang dapat menginput nilai. Nilai yang diinput belum terpublikasi; KHS hanya menampilkan nilai terpublikasi. Rentang nilai yang sah mengikuti ketentuan akademik (pertanyaan terbuka Q1). Mekanisme publikasi dan koreksi nilai belum dimodelkan (Q2, Q3). |

### Alur utama

| Langkah | Tindakan dosen | Respons sistem |
|---|---|---|
| 1 | Memilih mata kuliah yang diampu | Menerima pilihan mata kuliah |
| 2 | Tidak ada | Memeriksa bahwa dosen adalah pengampu dan masa perkuliahan telah berakhir; menampilkan daftar mahasiswa peserta |
| 3 | Mengisi nilai untuk setiap mahasiswa peserta | Menampung isian nilai |
| 4 | Tidak ada | Memeriksa setiap nilai berada dalam rentang yang sah |
| 5 | Menyimpan nilai | Menyimpan nilai dengan status belum dipublikasikan |
| 6 | Melihat konfirmasi | Menampilkan ringkasan nilai yang tersimpan |

### Alur alternatif atau pengecualian

- **A1: Dosen bukan pengampu (pada langkah 2).** Sistem menolak dan menampilkan pesan bahwa dosen tidak berhak menginput nilai mata kuliah tersebut. Pascakondisi gagal berlaku.
- **A2: Nilai di luar rentang yang sah (pada langkah 4).** Sistem menolak nilai tersebut, menandai isian yang salah, dan meminta dosen mengoreksi. Nilai tidak disimpan sampai semua isian sah; bila dosen membatalkan, pascakondisi gagal berlaku.
- **A3: Masa perkuliahan belum berakhir (pada langkah 2).** Sistem menolak input nilai dan menampilkan alasan. Pascakondisi gagal berlaku.

## SIA-UC09: Lihat KHS (deskripsi ringkas)

| Elemen | Isi |
|---|---|
| ID dan nama | SIA-UC09: Lihat KHS |
| Sumber kebutuhan | SIA-R09 dan SIA-R12 |
| Tujuan | Mahasiswa mengetahui hasil studinya pada semester tertentu |
| Aktor utama | Mahasiswa |
| Pemicu | Mahasiswa memilih fungsi lihat KHS dan menentukan semester |
| Prasyarat | Mahasiswa terautentikasi; nilai semester yang dipilih sudah dipublikasikan |
| Alur ringkas | Mahasiswa memilih semester; sistem memeriksa status publikasi; sistem menampilkan KHS yang **hanya memuat nilai yang sudah dipublikasikan**. |
| Alur alternatif | A1: Nilai semester belum dipublikasikan: sistem menampilkan pesan bahwa KHS belum tersedia dan tidak menampilkan nilai apa pun. |
| Pascakondisi berhasil | KHS semester terpilih tampil dengan nilai terpublikasi saja; tidak ada data yang berubah |
| Pascakondisi gagal | KHS tidak ditampilkan; tidak ada data yang berubah |
| Generalization | Tidak ada |
| Collaboration | SIA-CO02: Lihat KHS |

## Konsistensi dengan diagram

SIA-UC08 terhubung ke Dosen dan SIA-UC09 ke Mahasiswa (asosiasi khusus langsung, hubungan no. 5 dan 6). SIA-CO01 dan SIA-CO02 merealisasikan masing-masing use case tersebut (hubungan no. 17 dan 18) dan tidak terhubung ke aktor.
