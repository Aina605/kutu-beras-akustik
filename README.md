# kutu-beras-akustik
# Analisis Sinyal Akustik Kutu Beras (Topik 3, Kelompok 3)

Mata kuliah Sinyal & Sistem. Progres minggu 1: data siap, praproses, dan deteksi event.

## Data (semua publik, tidak ada pengambilan data mandiri)
- Bug Bytes sound library, USDA ARS (domain publik): 95 file WAV hama gudang + CSV inventaris.
  https://catalog.data.gov/dataset/bug-bytes-sound-library-stored-product-insect-pest-sounds
- Acoustic detection and classification of three stored product insect pests, USDA ARS (CC0): CSV fitur getaran (159 rekaman, 3 spesies x 3 kepadatan: 5, 20, 40 ekor/kg).
  https://catalog.data.gov/dataset/data-from-acoustic-detection-and-classification-of-three-stored-product-insect-pests

File audio dan CSV mentah tidak diunggah ke repositori ini; unduh dari tautan di atas.

## Isi repositori
- `Topik3_KutuBeras_Minggu1.ipynb`: notebook lengkap (unduh data, inventaris fs, praproses, deteksi event)
- `inventaris_fs.csv`: sample rate, durasi, dan kanal 95 file WAV
- `file_terpilih.csv`: 12 file terpilih (9 hama gudang + 3 noise)
- `hasil_event_minggu1.csv`: jumlah event, ambang, durasi, dan interval per file
- `plot_A3_event.png`: contoh deteksi event pada A3 (S. oryzae, sensor PVDF)

## Parameter praproses
- Resample ke fs bersama: 20.000 Hz (fs terkecil di file hama terpilih, tanpa upsampling)
- Highpass Butterworth orde 4, cutoff 200 Hz
- RMS per frame 10 ms
- Deteksi event: RMS > median + 3 x MAD

## Catatan
- Sensor ultrasonik (A5, A6, 50 kHz) kehilangan komponen di atas 10 kHz akibat resample ke 20 kHz.
- Jumlah event saja tidak membedakan hama dari noise (ambang dihitung per file); minggu 2 memakai campuran sinyal bersih + noise pada SNR terkendali.
- File noise I5 dan I6 terbaca 0 detik dan belum dipakai.

## Lingkungan
Python (Google Colab): numpy, scipy, librosa, soundfile, pandas, matplotlib.
