# 🌧️ Binary Rainfall Prediction with XGBoost  

> submission untuk [Kaggle Playground Series - Maret 2025](https://www.kaggle.com/competitions/playground-series-s5e3)

📘 Lihat juga eksperimen submission dengan model LSTM milik saya di Kaggle Notebook berikut:  
[LSTM Rainfall Prediction by Ikhwan Ramadhan](https://www.kaggle.com/code/ikhwanramadhan/ltsm-rainfall-prediction)

## 🧾 Informasi Kompetisi   

1. Nama Kompetisi: Playground Series - Season 5, Episode 3     
2. Platform: Kaggle        
3. Tugas: Klasifikasi biner Apakah akan hujan atau tidak?    
4. Metrik Evaluasi: ROC-AUC Score 

---

## 📌 Deskripsi Proyek

Selamat datang di kompetisi **Kaggle Playground Series 2025**!  
Repositori ini berisi solusi lengkap untuk kompetisi prediksi curah hujan harian menggunakan pendekatan pembelajaran mesin.

**Tujuan**: Memprediksi apakah akan terjadi hujan atau tidak pada suatu hari berdasarkan fitur cuaca seperti suhu, kelembapan, tekanan udara, kecepatan angin, dan informasi waktu.

---

Proyek ini dimulai dengan melakukan **Exploratory Data Analysis (EDA)** untuk memahami karakteristik data, distribusi target, serta hubungan antar variabel. Setelah itu, dilakukan beberapa tahapan lanjutan, yaitu:

- **Feature Engineering**: Menciptakan fitur-fitur baru seperti selisih suhu, encoding musiman, dan fitur temporal lainnya.
- **Preprocessing**: Meliputi normalisasi, penanganan missing values, dan penyeimbangan kelas menggunakan SMOTE.
- **Modeling**: Menggunakan tiga pendekatan berbeda — Random Forest, XGBoost, dan LSTM untuk mengevaluasi performa terbaik dalam konteks data tabular dan time-series.

Evaluasi model dilakukan dengan kombinasi stratified k-fold dan time-series split untuk memastikan generalisasi yang baik terhadap data yang belum terlihat.

---

## 🧠 Pendekatan Model

- **Model yang digunakan**: 
  - [Random Forest Classifier](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html)  
  - [LSTM (Long Short-Term Memory)](https://www.tensorflow.org/api_docs/python/tf/keras/layers/LSTM)  
  - [XGBoost Classifier](https://xgboost.readthedocs.io)

- **Feature Engineering**:
  - Selisih suhu maksimum dan minimum: `temp_range`
  - Selisih antara suhu dan titik embun: `temp_dew_diff`
  - *Cyclical encoding* untuk hari dalam setahun (`day_sin`, `day_cos`)
  - Fitur lag dan rolling statistik untuk mengidentifikasi pola temporal
- **Penanganan Data Tidak Seimbang**:
  - Menggunakan **SMOTE** untuk menyeimbangkan kelas "Rain" dan "No Rain"
- **Validasi Model**:
  - **Stratified K-Fold** untuk evaluasi umum
  - **TimeSeriesSplit** untuk pengujian generalisasi terhadap data waktu

---

## 📊 Ringkasan Hasil Evaluasi

| Metrik         | Nilai (Rata-rata ± Std) |
|----------------|--------------------------|
| Akurasi        | 0.9249 ± 0.0185          |
| Skor AUC       | 0.9769 ± 0.0095          |

Model menunjukkan performa tinggi dan stabil pada validasi silang, serta mampu mengklasifikasikan data secara konsisten.

---

## 🔍 Insight dari Evaluasi

- Model **XGBoost** memberikan performa sangat baik pada validasi *stratified*, tetapi menunjukkan hasil yang buruk pada **TimeSeriesSplit**, menandakan bahwa model kurang mampu menangkap dinamika waktu.
- Distribusi probabilitas prediksi menunjukkan dua kelompok dominan: satu dengan keyakinan tinggi bahwa tidak hujan, dan satu dengan keyakinan cukup tinggi bahwa hujan. Hal ini mengindikasikan bahwa model cukup percaya diri dalam prediksinya.
- Untuk peningkatan lebih lanjut, disarankan eksplorasi model berbasis sekuens seperti **LSTM** atau **GRU** yang lebih cocok untuk data deret waktu.

---

## 🚀 Cara Menjalankan

1. **Clone repositori ini**
```bash
git clone https://github.com/IngsR/Binary-Prediction-with-a-Rainfall-Dataset.git
```

```bash
cd Binary-Prediction-with-a-Rainfall-Dataset
```


```bash
python -m venv env
source env/bin/activate     # Untuk Linux/Mac
env\Scripts\activate        # Untuk Windows
```

```bash
conda create -n rainfall-prediction python=3.10
conda activate rainfall-prediction
```

```bash
pip install -r requirements.txt
```

```bash
 Select Kernel rainfall-prediction di jupyter notebook
```
---

<div align="center">

---

## 👨‍💻 Author [IngsR](https://github.com/IngsR) Ikhwan Ramadhan, 2025

</div>

   


