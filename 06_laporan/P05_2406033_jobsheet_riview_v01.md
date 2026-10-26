# DOKUMENTASI EVALUASI & REVIEW MODEL USE CASE (PERTEMUAN 05)
**Topik:** Skenario Use Case (Dari Diagram ke Langkah Kegiatan)  
**Dokumen:** `P05_2406033_Review_Evaluasi_Skenario_v01.md`  

---

## A. Kasus LAB — Penelaahan 12 Tabel Skenario Laboratorium (Pertemuan 5)

### A.1 Uji Konsistensi Skenario terhadap Diagram P04
| Situasi | Diagram | Deskripsi / Skenario | Konsisten? |
|:---:|---|---|:---:|
| **Alur Normal & Include** | `LAB-UC03` include `LAB-UC04`. | Step 2 Skenario Normal `LAB-UC03` merujuk ke tabel `LAB-UC04` tanpa menyalin langkahnya. | **Ya** |
| **Alur Alternative & Extend** | `LAB-UC05` extend `LAB-UC03`. | Step 11 Skenario Alternative `LAB-UC03` memuat *condition* `[mahasiswa memilih cetak]` & EP `Bukti pengajuan tersedia`. | **Ya** |
| **Penomoran Berlanjut** | Skenario Normal (1–6), Alternative (7–12). | Penomoran Skenario Alternative melanjutkan Skenario Normal tanpa mengulang dari nomor 1. | **Ya** |
| **Generalization & Collaboration** | Aktor `Peminjam`, Collaboration `LAB-CO01`. | Skenario ditulis 1x atas nama `Peminjam`; Collaboration dicantumkan pada bagian keterangan di bawah tabel. | **Ya** |

### A.2 Matriks Keterlacakan (Traceability) 12 Skenario LAB
| ID Use Case | Nama Use Case | Representasi Diagram P04 | Kelengkapan Skenario Teks | Keterangan Pemetaan |
|:---:|:---:|:---:|:---:|---|
| **LAB-UC01** | Lihat Ketersediaan Peralatan | Ya | Complete | Ditulis atas nama Aktor umum `Peminjam`. |
| **LAB-UC02** | Kelola Data Peralatan | Ya | Complete | Skenario umum pengelolaan data peralatan. |
| **LAB-UC03** | Ajukan Peminjaman | Ya | Complete | Memuat rujukan `include` `UC04` dan `extend` `UC05`. |
| **LAB-UC04** | Periksa Ketersediaan | Ya | Complete | Berjalan di dalam `UC03` tanpa interaksi langsung aktor luar. |
| **LAB-UC05** | Cetak Bukti Pengajuan | Ya | Complete | Cabang bersyarat khusus Mahasiswa. |
| **LAB-UC06** | Proses Keputusan Peminjaman | Ya | Complete | Memproses status *Menunggu Keputusan* $\rightarrow$ *Disetujui/Ditolak*. |
| **LAB-UC07** | Lihat Laporan Peminjaman | Ya | Complete | Standalone UC Kepala Lab tanpa relasi include/extend. |
| **LAB-UC08** | Tambah Data Peralatan | Ya | Complete | Skenario khusus dari `UC02` (perilaku pembeda: data baru tersimpan). |
| **LAB-UC09** | Ubah Data Peralatan | Ya | Complete | Skenario khusus dari `UC02` (perilaku pembeda: data berubah). |
| **LAB-UC10** | Hapus Data Peralatan | Ya | Complete | Skenario khusus dari `UC02` (syarat: tidak ada pengajuan aktif). |
| **LAB-UC11** | Catat Pengembalian Peralatan | Ya | Complete | Memuat rujukan `include` `UC12` dan catatan `LAB-CO02`. |
| **LAB-UC12** | Periksa Kondisi Peralatan | Ya | Complete | Berjalan di dalam `UC11` mencatat kondisi fisik alat. |

---

## B. Kasus SIA — 7 Tabel Skenario Tugas Academic (Pertemuan 5)

