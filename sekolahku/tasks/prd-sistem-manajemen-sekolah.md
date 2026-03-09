# PRD: Sistem Manajemen Sekolah (TK, Playgroup, SD)

## Introduction

Sistem manajemen sekolah terintegrasi untuk TK, Playgroup, dan SD yang memungkinkan admin dan guru mengelola data siswa, nilai, absensi, aktivitas harian, kalender sekolah, dan keuangan (SPP) dalam satu platform. Aplikasi ini dirancang untuk single-school (single-tenant) dengan fokus pada efisiensi operasional sekolah sehari-hari. Termasuk fitur publikasi kalender aktivitas yang dapat diakses oleh orang tua.

## Goals

- Mengelola data master sekolah (profil, tahun ajaran, semester, tingkat)
- Memudahkan admin mengelola data siswa, guru, dan kelas secara terpusat
- Memungkinkan guru menginput nilai dan absensi dengan cepat
- Mengotomatisasi pelacakan pembayaran SPP
- Mendokumentasikan aktivitas harian siswa
- Menyediakan dashboard untuk monitoring sekolah secara real-time
- Memublikasikan kalender aktivitas sekolah kepada orang tua

## User Roles

1. **Admin** - Mengelola seluruh sistem, data master, keuangan, dan laporan
2. **Guru** - Mengelola kelas, absensi, nilai, dan aktivitas siswa di kelasnya

---

## Module 0: Data Master & Konfigurasi Sekolah

### US-000A: Kelola profil sekolah
**Description:** Sebagai Admin, saya ingin mengelola profil sekolah sehingga informasi sekolah tercatat dan dapat ditampilkan di sistem.

**Acceptance Criteria:**
- [ ] Form input profil sekolah: nama sekolah, alamat lengkap, no. telepon, email, website
- [ ] Upload logo sekolah (JPG/PNG, max 2MB)
- [ ] Input informasi sekolah: NPSN/NSS, akreditasi, tanggal berdiri, nama kepala sekolah
- [ ] Input visi dan misi sekolah
- [ ] Upload foto fasilitas sekolah (multiple, opsional)
- [ ] Tampilkan profil di halaman publik/landing page
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

### US-000B: Kelola tahun ajaran
**Description:** Sebagai Admin, saya ingin mengelola tahun ajaran sehingga sistem dapat mengelola data per periode akademik.

**Acceptance Criteria:**
- [ ] CRUD tahun ajaran (contoh: 2024/2025, 2025/2026)
- [ ] Input tanggal mulai dan tanggal selesai tahun ajaran
- [ ] Setting status: active, inactive, upcoming
- [ ] Hanya boleh ada 1 tahun ajaran yang active
- [ ] Tidak bisa menghapus tahun ajaran yang sudah memiliki data siswa/nilai
- [ ] Tampilkan daftar tahun ajaran dengan status
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

### US-000C: Kelola semester
**Description:** Sebagai Admin, saya ingin mengelola semester dalam setiap tahun ajaran sehingga sistem dapat membedakan periode nilai.

**Acceptance Criteria:**
- [ ] CRUD semester (Ganjil, Genap) untuk setiap tahun ajaran
- [ ] Input tanggal mulai dan tanggal selesai semester
- [ ] Setting status: active, inactive, upcoming
- [ ] Hanya boleh ada 1 semester yang active per tahun ajaran
- [ ] Tidak bisa menghapus semester yang sudah memiliki data nilai
- [ ] Tampilkan daftar semester per tahun ajaran
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

### US-000D: Kelola tingkat (level) sekolah
**Description:** Sebagai Admin, saya ingin mengelola tingkat/level sekolah (TK, Playgroup, SD) sesuai jenjang yang ada.

**Acceptance Criteria:**
- [ ] CRUD tingkat sekolah: TK A, TK B, Playgroup, SD 1-6
- [ ] Setting urutan tingkat (untuk naik kelas otomatis)
- [ ] Assign tingkat ke kategori: TK (Taman Kanak-kanak), Playgroup, SD (Sekolah Dasar)
- [ ] Tampilkan daftar tingkat dengan jumlah kelas dan siswa
- [ ] Tidak bisa menghapus tingkat yang sudah memiliki kelas/siswa
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

---

## Module 1: Data Siswa

### US-001: Tambah data siswa baru
**Description:** Sebagai Admin, saya ingin menambahkan data siswa baru sehingga data siswa tercatat di sistem.

**Acceptance Criteria:**
- [ ] Form input data siswa: nama lengkap, NIS, tanggal lahir, jenis kelamin, kelas, foto
- [ ] Form input data orang tua: nama ayah, nama ibu, no. HP, alamat
- [ ] Validasi NIS tidak boleh duplikat
- [ ] Upload foto dengan format JPG/PNG (max 2MB)
- [ ] Data tersimpan di database
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

### US-002: Edit dan hapus data siswa
**Description:** Sebagai Admin, saya ingin mengedit dan menghapus data siswa sehingga data selalu updated.

**Acceptance Criteria:**
- [ ] Tombol edit pada setiap row data siswa
- [ ] Form edit menampilkan data existing
- [ ] Tombol hapus dengan konfirmasi dialog
- [ ] Data siswa yang sudah memiliki nilai/SPP tidak bisa dihapus (soft delete)
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

