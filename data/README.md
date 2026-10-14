# Data

Data belum disertakan dalam kerangka ini. Target awal pengumpulan mandiri adalah sekitar 300 foto dari sekitar 15 peserta, dengan dua kelas.

Nama folder kelas yang direncanakan: `postur_bagus` dan `tidak_bagus`.

Kolom metadata yang diusulkan:

| Kolom | Isi |
|---|---|
| `image_path` | Lokasi gambar |
| `participant_id` | Identitas kode peserta untuk pemisahan data |
| `label` | `Postur Bagus` atau `Tidak Bagus` |
| `split` | `train`, `validation`, atau `test` |
| `source` | `mandiri` atau sumber publik yang lolos audit |
| `posture_variant` | Subjenis postur untuk analisis, bila berlaku |

Pemisahan dilakukan per peserta sebelum augmentasi. Data publik hanya untuk training. Foto peserta tidak dimasukkan ke repository Public melalui paket ini.
