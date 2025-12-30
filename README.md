# 🧠 Sistem Pendukung Keputusan Bonus Karyawan

Proyek ini merupakan implementasi **Fuzzy Logic** menggunakan **metode Tsukamoto dan Sugeno** untuk menentukan **besar bonus karyawan** berdasarkan beberapa kriteria penilaian yang bersifat tidak pasti (fuzzy).

Proyek ini cocok digunakan untuk:

* 📘 Tugas kuliah Fuzzy Logic
* 📊 Studi Metode Tsukamoto vs Sugeno
* 💻 Implementasi Python (Google Colab)

---

## 🎯 Tujuan Sistem

Menentukan **bonus karyawan (%)** secara objektif dan fleksibel berdasarkan:

* Kinerja
* Kehadiran
* Pengalaman kerja
* Beban kerja

Karena penilaian bersifat linguistik (tinggi, sedang, rendah), maka digunakan pendekatan **Fuzzy Inference System (FIS)**.

---

## 🔢 Variabel Fuzzy

### 🔹 Input

| Variabel    | Rentang      | Himpunan Fuzzy         |
| ----------- | ------------ | ---------------------- |
| Kinerja     | 0 – 100      | Rendah, Sedang, Tinggi |
| Kehadiran   | 0 – 100      | Buruk, Cukup, Baik     |
| Pengalaman  | 0 – 10 tahun | Baru, Menengah, Lama   |
| Beban Kerja | 0 – 100      | Ringan, Normal, Berat  |

### 🔹 Output

| Metode    | Output                                           |
| --------- | ------------------------------------------------ |
| Tsukamoto | Bonus (%) berdasarkan fungsi keanggotaan monoton |
| Sugeno    | Bonus (%) berupa konstanta atau fungsi linear    |

---

## 📜 Aturan Fuzzy (Rule Base)

### 🔸 Bentuk Linguistik (Umum)

1. IF kinerja tinggi AND kehadiran baik AND pengalaman lama THEN bonus besar
2. IF kinerja sedang AND kehadiran baik AND beban kerja berat THEN bonus besar
3. IF kinerja sedang AND kehadiran cukup THEN bonus sedang
4. IF kinerja rendah OR kehadiran buruk THEN bonus kecil
5. IF pengalaman baru AND kinerja tinggi THEN bonus sedang
6. IF beban kerja berat AND kinerja rendah THEN bonus kecil

---

## 🔧 Aturan Sugeno (Konsekuen Numerik)

Pada metode **Sugeno**, bagian THEN harus berupa **angka atau fungsi linear**, sehingga aturan diubah menjadi:

```text
R1: z1 = 10 + 0.10*Kinerja + 0.10*Kehadiran + 0.05*Pengalaman
R2: z2 = 8 + 0.05*Kinerja + 0.10*Kehadiran + 0.05*BebanKerja
R3: z3 = 6 + 0.05*Kinerja + 0.05*Kehadiran
R4: z4 = 5
R5: z5 = 5 + 0.10*Kinerja
R6: z6 = 4
```

📌 Angka di depan (10, 8, 6, dst) adalah **konstanta dasar (base bonus)** yang merepresentasikan kebijakan minimum bonus saat rule aktif.

---

## ⚙️ Metode Inferensi

### 🔹 Tsukamoto

* Output berupa himpunan fuzzy dengan fungsi keanggotaan **monoton**
* Setiap rule menghasilkan nilai crisp
* Defuzzifikasi menggunakan **rata-rata terbobot**

### 🔹 Sugeno

* Output berupa **fungsi linear atau konstanta**
* Defuzzifikasi menggunakan **weighted average**
* Cocok untuk optimasi dan sistem kontrol

---

## 🧪 Contoh Input

```text
Kinerja     = 78
Kehadiran   = 85
Pengalaman  = 4 tahun
Beban Kerja = 70
```

Hasil berupa nilai bonus (%) dari metode Tsukamoto dan Sugeno.

---

## 🧑‍💻 Teknologi

* Python 3
* NumPy
* Pandas
* Matplotlib
* Skfuzzy
* FloatSlider
* Google Colab

---

## 📁 Struktur Proyek

```text
.
├── TugasAkhir_FuzzyLogic_G.231.22.0104.ipynb   # Notebook utama (Colab)
├── README.md                                   # Dokumentasi proyek
```

---

## ✨ Penutup

Proyek ini diharapkan dapat membantu memahami:

* Perbedaan fundamental Tsukamoto dan Sugeno
* Cara merancang rule fuzzy yang konsisten
* Implementasi fuzzy logic secara praktis di Python

Silakan gunakan, kembangkan, dan sesuaikan proyek ini sesuai kebutuhan akademik 🚀

---

📬 Jika proyek ini bermanfaat, jangan ragu untuk ⭐ repository ini di GitHub.