### B.1 Uji Konsistensi Skenario Tugas SIA
| Situasi | Diagram | Deskripsi / Skenario | Konsisten? |
|:---:|---|---|:---:|
| **SIA-UC07 Lihat Kalender Akademik** | Terhubung ke `Civitas Akademika`. | Skenario ditulis 1x atas nama `Civitas Akademika` (berlaku untuk Mahasiswa dan Dosen). | **Ya** |
| **SIA-UC08 Input Nilai Mata Kuliah** | Terhubung ke `Dosen`, Collaboration `SIA-CO01`. | Prasyarat Dosen Pengampu; Skenario Alternative menolak nilai di luar rentang sah (0–100). | **Ya** |
| **SIA-UC09 Lihat KHS** | Terhubung ke `Mahasiswa`, Collaboration `SIA-CO02`. | Skenario Normal hanya menampilkan nilai yang sudah dipublikasikan oleh Fakultas. | **Ya** |
| **SIA-UC10 s.d. SIA-UC13 Kelola Data Mahasiswa** | `Generalization` ke `SIA-UC10`. | `SIA-UC10` memuat langkah bersama; `UC11-13` hanya memuat perilaku pembeda (tambah/ubah/hapus). | **Ya** |

### B.2 Matriks Keterlacakan (Traceability) Skenario SIA
| ID Use Case | Nama Use Case | Aktor Utama | Dokumen Skenario (`.md`) | Keterangan Aturan |
|:---:|:---:|:---:|:---:|---|
| **SIA-UC07** | Lihat Kalender Akademik | Civitas Akademika | Complete | Mewariskan fungsi ke Mahasiswa dan Dosen. |
| **SIA-UC08** | Input Nilai Mata Kuliah | Dosen | Complete | Memuat nota `SIA-CO01` dan aturan Dosen Pengampu. |
| **SIA-UC09** | Lihat KHS | Mahasiswa | Complete | Memuat nota `SIA-CO02` dan syarat nilai terpublikasi. |
| **SIA-UC10** | Kelola Data Mahasiswa | Admin Akademik | Complete | Skenario umum pengelolaan data mahasiswa. |
| **SIA-UC11** | Tambah Data Mahasiswa | Admin Akademik | Complete | Skenario khusus (perilaku pembeda: data mahasiswa baru). |
| **SIA-UC12** | Ubah Data Mahasiswa | Admin Akademik | Complete | Skenario khusus (perilaku pembeda: data mahasiswa berubah). |
| **SIA-UC13** | Hapus Data Mahasiswa | Admin Akademik | Complete | Skenario khusus (syarat: tidak ada data akademik aktif). |

---

## C. Checklist Evaluasi Model Pertemuan 5

| Indikator Evaluasi | Kasus LAB | Kasus SIA | Status Evaluasi |
|---|:---:|:---:|:---:|
| Seluruh field tabel terisi lengkap (Nama, Aktor, Tujuan, Deskripsi, Skenario Normal, Alternative, Akhir) | ✓ | ✓ | Terpenuhi |
| Satu langkah berisi tepat satu aksi, dan penomoran berlanjut ke Skenario Alternative | ✓ | ✓ | Terpenuhi |
| Kolom Kegiatan hanya berisi aksi aktor; kolom Respon Sistem hanya berisi tanggapan sistem | ✓ | ✓ | Terpenuhi |
| Data, nilai field, dan status disebutkan secara eksplisit pada langkah skenario | ✓ | ✓ | Terpenuhi |
| Relasi `include` ditulis sebagai langkah rujukan pada Skenario Normal tanpa menyalin alurnya | ✓ | ✓ | Terpenuhi |
| Relasi `extend` ditulis sebagai cabang Skenario Alternative lengkap dengan condition & extension point | ✓ | ✓ | Terpenuhi |
| Collaboration dicatat pada keterangan di bawah tabel, tanpa dibuatkan langkah tersendiri | ✓ | ✓ | Terpenuhi |
| Berkas diagram Pertemuan 4 (`P04`) dipertahankan utuh dan tidak diubah/ditimpa | ✓ | ✓ | Terpenuhi |

---

## D. Log Review Rekan / Asisten Praktikum Pertemuan 5

| No | Kasus | Temuan Review *(Arah Panah / Kondisi / Extension Point / Pascakondisi)* | Tindakan Perbaikan | Versi Terakhir |
|:---:|:---:|---|---|:---:|
| **1** | SIA | *Penomoran langkah pada Skenario Alternative SIA-UC08 diulang kembali dari nomor 1.* | Memperbaiki penomoran Skenario Alternative agar berlanjut dari Skenario Normal (langkah 7–10). | `v01` |
| **2** | LAB | *Keterangan Collaboration LAB-CO01 ditulis sebagai langkah kegiatan tersendiri di dalam tabel.* | Memindahkan informasi collaboration ke bagian keterangan khusus di bawah tabel skenario. | `v01` |