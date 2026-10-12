## a. SIA-UC01 — Ajukan KRS

| Bagian | Isi |
|---|---|
| **ID dan nama** | SIA-UC01 — Ajukan KRS |
| **Sumber kebutuhan** | SIA-R03, SIA-R04, SIA-R05 |
| **Tujuan** | Menghasilkan pengajuan KRS yang tersimpan dan menunggu persetujuan dosen wali |
| **Aktor utama** | Mahasiswa |
| **Aktor pendukung** | — |
| **Pemicu** | Mahasiswa memilih fungsi pengajuan KRS |
| **Prasyarat** | Mahasiswa telah terautentikasi; data mata kuliah, prasyarat, dan jadwal tersedia |
| **Include** | SIA-UC02 — Validasi KRS (dipanggil pada langkah 4) |
| **Extension point** | Bukti pengajuan tersedia, pada langkah 6 |
| **Extend** | SIA-UC03 — Unduh bukti pengajuan KRS jika `[mahasiswa memilih unduh]` |
| **Pascakondisi berhasil** | Pengajuan tersimpan dengan nomor dan status *Menunggu persetujuan dosen wali* |
| **Pascakondisi gagal** | Tidak ada pengajuan baru yang berhasil tersimpan |
| **Aturan bisnis/asumsi** | Validasi gagal = tidak tersimpan; unduh bukti bukan syarat keberhasilan; tersimpan ≠ disetujui |

**Alur Utama**

| Langkah | Tindakan Mahasiswa | Respons Sistem |
|:---:|---|---|
| 1 | Membuka pengajuan KRS | Menampilkan formulir dan daftar mata kuliah |
| 2 | Memilih mata kuliah | Menampung pilihan |
| 3 | Mengirim pengajuan | Menerima pengajuan |
| 4 | — | Menjalankan **SIA-UC02 Validasi KRS** |
| 5 | — | Jika validasi berhasil, menyimpan pengajuan, memberi nomor, dan menetapkan status *Menunggu persetujuan dosen wali* |
| 6 | Melihat konfirmasi | Menampilkan nomor dan status; mencapai *extension point* **Bukti pengajuan tersedia** |
| 7 | Mengakhiri pengajuan | Menutup proses pengajuan |

**Alur Alternatif / Pengecualian**

| Rujukan | Kondisi | Respons dan Hasil Akhir |
|:---:|---|---|
| 2a | Mahasiswa membatalkan sebelum mengirim | Tidak ada data disimpan; pascakondisi gagal. |
| 4a | Validasi gagal (dari SIA-UC02) | Sistem menampilkan alasan (data tidak lengkap, prasyarat tidak terpenuhi, atau benturan jadwal). Pengajuan **tidak disimpan**. Mahasiswa kembali ke langkah 2. Jika membatalkan: pascakondisi gagal. |
| 6a | Mahasiswa memilih unduh bukti | Menjalankan **SIA-UC03 Unduh bukti pengajuan KRS**, lalu kembali ke langkah 7. Status pengajuan tidak berubah. |

---

## b. SIA-UC02 — Validasi KRS

| Bagian | Isi |
|---|---|
| **ID dan nama** | SIA-UC02 — Validasi KRS |
| **Sumber kebutuhan** | SIA-R04 |
| **Tujuan** | Memastikan pilihan mata kuliah lengkap, memenuhi prasyarat, dan tidak berbenturan jadwal |
| **Aktor utama** | — *(Dijalankan sistem atas pemanggilan dari SIA-UC01)* |
| **Aktor pendukung** | — |
| **Pemicu** | SIA-UC01 mencapai langkah 4 (memanggil fungsi validasi) |
| **Prasyarat** | Pilihan mata kuliah diterima dari SIA-UC01; data mata kuliah, prasyarat, dan jadwal tersedia |
| **Pascakondisi berhasil** | Hasil "valid" dikembalikan ke SIA-UC01. Belum ada penyimpanan. |
| **Pascakondisi gagal** | Hasil "tidak valid" beserta daftar alasan dikembalikan ke SIA-UC01; data tidak berubah. |
| **Aturan bisnis/asumsi** | Validasi mencakup tiga pemeriksaan; semua temuan dikumpulkan dan dikembalikan sekaligus. |

**Alur Utama**

| Langkah | Respons Sistem |
|:---:|---|
| 1 | Menerima pilihan mata kuliah dari SIA-UC01. |
| 2 | Memeriksa kelengkapan pengajuan (ada mata kuliah yang dipilih dan data wajib terisi). |
| 3 | Memeriksa prasyarat setiap mata kuliah yang dipilih. |
| 4 | Memeriksa benturan jadwal antar mata kuliah yang dipilih. |
| 5 | Menetapkan hasil "valid" bila ketiga pemeriksaan lolos, lalu mengembalikan status ke SIA-UC01. |

**Alur Alternatif / Pengecualian**

| Rujukan | Kondisi | Respons dan Hasil Akhir |
|:---:|---|---|
| 2a | Data tidak lengkap | Mencatat temuan "tidak lengkap", lanjut ke langkah 3. |
| 3a | Prasyarat belum terpenuhi | Mencatat mata kuliah yang bermasalah, lanjut ke langkah 4. |
| 4a | Terdapat benturan jadwal | Mencatat pasangan mata kuliah yang berbenturan, lanjut ke langkah 5. |
| 5a | Ada minimal satu temuan (2a/3a/4a) | Menetapkan hasil "tidak valid", mengembalikan semua alasan ke SIA-UC01 (SIA-UC01 mengeksekusi alur alternatif 4a). |

