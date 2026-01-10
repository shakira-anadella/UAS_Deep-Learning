<h1 align="center">📊 Proyek UAS Deep Learning</h1>
<h2 align="center">Analisis Sentimen Ulasan Pengguna Aplikasi E-Commerce di Google Play Store Menggunakan Metode Deep Learning (LSTM)</h2>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.9+-blue">
  <img src="https://img.shields.io/badge/Deep%20Learning-TensorFlow-orange">
  <img src="https://img.shields.io/badge/Status-Completed-success">
</p>

<hr>

<h2>🪶 Latar Belakang</h2>
<p align="justify">
Google Play Store menyediakan ribuan ulasan pengguna yang mencerminkan opini,
kepuasan, dan permasalahan terhadap suatu aplikasi. Namun, ketidakseimbangan
distribusi sentimen (class imbalance) sering menjadi tantangan dalam analisis
sentimen berbasis pembelajaran mesin.
</p>

<p align="justify">
Oleh karena itu, proyek ini menerapkan pendekatan <b>Deep Learning</b> untuk melakukan
<b>analisis sentimen otomatis</b>, sekaligus mengevaluasi pengaruh <i>class imbalance</i>
dan teknik <i>oversampling</i> terhadap performa model.
</p>

<hr>

<h2>🗂️ Dataset dan Sumber Data</h2>
<ul>
  <li><b>Sumber data:</b> Google Play Store</li>
  <li><b>Metode:</b> Web scraping mandiri menggunakan Python</li>
  <li><b>Library:</b> <code>google-play-scraper</code></li>
  <li><b>Total data:</b> ≥ 3.000 ulasan</li>
  <li><b>Format:</b> CSV</li>
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

<h2>⚙️ Model dan Skema Pelatihan</h2>

<table border="1" cellpadding="8" cellspacing="0">
  <thead>
    <tr>
      <th>No</th>
      <th>Model</th>
      <th>Pembagian Data</th>
      <th>Teknik Tambahan</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1</td>
      <td>LSTM</td>
      <td>80% Train – 20% Test</td>
      <td>Class Weight</td>
    </tr>
    <tr>
      <td>2</td>
      <td>CNN</td>
      <td>80% Train – 20% Test</td>
      <td>Oversampling</td>
    </tr>
    <tr>
      <td>3</td>
      <td>BiLSTM</td>
      <td>70% Train – 30% Test</td>
      <td>Bidirectional Layer</td>
    </tr>
  </tbody>
</table>

<hr>

<h2>📈 Hasil dan Evaluasi Model</h2>

<table border="1" cellpadding="8" cellspacing="0">
  <thead>
    <tr>
      <th>Model</th>
      <th>Accuracy Testing</th>
      <th>Catatan</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>LSTM / CNN (tanpa oversampling)</td>
      <td><b>85.41%</b></td>
      <td>Memenuhi kriteria UAS</td>
    </tr>
    <tr>
      <td>CNN (dengan oversampling)</td>
      <td>≈ 79.6%</td>
      <td>Distribusi kelas lebih seimbang</td>
    </tr>
    <tr>
      <td>BiLSTM (70/30)</td>
      <td>≈ 81.75%</td>
      <td>Model pembanding</td>
    </tr>
  </tbody>
</table>

<p align="justify">
Hasil eksperimen menunjukkan bahwa meskipun oversampling berhasil memperbaiki
ketidakseimbangan kelas, peningkatan performa model tidak selalu tercermin
langsung pada nilai akurasi. Hal ini menunjukkan adanya trade-off antara
keseimbangan data dan kemampuan generalisasi model.
</p>

<hr>

<h2>🧪 Inference / Prediksi Sentimen</h2>
<pre>
Input  : "Aplikasinya sangat membantu dan mudah digunakan"
Output : Positif
</pre>

<hr>

<h2>📂 Struktur Repository</h2>
<pre>
📁 UAS_Deep-Learning
│
├── 📁 data
│   ├── dataset_raw.csv
│   ├── dataset_clean.csv
├── scraping.ipynb 
├── training.ipynb 
├── requirements.txt
├── README.md

</pre>

<hr>

<h2>✅ Kesimpulan</h2>
<p align="justify">
Proyek ini berhasil memenuhi seluruh kriteria tugas UAS Deep Learning. Model
Deep Learning mampu mengklasifikasikan sentimen ulasan dengan baik, serta
menunjukkan bahwa penanganan ketidakseimbangan data merupakan aspek penting
dalam analisis sentimen. Eksperimen ini memberikan dasar yang kuat untuk
pengembangan lebih lanjut menggunakan model berbasis Transformer.
</p>

<p align="center">
✨ <i>Disusun untuk memenuhi Ujian Akhir Semester (UAS) Mata Kuliah Deep Learning.</i>
</p>
