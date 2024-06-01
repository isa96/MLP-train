# Laporan Proyek Machine Learning On Production Part 3 - Izzan Silmi Aziz 

MLP Part 1 & 2 : [EDA](https://github.com/isa96/MLP)

Setelah menjelaskan problem statement dan melakukan EDA pada _part_ sebelumnya. Pada _part_ 3 ini akan menjelaskan tentang bagaimana membuat _training_ _code_, membuat file konfigurasi yang bertujuan untuk memilih model yang akan dipakai proses _training_ data, dan mengunggah model hasil _training_, metrik hasil test data ke platfrom _neptune.ai_.

## Modeling
### Training Data

<!-- ![Load Data](https://github.com/isa96/MLP-train/blob/main/assets/8.PNG "Load Data") -->

Gambar 1. Load Data.

Pertama disiapkan fungsi untuk load data train/test.

<!-- ![Parameter Model](https://github.com/isa96/MLP-train/blob/main/assets/9.PNG "Parameter Model") -->

Gambar 2. Konfigurasi Parameter Model.

Kedua disiapkan model apa saja yang dipilih untuk nantinya akan dilakukan proses _training_ dan beserta konfigurasi parameter model yang dipilih yang disimpan dalam bentuk file dengan ekstensi _yaml_.

<!-- ![Konversi Parameter](https://github.com/isa96/MLP-train/blob/main/assets/10.PNG "Konversi Parameter") -->

Gambar 3. Konfersi Parameter Model.

Lalu, disiapkan fungsi untuk konversi nilai parameter yang mana nantinya dibaca oleh model saat melakukan _training_ model.

Setelah semua fungsi file yang dibutuhkan telah selesai maka dibuat sebuah file _train.py_. Sebelum mengisi kode di file _train.py_ terlebih dahulu buat projek dan workspace terlebih dahulu di _neptune.ai_. Setelah membuat projek di _neptune.ai_, maka nanti akan muncul 2 data yang dibutuhkan untuk mengirim beberapa metadata hasil proses _training_. Dua data tersebut adalah nama project dan token api yang diberikan oleh _neptune.ai_. 

Selanjutnya isi file _train.py_ dengan pertama masukan _library_ yang dibutuhkan. Lalu, _load_ dua data yang didapatkan dari _neptune.ai_. Selanjutnya, buat variabel yang menginisialisasi pengiriman metadata ke _neptune.ai_. Berikutnya, _load_ data latih dan tes yang sudah di simpan sebelumnya. Siapkan variabel yang bertujuan untuk menyimpan konfigurasi parameter model yang sudah disiapkan dengan ekstensi _yaml_. Setelah itu, lakukan pemetaan terhadap model yang sudah dipilih dengan konfigurasi file _yaml_ yang ada sehingga masukan parameter model yang dipilih sesuai. Terakhir, dilakukan proses perulangan untuk melakukan proses _training_ model dan menyimpan metadata yang diperlukan ke _neptune.ai_. Jika proses _training_ dan penyimpanan sudah selesai maka hentikan proses pengiriman ke _neptune.ai_.

<!-- ![Metadata Neptune](https://github.com/isa96/MLP-train/blob/main/assets/11.PNG "Metadata Neptune") -->

Gambar 4. Hasil Penyimpanan Metadata di _Neptune.ai_.

Di Gambar 4 terlihat bahwa ada 4 folder yaitu models, monitoring, source-code, dan sys. Dimana isinya semua metadata yang sudah disimpan. Ini memudahkan untuk model _versioning_ dan bisa juga memonitoring hasil metrik dari proses _training_.

### Evalusasi Model

<!-- ![Evaluasi LR](https://github.com/isa96/MLP-train/blob/main/assets/12.PNG "Evaluasi LR") -->

Gambar 5. Hasil Evaluasi Data Dengan Model Logistic Regression.

<!-- ![Evaluasi SVM](https://github.com/isa96/MLP-train/blob/main/assets/13.PNG "Evaluasi SVM") -->

Gambar 6. Hasil Evaluasi Data Dengan Model Support Vector Machine.

Pada Gambar 5 & 6 merupakan contoh hasil metadata yang disimpan di _neptune.ai_ yaitu hasil _classification-report_ tiap model. Model yang digunakan juga memiliki hasil evaluasi yang bagus, terlihat dari hasil perhitungan metrik model seperti akurasi, presisi, _recall_, dan _f1-score_ yang mencapai 100%.


