# Jawaban Praktikum: 
Nama    : Nisa Asiah Paujiati Sstani 
NIM     : 10224119

## Bagian 1: Pemanasan
1. 
   - **Selector**: `nav a.active:hover`
   - **Deklarasi**: `{ color: red; }`
   - **Property**: `color`
   - **Value**: `red`
   - **Pseudo-class**: `:hover` (serta `.active` sebagai class selector / pseudo-class selector)

2. 
   - **Block**: `<p>`, `<li>`, `<h2>`
   - **Inline**: `<span>`, `<a>`, `<strong>`

3. Paragraf yang menjadi hijau adalah **A** dan **B**. 
   (Sebab selector `.box p` memilih semua elemen `<p>` yang berada di dalam elemen ber-class `box`).

4. Warna teksnya adalah **merah** (`red`). 
   **Alasan**: ID selector (`#title`) memiliki nilai *specificity* paling tinggi dibanding class selector (`.heading`) dan element selector (`h1`).

5. **Kesalahan**: Terjadi kesalahan penutupan tag (*nesting tag* yang salah). Tag `<strong>` dibuka di dalam `<p>`, tetapi ditutup di luar tag `</p>`. Seharusnya dipasang berurutan: `<p>Hello <strong>world</strong></p>`.

---

## Bagian 3: Prediksi Selector Golf
**Prediksi:**
- **P1.** 
  (a) "Weekly hack nights." -> **green** (terkena aturan `section p`)
  (b) "Bring your own laptop." -> **orange** (terkena aturan `.note` karena class lebih spesifik)
  (c) "© 2026 Student Affairs" -> **blue** (terkena aturan `p` biasa)
- **P2.** Urutan specificity dari tertinggi ke terendah:
  1. `#tech p` (1 ID, 1 Element)
  2. `.club p` (1 Class, 1 Element)
  3. `main section p` (3 Elements)
  4. `p` (1 Element)

**Setelah diuji (hasil sebenarnya):**
- Hasil P1 dan P2 sesuai dengan prediksi. Spesifisitas selector dihitung berdasarkan jumlah ID, Class, dan Element yang digunakan pada aturan CSS.

---

## Bagian 4: Box model
- **Q1 (content-box):** Lebar yang terlihat = `334px`.
  - **Perhitungan**: `Width` (300px) + `Padding Left/Right` (16px + 16px) + `Border Left/Right` (1px + 1px) = 334px. (Margin tidak dihitung dalam lebar fisik elemen).
- **Q2 (border-box):** Lebar yang terlihat tetap **300px**. Padding dan border dimasukkan ke dalam total ukuran `width`, sehingga ukuran konten menyusut menjadi `266px` (300 - 32 - 2).
- **Pengecekan DevTools:**
  - Content: `928px` x `...px` (menyesuaikan area main)
  - Padding: `16px` di seluruh sisi
  - Border: `1px` di seluruh sisi
  - Margin: `0px` atas/bawah, `0px` kiri/kanan (margin-bottom: `24px`)

---

## Bagian 5: Tabel debug
| # | Baris | Bug | Perbaikan | Cara menemukannya |
|---|-------|-----|-----------|-------------------|
| 1 | 8 | `colour: #333;` salah penulisan property | Ubah menjadi `color: #333;` | Membaca kode / DevTools menyilang property |
| 2 | 11 | Kurang titik koma `;` setelah `#dbe7f3` | Tambahkan `;` di akhir baris | Membaca kode |
| 3 | 14 | Selector `.Card` menggunakan huruf kapital | Ubah menjadi `.card` (sesuai class di HTML) | Inspect DevTools / Membaca kode |
| 4 | 18 | Nilai unit `18 px` ada spasi | Hilangkan spasi menjadi `18px` | DevTools menandai invalid property |
| 5 | 22 | `text-align: centre;` ejaan salah | Ubah menjadi `text-align: center;` | DevTools menyilang property |
| 6 | 28 | Tag penutup `</h2>` tidak cocok dengan `<h1>` | Ubah `</h2>` menjadi `</h1>` | W3C Validator |
| 7 | 31 | Atribut `href="about.html>` kurang tanda kutip penutup | Ubah menjadi `href="about.html"` | W3C Validator |
| 8 | 38 | Atribut `id="newsList"` tidak sesuai CSS (`#news-list`) | Ubah id menjadi `id="news-list"` | Membaca kode |
| 9 | 36 | Tag `<img>` tidak memiliki atribut `alt` | Tambahkan `alt="Gambar berita"` | W3C Validator |

