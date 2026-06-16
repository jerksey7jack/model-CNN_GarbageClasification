# Garbage Classification Image Classifier

Proyek ini adalah model Machine Learning untuk mengklasifikasikan gambar sampah ke dalam 12 kelas berbeda guna mendukung pemilahan sampah otomatis. 

## Dataset
Dataset yang digunakan adalah "Garbage Classification - 12 Classes Enhanced" yang terdiri dari belasan ribu gambar dengan resolusi yang bervariasi. Dataset dibagi menjadi:
- 80% Training Set
- 10% Validation Set
- 10% Test Set
## link dataset: https://www.kaggle.com/datasets/huberthamelin/garbage-classification-labels-corrections?resource=download

## Arsitektur Model (Revisi Kriteria 4)
Model dibangun menggunakan metode **Transfer Learning** dengan *base model* **MobileNetV2**. Sesuai kriteria, model ini menggunakan arsitektur `Sequential` dengan penambahan layer eksplisit berupa:
- `Conv2D` dengan 512 filter.
- `MaxPooling2D`.
- Dilanjutkan dengan `GlobalAveragePooling2D`, `Dropout(0.5)`, dan `Dense` layer (Softmax).

Untuk memaksimalkan akurasi dan mencegah hilangnya informasi (*bottleneck*), dilakukan juga proses **Fine-Tuning** dengan membuka kunci (*unfreeze*) 20 layer terakhir pada base model dan menggunakan *learning rate* yang lebih kecil (0.0001).

## Performa
- Mengimplementasikan `Callback` untuk menghentikan pelatihan secara otomatis saat akurasi tinggi tercapai.
- Model berhasil mencapai akurasi yang ditargetkan pada tahap training dan testing.
- Model diekspor ke dalam tiga format: `SavedModel`, `TF-Lite`, dan `TFJS` agar siap di-deploy ke berbagai platform (Web, Mobile, dan Server).

## This directory includes a few sample datasets to get you started.

*   `california_housing_data*.csv` is California housing data from the 1990 US
    Census; more information is available at:
    https://docs.google.com/document/d/e/2PACX-1vRhYtsvc5eOR2FWNCwaBiKL6suIOrxJig8LcSBbmCbyYsayia_DvPOOBlXZ4CAlQ5nlDD8kTaIDRwrN/pub

*   `mnist_*.csv` is a small sample of the
    [MNIST database](https://en.wikipedia.org/wiki/MNIST_database), which is
    described at: http://yann.lecun.com/exdb/mnist/

*   `anscombe.json` contains a copy of
    [Anscombe's quartet](https://en.wikipedia.org/wiki/Anscombe%27s_quartet); it
    was originally described in

    Anscombe, F. J. (1973). 'Graphs in Statistical Analysis'. American
    Statistician. 27 (1): 17-21. JSTOR 2682899.

    and our copy was prepared by the
    [vega_datasets library](https://github.com/altair-viz/vega_datasets/blob/4f67bdaad10f45e3549984e17e1b3088c731503d/vega_datasets/_data/anscombe.json).
