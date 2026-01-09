# Feature Specification: Notification System

> Dokumen ini merinci logika dan spesifikasi fitur Notification.

---

## Header & Navigation

- [Back to Notification Overview](./overview.md)
- [Link ke API Specification](../../api/notification/api-notifications.md)

---

## 1. Feature: Sending Notification

### 1.1 Description
Mekanisme standar untuk mengirim notifikasi ke user via berbagai channel.

### 1.2 User Stories
- Sebagai **System**, saya ingin mengirim email konfirmasi pendaftaran agar user memvalidasi akunnya.
- Sebagai **Admin**, saya ingin mengirim push notification promo agar user membuka aplikasi.

### 1.3 Business Logic
1.  **Validasi Request:** Cek apakah `user_id` valid dan `template_code` ada.
2.  **Check Preference:** Cek apakah user mematikan notifikasi tipe tersebut.
3.  **Render Template:** Menggabungkan template dengan variable data.
4.  **Queueing:** Masukkan ke antrian agar response API cepat.
5.  **Dispatch:** Worker mengambil job dan mengirim ke 3rd party provider.

### 1.4 Constraints
- Ukuran payload maksimal 10KB.
- Attachment email maksimal 5MB.

---

## 2. Feature: In-App Notification Center

### 2.1 Description
Fitur bagi user untuk melihat riwayat notifikasi di dalam aplikasi.

### 2.2 User Stories
- Sebagai **User**, saya ingin melihat daftar notifikasi saya.
- Sebagai **User**, saya ingin menandai notifikasi sebagai "sudah dibaca".

### 2.3 Business Logic
- **List:** Menampilkan notifikasi terurut dari yang terbaru.
- **Pagination:** Menggunakan cursor-based pagination.
- **Unread Count:** Menghitung jumlah notifikasi dengan status `SENT`.

---

## 3. Feature: Template Management

### 3.1 Description
CRUD Template notifikasi agar pesan dinamis dan mudah diubah.

### 3.2 Business Logic
- Template mendukung syntax Mustache/Handlebars: `Halo {{name}}, kode Anda {{code}}`.
- Template memiliki versi (audit trail).

---
