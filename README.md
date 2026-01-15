# Performance Evaluation of YOLOv11 for Road Pothole Detection Under Diverse Environmental Conditions

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/)

Repositori ini berisi implementasi kode dan laporan penelitian Tugas Akhir mengenai deteksi lubang jalan (pothole) menggunakan arsitektur YOLOv11, YOLOv10, dan RT-DETR.

## 📌 Abstrak

Lubang jalan merupakan salah satu bentuk kerusakan jalan yang paling sering ditemui dan diketahui menyebabkan kecelakaan lalu lintas serta meningkatkan biaya perawatan kendaraan. Penelitian ini mengevaluasi performa YOLOv11 sebagai model utama dan membandingkannya dengan YOLOv10 dan RT-DETR. 

Eksperimen dilakukan menggunakan dataset **Pothole Detection** yang berisi **4.231 gambar beranotasi** dengan berbagai variasi kondisi pencahayaan dan lingkungan. Semua model dilatih di lingkungan Google Colab menggunakan GPU NVIDIA Tesla T4 dengan pengaturan yang konsisten. Setiap arsitektur telah melalui proses optimasi hyperparameter secara sistematis untuk memastikan evaluasi yang adil.

## 🎯 Hasil Utama

YOLOv11 menunjukkan hasil paling optimal dengan mencapai:
- **Precision**: 0.83
- **Recall**: 0.71
- **mAP@0.5**: 0.76
- **mAP@0.5:0.95**: 0.37
- **Inference Time**: ~0.021 detik/gambar

Model ini memberikan keseimbangan terbaik antara akurasi dan kecepatan, melampaui performa YOLOv10 dan RT-DETR.

## 📊 Perbandingan Performa Model

Berikut adalah ringkasan performa ketiga model yang diuji pada test set:

| Model | Precision | Recall | mAP@0.5 | mAP@0.5:0.95 | Inference Time (s/img) |
|-------|-----------|--------|---------|--------------|------------------------|
| **YOLOv11s** | **0.8305** | **0.7098** | **0.7568** | **0.3656** | **0.0210** |
| YOLOv10s | 0.7923 | 0.6895 | 0.7387 | 0.3540 | 0.0215 |
| RT-DETR | 0.8096 | 0.6900 | 0.7045 | 0.3204 | 0.0528 |

**Kesimpulan**: YOLOv11 memberikan hasil yang paling tangguh (robust) untuk deteksi lubang jalan di berbagai kondisi lingkungan dengan keseimbangan akurasi dan kecepatan yang optimal.

## 📂 Struktur Repositori

```
├── TA_YOLOv11.ipynb      # Implementasi model YOLOv11 (model utama)
├── TA_YOLOv10.ipynb      # Implementasi model YOLOv10 (pembanding)
├── TA_RTDETR.ipynb       # Implementasi RT-DETR (pembanding)
├── 2025442701.pdf        # Paper lengkap penelitian
└── README.md             # File ini
```

### Penjelasan File:

- **`TA_YOLOv11.ipynb`**: Notebook utama yang berisi implementasi YOLOv11, termasuk proses baseline training, hyperparameter tuning, dan evaluasi akhir.
- **`TA_YOLOv10.ipynb`**: Notebook implementasi model YOLOv10 sebagai pembanding untuk menganalisis arsitektur yang lebih efisien dengan struktur tanpa NMS (Non-Maximum Suppression).
- **`TA_RTDETR.ipynb`**: Notebook implementasi RT-DETR (Real-Time Detection Transformer) untuk membandingkan pendekatan berbasis konvolusi (CNN) dengan arsitektur berbasis Transformer.
- **`2025442701.pdf`**: Laporan lengkap (Paper) yang berisi metodologi detail, tinjauan pustaka, hasil eksperimen, dan analisis mendalam.

## 🔬 Metodologi Penelitian

Penelitian ini mengikuti alur kerja sebagai berikut:

1. **Pengumpulan Data**: Dataset Pothole Detection dari Roboflow (4.231 gambar)
2. **Preprocessing**: Koreksi orientasi, resizing, normalisasi, dan augmentasi
3. **Pembagian Dataset**: 
   - Training: 71%
   - Validation: 16%
   - Testing: 13%
4. **Hyperparameter Tuning**: Optimasi parameter untuk setiap model
5. **Training**: Pelatihan model dengan GPU NVIDIA Tesla T4
6. **Evaluasi**: Pengukuran menggunakan Precision, Recall, mAP, dan Inference Time
7. **Analisis**: Perbandingan kuantitatif dan kualitatif hasil deteksi

