<!-- Deskripsi Skenario -->

Skenario berikut merupakan bahan latihan yang ditetapkan untuk jobsheet, bukan hasil pengumpulan kebutuhan laboratorium nyata. Skenario ini melanjutkan potongan model Pertemuan 3. Selain mahasiswa, dosen juga meminjam peralatan laboratorium untuk kegiatan praktikum dan penelitian. Mahasiswa dan dosen sama-sama dapat melihat ketersediaan peralatan dan mengajukan peminjaman. Petugas laboratorium mengelola data peralatan: menambah peralatan baru, mengubah data peralatan, dan menghapus data peralatan yang tidak lagi dipakai. Setelah peminjaman disetujui dan alat diambil, petugas mencatat pengembalian peralatan. Pada saat mencatat pengembalian, petugas memeriksa dan mencatat kondisi peralatan. Dua use case utama pada potongan model ini, Ajukan Peminjaman dan Catat Pengembalian Peralatan, ditunjukkan realisasinya oleh collaboration yang bersesuaian. Seluruh fungsi Pertemuan 3 tetap berlaku dan tetap digambar: pemeriksaan ketersediaan di dalam pengajuan, pencetakan bukti pengajuan oleh mahasiswa, proses keputusan peminjaman oleh petugas, dan laporan peminjaman untuk kepala laboratorium. Diagram Pertemuan 4 adalah diagram Pertemuan 3 yang ditambah, bukan diagram baru yang menggantikannya.

<!-- Aktor Utama dan Aktor Khusus -->

| Aktor | Kedudukan | Tujuan terhadap Sistem |
|---|---|---|
| Peminjam | Umum (*general*), baru pada Pertemuan 4 | Peran umum bagi peminjam peralatan. Mewariskan fungsinya kepada Mahasiswa dan Dosen. |
| Mahasiswa | Khusus dari Peminjam, tetap dari Pertemuan 3 | Melihat ketersediaan dan mengajukan peminjaman (diwarisi dari Peminjam), ditambah mencetak bukti pengajuan sebagai asosiasi khususnya sendiri. |
| Dosen | Khusus dari Peminjam, baru pada Pertemuan 4 | Melihat ketersediaan dan mengajukan peminjaman (diwarisi dari Peminjam). |
| Petugas Laboratorium | Tetap dari Pertemuan 3 | Mengelola data peralatan, memproses keputusan peminjaman, dan mencatat pengembalian peralatan. |
| Kepala Laboratorium | Tetap dari Pertemuan 3 | Melihat laporan peminjaman. |


| ID | Nama Use Case | Peran dalam Model | Sumber Kebutuhan |
|---|---|---|---|
| LAB-UC01 | Lihat Ketersediaan Peralatan | Tetap dari Pertemuan 3; fungsi aktor umum Peminjam | LAB-R01, LAB-R07 |
| LAB-UC02 | Kelola Data Peralatan | Tetap dari Pertemuan 3; use case umum bagi LAB-UC08, LAB-UC09, dan LAB-UC10 | LAB-R02, LAB-R08 |
| LAB-UC03 | Ajukan Peminjaman | Tetap dari Pertemuan 3; fungsi aktor umum Peminjam; menyertakan LAB-UC04; direalisasikan LAB-CO01 | LAB-R03, LAB-R07 |
| LAB-UC04 | Periksa Ketersediaan | Tetap dari Pertemuan 3; perilaku yang disertakan LAB-UC03 | LAB-R03 |
| LAB-UC05 | Cetak Bukti Pengajuan | Tetap dari Pertemuan 3; tambahan bersyarat pada LAB-UC03 melalui `<<extend>>` | LAB-R04 |
| LAB-UC06 | Proses Keputusan Peminjaman | Tetap dari Pertemuan 3; fungsi utama petugas | LAB-R05 |
| LAB-UC07 | Lihat Laporan Peminjaman | Tetap dari Pertemuan 3; fungsi utama kepala laboratorium | LAB-R06 |
| LAB-UC08 | Tambah Data Peralatan | Baru pada Pertemuan 4; use case khusus dari LAB-UC02 | LAB-R08 |
| LAB-UC09 | Ubah Data Peralatan | Baru pada Pertemuan 4; use case khusus dari LAB-UC02 | LAB-R08 |
| LAB-UC10 | Hapus Data Peralatan | Baru pada Pertemuan 4; use case khusus dari LAB-UC02 | LAB-R08 |
| LAB-UC11 | Catat Pengembalian Peralatan | Baru pada Pertemuan 4; fungsi utama petugas; direalisasikan LAB-CO02 | LAB-R09 |
| LAB-UC12 | Periksa Kondisi Peralatan | Baru pada Pertemuan 4; perilaku yang disertakan LAB-UC11 | LAB-R10 |



