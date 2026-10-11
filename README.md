# Lancar Jaya Deskprint — edisi tampilan pelanggan

Dibuat dari Prepress v0.8.0. Identitas tampilan mengikuti https://lancarjayaprinting.com/: logo resmi dari website, warna utama merah #E53935, latar putih, aksen biru dan kuning. Fungsi layout, crop/fit, duplex, preset, upload, editor dan preview tetap sama. Metadata Creator PDF memakai Lancar Jaya Deskprint; branding tidak ditambahkan ke artwork cetak.

Mac: ekstrak folder lancar-jaya-deskprint ke Documents, tutup server lama dengan Control+C, lalu jalankan:

```bash
bash ~/Documents/lancar-jaya-deskprint/Launch.command
```

Windows: jalankan Launch.bat. Python 3.11+ dan internet diperlukan saat instalasi pertama. Biarkan Terminal terbuka, lalu akses http://127.0.0.1:8700. Preset lama dipindahkan dengan menyalin config/shop_presets.json. Server ini masih lokal; belum diubah menjadi layanan hosting untuk banyak pengguna.

Internal API/header bernama Luxora dipertahankan untuk kompatibilitas dan bukan identitas yang tampil ke operator. Mesin pengolahan dan aturan keamanan/kalibrasi tidak diubah. Lakukan cetak uji fisik sebelum produksi.

---

# Lancar Jaya Deskprint v0.8.0

Semua queue terbaru sudah diterapkan:

- Kolom pengaturan kiri memanjang penuh, tanpa scrollbar terpisah. Preview kanan mengikuti scroll desktop.
- Preset ukuran toko: simpan nama, ukuran, bleed dan jenis produk; tetap bisa Custom. Quantity dan setelan mesin tidak ikut berubah. Gap dinaikkan jika kurang dari 2 x bleed.
- **Editor visual** untuk PDF/JPG/PNG: geser artwork, zoom +/−, tengah/reset, masing-masing sisi terpisah. Kotak potong mengikuti ukuran jadi + bleed.
- Dasar **Cover**: penuh dengan crop; **Utuh**: jaga rasio, boleh area kosong; **Fit**: boleh gepeng dengan kontrol lebar/tinggi terpisah. Zoom 100% mengacu dasar penempatan terpilih, bukan ukuran fisik asli file.
- Ringkasan order sebelum persetujuan unduh.
- Preview duplex 2D depan/belakang dan lembar datar 3D yang bisa diputar dengan mouse/touch/sliders. Tanda ATAS ikut berputar. Simulasi mengikuti pemetaan x/y; tetap perlu cetak fisik untuk kalibrasi.

## Jalankan di Mac

1. Tutup aplikasi lama dengan Control+C di Terminal.
2. Ekstrak ZIP, pindahkan folder **lancar-jaya-deskprint** ke Documents.
3. Jalankan:

```bash
bash ~/Documents/lancar-jaya-deskprint/Launch.command
```

Biarkan Terminal terbuka. Browser otomatis dibuka; jika tidak, buka http://127.0.0.1:8700. Pastikan **v0.8.0**. Python 3.11+ diperlukan, instalasi dependency awal perlu internet. Windows: Launch.bat.

## Coba editor dan 3D

Klik **Isi contoh**, pilih **Editor visual** di Penempatan. Pilih sisi, tarik artwork atau ubah zoom. Pilih Fit jika memang ingin mengubah rasio. Klik **Buat preview & PDF uji**, periksa ringkasan/peringatan, lalu pilih **Putar 3D**. Tombol Lihat depan/belakang memberi tampilan lurus; drag/sliders memberi sudut bebas.

Untuk file customer: isi ukuran dari order, unggah file, periksa indikator ukuran/resolusi. PDF satu file tepat dua halaman memakai mode Satu PDF. Zoom out atau geser bisa menyisakan area putih; program memberi peringatan. Crop tidak menciptakan bleed. Fit dapat merusak bentuk teks/logo/QR. Thumbnail editor bukan hasil penajaman; PDF hasil tetap memakai sumber asli.

Preview PDF dan 3D menampilkan lembar perwakilan awal/akhir; halaman tengah tetap bisa dilihat posisi 2D-nya. Program masih memakai grid satu orientasi; belum ada nesting campuran, lipatan atau kisscut otomatis. Cetak satu lembar uji sebelum produksi banyak.

## Preset toko

