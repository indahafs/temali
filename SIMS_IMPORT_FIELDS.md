# Catatan format impor SIMS

File contoh memiliki 92 kolom. Importer menerima header dinamis dan menyimpan seluruh nilai pada `raw_data` JSONB. Header wajib untuk validasi dasar: `APPL_ID`, `CLNT_NAME`, `FREQ`. Duplikasi diperiksa dengan SHA-256 atas keseluruhan baris 92 kolom; APPL_ID bukan kunci unik.

Field tampilan ternormalisasi: `APPL_ID`, `NO_SIMF`, `SITE_ID`, `CLNT_NAME`, `STATUS_SIMF`, `SERVICE`, `FREQ`, `BWIDTH`, `EQ_MDL`, `STN_NAME`, `STN_ADDR`, `CITY`, `DISTRICT`, `PROVINCE`, `SID_LAT`, `SID_LONG`. Semua field sumber lainnya tetap tersimpan pada `raw_data`.