### US-003: Daftar dan pencarian siswa
**Description:** Sebagai Admin/Guru, saya ingin melihat daftar siswa dan mencari siswa tertentu sehingga mudah ditemukan.

**Acceptance Criteria:**
- [ ] Tabel daftar siswa dengan pagination (20 data per halaman)
- [ ] Search by nama atau NIS
- [ ] Filter by kelas dan tingkat (TK/Playgroup/SD)
- [ ] Tampilkan foto kecil, nama, NIS, kelas, nama orang tua
- [ ] Klik row untuk melihat detail siswa
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

### US-004: Import data siswa dari Excel/CSV
**Description:** Sebagai Admin, saya ingin import data siswa dari file Excel/CSV sehingga tidak perlu input satu per satu.

**Acceptance Criteria:**
- [ ] Upload file Excel/CSV dengan format template tertentu
- [ ] Validasi kolom required (nama, NIS, kelas, dll)
- [ ] Preview data sebelum konfirmasi import
- [ ] Show error jika ada data invalid (NIS duplikat, format salah)
- [ ] Proses import batch dan tampilkan hasil sukses/gagal
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

### US-004A: Riwayat kelas siswa (History Perkembangan Kelas)
**Description:** Sebagai Admin/Guru, saya ingin melihat riwayat kelas yang pernah ditempati siswa dari awal masuk hingga sekarah untuk melihat perkembangan akademiknya.

**Acceptance Criteria:**
- [ ] Tampilkan riwayat kelas di halaman detail siswa
- [ ] Setiap riwayat menampilkan: tahun ajaran, semester, nama kelas, wali kelas, status (aktif/lulus/keluar)
- [ ] Otomatis buat record baru saat siswa naik kelas/kenaikan tingkat
- [ ] Support untuk siswa yang tinggal kelas (duplicate record kelas yang sama)
- [ ] Tampilkan total durasi di setiap kelas
- [ ] Tombol "Naik Kelas" untuk memindahkan siswa ke kelas berikutnya (otomatis archive riwayat)
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

---

## Module 2: Akademik & Nilai

### US-005: Input nilai per siswa
**Description:** Sebagai Guru, saya ingin input nilai per siswa per mata pelajaran sehingga nilai tercatat.

**Acceptance Criteria:**
- [ ] Form input nilai: pilih kelas, siswa, mata pelajaran
- [ ] Input nilai: tugas, ulangan harian, PTS, PAS
- [ ] Validasi nilai 0-100
- [ ] Simpan dan lanjut ke siswa berikutnya
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

### US-006: Generate raport siswa
**Description:** Sebagai Guru/Admin, saya ingin generate raport siswa sehingga bisa dicetak/dilihat.

**Acceptance Criteria:**
- [ ] Pilih siswa dan semester
- [ ] Tampilkan semua nilai per mata pelajaran
- [ ] Hitung rata-rata dan ranking (opsional untuk TK/Playgroup)
- [ ] Kolom catatan/remarks guru
- [ ] Tombol print/cetak PDF
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

### US-007: Kelola mata pelajaran
**Description:** Sebagai Admin, saya ingin mengelola mata pelajaran sesuai tingkat (TK/Playgroup/SD).

**Acceptance Criteria:**
- [ ] CRUD mata pelajaran
- [ ] Input: kode mata pelajaran, nama, deskripsi, kkm (opsional untuk SD)
- [ ] Assign mata pelajaran ke tingkat (TK A/B, Playgroup, SD 1-6)
- [ ] Tampilkan daftar mata pelajaran per tingkat
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

### US-007A: Assign guru ke mata pelajaran
**Description:** Sebagai Admin, saya ingin assign guru ke mata pelajaran sehingga terdata siapa yang mengajar apa.

**Acceptance Criteria:**
- [ ] Pilih mata pelajaran dan tingkat
- [ ] Pilih guru yang mengajar (bisa multiple untuk paralel)
- [ ] Tampilkan daftar mata pelajaran dengan guru pengampunya
- [ ] Filter by tingkat dan mata pelajaran
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

### US-007B: Daftar dan pencarian mata pelajaran
**Description:** Sebagai Admin/Guru, saya ingin melihat daftar mata pelajaran dan mencari mata pelajaran tertentu.

**Acceptance Criteria:**
- [ ] Tabel daftar mata pelajaran dengan pagination
- [ ] Search by nama atau kode mata pelajaran
- [ ] Filter by tingkat (TK/Playgroup/SD 1-6)
- [ ] Tampilkan: kode, nama, tingkat, kkm, guru pengampu
- [ ] Klik row untuk melihat detail dan edit
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

### US-008: Kelola kelas
**Description:** Sebagai Admin, saya ingin mengelola kelas (tambah, edit, hapus, assign guru wali).

**Acceptance Criteria:**
- [ ] CRUD kelas (contoh: TK A1, TK A2, SD 1A, SD 1B)
- [ ] Input: nama kelas, tingkat, kapasitas maksimal, ruang kelas
- [ ] Assign guru wali kelas
- [ ] Assign tahun ajaran active sebagai default
- [ ] Tampilkan jumlah siswa per kelas
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

