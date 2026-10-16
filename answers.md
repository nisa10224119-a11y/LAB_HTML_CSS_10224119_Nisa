# Jawaban Praktikum: <Nama> (<NIM>)

## Bagian 1: Pemanasan

1. **Anatomi aturan CSS `nav a.active:hover { color: red; }`:**
   - **Selector:** `nav a.active:hover`
   - **Pseudo-class:** `:hover` (dan `.active` adalah class selector)
   - **Deklarasi:** `{ color: red; }`
   - **Property:** `color`
   - **Value:** `red`

2. **Sifat default elemen:**
   - **Block:** `<p>`, `<h2>`, `<li>`
   - **Inline:** `<span>`, `<a>`, `<strong>`

3. **Jawaban:** **A** dan **B**.
   - *Penjelasan:* Selector `.box p` memilih semua elemen `<p>` yang berada di dalam elemen ber-class `box` (descendant selector), baik anak langsung maupun keturunan berikutnya. Paragraf C memiliki class `box` (bukan di dalam), sedangkan D berada di luar `.box`.

4. **Warnanya: Merah (`red`).**
   - *Penjelasan:* ID selector (`#title`) memiliki nilai *specificity* paling tinggi (1-0-0) dibandingkan Class selector (`.heading`, specificity 0-1-0) dan Tag selector (`h1`, specificity 0-0-1). Rule dengan specificity tertinggi yang akan diterapkan.

5. **Kesalahan:** Tag saling bertabrakan/tumpang tindih (*overlapping tags / improper nesting*).
   - *Perbaikan:* `<p>Hello <strong>world</strong></p>` (tag `<strong>` harus ditutup sebelum tag `<p>` ditutup).

---

## Bagian 3: Prediksi Selector Golf

- **P1. Prediksi awal:**
  - (a) "Weekly hack nights.": **green** (karena dipilih oleh `section p`)
  - (b) "Bring your own laptop.": **orange** (karena dipilih oleh `.note` yang memiliki class specificity lebih tinggi)
  - (c) "© 2026 Student Affairs": **blue** (pilihan default `p` karena berada di footer, bukan di dalam section)

- **P2. Urutan specificity (tertinggi ke terendah):**
  1. `#tech p` (1 ID, 1 Element -> 1-0-1)
  2. `.club p` (1 Class, 1 Element -> 0-1-1)
  3. `main section p` (3 Elements -> 0-0-3)
  4. `p` (1 Element -> 0-0-1)

- **Setelah diuji (hasil sebenarnya):**
  - Prediksi P1 dan P2 100% tepat dan terbukti sesuai dengan aturan specificity di CSS.

---

## Bagian 4: Box Model

- **Q1 (content-box):**
  - Lebar yang terlihat (*visible width*) = `width` + `padding-left` + `padding-right` + `border-left-width` + `border-right-width`
  - Perhitungan: $300\text{px} + 16\text{px} + 16\text{px} + 1\text{px} + 1\text{px} = \mathbf{334\text{px}}$.

- **Q2 (border-box):**
  - Lebar total yang terlihat tetap tepat **300px**. Browser secara otomatis menyesuaikan lebar konten (*content width*) menjadi $300\text{px} - 32\text{px} - 2\text{px} = 266\text{px}$.

- **Pengecekan DevTools:**
  - Content: 926px × (tinggi elemen)
  - Padding: 16px (top, right, bottom, left)
  - Border: 1px (top, right, bottom, left)
  - Margin: 0px top/bottom (atau 24px bottom), auto di left/right.

---

## Bagian 5: Tabel Debug

| # | Baris | Bug | Perbaikan | Cara Menemukannya |
|---|-------|-----|-----------|-------------------|
| 1 | 9 | Penulisan property salah (`colour`) | Ganti menjadi `color` | DevTools (property tidak dikenali / invalid) |
| 2 | 12 | Titik koma hilang setelah `#dbe7f3` | Tambahkan `;` di akhir baris | Membaca kode / Syntax highlighter |
| 3 | 15 | Case-sensitivity class CSS (`.Card` vs `class="card"`) | Ubah `.Card` menjadi `.card` | Membaca kode (perbandingan CSS dan HTML) |
| 4 | 19 | Spasi antara angka dan satuan (`18 px`) | Ubah menjadi `18px` | DevTools (value invalid) |
| 5 | 22 | Ejaan property salah (`text-align: centre`) | Ubah `centre` menjadi `center` | DevTools / CSS Validator |
| 6 | 27 | Penutup tag tidak cocok (`<h1>...</h2>`) | Ubah `</h2>` menjadi `</h1>` | W3C HTML Validator |
| 7 | 30 | Tanda petik penutup hilang pada atribut href (`"about.html>`) | Ubah menjadi `href="about.html"` | W3C HTML Validator |
| 8 | 35 | Tag `<img>` tidak memiliki atribut `alt` | Tambahkan `alt="News Image"` | W3C HTML Validator |
| 9 | 36 | Mismatch ID antara HTML (`id="newsList"`) dan CSS (`#news-list`) | Ubah ID di HTML jadi `news-list` atau di CSS jadi `#newsList` | Membaca kode / DevTools |

