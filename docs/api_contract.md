# Kontrak API awal

Status: rencana implementasi, belum ada endpoint aktif.

| Bagian | Rancangan |
|---|---|
| Method dan path | `POST /predict` |
| Framework | FastAPI |
| Body | `multipart/form-data` |
| Field | `file` |
| Isi field | Satu citra postur duduk tampak samping |
| Tahap | Validasi gambar, preprocessing, inference, pemetaan kelas, response JSON |

Contoh struktur respons berikut hanya ilustrasi kontrak, bukan hasil inference:

```json
{
  "prediction": "Postur Bagus"
}
```

Nilai `prediction` yang direncanakan: `Postur Bagus` atau `Tidak Bagus`.

## Preprocessing dan model

Gunakan ukuran input, kanal warna, normalisasi, dan urutan indeks kelas yang sesuai dengan model hasil training. Preprocessing evaluasi dan API harus konsisten. Augmentasi acak hanya untuk training. Framework inference dan format bobot ditentukan setelah rancangan model disepakati.

## Rencana pengujian Postman

| Kasus | Hal yang akan diperiksa |
|---|---|
| Gambar valid | Permintaan diterima dan respons memiliki label yang diizinkan |
| Field file kosong | API memberikan respons kesalahan yang jelas |
| Berkas bukan gambar/rusak | API menolak input dengan respons kesalahan |
| Gambar yang sama pada inference lokal dan API | Preprocessing serta prediksi konsisten |

Status HTTP dan format detail pesan error akan ditetapkan saat implementasi. Pengujian endpoint memastikan alur API bekerja; kualitas klasifikasi dinilai terpisah menggunakan metrik pada data uji.
