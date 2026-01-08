# Aturan Struktur Folder Dokumentasi

File ini menjelaskan standar struktur folder untuk dokumentasi dalam proyek ini.

## Struktur Folder

Dokumentasi harus diorganisir berdasarkan modul dalam direktori `.agent/modules/`.

### 1. Dokumentasi Modul
Setiap dokumentasi resource atau fitur dalam modul harus mengikuti format path berikut:

```
.agent/modules/<nama-module>/(resource).md
```

Contoh:
- `.agent/modules/auth/login.md`
- `.agent/modules/payment/gateway.md`

### 2. Dokumentasi Testing
Dokumentasi pengujian (testing) juga harus mengikuti struktur yang sama dan ditempatkan di dalam folder modul terkait.

```
.agent/modules/<nama-module>/testing.md
```
atau spesifik per resource:
```
.agent/modules/<nama-module>/tests/(resource).md
```

Pastikan semua dokumentasi teknis dan pengujian tersentralisasi di bawah folder modul masing-masing untuk memudahkan pemeliharaan dan navigasi.