## 🛠️ Cara Penggunaan

### Prasyarat
- Akun Google untuk menggunakan Google Colab
- Akun Roboflow untuk mengakses dataset
- Koneksi internet yang stabil

### Langkah-langkah:

1. **Buka Notebook di Google Colab**
   - Klik badge "Open In Colab" di bagian atas
   - Atau upload file `.ipynb` secara manual ke Google Colab

2. **Persiapan Dataset**
   - Buat akun di [Roboflow](https://roboflow.com/)
   - Akses dataset: [Pothole Detection](https://universe.roboflow.com/arthana-dbw2b/pothole-detection-th8es)
   - Dapatkan API Key dari akun Roboflow Anda

3. **Konfigurasi Notebook**
   - Ganti `API_KEY` pada bagian pengunduhan dataset dengan kunci API milik Anda
   - Pastikan menggunakan runtime GPU (T4 atau lebih tinggi) di Google Colab

4. **Jalankan Training**
   - Jalankan cell secara berurutan
   - Proses training akan memakan waktu beberapa jam tergantung konfigurasi

5. **Evaluasi Hasil**
   - Hasil evaluasi akan tersimpan dalam folder `runs/`
   - Visualisasi dan metrik dapat dilihat di akhir notebook

## 💡 Kontribusi Utama

1. **Implementasi dan Perbandingan**: Evaluasi komprehensif tiga arsitektur modern (YOLOv11, YOLOv10, RT-DETR) untuk deteksi lubang jalan
2. **Evaluasi Performa**: Penggunaan metrik Precision, Recall, mAP, dan Inference Time sebagai kriteria evaluasi inti
3. **Analisis Trade-off**: Analisis mendalam terhadap trade-off performa antara sistem deteksi berbasis konvolusi dan berbasis Transformer

## 🌟 Keunggulan YOLOv11

YOLOv11 menunjukkan performa superior karena:
- **Modul C3K2**: Meningkatkan ekstraksi fitur multi-skala
- **SPPF (Spatial Pyramid Pooling Fast)**: Memperbaiki kesadaran spasial
- **C2PSA (Cross Stage Partial Spatial Attention)**: Meningkatkan fusi fitur dan perhatian spasial
- **Konvergensi Cepat**: Mencapai stabilitas pelatihan lebih cepat
- **Generalisasi Kuat**: Performa konsisten di berbagai kondisi lingkungan

## ⚠️ Keterbatasan

1. Dataset terbatas dan kurang beragam dalam variasi cuaca dan pencahayaan
2. Belum diimplementasikan pada sistem real-time seperti kamera kendaraan
3. Eksperimen terbatas pada GPU Tesla T4 dengan kapasitas komputasi terbatas

## 🔮 Pengembangan Masa Depan

- Deployment pada skenario lapangan menggunakan kamera terpasang di kendaraan atau tepi jalan
- Ekspansi dataset dengan kondisi lingkungan yang lebih beragam
- Optimasi untuk perangkat edge computing dengan resource terbatas
- Integrasi dengan sistem monitoring jalan dan transportasi cerdas

## 📚 Referensi

Untuk referensi lengkap, silakan lihat bagian References dalam file `2025442701.pdf`.

Beberapa referensi utama:
- Khanam & Hussain (2024) - YOLOv11: An overview of the key architectural enhancements
- Lv et al. (2023) - DETRs Beat YOLOs on Real-time Object Detection
- Katsamenis et al. (2023) - Deep transformer networks for precise pothole segmentation tasks

## ✍️ Penulis

**Andito Rizkyka Rianto**  
Program Studi Informatika  
Fakultas Informatika  
Universitas Telkom  
📧 ditorizkyka@student.telkomuniversity.ac.id

**Pembimbing:**  
**Gamma Kosala, S.T., M.T.**  
School of Computing  
Telkom University  
📧 gammakosala@telkomuniversity.ac.id

---

## 📄 Lisensi

Penelitian ini dibuat sebagai syarat kelulusan Program Studi Informatika, Fakultas Informatika, Universitas Telkom.

## 🙏 Ucapan Terima Kasih

- Universitas Telkom atas dukungan fasilitas penelitian
- Roboflow atas penyediaan dataset Pothole Detection
- Google Colab atas akses gratis ke GPU untuk keperluan penelitian
- Komunitas Ultralytics atas framework YOLO yang powerful

---

**Catatan**: Untuk detail lengkap mengenai metodologi, hasil eksperimen, dan analisis, silakan rujuk paper lengkap di `2025442701.pdf`.

*Last Updated: Januari 2026*