### US-008A: Daftar dan pencarian kelas
**Description:** Sebagai Admin/Guru, saya ingin melihat daftar kelas dan mencari kelas tertentu.

**Acceptance Criteria:**
- [ ] Tabel daftar kelas dengan pagination
- [ ] Search by nama kelas
- [ ] Filter by tingkat dan tahun ajaran
- [ ] Tampilkan: nama kelas, tingkat, wali kelas, jumlah siswa, kapasitas
- [ ] Klik row untuk melihat detail dan daftar siswa
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

### US-008B: Assign siswa ke kelas
**Description:** Sebagai Admin, saya ingin assign siswa ke kelas sehingga setiap siswa memiliki kelas.

**Acceptance Criteria:**
- [ ] Pilih kelas dan tahun ajaran/semester
- [ ] Tampilkan daftar siswa yang belum assign kelas di tahun ajaran tersebut
- [ ] Checkbox untuk pilih siswa (bisa multiple)
- [ ] Tombol assign untuk memindahkan siswa ke kelas
- [ ] Validasi: tidak bisa assign melebihi kapasitas kelas
- [ ] Tampilkan daftar siswa per kelas
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

### US-008C: Naik kelas (kenaikan tingkat)
**Description:** Sebagai Admin, saya ingin melakukan proses naik kelas secara batch untuk semua siswa.

**Acceptance Criteria:**
- [ ] Pilih tahun ajaran asal dan tujuan
- [ ] Tampilkan preview siswa yang akan naik kelas
- [ ] Pilih kelas tujuan untuk setiap kelas asal
- [ ] Konfirmasi sebelum proses naik kelas
- [ ] Otomatis archive riwayat kelas di modul Data Siswa
- [ ] Handle siswa yang tidak naik kelas (tinggal kelas)
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

### US-008D: Pembagian kelas otomatis
**Description:** Sebagai Admin, saya ingin membagi siswa ke dalam beberapa kelas secara otomatis berdasarkan kriteria tertentu.

**Acceptance Criteria:**
- [ ] Pilih tingkat dan jumlah kelas yang akan dibuat
- [ ] Pilih metode pembagian: acak, berdasarkan jenis kelamin (balance), berdasarkan nilai tahun lalu
- [ ] Set kapasitas maksimal per kelas
- [ ] Preview hasil pembagian sebelum konfirmasi
- [ ] Konfirmasi untuk create kelas dan assign siswa secara batch
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

### US-009: Kelola jadwal pelajaran
**Description:** Sebagai Admin, saya ingin mengelola jadwal pelajaran per kelas sehingga jadwal sekolah terorganisir.

**Acceptance Criteria:**
- [ ] Pilih kelas, hari, dan tahun ajaran/semester
- [ ] Input jadwal: jam ke-, waktu mulai, waktu selesai, mata pelajaran, guru, ruang kelas
- [ ] Tampilan jadwal dalam format tabel/grid per hari
- [ ] Validasi: tidak ada bentrok jadwal untuk guru yang sama di waktu yang sama
- [ ] Validasi: tidak ada bentrok jadwal untuk ruangan yang sama di waktu yang sama
- [ ] Copy jadwal dari kelas lain untuk efisiensi
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

### US-009A: Daftar dan pencarian jadwal pelajaran
**Description:** Sebagai Admin/Guru, saya ingin melihat daftar jadwal pelajaran dan mencari jadwal tertentu.

**Acceptance Criteria:**
- [ ] Filter by kelas, hari, guru, atau mata pelajaran
- [ ] Tampilan jadwal mingguan per kelas (Senin-Jumat)
- [ ] Tampilkan: jam, mata pelajaran, guru, ruang kelas
- [ ] Highlight jadwal yang sedang berlangsung (hari dan jam ini)
- [ ] Export jadwal ke PDF/Excel
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

### US-009B: Penjadwalan guru (jadwal mengajar guru)
**Description:** Sebagai Guru/Admin, saya ingin melihat jadwal mengajar seorang guru untuk melihat kapan mereka mengajar.

**Acceptance Criteria:**
- [ ] Pilih guru dan tahun ajaran/semester
- [ ] Tampilan jadwal mingguan guru (Senin-Jumat)
- [ ] Tampilkan: jam, kelas, mata pelajaran, ruang kelas
- [ ] Highlight jadwal yang sedang berlangsung
- [ ] Tampilkan total jam mengajar per minggu
- [ ] Export jadwal guru ke PDF
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

### US-009C: Kelola kurikulum
**Description:** Sebagai Admin, saya ingin mengelola kurikulum per tingkat dan mata pelajaran.

**Acceptance Criteria:**
- [ ] Pilih tingkat dan mata pelajaran
- [ ] Input materi/kompetensi yang harus diajarkan per semester
- [ ] Struktur materi: bab/topik, sub-topik, indikator pencapaian
- [ ] Assign materi ke minggu ke-X dalam semester
- [ ] Tampilkan progress coverage materi per kelas
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

### US-009D: Jurnal mengajar guru
**Description:** Sebagai Guru, saya ingin mencatat jurnal mengajar harian sehingga ada dokumentasi apa yang diajarkan.

