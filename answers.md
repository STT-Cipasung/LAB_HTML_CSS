# Jawaban Praktikum: <Siti Mulyani> (<10224025>)

## Bagian 1: Pemanasan
1. **Aturan `nav a.active:hover { color: red; }`:**
   - **Selector:** `nav a.active:hover`
   - **Deklarasi:** `{ color: red; }`
   - **Property:** `color`
   - **Value:** `red`
   - **Pseudo-class:** `:hover` (Catatan: `.active` adalah class selector, sedangkan `:hover` adalah pseudo-class)

2. **Default display element:**
   - `span`: Inline
   - `p`: Block
   - `a`: Inline
   - `li`: Block (berperilaku dasar sebagai block)
   - `h2`: Block
   - `strong`: Inline

3. **Paragraf yang menjadi hijau:**
   - Paragraf **A** dan **B**. 
   - *Alasan:* Selector `.box p` menargetkan semua elemen `<p>` yang merupakan keturunan (descendant) di dalam elemen berperekat `class="box"`.

4. **Warna teks `<h1 id="title" class="heading">`:**
   - Warna: **Red (Merah)**
   - *Alasan:* Selector ID (`#title`) memiliki nilai *specificity* tertinggi (0,1,0,0) dibandingkan selector class (`.heading` = 0,0,1,0) dan selector tipe element (`h1` = 0,0,0,1).

5. **Kesalahan HTML `<p>Hello <strong>world</p></strong>`:**
   - Tag saling tumpang tindih (*improper nesting*). Tag `<strong>` dibuka di dalam `<p>`, tetapi ditutup setelah tag penutup `</p>`.
   - *Perbaikan:* `<p>Hello <strong>world</strong></p>`

---

## Bagian 3: Prediksi Selector Golf
P1. Prediksi warna:
   (a) "Weekly hack nights." -> **Green (Hijau)** (Kalah spesifik dibanding `section p`)
   (b) "Bring your own laptop." -> **Orange (Oranye)** (Class `.note` paling spesifik)
   (c) "© 2026 Student Affairs" -> **Blue (Biru)** (Hanya cocok dengan `p`)

P2. Urutan specificity dari tertinggi ke terendah:
   1. `#tech p` (Specificity: 0, 1, 0, 1)
   2. `.club p` (Specificity: 0, 0, 1, 1)
   3. `main section p` (Specificity: 0, 0, 0, 3)
   4. `p` (Specificity: 0, 0, 0, 1)

Setelah diuji (hasil sebenarnya): Hasil pengujian sama persis dengan prediksi karena perhitungan nilai specificity CSS terbukti konsisten.

---

## Bagian 4: Box model
Q1 (content-box): 
   - **Lebar yang terlihat (visible width):** `334px`
   - *Perhitungan:* `300px` (content) + `16px` (padding kiri) + `16px` (padding kanan) + `1px` (border kiri) + `1px` (border kanan) = `334px`.

Q2 (border-box):
   - Lebar total kartu tetap **300px**. Lebar area konten (*content width*) secara otomatis menyusut menjadi **266px** (`300px` - `32px padding` - `2px border`).

Pengecekan DevTools:
   - Content: `926px × height` (pada layar 960px)
   - Padding: `16px` (top, right, bottom, left)
   - Border: `1px` (top, right, bottom, left)
   - Margin: `0px 0px 24px 0px`

---

