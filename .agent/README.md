# Aturan Struktur Folder Dokumentasi

File ini menjelaskan standar struktur folder untuk dokumentasi dalam proyek ini.

## Struktur Folder

Dokumentasi harus diorganisir secara terstruktur untuk memudahkan navigasi dan pemeliharaan.

### 1. Dokumentasi Modul
Setiap dokumentasi resource atau fitur dalam modul harus ditempatkan dalam direktori `.agent/modules/` dan mengikuti format path berikut:

```
.agent/modules/<nama-module>/(resource).md
```

Contoh:
- `.agent/modules/auth/login.md`
- `.agent/modules/payment/gateway.md`

### 2. Dokumentasi API
Dokumentasi spesifikasi API harus dipisahkan dari dokumentasi modul dan ditempatkan dalam direktori `.agent/api/`.

```
.agent/api/<nama-module>/api-<fitur>.md
```

Contoh:
- `.agent/api/auth/api-login.md`
- `.agent/api/payment/api-gateway.md`

### 3. Dokumentasi Testing
Dokumentasi pengujian (testing) juga harus mengikuti struktur yang sama dan ditempatkan di dalam folder modul terkait.

```
.agent/modules/<nama-module>/testing.md
```
atau spesifik per resource:
```
.agent/modules/<nama-module>/tests/(resource).md
```

Pastikan semua dokumentasi teknis, API, dan pengujian tersentralisasi dengan rapi untuk memudahkan pemeliharaan dan navigasi.