**Acceptance Criteria:**
- [ ] Pilih kelas, mata pelajaran, tanggal, dan jam pelajaran
- [ ] Input materi yang diajarkan (dari kurikulum atau custom)
- [ ] Input catatan: metode mengajar, respons siswa, kendala
- [ ] Upload foto/dokumen kegiatan mengajar (opsional)
- [ ] Tampilkan riwayat jurnal mengajar per guru
- [ ] Export jurnal ke PDF untuk laporan
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

### US-009E: Kelola materi pembelajaran
**Description:** Sebagai Guru, saya ingin mengupload dan mengelola materi pembelajaran untuk siswa.

**Acceptance Criteria:**
- [ ] Upload materi: file (PDF, DOC, PPT), video, gambar, atau link
- [ ] Input judul, deskripsi, mata pelajaran, tingkat/kelas
- [ ] Tag materi dengan topik/bab (opsional)
- [ ] Tampilkan daftar materi per mata pelajaran/kelas
- [ ] Filter by mata pelajaran, tingkat, tag, atau pencarian
- [ ] Download atau preview materi
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

### US-009F: Kelola tugas siswa
**Description:** Sebagai Guru, saya ingin membuat dan mengelola tugas untuk siswa.

**Acceptance Criteria:**
- [ ] Buat tugas: judul, deskripsi, mata pelajaran, kelas, deadline
- [ ] Upload lampiran tugas (file, gambar, dll)
- [ ] Setting tipe tugas: online (upload file) atau offline
- [ ] Tampilkan daftar tugas per kelas dengan status deadline
- [ ] Edit dan hapus tugas
- [ ] Tanggal tugas yang sudah lewat ditandai "overdue"
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

### US-009G: Submit tugas siswa
**Description:** Sebagai Guru (atas nama siswa) atau Siswa (jika ada fitur portal), saya ingin submit tugas.

**Acceptance Criteria:**
- [ ] Pilih tugas yang akan dikerjakan
- [ ] Upload jawaban tugas (file, gambar, atau link)
- [ ] Add catatan/keterangan (opsional)
- [ ] Submit tugas dengan timestamp
- [ ] Bisa edit/re-submit sebelum deadline (dengan catatan)
- [ ] Tampilkan status: belum submit, submitted, graded
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

### US-009H: Penilaian tugas siswa
**Description:** Sebagai Guru, saya ingin memberi nilai dan feedback pada tugas siswa.

**Acceptance Criteria:**
- [ ] List siswa yang sudah submit tugas
- [ ] Input nilai dan feedback komentar untuk setiap siswa
- [ ] Download atau preview jawaban siswa
- [ ] Tombol "nilai semua" untuk batch grading
- [ ] Notifikasi ke siswa (jika ada portal) tentang nilai tugas
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

### US-009I: Kelola bank soal ujian
**Description:** Sebagai Guru, saya ingin membuat dan mengelola bank soal ujian.

**Acceptance Criteria:**
- [ ] Buat soal: pertanyaan, tipe soal (pilihan ganda, isian, essay), opsi jawaban, kunci jawaban
- [ ] Tag soal dengan: mata pelajaran, tingkat, topik/bab, tingkat kesulitan
- [ ] Import soal dari file Excel/Word (opsional)
- [ ] Edit dan hapus soal
- [ ] Preview soal
- [ ] Filter and search soal by tag atau mata pelajaran
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

### US-009J: Buat ujian online
**Description:** Sebagai Guru, saya ingin membuat ujian online dari bank soal.

**Acceptance Criteria:**
- [ ] Create ujian: judul, deskripsi, mata pelajaran, kelas, tanggal buka, tanggal tutup, durasi
- [ ] Pilih soal dari bank soal (manual atau random by tag/topik)
- [ ] Setting urutan soal: acak atau fix
- [ ] Setting tampilan jawaban: acak atau fix
- [ ] Setting attempt: bisa ulang atau sekali saja
- [ ] Tampilkan daftar ujian dengan status
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

### US-009K: Ambil ujian online
**Description:** Sebagai Siswa (via admin/guru input) atau Siswa (portal), saya ingin mengerjakan ujian online.

**Acceptance Criteria:**
- [ ] Tampilkan daftar ujian yang tersedia berdasarkan kelas siswa
- [ ] Tampilkan info ujian: durasi, jumlah soal, rentang waktu
- [ ] Tombol mulai ujian dengan konfirmasi
- [ ] Timer countdown durasi ujian
- [ ] Tampilkan soal satu per satu atau semua sekaligus
- [ ] Navigasi soal: previous, next, jump to question
- [ ] Mark/buat penanda soal yang ragu-ragu
- [ ] Submit jawaban selesai ujian atau auto-submit saat waktu habis
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

### US-009L: Penilaian otomatis ujian online
**Description:** Sebagai Sistem, saya ingin otomatis menilai ujian online untuk soal pilihan ganda.

**Acceptance Criteria:**
- [ ] Auto-grade soal pilihan ganda berdasarkan kunci jawaban
- [ ] Tampilkan skor langsung setelah submit
- [ ] Review jawaban: tampilkan jawaban siswa vs kunci jawaban
- [ ] Flag soal isian/essay untuk manual grading
- [ ] Simpan hasil ujian: skor, waktu mengerjakan, jawaban per soal
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

