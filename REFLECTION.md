# Refleksi Tim

> Jawaban dalam Bahasa Indonesia. Maksimal 1 halaman (~500 kata). Yang dinilai adalah **kedalaman pemahaman**, bukan panjang tulisan.

---

## 1. Parameter vs Hyperparameter

Berdasarkan eksperimen yang kalian lakukan, jelaskan dengan **kata-kata kalian sendiri**:
- Apa yang termasuk **parameter** dalam model kalian, dan apa yang termasuk **hyperparameter**?
- Manakah yang berubah saat training berjalan, dan manakah yang ditentukan oleh kalian sebelum training?

**Jawaban:**
> Dalam eksperimen kami, parameter adalah nilai yang dipelajari langsung oleh model selama proses training, seperti bobot (weights) dan bias pada setiap neuron. Nilai ini awalnya diinisialisasi secara acak, lalu terus diperbarui menggunakan algoritma optimasi berdasarkan error yang dihasilkan model. Semakin banyak iterasi training dilakukan, semakin berubah pula nilai parameter agar prediksi model mendekati target sebenarnya.

> Sedangkan hyperparameter adalah konfigurasi yang ditentukan sebelum training dimulai dan tidak dipelajari otomatis oleh model. Contohnya seperti learning rate, batch size, jumlah epoch, jumlah layer, jumlah neuron, dan optimizer yang digunakan. Hyperparameter dipilih oleh kami sebagai pengembang karena nilainya sangat memengaruhi proses pembelajaran model.

> Jadi, parameter berubah selama training berjalan melalui proses back propagation, sedangkan hyperparameter ditentukan di awal sebagai pengaturan cara model belajar.

---

## 2. Hyperparameter dengan Dampak Terbesar

Dari semua hyperparameter yang kalian eksperimen, mana yang menurut kalian memberikan **dampak paling besar** terhadap akurasi? Mengapa demikian — apa yang kalian amati pada kurva loss/accuracy?

**Jawaban:**
>Hyperparameter yang menurut kami paling berpengaruh terhadap akurasi adalah learning rate. Saat menggunakan learning rate yang terlalu kecil, penurunan loss berjalan sangat lambat sehingga model membutuhkan epoch lebih banyak untuk mencapai akurasi yang baik. Sebaliknya, ketika learning rate terlalu besar, kurva loss menjadi tidak stabil dan kadang naik turun drastis.

>Dari hasil eksperimen, kami melihat bahwa learning rate yang optimal membuat kurva loss turun secara konsisten dan kurva accuracy meningkat lebih stabil. Pada learning rate yang tidak sesuai, model cenderung gagal mencapai titik minimum karena langkah pembaruan bobot terlalu besar sehingga melewati solusi optimal.

---

## 3. Learning Rate

Coba set `LEARNING_RATE = 1.0` (atau bahkan lebih besar) dan jalankan sekali. Apa yang terjadi pada kurva loss? Hubungkan jawaban kalian dengan rumus:

$$W_j = W_j - \lambda \frac{\partial F(W_j)}{\partial W_j}$$

**Jawaban:**
>Saat kami mencoba `LEARNING_RATE = 1.0`, kurva loss menjadi sangat tidak stabil bahkan cenderung meningkat. Pada beberapa percobaan, model gagal konvergen dan akurasi tidak berkembang secara signifikan.

>Hal ini sesuai dengan rumus:
>$$W_j = W_j - \lambda \frac{\partial F(W_j)}{\partial W_j}$$


>Nilai λ (learning rate) menentukan seberapa besar perubahan bobot setiap iterasi. Ketika learning rate terlalu besar, perubahan bobot menjadi terlalu ekstrem sehingga model “melompat-lompat” melewati titik minimum loss. Akibatnya proses optimasi menjadi tidak stabil dan loss sulit turun.

---

## 4. Batch Size & Trade-off

Bandingkan eksperimen dengan **batch size kecil** (misal 16) vs **batch size besar** (misal 256). Apa yang kalian amati dari sisi:
- Waktu training?
- Stabilitas kurva loss?
- Akurasi akhir?

Apakah pengamatan ini sesuai dengan teori di slide kuliah?

