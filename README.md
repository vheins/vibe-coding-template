# Vibe Coding Template

Selamat datang di **Vibe Coding Template**. Repository ini dirancang untuk menyusun struktur proyek perangkat lunak modern dengan dokumentasi yang komprehensif dan praktik pengujian yang terstandarisasi.

## 📚 Dokumentasi

Dokumentasi teknis disusun di dalam direktori `.agent/documents/` agar root folder tetap bersih, namun tetap memberikan wawasan mendalam bagi AI agent maupun pengembang.

### Tautan Cepat

- **[📖 Beranda Dokumentasi](.agent/documents/README.md)**: Pusat dari segala dokumentasi teknis.
- **[📦 Modul Aplikasi](.agent/documents/application/modules/README.md)**: Spesifikasi fitur, Aturan Bisnis, dan ERD.
- **[🔌 Spesifikasi API](.agent/documents/application/api/README.md)**: Kontrak REST API dan detail endpoint.
- **[✅ Pengujian (Testing)](.agent/documents/application/testing/README.md)**: Skenario pengujian (Positif, Negatif, Monkey) dan strateginya.

## 🚀 Memulai

1.  **Jelajahi Modul**: Periksa `application/modules` untuk memahami logika bisnis domain.
2.  **Tinjau API**: Lihat `application/api` untuk titik integrasi.
3.  **Jalankan Test**: Ikuti strategi yang ada di `application/testing`.

## 📁 Struktur Proyek

```bash
.
├── .agent/
│   └── documents/          # Hub Dokumentasi Terpusat
│       ├── application/    # Dokumen spesifik aplikasi (API, Modules, Testing)
│       ├── templates/      # Template standar untuk dokumen baru
│       └── README.md       # Indeks Dokumentasi Global
├── README.md               # Anda di sini
└── [Source Code]           # Kode sumber aplikasi (akan diimplementasikan)
```