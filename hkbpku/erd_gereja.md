# Database Schema Gereja Komprehensif

Berikut adalah rancangan struktur **Entity-Relationship Diagram (ERD) Mermaid** yang menyeluruh dengan tambahan struktur entitas **Gereja** dan **Riwayat Pindah Jemaat** (history keanggotaan).

```mermaid
erDiagram
    %% Tabel Referensi / Organisasi (Master Data)
    Distrik ||--o{ Resort : "memiliki"
    Resort ||--o{ Huria : "memiliki"
    
    %% Organisasi Gereja
    Distrik ||--o{ Gereja : "menaungi"
    Resort ||--o{ Gereja : "menaungi"
    Huria ||--o{ Gereja : "menaungi"

    %% Relasi Level Gereja
    Gereja ||--o{ Wijk : "memiliki area pelayanan"
    Gereja ||--o{ Keluarga_Jemaat : "tempat terdaftar"

    %% Relasi Jemaat Utama
    Wijk ||--o{ Keluarga_Jemaat : "tempat domisili"
    Keluarga_Jemaat ||--o{ Anggota_Keluarga : "memiliki anak/tanggungan"
    Keluarga_Jemaat ||--|| Dokumen_Jemaat : "melampirkan"

    %% History Perpindahan Jemaat
    Keluarga_Jemaat ||--o{ Riwayat_Pindah : "mencatat histori"
    Gereja ||--o{ Riwayat_Pindah : "gereja asal"
    Gereja ||--o{ Riwayat_Pindah : "gereja tujuan"

    %% Relasi Pendaftaran Baptis
    Keluarga_Jemaat ||--o{ Pendaftaran_Baptis : "mendaftarkan baptis"
    Wijk ||--o{ Pendaftaran_Baptis : "titip daftar (jika bukan jemaat lokal)"
    Pendaftaran_Baptis ||--o{ Anak_Baptis : "mendaftarkan anak"
    Pendaftaran_Baptis ||--|| Dokumen_Baptis : "melampirkan surat"

    %% Relasi Berita Anak Lahir
    Keluarga_Jemaat ||--o{ Berita_Anak_Lahir : "melaporkan kelahiran"
    Wijk ||--o{ Berita_Anak_Lahir : "titipan dari wijk lain"
    Berita_Anak_Lahir ||--|| Dokumen_Anak_Lahir : "melampirkan dokumen"

    %% Relasi Pelayanan Pernikahan
    Wijk ||--o{ Pendaftaran_Nikah : "lokasi pemberkatan"
    Pendaftaran_Nikah ||--|| Dokumen_Nikah : "melampirkan dokumen"

    Distrik {
        int id PK
        string nama "01 - Distrik I ... dst"
    }
    
    Resort {
        int id PK
        int distrik_id FK
        string nama
    }
    
    Huria {
        int id PK
        int resort_id FK
        string nama
    }
    
    Gereja {
        int id PK
        string nama
        text alamat
        int distrik_id FK
        int resort_id FK
        int huria_id FK
        datetime created_at
    }

    Wijk {
        int id PK
        int gereja_id FK
        string nama
    }

    %% ==========================================
    %% ENTITAS PENDAFTARAN & HISTORY JEMAAT
    %% ==========================================
    Keluarga_Jemaat {
        int id PK
        int gereja_id FK "Terelasi langsung 1 gereja"
        int wijk_id FK
        string nama_suami
        string nama_istri
        string nomor_hp
        string email
        text alamat
        string asal_gereja
        datetime created_at
    }

    Riwayat_Pindah {
        int id PK
        int keluarga_id FK
        int gereja_asal_id FK "Referensi dari ID Gereja sebelumnya"
        int gereja_tujuan_id FK "Referensi ke ID Gereja penempatan baru"
        date tanggal_pindah
        string status "Keluar / Masuk HKBP"
        text alasan_pindah
    }

    Anggota_Keluarga {
        int id PK
        int keluarga_id FK
        string nama_anggota
        string tempat_lahir
        date tanggal_lahir
        string jenis_kelamin "Laki-laki / Perempuan"
        string hubungan "Anak / Tanggungan"
    }

    Dokumen_Jemaat {
        int id PK
        int keluarga_id FK
        boolean surat_keterangan_gereja
        boolean akte_pernikahan
        boolean akte_baptis
        boolean akte_sidi
        boolean surat_pengantar_sintua_wijk
    }

    %% ==========================================
    %% ENTITAS PENDAFTARAN BAPTISAN KUDUS
    %% ==========================================
    Pendaftaran_Baptis {
        int id PK
        int keluarga_id FK  "NULL jika bukan jemaat lokal"
        int wijk_id FK      "Pilihan Wijk daftar"
        string nama_ayah    
        string nama_ibu     
        string nomor_hp
        string email
        text alamat
        date tanggal_kebaktian "Tanggal rencana baptis"
        datetime created_at
    }

    Anak_Baptis {
        int id PK
        int pendaftaran_baptis_id FK
        string nama_anak
        string tempat_lahir
        date tanggal_lahir
        string jenis_kelamin "Laki-laki / Perempuan"
    }

    Dokumen_Baptis {
        int id PK
        int pendaftaran_baptis_id FK
        boolean akte_pernikahan
        boolean surat_pengantar_sintua
        boolean surat_pengantar_hkbp_lain
    }

    %% ==========================================
    %% ENTITAS BERITA ANAK LAHIR
    %% ==========================================
    Berita_Anak_Lahir {
        int id PK
        int keluarga_id FK  "Identifikasi keluarga yang melapor"
        int wijk_id FK
        string nama_ayah
        string nama_ibu
        string nomor_hp
        string email
        text alamat
        int anak_ke         "Anak urutan ke berapa (1-10)"
        date tanggal_lahir  
        string jenis_kelamin "Laki-laki / Perempuan"
        string tempat_lahir
        datetime created_at
    }

    Dokumen_Anak_Lahir {
        int id PK
        int berita_anak_lahir_id FK
        boolean akte_pernikahan_anak_pertama "Bila lapor anak pertama"
        boolean surat_pengantar_sintua
    }

    %% ==========================================
    %% ENTITAS PENDAFTARAN & PEMBERKATAN NIKAH
    %% ==========================================
    Pendaftaran_Nikah {
        int id PK
        int wijk_id FK
        %% Data Mempelai Pria (CP Pria)
        string cp_pria_nama
        string cp_pria_hp
        string cp_pria_email
        string cp_pria_tempat_lahir
        date cp_pria_tanggal_lahir
        date cp_pria_tanggal_baptis
        date cp_pria_tanggal_sidi
        string cp_pria_nama_ayah
        string cp_pria_nama_ibu
        string cp_pria_asal_gereja
        string cp_pria_wijk
        text cp_pria_alamat_rumah
        %% Data Mempelai Wanita (CP Perempuan)
        string cp_perempuan_nama
        string cp_perempuan_hp
        string cp_perempuan_email
        string cp_perempuan_tempat_lahir
        date cp_perempuan_tanggal_lahir
        date cp_perempuan_tanggal_baptis
        date cp_perempuan_tanggal_sidi
        string cp_perempuan_nama_ayah
        string cp_perempuan_nama_ibu
        string cp_perempuan_asal_gereja
        string cp_perempuan_wijk
        text cp_perempuan_alamat_rumah
        %% Data Pelaksanaan & Martumpol
        date tanggal_martumpol "Opsional - Tanggal pertunangan"
        string keterangan_martumpol
        date tanggal_pemberkatan "Tanggal pemberkatan nikah"
        string keterangan_pemberkatan
        datetime created_at
    }

    Dokumen_Nikah {
        int id PK
        int pendaftaran_nikah_id FK
        boolean surat_keterangan_gereja_asal
        boolean surat_baptis_pria
        boolean surat_baptis_perempuan
        boolean surat_sidi_pria
        boolean surat_sidi_perempuan
        boolean foto_gandeng_4x6
        boolean surat_persetujuan_tni_polri "Opsional untuk TNI/Polri"
        boolean surat_pengantar_sintua_wijk
    }
```
