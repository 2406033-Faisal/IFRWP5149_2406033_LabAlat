# DOKUMENTASI EVALUASI & REVIEW MODEL USE CASE (PERTEMUAN 04)
**Topik:** Use Case Diagram Lanjutan (Generalization, Collaboration, Include, Extend)  
**Dokumen:** `P04_2406033_Review_Evaluasi_Model_v01.md`  

---

## A. Kasus LAB — Peminjaman Peralatan Laboratorium (Pertemuan 4)

### A.1 Uji Konsistensi
| Situasi | Diagram | Deskripsi | Konsisten? |
|:---:|---|---|:---:|
| **Peminjaman biasa (Mahasiswa/Dosen)** | `LAB-UC03` dihubungkan ke aktor umum `Peminjam`; mengeksekusi `LAB-UC04` (`<<include>>`). | `LAB-UC03` alur utama langkah 1–6; tersimpan dengan status *Menunggu keputusan*. | **Ya** |
| **Peminjaman dengan cetak bukti (Khusus Mahasiswa)** | `LAB-UC05` memperluas `LAB-UC03` (`<<extend>>`) pada *extension point* **Bukti pengajuan tersedia**, kondisi `[mahasiswa memilih cetak]`. | `LAB-UC03` mengeksekusi `LAB-UC05` untuk cetak bukti; status pengajuan tidak berubah. | **Ya** |
| **Pengelolaan data peralatan (Petugas)** | `LAB-UC08`, `LAB-UC09`, dan `LAB-UC10` mewarisi (`Generalization`) `LAB-UC02`. | Perilaku pembeda (tambah, ubah, hapus) dieksekusi melalui skenario khusus `LAB-UC02`. | **Ya** |
| **Pencatatan pengembalian & kondisi alat** | `LAB-UC11` mengeksekusi `LAB-UC12` (`<<include>>`) dan direalisasikan oleh `LAB-CO02`. | `LAB-UC11` mencatat pengembalian dan kondisi alat (*Baik/Rusak*); status berubah menjadi *Selesai*. | **Ya** |

### A.2 Matriks Keterlacakan (Traceability)
| ID Kebutuhan | Use Case Terkait | Representasi Diagram | Dokumen Deskripsi | Keterangan |
|:---:|:---:|:---:|:---:|---|
| **LAB-R07** | `LAB-UC01`, `LAB-UC03` | Ya (`Generalization` Aktor `Peminjam`) | Ya | Mahasiswa dan Dosen mewarisi akses dari `Peminjam`. |
| **LAB-R08** | `LAB-UC02`, `LAB-UC08`, `LAB-UC09`, `LAB-UC10` | Ya (`Generalization` Use Case) | Ya | Pengelolaan data dalam bentuk tambah, ubah, dan hapus. |
| **LAB-R09** | `LAB-UC11` | Ya | Ya | Pencatatan pengembalian peralatan oleh Petugas. |
| **LAB-R10** | `LAB-UC12` | Ya (`<<include>>` dari `LAB-UC11`) | Ya | Pemeriksaan dan pencatatan kondisi fisik peralatan. |
| **LAB-R11** | `LAB-CO01`, `LAB-CO02` | Ya (`Realization` ke `UC03` & `UC11`) | Ya | Collaboration yang merealisasikan alur utama sistem. |

---

## B. Kasus SIA — Layanan Hasil Studi (Pertemuan 4)

### B.1 Uji Konsistensi Tiga Situasi
| Situasi | Diagram | Deskripsi | Konsisten? |
|:---:|---|---|:---:|
| **Akses kalender akademik (Civitas Akademika)** | `SIA-UC07` dihubungkan ke aktor umum `Civitas Akademika`. | `SIA-UC07` alur utama: Mahasiswa dan Dosen dapat melihat jadwal kalender akademik. | **Ya** |
| **Input nilai mata kuliah oleh Dosen** | `SIA-UC08` terhubung ke Dosen dan direalisasikan oleh `SIA-CO01`. | `SIA-UC08` memeriksa hak akses Dosen Pengampu; nilai tersimpan jika sah (0–100). | **Ya** |
| **Pengelolaan data mahasiswa oleh Admin** | `SIA-UC11`, `SIA-UC12`, `SIA-UC13` mewarisi (`Generalization`) `SIA-UC10`. | `SIA-UC13` memeriksa tidak ada data akademik aktif sebelum menghapus data mahasiswa. | **Ya** |

### B.2 Matriks Keterlacakan (Traceability)
| ID Kebutuhan | Use Case Terkait | Representasi Diagram | Dokumen Deskripsi | Keterangan |
|:---:|:---:|:---:|:---:|---|
| **SIA-R07** | `SIA-UC07` | Ya (`Generalization` Aktor) | Ya | Akses kalender akademik oleh Mahasiswa dan Dosen. |
| **SIA-R08** | `SIA-UC08` | Ya (`Realization` `SIA-CO01`) | Ya | Input nilai mata kuliah oleh Dosen Pengampu. |
| **SIA-R09** | `SIA-UC09` | Ya (`Realization` `SIA-CO02`) | Ya | Mahasiswa melihat KHS yang sudah dipublikasikan. |
| **SIA-R10 & SIA-R11** | `SIA-UC10`, `SIA-UC11`, `SIA-UC12`, `SIA-UC13` | Ya (`Generalization` Use Case) | Ya | Pengelolaan data mahasiswa (tambah, ubah, hapus). |
| **SIA-R12** | `SIA-CO01`, `SIA-CO02` | Ya (`Realization`) | Ya | Pemodelan collaboration perwujudan alur utama. |

---

## C. Checklist Evaluasi Model Pertemuan 4

| Indikator Evaluasi | Kasus LAB | Kasus SIA | Status Evaluasi |
|---|:---:|:---:|:---:|
| Panah `Generalization` aktor mengarah tepat dari aktor khusus ke aktor umum | ✓ (`M/D` → `Peminjam`) | ✓ (`M/D` → `Civitas`) | Terpenuhi |
| Panah `Generalization` use case mengarah tepat dari use case khusus ke use case umum | ✓ (`UC08-10` → `UC02`) | ✓ (`UC11-13` → `UC10`) | Terpenuhi |
| Collaboration digambar elips putus-putus dan terhubung `Realization` ke use case | ✓ (`CO01/CO02`) | ✓ (`CO01/CO02`) | Terpenuhi |
| Tidak ada garis asosiasi langsung dari Aktor menuju ke Collaboration | ✓ | ✓ | Terpenuhi |
| Seluruh elemen lama Pertemuan 3 dipertahankan utuh tanpa menimpa file berkas P03 | ✓ | ✓ | Terpenuhi |
| File sumber diagram (`.drawio`) dan ekspor gambar (`.png`) sinkron versi `v01` | ✓ | ✓ | Terpenuhi |

---

## D. Log Review Rekan / Asisten Praktikum Pertemuan 4

| No | Kasus | Temuan Review *(Arah Panah / Kondisi / Extension Point / Pascakondisi)* | Tindakan Perbaikan | Versi Terakhir |
|:---:|:---:|---|---|:---:|
| **1** | LAB | *Arah panah generalization aktor Dosen terbalik ke arah luar.* | Mengubah arah panah segitiga kosong menunjuk ke aktor umum `Peminjam`. | `v01` |
| **2** | SIA | *Garis realization collaboration SIA-CO01 dihubungkan ke Aktor Dosen.* | Menghapus garis ke Aktor dan menghubungkannya ke Use Case `SIA-UC08`. | `v01` |