### US-009M: Rekap hasil ujian
**Description:** Sebagai Guru, saya ingin melihat rekap hasil ujian per kelas.

**Acceptance Criteria:**
- [ ] Tampilkan daftar siswa dengan skor ujian
- [ ] Statistik: nilai tertinggi, terendah, rata-rata, lulus/tidak lulus
- [ ] Grafik distribusi nilai
- [ ] Filter by rentang nilai
- [ ] Export hasil ujian ke Excel
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

### US-009N: E-rapor (enhanced)
**Description:** Sebagai Admin/Guru, saya ingin generate rapor digital (e-rapor) yang lengkap dengan berbagai aspek penilaian.

**Acceptance Criteria:**
- [ ] Pilih siswa dan semester
- [ ] Tampilkan semua nilai per mata pelajaran (tugas, ulangan, PTS, PAS, ujian online)
- [ ] Hitung rata-rata dan ranking (opsional untuk TK/Playgroup)
- [ ] Kolom catatan/remarks guru per mata pelajaran
- [ ] Kolom catatan umum dari wali kelas
- [ ] Kolom catatan untuk orang tua
- [ ] Tampilkan statistik kehadiran semester ini (total H, S, I, A)
- [ ] Tampilkan ekstrakurikuler yang diikuti
- [ ] Template rapor yang bisa customize header/footer sekolah
- [ ] Tombol print/cetak PDF dengan format rapor resmi
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

---

## Module 3: Absensi

### US-010: Input absensi harian siswa
**Description:** Sebagai Guru, saya ingin input absensi siswa per kelas per hari sehingga kehadiran tercatat.

**Acceptance Criteria:**
- [ ] Pilih kelas dan tanggal
- [ ] List semua siswa di kelas tersebut
- [ ] Radio button/checkbox: Hadir, Sakit, Izin, Alpha
- [ ] Optional: catatan/keterangan
- [ ] Tombol simpan untuk semua sekaligus
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

### US-011: Rekap kehadiran bulanan
**Description:** Sebagai Admin/Guru, saya ingin melihat rekap kehadiran per bulan sehingga bisa monitoring.

**Acceptance Criteria:**
- [ ] Pilih siswa dan bulan
- [ ] Tampilkan kalender dengan status kehadiran (H/S/I/A)
- [ ] Hitung total: hadir, sakit, izin, alpha
- [ ] Tombol export ke PDF/Excel
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

### US-012: Daftar siswa tidak hadir hari ini
**Description:** Sebagai Admin, saya ingin melihat daftar siswa yang tidak hadir hari ini untuk follow-up.

**Acceptance Criteria:**
- [ ] Dashboard widget atau page khusus
- [ ] List siswa yang statusnya Sakit/Izin/Alpha hari ini
- [ ] Tampilkan nama, kelas, status, dan no HP orang tua
- [ ] Filter by status
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

---

## Module 4: Aktivitas Harian Siswa

### US-013: Catat aktivitas harian siswa
**Description:** Sebagai Guru, saya ingin mencatat aktivitas harian siswa untuk dokumentasi dan laporan ke orang tua.

**Acceptance Criteria:**
- [ ] Pilih kelas, tanggal, dan jenis aktivitas (belajar, makan, tidur, bermain, ekskul)
- [ ] Input deskripsi aktivitas
- [ ] Upload foto/video opsional
- [ ] Tag siswa yang berpartisipasi (bisa multiple)
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

### US-014: Timeline aktivitas siswa
**Description:** Sebagai Guru, saya ingin melihat timeline aktivitas seorang siswa sehingga bisa melihat perkembangannya.

**Acceptance Criteria:**
- [ ] Pilih siswa dan rentang tanggal
- [ ] Tampilkan timeline aktivitas secara kronologis
- [ ] Tampilkan foto/video jika ada
- [ ] Filter by jenis aktivitas
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

### US-015: Laporan aktivitas bulanan
**Description:** Sebagai Guru/Admin, saya ingin generate laporan aktivitas bulanan per kelas atau per siswa.

**Acceptance Criteria:**
- [ ] Pilih kelas/siswa dan bulan
- [ ] Summary aktivitas: jumlah per jenis aktivitas
- [ ] Tampilkan galeri foto/video dari aktivitas bulan tersebut
- [ ] Tombol share/download untuk kirim ke orang tua
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

---

## Module 5: Keuangan (SPP)

### US-016: Kelola data SPP
**Description:** Sebagai Admin, saya ingin mengelola data SPP (nominal, jatuh tempo) sehingga sistem siap digunakan.

**Acceptance Criteria:**
- [ ] Setting nominal SPP per tingkat (TK, Playgroup, SD)
- [ ] Setting tanggal jatuh tempo (default: tanggal 10 setiap bulan)
- [ ] Setting denda keterlambatan (opsional)
- [ ] Tampilkan daftar konfigurasi SPP
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

### US-017: Tagihan SPP bulanan
**Description:** Sebagai Admin, saya ingin generate tagihan SPP bulanan untuk semua siswa.

**Acceptance Criteria:**
- [ ] Pilih bulan dan tahun tagihan
- [ ] Generate tagihan untuk semua siswa aktif
- [ ] Tampilkan preview daftar tagihan sebelum konfirmasi
- [ ] Konfirmasi create tagihan batch
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

