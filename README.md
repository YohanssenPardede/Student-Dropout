# Proyek Akhir: Menyelesaikan Permasalahan Jaya Jaya Institut

## Business Understanding
Jaya Jaya Institut merupakan institusi pendidikan tinggi yang telah berdiri sejak tahun 2000. Institusi ini telah mencetak banyak lulusan berprestasi dan memiliki reputasi yang sangat baik di kalangan akademisi dan industri. Namun, Jaya Jaya Institut menghadapi tantangan serius yaitu tingginya angka dropout di kalangan mahasiswanya. Hal ini tidak hanya berdampak pada reputasi, tetapi juga pada aspek finansial dan akreditasi institusi.

### Permasalahan Bisnis
Proyek ini bertujuan untuk menyelesaikan permasalahan bisnis utama berikut:
* Angka dropout mahasiswa yang tinggi.
* Sulitnya mengidentifikasi mahasiswa yang berisiko drop out secara dini.
* Minimnya dashboard monitoring performa mahasiswa untuk tim akademik dan manajemen.

### Cakupan Proyek
Proyek ini mencakup langkah-langkah berikut:
* Eksplorasi dan analisis data mahasiswa (demografis, sosial-ekonomi, performa semester 1 & 2).
* Pembuatan model klasifikasi untuk memprediksi risiko dropout mahasiswa.
* Penyusunan dashboard bisnis untuk memonitor performa mahasiswa dan visualisasi faktor dropout mahasiswa.
* Rekomendasi action items berdasarkan hasil analisis dan model.

