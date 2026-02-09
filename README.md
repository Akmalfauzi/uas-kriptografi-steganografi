# UAS Kriptografi dan Steganografi

**Nama**  : AKMAL FAUZI<br>
**NIM**   : 230401010160<br>
**Kelas**  : IF 502<br>
**Prodi**  : S1 PJJ Informatika<br>
**Mata Kuliah** : Kriptografi dan Steganografi

---

## Tentang Proyek

Proyek ini merupakan implementasi sederhana teknik **Steganografi** menggunakan metode **LSB (Least Significant Bit)**. Teknik ini digunakan untuk menyembunyikan pesan teks di dalam gambar dengan cara mengubah bit terakhir dari setiap piksel.

### Cara Kerja

1. Pesan teks dikonversi menjadi biner (8 bit per karakter)
2. Gambar dibaca dan diratakan menjadi array 1D
3. Setiap bit pesan disisipkan ke bit terakhir (LSB) piksel gambar
4. Gambar hasil steganografi (stego image) dihasilkan

---

## Cara Menjalankan

### 1. Clone Repository

Pertama, clone repository ini ke komputer lokal Anda:

```bash
git clone https://github.com/akmalfauzi/uas-kriptografi-steganografi.git
cd uas-kriptografi-steganografi
```

---

### 2. Google Colab (Rekomendasi - Paling Mudah)

Cara ini paling praktis karena tidak perlu instalasi lokal.

1. Buka [Google Colab](https://colab.research.google.com/)
2. Upload file `UAS_IF502_230401010160.ipynb`
3. Jalankan sel (cell) satu per satu
4. Library `numpy` dan `matplotlib` sudah tersedia di Colab
5. Jika `imageio` belum terinstall, jalankan di sel pertama:
   ```python
   !pip install imageio
   ```

---

### 3. Instalasi Lokal dengan Virtual Environment (venv)

Disarankan menggunakan virtual environment untuk menghindari konflik library.

#### Windows

```bash
# Buat virtual environment
python -m venv venv

# Aktifkan virtual environment
venv\Scripts\activate

# Install dependencies
pip install numpy imageio matplotlib pillow

# Jalankan program
python UAS_IF502_230401010160.py
```

#### macOS / Linux

```bash
# Buat virtual environment
python3 -m venv venv

# Aktifkan virtual environment
source venv/bin/activate

# Install dependencies
pip install numpy imageio matplotlib pillow

# Jalankan program
python UAS_IF502_230401010160.py
```

---

### 4. Instalasi Lokal Tanpa Virtual Environment

Jika Anda tidak ingin menggunakan virtual environment.

#### Windows

```bash
pip install numpy imageio matplotlib pillow
python UAS_IF502_230401010160.py
```

#### macOS / Linux

```bash
pip3 install numpy imageio matplotlib pillow
python3 UAS_IF502_230401010160.py
```

---

## Dependencies

| Library | Fungsi |
|---------|--------|
| `numpy` | Operasi array dan manipulasi piksel gambar |
| `imageio` | Membaca dan menulis file gambar (menggunakan API v3) |
| `matplotlib` | Menampilkan visualisasi gambar |
| `pillow` | Dukungan pemrosesan gambar tambahan |

Install semua dependencies:
```bash
pip install numpy imageio matplotlib pillow
```

---

## Struktur Kode

### Fungsi Utama

```python
text_to_bits(text)    # Mengubah teks menjadi biner
bits_to_text(bits)    # Mengubah biner menjadi teks
sembunyikan_pesan(nama_file_input, pesan)  # Menyembunyikan pesan dalam gambar
```

### Algoritma LSB

```python
# Inti dari teknik LSB:
pixel[i] = (pixel[i] & 254) | bit_pesan[i]
```

Kode di atas melakukan:
1. `pixel[i] & 254` - Menghapus bit terakhir (LSB)
2. `| bit_pesan[i]` - Menyisipkan bit pesan ke posisi LSB

---

## Contoh Output

Program akan membuat:
- `cover.png` - Gambar tes acak 10x10 piksel
- Menampilkan perbandingan gambar original dan stego image

Pesan yang disembunyikan: **"AKU"**

---

## Catatan

- Program ini menggunakan `imageio.v3` API (`import imageio.v3 as iio`)
- Untuk Google Colab, gunakan file `.ipynb`
- Untuk menjalankan lokal, gunakan file `.py`