Isi ukuran, bleed dan produk, beri nama, lalu **Simpan sebagai preset**. Data disimpan di **config/shop_presets.json** di komputer ini, tidak di GitHub. Saat pindah versi/folder/komputer, salin file tersebut ke folder config versi baru. Preset lama dengan nama sama harus dihapus atau gunakan nama baru.

## Validasi

91 tes Python lulus, tes UI Node dan pemeriksaan browser desktop/mobile lulus. Lihat TEST_REPORT.md. Pengembangan: `python -m pytest -q`, `node tests/test_ui_geometry.js`. Tes browser opsional memerlukan Playwright/Chromium: `node tests/test_studio_browser.js`; LUXORA_PYTHON memilih interpreter dan LUXORA_CHROMIUM memilih binary bila perlu. Tes memakai artwork sintetis, bukan customer.

---
Dokumentasi versi sebelumnya di bawah adalah referensi; v0.8 dan docs/PROJECT_STATE.md berlaku saat ini.

# Lancar Jaya Deskprint v0.7.0

Tampilan Opsi A hitam–gold: pengaturan dibagi menjadi Produk & ukuran, File customer, Penempatan, dan Cetak dua sisi. Preview besar di kanan pada desktop; tampilan menyesuaikan layar kecil.

Tab **Susunan** menampilkan posisi produk. Setelah proses, tab **Hasil PDF** menampilkan artwork dari PDF hasil. Preview yang dirender hanya halaman perwakilan awal/akhir; halaman lainnya menampilkan susunan dengan keterangan yang jelas. Warna tema tidak mengubah artwork customer. Pengaturan yang diedit membatalkan hasil dan persetujuan unduh sebelumnya.

Semua fitur v0.6 tetap tersedia: pilihan produk, rotasi yang menukar ukuran, indikator ukuran/kualitas, PDF dua halaman depan/belakang, Exact/Cover/Manual/Fit, koreksi orientasi belakang, dan batas 200 MiB/file. Layout campuran rotasi belum tersedia.

## Jalankan di Mac

1. Tutup server versi lama dengan Control+C di Terminal.
2. Ekstrak ZIP dan pindahkan folder **luxora-prepress-v07** ke Documents.
3. Buka Terminal dan jalankan:

```bash
bash ~/Documents/luxora-prepress-v07/Launch.command
```

Python 3.11+ diperlukan; instalasi dependency pertama memerlukan internet. Biarkan Terminal terbuka. Browser otomatis dibuka; jika tidak, buka http://127.0.0.1:8700. Pastikan label aplikasi **v0.7.0**. Windows: Launch.bat.

70 tes Python, tes UI Node, serta pemeriksaan browser desktop/mobile lulus. Coba tombol **Isi contoh** untuk memeriksa alur; periksa satu lembar cetak fisik sebelum produksi banyak.

---
Dokumentasi versi sebelumnya di bawah adalah referensi. Bagian v0.7 dan docs/PROJECT_STATE.md berlaku untuk versi ini.

# Lancar Jaya Deskprint v0.6.0

Pilihan produk: stiker, kartu nama, ID card, flyer, brosur, placemat, thank you card, paper belt, custom. Masing-masing memberi panduan; ukuran order tetap diisi/dipilih secara eksplisit. Jenis produk tercatat di catatan JSON.

Duplex: orientasi belakang kini dijelaskan terpisah dari pemetaan posisi. Jika hasil depan/belakang berlawanan arah, gunakan tombol koreksi untuk mengganti 0° ↔ 180°, pertahankan setelan driver/pemetaan yang sebelumnya, lalu cetak satu lembar uji. Ini bukan bukti kalibrasi mesin; posisi dan arah perlu diperiksa pada hasil fisik.

Pilihan produk belum mengaktifkan layout campuran rotasi, jalur kisscut, panel brosur, atau penjilidan otomatis. Mesin layout masih grid satu desain persegi panjang per sisi. Batas 200 MiB tetap berlaku.

Mac: tutup aplikasi lama dengan Control+C. Ekstrak folder luxora-prepress-v06 ke Documents, lalu jalankan:

```bash
bash ~/Documents/luxora-prepress-v06/Launch.command
```

Cek http://127.0.0.1:8700/health untuk version 0.6.0. Windows: Launch.bat.

70 tes Python dan tes UI Node diperiksa untuk versi ini; lihat TEST_REPORT.md.

---
Dokumentasi versi sebelumnya disimpan sebagai referensi. Bagian terbaru dan docs/PROJECT_STATE.md adalah yang berlaku.

