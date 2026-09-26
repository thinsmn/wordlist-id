# Indonesian Wordlist (`wordlist-id.txt`)

Daftar kata Bahasa Indonesia pilihan yang telah dikurasi berisi **2.048 kata** unik, bersih, dan ringkas. Wordlist ini dirancang sebagai korpus kata dasar yang dapat digunakan untuk berbagai keperluan umum, seperti pengujian sistem, permainan kata (*word games*), analisis teks/NLP ringan, mekanisme *lookup* atau *autocomplete*, pemeriksa ejaan (*spell checker*), hingga kamus referensi cepat.

---

## Daftar Isi
- [Tentang Wordlist](#tentang-wordlist)
- [Metodologi Pembuatan](#metodologi-pembuatan)
  - [1. Sumber dan Kurasi Kata](#1-sumber-dan-kurasi-kata)
  - [2. Kriteria Seleksi & Eliminasi](#2-kriteria-seleksi--eliminasi)
  - [3. Keunikan Prefiks (4 Karakter)](#3-keunikan-prefiks-4-karakter)
  - [4. Batasan Karakter & Format](#4-batasan-karakter--format)
  - [5. Normalisasi & Pengurutan](#5-normalisasi--pengurutan)
- [Statistik Wordlist](#statistik-wordlist)
  - [Distribusi Panjang Kata](#distribusi-panjang-kata)
  - [Distribusi Huruf Awal](#distribusi-huruf-awal)
- [Struktur & Format File](#struktur--format-file)
- [Contoh Penggunaan](#contoh-penggunaan)
  - [1. Python](#1-python)
  - [2. JavaScript / Node.js](#2-javascript--nodejs)
  - [3. Bash / Shell](#3-bash--shell)
- [Lisensi](#lisensi)

---

## Tentang Wordlist

Daftar kata ini dibuat untuk menyediakan himpunan kata Bahasa Indonesia yang terstandardisasi, ringkas, dan bebas dari ambiguitas. Dengan ukuran tepat **2.048 entri**, wordlist ini memiliki ukuran yang proporsional untuk dimuat langsung ke dalam memori aplikasi (*in-memory lookup*), tabel *hash*, maupun array pencarian cepat.

---

## Metodologi Pembuatan

Proses kurasi dan penyaringan kata dilakukan melalui langkah-langkah terstruktur berikut:

### 1. Sumber dan Kurasi Kata
- Kata-kata dihimpun dari kosakata umum Bahasa Indonesia dan diselaraskan dengan kaidah leksikon baku (mengacu pada KBBI).
- Diprioritaskan kata dasar (*root words*) yang lazim dikenali oleh masyarakat umum sehari-hari dan mudah dipahami maknanya.

### 2. Kriteria Seleksi & Eliminasi
Untuk menjaga agar daftar kata tetap bersih dan netral:
- **Menghindari Kata Vulgar & Kasar**: Kata-kata yang bermakna tabu, ofensif, atau tidak pantas dieliminasi dari daftar.
- **Menghindari Homofon & Ambiguitas Ejaan**: Menghindari kata yang memiliki variasi ejaan yang membingungkan atau sangat mirip bunyi pelafalannya dengan kata lain.
- **Mengutamakan Kata yang Ringkas**: Membatasi penggunaan kata berimbuhan majemuk atau terlalu panjang agar tetap efisien ketika dibaca maupun ditulis.

### 3. Keunikan Prefiks (4 Karakter)
- Seluruh kata di dalam daftar memiliki karakteristik unik: **setiap kata dapat dibedakan hanya melalui 4 huruf pertamanya** (atau seluruh huruf jika panjang kata kurang dari 4 karakter).
- Tidak ada dua kata berbeda yang berbagi 4 huruf awalan yang sama.
- Fitur ini sangat memudahkan integrasi sistem *autocomplete*, *predictive text*, maupun pengindeksan pohon prefix (*Trie*) dengan tingkat benturan (*collision*) nol.

### 4. Batasan Karakter & Format
- Hanya menggunakan huruf alfabet Latin kecil (`a`–`z`).
- Bebas dari angka, spasi, tanda baca, tanda hubung (`-`), ataupun karakter diakritik/simbol khusus.
- Panjang kata berada dalam rentang **3 hingga 8 huruf** (dengan rata-rata 5,30 huruf per kata), menjaga keseimbangan antara kekayaan kosakata dan kesederhanaan.

### 5. Normalisasi & Pengurutan
- Dikodekan dalam format teks standar **UTF-8**.
- Semua kata dinormalisasi ke huruf kecil (*lowercase*).
- Kata-kata diurutkan secara umum berdasarkan abjad (A–Z) guna mendukung pencarian berkinerja tinggi (*binary search*).

---

## Statistik Wordlist

| Parameter | Keterangan |
| :--- | :--- |
| **Jumlah Total Kata** | 2.048 kata |
| **Kata Duplikat** | 0 (tidak ada duplikasi) |
| **Keunikan Prefiks 4 Huruf** | 2.048 / 2.048 (100% unik) |
| **Panjang Kata Minimum** | 3 huruf |
| **Panjang Kata Maksimum** | 8 huruf |
| **Rata-rata Panjang Kata** | 5,30 huruf |
| **Karakter** | `a` sampai `z` (ASCII murni) |

### Distribusi Panjang Kata

| Panjang Huruf | Jumlah Kata | Persentase | Contoh |
| :---: | :---: | :---: | :--- |
| **3 huruf** | 7 | 0,3% | `air`, `api`, `doa`, `ibu`, `lem`, `rek`, `tas` |
| **4 huruf** | 399 | 19,5% | `abad`, `akal`, `emas`, `kopi`, `padi`, `zona` |
| **5 huruf** | 909 | 44,4% | `bagus`, `cetak`, `hutan`, `surat`, `wajah` |
| **6 huruf** | 486 | 23,7% | `alamat`, `berkah`, `dompet`, `kamera`, `sensor` |
| **7 huruf** | 192 | 9,4% | `anggota`, `bintang`, `menteri`, `pesawat` |
| **8 huruf** | 55 | 2,7% | `kacamata`, `pancasila`, `yudisial` |

### Distribusi Huruf Awal

```text
a: 106    b: 143    c:  57    d:  69    e:  31    f:  14    g:  76
h:  67    i:  47    j:  74    k: 204    l: 135    m: 126    n:  57
o:  28    p: 190    q:   5    r: 116    s: 214    t: 151    u:  57
v:  24    w:  36    x:   4    y:   9    z:   8
```

---

## Struktur & Format File

Daftar kata tersimpan dalam berkas [wordlist-id.txt](wordlist-id.txt):
- Setiap baris berisi tepat **satu kata**.
- Baris dipisahkan oleh karakter *newline* (`\n`).
- Tanpa spasi tambahan atau karakter kosong.

---

## Contoh Penggunaan

### 1. Python

Membaca wordlist dan melakukan pencarian berdasarkan prefix:

```python
# Memuat wordlist ke dalam list / set
with open("wordlist-id.txt", "r", encoding="utf-8") as f:
    words = [line.strip() for line in f if line.strip()]

# Menampilkan total kata
print(f"Total kata yang dimuat: {len(words)}")

# Pencarian kata berdasarkan prefix
prefix_input = "kopi"
matching = [w for w in words if w.startswith(prefix_input)]
print(f"Kata dengan prefix '{prefix_input}': {matching}")
```

### 2. JavaScript / Node.js

```javascript
const fs = require('fs');

const words = fs.readFileSync('wordlist-id.txt', 'utf-8')
  .split(/\r?\n/)
  .filter(word => word.length > 0);

console.log(`Total kata: ${words.length}`);

// Memeriksa keberadaan kata
const cekKata = (kata) => words.includes(kata.toLowerCase());
console.log("Apakah 'hutan' ada di daftar?", cekKata('hutan'));
```

### 3. Bash / Shell

```bash
# Menghitung jumlah kata
wc -l wordlist-id.txt

# Menampilkan 10 kata pertama
head -n 10 wordlist-id.txt

# Mencari kata tertentu
grep "^buku" wordlist-id.txt
```

---

## Lisensi

Proyek dan wordlist ini didistribusikan di bawah ketentuan **GNU Affero General Public License v3.0 (GNU AGPL v3)**.

Silakan membaca berkas [LICENSE](LICENSE) untuk rincian lengkap hak cipta dan izin penggunaan.