### US-018: Input pembayaran SPP
**Description:** Sebagai Admin, saya ingin input pembayaran SPP sehingga status pembayaran terupdate.

**Acceptance Criteria:**
- [ ] List tagihan SPP yang belum lunas
- [ ] Pilih tagihan dan input nominal bayar, tanggal bayar, metode bayar
- [ ] Upload bukti pembayaran opsional
- [ ] Update status: Lunas/Sebagian/Belum Bayar
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

### US-019: Laporan tunggakan SPP
**Description:** Sebagai Admin, saya ingin melihat daftar siswa yang menunggak SPP untuk follow-up.

**Acceptance Criteria:**
- [ ] List siswa dengan tunggakan SPP
- [ ] Tampilkan: nama, kelas, total tunggakan, bulan menunggak
- [ ] Sort by total tunggakan (terbanyak dulu)
- [ ] Filter by lama tunggakan (1 bulan, 2 bulan, dll)
- [ ] Tombol export ke Excel
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

---

## Module 6: Guru & Staff

### US-020: Manajemen data guru
**Description:** Sebagai Admin, saya ingin mengelola data guru dan staff sehingga tercatat di sistem.

**Acceptance Criteria:**
- [ ] Form input data guru: NIP, nama lengkap, jenis kelamin, no HP, email, alamat
- [ ] Upload foto guru
- [ ] Assign mata pelajaran yang diajar
- [ ] Assign sebagai wali kelas (opsional)
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

### US-021: Absensi guru
**Description:** Sebagai Admin, saya ingin mencatat absensi guru harian.

**Acceptance Criteria:**
- [ ] Input absensi guru per tanggal
- [ ] Status: Hadir, Sakit, Izin, Alpha
- [ ] Rekap kehadiran bulanan
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

### US-021A: Riwayat mengajar guru (Teaching History)
**Description:** Sebagai Admin/Guru, saya ingin melihat riwayat mata pelajaran dan kelas yang pernah diajar oleh guru tertentu untuk dokumentasi portofolio guru.

**Acceptance Criteria:**
- [ ] Tampilkan riwayat mengajar di halaman detail guru
- [ ] Setiap riwayat menampilkan: tahun ajaran, semester, mata pelajaran yang diajar, kelas yang diampu, jumlah siswa
- [ ] Otomatis buat record baru setiap tahun ajaran/semester baru berdasarkan assignment kelas dan mata pelajaran
- [ ] Tampilkan statistik: total tahun mengajar, total kelas pernah diampu, total siswa pernah diajar
- [ ] Filter dan sort riwayat berdasarkan tahun ajaran atau mata pelajaran
- [ ] Export riwayat mengajar ke PDF untuk portofolio guru
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

---

## Module 7: Kalender Aktivitas Sekolah (Publikasi ke Orang Tua)

### US-022: Kelola kalender aktivitas sekolah
**Description:** Sebagai Admin, saya ingin mengelola kalender aktivitas sekolah untuk dipublikasikan ke orang tua.

**Acceptance Criteria:**
- [ ] Form input aktivitas: judul, deskripsi, tanggal, waktu, lokasi, kategori (upacara, rapat, lomba, libur, lainnya)
- [ ] Upload gambar/flyer opsional
- [ ] Pilih target audience: semua orang tua, kelas tertentu, tingkat tertentu
- [ ] Setting status: draft, published, cancelled
- [ ] Tampilan calendar (monthly grid) dengan marker untuk tanggal yang ada aktivitas
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

### US-023: Edit dan hapus aktivitas kalender
**Description:** Sebagai Admin, saya ingin mengedit dan menghapus aktivitas kalender sehingga informasi selalu akurat.

**Acceptance Criteria:**
- [ ] Tombol edit pada setiap aktivitas
- [ ] Form edit menampilkan data existing
- [ ] Tombol hapus dengan konfirmasi dialog
- [ ] Soft delete untuk aktivitas yang sudah published
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

### US-024: Detail dan reminder aktivitas
**Description:** Sebagai Admin/Guru, saya ingin melihat detail aktivitas dan mengatur reminder sehingga tidak lupa.

**Acceptance Criteria:**
- [ ] Klik aktivitas di calendar untuk lihat detail
- [ ] Tampilkan semua informasi: judul, deskripsi lengkap, tanggal, waktu, lokasi, gambar/flyer
- [ ] Tombol reminder (set reminder X hari sebelum)
- [ ] List aktivitas upcoming (7 hari ke depan) di dashboard
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

### US-025: Share link kalender ke orang tua
**Description:** Sebagai Admin, saya ingin membagikan link kalender kepada orang tua untuk akses publik.

**Acceptance Criteria:**
- [ ] Generate unik URL/public link untuk kalender
- [ ] Mode read-only untuk orang tua (hanya view, tidak bisa edit)
- [ ] Filter by target audience (kelas/tingkat) jika diakses via link
- [ ] Support embed kalender di website sekolah
- [ ] Tombol copy link dan QR code untuk mudah dibagikan
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

---

## Module 8: Dashboard Admin

### US-026: Dashboard overview
**Description:** Sebagai Admin, saya ingin melihat overview sekolah di dashboard sehingga bisa monitoring cepat.

