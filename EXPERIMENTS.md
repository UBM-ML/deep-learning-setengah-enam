# Experiment Log

Catat setiap percobaan hyperparameter di sini. **Minimal 5 eksperimen.**

> Tips: ubah **satu hyperparameter pada satu waktu** agar bisa mengisolasi efeknya. Setelah memahami efek tiap variabel, baru gabungkan untuk hasil terbaik.

---

## 📋 Tabel Ringkasan

Isi tabel ini setelah selesai semua eksperimen.

| # | Hidden | Neurons | Activation | Optimizer | LR     | Batch | Epochs | Dropout | Test Acc | Train Time |
|---|--------|---------|------------|-----------|--------|-------|--------|---------|----------|------------|
| 0 | 1      | 64      | relu       | sgd       | 0.01   | 32    | 10     | 0.0     | ~85%     | ~30s       |
| 1 | 2       |  64       |  relu          | sgd          | 0.01       | 32   |     10       | 0.0       |  85.57%       |     47.8s     |
| 2 |   3     |     64    |     relu       |     sgd      |   0.01     |   32    |    10    |     0.0    |   86.15%       |    50.3s        |
| 3 |   1     |    128     |       tanh     |   adam        |0.001        |    32   |   50     |      0.3   |   88.05%       |     363.8s       |
| 4 |   5     |     64    |        relu    |    sgd       |   0.01     |    32   |    10    |    0.0     |     86.48%     |     50.2s       |
| 5 |    1    |     128    |      tanh      |     adam      |     0.001   |   32    |    10    |    0.3     |    86.50%      |   68.2s         |

> **Eksperimen #0** = baseline (jangan ubah, ini patokan kalian).

---

## 🧪 Detail Setiap Eksperimen

Gunakan template di bawah untuk SETIAP eksperimen.

---

### Eksperimen #1

**Apa yang diubah dari baseline:**
> Mengganti jumlah hidden layer dari 1 menjadi 2, sisanya tetap (Neurons=64, Activation=relu, Optimizer=sgd, LR=0.01, Batch=32, Epochs=10, Dropout=0.0).

**Hipotesis sebelum run:**
> Menambah jumlah hidden layer diharapkan dapat meningkatkan kapasitas model untuk mempelajari pola yang lebih kompleks, sehingga akurasi bisa sedikit meningkat atau tetap stabil.

**Hasil:**
- Test accuracy: 85.57%
- Train accuracy: 86.59%
- Validation accuracy: 86.02%
- Train time: ~47.8s
- Apakah overfit/underfit? Goodfit.

**Observasi & Insight:**
> Peningkatan satu hidden layer menghasilkan sedikit peningkatan pada akurasi tes (dari ~85% menjadi 85.57%), namun waktu training meningkat secara signifikan.

**Rencana eksperimen berikutnya:**
> Lanjutkan eksplorasi dengan menambah jumlah hidden layer untuk melihat apakah ada pola peningkatan akurasi yang konsisten.

---

### Eksperimen #2

**Apa yang diubah dari baseline:**
> Mengganti jumlah hidden layer dari 1 menjadi 3, sisanya tetap (Neurons=64, Activation=relu, Optimizer=sgd, LR=0.01, Batch=32, Epochs=10, Dropout=0.0).

**Hipotesis sebelum run:**
> Dengan penambahan hidden layer lagi, akurasi tes mungkin akan terus meningkat atau mencapai puncaknya, sambil mengamati dampak pada waktu training.

**Hasil:**
- Test accuracy: 86.15%
- Train accuracy: ___%
- Validation accuracy: ___%
- Train time: 50.3s
- Apakah overfit/underfit? Tidak dapat ditentukan hanya dari Test Accuracy.

**Observasi & Insight:**
> Akurasi tes kembali sedikit meningkat menjadi 86.15%, menunjukkan bahwa model mungkin masih mendapat manfaat dari kedalaman yang lebih besar. Waktu training relatif stabil dibandingkan Eksperimen #1.

**Rencana eksperimen berikutnya:**
> Terus menambah hidden layer hingga 4 atau 5 untuk melihat apakah ada titik jenuh atau penurunan kinerja.

---

### Eksperimen #3

