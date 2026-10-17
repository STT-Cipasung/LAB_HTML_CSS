# Jawaban Praktikum: <Ridho> (<10224009>)

## Bagian 1: Pemanasan
1.Selector: nav a.active:hover. Deklarasi: color: red;. Property: color. Value: red. Pseudo-class: :hover.
2.Block: p, li, h2. Inline: span, a, strong.
3.Paragraf yang menjadi hijau adalah A dan B, karena keduanya berada di dalam elemen dengan class box. Selector .box p memilih semua paragraf yang merupakan keturunan elemen tersebut.
4.Warnanya merah karena selector #title memiliki specificity lebih tinggi daripada .heading dan h1.
5.Urutan penutupan tag salah. Tag <strong> harus ditutup sebelum </p>. Perbaikan: <p>Hello <strong>world</strong></p>.

## Bagian 3: Prediksi Selector Golf
P1.(a) "Weekly hack nights." = hijau, karena cocok dengan section p. (b) "Bring your own laptop." = oranye, karena cocok dengan .note, yang memiliki specificity lebih tinggi daripada section p. (c) "© 2026 Student Affairs" = biru, karena hanya cocok dengan selector p.
P2.
1.#tech p
2..club p
3.main section p
4.p
Setelah diuji (hasil sebenarnya): (a) Hijau. (b) Oranye. (c) Biru.

## Bagian 4: Box model
Q1 (content-box): lebar terlihat = lebar content + padding kiri/kanan + border kiri/kanan = 300px + (16px x 2) + (1px x 2) = 334px. Margin 24px di setiap sisi menambah jarak luar, bukan lebar kartu dari tepi border ke tepi border.
Q2 (border-box): lebar total dari tepi border ke tepi border menjadi 300px, karena nilai width sudah mencakup content, padding, dan border. Lebar content menjadi 300px - 32px - 2px = 266px. Margin tetap berada di luar lebar 300px.
Pengecekan DevTools: section #programs pada viewport 605 x 537px. Content: 539.333px; padding: 16px pada setiap sisi; border: 0.667px pada setiap sisi menurut computed style browser (deklarasi CSS 1px); margin: 0px atas/kiri/kanan dan 24px bawah. Nilai lebar content bergantung pada lebar viewport.

## Bagian 5: Tabel debug
| # | Baris | Bug | Perbaikan | Cara menemukannya |
|---|-------|-----|-----------|-------------------|
| 1 | 9 | Property `colour` tidak dikenal di CSS. | Ganti menjadi `color`. | DevTools menampilkan deklarasi yang tidak valid/tidak diterapkan. |
| 2 | 12 | Deklarasi `background` tidak diakhiri titik koma, sehingga deklarasi berikutnya ikut gagal dibaca. | Tambahkan `;` setelah `#dbe7f3`. | Membaca kode dan memeriksa aturan CSS di DevTools. |
| 3 | 15 | Selector `.Card` tidak cocok dengan class HTML `card` karena nama class peka huruf besar-kecil. | Samakan menjadi `.card`. | Membandingkan selector CSS dengan atribut `class` di HTML. |
| 4 | 20 | Spasi pada `18 px` membuat nilai `font-size` tidak valid. | Tulis `18px`. | DevTools Computed tidak menunjukkan ukuran font 18px dari aturan ini. |
| 5 | 23 | Nilai `centre` bukan nilai CSS yang valid untuk `text-align`. | Ganti menjadi `center`. | DevTools menandai deklarasi sebagai tidak valid/tidak diterapkan. |
| 6 | 29 | Elemen `<h1>` ditutup dengan tag `</h2>`. | Tutup dengan `</h1>`. | Validator HTML melaporkan penutupan elemen heading yang tidak cocok. |
| 7 | 32 | Atribut `href` pada tautan About tidak memiliki tanda kutip penutup. | Gunakan `href="about.html"`. | Validator HTML atau membaca struktur atribut. |
| 8 | 37 | Gambar tidak memiliki atribut `alt`. | Tambahkan teks alternatif yang menjelaskan gambar. | Validator aksesibilitas/HTML melaporkan atribut alt yang hilang. |
| 9 | 38 | `id="newsList"` tidak cocok dengan selector CSS `#news-list`. | Samakan ID menjadi `news-list`. | Membandingkan selector CSS dengan atribut `id` di HTML. |

