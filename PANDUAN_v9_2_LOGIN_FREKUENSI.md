# TEMALI v9.2.1 — Penyempurnaan Login dan Format Frekuensi

## Penyempurnaan login
- Tombol Daftar dan Kembali ke Dashboard Publik dipisahkan dalam susunan vertikal.
- Tombol tampil/sembunyikan password.
- Autocomplete email dan password sesuai standar browser.
- Tombol masuk memiliki state proses, indikator loading, dan hover/focus yang lebih jelas.
- Tampilan responsif untuk layar kecil.

## Penanganan frekuensi SIMS
Setelah memeriksa file SIMS 28 OKTOBER 2026, nilai FREQ sumber tidak boleh dikalikan 100 secara massal.
Contoh record sumber:
- BASARNAS, Land Mobile (private), CODAN MBS TRANSCEIVER: 4.4450 MHz.
- MATSC, Aeronautical Ground-To-Air Transmitter, R&S MR-4100: 8.8820 MHz.
Nilai-nilai tersebut konsisten dengan kanal HF dalam MHz. Mengalikan 4.445 menjadi 444.5 MHz akan mengubah kanal HF menjadi frekuensi yang berbeda dan keliru.
Karena itu:
- FREQ disimpan apa adanya dari sumber SIMS dan diperlakukan sebagai MHz.
- FREQ_PAIR dan BWIDTH tidak dikonversi otomatis.
- Raw source tetap utuh dalam raw_data.
- Label tabel dan filter diperjelas menjadi MHz.
- Nilai di bawah 10 MHz tidak dianggap salah hanya karena kurang dari 10.

Jika unit ekspor SIMS berubah pada sumber lain, lakukan pemetaan unit secara eksplisit saat impor, bukan tebakan berdasarkan besar angka.