**Apa yang diubah dari baseline:**
> Mengganti jumlah hidden layer dari 1 menjadi 4, sisanya tetap (Neurons=64, Activation=relu, Optimizer=sgd, LR=0.01, Batch=32, Epochs=10, Dropout=0.0).

**Hipotesis sebelum run:**
> Akurasi bisa terus meningkat, namun ada risiko overfitting atau diminishing returns jika model terlalu dalam untuk dataset ini.

**Hasil:**
- Test accuracy: 85.56%
- Train accuracy: ___%
- Validation accuracy: ___%
- Train time: 49.4s
- Apakah overfit/underfit? Tidak dapat ditentukan hanya dari Test Accuracy.

**Observasi & Insight:**
> Akurasi tes sedikit menurun dari Eksperimen #2 (86.15% menjadi 85.56%), yang mungkin mengindikasikan bahwa 3 hidden layer mungkin sudah optimal atau mendekati optimal untuk konfigurasi ini, atau terjadi overfitting ringan yang tidak terlihat dari data tabel ini.

**Rencana eksperimen berikutnya:**
> Coba satu penambahan hidden layer lagi (menjadi 5) untuk mengkonfirmasi tren ini, kemudian pertimbangkan perubahan hyperparameter lain.

---

### Eksperimen #4

**Apa yang diubah dari baseline:**
> Mengganti jumlah hidden layer dari 1 menjadi 5, sisanya tetap (Neurons=64, Activation=relu, Optimizer=sgd, LR=0.01, Batch=32, Epochs=10, Dropout=0.0).

**Hipotesis sebelum run:**
> Akurasi mungkin akan kembali meningkat, atau terus menurun jika model sudah terlalu kompleks.

**Hasil:**
- Test accuracy: 86.48%
- Train accuracy: ___%
- Validation accuracy: ___%
- Train time: 50.2s
- Apakah overfit/underfit? Tidak dapat ditentukan hanya dari Test Accuracy.

**Observasi & Insight:**
> Akurasi tes menunjukkan sedikit peningkatan lagi menjadi 86.48%, menjadikannya yang tertinggi sejauh ini untuk variasi hidden layer. Ini menunjukkan bahwa dengan 5 hidden layer, model dapat mempelajari representasi yang lebih baik tanpa terlalu banyak dampak negatif pada waktu training.

**Rencana eksperimen berikutnya:**
> Berdasarkan hasil ini, 5 hidden layer tampaknya menjadi titik yang baik. Selanjutnya, eksplorasi dampak dari jumlah neuron per layer.

---

### Eksperimen #5

**Apa yang diubah dari baseline:**
> Mengganti jumlah neuron per layer dari 64 menjadi 32, sisanya tetap (Hidden=1, Activation=relu, Optimizer=sgd, LR=0.01, Batch=32, Epochs=10, Dropout=0.0).

**Hipotesis sebelum run:**
> Mengurangi jumlah neuron per layer akan mengurangi kapasitas model. Akurasi tes kemungkinan akan menurun, dan waktu training juga akan lebih cepat.

**Hasil:**
- Test accuracy: 84.90%
- Train accuracy: ___%
- Validation accuracy: ___%
- Train time: 38.6s
- Apakah overfit/underfit? Tidak dapat ditentukan hanya dari Test Accuracy.

**Observasi & Insight:**
> Akurasi tes menurun dibandingkan baseline (84.90% vs ~85%), mengkonfirmasi hipotesis bahwa mengurangi neuron per layer menurunkan kapasitas model. Waktu training juga lebih cepat.

**Rencana eksperimen berikutnya:**
> Eksplorasi dengan menambah jumlah neuron per layer (misal 128 atau 256) untuk melihat apakah ada peningkatan akurasi.

---

## 🏆 Konfigurasi Terbaik

Setelah semua eksperimen, salin konfigurasi terbaik kalian ke sini:

```python
HIDDEN_LAYERS     = ?
NEURONS_PER_LAYER = ?
ACTIVATION        = ?
DROPOUT_RATE      = ?
OPTIMIZER         = ?
LEARNING_RATE     = ?
BATCH_SIZE        = ?
EPOCHS            = ?
```

**Test accuracy final: ___%**
