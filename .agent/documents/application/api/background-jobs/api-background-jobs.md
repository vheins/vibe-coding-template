# API Specification: Background Jobs

> Dokumen ini berisi spesifikasi teknis API untuk fitur Background Jobs & Queue management.
> Sebagian besar interaksi melalui Redis, namun API HTTP disediakan untuk monitoring/trigger manual.

---

## 1. Global Standards

- **Base URL:** `/api/v1/jobs`
- **Content-Type:** `application/vnd.api+json`

---

## 2. Endpoints

### 2.1 Get Job Status

- **URL:** `GET /:queueName/:jobId`
- **Description:** Mengambil status job tertentu (Completed/Failed/Active).
- **Access Control:** Authenticated (Admin/System).

#### Request

**Headers:**
```http
Authorization: Bearer <token>
```

#### Response

**Success (200):**
```json
{
  "data": {
    "type": "job_status",
    "id": "123",
    "attributes": {
        "status": "completed",
        "progress": 100,
        "result": { "exported_file": "https://..." }
    }
  }
}
```

---

### 2.2 Retry Failed Job

- **URL:** `POST /:queueName/:jobId/retry`
- **Description:** Menjalankan ulang job yang gagal.

#### Response

**Success (200):**
```json
{
  "meta": {
    "message": "Job retried successfully"
  }
}
```