---

## c. SIA-UC03 — Unduh Bukti Pengajuan KRS

| Bagian | Isi |
|---|---|
| **ID dan nama** | SIA-UC03 — Unduh bukti pengajuan KRS |
| **Sumber kebutuhan** | SIA-R05 |
| **Tujuan** | Mahasiswa memperoleh berkas bukti pengajuan KRS yang dapat disimpan |
| **Aktor utama** | Mahasiswa |
| **Aktor pendukung** | — |
| **Pemicu** | Pada konfirmasi pengajuan, mahasiswa memilih opsi untuk mengunduh bukti |
| **Prasyarat** | Mahasiswa terautentikasi; SIA-UC01 mencapai *extension point* **Bukti pengajuan tersedia** |
| **Extend terhadap** | SIA-UC01 pada *extension point* **Bukti pengajuan tersedia**, kondisi `[mahasiswa memilih unduh]` |
| **Pascakondisi berhasil** | Berkas bukti pengajuan diterima mahasiswa; data dan status pengajuan tidak berubah. |
| **Pascakondisi gagal** | Berkas bukti tidak terunduh; pengajuan tetap tersimpan dalam sistem. |
| **Aturan bisnis/asumsi** | Unduh bukti bersifat opsional dan bukan syarat keberhasilan pengajuan. |

**Alur Utama**

| Langkah | Tindakan Mahasiswa | Respons Sistem |
|:---:|---|---|
| 1 | Memilih unduh bukti pengajuan | Menerima pilihan mahasiswa. |
| 2 | — | Menyiapkan berkas bukti (memuat nomor pengajuan, status, daftar mata kuliah, dan waktu). |
| 3 | — | Menyediakan berkas untuk diunduh. |
| 4 | Menerima berkas | Kembali ke SIA-UC01 langkah 7. |

**Alur Alternatif / Pengecualian**

| Rujukan | Kondisi | Respons dan Hasil Akhir |
|:---:|---|---|
| 2a | Berkas bukti gagal disiapkan/diunduh | Menampilkan pesan kesalahan; pascakondisi gagal; pengajuan di SIA-UC01 tetap aman tersimpan. |

---

## d. SIA-UC04 — Proses Keputusan KRS

| Bagian | Isi |
|---|---|
| **ID dan nama** | SIA-UC04 — Proses keputusan KRS |
| **Sumber kebutuhan** | SIA-R06 |
| **Tujuan** | Menetapkan keputusan KRS mahasiswa menjadi *Disetujui* atau *Ditolak* beserta catatan keputusan |
| **Aktor utama** | Dosen Wali |
| **Aktor pendukung** | — |
| **Pemicu** | Dosen wali memilih fungsi proses keputusan KRS |
| **Prasyarat** | Dosen wali telah terautentikasi; terdapat pengajuan KRS berstatus *Menunggu persetujuan dosen wali* |
| **Pascakondisi berhasil** | Status pengajuan diperbarui menjadi *Disetujui* atau *Ditolak*, dan catatan keputusan tersimpan |
| **Pascakondisi gagal** | Status pengajuan tetap *Menunggu persetujuan dosen wali* |
| **Aturan bisnis/asumsi** | KRS tersimpan belum tentu disetujui; persetujuan dan penolakan adalah dua variasi hasil dari satu use case. |

**Alur Utama (Persetujuan)**

| Langkah | Tindakan Dosen Wali | Respons Sistem |
|:---:|---|---|
| 1 | Membuka fungsi proses keputusan KRS | Menampilkan daftar pengajuan KRS berstatus *Menunggu persetujuan dosen wali*. |
| 2 | Memilih salah satu pengajuan | Menampilkan rincian pilihan mata kuliah mahasiswa. |
| 3 | Memilih keputusan **Setuju** | Menampung pilihan keputusan. |
| 4 | Mengisi catatan keputusan | Menampung catatan. |
| 5 | Mengonfirmasi keputusan | Menyimpan keputusan, mengubah status menjadi *Disetujui*, dan mencatat waktu keputusan. |
| 6 | Melihat konfirmasi | Menampilkan status akhir dan catatan yang telah tersimpan. |

**Alur Alternatif / Pengecualian**

| Rujukan | Kondisi | Respons dan Hasil Akhir |
|:---:|---|---|
| 2a | Tidak ada pengajuan yang menunggu | Menampilkan informasi bahwa daftar pengajuan kosong; pascakondisi gagal. |
| 3a | Dosen wali memilih keputusan **Tolak** | Lanjut ke langkah 4. Pada langkah 5, sistem mengubah status menjadi *Ditolak* dan menyimpan catatan penolakan. Pascakondisi berhasil (tujuan menetapkan keputusan tercapai). |
| 5a | Dosen wali membatalkan sebelum konfirmasi | Sistem membatalkan perubahan; status pengajuan tetap *Menunggu persetujuan dosen wali*; pascakondisi gagal. |