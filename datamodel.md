# 🗂️ BridgeNote Data Model

## 🧩 Entity Overview

- **User**
- **Note**
- **Notebook**
- **Tag**
- **CRM Account**
- **CRM Contact**
- **Meeting**
- **Task**
- **Template**
- **Attachment**
- **IntegrationAccount**
- **Organization**
- **Permission**

---

## 👤 User

Represents an individual user within an organization.

| Field           | Type        | Description                            |
|----------------|-------------|----------------------------------------|
| id             | UUID        | Primary key                            |
| org_id         | UUID        | FK to `Organization`                  |
| name           | String      | Full name                              |
| email          | String      | Unique email                           |
| role           | Enum        | ['admin', 'member']                    |
| created_at     | Timestamp   | Account creation timestamp             |
| last_login     | Timestamp   | Last login timestamp                   |

---

## 🏢 Organization

Represents an enterprise team or company.

| Field       | Type      | Description                  |
|------------|-----------|------------------------------|
| id         | UUID      | Primary key                  |
| name       | String    | Company name                 |
| domain     | String    | Email domain                 |
| plan       | Enum      | ['free', 'pro', 'enterprise']|
| created_at | Timestamp | Creation timestamp           |

---

## 📓 Notebook

Organizational container for notes.

| Field       | Type      | Description                |
|------------|-----------|----------------------------|
| id         | UUID      | Primary key                |
| user_id    | UUID      | FK to `User`               |
| org_id     | UUID      | FK to `Organization`       |
| title      | String    | Notebook title             |
| created_at | Timestamp |                            |

---

## 📝 Note

Core content unit for users.

| Field         | Type      | Description                              |
|--------------|-----------|------------------------------------------|
| id           | UUID      | Primary key                              |
| notebook_id  | UUID      | FK to `Notebook`                         |
| user_id      | UUID      | FK to `User`                             |
| crm_account_id | UUID (nullable) | FK to `CRMAccount`             |
| title        | String    | Note title                               |
| content      | Text      | Rich text or markdown                    |
| summary      | Text      | AI-generated summary                     |
| created_at   | Timestamp |                                          |
| updated_at   | Timestamp |                                          |

---

## 🏷️ Tag

Tags for categorizing notes.

| Field     | Type  | Description         |
|----------|-------|---------------------|
| id       | UUID  | Primary key         |
| name     | String| Tag name (lowercase)|
| user_id  | UUID  | FK to `User`        |

**Note_Tag (join table)**

| note_id | UUID |
| tag_id  | UUID |

---

## 🧩 CRMAccount

CRM deal/account record reference.

| Field         | Type    | Description                 |
|--------------|---------|-----------------------------|
| id           | UUID    | Primary key                 |
| external_id  | String  | CRM system ID               |
| name         | String  | Account name                |
| crm_provider | Enum    | ['salesforce', 'hubspot']   |
| synced_at    | Timestamp | Last sync time            |

---

## 👥 CRMContact

CRM-linked contacts tied to notes or meetings.

| Field         | Type    | Description                  |
|--------------|---------|------------------------------|
| id           | UUID    | Primary key                  |
| account_id   | UUID    | FK to `CRMAccount`           |
| name         | String  | Contact name                 |
| email        | String  | Email address                |
| role         | String  | Role at account              |

---

## 📅 Meeting

Linked meeting notes or transcriptions.

| Field       | Type      | Description                        |
|------------|-----------|------------------------------------|
| id         | UUID      | Primary key                        |
| note_id    | UUID      | FK to `Note`                       |
| video_url  | String    | Optional call recording link       |
| transcript | Text      | Auto-generated transcript          |
| summary    | Text      | AI-generated summary               |
| meeting_at | Timestamp | Meeting start time                 |

---

## ✅ Task

Extracted or manually added action items.

| Field       | Type      | Description                  |
|------------|-----------|------------------------------|
| id         | UUID      | Primary key                  |
| note_id    | UUID      | FK to `Note`                 |
| title      | String    | Task name                    |
| assigned_to| UUID      | FK to `User`                 |
| due_date   | Date      | Optional due date            |
| status     | Enum      | ['open', 'done', 'overdue']  |

---

## 🧰 Template

Standardized note structures for sellers.

| Field       | Type      | Description                    |
|------------|-----------|--------------------------------|
| id         | UUID      | Primary key                    |
| org_id     | UUID      | FK to `Organization`           |
| title      | String    | Template name                  |
| content    | Text      | Markdown or HTML template body |
| type       | Enum      | ['discovery', 'qbr', 'custom'] |

---

## 📎 Attachment

Files, images, and media embedded in notes.

| Field       | Type      | Description                     |
|------------|-----------|---------------------------------|
| id         | UUID      | Primary key                     |
| note_id    | UUID      | FK to `Note`                    |
| file_name  | String    | Original filename               |
| mime_type  | String    | MIME type                       |
| url        | String    | CDN or storage location         |

---

## 🔗 IntegrationAccount

External service tokens and connections.

| Field         | Type    | Description                          |
|--------------|---------|--------------------------------------|
| id           | UUID    | Primary key                          |
| user_id      | UUID    | FK to `User`                         |
| service      | Enum    | ['evernote', 'onenote', 'salesforce']|
| access_token | String  | Encrypted OAuth token                |
| expires_at   | Timestamp | Token expiry date                  |

---

## 🛡️ Permission (RBAC)

Defines roles and access scopes.

| Field       | Type    | Description                        |
|------------|---------|------------------------------------|
| id         | UUID    | Primary key                        |
| org_id     | UUID    | FK to `Organization`               |
| user_id    | UUID    | FK to `User`                       |
| role       | Enum    | ['admin', 'manager', 'member']     |
| scope      | JSON    | Granular permission rules (optional) |

---