# Lancar Jaya Deskprint v0.5.0

1. Rotasi 90°/270° kini menukar angka pada kolom lebar/tinggi. Indikator file juga menampilkan dimensi setelah rotasi; kapasitas tetap dihitung ulang.
2. Pilih sumber **Satu PDF — halaman 1 depan, halaman 2 belakang**, lalu unggah PDF tepat 2 halaman. Mode dua sisi aktif, upload belakang terpisah disembunyikan. Preview dan manifest menunjukkan pasangan kedua sisi. Ukuran tiap halaman diperiksa; tidak ditebak.
3. File terpisah tetap tersedia. Exact, Cover, Manual Crop, Fit dan indikator kualitas tetap didukung seperti v0.3.

Contoh gabungan sintetis: `examples/synthetic/front-back-2-pages.pdf`.

Mac: tutup aplikasi lama dengan Control+C, ekstrak folder `luxora-prepress-v04` ke Documents lalu jalankan:

```bash
bash ~/Documents/luxora-prepress-v04/Launch.command
```

Windows: jalankan Launch.bat. Cek http://127.0.0.1:8700/health: version 0.5.0.

68 tes Python dan tes UI/geometry Node lulus. Node hanya untuk tes pengembangan; aplikasi tidak memerlukan Node. Periksa preview dan satu lembar fisik sebelum produksi banyak.

---
Dokumentasi versi sebelumnya di bawah adalah referensi instalasi. Fitur versi terbaru di atas dan docs/PROJECT_STATE.md adalah yang berlaku.

# Lancar Jaya Deskprint v0.3.0

Tambahan:
- Rotasi produk/artwork 0°, 90°, 180°, 270°. Kedua sisi ikut diputar; 90°/270° menukar ukuran layout dan menghitung ulang kapasitas.
- Ukuran file muncul setelah unggah: PDF mm, JPG/PNG piksel, ukuran dari DPI jika tersedia, acuan ukuran pada 300 ppi, dan ppi efektif pada ukuran cetak.
- Tombol menyesuaikan tinggi berdasarkan rasio file depan; lebar dipertahankan. Periksa ukuran jadi setelah perubahan.
- Mode Fit untuk PDF/JPG/PNG: mengisi ukuran tanpa crop, boleh mengubah rasio. Exact tetap default. Cover dan Manual Crop untuk raster tetap tersedia.

Fit dapat mengubah bentuk teks/logo/QR. Resolusi 300 ppi adalah indikator, bukan jaminan gambar tajam. File tanpa metadata DPI tidak punya ukuran mm asli yang pasti. Bleed tidak dibuat/divalidasi otomatis.

Mac: ekstrak folder baru `luxora-prepress-v03` ke Documents. Jalankan `bash ~/Documents/luxora-prepress-v03/Launch.command`. Windows: jalankan Launch.bat. Tutup server lama dengan Control+C sebelum menjalankan baru. Cek http://127.0.0.1:8700/health: version 0.3.0.

55 tes lulus; lihat TEST_REPORT.md. Mulai dari docs/PROJECT_STATE.md, PRINT_RULES.md, TEST_CASES.md dan TOKEN_POLICY.md. Sebelum produksi banyak, periksa preview dan satu lembar cetak fisik.

---
Dokumentasi versi terdahulu di bawah dipertahankan untuk referensi instalasi. Ketentuan fitur di atas dan docs/PROJECT_STATE.md adalah yang berlaku saat ini.

# Update v0.2.0

Penempatan JPG/PNG: **Exact** (default), **Cover** (crop tengah), **Manual Crop** (posisi 0–100% depan/belakang, tanpa zoom). Semua menjaga rasio; ukuran jadi tetap sesuai order. PDF tetap memakai Exact. Periksa preview, teks/QR, bleed dan satu lembar cetak fisik.

Mulai dari `docs/PROJECT_STATE.md`, `PRINT_RULES.md`, `TEST_CASES.md`, `TOKEN_POLICY.md`. Struktur kode tetap mengikuti v0.1 agar perubahan ini terbatas.

Bagian di bawah merupakan dokumentasi baseline v0.1; pernyataan bahwa crop tidak tersedia sudah digantikan oleh update di atas.

# Lancar Jaya Deskprint

**Versi 0.1.0 - prototipe lokal untuk uji, bukan perangkat produksi terkalibrasi.**

