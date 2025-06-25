# UAS Sistem Multimedia

Repository ini berisi implementasi berbagai teknik pemrosesan multimedia termasuk kompresi JPEG, analisis audio, dan watermarking digital untuk mata kuliah Sistem Multimedia.

## Struktur Proyek

```
UAS-Sistem-Multimedia/
├── problem1.ipynb                           # Implementasi Kompresi JPEG
├── problem3.ipynb                           # Analisis Kompresi Audio MP3
├── problem4.ipynb                           # Watermarking Audio Digital
├── 33.wav                                   # File audio input untuk analisis
├── audio_kompresi.mp3                       # Hasil kompresi MP3
├── hasil_analisis_kompresi.png              # Visualisasi perbandingan audio
├── sinyal_asli.wav                          # Output watermarking: sinyal asli
├── sinyal_watermarked_bobot_0.015.wav       # Output watermarking: bobot tinggi
├── sinyal_watermarked_bobot_0.003.wav       # Output watermarking: bobot rendah
├── img/
│   └── 1.jpeg                               # File gambar untuk kompresi JPEG
└── README.md                                # Dokumentasi ini
```

## Problem 1: Kompresi JPEG ([problem1.ipynb](problem1.ipynb))

### Deskripsi
Implementasi lengkap algoritma kompresi JPEG dari scratch, mencakup semua tahap dari transformasi DCT hingga proses decoding dengan analisis kualitas.

### Fitur Utama
- **Transformasi DCT 2D**: Konversi domain spasial ke domain frekuensi
- **Kuantisasi**: Implementasi tabel kuantisasi standar JPEG
- **Zigzag Scanning**: Pengurutan koefisien DCT untuk optimasi kompresi
- **Run-Length Encoding (RLE)**: Kompresi data dengan encoding panjang run
- **Simulasi Huffman Coding**: Persiapan data untuk kompresi entropy
- **Proses Decoding**: Rekonstruksi gambar dari data terkompresi
- **Analisis Kualitas**: Perhitungan Mean Square Error (MSE)
- **Visualisasi**: Perbandingan blok asli vs rekonstruksi

### Dependencies
```bash
pip install numpy matplotlib pillow
```

### Input yang Diperlukan
- File gambar: `img/1.jpeg`

### Output
- Visualisasi tahapan kompresi JPEG
- Matriks DCT dan hasil kuantisasi
- Data RLE dan simulasi bitstream
- Perbandingan blok asli vs rekonstruksi
- Perhitungan MSE sebagai metrik kualitas

---

## Problem 3: Analisis Kompresi Audio MP3 ([problem3.ipynb](problem3.ipynb))

### Deskripsi
Analisis komprehensif perbandingan karakteristik audio format WAV (lossless) vs MP3 (lossy) dengan visualisasi domain waktu dan frekuensi.

### Fitur Utama
- **Kompresi Audio**: Konversi WAV ke MP3 dengan bitrate 128k
- **Analisis Ukuran**: Perhitungan rasio kompresi dan penghematan storage
- **Visualisasi Waveform**: Perbandingan bentuk gelombang audio
- **Analisis Spektrum FFT**: Transformasi Fourier untuk analisis frekuensi
- **Multi-scale Visualization**: Plot linear dan logaritmik untuk spektrum
- **Deteksi Cutoff Frekuensi**: Identifikasi batas frekuensi yang dihilangkan MP3

### Dependencies
```bash
pip install numpy matplotlib scipy pydub
```

### System Requirements
**FFmpeg diperlukan untuk pydub dalam pemrosesan MP3:**
```bash
# Ubuntu/Debian
sudo apt update
sudo apt install ffmpeg

# macOS
brew install ffmpeg

# Windows
# Download dari https://ffmpeg.org/download.html dan tambahkan ke PATH
```

### Input yang Diperlukan
- File audio: `33.wav` (format WAV)

### Output
- File `audio_kompresi.mp3`: Hasil kompresi MP3
- File `hasil_analisis_kompresi.png`: Visualisasi perbandingan lengkap
- Laporan analisis:
  - Rasio kompresi (~12:1)
  - Perbandingan spektrum frekuensi
  - Analisis cutoff frekuensi tinggi

---

## Problem 4: Watermarking Audio Digital ([problem4.ipynb](problem4.ipynb))

### Deskripsi
Implementasi teknik watermarking audio menggunakan metode spread spectrum dengan analisis efek variasi bobot embedding pada detektabilitas dan imperceptibility.

### Fitur Utama
- **Generasi Sinyal**: Pembuatan sinyal sinusoidal 440 Hz (nada A4)
- **Watermark Generation**: Sinyal noise pseudo-random dengan seed deterministik
- **Dual-Weight Embedding**: Perbandingan dua bobot berbeda (0.015 vs 0.003)
- **Audio Export**: Penyimpanan file WAV untuk semua varian sinyal
- **Deteksi Korelasi**: Algoritma deteksi watermark menggunakan korelasi
- **Visualisasi**: Perbandingan grafik sinyal sebelum dan sesudah watermarking
- **Analisis Trade-off**: Evaluasi detektabilitas vs imperceptibility

### Dependencies
```bash
pip install numpy matplotlib scipy
```

### Parameter Konfigurasi
```python
SAMPLE_RATE = 48000    # Sample rate audio (Hz)
DURATION = 5           # Durasi sinyal (detik)
FREQUENCY = 440.0      # Frekuensi carrier (Hz) - Nada A4
SEED = 718            # Seed untuk reproducibility
WEIGHT_1 = 0.015      # Bobot tinggi (lebih terdeteksi, lebih terdengar)
WEIGHT_2 = 0.003      # Bobot rendah (lebih tersembunyi, kurang terdengar)
```