---

## Bagian 6: Tabel Code Review
| # | Baris | Masalah | Mengapa penting | Perbaikan saya |
|---|-------|---------|-----------------|----------------|
| 1 | 1 | Tidak ada `<!DOCTYPE html>` dan atribut `lang` | Mengganggu rendering browser dan SEO/Aksesibilitas | Tambahkan `<!DOCTYPE html>` dan `<html lang="id">` |
| 2 | 5 | Menggunakan lebar tetap `width: 1200px;` | Membuat tampilan tidak responsif di layar kecil | Hapus `width`, gunakan `max-width` dan layout responsif |
| 3 | 6 | Menggunakan `!important` pada CSS | Merusak hirarki spesifisitas CSS dan sulit di-maintain | Hapus `!important`, gunakan selector yang lebih presisi |
| 4 | 13-28 | Penggunaan elemen `<div>` secara berlebihan (divitis) | Tidak ada makna semantik bagi screen reader & SEO | Ganti dengan `<header>`, `<nav>`, `<main>`, `<section>`, `<footer>` |
| 5 | 14 | Menggunakan `<b>` untuk judul | Tidak semantik untuk struktur hirarki halaman | Ganti dengan `<h1>` atau `<h2>` |
| 6 | 16 | Pembatas menu menggunakan teks `|` | Kurang rapi dan membingungkan screen reader | Gunakan `<ul>` dan `<li>` ditata menggunakan Flexbox |
| 7 | 20, 24 | Menggunakan inline style `style="font-size:..."` | Menyulitkan maintenance kode dan konsistensi | Pindahkan styling ke kelas CSS |
| 8 | 21, 23 | Menggunakan `<br>` untuk membuat jarak/spasi | Tag `<br>` hanya untuk jeda baris teks, bukan layout | Gunakan `margin` atau `padding` di CSS |
| 9 | 26-28 | Kolom input form tidak memiliki `<label>` | Menyulitkan pengguna pengguna screen reader | Tambahkan tag `<label for="...">` pada tiap input |

### Refleksi:
1. Masalah yang paling sulit disadari hanya dengan melihat browser adalah penggunaan tag non-semantik (seperti `<div>` untuk seluruh elemen) dan ketiadaan atribut `<label>` pada form. Secara visual tampilan tetap terlihat baik, tetapi dari segi struktur dan aksesibilitas sangat buruk.
2. Meskipun halaman "berfungsi" di browser, masalah ini tetap penting karena memengaruhi keterbacaan kode oleh tim (*maintainability*), peringkat SEO, responsivitas di berbagai perangkat, dan aksesibilitas bagi penyandang disabilitas (*screen reader*).
3. Satu kebiasaan yang akan saya lakukan adalah selalu menguji HTML melalui **W3C Validator** dan memeriksa responsivitas layout menggunakan **DevTools** sebelum mengumpulkan tugas.

---

## Bagian 7: Exit ticket
1. Anatomi aturan CSS terdiri dari **Selector** (elemen yang dituju), diikuti oleh blok deklarasi dalam kurung kurawal `{}`. Di dalamnya terdapat satu atau lebih **Property** (sifat yang ingin diubah) dan **Value** (nilai perubahan) yang dipisahkan oleh tanda titik dua `:` serta diakhiri titik koma `;`.
2. *(Tuliskan topik yang menurutmu masih agak membingungkan, contoh: Perhitungan spesifisitas selector CSS yang kompleks).*
3. Menulis kerangka dasar HTML5 semantik beserta pembuatan form dan tabel tanpa perlu mencari contoh di internet.