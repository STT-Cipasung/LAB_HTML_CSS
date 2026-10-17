```markdown
# Jawaban Praktikum: <NadaAzrilAfdal> (<10224056>)

## Bagian 1: Pemanasan
1. Selector: nav a.active:hover
Deklarasi: color: red;
Property: color
Value: red
Pseudo-class: :hover
2. Block: p, h2
Inline: span, a, strong
List item: li — secara default display: list-item (berperilaku seperti item blok dalam daftar)
3. Paragraf A dan B menjadi hijau karena keduanya berada di dalam elemen .box. Selector .box p memilih semua elemen <p> yang merupakan keturunan elemen berkelas box (termasuk yang berada di dalam <section>).
C tidak cocok karena .box ada pada elemen <p> itu sendiri, bukan pada elemen induknya. D juga tidak cocok.
4. Warnanya merah. Ketiga aturan menargetkan elemen yang sama, tetapi selector ID (#title) memiliki spesifisitas lebih tinggi daripada selector class (.heading) dan selector elemen (h1), sehingga aturan #title { color: red; } menang.
5. Tag-nya bertumpuk tidak berurutan. Elemen <strong> dibuka di dalam <p>, jadi </strong> harus ditutup sebelum </p>.

## Bagian 3: Prediksi Selector Golf
P1. (a) “Weekly hack nights.” — hijau, karena section p lebih spesifik daripada p.
(b) “Bring your own laptop.” — oranye, karena .note lebih spesifik daripada section p.
(c) “© 2026 Student Affairs” — biru, karena hanya cocok dengan selector p.
P2. Urutan specificity tertinggi ke terendah:
#tech p — (1, 0, 1)
.club p — (0, 1, 1)
main section p — (0, 0, 3)
p — (0, 0, 1)
Setelah diuji di test-p1.html dengan test.css (hasil sebenarnya):
(a) “Weekly hack nights.” — hijau (rgb(0, 128, 0)).
(b) “Bring your own laptop.” — oranye (rgb(255, 165, 0)).
(c) “© 2026 Student Affairs” — biru (rgb(0, 0, 255)).

## Bagian 4: Box model
Q1 (content-box): Lebar terlihat = 300px + (16px × 2) + (1px × 2) = 334px. Margin 24px di kiri dan kanan tidak termasuk lebar dari tepi border ke tepi border (total ruang termasuk margin = 382px).
Q2 (border-box): Lebar terlihat menjadi 300px karena width sudah mencakup content, padding, dan border. Lebar content menjadi 300px - 32px - 2px = 266px. Margin tetap berada di luar kotak, sehingga total ruang termasuk margin = 348px.
Pengecekan DevTools: Section pertama dengan class .card — content sekitar 600.67px, padding 16px pada tiap sisi, border ditetapkan 1px pada CSS (browser menampilkan sekitar 0.67px pada skala halaman saat diperiksa), dan margin bawah 24px.

## Bagian 5: Tabel debug
| # | Baris | Bug | Perbaikan | Cara menemukannya |
|---|-------|-----|-----------|-------------------|
| 1 | 9 | Property `colour` bukan nama property CSS yang valid. | Ganti menjadi `color`. | DevTools menandai deklarasi sebagai tidak dikenal. |
| 2 | 12 | Deklarasi `background` tidak diakhiri titik koma, sehingga deklarasi `padding` berikutnya ikut menjadi tidak valid. | Tambahkan `;` setelah nilai `#dbe7f3`. | Membaca kode atau memeriksa deklarasi yang tidak diterapkan di DevTools. |
| 3 | 15 | Selector `.Card` peka huruf besar-kecil dan tidak cocok dengan class `card`. | Ganti selector menjadi `.card`. | Membaca kode dan membandingkan selector dengan atribut class. |
| 4 | 20 | Spasi pada `18 px` membuat nilai `font-size` tidak valid. | Ganti menjadi `18px`. | DevTools menampilkan deklarasi invalid/tidak diterapkan. |
| 5 | 23 | Nilai `centre` tidak valid untuk `text-align`. | Ganti menjadi `center`. | DevTools menampilkan nilai property yang tidak valid. |
| 6 | 29 | Elemen `<h1>` ditutup dengan `</h2>`. | Tutup dengan `</h1>`. | Validator HTML. |
| 7 | 32 | Atribut `href` pada link About tidak memiliki tanda kutip penutup. | Gunakan `href="about.html"`. | Validator HTML atau membaca kode. |
| 8 | 37 | Gambar tidak memiliki atribut `alt`. | Tambahkan deskripsi bermakna pada `alt`. | Validator HTML dan pemeriksaan aksesibilitas. |
| 9 | 38 | ID `newsList` tidak cocok dengan selector CSS `#news-list`. | Samakan selector dan ID; di sini selector diperbaiki menjadi `#newsList`. | Membandingkan selector CSS dengan ID pada HTML. |