**Acceptance Criteria:**
- [ ] Widget total siswa aktif (per tingkat)
- [ ] Widget total guru
- [ ] Widget total kelas
- [ ] Widget siswa tidak hadir hari ini
- [ ] Widget tagihan SPP bulan ini (total tagihan, total lunas, total tunggakan)
- [ ] Grafik kehadiran 7 hari terakhir
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

### US-027: Widget aktivitas terbaru
**Description:** Sebagai Admin, saya ingin melihat aktivitas terbaru di dashboard.

**Acceptance Criteria:**
- [ ] List 5-10 aktivitas harian terbaru (dari modul Aktivitas Harian)
- [ ] List 3-5 aktivitas kalender upcoming (dari modul Kalender)
- [ ] Tampilkan: tanggal, kelas, jenis aktivitas, thumbnail foto
- [ ] Klik untuk lihat detail
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill

---

## Functional Requirements

### Data Master & Konfigurasi Sekolah
- FR-0A: Sistem harus menyimpan profil sekolah: nama, alamat, telepon, email, website, logo, NPSN/NSS, akreditasi, visi, misi
- FR-0B: Sistem harus menyimpan tahun ajaran dengan tanggal mulai dan selesai
- FR-0C: Sistem harus menyimpan semester per tahun ajaran dengan status
- FR-0D: Sistem harus menyimpan tingkat/level sekolah (TK, Playgroup, SD)
- FR-0E: Sistem harus memastikan hanya 1 tahun ajaran dan 1 semester yang active
- FR-0F: Sistem harus mencegah penghapusan tahun ajaran/semester yang sudah memiliki data

### Data Siswa
- FR-1: Sistem harus menyimpan data siswa: nama, NIS, tanggal lahir, jenis kelamin, kelas, foto, data orang tua
- FR-2: Sistem harus memvalidasi NIS unik
- FR-3: Sistem harus support upload foto dengan validasi size dan format
- FR-3A: Sistem harus menyimpan riwayat kelas siswa per tahun ajaran/semester (class history)
- FR-3B: Sistem harus otomatis membuat record riwayat saat siswa naik kelas atau pindah kelas
- FR-3C: Sistem harus mendukung status riwayat: aktif, lulus, keluar, tinggal kelas

### Akademik & Nilai
- FR-4: Sistem harus menyimpan nilai per siswa per mata pelajaran: tugas, ulangan harian, PTS, PAS
- FR-5: Sistem harus generate raport dengan perhitungan rata-rata
- FR-6: Sistem harus menyimpan mata pelajaran per tingkat (TK/Playgroup/SD)
- FR-6A: Sistem harus menyimpan data mata pelajaran: kode, nama, deskripsi, kkm, tingkat
- FR-6B: Sistem harus assign guru ke mata pelajaran sebagai pengampu
- FR-6C: Sistem harus menyimpan data kelas: nama, tingkat, kapasitas, ruang kelas, wali kelas, tahun ajaran
- FR-6D: Sistem harus assign siswa ke kelas per tahun ajaran/semester
- FR-6E: Sistem harus memvalidasi kapasitas kelas saat assign siswa
- FR-6F: Sistem harus support proses naik kelas batch dengan archive riwayat
- FR-6G: Sistem harus support pembagian kelas otomatis berdasarkan kriteria tertentu

### Jadwal & Penjadwalan
- FR-7A: Sistem harus menyimpan jadwal pelajaran: jam, hari, mata pelajaran, guru, ruang kelas, kelas
- FR-7B: Sistem harus memvalidasi tidak ada bentrok jadwal untuk guru dan ruangan
- FR-7C: Sistem harus menampilkan jadwal mingguan per kelas dan per guru
- FR-7D: Sistem harus support copy jadwal dari kelas lain untuk efisiensi

### Kurikulum & Jurnal Mengajar
- FR-8A: Sistem harus menyimpan kurikulum per tingkat dan mata pelajaran dengan struktur materi
- FR-8B: Sistem harus menampilkan progress coverage materi per kelas
- FR-8C: Sistem harus menyimpan jurnal mengajar guru harian dengan materi dan catatan
- FR-8D: Sistem harus support upload foto/dokumen kegiatan mengajar

### Materi Pembelajaran
- FR-9A: Sistem harus menyimpan materi pembelajaran: file, video, gambar, atau link
- FR-9B: Sistem harus support tag materi dengan topik/bab
- FR-9C: Sistem harus menampilkan daftar materi per mata pelajaran/kelas dengan filter

### Tugas & Ujian
- FR-10A: Sistem harus menyimpan tugas: judul, deskripsi, mata pelajaran, kelas, deadline, lampiran
- FR-10B: Sistem harus support submit tugas siswa dengan upload file
- FR-10C: Sistem harus menyimpan bank soal ujian dengan tipe (pilihan ganda, isian, essay)
- FR-10D: Sistem harus support tag soal dengan mata pelajaran, tingkat, topik, kesulitan
- FR-10E: Sistem harus membuat ujian online dari bank soal dengan setting durasi dan attempt
- FR-10F: Sistem harus auto-grade soal pilihan ganda dan flag soal isian/essay
- FR-10G: Sistem harus menyimpan hasil ujian: skor, waktu mengerjakan, jawaban per soal
- FR-10H: Sistem harus menampilkan rekap hasil ujian dengan statistik

