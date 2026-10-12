## A. Kasus LAB — Peminjaman Peralatan Laboratorium

### A.1 Uji Konsistensi
| Situasi | Diagram | Deskripsi | Konsisten? |
|:---:|---|---|:---:|
| **Alat tersedia, tidak mencetak** | `LAB-UC03` menjalankan `LAB-UC04` (`<<include>>`); kondisi `<<extend>>` tidak terpenuhi. | `LAB-UC03` langkah 1–7 (tanpa 6a); pengajuan tersimpan dengan status *Menunggu keputusan*. | **Ya** |
| **Alat tidak tersedia** | `LAB-UC04` tetap dijalankan; *extension point* tidak tercapai. | `LAB-UC03` alur alternatif 4a: data tidak disimpan; pascakondisi gagal. | **Ya** |
| **Alat tersedia, mahasiswa mencetak** | `LAB-UC05` memperluas `LAB-UC03` pada *extension point* **Bukti pengajuan tersedia**, kondisi `[mahasiswa memilih cetak]`. | `LAB-UC03` langkah 6a lalu mengeksekusi `LAB-UC05`; status pengajuan tidak berubah. | **Ya** |

### A.2 Matriks Keterlacakan (Traceability)
| ID Kebutuhan | Use Case Terkait | Representasi Diagram | Dokumen Deskripsi | Keterangan |
|:---:|:---:|:---:|:---:|---|
| **LAB-R01** | `LAB-UC01` | Ya | Belum ditulis | Representasi diagram ada; deskripsi belum disusun. |
| **LAB-R02** | `LAB-UC02` | Ya | Belum ditulis | Representasi diagram ada; deskripsi belum disusun. |
| **LAB-R03** | `LAB-UC03`, `LAB-UC04` | Ya (`<<include>>`) | Ya | Terlacak penuh pada diagram dan deskripsi. |
| **LAB-R04** | `LAB-UC05` | Ya (`<<extend>>`) | Ya | Terlacak penuh pada diagram dan deskripsi. |
| **LAB-R05** | `LAB-UC06` | Ya | Ya | Terlacak penuh pada diagram dan deskripsi. |
| **LAB-R06** | `LAB-UC07` | Ya | Belum ditulis | Representasi diagram ada; deskripsi belum disusun. |


## B. Kasus SIA — Pengajuan KRS

### B.1 Uji Konsistensi Tiga Situasi
| Situasi | Diagram | Deskripsi | Konsisten? |
|:---:|---|---|:---:|
| **Validasi berhasil, tidak mengunduh bukti** | `SIA-UC01` menjalankan `SIA-UC02` (`<<include>>`); `SIA-UC03` tidak dieksekusi. | `SIA-UC01` alur utama langkah 1–7 (tanpa 6a); tersimpan berstatus *Menunggu persetujuan dosen wali*. | **Ya** |
| **Validasi gagal** | `SIA-UC02` tetap dieksekusi; *extension point* tidak tercapai. | `SIA-UC01` alur alternatif 4a: data tidak disimpan; `SIA-UC02` alur 5a: mengembalikan status tidak valid. | **Ya** |
| **Validasi berhasil, mahasiswa mengunduh bukti** | `SIA-UC03` memperluas `SIA-UC01` pada *extension point* **Bukti pengajuan tersedia**, kondisi `[mahasiswa memilih unduh]`. | `SIA-UC01` alur alternatif 6a mengeksekusi `SIA-UC03`; status pengajuan tidak berubah. | **Ya** |

### B.2 Matriks Keterlacakan (Traceability)
| ID Kebutuhan | Use Case Terkait | Representasi Diagram | Dokumen Deskripsi | Keterangan |
|:---:|:---:|:---:|:---:|---|
| **SIA-R03** | `SIA-UC01` | Ya | Ya | Pengajuan KRS oleh Mahasiswa. |
| **SIA-R04** | `SIA-UC02` | Ya (`<<include>>`) | Ya | Validasi KRS otomatis oleh sistem. |
| **SIA-R05** | `SIA-UC03` | Ya (`<<extend>>`) | Ya | Unduh bukti pengajuan KRS (opsional). |
| **SIA-R06** | `SIA-UC04` | Ya | Ya | Memproses keputusan persetujuan/penolakan oleh Dosen Wali. |


## C. Checklist Evaluasi Model (Penulis)

| Indikator Evaluasi | Kasus LAB | Kasus SIA | Status Evaluasi |
|---|:---:|:---:|:---:|
| Setiap aktor mempunyai interaksi yang jelas dan spesifik | ✓ | ✓ | Terpenuhi |
| Use Case sesuai dengan kebutuhan dan berada di dalam *System Boundary* | ✓ | ✓ | Terpenuhi |
| Relasi `<<include>>` mengarah tepat ke perilaku yang disertakan | ✓ (`UC03` → `UC04`) | ✓ (`UC01` → `UC02`) | Terpenuhi |
| Relasi `<<extend>>` mengarah tepat ke Use Case dasar (*Base Use Case*) | ✓ (`UC05` → `UC03`) | ✓ (`UC03` → `UC01`) | Terpenuhi |
| *Extension point* ditempatkan secara eksplisit pada Use Case dasar | ✓ | ✓ | Terpenuhi |
| Kondisi `<<extend>>` tercantum jelas pada diagram/catatan dan deskripsi | ✓ | ✓ | Terpenuhi |
| Pengajuan tetap berhasil tersimpan tanpa perlu mengeksekusi perilaku tambahan | ✓ | ✓ | Terpenuhi |
| Prasyarat dibedakan secara tegas dari perilaku `<<include>>` (misal: Autentikasi = Prasyarat) | ✓ | ✓ | Terpenuhi |
| Alur alternatif menjelaskan skenario kegagalan beserta status pascakondisinya | ✓ | ✓ | Terpenuhi |
| Diagram dan deskripsi menggunakan ID dan penamaan yang konsisten | ✓ | ✓ | Terpenuhi |
| File sumber diagram dapat dibuka dan diedit kembali (`.drawio` / `.puml`) | ✓ | ✓ | Terpenuhi |
| File ekspor gambar (`.png`) sinkron dengan versi sumber diagram terkini (`v01`) | ✓ | ✓ | Terpenuhi |
| Kebutuhan yang belum dimodelkan atau berada di luar cakupan ditandai secara jelas | ✓ *(Deskripsi UC01, UC02, UC07; Pengembalian & Denda)* | ✓ *(SIA-R01, SIA-R02; Hasil Keputusan untuk Mahasiswa)* | Terpenuhi |

## D. Log Review Rekan / Asisten Praktikum

*(Tabel ini diisi secara bertahap saat melakukan proses review bersama rekan atau asisten laboratorium)*

| No | Kasus | Temuan Review *(Arah Panah / Kondisi / Extension Point / Pascakondisi)* | Tindakan Perbaikan | Versi Terakhir |
|:---:|:---:|---|---|:---:|
| **1** | SIA | *Contoh: Panah `<<extend>>` terbalik arahnya pada draf awal.* | Mengubah arah panah dari `SIA-UC03` menuju ke Use Case dasar `SIA-UC01`. | `v02` |
| **2** | LAB | *Contoh: Teks kondisi extend belum dituliskan pada diagram.* | Menambahkan note `condition: [mahasiswa memilih cetak]` pada garis extend. | `v02` |

