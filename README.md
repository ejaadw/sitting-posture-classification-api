# Pengembangan Model Deep Learning untuk Klasifikasi Postur Duduk Berbasis Citra dan Implementasi API

Proyek mata kuliah Deep Learning A, Program Studi Teknologi Informasi, Universitas Udayana, 2026.

## Status proyek

Tahap proposal untuk presentasi 14 Oktober 2026. Dokumen dan struktur folder ini merupakan kerangka awal. Kode training, model terlatih, dan endpoint prediksi belum diimplementasikan dalam paket ini. Belum ada hasil eksperimen atau hasil pengujian API. Repository GitHub belum dipublikasikan melalui paket ini.

Nama repository yang diusulkan: `sitting-posture-classification-api`.

## Anggota

Nama mengikuti slide kelompok. Angka berikut adalah nomor yang tercantum pada slide, bukan NIM lengkap.

| Nama | Nomor pada slide |
|---|---|
| Nadhira Salsabila | 022 |
| Awan Ganter | 030 |
| Reza Kurniawan | 167 |

Reza bertugas sebagai Anggota 3: evaluasi, API, dokumentasi, dan integrasi. Penetapan nama untuk peran Anggota 1 dan 2 mengikuti kesepakatan kelompok.

## Tujuan dan ruang lingkup

Mengembangkan model Deep Learning yang mengklasifikasikan satu citra postur duduk tampak samping dan menyediakan akses prediksi melalui API.

| Label tampilan | Nama folder |
|---|---|
| Postur Bagus | `postur_bagus` |
| Tidak Bagus | `tidak_bagus` |

Variasi membungkuk, kepala condong ke depan, dan bersandar berlebihan dicatat sebagai metadata kelas Tidak Bagus. Definisi operasional kelas ditetapkan dalam protokol pelabelan kelompok.

## Rencana data dan model

- Target awal pengumpulan mandiri: sekitar 15 peserta, 10 foto per kelas per peserta, sehingga sekitar 300 foto. Ini target, bukan jumlah data yang sudah terkumpul.
- Data dibagi berdasarkan identitas peserta menjadi training, validasi, dan uji. Peserta tidak boleh tumpang tindih antar-subset.
- Dataset publik masih dalam audit dan hanya direncanakan sebagai tambahan training. Data uji hanya menggunakan foto yang dikumpulkan sendiri.
- Model utama yang direncanakan: MobileNetV2.
- Kandidat pembanding pada PDF pembagian tugas: EfficientNet-B0, CNN sederhana dari nol, dan baseline aturan sudut dari keypoint MediaPipe. Daftar akhir mengikuti keputusan kelompok.
- Ukuran input, normalisasi, framework training, dan konfigurasi fine-tuning mengikuti rancangan model Anggota 2. Kerangka ini belum menetapkan nilai yang belum disepakati.

## Rencana evaluasi

Macro F1-score menjadi metrik utama. Accuracy, precision, recall, dan confusion matrix menjadi pendukung. Precision dan recall dilaporkan per kelas.

Target awal pengumpulan data seimbang, tetapi proporsi akhir dapat berubah setelah seleksi dan penambahan data. Macro F1 memberi bobot sama pada F1 setiap kelas.

Model dibandingkan pada pembagian peserta dan data uji yang sama. Pemilihan konfigurasi menggunakan validasi; data uji digunakan untuk evaluasi akhir. Analisis mencakup contoh prediksi benar dan salah serta variasi postur Tidak Bagus pada metadata.

Rincian: [rencana evaluasi](docs/evaluation_plan.md).

## Rencana API

| Komponen | Rencana |
|---|---|
| Framework | FastAPI |
| Endpoint | `POST /predict` |
| Input | Satu berkas citra melalui `multipart/form-data`, field `file` |
| Preprocessing | Mengikuti preprocessing evaluasi model terpilih |
| Inference | Model hasil training kelompok |
| Output | JSON berisi `prediction`: `Postur Bagus` atau `Tidak Bagus` |
| Pengujian | Postman |

Urutan proses: input gambar, preprocessing, model, prediksi kelas, lalu response JSON.

Rincian: [kontrak API awal](docs/api_contract.md). Belum tersedia perintah menjalankan server karena implementasi belum dibuat.

## Struktur proyek yang disiapkan

| Lokasi | Fungsi yang direncanakan |
|---|---|
| `src/training/` | Kode training dan evaluasi model |
| `src/preprocessing/` | Transformasi citra yang dipakai bersama |
| `src/inference/` | Pemuatan bobot model dan prediksi |
| `src/api/` | Aplikasi FastAPI dan endpoint |
| `notebooks/` | Eksplorasi dan eksperimen |
| `data/` | Petunjuk data dan metadata peserta |
| `models/` | Petunjuk bobot model dan tautan unduhan |
| `tests/` | Pengujian yang akan dibuat saat implementasi |
| `docs/` | Rencana evaluasi dan kontrak API |
| `requirements.txt` | Dependensi awal API; dependensi training menyusul |

Folder kode hanya berisi penanda `.gitkeep` agar struktur dapat dilacak Git.

## Bobot model

Tautan Google Drive belum tersedia. Setelah training, cantumkan tautan bobot, format model, pemetaan indeks kelas, dan konfigurasi preprocessing di `models/README.md`.

## Jadwal resmi 2026

| Tanggal | Kegiatan |
|---|---|
| 14 Oktober | Presentasi proposal |
| 21 Oktober | Presentasi perkembangan |
| 28 Oktober | Presentasi perkembangan |
| 11 November | Presentasi perkembangan |
| 18 November | Presentasi perkembangan |
| 25 November | Presentasi perkembangan |
| 2 Desember | Presentasi akhir |
| 9 Desember | Pengumpulan akhir |

## Referensi untuk bagian evaluasi

1. Carneros-Prado, D., et al. (2024). A Comparison Between Multilayer Perceptrons and Kolmogorov-Arnold Networks for Multi-Task Classification in Sitting Posture Recognition. IEEE Access, 12, 180198–180209. [DOI](https://doi.org/10.1109/ACCESS.2024.3510034). PDF hlm. 7 mendukung pemisahan peserta. Proyek tidak mengklaim telah menerapkan LOSO.
2. Pradhan, A. K., et al. (2026). Comparative Analysis of Transfer Learning Architectures for Human Posture Classification Using Silhouette Images. Future Internet, 18, 494. [DOI](https://doi.org/10.3390/fi18090494). PDF hlm. 14–15 mendukung pemilihan metrik dan analisis kesalahan. Backbone MobileNet pada artikel adalah MobileNetV1.

## Publikasi repository

Repository direncanakan berstatus Public. Publikasi memerlukan akun pemilik dan persetujuan kelompok. Paket ini belum memiliki URL GitHub dan belum diunggah sebagai repository Public. Foto peserta dan bobot model tidak disertakan dalam paket kerangka.
