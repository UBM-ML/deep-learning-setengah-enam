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
- Train accuracy: 87.51%
- Validation accuracy: 86.72%
- Train time: 50.3s
- Apakah overfit/underfit? Goodfit.

**Observasi & Insight:**
> Akurasi tes kembali sedikit meningkat menjadi 86.15%, menunjukkan bahwa model mungkin masih mendapat manfaat dari kedalaman yang lebih besar. Waktu training relatif stabil dibandingkan Eksperimen #1.

**Rencana eksperimen berikutnya:**
> Terus menambah hidden layer hingga 4 atau 5 untuk melihat apakah ada titik jenuh atau penurunan kinerja.

---

### Eksperimen #3
**Apa yang diubah dari baseline:**
Hidden Layers=1, Neurons=128, Activation=tanh, Optimizer=adam, LR=0.001, Batch=32, Epochs=50, Dropout=0.3.

**Hipotesis sebelum run:**
Menggunakan Adam dan epoch yang lebih banyak (50) akan meningkatkan akurasi secara signifikan meskipun hanya 1 layer.

**Hasil:**
- Test accuracy: 88.05%
- Train accuracy: 91.12%
- Validation accuracy: 88.43%
- Train time: 363.8s
- Apakah overfit/underfit? overfit

**Observasi & Insight:**
Hasil terbaik sejauh ini, namun memakan waktu sangat lama.

**Rencana eksperimen berikutnya:**
> Coba kembali ke eksperimen 2 dengan hidden layer menjadi 5 untuk mengkonfirmasi tren ini, kemudian pertimbangkan perubahan hyperparameter lain.

---

### Eksperimen #4

**Apa yang diubah dari baseline:**
> Mengganti jumlah hidden layer dari 1 menjadi 5, sisanya tetap (Neurons=64, Activation=relu, Optimizer=sgd, LR=0.01, Batch=32, Epochs=10, Dropout=0.0).

**Hipotesis sebelum run:**
> Akurasi mungkin akan kembali meningkat, atau terus menurun jika model sudah terlalu kompleks.

**Hasil:**
- Test accuracy: 86.48%
- Train accuracy: 87.78%
- Validation accuracy: 85.92%
- Train time: 50.2s
- Apakah overfit/underfit? Goodfit.

**Observasi & Insight:**
> Akurasi tes menunjukkan sedikit peningkatan lagi menjadi 86.48%, menjadikannya yang tertinggi sejauh ini untuk variasi hidden layer. Ini menunjukkan bahwa dengan 5 hidden layer, model dapat mempelajari representasi yang lebih baik tanpa terlalu banyak dampak negatif pada waktu training.

**Rencana eksperimen berikutnya:**
> Berdasarkan hasil ini, 5 hidden layer tampaknya menjadi titik yang baik. Selanjutnya, eksplorasi dampak dari menggunakan tanh + adam dengan 1 layer dan 128 neuron serta learning 0.001.

---

### Eksperimen #5

**Apa yang diubah dari baseline:**
Hidden Layers=1, Neurons=128, Activation=tanh, Optimizer=adam, LR=0.001, Batch=32, Epochs=10, Dropout=0.3.

**Hipotesis sebelum run:**
Menguji apakah performa tinggi Adam di Exp #3 karena jumlah epochnya atau memang optimizernya.

**Hasil:**
- Test accuracy: 86.50%
- Train accuracy: 87.60%
- Validation accuracy: 87.03%
- Train time: 68.2s
- Apakah overfit/underfit? Goodfit

**Observasi & Insight:**
Dengan hanya 10 epoch, Adam + Tanh sudah mengalahkan 5 layer SGD.

**Rencana eksperimen berikutnya:**
> -

---

## 🏆 Konfigurasi Terbaik

Setelah semua eksperimen, salin konfigurasi terbaik kalian ke sini:

```python
HIDDEN_LAYERS     = 1
NEURONS_PER_LAYER = 128
ACTIVATION        = tanh
DROPOUT_RATE      = 0.3
OPTIMIZER         = adam
LEARNING_RATE     = 0.001
BATCH_SIZE        = 32
EPOCHS            = 50
```

**Test accuracy final: 88.05%**