---

## Bagian 6: Tabel Code Review

| # | Baris | Masalah | Mengapa Penting | Perbaikan Saya |
|---|-------|---------|-----------------|----------------|
| 1 | 1 | Tag `<!DOCTYPE html>` dan atribut `lang="id"` tidak ada | Browser bisa masuk ke *Quirks Mode* dan merusak rendering | Tambahkan `<!DOCTYPE html><html lang="id">` |
| 2 | 10-22 | Penggunaan `<div>` berlebihan (*divsoup*) tanpa elemen semantik | Merusak aksesibilitas (screen reader) dan struktur SEO | Ganti dengan `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<footer>` |
| 3 | 5 | Penggunaan `!important` pada CSS | Menyulitkan pemeliharaan kode (*code maintenance*) dan merusak *cascade* | Hapus `!important`, perbaiki selector specificity |
| 4 | 4 | Fixed width `width: 1200px` pada header | Membuat layout tidak responsif di layar kecil/HP | Gunakan `max-width: 1200px; width: 100%;` |
| 5 | 11, 18 | Tidak menggunakan heading semantik (`<h1>`-`<h6>`), hanya `<div>` yang dibold | Screen reader tidak bisa mengenali hierarki struktur dokumen | Gunakan `<h1>` untuk nama kampus dan `<h2>` untuk judul section |
| 6 | 13 | Menggunakan pemisah Teks `|` pada navigasi | Mengganggu pembacaan *screen reader* | Gunakan daftar semantik `<ul>` / `<li>` styled dengan Flexbox |
| 7 | 18, 20 | Menggunakan `<br>` untuk mengatur jarak layout | `<br>` hanya untuk perpindahan baris kalimat, bukan spasi layout | Gunakan `margin` atau `padding` CSS |
| 8 | 21 | Tag `<img>` tidak memiliki atribut `alt` | Aksesibilitas buruk bagi tunanetra dan gambar tidak punya teks alternatif saat error | Tambahkan atribut `alt` yang deskriptif |
| 9 | 23-25 | Elemen form (`<input>`) tidak menggunakan `<label>` | Pengguna tidak tahu fungsi input secara pasti & buruk untuk aksesibilitas | Bungkus/hubungkan dengan atribut `<label for="...">` |

### Refleksi

1. **Masalah yang paling sulit disadari:** Penggunaan elemen non-semantik (seperti `<div>` sebagai ganti `<header>` atau `<h2>`). Halaman terlihat normal di browser desktop, tetapi struktur datanya rusak bagi *screen reader* dan mesin pencari.
2. **Mengapa penting diperbaiki:** Kode yang sekadar "berfungsi" belum tentu aksesibel, responsif, ramah SEO, atau mudah dirawat oleh tim developer di masa depan.
3. **Kebiasaan sebelum mengumpulkan:** Selalu menjalankan kode melalui W3C Markup Validator dan melakukan pengujian *DevTools audit/accessibility* serta pengujian di berbagai ukuran layar.

---

## Bagian 7: Exit Ticket

1. **Anatomi aturan CSS:** Terdiri dari **Selector** (elemen yang ditargetkan), dibuka dengan kurung kurawal `{}` yang berisi satu atau lebih **Deklarasi**. Setiap deklarasi terdiri dari **Property** (sifat yang diubah) dan **Value** (nilai perubahan), diakhiri dengan titik koma `;`.
2. **Konsep yang masih membingungkan:** Menghitung nilai spesifik *Specificity* pada kombinasi pseudo-class dan attribute selector yang kompleks.
3. **Hal yang bisa dilakukan tanpa melihat catatan:** Membuat struktur dasar dokumen HTML5 (`<!DOCTYPE html>`, `<head>`, `<body>`), menggunakan tag semantik dasar, dan mengatur layout horizontal sederhana menggunakan Flexbox.