### E-Rapor
- FR-11A: Sistem harus generate rapor lengkap: nilai, catatan guru, kehadiran, ekskul
- FR-11B: Sistem harus support customize template rapor dengan header/footer sekolah
- FR-11C: Sistem harus menampilkan semua nilai per semester (tugas, ulangan, PTS, PAS, ujian online)

### Absensi
- FR-12: Sistem harus menyimpan absensi harian siswa per kelas
- FR-13: Sistem harus menyediakan status: Hadir, Sakit, Izin, Alpha
- FR-14: Sistem harus rekap kehadiran per bulan per siswa

### Aktivitas Harian
- FR-15: Sistem harus menyimpan aktivitas harian: tanggal, kelas, jenis aktivitas, deskripsi, media
- FR-16: Sistem harus support multiple tag siswa per aktivitas
- FR-17: Sistem harus menyimpan jenis aktivitas: belajar, makan, tidur, bermain, ekskul

### Keuangan (SPP)
- FR-18: Sistem harus menyimpan konfigurasi nominal SPP per tingkat
- FR-19: Sistem harus generate tagihan SPP bulanan untuk semua siswa
- FR-20: Sistem harus menyimpan status pembayaran: Lunas, Sebagian, Belum Bayar
- FR-21: Sistem harus menghitung denda keterlambatan (jika dikonfigurasi)

### Guru & Staff
- FR-22: Sistem harus menyimpan data guru: NIP, nama, jenis kelamin, no HP, email, alamat
- FR-23: Sistem harus assign mata pelajaran dan wali kelas ke guru
- FR-24: Sistem harus menyimpan riwayat mengajar guru per tahun ajaran/semester (teaching history)
- FR-25: Sistem harus otomatis membuat record riwayat mengajar berdasarkan assignment mata pelajaran dan kelas
- FR-26: Sistem harus menghitung statistik: total tahun mengajar, total kelas diampu, total siswa diajar

### Dashboard
- FR-27: Sistem harus menampilkan statistik: total siswa, guru, kelas, kehadiran hari ini, tagihan SPP
- FR-28: Sistem harus menampilkan grafik kehadiran 7 hari terakhir
- FR-29: Sistem harus menampilkan aktivitas terbaru

### Kalender Aktivitas Sekolah
- FR-30: Sistem harus menyimpan aktivitas kalender: judul, deskripsi, tanggal, waktu, lokasi, kategori, gambar/flyer
- FR-31: Sistem harus support kategori aktivitas: upacara, rapat, lomba, libur, acara khusus, lainnya
- FR-32: Sistem harus support target audience: semua orang tua, kelas tertentu, tingkat tertentu
- FR-33: Sistem harus menyediakan status: draft, published, cancelled
- FR-34: Sistem harus generate public link untuk akses read-only oleh orang tua
- FR-35: Sistem harus menampilkan calendar view (monthly grid) dengan marker aktivitas

## Non-Goals (Out of Scope)

- Tidak ada portal orang tua (parent portal) lengkap di MVP (hanya kalender publik read-only)
- Tidak ada fitur notifikasi WA/Email otomatis
- Tidak ada multi-tenant (banyak sekolah dalam satu sistem)
- Tidak ada fitur inventory/barang
- Tidak ada modul jadwal pelajaran kompleks
- Tidak ada integrasi payment gateway
- Tidak ada fitur ekspor raport ke format dinas
- Tidak ada modul perpustakaan
- Tidak ada fitur chat/komunikasi dua arah
- Orang tua tidak bisa login ke sistem (hanya akses kalender via public link)

## Design Considerations

- UI sederhana dan intuitive untuk user yang tidak tech-savvy
- Responsive design (support tablet untuk mobile input oleh guru)
- Color coding untuk status (absensi, pembayaran)
- Fast data entry untuk input batch (absensi, nilai)
- Preview sebelum konfirmasi untuk aksi critical (hapus, import)
- Calendar view yang mobile-friendly untuk akses orang tua
- Public link yang mudah di-share (copy link, QR code)

## Technical Considerations

- Stack: Next.js 16 (App Router) + React 19
- Database: D1 (SQLite) via Drizzle ORM
- Auth: Better-auth dengan role Admin/Guru
- File Upload: Cloudflare R2 untuk foto dan media
- Deployment: Cloudflare Workers
- State Management: Zustand untuk client state

## Success Metrics

- Admin bisa tambah siswa baru dalam < 2 menit
- Guru bisa input absensi 1 kelas dalam < 5 menit
- Laporan kehadiran dan SPP bisa generate dalam < 10 detik
- Sistem bisa handle 1000+ siswa tanpa degradation performa

## Open Questions

- Apakah perlu fitur arsip siswa (lulus/keluar)?
- Apakah TK/Playgroup menggunakan skala nilai atau deskripsi?
- Apakah perlu fitur backup/restore data?
- Apakah ada requirement khusus untuk laporan ke dinas pendidikan?
- Apakah kalender perlu support recurring events (event berulang seperti rapat rutin bulanan)?
- Apakah perlu fitur reminder otomatis ke orang tua (WA/Email) untuk aktivitas kalender?
