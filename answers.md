## Bagian 1: Pemanasan
1.nav a.active:hover { color: red; }
  Selector: nav a.active:hover
  Deklarasi: { color: red; }
  Property: color
  Value: red
  Pseudo-class: :active dan :hover
2.Block: <p>, <li>, <h2>
  Inline: <span>, <a>, <strong>
3.A dan B karena selector .box p akan memilih semua elemen <p> yang berada
  di dalam elemen ber-class box. Paragraf A dan B ada di dalam <div class="box">.
4.Warna Merah (red) karena tingkat spesifisitas (specificity) selector ID
  (#title) lebih tinggi daripada selector class (.heading) maupun selector elemen (h1).
5.Kesalahan: Terjadi tumpang tindih urutan penutupan tag (improper
  nesting). Tag <strong> dibuka di dalam elemen <p>, sehingga harus ditutup sebelum tag </p>.
  Perbaikan: <p>Hello <strong>world</strong></p>

## Bagian 3: Prediksi Selector Golf
P1. Prediksi Warna Teks
a "Weekly hack nights."
   Prediksi: Hijau (`green`)
   Hasil Sebenarnya: Hijau (`green`)
   Penjelasan: Teks ini adalah tag `<p>` di dalam `<section id="tech">`. Selector `section p` memilliki spesifisitas `(0, 0, 0, 2)` yang lebih tinggi daripada `p` `(0, 0, 0, 1)`.
b "Bring your own laptop."
   Prediksi: Oranye (`orange`)
   Hasil Sebenarnya: Oranye (`orange`)
   Penjelasan: Elemen ini memiliki `class="note"`. Selector `.note` memilliki spesifisitas `(0, 0, 1, 0)` yang lebih tinggi daripada `section p` `(0, 0, 0, 2)` dan `p` `(0, 0, 0, 1)`.
c "© 2026 Student Affairs"
  Prediksi: Biru (`blue`)
  Hasil Sebenarnya: Biru (`blue`)
  Penjelasan: Paragraf di footer hanya cocok dengan selector `p` `(0, 0, 0, 1)` karena berada di luar elemen `<section>`.

P2. Urutan Specificity (Tertinggi ke Terendah)
1.`#tech p` — `(0, 1, 0, 1)` (1 ID, 1 Element)
2.`.club p` — `(0, 0, 1, 1)` (1 Class, 1 Element)
3.`main section p` — `(0, 0, 0, 3)` (3 Element)
4.`p` — `(0, 0, 0, 1)` (1 Element)

## Bagian 4: Box model
Q1.Lebar yang Terlihat dengan `box-sizing: content-box`
Lebar yang terlihat:** `334px`
Perhitungan:
Lebar total yang terlihat (border-to-border) dihitung dengan rumus:
$$\text{Lebar} = \text{width} + \text{padding-left} + \text{padding-right} + \text{border-left} + \text{border-right}$$
$$\text{Lebar} = 300\text{px} + 16\text{px} + 16\text{px} + 1\text{px} + 1\text{px} = 334\text{px}$$

Q2.Perubahan saat Ditambahkan `box-sizing: border-box`
Perubahan: Lebar total yang terlihat dari tepi border ke tepi border akan tetap 300px.
Penjelasan: Properti `padding` (16px) dan `border` (1px) akan dimasukkan ke dalam perhitungan total `width` (300px), sehingga area konten (content width) secara otomatis menyusut menjadi:
$$300\text{px} - (16\text{px} \times 2) - (1\text{px} \times 2) = 266\text{px}$$

Pengecekan DevTools
Catatan nilai pada panel **Computed → box model** untuk elemen `<section>`:
Content:`926px` × (tinggi konten)
Padding:`16px` (atas, kanan, bawah, kiri)
Border:`1px` (atas, kanan, bawah, kiri)
Margin:`0px` (atas, kanan, kiri), `24px` (bawah)

## Bagian 5: Tabel Debug
| No | Lokasi Bug | Kode Asli (Salah) | Kode Perbaikan | Cara Menemukannya | Jenis Bug |
| --- | --- | --- | --- | --- | --- |
| 1 | CSS `body` | `colour: #333;` | `color: #333;` | DevTools (property tidak valid/dicoret) | CSS |
| 2 | CSS `header` | `background: #dbe7f3` (kurang `;`) | `background: #dbe7f3;` | Membaca kode / DevTools (rule error) | CSS |
| 3 | CSS `.Card` vs HTML `.card` | `.Card` (C kapital) | `.card` | DevTools (style tidak terapkan ke elemen) | CSS |
| 4 | CSS `#news-list` vs HTML `#newsList` | `#news-list` | `#newsList` | DevTools (selector ID tidak cocok) | CSS |
| 5 | CSS `#news-list` | `font-size: 18 px;` (ada spasi) | `font-size: 18px;` | DevTools (nilai tidak valid/dicoret) | CSS |
| 6 | CSS `footer` | `text-align: centre;` | `text-align: center;` | DevTools (nilai property tidak valid/dicoret) | CSS |
| 7 | HTML `<h1>` | `<h1>Campus News</h2>` | `<h1>Campus News</h1>` | Validator W3C / Membaca kode | HTML |
| 8 | HTML `<a href...>` | `<a href="about.html>About</a>` | `<a href="about.html">About</a>` | Validator W3C / Syntax Highlighting | HTML |
| 9 | HTML `<img>` | Atribut `src` terpotong & kurang `alt` | `<img src="[https://placehold.co/600x200?text=News](https://placehold.co/600x200?text=News)" alt="Campus News Image">` | Validator W3C / Membaca kode | HTML |
| 10 | HTML `<li>` | `<li>New library books have arrived</li` | `<li>New library books have arrived</li>` | Validator W3C / Syntax Highlighting | HTML |
| 11 | HTML `<li>` | `<li>Coding Day registration is open</l` | `<li>Coding Day registration is open</li>` | Validator W3C / Syntax Highlighting | HTML |

## Bagian 6: Tabel Code Review
| No | Lokasi Kode | Masalah | Alasan Mengapa Ini Buruk & Rekomendasi Perbaikan |
|---|---|---|---|
| 1 | Tag `<html>` | Kurang atribut `lang="id"` atau `lang="en"`. | Buruk untuk *accessibility* dan SEO karena *screen reader* tidak dapat mendeteksi bahasa utama halaman. **Solusi:** Tambahkan `lang="id"` atau `lang="en"`. |
| 2 | Struktur `<head>` | Tidak ada `<meta charset="UTF-8">` dan `<meta name="viewport"...>`. | Karakter non-ASCII berisiko rusak dan tampilan menjadi tidak responsif di perangkat seluler. **Solusi:** Tambahkan meta tag charset dan viewport. |
| 3 | Penggunaan `<div>` | *Div soup* (menggunakan `<div>` untuk header, nav, content, sidebar, footer, dan judul). | Tidak memiliki struktur semantik HTML5, membuat *screen reader* dan mesin pencari sulit memahami hirarki halaman. **Solusi:** Gunakan elemen semantik seperti `<header>`, `<nav>`, `<main>`, `<section>`, dan `<footer>`. |
| 4 | Elemen Heading | Judul menggunakan `<div>` bertuliskan tebal (`<div class="title">`, `style="font-size: 24px..."`). | Merusak hirarki dokumen. *Screen reader* dan SEO mengandalkan tag `<h1>`-`<h6>` untuk navigasi. **Solusi:** Gunakan `<h1>` untuk judul utama dan `<h2>` untuk judul section. |
| 5 | Aksesibilitas Gambar | Tag `<img>` tidak memiliki atribut `alt`. | Pengguna *screen reader* tidak bisa mengetahui deskripsi gambar, dan halaman gagal memenuhi standar aksesibilitas W3C. **Solusi:** Tambahkan atribut `alt="Deskripsi gambar"`. |
| 6 | Aksesibilitas Form | Elemen `<input>` tidak menggunakan elemen `<label>` (hanya mengandalkan `placeholder`). | *Placeholder* akan hilang saat teks diketik dan tidak terbaca dengan baik oleh *screen reader*. **Solusi:** Tambahkan elemen `<label for="...">` pada setiap input. |
| 7 | Tipe Input Form | Kolom email menggunakan `type="text"`. | Tidak ada validasi bawaan browser untuk format email dan keyboard HP tidak secara otomatis menampilkan simbol `@`. **Solusi:** Ubah menjadi `type="email"`. |
| 8 | Inline Style & `!important` | Banyak menggunakan atribut `style="..."` serta `!important` di CSS. | Merusak prinsip pemisahan struktur dan gaya (*separation of concerns*) serta menyulitkan *override* CSS di masa mendatang. **Solusi:** Pindahkan semua gaya ke file CSS terpisah dan hapus `!important`. |
| 9 | CSS Tidak Terpakai | Selector `.sidebar` dibuat di CSS tetapi tidak pernah dipakai di HTML. | Menambah ukuran file CSS tanpa memberikan fungsi apa pun (*dead code*). **Solusi:** Hapus selector yang tidak terpakai. |
| 10 | Layout & Kontras Warna | `.header` menggunakan `width: 1200px;` kaku dan kontras warna teks `.content` (`#bbbbbb`) sangat rendah. | Tampilan akan terpotong (*overflow*) di layar kecil dan teks abu-abu terang sangat sulit dibaca (melanggar standar WCAG). **Solusi:** Gunakan `max-width` responsif dan tingkatkan kontras warna teks. |
| 11 | Pemisah Baris | Menggunakan tag `<br><br>` untuk membuat jarak antar elemen. | Mengatur jarak (*spacing*) adalah tugas dari properti CSS (`margin`/`padding`), bukan elemen pemisah baris HTML. **Solusi:** Hapus `<br>` dan atur jarak menggunakan margin di CSS. |
Refleksi
1.Masalah yang Paling Sulit Disadari:
Masalah struktur semantik (seperti penggunaan `<div>` untuk judul alih-alih `<h1>`/`<h2>`) dan ketiadaan atribut `alt` atau `<label>` adalah yang paling sulit disadari secara visual. Hal ini terjadi karena browser tetap merender tampilan sesuai ukuran font dan style yang diberikan tanpa menampilkan error visual. Namun, masalah ini sangat merugikan bagi pengguna *screen reader* dan menurunkan peringkat SEO halaman.

2.Mengapa Masalah Ini Tetap Penting Meskip Halaman "Berfungsi":
Halaman yang sekadar "terlihat berfungsi" sering kali tidak dapat diakses (*accessible*) oleh penyandang disabilitas, tidak responsif di berbagai perangkat, dan sulit diindeks oleh mesin pencari. Selain itu, praktik buruk seperti penggunaan inline style, tag `<br>` berlebihan, dan `!important` membuat basis kode sangat kaku dan sulit dipelihara (*maintainability*) oleh tim di masa depan.

3.Kebiasaan Utama Sebelum Mengumpulkan Kode:
Saya akan selalu menjalankan validasi HTML melalui W3C HTML Validator serta menguji halaman menggunakan DevTools (termasuk audit Lighthouse untuk pengecekan *accessibility*, serta simulasi tampilan seluler/responsif) sebelum mempublikasikan atau mengumpulkan kode.

## Bagian 7: Exit ticket
1.Anatomi Aturan CSS:
   Aturan CSS terdiri dari selector dan blok deklarasi. Selector berfungsi untuk menunjuk atau memilih elemen HTML mana yang ingin diubah gayanya. Di dalam kurung kurawal `{ ... }`, terdapat deklarasi yang terdiri dari pasangan property (sifat yang ingin diubah, seperti warna atau ukuran) dan value (nilai dari sifat tersebut), yang diakhiri dengan tanda titik koma `;`.

2.Konsep yang Masih Perlu Dipahami Lebih Lanjut:
   Perhitungan spesifisitas (*specificity*) pada kombinasi selector yang kompleks (seperti penggabungan pseudo-class, atribut, dan descendant) masih memerlukan lebih banyak latihan agar bisa memprediksi hasilnya secara cepat tanpa ragu.

3. Hal yang Sudah Dikuasai Tanpa Perlu Mencarinya:
   Membuat struktur dokumen HTML5 semantik secara mandiri (mulai dari `<!DOCTYPE html>`, `<head>` lengkap dengan meta tag, hingga tag utama seperti `<header>`, `<nav>`, `<main>`, `<section>`, dan `<footer>`) serta menerapkan styling tata letak dasar menggunakan Flexbox dan Box Model.