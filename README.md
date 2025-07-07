---

# Proyek Analisis Sentimen dengan LSTM

Proyek ini adalah implementasi model Long Short-Term Memory (LSTM) untuk analisis sentimen pada berita keuangan berbahasa Inggris, dibangun dan dilatih menggunakan TensorFlow/Keras. Model ini mampu mengklasifikasikan teks ke dalam sentimen **negatif**, **netral**, atau **positif**.

---

## Struktur Proyek

Repositori ini memiliki struktur sebagai berikut:

```
nama-repositori-anda/
├── notebooks/
│   └── sentiment_analysis.ipynb   <- Notebook utama Anda
├── data/
│   └── testing_converted.xlsx     <- Dataset input
├── models/
│   ├── sentiment_lstm_model.h5    <- Model LSTM yang sudah dilatih
│   └── tokenizer.pkl              <- Objek Keras Tokenizer
├── README.md                      <- File ini
```

---

## Cara Menjalankan Kode di Google Colaboratory (Direkomendasikan)

Menggunakan Google Colab sangat direkomendasikan karena dapat memudahkan untuk menjalankan proyek ini.

#### 1\. Buka Notebook di Google Colab

- Klik file `notebooks/sentiment_analysis.ipynb` di repositori GitHub ini.
- Pilih "**Open in Colab**" di bagian atas untuk membukanya langsung di Google Colab.

#### 2\. Kloning Repositori ini

Untuk mendapatkan file `testing_converted.xlsx`, `sentiment_lstm_model.h5`, dan `tokenizer.pkl` ke lingkungan Colab Anda, Anda perlu mengkloning repositori ini. Jalankan perintah berikut di **sel Colab pertama Anda**:

```bash
!git clone https://github.com/Luthfiyana/lstm-sentiment-analysis.git
%cd lstm-sentiment-analysis/notebooks # Pindah ke direktori tempat notebook berada
```

#### 3\. Sesuaikan Path dalam Kode

Karena Anda telah mengkloning repositori, file data dan model akan berada di direktori relatif terhadap lokasi notebook. Pastikan path dalam kode Anda sudah benar dan merujuk ke lokasi yang tepat:

- **Untuk data (`Sel 2`):**
  ```python
  df = pd.read_excel('../data/testing_converted.xlsx')
  ```
- **Untuk model dan tokenizer (`Sel 3`):**
  ```python
  TOKENIZER_PATH = '../models/tokenizer.pkl'
  MODEL_PATH = '../models/sentiment_lstm_model.h5'
  ```

#### 4\. Instal Dependensi

Pastikan Anda memiliki _library_ Python berikut terinstal. Google Colab sudah menyediakan sebagian besar dari ini secara _default_. Jika ada yang kurang, Anda bisa menginstalnya dengan perintah `pip install` di sel Colab:

```bash
!pip install pandas openpyxl tensorflow scikit-learn matplotlib seaborn gradio
```

#### 5\. Jalankan Setiap Sel

Jalankan setiap sel di notebook secara berurutan.

- Kode akan **memuat** data, model, dan tokenizer dari lokasi relatif (yang berasal dari kloning GitHub Anda).
- Jika model belum ada (misalnya, Anda menghapus file `.h5` dari folder `models/` di GitHub, atau ini pertama kali Anda menjalankannya tanpa model yang tersimpan), model akan **dilatih** dan kemudian **disimpan** ke path relatif yang sama.

---

## File Penting

- `notebooks/sentiment_analysis.ipynb`: Notebook utama yang berisi seluruh kode untuk pra-pemrosesan data, pelatihan model, dan evaluasi.
- `data/testing_converted.xlsx`: Dataset input yang digunakan untuk pelatihan dan pengujian.
- `models/tokenizer.pkl`: Objek Keras Tokenizer yang sudah dilatih, digunakan untuk mengubah teks menjadi urutan numerik.
- `models/sentiment_lstm_model.h5`: Model LSTM yang sudah dilatih untuk klasifikasi sentimen.

---

## Penjelasan Singkat Kode

- **Sel 1:** Mengimpor semua _library_ yang diperlukan.
- **Sel 2:** Memuat data dari `testing_converted.xlsx`, membersihkan teks, dan menampilkan distribusi sentimen awal.
- **Sel 3:** Pra-pemrosesan data (tokenisasi, _padding_), pemetaan label sentimen ke numerik, pembagian data menjadi _training_ dan _testing set_, serta perhitungan `class_weights` untuk menangani ketidakseimbangan kelas.
- **Sel 4:**
  - Memeriksa apakah model dan tokenizer sudah ada di direktori `models/`.
  - Jika ada, model dan tokenizer dimuat.
  - Jika belum ada, model LSTM dibangun, dilatih, dan kemudian disimpan ke direktori `models/`.
  - Model dievaluasi menggunakan data uji, dan menampilkan Confusion Matrix serta Classification Report.

---
