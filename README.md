# TEMALI — Terpadu Monitoring Analitik Legalitas ISR

## Versi tampilan HTML referensi

Halaman utama project sekarang menggunakan langsung `index.html` yang berasal dari file `TEMALI_bismillah.html` sebagai acuan tampilan dan interaksi. Struktur React lama di folder `src/` tetap disimpan sebagai arsip pengembangan, tetapi tidak lagi dipanggil oleh halaman utama.

## Menjalankan secara lokal

Persyaratan: Node.js dan npm.

```bash
npm install
npm run dev
```

Buka alamat lokal yang ditampilkan Vite.

## Build untuk Vercel

- Framework Preset: Vite
- Build Command: `npm run build`
- Output Directory: `dist`
- Install Command: `npm install`

## Catatan integrasi data

Tampilan dan alur interaksi mengikuti HTML referensi. Data contoh/simulasi dan integrasi eksternal yang sudah tertanam di HTML tetap mengikuti implementasi referensi tersebut. Kode React/Supabase lama masih disimpan di `src/`, tetapi tidak aktif pada entry point ini. Integrasi ke Supabase perlu disambungkan secara eksplisit pada versi HTML ini apabila diperlukan.
