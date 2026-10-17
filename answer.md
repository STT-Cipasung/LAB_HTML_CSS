## Bagian 1: Pemanasan
1. selector: `nav a.active:hover, deklarasi: color: red;, property: color, value: red, pseudo-class: :hover.
2. block: p, li, h2 | inline: span, a, strong
3. a dan b
4. warnanya merah karena  selector ID memiliki spesifisitas paling tinggi dibandingkan selector lainnya.
5. penutup elmen  <p> ada di dalam tag <strong> jadi elmen penutup </p> tidak akan terbaca dan ada kata 'hello' ada di luar tag <strong> jadi 'hello' tidak tebal, harusnya <p>hello world</strong></p> 
## Bagian 3: Selector Golf (Prediksi & Hasil)

### Prediksi (P1 & P2)
- P1. Prediksi Warna Teks:**
  - (a) "Weekly hack nights.": **green** (karena selector `section p` [0,0,0,2] lebih spesifik dibanding `p` [0,0,0,1]).
  - (b) "Bring your own laptop.": **orange** (karena class `.note` [0,0,1,0] memilik specificity lebih tinggi dari `section p` [0,0,0,2]).
  - (c) "© 2026 Student Affairs": **blue** (karena hanya cocok dengan selector `p` [0,0,0,1]).

- P2. Urutan Specificity (Tertinggi ke Terendah):**
  1. `#tech p` (Specificity: `0,1,0,1` — ID + Element)
  2. `.club p` (Specificity: `0,0,1,1` — Class + Element)
  3. `main section p` (Specificity: `0,0,0,3` — 3 Elements)
  4. `p` (Specificity: `0,0,0,1` — 1 Element)

---

### Hasil Uji Sebenarnya
- Hasil P1:**
  - (a) "Weekly hack nights." = **green**
  - (b) "Bring your own laptop." = **orange**
  - (c) "© 2026 Student Affairs" = **blue**
- **Penjelasan:** Hasil uji sesuai dengan prediksi awal karena mengikuti aturan CSS Specificity: ID > Class > Element.
## Bagian 4: Box Model

### Q1. Lebar yang Terlihat (`content-box`)
Perhitungan lebar tampak (border-box width) dari kiri ke kanan:
- Content Width = 300px
- Padding Kiri & Kanan = 16px + 16px = 32px
- Border Kiri & Kanan = 1px + 1px = 2px

**Total Lebar Terlihat:** 300px + 32px + 2px = **334px**
*(Margin 24px berada di luar border sehingga tidak dihitung sebagai bagian dari fisik kartu)*

### Q2. Efek `box-sizing: border-box`
Jika `box-sizing: border-box` digunakan, **lebar total yang terlihat tetap tepat 300px**. Browser secara otomatis memperkecil area content menjadi `266px` (300px - 32px - 2px) agar total elemen pas di ukuran `300px`.

### Pengecekan DevTools
Pada elemen section kartu (`.card`):
- **Content:** ~926px (atau sesuai sisa area container)
- **Padding:** 16px (top, right, bottom, left)
- **Border:** 1px (top, right, bottom, left)
- **Margin:** 0px top/right/left, 24px bottom
## Bagian 5: Debugging

| Bug | Jenis (HTML/CSS) | Sebelum Perbaikan | Sesudah Perbaikan | Cara Menemukannya |
| --- | --- | --- | --- | --- |
| 1 | CSS | `colour: #333;` | `color: #333;` | DevTools menampilkan property yang dicoret |
| 2 | CSS | `background: #dbe7f3` (kurang titik koma) | `background: #dbe7f3;` | Membaca kode / DevTools syntax error |
| 3 | CSS | `.Card` (C kapital) | `.card` (c kecil) | Membaca kode (perbedaan case-sensitivity dengan HTML) |
| 4 | CSS | `font-size: 18 px;` (ada spasi) | `font-size: 18px;` | DevTools menampilkan nilai invalid / dicoret |
| 5 | CSS | `text-align: centre;` | `text-align: center;` | DevTools menampilkan property/value yang dicoret |
| 6 | HTML | `<h1>Campus News</h2>` | `<h1>Campus News</h1>` | Validator W3C / Membaca kode |
| 7 | HTML | `<a href="about.html>About</a>` | `<a href="about.html">About</a>` | Validator W3C / Membaca kode (penutup petik hilang) |
| 8 | HTML | `<img src="...">` | `<img src="..." alt="Gambar Berita Kampus">` | Validator W3C (atribut alt wajib untuk elemen img) |
| 9 | HTML/CSS | `#news-list` di CSS vs `id="newsList"` di HTML | `#newsList` di CSS (atau `id="news-list"` di HTML) | Membaca kode / DevTools selector tidak terhubung |