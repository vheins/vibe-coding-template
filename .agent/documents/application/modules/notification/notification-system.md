# Notification System

> Fitur pengelolaan dan pengiriman notifikasi multi-channel.

---

## Header & Navigation

- [Back to Module Overview](./overview.md)
- [Link to API Specification](../../api/notification/api-notifications.md)
- [Link to Testing Scenario](../../testing/notification/test-notification.md)

---

## 1. Feature Overview

- **Deskripsi singkat fitur:** Orkestra pengiriman notifikasi *omni-channel* (Email, Push, SMS, WebSocket) dengan manajemen antrian dan templat terpusat.
- **Peran dalam modul:** Bertindak sebagai *Communication Hub* yang menjembatani sistem dengan pengguna akhir.
- **Nilai bisnis:** Meningkatkan *retention* dan *engagement* pengguna melalui komunikasi transaksional dan promosi yang tepat waktu dan relevan.

---

## 2. User Stories

### US-NOT-01 — Kirim Kode OTP (2FA)

**Sebagai** Sistem
**Saya ingin** mengirimkan kode OTP via Email/SMS
**Sehingga** user dapat memverifikasi identitasnya

**Acceptance Criteria:**

* Support multi-channel (Email, WhatsApp, SMS)
* Kode OTP berlaku singkat (misal: 2 menit)
* Rate limiting diterapkan untuk mencegah spam
* Template pesan dapat dikonfigurasi

### US-NOT-02 — Update Status Pesanan Real-time

**Sebagai** User
**Saya ingin** menerima notifikasi saat status pesanan berubah
**Sehingga** saya mengetahui progres pembelian saya

**Acceptance Criteria:**

* Notifikasi Push / WebSocket ke aplikasi client
* Trigger otomatis saat event perubahan status terjadi di backend
* Notifikasi tersimpan di inbox aplikasi

### US-NOT-04 — Riwayat Notifikasi (Inbox)

**Sebagai** User
**Saya ingin** melihat riwayat notifikasi saya
**Sehingga** saya tidak ketinggalan info penting

**Acceptance Criteria:**

* List notifikasi dengan status read/unread
* Fitur "Mark as Read"
* Pagination untuk list notifikasi
* Grouping notifikasi berdasarkan kategori (Promo, Transaksi, System)

### US-NOT-05 — Auto Retry Delivery

**Sebagai** Sistem
**Saya ingin** mencoba kirim ulang notifikasi jika gagal
**Sehingga** pesan kritis tetap tersampaikan meski jaringan gangguan

**Acceptance Criteria:**

* Exponential backoff strategy untuk retry
* Maksimal percobaan: 3 kali
* Log error detail jika gagal permanen
* Mekanisme fallback channel (misal: WA gagal -> kirim SMS)

---

## 3. Business Flow & Rules

### 3.1 Business Flow

#### Sending Notification Flow
```mermaid
sequenceDiagram
    participant Client as Client Module
    participant API as Notification API
    participant Queue as Job Queue
    participant Worker as Notification Worker
    participant Provider as Email/Push Provider
    participant DB as Database

    Client->>API: POST /notifications/send
    API->>DB: Validate & Store (Status: Pending)
    API->>Queue: Enqueue Job
    API-->>Client: 202 Accepted

    Queue->>Worker: Process Job
    Worker->>DB: Get Template & Data
    Worker->>Provider: Send Request (SMTP/FCM)
    
    alt Success
        Provider-->>Worker: OK
        Worker->>DB: Update Status: Sent
    else Failure
        Worker->>Queue: Retry
    end
```

### 3.2 Business Rules
- **User Preference:** Jangan kirim jika user Opt-Out.
- **Rate Limit:** Limit OTP (misal 10/jam).
- **Retention:** Log disimpan 1 tahun.

---

## 4. Data Model

- **Notification:** Log pesan (Type, Channel, Status).
- **Template:** Blueprint pesan (`Hello {{name}}`).
- **UserPreference:** Opt-in/out settings.

```mermaid
erDiagram
    Notifications {
        uuid id PK
        string type
        string notifiable_type
        int notifiable_id
        text data
        timestamp read_at
        timestamp created_at
        timestamp updated_at
    }

    NotificationTemplates {
        string code PK
        string channel "mail, database, broadcast"
        text content
        boolean is_active
    }

    UserPreferences {
        int user_id FK
        string channel
        boolean is_enabled
    }

    Notifications }o--|| NotificationTemplates : "uses"
```

---

## 5. Compliance & Audit

- **Anti-Spam:** Hormati Unsubscribe.
- **Security:** Masking OTP di log.

---

## 6. Implementation Tasks

| ID        | Platform | Status | Deskripsi                                       |
| :-------- | :------- | :----- | :---------------------------------------------- |
| NOT-BE-01 | Backend  | Todo   | Setup Notification Service & Queue (Redis/Bull) |
| NOT-BE-02 | Backend  | Todo   | Implement Provider Adapters (Email, Push)       |
| NOT-BE-03 | Backend  | Todo   | Implement API `POST /send` & `GET /list`        |
| NOT-FE-01 | Frontend | Todo   | Implement Notification Bell & Badge             |
| NOT-FE-02 | Frontend | Todo   | Implement Notification List Page                |
