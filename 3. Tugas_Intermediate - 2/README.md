# 🐍 Tugas 3: Data Analytics & Cleaning with Python

Proyek ini mendokumentasikan proses analisis data menggunakan **Python** untuk dataset penjualan "Kopi Nangkau" periode 2021-2023. Fokus utama proyek ini adalah menangani data yang hilang (*missing values*) dan tidak konsisten menggunakan logika pemrograman yang selaras dengan aturan bisnis perusahaan.

🔗 **[Lihat Google Colab Di Sini]
https://colab.research.google.com/drive/1Xx6XWCkBlEryDaZk16Kf4p9QuDt6iy3J?usp=sharing
---

## 🛠️ Alur Kerja (Workflow)

### 1. Eksplorasi Data Awal
* **Library yang Digunakan:** `Pandas`, `NumPy`, `Matplotlib`, dan `Seaborn`.
* **Aturan Bisnis (Pricing Logic):** Implementasi fungsi `calculate_yearly_price` untuk menangani kenaikan harga otomatis sebesar **2% setiap tahun** dari harga dasar tahun 2021.
* **Identifikasi Masalah:** Ditemukan 500 baris data yang memiliki nilai kosong pada kolom `Produk`, `Unit_Terjual`, dan `Harga_Per_Unit`.

### 2. Data Cleaning & Logic Imputation
Saya menerapkan teknik pembersihan data yang cerdas untuk memulihkan informasi yang hilang berdasarkan keterkaitan antar kolom:

* **Pemulihan Nama Produk:** Jika nama produk kosong namun harga tersedia, sistem secara otomatis menentukan produk yang sesuai berdasarkan kecocokan harga dan tahun transaksi.
* **Kalkulasi Harga Otomatis:** Jika harga kosong namun nama produk ada, sistem mengisi nilai tersebut menggunakan rumus kenaikan harga tahunan (2% per tahun).
* **Penghapusan Data Tidak Valid:** * Menghapus baris di mana `Produk` dan `Harga_Per_Unit` keduanya bernilai kosong.
    * Menghapus baris dengan `Unit_Terjual` bernilai negatif atau kosong.
    * Membersihkan data duplikat untuk memastikan akurasi total penjualan.

### 3. Validasi Konsistensi
Melakukan pengecekan akhir menggunakan fungsi `np.isclose` untuk memastikan seluruh harga per unit yang tercatat sudah konsisten dengan aturan kenaikan harga tahunan yang ditetapkan perusahaan.

---

## 💡 Findings & Strategic Recommendations

### 1. Integritas Sistem Pencatatan
* **Temuan:** Banyaknya data kosong pada nama produk (meskipun harga tercatat) menunjukkan adanya celah pada sistem input manual di lapangan.
* **Rekomendasi:** Mengintegrasikan skrip Python ini ke dalam sistem kasir untuk memvalidasi input secara *real-time* berdasarkan database harga pusat.

### 2. Analisis Struktur Harga
* **Temuan:** Dengan kenaikan harga 2% per tahun, margin keuntungan meningkat secara bertahap.
* **Rekomendasi:** Perlu dilakukan analisis korelasi lebih lanjut untuk melihat apakah kenaikan harga tahunan ini berdampak pada penurunan volume unit yang terjual di setiap kategori produk.

### 3. Optimalisasi Operasional
* **Rekomendasi:** Fokus pada kategori produk yang paling resilien terhadap kenaikan harga (tetap memiliki unit terjual yang stabil) untuk dijadikan menu *bundling* di masa mendatang.

---

## 🚀 Tech Stack
* **Language:** Python
* **Libraries:** Pandas (Data Manipulation), NumPy (Numerical Logic), Seaborn & Matplotlib (Data Visualization).
* **Tool:** Jupyter Notebook / Google Colab.