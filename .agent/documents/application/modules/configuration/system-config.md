# Feature Specification: Configuration System

> Dokumen ini merinci logika dan spesifikasi fitur Configuration.

---

## Header & Navigation

- [Back to Configuration Overview](./overview.md)
- [Link ke API Specification](../../api/configuration/api-configurations.md)

---

## 1. Feature: Dynamic Configuration

### 1.1 Description
Kemampuan mengubah perilaku sistem secara real-time.

### 1.2 Business Logic
1.  **Retrieve:**
    - Cek Redis Cache.
    - Jika ada, kembalikan.
    - Jika tidak, query DB -> convert type -> simpan Redis -> kembalikan.
    
    ```mermaid
    flowchart TD
        Start[Request Config] --> CheckCache{Cache Exists?}
        CheckCache -- Yes --> ReturnCache[Return Value]
        CheckCache -- No --> QueryDB[Query Database]
        QueryDB --> Convert[Convert Type]
        Convert --> SaveCache[Save to Redis]
        SaveCache --> ReturnDB[Return Value]
    ```

2.  **Update:**
    - Update DB.
    - **Invalidate Cache:** Hapus key terkait di Redis agar fetch selanjutnya mengambil data baru.
    - Kirim webhook/event (opsional) jika ada service lain yang perlu tahu perubahan ini secara instan.

### 1.3 Data Types Handling
- `BOOLEAN`: String "true"/"false" -> Native boolean.
- `NUMBER`: String "123" -> Native integer/float.
- `JSON`: String "{...}" -> Parsed Object.

---

## 2. Feature: Feature Flags

### 2.1 Description
Toggle sederhana untuk menyalakan/mematikan fitur.

### 2.2 Logic
- Flags biasanya bertipe `BOOLEAN`.
- Frontend mengecek flags saat inisialisasi aplikasi untuk menyembunyikan/menampilkan menu.
- Backend mengecek flags di Middleware untuk menolak request ke fitur yang dimatikan.

---