## Bagian 5: Tabel debug
| # | Baris | Bug | Perbaikan | Cara menemukannya |
|---|-------|-----|-----------|-------------------|
| 1 | 9 | Tipografi properti `colour` salah | Ubah menjadi `color` | DevTools (properti tidak dikenali) |
| 2 | 12 | Kurang titik koma `;` pada `background` | Tambahkan `;` di akhir nilai `#dbe7f3;` | Membaca kode / DevTools |
| 3 | 15 | Selector `.Card` menggunakan huruf kapital | Ubah menjadi `.card` (sesuai HTML) | Membaca kode (CSS bersifat case-sensitive) |
| 4 | 19 | Selector `#news-list` tidak cocok dengan ID HTML | Ubah menjadi `#newsList` | Membaca kode / DevTools |
| 5 | 20 | Terdapat spasi pada unit `18 px` | Ubah menjadi `18px` | DevTools |
| 6 | 23 | Ejaan nilai properti `centre` salah | Ubah menjadi `center` | DevTools |
| 7 | 28 | Tag penutup heading tidak cocok `<h1>...</h2>` | Ubah `</h2>` menjadi `</h1>` | W3C Validator |
| 8 | 31 | Kurang tanda kutip penutup pada `href="about.html>` | Ubah menjadi `href="about.html">` | W3C Validator |
| 9 | 36 | Tag `<img>` tidak memiliki atribut `alt` | Tambahkan `alt="Gambar Berita Kampus"` | W3C Validator |

---

## Bagian 6: Tabel Code Review
| # | Baris | Masalah | Mengapa penting | Perbaikan saya |
|---|-------|---------|-----------------|----------------|
| 1 | 1 | Tidak ada `<!DOCTYPE html>` dan atribut `lang` | Dokumen dianggap quirks mode dan tidak ramah aksesibilitas | Menambahkan `<!DOCTYPE html>` dan `<html lang="id">` |
| 2 | 12,18 | Penggunaan `<div>` tanpa tag semantik | Buruk untuk SEO dan screen reader | Mengganti dengan `<header>`, `<main>`, `<section>`, `<nav>`, `<footer>` |
| 3 | 13,19 | Menggunakan `<div>` bergaya tebal sebagai judul | Tidak membentuk hirarki outline dokumen | Mengganti dengan tag `<h1>` dan `<h2>` |
| 4 | 4 | Fixed width `width: 1200px;` pada header | Menyebabkan scroll horizontal di layar HP/tablet | Menggunakan `max-width: 1200px;` dan `width: 100%` |
| 5 | 5 | Penggunaan `!important` pada `.nav a` | Mempersulit overriding CSS di masa mendatang | Menghapus `!important` dan merapikan hirarki selector |
| 6 | 24,25 | Input form tidak memiliki `<label>` dan type email | Menyulitkan pengguna perangkat bantu dan validasi form | Menambahkan `<label for="...">` dan `type="email"` |
| 7 | 22 | Tag `<img>` tanpa atribut `alt` | Melanggar standar aksesibilitas web | Menambahkan atribut `alt` deskriptif |
| 8 | 19,21 | Penggunaan inline `style="..."` dan tag `<br>` berlebih | Mengotori struktur HTML dan menyulitkan pemeliharaan | Memindahkan style ke CSS dan gunakan `margin` |

Refleksi:
1. Masalah semantik HTML dan aksesibilitas (seperti hilangnya tag `<label>` dan `alt`). Alasannya, di browser visualnya terlihat baik-baik saja, namun struktur kodenya rusak bagi SEO dan screen reader.
2. Karena kode yang hanya "tampak bekerja" belum tentu aksesibel untuk penyandang disabilitas, sulit dipelihara (*maintainability*), buruk untuk SEO, dan bisa rusak di layar perangkat yang berbeda.
3. Selalu mengecek kode menggunakan W3C Validator dan Inspect Element DevTools sebelum mengumpulkan tugas.

---

## Bagian 7: Exit ticket
1. Anatomi aturan CSS terdiri dari **Selector** (penunjuk elemen) dan **Declaration Block** `{}` yang berisi pasangan **Property** (sifat) dan **Value** (nilai) yang dipisahkan oleh titik dua dan diakhiri titik koma.
2. Penghitungan kombinasi specificity CSS ketika menggabungkan pseudo-class dan attribute selector.
3. Membuat struktur dasar HTML5 semantik lengkap dengan form, tabel, dan tautan CSS tanpa melihat panduan.