<h1 align="center">📊 Proyek UAS Deep Learning</h1>
<h2 align="center">Analisis Sentimen Ulasan Pengguna Aplikasi E-Commerce di Google Play Store Menggunakan Metode Deep Learning (LSTM)</h2>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.9+-blue">
  <img src="https://img.shields.io/badge/Deep%20Learning-TensorFlow-orange">
  <img src="https://img.shields.io/badge/Status-Completed-success">
</p>

<hr>

<h2>🪔 Latar Belakang</h2>
<p>
Ulasan pengguna pada aplikasi Play Store mengandung informasi penting mengenai
kualitas aplikasi. Namun, jumlah data yang besar membuat analisis manual tidak
efisien. Oleh karena itu, pendekatan <i>Deep Learning</i> digunakan untuk
mengklasifikasikan sentimen ulasan menjadi <b>negatif</b>, <b>netral</b>,
dan <b>positif</b>.
</p>

<hr>

<h2>🗂️ Dataset dan Sumber Data</h2>
<ul>
  <li>Sumber data: Google Play Store</li>
  <li>Metode pengambilan: Web Scraping</li>
  <li>Total data awal: <b>2.622 ulasan</b></li>
</ul>

<h3>🧭 Skema Pelabelan Sentimen</h3>
<ul>
  <li>⭐ Rating 1–2 → <b>Negatif</b></li>
  <li>⭐ Rating 3 → <b>Netral</b></li>
  <li>⭐ Rating 4–5 → <b>Positif</b></li>
</ul>

<hr>

<h2>🧹 Pemrosesan Data</h2>
<ul>
  <li>Case folding (lowercase)</li>
  <li>Penghapusan URL, angka, dan tanda baca</li>
  <li>Normalisasi spasi</li>
  <li>Filtering teks terlalu pendek</li>
  <li>Tokenisasi dan padding sequence</li>
</ul>

<h3>⚖️ Distribusi Kelas</h3>

<b>Sebelum Oversampling:</b>
<pre>
Positif (2) : 1431
Negatif (0) : 1041
Netral  (1) : 150
</pre>

<b>Sesudah Oversampling:</b>
<pre>
Positif (2) : 1431
Negatif (0) : 1041
Netral  (1) : 1041
</pre>

<p align="justify">
Oversampling diterapkan untuk meningkatkan representasi kelas netral yang
sebelumnya sangat sedikit, sehingga model dapat mempelajari pola sentimen
secara lebih seimbang.
</p>

<hr>

<h2>🧬 Model dan Skema Pelatihan</h2>

<h3>🔹 Skema 1 — CNN + Oversampling (Split 80/20)</h3>
<ul>
  <li>Arsitektur: Embedding → Conv1D → Conv1D → GlobalMaxPooling → Dense</li>
  <li>Oversampling: Ya</li>
  <li>Epoch: 12 (EarlyStopping)</li>
  <li><b>Akurasi Testing: 0.8716</b></li>
</ul>

<h3>🔹 Skema 2 — CNN Baseline (Tanpa Oversampling, Split 80/20)</h3>
<ul>
  <li>Arsitektur CNN sederhana</li>
  <li>Oversampling: Tidak</li>
  <li>Epoch: 6</li>
  <li><b>Akurasi Testing: 0.7943</b></li>
</ul>

<h3>🔹 Skema 3 — BiLSTM + Oversampling (Split 70/30)</h3>
<ul>
  <li>Arsitektur: Embedding → BiLSTM → Dense</li>
  <li>Oversampling: Ya</li>
  <li>Epoch: 6</li>
  <li><b>Akurasi Testing: 0.8614</b></li>
</ul>

<hr>

<h2>📈 Perbandingan Hasil Akurasi</h2>
<table border="1" cellpadding="6" cellspacing="0">
  <tr>
    <th>Skema</th>
    <th>Model</th>
    <th>Akurasi</th>
  </tr>
  <tr>
    <td>Skema 1</td>
    <td>CNN + Oversampling</td>
    <td><b>0.8716</b></td>
  </tr>
  <tr>
    <td>Skema 2</td>
    <td>CNN Baseline</td>
    <td>0.7943</td>
  </tr>
  <tr>
    <td>Skema 3</td>
    <td>BiLSTM + Oversampling</td>
    <td>0.8614</td>
  </tr>
</table>

<p>
<b>Model terbaik:</b> CNN dengan oversampling (Skema 1)
</p>

<hr>

<h2>🔮 Inference / Prediksi Sentimen</h2>
<p>Contoh hasil prediksi menggunakan model terbaik (CNN Skema 1):</p>

<ul>
  <li>
    <b>Teks:</b> Aplikasinya bagus banget, fiturnya lengkap dan cepat<br>
    <b>Prediksi:</b> Positif (Confidence: 0.9998)
  </li>
  <li>
    <b>Teks:</b> Error terus, tidak bisa login, parah<br>
    <b>Prediksi:</b> Negatif (Confidence: 0.944)
  </li>
  <li>
    <b>Teks:</b> Lumayan sih, tapi masih sering lemot<br>
    <b>Prediksi:</b> Negatif (Confidence: 0.7291)
  </li>
</ul>

<hr>

<h2>📂 Struktur Repository</h2>
<pre>
📁 UAS_Deep-Learning
├── data
│   ├── dataset_raw.csv
│   ├── dataset_clean.csv
│   └── .gitkeep
├── 01_scrapping.ipynb
├── 02_training.ipynb
├── README.md
└── requirements.txt
</pre>

<hr>

<h2>🏁 Kesimpulan</h2>
<p>
Eksperimen menunjukkan bahwa penerapan <b>oversampling</b> secara signifikan
meningkatkan performa model. CNN dengan oversampling menghasilkan akurasi
tertinggi dan dipilih sebagai model terbaik untuk sistem analisis sentimen ini.
</p>

<p align="center">
✨ <i>Proyek ini dibuat untuk memenuhi Ujian Akhir Semester (UAS) mata kuliah Deep Learning</i> ✨
</p>
