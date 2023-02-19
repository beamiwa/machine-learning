# E-commerce Churn Prediction
Dalam jangka panjang, customer churn akan memberikan dampak kerugian yang besar bagi perusahaan karena biaya untuk memperoleh customer baru 6x lebih mahal daripada biaya untuk mempertahankan customer lama.

# Tujuan
Proyek ini bertujuan untuk mengurangi tingkat churn dengan bantuan model prediksi, serta untuk menemukan faktor penting yang mempengaruhi customer churn. Dengan mengetahui faktor-faktor tersebut dapat membantu perusahaan E-commerce untuk menerapkan strategi pemasaran yang tepat sasaran kepada customer yang akan churn saja sehingga biaya pemasaran menjadi tidak sia-sia karena salah sasaran.

# Dataset
- Data historikal 1 tahun yang terdiri dari 3941 data riwayat aktivitas customer dan 10 features.
- Target menjelaskan apakah pelanggan akan churn atau tidak.

# Data Preprocessing
- Missing Values Handling
- Feature Engineering
- Feature Encoding
- Feature Transformation
- Outlier Handling
- Target Imbalance Handling

# Metric
Saya merasa FN dan FP sama-sama penting, maka sebisa mungkin yang akan saya lakukan adalah membuat model yang dapat membuat customer tidak berkurang/hilang tanpa membuat biaya pemasaran sia-sia. Saya perlu meminimalisir bagian False Negative Rate. Jika model gagal dalam meminimalkan False Negative Rate (Type 1 error), artinya customer yang harusnya churn diprediksi oleh model sebagai customer tidak churn. Jika ini terjadi, maka perusahaan akan mengalami kehilangan customer sehingga mempengaruhi pendapatan perusahaan itu sendiri. Namun, saya juga harus memperhatikan angka False Positive (Type 2 error) pada hasil prediksi. Jika tinggi, berarti model salah memprediksi customer yang tidak churn. Ini akan menyebabkan biaya yang terbuang sia-sia karena customer yang padahal tidak akan churn namun diprediksi churn. Maka model yang saya cari adalah model yang memberikan prediksi akurat pada kelas positif dengan nilai recall setinggi mungkin untuk menghindari kehilangan customer berpotensi loyal diikuti dengan nilai precision yang juga harus sama tingginya untuk menghindari terbuangnya biaya yang dialokasikan. Maka saya harus menyeimbangkan antara precision dan recall dari 1 kelas positif. Maka metric yang akan saya gunakan adalah F1-Score.

# Modeling
Setelah melakukan beberapa percobaan dengan mencoba 5 algoritma untuk menemukan model terbaik. Saya menemukan XGBoost adalah model yang terbaik dengan skor:
- F1-Score training data : 0.700
- F1-Score test data : 0.720
- F1-Score setelah hyperparameter tuning : 0.757

# Recommendation for E-Commerce
1. Menggunakan jumlah total cashback yang sama tetapi alokasi yang berbeda, seperti menurunkan 4% Cashback pada jumlah customer tidak churn dan meningkatkan 20% Cashback pada jumlah customer Churn. Biayanya hampir sama dengan biaya pemasaran.
2. Membatasi jumlah device yang terhubung.
3. Memberikan penawaran alokasi 10% cashback pada customer churn dan 10% potongan ongkos kirim (total 20%) pada potensi customer churn yang memiliki jarak dari warehouse ke rumah customer yang jauh.
4.Berdasarkan tenure bahwa customer yang churn banyak terjadi di 0-2 bulan, maka dapat dilakukan survey pada customer baru di awal 1 bulan pemakaian agar alasan customer churn bisa diketahui lebih dalam, kenapa banyak churn di bulan-bulan pertama pemakaian platform.
5. Berdasarkan hari terakhir, banyak customer churn dihari 1-2 terakhir order dan orderannya adalah kebanyakan churn dari kategori mobile phone. Maka perbanyak kategori barang agar lebih menarik customer.
6. Berdasarkan complain, customer yang churn lebih banyak complain, maka tim customer service harus ekstra sabar dalam menghadapi complain dan membuat tim customer service dibagi menjadi 3 shift kerja agar dapat 24 jam melayani customer yang complain.

# Recommendation for Model
1. Menambahkan feature 'age' agar bisa diketahui alasan di balik churn paling banyak di umur berapa dan agar bisa diketahui apakah churn tersebut tipe voluntary atau involuntary. Involuntary churn adalah customer yang pindah dari platform berdasarkan faktor eksternal seperti berpindah lokasi, kematian, dll. Sedangkan voluntary churn adalah customer yang berpindah dari platform karena sengaja berhenti maupun sengaja beralih ke platform lain. Saya rasa feature age dapat menjadi feature yang cukup berpengaruh penting untuk ditambahkan dalam memprediksi churn
2. Menambahkan data dikelas 1 (churn) agar model dapat belajar dari banyak data.
3. Mencoba menggunakan algoritma machine learning lain yang belum dicoba, dan menerapkan langkah langkah seperti feature select by feature importances/coef
4. Mencoba menggunakan threshold
5. Mencoba metode oversampling lain seperti RandomOversampling
6. Mencoba untuk tidak drop semua outlier yang ada