| Kelompok | Isi |
|---|---|
| Tetap sama dari Pertemuan 3 | Aktor Mahasiswa, Petugas Laboratorium, dan Kepala Laboratorium; use case LAB-UC01 sampai LAB-UC07; relasi `<<include>>` LAB-UC03 ke LAB-UC04; relasi `<<extend>>` LAB-UC05 ke LAB-UC03 lengkap dengan *condition* `[mahasiswa memilih cetak]` dan *extension point* `Bukti pengajuan tersedia`; asosiasi Petugas Laboratorium ke LAB-UC02 dan LAB-UC06; asosiasi Kepala Laboratorium ke LAB-UC07; serta asosiasi Mahasiswa ke LAB-UC05. |
| Berubah karena generalization aktor | Asosiasi ke LAB-UC01 dan LAB-UC03 yang pada Pertemuan 3 digambar dari Mahasiswa kini digambar satu kali dari Peminjam. Fungsi Mahasiswa tidak hilang karena Mahasiswa mewarisinya dari Peminjam. Inilah satu-satunya perubahan garis pada diagram lama, yang terjadi karena aturan *generalization*, bukan penghapusan fungsi. |
| Ditambah pada Pertemuan 4 | Aktor Peminjam dan Dosen; dua relasi *generalization* aktor; use case LAB-UC08, LAB-UC09, dan LAB-UC10 beserta tiga relasi *generalization* ke LAB-UC02; use case LAB-UC11 dan LAB-UC12 beserta relasi `<<include>>` di antara keduanya dan asosiasi Petugas Laboratorium ke LAB-UC11; serta *collaboration* LAB-CO01 dan LAB-CO02 beserta dua relasi *realization*. |


| ID | Nama Collaboration (Sama dengan Nama Use Case) | Use Case yang Direalisasikan |
|---|---|---|
| LAB-CO01 | Ajukan Peminjaman | LAB-UC03: Ajukan Peminjaman |
| LAB-CO02 | Catat Pengembalian Peralatan | LAB-UC11: Catat Pengembalian Peralatan |


| Elemen | LAB-UC11: Catat Pengembalian Peralatan |
|---|---|
| ID dan Nama | LAB-UC11: Catat Pengembalian Peralatan |
| Sumber Kebutuhan | LAB-R09 dan LAB-R10 |
| Tujuan | Pengembalian tercatat dan status peminjaman serta kondisi peralatan terbarui. |
| Aktor Utama | Petugas Laboratorium |
| Pemicu | Petugas memilih fungsi pencatatan pengembalian dan menentukan peminjaman yang akan dikembalikan. |
| Prasyarat | Petugas telah terautentikasi; peminjaman terpilih berstatus Dipinjam. |
| Pascakondisi Berhasil | Pengembalian tercatat dengan tanggal kembali dan kondisi peralatan; status peminjaman menjadi Selesai. |
| Pascakondisi Gagal | Tidak ada pengembalian baru yang tercatat; status peminjaman tidak berubah. |
| Include | LAB-UC12: Periksa Kondisi Peralatan |
| Collaboration | LAB-CO02: Catat Pengembalian Peralatan |


| Langkah | Tindakan Petugas | Respons Sistem |
|---|---|---|
| 1 | Memilih peminjaman yang akan dikembalikan. | Menampilkan data peminjaman terpilih dan statusnya. |
| 2 | Mengonfirmasi alat yang kembali dan jumlahnya. | Menampung konfirmasi petugas. |
| 3 | Tidak ada. | Memeriksa bahwa status peminjaman harus Dipinjam. |
| 4 | Tidak ada. | Menjalankan LAB-UC12: memeriksa dan mencatat kondisi peralatan. |
| 5 | Menyimpan pencatatan pengembalian. | Menyimpan tanggal kembali dan kondisi; mengubah status peminjaman menjadi Selesai. |
| 6 | Melihat konfirmasi. | Menampilkan ringkasan pengembalian. |


Mahasiswa dan Dosen ditetapkan sebagai aktor khusus dari aktor umum Peminjam.

**Alasan:**
Mahasiswa dan Dosen sama-sama dapat melihat ketersediaan peralatan dan mengajukan peminjaman. Oleh karena itu, fungsi umum tersebut ditempatkan pada aktor Peminjam agar tidak perlu digambarkan berulang kali.

**Keputusan pemodelan:**
1. Mahasiswa merupakan aktor khusus dari Peminjam.
2. Dosen merupakan aktor khusus dari Peminjam.
3. Asosiasi Peminjam dengan LAB-UC01 dan LAB-UC03 digambar satu kali dari aktor Peminjam.
4. Mahasiswa tetap memiliki asosiasi khusus dengan LAB-UC05 Cetak Bukti Pengajuan.
5. Fungsi umum Peminjam diwariskan kepada Mahasiswa dan Dosen.

