# API Specification: [Feature Name]

> Dokumen ini berisi spesifikasi teknis API untuk fitur [Feature Name].
> Semua endpoint **WAJIB** mengikuti standar **JSON:API** (https://jsonapi.org).

---

## 1. Global Standards

- **Base URL:** `/api/v1`
- **Content-Type:** `application/vnd.api+json`
- **Accept:** `application/vnd.api+json`
- **Date Format:** ISO 8601 (`YYYY-MM-DDTHH:mm:ssZ`)

---

## 2. Endpoints

### 2.1 [Endpoint Name]

- **URL:** `[METHOD] /resource-name`
- **Description:** [Deskripsi singkat endpoint]
- **Access Control:** [Public / Authenticated / Role: Admin]

#### Request

**Headers:**
```http
Content-Type: application/vnd.api+json
Accept: application/vnd.api+json
Authorization: Bearer <token>
```

**Query Parameters:**
- `page[number]`: Page number (default: 1)
- `page[size]`: Items per page (default: 10)
- `filter[field]`: Filter value
- `include`: Related resources to include

**Body:**
```json
{
  "data": {
    "type": "resource_name",
    "attributes": {
      "field_1": "value",
      "field_2": 123
    },
    "relationships": {
      "related_resource": {
        "data": { "type": "related_type", "id": "uuid" }
      }
    }
  }
}
```

#### Response

**Success (2xx):**
```json
{
  "data": {
    "type": "resource_name",
    "id": "uuid",
    "attributes": {
      "field_1": "value",
      "field_2": 123,
      "created_at": "2023-01-01T00:00:00Z"
    },
    "relationships": {
      "related_resource": {
        "links": {
          "self": "/api/v1/resource_name/uuid/relationships/related_resource",
          "related": "/api/v1/resource_name/uuid/related_resource"
        }
      }
    },
    "links": {
      "self": "/api/v1/resource_name/uuid"
    }
  },
  "included": [
    {
      "type": "related_type",
      "id": "uuid",
      "attributes": { ... }
    }
  ]
}
```

**Error (4xx/5xx):**
```json
{
  "errors": [
    {
      "status": "422",
      "source": { "pointer": "/data/attributes/field_1" },
      "title": "Invalid Attribute",
      "detail": "Field_1 must be a string."
    }
  ]
}
```

---

### 2.2 [Endpoint Name 2]

...