Aplikasi browser lokal untuk menyusun satu desain berulang pada lembar cetak.
Kode disimpan di repository GitHub private; aplikasi berjalan di komputer kerja.
Tidak membutuhkan API key, layanan AI, akun cloud, Node.js, atau server berbayar.
File customer tidak dikirim ke GitHub maupun layanan pihak ketiga oleh aplikasi.

## Mulai sekarang

Prasyarat: Python 3.11 atau lebih baru. Instalasi dependency pertama memerlukan internet.

- **Windows:** ekstrak folder, klik dua kali `Launch.bat`.
- **macOS:** ekstrak folder, buka Terminal di folder itu, jalankan `sh Launch.command`.
- **Linux:** jalankan `sh Launch.command` di folder proyek.

Aplikasi membuka `http://127.0.0.1:8700` di browser. Biarkan Terminal tetap berjalan;
`Ctrl+C` menghentikan aplikasi. Server hanya mendengarkan alamat loopback komputer.
Jangan mengganti bind address menjadi `0.0.0.0` atau menerbitkan server ini ke internet.

Alternatif manual:

```sh
python3 -m venv .venv
. .venv/bin/activate
python -m pip install -r requirements.txt
python app.py
```

Windows: aktivasi dengan `.venv\Scripts\activate` dan gunakan `py -3` saat membuat venv.
Bila port terpakai, jalankan `python app.py --port 8701`.

## Tes pertama tanpa file customer

Klik **Isi contoh 36 kartu**, lalu **Buat preview & PDF uji**.
Contoh dibuat dari desain sintetis: file 58 x 89 mm termasuk bleed 2 mm,
ukuran jadi 54 x 85 mm. Hasil: 24 kartu pada lembar pertama dan 12 pada lembar
kedua; dua sisi menghasilkan empat halaman PDF berurutan.
Area kosong belakang dipetakan dari posisi depan menurut sumbu balik yang dipilih.
Tidak ada artwork customer yang disertakan dalam proyek.

Setelah memeriksa preview, centang persetujuan uji untuk menyimpan PDF dan catatan JSON.
PDF berlabel **UJI**. Print actual size / 100%, copies=1, gunakan satu lembar uji
untuk mengecek arah balik, registrasi, ukuran dan hasil potong sebelum produksi.
Jangan memakai "Fit" dan jangan menggandakan copies berdasarkan jumlah lembar:
seluruh lembar pekerjaan sudah diperluas di dalam PDF.

## Fitur yang benar-benar tersedia

- PDF satu halaman per sisi, JPG dan PNG, maksimal 200 MiB (209.715.200 byte) per file.
- Ukuran jadi dan jumlah bebas dalam batas prototipe; grid satu ukuran/satu orientasi.
- Kertas awal 485 x 325 mm, area cetak 480 x 320 mm; preset portrait untuk placemat.
- Posisi area cetak dapat diubah. Default kiri/atas 2,5 mm **hanya asumsi di tengah**.
- Bleed, jarak antarbatas potong, dan tanda potong memakai ukuran mm.
- Penghitungan ruang sudah mencakup bleed, stroke tanda, jarak tanda, dan label.
- Lembar terakhir boleh kosong sebagian. Tidak menambah jumlah produk diam-diam.
- Duplex: refleksi koordinat kiri-kanan / atas-bawah, putaran artwork belakang opsional 180.
- Pemeriksaan ukuran sumber; mismatch dihentikan, bukan di-stretch/crop otomatis.
- Penempatan konten PDF tanpa merasterkan seluruh halaman menjadi JPG.
- Preview PDF hasil render, catatan koordinat/hash sumber/pemakaian/tagihan terpisah.
- Halaman output urutan depan 1, belakang 1, depan 2, belakang 2. Semua halaman dicetak sekali.
- File diproses di memori server lokal. Tidak ada arsip pekerjaan permanen otomatis.

Jumlah tagihan `0` berarti mengikuti jumlah kertas. Nilai khusus tidak mengubah
jumlah produk. Cadangan, lembar kalibrasi, waste dan ongkos belum dihitung.
Tanda potong seluruh grid tetap ada di lembar parsial agar pola potong konsisten.

## Batas penting sebelum memakai file asli

1. **Bleed belum dibuat otomatis.** Dengan trim 54 x 85 mm dan bleed 2 mm,
   halaman sumber harus 58 x 89 mm. File 54 x 85 mm ditolak pada setelan itu.
   Pilihan bleed=0 hanya untuk pekerjaan yang memang tidak memerlukan bleed
   atau untuk uji, bukan cara menyelesaikan kebutuhan bleed produksi.
