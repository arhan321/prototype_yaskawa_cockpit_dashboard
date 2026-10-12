# RMS — Prototype HTML, CSS, dan JavaScript Lengkap

Prototype interaktif untuk monitoring 8 robot Yaskawa dan preventive maintenance.
Paket ini berisi seluruh source code antarmuka dan interaksi dari prototype yang dibuat pada 12 Oktober 2026.

## Cara menjalankan

1. Klik kanan ZIP, lalu pilih **Extract All / Ekstrak Semua**.
2. Buka folder **RMS_Prototype_HTML_CSS_JS** hasil ekstraksi.
3. Klik dua kali **index.html** untuk membuka prototype di browser.
4. Klik **Mode presentasi** untuk menjalankan panduan 12 langkah.

Tidak perlu install package, menjalankan npm, login, koneksi internet, atau database untuk menjalankan prototype.
Pastikan index.html, styles.css, dan app.js tetap berada di folder yang sama.

Alternatif: buka **rms-prototype-offline.html**. File ini sudah menggabungkan HTML, CSS, JavaScript, dan ikon sehingga dapat dipindahkan sendiri.

## Isi paket

| File | Kegunaan |
| --- | --- |
| index.html | Halaman utama, memuat styles.css dan app.js. |
| styles.css | Seluruh gaya visual, layout responsif, sidebar, tabel, modal, kalender, dan mode presentasi. |
| app.js | Seluruh data simulasi, render halaman, interaksi, grafik, form, ekspor CSV, dan penyimpanan lokal. |
| rms-prototype-offline.html | Versi mandiri satu file HTML untuk presentasi offline. |
| build-offline.js | Utilitas opsional untuk membuat ulang versi mandiri setelah mengedit source. |
| CARA_MENJALANKAN.txt | Petunjuk singkat dalam format teks. |
| README.md | Dokumentasi paket. |

Semua ikon, ilustrasi robot, dan grafik menggunakan SVG yang ditulis di dalam source. Tidak ada folder gambar, font, CDN, atau library tambahan yang perlu diunduh.

## Halaman dan interaksi yang tersedia

- Overview delapan robot dengan filter status serta pilihan grid/daftar.
- Robot monitor dan detail controller: mode, servo, cycle, dan koneksi.
- Grafik torque enam sumbu S, L, U, R, B, T dengan animasi simulasi.
- Posisi PULSE, operating hours, job monitoring, dan I/O read-only.
- Alarm center: pencarian, filter robot/severity, riwayat, detail, dan penandaan review.
- Preventive maintenance: interval jam, penjadwalan, kalender, dan jurnal pekerjaan.
- Downtime dan utilization: pilihan periode serta ekspor CSV.
- Notifikasi: aturan, penerima contoh, pratinjau email, dan log simulasi.
- Data & koneksi: arsitektur, processing layer, health snapshot, dan registry perangkat.
- Hardware insights: kebutuhan data investigasi tanpa klaim sisa umur komponen.
- Status pengembangan: seluruh 13 fitur pada gambar acuan.
- Mode presentasi: 12 langkah, tombol panah kiri/kanan, Esc, dan layar penuh.
- Pencarian global, layout responsif, penyimpanan lokal, dan reset data demo.

## Mengubah source code

Buka folder ini menggunakan editor kode.

- Warna dan komponen: edit **styles.css**, terutama variabel pada :root.
- Data delapan robot: edit array **robots** di **app.js**.
- Jadwal dan jurnal awal: edit **defaultTasks** dan **defaultJournal**.
- Daftar fitur: edit **capabilities**.
- Urutan/narasi presentasi: edit **tourSteps**.
- Struktur awal halaman: edit **index.html**.

Setelah menyimpan perubahan, refresh index.html di browser. Perubahan source tidak otomatis mengubah rms-prototype-offline.html.

Untuk membuat ulang versi satu file, jika Node.js tersedia, buka terminal pada folder ini dan jalankan:

```sh
node build-offline.js
```

Node.js hanya diperlukan untuk utilitas tersebut; tidak diperlukan untuk menjalankan prototype.

## Penyimpanan dan reset

Jadwal tambahan, jurnal, review alarm, aturan notifikasi, dan log uji menggunakan localStorage dengan key **rms-prototype-v1**. Data bersifat lokal pada browser/perangkat yang digunakan, tidak disinkronkan ke server. Perubahan lokal pada prototype online tidak otomatis terbawa ke paket ini.

Untuk kembali ke data awal: **Status pengembangan → Reset data demo**.
Jika browser memblokir penyimpanan pada file lokal, interaksi dapat terbatas pada sesi tersebut. Opsional, bila Python tersedia, jalankan server lokal dari folder ini:

```sh
python -m http.server 8000
```

Kemudian buka **http://localhost:8000**. Ini hanya menyajikan file lokal; bukan backend robot.

## Data demo dan batasan

Seluruh telemetry, nama station, job, IP, alarm, dan interval PM adalah contoh untuk presentasi. Paket ini berisi frontend lengkap dari prototype, belum berisi collector YMConnect C++, backend, database PostgreSQL, atau layanan SMTP production. Tidak ada perintah kontrol robot maupun email yang dikirim.

Snapshot utama: 12 Oktober 2026, 06:00–08:30. Total 1.200 robot-menit, dengan running 1.001, idle 121, stop 71, dan unknown 7. Utilization dihitung dari running / waktu terjadwal = 83,4%. Kondisi offline tidak disamakan dengan robot berhenti. Hardware life estimation tetap perlu investigasi.

## Pemeriksaan

Source HTML, CSS, JavaScript, dan file mandiri pada paket ini disalin dari versi prototype yang diterbitkan. File aplikasi diperiksa kesamaannya dengan source tersebut, sintaks JavaScript diperiksa, dan arsip ZIP diperiksa integritasnya. Pengujian logika interaksi pada pengembangan sebelumnya mencakup navigasi, detail robot, perhitungan, alarm, PM/jurnal, notifikasi, presentasi, ekspor, dan reset. Pemeriksaan visual seluruh halaman melalui browser otomatis belum dilakukan.
