# Test Scenarios: Configuration

## 3. Test Scenarios (Backend / API)

### 3.1 Managing Configuration

| ID | Test Case | Pre-condition | Input Data | Expected Result | Priority |
| :--- | :--- | :--- | :--- | :--- | :--- |
| CFG-API-01 | Update Config Value | Admin Logged In | `value: "new_value"` | 200 OK, Value updated in DB | High |
| CFG-API-02 | Cache Invalidation | Config cached | Update Value | Next GET returns new value | High |
| CFG-API-03 | Prevent Duplicate Key | Key exists | Create same Key | 409 Conflict | Medium |

### 3.2 Fetching Configuration

| ID | Test Case | Pre-condition | Input Data | Expected Result | Priority |
| :--- | :--- | :--- | :--- | :--- | :--- |
| CFG-API-04 | Get Public Configs | None | None | 200 OK, Only `is_public=true` items | High |
| CFG-API-05 | Get All Configs | Admin Logged In | None | 200 OK, All items | Medium |
| CFG-API-06 | Get All Configs | User Logged In | None | 403 Forbidden | High |

---

## 4. Frontend Testing Scenarios

| ID | Flow Name | Steps | Expected Outcome |
| :--- | :--- | :--- | :--- |
| CFG-FE-01 | Edit Config | Admin click edit -> Save | Toast Success, Table updated |
| CFG-FE-02 | Type Validation | Input Text in Number Config | Show validation error |