**Jawaban:**
>Pada batch size kecil seperti 16, training berlangsung lebih lambat karena jumlah iterasi per epoch lebih banyak. Namun kurva loss terlihat lebih dinamis dan model kadang menghasilkan generalisasi yang lebih baik. Sebaliknya, batch size besar seperti 256 membuat training lebih cepat karena pemrosesan dilakukan lebih efisien dalam sekali komputasi, tetapi kurva loss menjadi lebih halus dan kadang model sedikit lebih sulit mencapai akurasi tertinggi.

>Dari sisi stabilitas, batch size besar memang menghasilkan kurva yang lebih stabil karena gradien dihitung dari data lebih banyak. Sedangkan batch size kecil menghasilkan gradien yang lebih “berisik”. Hasil pengamatan ini sesuai dengan teori pada kuliah bahwa batch kecil memberi generalisasi lebih baik tetapi membutuhkan waktu training lebih lama.

---

## 5. Feed Forward & Back Propagation

Pada saat kalian menekan `model.fit(...)`, sebenarnya proses feed forward dan back propagation berjalan **ribuan kali**. Hitung kira-kira berapa kali back propagation terjadi pada salah satu eksperimen kalian.

> Petunjuk: `(jumlah_sample_training / batch_size) × epochs`

Jelaskan apa yang terjadi pada **bobot** dan **bias** model kalian di antara iterasi pertama dan terakhir.

**Jawaban:**
>Misalnya pada eksperimen dengan 48.000 data training, batch size 32, dan 10 epoch:

>[
>(48000 / 32) \times 10 = 15000
>]

>Artinya proses back propagation terjadi sekitar 15.000 kali.

>Pada iterasi awal, bobot dan bias model masih acak sehingga prediksi model banyak salah. Setelah ribuan iterasi feed forward dan back propagation, bobot serta bias terus disesuaikan untuk memperkecil error. Di iterasi akhir, nilai parameter menjadi lebih optimal sehingga model mampu mengenali pola data Fashion-MNIST dengan akurasi lebih tinggi.

---

## 6. Kapan Deep Learning Tepat Digunakan?

Berdasarkan pengalaman kalian dengan Fashion-MNIST, menurut kalian apakah masalah ini *benar-benar* membutuhkan deep learning, atau bisa diselesaikan dengan machine learning klasik (misal Logistic Regression atau Random Forest)? Beri argumen.

**Jawaban:**
>Menurut kami, Fashion-MNIST sebenarnya masih bisa diselesaikan menggunakan machine learning klasik seperti Logistic Regression atau Random Forest karena ukuran gambar relatif kecil dan kompleksitas objek tidak terlalu tinggi. Bahkan beberapa algoritma klasik dapat mencapai akurasi cukup baik.

>Namun deep learning memiliki keunggulan dalam mempelajari fitur otomatis langsung dari data gambar tanpa perlu ekstraksi fitur manual. Untuk dataset yang lebih kompleks, jumlah data besar, atau variasi objek tinggi, deep learning menjadi jauh lebih efektif dibanding metode klasik. Jadi pada kasus Fashion-MNIST, deep learning belum sepenuhnya wajib, tetapi tetap relevan sebagai latihan memahami proses pembelajaran jaringan saraf.

---

## 7. Refleksi Tim

- Tantangan apa yang paling sulit?
- Apa pelajaran terpenting yang kalian dapat dari aktivitas ini?
- Jika diberi waktu lebih, apa yang ingin kalian coba lagi?

**Jawaban:**
>Tantangan paling sulit adalah memahami hubungan antara hyperparameter dengan perilaku model selama training. Awalnya kami hanya melihat angka akurasi, tetapi setelah beberapa eksperimen kami mulai memahami bahwa perubahan kecil pada learning rate atau batch size dapat memengaruhi stabilitas training secara signifikan.

>Pelajaran terpenting yang kami dapat adalah bahwa deep learning bukan sekadar menjalankan kode, tetapi memahami bagaimana model belajar dari data melalui proses optimasi parameter secara bertahap.

>Jika diberi waktu lebih, kami ingin mencoba arsitektur model yang lebih kompleks seperti CNN dan membandingkan performanya dengan model sederhana yang kami gunakan sekarang. Selain itu kami juga ingin mencoba teknik regularisasi dan data augmentation untuk melihat pengaruhnya terhadap overfitting.