### Persiapan
**Sumber data**: [GitHub](https://github.com/dicodingacademy/dicoding_dataset/blob/main/students_performance/data.csv)

**Setup environment**:
```bash
# Install dependensi
pip install -r requirements.txt
```

## Business Dashboard
Business dashboard ini dirancang untuk membantu Jaya Jaya Institut mengidentifikasi mahasiswa berisiko dropout lebih awal, memantau kinerja akademik mahasiswa, serta mengarahkan kebijakan berbasis data yang efektif. Anda dapat mengakses dashboard yang telah dibuat dengan memasukkan *username* dan *password* berikut:
```bash
username: root@mail.com
password: root123
```

Adapun fitur-fitur pada dashboard sebagai berikut:
1. **Jumlah Mahasiswa Aktif / Lulus / Keluar**
   * **Tujuan:** Menyajikan snapshot jumlah total mahasiswa dalam tiga kategori utama.
   * **Hasil:**
     * Aktif: 794
     * Lulus: 2.209
     * Keluar (Dropout): 1.421

2. **Persentase Dropout (Gauge)**
   * **Tujuan:** Menunjukkan proporsi mahasiswa yang sudah berhenti studi.
   * **Hasil:** 32,12% tingkat dropout pada Jaya Jaya Institut

3. **Potensi Dropout (Gauge + Jumlah)**
   * **Tujuan:** Visualisasi output model prediksi untuk tindakan pencegahan.
   * **Hasil:**
     * Potensi: 53,53%
     * Jumlah terdeteksi berisiko: 425 mahasiswa

4. **Distribusi Gender (Donut Chart)**
   * **Tujuan:** Mengidentifikasi perbedaan jumlah dan proporsi laki‑laki vs perempuan.
   * **Hasil:**
     * Perempuan: 61,3%
     * Laki‑laki: 38,7%

5. **Status Beasiswa (Donut Chart)**
   * **Tujuan:** Menilai berapa banyak mahasiswa yang menerima beasiswa.
   * **Hasil:**
     * Penerima beasiswa: 16,4%
     * Bukan penerima: 83,6%

6. **Kebutuhan Khusus (Donut Chart)**
   * **Tujuan:** Mengecek proporsi mahasiswa dengan special needs untuk layanan dukungan.
   * **Hasil:**
     * Ya: 1,39%
     * Tidak: 98,61%

7. **Distribusi Jurusan (Bar Chart)**
   * **Tujuan:** Mengetahui persebaran mahasiswa per jurusan.
   * **Hasil:** Jurusan manajemen merupakan jurusan dengan mahasiswa terbanyak mencapai 162 orang.

8. **Tingkat Kelulusan Mata Kuliah per Semester (Clustered Bar)**
   * **Tujuan:** Membandingkan rata‑rata jumlah mata kuliah yang diambil vs yang lulus di semester 1 & 2.
   * **Hasil:**
     * Semester 1: Diambil ≈ 6 matkul, Lulus ≈ 4 matkul
     * Semester 2: Diambil ≈ 6 matkul, Lulus ≈ 4 matkul

9. **Distribusi “Lulus” per Jumlah Mata Kuliah (Histogram Dropout vs Graduate)**
    * **Tujuan:** Melihat pola jumlah matkul lulus yang membedakan mahasiswa lulus dan dropout.
    * **Hasil:**
   Semester 1
        * Graduate mayoritas lulus 5–10 matkul (>1.800 orang)
        * Dropout mayoritas lulus 0–4 matkul (>1.000 orang)
    Semester 2
        * Graduate mayoritas lulus 5–10 matkul (>1.800 orang)
        * Dropout mayoritas lulus 0–4 matkul (>1.100 orang)

10. **Distribusi “Diambil” Semester 2 per Jumlah Mata Kuliah (Histogram)**
    * **Tujuan:** Mengobservasi beban sks yang diambil mahasiswa lulus vs dropout.
    * **Hasil:**
      * Graduate ≈ 2.000 orang mengambil 5–10 matkul
      * Dropout ≈ 1.200 orang mengambil 5–10 matkul

11. **Status Pembayaran UKT (Bar Chart Dropout vs Graduate)**
    * **Tujuan:** Memeriksa hubungan kepatuhan UKT dengan outcome studi.
    * **Hasil:** Hanya sedikit mahasiswa yang lulus tidak patuh/terlambat membayar UKT.

12. **Tunggakan Mahasiswa (Bar Chart Dropout vs Graduate)**
    * **Tujuan:** Mengukur risiko finansial (debtor) terhadap dropout.
    * **Hasil:** Hanya sedikit mahasiswa yang lulus yang memiliki masalah finansial.

## Menjalankan Sistem Machine Learning
### Sistem Pembuatan Model (notebook.ipynb)
Sistem *machine learning* yang diimplementasikan dalam notebook ini bertujuan untuk membuat model **prediksi dropout mahasiswa**, yaitu kemungkinan seorang mahasiswa untuk keluar/dropout dari institut. Algoritma yang digunakan adalah **XGBoost (Extreme Gradient Boosting)**, XGBoost adalah salah satu algoritma machine learning berbasis ensemble yang sangat populer dan kuat, terutama untuk tugas klasifikasi dan regresi. XGBoost bekerja berdasarkan teknik gradient boosting, yaitu membangun model secara bertahap menggunakan pohon keputusan (decision trees). Sebelum Anda menjalankan notebook, Anda perlu menyiapkan beberapa hal sebagai berikut:
1. **Virtual Environment:**
   Membuat *virtual environment* akan mengisolasi dependensi proyek dan mencegah konflik dengan *package* sistem.
   **Menggunakan `venv` (bawaan Python):**
   ```bash
   # Membuat virtual environment 
   python3 -m venv venv
   # Mengaktifkan virtual environment (Linux/macOS)
   source venv/bin/activate
   # Mengaktifkan virtual environment (Windows)
   venv\Scripts\activate
   ```
   **Menggunakan `conda` (jika Anda menggunakan Anaconda):**
   ```bash
   # Membuat conda environment (misalnya, bernama "myenv")
   conda create -n myenv python=3.8  # Ganti 3.8 jika perlu
   conda activate myenv
   ```

2. **Instal Dependensi:**
   Instal *library* Python yang diperlukan menggunakan `pip` dan file `requirements.txt` .
   ```bash
   pip install -r requirements.txt  # Jika ada requirements.txt
   ```

3. **Menjalankan Notebook:**
   Anda dapat menjalankan notebook menggunakan Jupyter Notebook atau JupyterLab.
   **Jupyter Notebook:**
   ```bash
   jupyter notebook notebook.ipynb
   ```
   **JupyterLab:**
   ```bash
   jupyter lab notebook.ipynb
   ```
Alur kerja model:
1. **Persiapan**: Impor library, unduh data mahasiswa, dan baca ke dalam DataFrame.
Pemahaman Data: Periksa informasi data, statistik deskriptif, duplikat, missing value, visualisasikan distribusi status mahasiswa (Graduate/Dropout/Enrolled) dan fitur numerik, serta analisis korelasi fitur.
2. **Pra-pemrosesan Data**: Saring data untuk status 'Graduate' dan 'Dropout', konversi status ke biner, pisahkan fitur dan target, skala fitur numerik, bagi data menjadi latih dan uji, dan tangani class imbalance pada data latih dengan SMOTE.
3. **Pemodelan**: Latih model klasifikasi XGBoost, termasuk hyperparameter tuning menggunakan cross-validation untuk menemukan model terbaik.
4. **Evaluasi**: Evaluasi model terbaik pada data uji menggunakan metrik seperti ROC AUC, Classification Report, dan Confusion Matrix untuk menilai performanya.
5. **Analisis Fitur & Pemilihan Fitur**: Identifikasi fitur terpenting untuk prediksi dropout, pilih 5 fitur teratas, dan latih ulang model dengan hanya menggunakan 5 fitur tersebut. Bandingkan performa model dengan semua fitur dan 5 fitur.
6. **Prediksi pada Data Baru**: Gunakan model yang dilatih dengan 5 fitur untuk memprediksi probabilitas dan mengidentifikasi mahasiswa dengan status 'Enrolled' yang berpotensi dropout.
Penyimpanan Model: Simpan model terbaik dan daftar fitur yang digunakannya ke file untuk penggunaan di masa depan.

### Sistem Prediksi (app.py)
Sistem ini adalah **aplikasi web interaktif berbasis Streamlit** untuk memprediksi **risiko dropout mahasiswa** berdasarkan lima parameter utama akademik dan finansial dengan memanfaatkan model machine learning XGBoost yang sudah dilatih dan disimpan. Sistem prediksi dijalankan melalui Streamlit, berikut cara menjalankannya:

```bash
# Jalankan aplikasi Streamlit
streamlit run app.py
```

Anda juga dapat mengakses sistem ini melalui link berikut: https://jip6mqbr5jjgaup9jxwlph.streamlit.app/

###  **Alur Kerja Sistem**
1. **Memuat model**: Model prediksi yang telah dilatih dimuat dari file `model.pkl`.
2. **Tampilan antarmuka pengguna**: User mengisi data input berupa:
   * Jumlah mata kuliah lulus semester 1 dan 2
   * Status pembayaran
   * Status tunggakan biaya
   * Jumlah mata kuliah yang diambil semester 2
3. **Prediksi dilakukan**: Input pengguna diubah menjadi array numerik dan diberikan ke model untuk menghitung **probabilitas dropout**.
4. **Output ditampilkan**: Sistem menunjukkan persentase risiko dropout, visualisasi progress bar, dan rekomendasi tindakan (peringatan atau pujian).

## Conclusion
Proyek ini berhasil merespons tantangan utama yang dihadapi Jaya Jaya Institut, yaitu tingginya angka dropout mahasiswa, dengan pendekatan berbasis data dan machine learning. Dengan membangun model prediksi dropout menggunakan algoritma XGBoost, institusi kini dapat mengidentifikasi mahasiswa berisiko secara dini, terutama dengan hanya lima indikator utama akademik dan finansial mahasiswa. Business dashboard yang dikembangkan mempermudah tim akademik dan manajemen memantau performa mahasiswa secara menyeluruh, mengamati pola dropout, dan mengambil keputusan berbasis data. Dengan akurasi model yang baik (ROC AUC: 96,8%) dan visualisasi yang informatif, proyek ini memberikan kemudahan bagi perbaikan sistem akademik dan kebijakan pencegahan dropout di masa depan.

### Rekomendasi Action Items
Berikut adalah beberapa rekomendasi action item yang dapat dilakukan Jaya Jaya Institut guna mengatasi tingginya tingkat dropout mahasiswa:
* **Remedial dan mentoring**: Identifikasi mahasiswa dengan potensi kelulusan rendah, lalu adakan sesi mentoring intensif bagi mereka.
* **Skema pembayaran UKT yang fleksibel**: Tawarkan opsi cicilan dan dana darurat untuk meningkatkan pembayaran UKT tepat waktu.
* **Bimbingan akademik**: Konsultasi beban mata kuliah tiap akhir semester kepada dosen pembimbing untuk menghindari overload SKS/mata kuliah.
* **Peer Mentoring**: Program bimbingan dari teman sebaya untuk meningkatkan pemahaman belajar.
