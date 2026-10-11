# Rencana Build Website NxNode

## Masalah

`website.md` di root proyek berisi materi konten landing page (dwibahasa ID/EN), tetapi belum ada
website nyata yang bisa dibuka di browser. Tujuan: mengubah materi itu menjadi landing page statis
yang siap dilihat.

## Keputusan Desain

- **Stack:** HTML + CSS + JS statis murni (tanpa framework, tanpa dependency baru). Selaras aturan
  proyek "gunakan JavaScript murni / jangan tambah dependency jika bisa tanpa itu".
- **Switch bahasa ID/EN:** mengikuti pola website `D:\CLI\nxdom\` — atribut `data-i18n` pada elemen,
  tombol `data-lang-btn="id"` / `"en"`, kamus `I18N` di `index.js`, disimpan di `localStorage`
  (kunci `nxnode-lang`), plus `data-i18n-attr` untuk atribut seperti `<meta name="description">`.
  Bahasa awal mengikuti preferensi tersimpan, lalu `navigator.language` (default `id`).
- **Tema:** gelap, aksen hijau NxNode, kartu fitur, blok terminal, tabel perintah, FAQ accordion
  (`<details>`).
- **Sumber konten:** seluruh teks diambil dari `website.md` (hero, masalah/solusi, fitur, cara kerja,
  demo terminal, referensi perintah, mode linking, konfigurasi, integrasi, kompatibilitas, FAQ, CTA).

## Perubahan File

- `website/README.md` — dokumen rencana ini.
- `website/index.html` — struktur landing page; teks dwibahasa lewat `data-i18n`.
- `website/index.js` — kamus `I18N` (ID/EN) + logika `setLang()` dan tombol bahasa.
- `website/styles.css` — seluruh gaya tampilan, termasuk `.lang-switch` (tombol ID/EN).
- `website/serve.js` — server statis opsional untuk uji lokal (tidak wajib).

## Langkah

1. Buat folder `website/`.
2. Tulis `index.html` (sesuai section di `website.md`, atribut `data-i18n`).
3. Tulis `index.js` (kamus ID/EN + switch bahasa).
4. Tulis `styles.css` (layout, hero, grid fitur, terminal, tabel, FAQ, footer, tombol bahasa).
5. Verifikasi: buka `index.html`, cek tombol ID/EN berganti seluruh teks.

## Status

✅ SUDAH DIEKSEKUSI — `index.html`, `index.js`, dan `styles.css` sudah dibuat; switch bahasa ID/EN
memakai pola `data-i18n` seperti contoh `D:\CLI\nxdom\`.