## Bagian 6: Tabel Code Review
| # | Baris | Masalah | Mengapa penting | Perbaikan saya |
|---|-------|---------|-----------------|----------------|
| 1 | 1 | Tidak ada `<!DOCTYPE html>`. | Browser dapat memakai quirks mode sehingga perilaku layout berbeda. | Tambahkan doctype HTML5 di awal dokumen. |
| 2 | 1 | Elemen `<html>` tidak memiliki atribut bahasa. | Pembaca layar dan alat bahasa tidak dapat menentukan bahasa utama halaman. | Tambahkan `lang="en"`. |
| 3 | 2-3 | Metadata charset dan viewport tidak tersedia. | Encoding karakter dan tampilan perangkat mobile tidak dinyatakan dengan benar. | Tambahkan `<meta charset="UTF-8">` dan meta viewport. |
| 4 | 13-21, 33 | Struktur halaman dibangun dari `<div>`, bukan landmark semantik. | Landmark membantu navigasi pembaca layar dan membuat tujuan bagian dokumen jelas. | Gunakan `<header>`, `<nav>`, `<main>`, `<section>`, dan `<footer>`. |
| 5 | 14, 22, 28 | Nama kampus dan judul bagian dibuat dengan `<div>`/`<b>`, bukan heading. | Struktur outline tidak menunjukkan hierarki judul kepada pembaca layar dan alat bantu. | Gunakan satu `<h1>` lalu `<h2>` untuk bagian. |
| 6 | 16-18 | Semua tautan memakai `href="#"` tanpa tujuan konten. | Tautan tidak membawa pengguna ke halaman atau bagian yang dijanjikan. | Hubungkan tautan ke URL atau ID section yang benar. |
| 7 | 5 | Header memiliki lebar tetap `1200px`. | Lebarnya melampaui layar kecil dan dapat menyebabkan scroll horizontal. | Hapus lebar tetap dan batasi konten dengan `max-width` responsif. |
| 8 | 6 | Deklarasi warna nav memakai `!important`. | Sulit ditimpa dan membuat cascade makin sukar dirawat. | Hapus `!important` dan atur prioritas selector secara wajar. |
| 9 | 7 | Warna teks `#bbbbbb` pada latar putih memiliki kontras rendah. | Teks kecil sulit dibaca dan tidak memenuhi kontras aksesibilitas. | Gunakan warna teks yang lebih gelap dan uji rasio kontras. |
| 10 | 8 | Selector `.sidebar` tidak digunakan dan tidak ada elemen sidebar. | CSS mati menambah kebingungan saat halaman dirawat. | Hapus aturan yang tidak dipakai atau implementasikan sidebar bila memang diperlukan. |
| 11 | 22, 28 | Gaya heading ditulis inline dan diulang. | Presentasi bercampur dengan konten serta sulit diubah konsisten. | Pindahkan aturan ke stylesheet dan gunakan selector heading. |
| 12 | 23, 25, 27 | `<br>` dipakai untuk membuat jarak antarbagian. | Line break menyatakan pemenggalan teks, bukan jarak layout; hasilnya rapuh. | Atur jarak dengan margin/padding CSS. |
| 13 | 26 | Gambar tidak memiliki teks alternatif. | Pengguna pembaca layar kehilangan informasi gambar. | Tambahkan `alt` yang menjelaskan gambar. |
| 14 | 29-30 | Input tidak memiliki label dan hanya mengandalkan placeholder. | Placeholder hilang saat diketik dan bukan pengganti nama aksesibel yang tetap terlihat. | Tambahkan `<label for>` yang terhubung ke ID masing-masing input. |
| 15 | 30 | Kolom Email menggunakan `type="text"`. | Browser tidak dapat memberi validasi dan keyboard email yang sesuai. | Gunakan `type="email"`. |
| 16 | 29-31 | Kontrol tidak berada dalam `<form>`; tombol menjalankan inline `onclick` yang hanya menampilkan alert. | Data tidak dikirim sebagai formulir, perilaku tidak terpisah dari markup, dan tombol tidak memiliki tipe eksplisit. | Bungkus field dalam `<form>`, beri `name`, lalu gunakan tombol `type="submit"` tanpa inline JavaScript. |

Refleksi:
1. Yang paling sulit disadari hanya dari tampilan adalah struktur semantik yang semuanya dibuat dengan `<div>`. Secara visual halaman masih bisa tampak sama, tetapi navigasi landmark dan hierarki heading bagi pembaca layar menjadi hilang.
2. Halaman yang terlihat berfungsi tetap dapat menyulitkan pengguna keyboard atau pembaca layar, gagal di layar kecil, dan susah dikembangkan. Masalah semantik, kontras, dan struktur formulir baru terasa saat kondisi penggunaan berbeda dari pengujian visual biasa.
3. Sebelum dikumpulkan, saya akan memeriksa struktur dengan validator HTML dan meninjau halaman pada ukuran layar kecil. Saya juga akan menguji navigasi keyboard, label formulir, serta kontras teks.

## Bagian 7: Exit ticket
1. Aturan CSS terdiri dari selector yang memilih elemen, lalu blok deklarasi di dalam kurung kurawal. Setiap deklarasi memasangkan property dengan value, misalnya `color: navy;`.
2. Saya masih ingin lebih lancar memahami specificity dan cascade ketika beberapa selector yang berbeda sama-sama cocok pada satu elemen. Saya perlu lebih banyak latihan menentukan aturan mana yang akhirnya diterapkan.
3. Saya sekarang bisa menyusun halaman dengan elemen semantik, menghubungkan label ke input, dan membuat navigasi horizontal dengan flexbox tanpa perlu mencari contoh terlebih dahulu.