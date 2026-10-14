# Rencana evaluasi

Status: rancangan proposal, belum merupakan hasil eksperimen.

## Pembagian peserta

1. Siapkan metadata identitas peserta untuk setiap foto mandiri.
2. Tetapkan kelompok peserta training, validasi, dan uji tanpa tumpang tindih.
3. Terapkan augmentasi acak hanya pada data training setelah pembagian dilakukan.
4. Gunakan data publik yang lolos audit hanya sebagai tambahan training.
5. Gunakan set uji foto mandiri yang sama untuk seluruh model dan baseline.

Jumlah peserta pada setiap subset belum ditetapkan. Data uji tidak digunakan untuk memilih konfigurasi, ambang prediksi, atau model yang akan dipasang pada API.

## Metrik

Macro F1 = (F1 kelas Postur Bagus + F1 kelas Tidak Bagus) / 2.

| Metrik | Peran |
|---|---|
| Macro F1-score | Metrik utama, bobot sama untuk kedua kelas |
| Accuracy | Proporsi prediksi benar secara keseluruhan |
| Precision per kelas | Ketepatan saat model memprediksi kelas tersebut |
| Recall per kelas | Kemampuan menemukan seluruh contoh kelas tersebut |
| Confusion matrix 2 × 2 | Pola pertukaran prediksi antar-kelas |

## Perbandingan dan analisis

MobileNetV2 akan dibandingkan dengan model pembanding dan baseline yang ditetapkan kelompok. Referensi pembagian tugas menyebut EfficientNet-B0, CNN sederhana, dan aturan sudut dari keypoint MediaPipe. Gunakan peserta pada subset yang sama dan preprocessing yang sesuai bagi setiap arsitektur. Kesesuaian ini tidak berarti semua arsitektur harus menerima normalisasi numerik yang identik.

Catat contoh prediksi benar dan salah, termasuk kemungkinan pengaruh variasi postur, pakaian, pencahayaan, dan latar belakang. Jangan menyimpulkan penyebab kesalahan sebelum contoh citra diperiksa. Subjenis postur Tidak Bagus tetap metadata, bukan kelas keluaran tambahan.

Jika baseline keypoint gagal menemukan pose, catat jumlah kegagalannya dan jelaskan perlakuannya dalam evaluasi; jangan diam-diam menghapus contoh itu hanya dari evaluasi baseline.

## Sumber

Carneros-Prado dkk. (2024), DOI 10.1109/ACCESS.2024.3510034, PDF hlm. 7: evaluasi berdasarkan peserta. Pradhan dkk. (2026), DOI 10.3390/fi18090494, PDF hlm. 14–15: metrik dan confusion matrix. Angka hasil kedua artikel tidak menjadi angka hasil atau target wajib proyek ini.