2. **Garis biru/tanda potong customer tidak dihapus.** Trim yang dimaksud harus
   diperiksa manual. Aplikasi memakai CropBox halaman sebagai batas artwork;
   belum ada pemilihan trim/bleed box otomatis atau crop editor.
3. **Belum ada validasi produksi lengkap:** ICC/CMYK/PDF-X, font, overprint,
   transparansi, gamut, QR dan resolusi objek gambar di dalam PDF belum diaudit.
   Resolusi efektif hanya dilaporkan untuk input JPG/PNG. Tidak ada konversi warna otomatis.
4. **Registrasi fisik belum dikalibrasi.** Label nama driver long-edge/short-edge
   tidak dipetakan otomatis. Simulasi memakai koordinat file, bukan jaminan hasil mesin.
5. PDF dengan password, anotasi/form/link, UserUnit khusus, atau optional layers
   ditolak agar penanganannya tidak diam-diam menghilangkan atau mengubah konten.
6. Maksimal 1.500 produk, 500 posisi per lembar, 100 halaman PDF. Belum ada mixed-size
   nesting, booklet, penomoran variabel, banyak desain, cut contour atau finishing lipat.
7. Ini server pengembangan lokal, belum sandbox pemrosesan dokumen untuk layanan
   publik. File rusak/kompleks dapat menghabiskan waktu atau RAM. Jangan unggah file
   yang mencurigakan; proses terisolasi dan timeout merupakan pekerjaan berikutnya.
8. Dependency dikunci ke snapshot pengujian; ini bukan audit keamanan atau klaim
   versi paling baru. Tinjau pembaruan keamanan dan jalankan tes saat upgrade.

## Tempat mengubah kode

| File | Tugas |
| --- | --- |
| `engine.py` | Validasi parameter, hitung grid, pemetaan duplex, gabung PDF, marks |
| `app.py` | API lokal dan pembatasan request/asal akses |
| `templates/index.html` | Struktur layar/form |
| `static/style.css` | Tampilan dan responsif |
| `static/app.js` | Interaksi, simulasi grid, upload dan unduhan |
| `demo.py` | Desain sintetis untuk pengujian |
| `tests/` | Tes perhitungan, penolakan input, PDF dan API |

Edit HTML/CSS/JS, lalu refresh browser. Edit Python, hentikan dengan Ctrl+C lalu
jalankan lagi. Input pengaturan belum dipersistenkan saat halaman di-refresh.

Tes:

```sh
python -m pip install -r requirements-dev.txt
python -m pytest -q
```

Jangan mengubah hasil tes supaya implementasi yang salah terlihat lulus.
Untuk kasus baru: tambahkan tes ukuran/posisi/jumlah yang diinginkan terlebih dahulu,
kemudian ubah logika sampai tes lama dan baru sama-sama lulus.

## Masukkan ke GitHub

Buat repository baru bernama `luxora-prepress`, visibility **Private**.
Jangan menggunakan repository website lama dan jangan mengaktifkan GitHub Pages.
Repository hanya menyimpan kode, bukan file customer atau hasil cetaknya.

Cara mudah: buat repository dengan README, lalu gunakan GitHub Desktop untuk clone.
Salin isi folder proyek ke folder clone (termasuk `.gitignore` dan `.github`),
review daftar perubahan, commit lalu push. README bawaan boleh diganti README ini.
Jangan menyeret file ZIP sebagai satu file ke repository; yang diperlukan adalah
isi source code-nya. Bila koneksi GitHub ChatGPT dibatasi ke selected repositories,
berikan akses ke repository baru tersebut untuk bisa melakukan perubahan dari chat.

Alur harian: minta perubahan -> buat branch -> jalankan tes -> tinjau perubahan
-> merge -> ambil kode terbaru di komputer. Workflow CI tersedia untuk menjalankan
tes pada push/pull request; CI belum dijalankan di akun GitHub Anda.

## Arah pengembangan berikutnya

Utamakan kalibrasi mesin/duplex, trim/bleed editor dengan persetujuan eksplisit,
preflight warna/font/resolusi, dan riwayat pekerjaan. Sesudah itu baru batch,
manual placement, campur beberapa desain, dan akses banyak operator.

Referensi implementasi:
- https://pypdf.readthedocs.io/en/stable/user/cropping-and-transforming.html
- https://fastapi.tiangolo.com/
- https://pypdfium2.readthedocs.io/en/stable/
- https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-new-repository
