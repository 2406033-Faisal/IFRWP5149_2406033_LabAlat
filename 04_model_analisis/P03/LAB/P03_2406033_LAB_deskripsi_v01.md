|Elemen                   |   LAB-UC03 — Ajukan peminjaman
|Tujuan                   |   Menghasilkan pengajuan peminjaman yang tersimpan
|Aktor                    |   utama Mahasiswa
|Sumber kebutuhan         |   LAB-R03 dan LAB-R04
|Pemicu                   |   Mahasiswa memilih fungsi pengajuan peminjaman
|rasyarat                 |   Mahasiswa telah terautentikasi; data peralatan tersedia
|ascakondisi berhasil     |   Pengajuan tersimpan dengan nomor dan status Menunggu keputusan
|Pascakondisi gagal       |   Tidak ada pengajuan baru yang berhasil tersimpan
|nclude                   |   LAB-UC04 — Periksa ketersediaan
|xtension point           |   Bukti pengajuan tersedia, pada langkah 6
|Extend                   |   LAB-UC05 jika [mahasiswa memilih cetak]


|Langkah  |       Tindakan mahasiswa                              |    Respons sistem
|1        |       Membuka pengajuan                               |    Menampilkan formulir
|2        |       Memilih alat, jumlah, rentang waktu, dan tujuan |    Menampung isian
|3        |       Mengirim pengajuan Memeriksa kelengkapan data   |    Memeriksa kelengkapan data
|4 —      |                                                       |    Menjalankan LAB-UC04
|5 —      |                                                       |    Jika tersedia, menyimpan pengajuan dan memberikan nomor
|6        |       Melihat konfirmasi                              |    Menampilkan nomor dan status; mencapai extension point
|7        |       Mengakhiri pengajuan                            |    Menutup proses pengajuan