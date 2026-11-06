# TEMALI v9

## Perubahan utama
1. Database SIMS: filter Service diganti menjadi Frekuensi.
2. Monitoring ISR: filter kabupaten/kota dipindahkan ke filter dinamis; field filter mendukung ketik dan saran dropdown (datalist).
3. Kegiatan: aksi hapus mencoba menghapus hasil monitoring terkait sebelum menghapus kegiatan.
4. Dokumen: pratinjau menggunakan iframe modal di halaman, bukan popup tab baru; tombol cetak membuka dialog print browser.
5. Dashboard publik menjadi halaman pertama tanpa login. Data hanya dibaca dari `public_dashboard_aggregate` yang berisi publikasi Disetujui.
6. Dashboard internal mendapat filter tahun, bulan, kabupaten/kota.
7. Panel insight terhubung ke Edge Function `temali-insight`, dengan fallback statistik transparan jika function belum siap.

## Perlu dilakukan setelah ekstraksi
- Jalankan `supabase/v9_migration.sql` di Supabase SQL Editor.
- Untuk AI generatif, deploy `supabase/functions/temali-insight` dan atur secret `OPENAI_API_KEY`.
- Jalankan `npm.cmd install` lalu `npm.cmd run dev` pada Windows.
- File `.env` lama dapat disalin ke root proyek; jangan pernah memasukkan service_role key ke frontend.

## Catatan
Build belum dapat diverifikasi dalam lingkungan ini karena instalasi dependensi npm mengalami timeout. Uji di komputer pengembangan sebelum deployment.

## v9.2 – AI Tanya Jawab, Dashboard Publik dan Peta Monitoring
- Dashboard publik menampilkan agregat hasil monitoring aktual tanpa menunggu batch publikasi disetujui.
- Menghapus menu halaman Dashboard Publik dari navigasi internal; dashboard publik tetap menjadi halaman awal sebelum login.
- Menghapus kartu Publikasi disetujui.
- Menambahkan total ISR unik termonitor, jumlah hasil sesuai/tidak sesuai, jumlah kabupaten/kota termonitor, peta sebaran, dan tabel rekap kabupaten/kota.
- Peta menggunakan titik tengah perkiraan kabupaten/kota; bukan koordinat stasiun atau pengguna.
- Memperbaiki aksi pratinjau dokumen dengan validasi pembuatan HTML, tombol bertipe button, dan iframe yang fleksibel.
- Menambahkan migrasi `supabase/v9_2_public_dashboard.sql` untuk view agregat aman yang dapat dibaca anon.


## Revisi tampilan 6 November 2026
- Refresh tema dan layout agar mengikuti referensi TEMALI_bismillah.html.
- Tambah kontrol sembunyikan/tampilkan sidebar desktop.
- Ubah generator dokumen menjadi modal/workspace yang dibuka melalui tombol Buat Dokumen.