## Bagian 6: Tabel Code Review
| # | Baris | Masalah | Mengapa penting | Perbaikan saya |
|---|-------|---------|-----------------|----------------|
| 1 | 1-2 | Tidak ada `<!DOCTYPE html>` dan atribut bahasa pada `<html>`. | Browser dapat masuk ke quirks mode, dan bahasa dokumen tidak tersedia untuk teknologi bantu maupun pemrosesan bahasa. | Tambahkan doctype HTML5 dan `lang="en"`. |
| 2 | 2-4 | Tidak ada deklarasi charset dan meta viewport. | Encoding dan tampilan pada perangkat seluler tidak dinyatakan secara eksplisit. | Tambahkan `<meta charset="UTF-8">` dan meta viewport. |
| 3 | 14-20, 32 | Header, navigasi, konten, dan footer dibangun dengan banyak `<div>` generik. | Elemen generik tidak menyampaikan struktur dokumen ke teknologi bantu. | Ganti dengan `<header>`, `<nav>`, `<main>`, `<section>`, dan `<footer>`. |
| 4 | 15 | Judul kampus hanya berupa `<b>` di dalam `<div>`, bukan heading. | Tidak ada judul utama yang bisa dinavigasi melalui heading oleh pengguna pembaca layar. | Jadikan nama kampus satu-satunya `<h1>`. |
| 5 | 21, 27 | Judul About Us dan Contact Us dibuat dengan `<div>` berukuran besar. | Tampilan tebal/besar tidak menggantikan semantik heading dan merusak outline dokumen. | Gunakan `<h2>` untuk judul section. |
| 6 | 6 | `.header` memiliki lebar tetap `1200px`. | Konten melampaui viewport pada layar lebih kecil dan dapat menyebabkan scroll horizontal. | Batasi lebar halaman dengan `max-width` dan pusatkan menggunakan `margin: 0 auto`. |
| 7 | 7 | Tautan nav menggunakan `!important` dan warna abu-abu muda. | `!important` membuat aturan lebih sulit ditimpa; warna `#cccccc` pada latar terang sulit dibaca. | Hapus `!important` dan gunakan warna dengan kontras yang memadai serta state hover/focus. |
| 8 | 8 | Teks `.content` menggunakan warna `#bbbbbb`. | Kontras teks terhadap latar putih rendah dan menyulitkan pengguna dengan gangguan penglihatan. | Gunakan warna teks gelap yang mudah dibaca. |
| 9 | 9 | `.sidebar` tidak digunakan di HTML. | Aturan CSS yang tidak terpakai menambah kebingungan dan beban pemeliharaan. | Hapus aturan yang tidak digunakan. |
| 10 | 21, 27 | Heading disimulasikan dengan inline style. | CSS bercampur dengan konten dan membuat perubahan tampilan sulit dipelihara. | Pindahkan styling ke CSS dan gunakan selector heading. |
| 11 | 22, 24, 26 | `<br>` berulang digunakan untuk mengatur jarak. | Line break bukan alat layout; jarak akan rapuh saat ukuran layar atau konten berubah. | Atur jarak dengan margin/padding CSS. |
| 12 | 25 | Gambar tidak memiliki atribut `alt`. | Pengguna pembaca layar tidak memperoleh informasi tentang gambar. | Tambahkan teks alternatif yang bermakna. |
| 13 | 28-29 | Input tidak memiliki `<label>`; placeholder saja bukan label yang memadai. | Label tidak tetap terlihat setelah pengguna mulai mengetik dan hubungan aksesibel dengan kolom tidak tersedia. | Tambahkan label dengan `for` yang cocok dengan `id` input. |
| 14 | 29 | Kolom Email menggunakan `type="text"`. | Browser tidak dapat memberikan validasi format email dan keyboard yang sesuai pada perangkat seluler. | Gunakan `type="email"`. |
| 15 | 27-30 | Kolom tidak berada di dalam elemen `<form>`. | Input tidak membentuk formulir yang dapat dikirim dengan perilaku standar HTML. | Kelompokkan kolom dan tombol di dalam `<form>`. |
| 16 | 30 | Tombol memakai `onclick` untuk menampilkan alert “Sent!”. | Pesan alert bukan pengiriman formulir, tidak memproses data, dan perilaku tercampur dengan markup. | Gunakan tombol submit dalam form; sambungkan ke endpoint saat backend tersedia. |
| 17 | 16-17 | Semua link memakai `href="#"`. | Link tidak mengarah ke bagian atau halaman yang dimaksud dan dapat mengubah posisi scroll tanpa aksi bermakna. | Gunakan tujuan nyata, seperti ID section yang ada. |
| 18 | 1-35 | Kode dirapatkan dan sulit dibaca. | Format yang buruk mempersulit review dan membuat kesalahan lebih mudah terlewat. | Terapkan indentasi konsisten dan satu elemen per baris. |

Refleksi:
1. Masalah yang paling sulit disadari hanya dari tampilan browser adalah kurangnya semantik heading dan label input. Tampilan bisa dibuat menyerupai heading dan placeholder terlihat seperti petunjuk, tetapi struktur tersebut tidak memberikan navigasi dan hubungan aksesibel yang sama.
2. Masalah ini tetap penting karena halaman juga digunakan melalui pembaca layar, keyboard, perangkat kecil, dan browser yang memvalidasi form; tampilan yang tampak baik belum menjamin pengalaman yang aksesibel atau responsif. Markup semantik dan CSS yang terpelihara juga membuat perubahan berikutnya lebih aman.
3. Sebelum mengumpulkan, saya akan menjalankan HTML melalui W3C Validator dan memeriksa halaman pada ukuran layar kecil serta dengan keyboard. Saya juga akan memeriksa label, teks alternatif, kontras, tautan, dan aturan CSS yang tidak terpakai.

## Bagian 7: Exit ticket
1. Aturan CSS terdiri dari selector yang menentukan elemen sasaran, lalu blok deklarasi di dalam kurung kurawal. Setiap deklarasi memasangkan property dengan value, misalnya `color: red;`.
2. Saya masih perlu berlatih membandingkan specificity ketika beberapa selector cocok pada elemen yang sama, terutama saat aturan berasal dari selector gabungan.
3. Saya sekarang bisa membuat selector untuk memilih elemen berdasarkan class, ID, hubungan keturunan, dan pseudo-class seperti `:hover`.
```