# TEMALI v9.2 — AI Insight & Tanya Jawab

## Pembaruan
- Panel Insight AI dashboard dirapikan menjadi panel Asisten Analisis TEMALI.
- Menambahkan input pertanyaan bebas dan tiga contoh pertanyaan.
- Pertanyaan dikirim bersama ringkasan filter aktif dan sampel maksimum 40 hasil monitoring.
- Edge Function menjawab pertanyaan berdasarkan data yang dikirim, dengan instruksi agar tidak mengarang fakta.
- Pesan gagal kini menampilkan error aktual, bukan lagi pesan fallback lama yang menyebut fungsi belum di-deploy.

## Cara memasang pada project yang sudah ada
1. Cadangkan folder project `temali-updated` yang sekarang.
2. Ekstrak ZIP ini.
3. Salin isi folder `temali-updated` dari ZIP ke folder project lokal, dan izinkan file yang sama ditimpa.
4. Pertahankan file `.env` lokal milik Anda. ZIP ini tidak menyertakan `.env` yang berisi kredensial.
5. Di terminal pada folder project jalankan `npm.cmd install` bila dependency belum terpasang, lalu `npm.cmd run dev`.
6. Buka Dashboard, cari panel **Insight & Tanya AI**.
7. Untuk mengaktifkan pertanyaan bebas, deploy ulang Edge Function karena kode fungsinya ikut diperbarui:

```powershell
npx.cmd supabase functions deploy temali-insight --use-api
```

## Keamanan
- `OPENAI_API_KEY` harus merupakan OpenAI API Key, bukan Supabase publishable/anon key.
- Simpan key hanya sebagai Supabase Function Secret. Jangan menaruhnya di `.env` frontend atau mengirimkannya melalui screenshot/chat.
- Pastikan pengguna sudah login; Edge Function memvalidasi access token Supabase.
- Analisis hanya menggunakan ringkasan dan maksimal 40 sampel hasil monitoring yang dikirim dari dashboard. Periksa kembali jawaban AI terhadap catatan dan bukti lapangan.

## Catatan verifikasi
Source telah diperbarui. Build Vite belum dapat dijalankan pada lingkungan pembuat karena instalasi dependency mengalami timeout; jalankan `npm.cmd run build` di komputer project untuk verifikasi build setelah file dipasang.
