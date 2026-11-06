# TEMALI v9.2 – Dashboard Publik & Peta Monitoring

## Fitur
1. Dashboard publik mengambil ringkasan langsung dari hasil monitoring aktual.
2. Kartu publikasi disetujui dihapus.
3. Menu Dashboard Publik di navigasi internal dihapus. Halaman awal sebelum login tetap dashboard publik.
4. Menampilkan total ISR unik termonitor, hasil sesuai, tidak sesuai, dan kabupaten/kota termonitor.
5. Peta interaktif Sulawesi Selatan dengan agregat per kabupaten/kota. Marker adalah titik tengah perkiraan kabupaten/kota, bukan lokasi stasiun.
6. Tabel agregat per kabupaten/kota tanpa identitas perusahaan, nomor ISR, koordinat, catatan, atau bukti.
7. Tombol pratinjau dokumen diberi handler eksplisit dan iframe pratinjau diperbaiki.

## Langkah pemasangan
1. Cadangkan folder project lama.
2. Ekstrak ZIP dan salin isi `temali-updated` ke folder project. Pertahankan file `.env` milik sendiri.
3. Jalankan `npm.cmd install` kemudian `npm.cmd run dev`.
4. Buka Supabase Dashboard → SQL Editor.
5. Jalankan seluruh isi file `supabase/v9_2_public_dashboard.sql`.
6. Muat ulang aplikasi. Dashboard publik akan membaca view `public_monitoring_summary`.

## Catatan data dan keamanan
- Dashboard publik hanya membaca view agregat `public_monitoring_summary`.
- View tersebut mengeluarkan kabupaten/kota, jumlah ISR unik, total hasil dan hitungan status. Tidak mengeluarkan nomor ISR, perusahaan, koordinat, catatan, maupun bukti.
- View menggunakan nama kota dari `sims_records.city`. Jika kosong, sistem mencoba mengenali nama kabupaten/kota dari `activities.location`; sisanya masuk kategori `Tidak diketahui`.
- Peta memuat pustaka Leaflet dan tile OpenStreetMap dari internet. Jika jaringan memblokir CDN/tile, peta dapat gagal tampil sementara rekap tabel tetap tersedia.
- Jumlah ISR dihitung sebagai distinct `sims_record_id` atau fallback `isr_id`. Satu ISR yang dimonitor berulang tetap dihitung satu pada kartu total ISR, sedangkan total hasil adalah jumlah catatan monitoring.
- Peta menggunakan titik tengah perkiraan kabupaten/kota untuk visualisasi, bukan koordinat ISR/stasiun aktual.

## Pemeriksaan pratinjau dokumen
Buka Dokumen & Laporan → lengkapi formulir → klik Pratinjau / cetak PDF. Pratinjau muncul sebagai overlay. Tombol Cetak / Simpan PDF menjalankan dialog cetak browser. Pilih Save as PDF.
