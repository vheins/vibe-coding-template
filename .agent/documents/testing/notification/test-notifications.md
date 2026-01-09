# Test Scenarios: Notification

## 3. Test Scenarios (Backend / API)

### 3.1 Sending Notification

| ID | Test Case | Pre-condition | Input Data | Expected Result | Priority |
| :--- | :--- | :--- | :--- | :--- | :--- |
| NOT-API-01 | Send Email Successfully | Valid Token | `type: email`, `template: OTP` | 202 Accepted, Job ID returned | High |
| NOT-API-02 | Send with Invalid Template | Valid Token | `template: INVALID` | 422 Unprocessable Entity | Medium |
| NOT-API-03 | Send to Opt-out User | User disabled email | `type: email` | 202 Accepted (but logic should drop it silently or log skip) | Low |

### 3.2 Reading Notification

| ID | Test Case | Pre-condition | Input Data | Expected Result | Priority |
| :--- | :--- | :--- | :--- | :--- | :--- |
| NOT-API-04 | List Notifications | User has notifs | `page[size]=10` | 200 OK, List of 10 items | High |
| NOT-API-05 | Mark as Read | User has unread | `is_read: true` | 200 OK, attribute updated | Medium |

---

## 4. Frontend Testing Scenarios

| ID | Flow Name | Steps | Expected Outcome |
| :--- | :--- | :--- | :--- |
| NOT-FE-01 | View Notification List | Click Bell Icon | Dropdown opens, list loads |
| NOT-FE-02 | Realtime Update | Trigger BE API | Badge count increases without refresh |