### Output
- `sinyal_asli.wav`: Sinyal audio asli (440 Hz)
- `sinyal_watermarked_bobot_0.015.wav`: Watermarked dengan bobot tinggi
- `sinyal_watermarked_bobot_0.003.wav`: Watermarked dengan bobot rendah
- Visualisasi perbandingan sinyal
- Analisis skor deteksi korelasi

---

## Installation & Setup

### 1. Clone Repository
```bash
git clone https://github.com/yourusername/UAS-Sistem-Multimedia.git
cd UAS-Sistem-Multimedia
```

### 2. Install Dependencies

**Untuk menjalankan semua program:**
```bash
pip install numpy matplotlib scipy pillow pydub
```

**Atau install per program:**

**Problem 1 (JPEG Compression):**
```bash
pip install numpy matplotlib pillow
```

**Problem 3 (MP3 Analysis):**
```bash
pip install numpy matplotlib scipy pydub
```

**Problem 4 (Audio Watermarking):**
```bash
pip install numpy matplotlib scipy
```

### 3. Install System Dependencies

**Khusus untuk Problem 3 - FFmpeg diperlukan:**
```bash
# Ubuntu/Debian
sudo apt update
sudo apt install ffmpeg

# macOS dengan Homebrew
brew install ffmpeg

# Windows
# Download dari https://ffmpeg.org/download.html dan tambahkan ke PATH
```

### 4. Persiapkan File Input
- Letakkan file `33.wav` di root directory untuk Problem 3
- Letakkan file `1.jpeg` di folder `img/` untuk Problem 1

## Cara Menjalankan

### Menggunakan Jupyter Notebook
```bash
# Start Jupyter Notebook
jupyter notebook

# Atau menggunakan JupyterLab
jupyter lab
```

Kemudian buka file `.ipynb` yang diinginkan dan jalankan semua cell secara berurutan.

### Menggunakan VS Code
1. Install extension "Jupyter" di VS Code
2. Buka file `.ipynb`
3. Pilih Python interpreter yang sudah ter-install dependencies
4. Jalankan cell satu per satu atau sekaligus

## Requirements per Program

| Program | Dependencies | System Deps | Input Files |
|---------|-------------|-------------|-------------|
| **Problem 1** | `numpy matplotlib pillow` | None | `img/1.jpeg` |
| **Problem 3** | `numpy matplotlib scipy pydub` | **FFmpeg** | `33.wav` |
| **Problem 4** | `numpy matplotlib scipy` | None | None (generated) |

## Hasil dan Analisis

### Problem 1: JPEG Compression Analysis
- **Demonstrasi**: Pipeline kompresi JPEG lengkap dari DCT hingga decoding
- **Analisis**: Efek kuantisasi terhadap kualitas gambar (MSE calculation)
- **Visualisasi**: Perbandingan blok asli vs rekonstruksi dengan error mapping

### Problem 3: Audio Compression Comparison
- **Compression Ratio**: ~12:1 (dari ~31MB WAV ke ~2.6MB MP3)
- **Spektral Analysis**: Identifikasi cutoff frekuensi tinggi pada MP3 (~16kHz)
- **Waveform Comparison**: Visualisasi perbedaan domain waktu

### Problem 4: Digital Audio Watermarking
- **Trade-off Analysis**: Perbandingan bobot embedding tinggi vs rendah
- **Detection Scores**: 
  - Sinyal asli: ~0.000000 (baseline)
  - Bobot 0.015: ~0.015000 (mudah terdeteksi)
  - Bobot 0.003: ~0.003000 (sulit terdeteksi)
- **Imperceptibility**: Bobot rendah menghasilkan distorsi yang lebih tidak terdengar

## File Output yang Dihasilkan

```
Generated Files:
├── audio_kompresi.mp3                    # Problem 3 output
├── hasil_analisis_kompresi.png           # Problem 3 visualization
├── sinyal_asli.wav                       # Problem 4 output
├── sinyal_watermarked_bobot_0.015.wav    # Problem 4 output
└── sinyal_watermarked_bobot_0.003.wav    # Problem 4 output
```

## Troubleshooting

### Problem 3: MP3 Conversion Errors
```bash
# Error: "ffmpeg not found"
sudo apt install ffmpeg  # Linux
brew install ffmpeg      # macOS

# Error: "Invalid data found when processing input"
# Pastikan file 33.wav tidak corrupt dan format valid
```

### General Installation Issues
```bash
# Jika terjadi error import
pip install --upgrade numpy matplotlib scipy pillow pydub

# Jika Jupyter tidak mendeteksi packages
python -m ipykernel install --user --name=myenv

# Jika pip tidak ditemukan
python -m pip install numpy matplotlib scipy pillow pydub
```

## Technical Details

### Audio Processing Specifications
- **Sample Rate**: 48 kHz (Problem 4), Variable (Problem 3)
- **Bit Depth**: 16-bit signed integer untuk output WAV
- **Channels**: Mono (single channel)
- **Format**: WAV untuk lossless, MP3 untuk lossy compression

### Image Processing Specifications
- **Color Space**: RGB → YCbCr conversion
- **Block Size**: 8×8 pixels untuk DCT
- **Quantization**: Standard JPEG quantization tables
- **Precision**: 8-bit per channel

---

### License
This project is created for educational purposes as part of Multimedia Systems coursework.

### Note
Pastikan semua file input tersedia di lokasi yang benar sebelum menjalankan program. Setiap program akan memberikan pesan error yang informatif jika ada file yang tidak ditemukan atau dependencies yang hilang.