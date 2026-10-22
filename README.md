# Dataset Nutrisi Makanan

Kumpulan data komposisi gizi makanan beserta berkas latih/uji untuk penelitian pemodelan nutrisi. Data dihimpun dari dua sumber: basis data **FoodData Central** milik USDA (Amerika Serikat) dan **Tabel Komposisi Pangan Indonesia (TKPI) 2020** terbitan Kementerian Kesehatan Republik Indonesia.

## Pemilik

- Muhamad Erwin Hariadinata
- Muh Nune Huria Sakti
- Hendra Ahmad Yani

## Sumber data

### 1. USDA FoodData Central — rilis 22 April 2025

Folder `FoodData_Central_csv_2025-04-24/` berisi unduhan lengkap basis data FoodData Central dalam format CSV, 31 berkas.

- Penerbit: U.S. Department of Agriculture, Agricultural Research Service
- Situs resmi: https://fdc.nal.usda.gov
- Unduhan resmi: https://fdc.nal.usda.gov/download-datasets.html
- Status hak cipta: domain publik. USDA menyatakan data FoodData Central bebas digunakan tanpa izin khusus.

Sitasi yang disarankan oleh penerbit:

> U.S. Department of Agriculture, Agricultural Research Service. FoodData Central, 2025. fdc.nal.usda.gov.

### 2. Tabel Komposisi Pangan Indonesia (TKPI) 2020

Berkas `Traintest/524164641-TKPI-2020.pdf` berisi TKPI 2020, tabel komposisi pangan untuk bahan makanan Indonesia.

- Penerbit: Kementerian Kesehatan Republik Indonesia
- Status hak cipta: **hak cipta tetap pada Kementerian Kesehatan RI**

> **Peringatan hak cipta.** Berkas PDF TKPI 2020 disertakan di repositori ini sebagai rujukan penelitian, bukan sebagai karya milik pemilik repositori. Hak cipta sepenuhnya pada Kementerian Kesehatan Republik Indonesia. Salinan ini bukan terbitan resmi dan tidak dijamin keasliannya — untuk penggunaan resmi, rujuk terbitan asli dari Kemenkes RI. Bila pemegang hak cipta berkeberatan atas pencantumannya di sini, berkas akan dihapus atas permintaan.

## Struktur

```
FoodData_Central_csv_2025-04-24/     Unduhan USDA FoodData Central, 31 berkas CSV
├── food.csv.gz                      205,6 MB (terkompresi jadi 34,8 MB)
├── fndds_ingredient_nutrient_value.csv
├── food_nutrient_*.csv, food_portion.csv, nutrient.csv, ...
└── Download API Field Descriptions.xlsx

Traintest/                           Data turunan dan berkas latih/uji
├── fndds_nutrient_data3.json        2,4 MB — ekstraksi nutrisi FNDDS (bahasa Inggris)
├── terjemah.json                    1,0 MB — hasil terjemahan ke bahasa Indonesia
├── train.csv                        700 baris — kolom: makanan, deskripsi_nutrisi
├── test.csv                         199 baris — kolom: Makanan; deskripsi makanan
├── train.ipynb                      Notebook pemrosesan dan penerjemahan
└── 524164641-TKPI-2020.pdf          20 MB — lihat peringatan hak cipta di atas
```

### Membuka `food.csv.gz`

Berkas asli berukuran 205,6 MB, melewati batas 100 MB per berkas di GitHub, sehingga dimampatkan. Untuk mengembalikannya:

```bash
gunzip -k FoodData_Central_csv_2025-04-24/food.csv.gz
```

Atau baca langsung tanpa membongkar:

```python
import pandas as pd
df = pd.read_csv("FoodData_Central_csv_2025-04-24/food.csv.gz", compression="gzip")
```

## Catatan tentang data turunan

Berkas `terjemah.json` adalah hasil terjemahan otomatis dari `fndds_nutrient_data3.json` memakai `deep_translator` (Google Translate), sebagaimana terlihat pada `train.ipynb`. Terjemahan mesin dapat keliru pada istilah pangan dan gizi — nama makanan yang tidak punya padanan langsung dalam bahasa Indonesia kerap diterjemahkan secara harfiah. Periksa ulang sebelum dipakai untuk kesimpulan ilmiah.

`train.csv` dan `test.csv` adalah pembagian buatan pemilik repositori, bukan pembagian baku dari penerbit data asli.

## Lisensi

Isi repositori ini berasal dari beberapa sumber dengan status berbeda:

| Bagian | Status |
|---|---|
| `FoodData_Central_csv_2025-04-24/` | Domain publik (USDA) |
| `Traintest/524164641-TKPI-2020.pdf` | Hak cipta Kementerian Kesehatan RI |
| `terjemah.json`, `train.csv`, `test.csv`, `train.ipynb` | Karya turunan oleh pemilik repositori |

Gunakan tiap bagian sesuai ketentuan sumbernya masing-masing. Bila mengutip repositori ini dalam tulisan ilmiah, sebutkan juga sumber aslinya, bukan repositori ini saja.

## Penafian

Data komposisi gizi di sini untuk keperluan penelitian. Bukan panduan diet, bukan saran medis, dan tidak boleh dipakai sebagai dasar keputusan klinis atau terapi gizi.
