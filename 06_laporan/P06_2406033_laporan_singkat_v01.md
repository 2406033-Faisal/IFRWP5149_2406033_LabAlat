# LAPORAN SINGKAT PRAKTIKUM PERTEMUAN 06

**Topik:** Activity Diagram: Dari Skenario ke Alur Aktivitas  
**Dokumen:** `P06_2406033_Laporan_Singkat_v01.md`

---

## 1. IDENTITAS ATRIBUT & METADATA

| Atribut | Keterangan |
|----------|------------|
| **ID Artefak** | `LAB-P06-ACT` / `SIA-P06-ACT` |
| **Judul** | Activity Diagram: Dari Skenario ke Alur Aktivitas |
| **Pertemuan** | 06 |
| **Pembuat** | Cecep Faisal Ahmad (NIM: 2406033) |
| **Sumber Kebutuhan** | LAB-R01 s.d. LAB-R11 & SIA-R07 s.d. SIA-R12 (Tabel Skenario Pertemuan 5) |
| **Kakas** | Draw.io / PlantUML & Markdown |
| **Versi & Tanggal** | v01 — 02 November 2026 |
| **Status** | Selesai |

---

## 2. RINGKASAN HASIL DOKUMENTASI & DELIVERABLES

Pada Pertemuan 6, dilakukan pemodelan alur aktivitas (**Activity Diagram**) yang diturunkan secara langsung dari **Tabel Skenario Use Case Pertemuan 5**. Seluruh artefak telah disusun sesuai struktur workspace standar `IFRWP5149_2406033_LabAlat/` versi `v01`.

### A. Deliverables Studi Kasus LAB (7 Activity Diagram)

1. **`P06_2406033_LAB_activity_lihat_ketersediaan_v01`** (`LAB-UC01`)  
   Pemodelan alur baca ketersediaan peralatan (Swimlane: Peminjam & Sistem).

2. **`P06_2406033_LAB_activity_kelola_data_v01`** (`LAB-UC02`, `UC08-10`)  
   Pemodelan 3 varian kelola data (*tambah*, *ubah*, *hapus*) dengan *decision/merge* vertikal teratur.

3. **`P06_2406033_LAB_activity_peminjaman_v01`** (`LAB-UC03`)  
   Pemodelan alur pengajuan peminjaman yang mengintegrasikan *include* `LAB-UC04` (Periksa Ketersediaan) dan cabang *extend* `LAB-UC05` (Cetak Bukti).

4. **`P06_2406033_LAB_activity_cetak_bukti_v01`** (`LAB-UC05`)  
   Pemodelan alur *extend* pencetakan bukti pengajuan bagi mahasiswa.

5. **`P06_2406033_LAB_activity_keputusan_v01`** (`LAB-UC06`)  
   Pemodelan proses keputusan persetujuan/penolakan oleh Petugas Laboratorium (Tugas Mandiri).

6. **`P06_2406033_LAB_activity_pengembalian_v01`** (`LAB-UC11`)  
   Pemodelan alur pengembalian alat dengan fitur **Fork & Join** untuk pemeriksaan fisik (`LAB-UC12`) dan kelengkapan aksesori secara paralel.

7. **`P06_2406033_LAB_activity_laporan_v01`** (`LAB-UC07`)  
   Pemodelan alur pemeriksaan laporan peminjaman (Swimlane khusus: Kepala Laboratorium & Sistem).

### B. Deliverables Tugas SIA (1 Activity Diagram Utuh)

- **`P06_2406033_SIA_activity_v01`** (`SIA-UC08` & `SIA-UC09`)  
  Activity Diagram terpadu dari *Input Nilai Mata Kuliah* sampai *Lihat KHS* yang menggunakan **4 Swimlane** (`Dosen`, `Sistem`, `Admin Akademik`, `Mahasiswa`). Memuat *decision* kelengkapan nilai serta **Fork & Join** untuk penerbitan KHS di portal dan pengiriman notifikasi.

---

## 3. CHECKLIST EVALUASI & KONSISTENSI MODEL

| Indikator Penilaian | Kriteria | LAB | SIA |
|---------------------|-----------|-----|-----|
| **Initial & Final Node** | Tepat 1 Initial Node & minimal 1 Final Node tanpa alur terputus | ✓ | ✓ |
| **Decision & Guard** | Seluruh cabang memiliki *guard* `[...]` lengkap dan bermuara ke *Merge/Final Node* | ✓ | ✓ |
| **Fork & Join** | Dipasang secara berpasangan untuk proses paralel | ✓ (`UC11`) | ✓ (`KHS`) |
| **Swimlane & Tanggung Jawab** | Aksi ditempatkan pada swimlane aktor pelakunya (Sistem pada swimlane Sistem) | ✓ | ✓ |
| **Keterlacakan Skenario** | Nama aksi konsisten dengan langkah skenario P05 | ✓ | ✓ |
| **Tata Letak Layout** | Bebas dari garis bertabrakan/berdempetan (`Ranksep`, `Nodesep`, `wrapWidth`) | ✓ | ✓ |

---

## 4. CATATAN PERBAIKAN TATA LETAK & REVISI MODEL

### 1. Penyelesaian Kendala Visual Layout (`kelola_data`)

Penggunaan parameter berikut:

```plantuml
skinparam Ranksep 60
skinparam Nodesep 50
skinparam wrapWidth 180
```

serta penambahan nodus `stop` langsung pada cabang kegagalan berhasil menghilangkan garis menyilang dan tumpang tindih pada alur percabangan `if-elif-else`.

### 2. Implementasi Fork-Join yang Tepat (`pengembalian` & `SIA_activity`)

Pemeriksaan fisik alat dan aksesori pada alur pengembalian LAB, serta penerbitan KHS dan pengiriman notifikasi pada SIA telah dipisah menggunakan `fork` dan disatukan kembali menggunakan `join` sebelum melanjutkan ke tahap pengesahan/perubahan status.

---

## 📦 BERKAS KODE UML & WORKSPACE COMPLETE

Seluruh berkas diagram dalam format:

- `.puml`
- `.drawio`
- `.png`

telah dikemas lengkap di dalam arsip:

```text
IFRWP5149_2406033_LabAlat_P06_LAB_SIA.zip
```

yang telah digenerasikan sebelumnya.

---

**Status Akhir:** ✅ Seluruh Activity Diagram LAB dan SIA telah selesai dimodelkan, diverifikasi terhadap skenario Use Case Pertemuan 5, serta memenuhi kaidah UML Activity Diagram yang mencakup penggunaan swimlane, decision/merge, fork/join, dan keterlacakan kebutuhan.   