LAB-UC08, LAB-UC09, dan LAB-UC10 ditetapkan sebagai bentuk khusus dari LAB-UC02 Kelola Data Peralatan.

| Use Case Khusus | Use Case Umum | Perilaku Pembeda |
|---|---|---|
| LAB-UC08 — Tambah Data Peralatan | LAB-UC02 — Kelola Data Peralatan | Menambahkan data peralatan baru ke dalam sistem. |
| LAB-UC09 — Ubah Data Peralatan | LAB-UC02 — Kelola Data Peralatan | Mengubah informasi data peralatan yang telah tersedia. |
| LAB-UC10 — Hapus Data Peralatan | LAB-UC02 — Kelola Data Peralatan | Menghapus data peralatan yang memenuhi aturan penghapusan. |

**Alasan:**
Ketiga use case tersebut merupakan bentuk khusus dari kegiatan pengelolaan data peralatan. Generalization digunakan untuk menunjukkan hubungan antara fungsi umum dan fungsi-fungsi khususnya.


| ID Collaboration | Nama Collaboration | Use Case yang Direalisasikan | Alasan |
|---|---|---|---|
| LAB-CO01 | Ajukan Peminjaman | LAB-UC03 — Ajukan Peminjaman | Ajukan Peminjaman merupakan salah satu use case utama yang realisasinya ditunjukkan secara eksplisit pada model. |
| LAB-CO02 | Catat Pengembalian Peralatan | LAB-UC11 — Catat Pengembalian Peralatan | Catat Pengembalian Peralatan merupakan use case utama baru pada Pertemuan 4 yang realisasinya ditunjukkan secara eksplisit. |

**Aturan pemodelan:**
1. Collaboration digambarkan sebagai elips dengan garis putus-putus.
2. Nama collaboration sama dengan nama use case yang direalisasikan.
3. Relasi realization berupa garis putus-putus dengan segitiga kosong yang mengarah ke use case.
4. Collaboration tidak dihubungkan langsung dengan aktor.
5. Collaboration untuk use case lain tidak ditambahkan pada model Pertemuan 4.


1. Sistem mencatat dan menyediakan informasi. Perpindahan fisik peralatan tidak dilakukan di dalam perangkat lunak.
2. Pengguna harus telah terautentikasi dan memiliki hak akses sesuai perannya.
3. Pengembalian hanya dapat dicatat jika status peminjaman adalah Dipinjam.
4. Peminjaman dengan status Menunggu Keputusan atau Ditolak tidak dapat dicatat pengembaliannya.
5. Kondisi peralatan yang dikembalikan dicatat menggunakan salah satu nilai berikut: Baik, Rusak Ringan, atau Rusak Berat.
6. Penghapusan data peralatan hanya dapat dilakukan untuk peralatan yang tidak sedang dipinjam dan tidak memiliki pengajuan aktif.
7. Keterlambatan pengembalian dan denda belum dimodelkan pada pertemuan ini.


Hal-hal berikut belum ditetapkan dalam skenario dan perlu dikonfirmasi sebelum dimodelkan lebih lanjut.

1. Bagaimana aturan penanganan keterlambatan pengembalian peralatan?
2. Apakah keterlambatan dikenai denda? Jika iya, bagaimana ketentuan dan perhitungannya?

Catatan: Pertanyaan terbuka ini tidak boleh dianggap sebagai aturan sistem yang sudah ditetapkan.

Sebelum diagram dan dokumen dikumpulkan, lakukan pemeriksaan berikut.

- [ ] Seluruh aktor dan use case dari Pertemuan 3 tetap dipertahankan.
- [ ] Aktor Peminjam menjadi aktor umum bagi Mahasiswa dan Dosen.
- [ ] Asosiasi Peminjam ke LAB-UC01 dan LAB-UC03 hanya digambar satu kali.
- [ ] Asosiasi Mahasiswa ke LAB-UC05 tetap dipertahankan.
- [ ] LAB-UC08, LAB-UC09, dan LAB-UC10 merupakan bentuk khusus LAB-UC02.
- [ ] LAB-UC11 menyertakan LAB-UC12 melalui relasi include.
- [ ] Petugas Laboratorium terhubung dengan LAB-UC11.
- [ ] Kepala Laboratorium hanya terhubung dengan LAB-UC07.
- [ ] LAB-CO01 merealisasikan LAB-UC03.
- [ ] LAB-CO02 merealisasikan LAB-UC11.
- [ ] Tidak ada garis langsung dari aktor ke collaboration.
- [ ] Nama dan ID pada skenario, katalog, deskripsi use case, dan diagram konsisten.
- [ ] Keterlambatan dan denda dicatat sebagai pertanyaan terbuka, bukan aturan baru.

