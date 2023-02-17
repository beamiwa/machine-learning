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

# Rekomendasi
- Berdasarkan Tenure, churn banyak terjadi di awal 0-2 bulan pemakaian platform, maka perusahaan dapat memberikan survey awal pemakaian platform di awal bulan 1 agar dapat ditelusuri lebih dalam penyebab churn kenapa.
- Berdasarkan Complain, customer yang churn lebih banyak complain, maka tim customer service harus ekstra sabar dalam menghadapi complain dan membuat tim customer service dibagi menjadi 3 shift kerja agar dapat 24 jam melayani customer yang complain.
- Berdasarkan DaySinceLastOrder, banyak customer churn dihari 1-2 terakhir order dan orderannya adalah kebanyakan churn dari kategori mobile phone. Maka perbanyak kategori barang agar lebih menarik customer.
