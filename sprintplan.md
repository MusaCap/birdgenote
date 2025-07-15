# 🚀 BridgeNote Sprint Plan (for Windsurf)

## ⏱️ Sprint Duration: 2 Weeks  
## 🧪 Sprint Velocity: 20–24 points per sprint (mid-sized agile team)  
## 🎯 Goal: MVP completion in 12 weeks (6 sprints)

---

## 🟢 Sprint 1: Core Note Infrastructure

### 🎯 Goal
Lay the foundational structure for notebooks, notes, users, and tags.

### 📦 Deliverables
- Note and notebook creation
- Rich text editor (MVP)
- Tagging system
- User authentication and organization setup

### 📋 User Stories
- As a user, I want to create rich text notes in a WYSIWYG editor.
- As a user, I want to create and organize notes into notebooks.
- As a user, I want to add and manage tags on notes.
- As a user, I want to log in and join an organization (via email domain).
- As an admin, I want to see and manage users in my organization.

### 🧩 Dependencies
- Backend schema design
- Role and permission scaffolding
- WYSIWYG/Markdown editor integration

---

## 🟡 Sprint 2: OneNote & Evernote Sync Layer

### 🎯 Goal
Enable initial sync from Evernote and OneNote with conflict resolution.

### 📦 Deliverables
- Evernote/OneNote OAuth and import
- Bridge Layer for syncing and format translation
- Basic export to Evernote/OneNote

### 📋 User Stories
- As a seller, I want to import my OneNote/Evernote notes and preserve formatting.
- As a seller, I want my notebooks and tags to sync properly.
- As a system, I want to use AI to resolve content conflicts during sync.
- As a seller, I want to export my BridgeNote notes to external apps.

### 🧩 Dependencies
- Notes infrastructure from Sprint 1
- Stable API keys for Microsoft Graph/Evernote API

---

## 🔵 Sprint 3: CRM & Meeting Integration (Part 1)

### 🎯 Goal
Connect to CRMs and begin logging meeting metadata and notes.

### 📦 Deliverables
- Salesforce and HubSpot OAuth
- Note-to-opportunity linking
- Calendar + meeting metadata ingestion

### 📋 User Stories
- As a seller, I want to link notes to opportunities or accounts in Salesforce.
- As a seller, I want to view account details inside my notes.
- As a seller, I want to auto-link calendar invites to notes.
- As an admin, I want to configure which CRM fields to sync.

### 🧩 Dependencies
- CRM API access
- Notes + user identity layer

---

## 🔴 Sprint 4: AI Layer (Summarization, Tags, Tasks)

### 🎯 Goal
Implement core AI services: summarization, action item extraction, smart tags.

### 📦 Deliverables
- OpenAI Whisper + GPT integration
- AI-generated summaries from note or transcript
- Task generation and tagging via prompt templates

### 📋 User Stories
- As a seller, I want AI to summarize my notes and highlight key takeaways.
- As a seller, I want action items auto-generated from meetings.
- As a seller, I want smart tag suggestions from my note content.
- As an admin, I want to configure AI confidence thresholds.

### 🧩 Dependencies
- Notes + transcript schema
- CRM and meeting data ingestion

---

## 🟣 Sprint 5: Collaboration & Templates

### 🎯 Goal
Enable sharing, templating, and collaborative editing of notes.

### 📦 Deliverables
- Shared notebooks with RBAC
- Pre-built templates (Discovery, QBR, etc.)
- Template editor + versioning
- Real-time co-editing MVP

### 📋 User Stories
- As a seller, I want to use preloaded templates to write meeting notes.
- As a team, I want to co-edit notes in real time.
- As a manager, I want to publish and update templates for my org.
- As a user, I want to comment and mention collaborators in notes.

### 🧩 Dependencies
- Notes infrastructure
- Real-time socket infra (e.g., WebSocket or Firestore)
- Template schema and roles

---

## 🟤 Sprint 6: Security, Reporting & Beta Launch

### 🎯 Goal
Finalize user permissions, analytics, and deliver MVP for beta testing.

### 📦 Deliverables
- SAML/SSO setup (Okta, Azure AD)
- Admin dashboard with activity insights
- Audit logs and permission enforcement
- Bug fixing, polish, and onboarding flow

### 📋 User Stories
- As an admin, I want to onboard users with SAML or domain rules.
- As an admin, I want to see usage metrics, task completion, and note activity.
- As a team lead, I want to audit recent changes to any shared notes.
- As a new user, I want an onboarding flow that introduces BridgeNote features.

### 🧩 Dependencies
- RBAC complete
- Telemetry and logging setup
- Core features tested and hardened

---

# ✅ MVP Release Checklist (Post-Sprint 6)

- [ ] Create marketing site and waitlist
- [ ] Beta user invitation system
- [ ] Support desk setup (chatbot + guides)
- [ ] Feedback capture loop
