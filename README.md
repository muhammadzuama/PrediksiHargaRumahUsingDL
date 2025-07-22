
## 🏠 Prediksi Harga Rumah Menggunakan Model RNN (LSTM, BiLSTM, GRU, BiGRU)

### 📌 Ringkasan Proyek

Proyek ini bertujuan untuk memprediksi harga rumah menggunakan model deep learning berbasis *Recurrent Neural Networks* (RNN). Model yang diterapkan mencakup:

* **LSTM (Long Short-Term Memory)**
* **BiLSTM (Bidirectional LSTM)**
* **GRU (Gated Recurrent Unit)**
* **BiGRU (Bidirectional GRU)**

Meskipun RNN umumnya digunakan untuk data sekuensial atau deret waktu, dalam proyek ini RNN diaplikasikan ke data tabular untuk mengeksplorasi kemampuannya dalam melakukan regresi.

---

### 📁 Dataset

Dataset mencakup berbagai fitur properti seperti:

* Jumlah kamar tidur dan kamar mandi
* Luas bangunan (dalam sqft)
* Lokasi (kota, dikodekan dengan One-Hot Encoding)
* Kondisi bangunan, kualitas, tahun dibangun
* Harga rumah (target)

> **Catatan**: Dataset ini **tidak** mengandung informasi tanggal, sehingga data dibagi secara **acak (random split)** untuk training dan testing.

---

### ⚙️ Pra-pemrosesan Data

Langkah-langkah pra-pemrosesan meliputi:

* Menghapus kolom yang tidak relevan: `['date', 'street', 'country', 'statezip']`
* Mengubah kolom kategori `city` menjadi numerik dengan **One-Hot Encoding**
* Normalisasi data menggunakan **MinMaxScaler**
* Membentuk input agar sesuai dengan format RNN: `(samples, timesteps, features)`

---

### 🧠 Arsitektur Model

Semua model memiliki arsitektur dasar sebagai berikut:

* **Dua layer RNN** (LSTM, GRU, atau versi bidirectional)
* **Beberapa layer Dense** dengan aktivasi ReLU
* **Dropout layer** untuk regularisasi
* **Output layer**: 1 neuron untuk prediksi harga

Model dikompilasi dengan:

```python
optimizer='adam'
loss='mse'
metrics=['mae']
```

---

### 📊 Evaluasi Model

Evaluasi dilakukan menggunakan **10-Fold Cross Validation** untuk memastikan model tidak overfitting dan dapat digeneralisasi dengan baik.

Metrik evaluasi:

* **MAE**: Mean Absolute Error
* **MSE**: Mean Squared Error
* **R² Score**: Koefisien Determinasi

---

### 📈 Hasil Evaluasi (10-Fold CV)

| Model      | MAE     | MSE     | R² Score |
| ---------- | ------- | ------- | -------- |
| **LSTM**   | 0.00515 | 0.00033 | 0.5582   |
| **BiLSTM** | 0.00515 | 0.00034 | 0.5540   |
| **GRU**    | 0.00546 | 0.00034 | 0.5242   |
| **BiGRU**  | 0.00537 | 0.00034 | 0.5393   |

---

### 🏆 Model Terbaik

* **LSTM** memberikan performa terbaik secara keseluruhan, khususnya pada metrik R² dan MSE.
* Perbedaan antara LSTM dan BiLSTM sangat kecil, namun LSTM sedikit lebih stabil dalam evaluasi cross-validation.

---

### ✅ Kesimpulan

* Meskipun tanpa fitur waktu, model RNN masih menunjukkan performa baik untuk regresi data tabular.
* LSTM dan BiLSTM adalah pilihan paling optimal dalam prediksi harga rumah pada dataset ini.
* Cross-validation membantu mengevaluasi model secara menyeluruh dan mengurangi risiko overfitting.

---

### 🚀 Pengembangan Selanjutnya

* Bandingkan dengan model tradisional seperti **Random Forest**, **XGBoost**, atau **Linear Regression**.
* Tambahkan fitur baru atau lakukan rekayasa fitur (*feature engineering*).
* Integrasikan data gambar atau peta jika tersedia, dan eksplorasi model CNN.

---

Jika kamu ingin README ini dalam format `.md` untuk GitHub atau dokumentasi, tinggal beri tahu, saya bisa bantu generasikan file-nya.
