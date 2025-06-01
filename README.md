# Wuji.io

**Wuji.io** is a modern, AI-assisted, multi-tenant CMDB SaaS platform designed for clarity, configurability, and intelligent infrastructure visibility.

---

## 🚀 Product Vision

Wuji.io helps teams manage their configuration items with precision, track change history, and leverage AI to streamline import and insight workflows — built with extensibility for enterprise and MSPs.

---

## ✅ Core MVP Features

### 1. Configuration Item (CI) Management
- CRUD for CIs: Server, Database, App, Network Device, Workstation
- Support for custom fields
- Relationship linking (e.g., “DependsOn”, “ConnectedTo”)
- Grouping by environment, owner, type

### 2. Change Tracking
- Full audit history for each CI
- Before/after snapshot storage
- Optional restore/rollback

### 3. AI-Assisted Import
- Upload CSV/Excel
- LLM auto-suggests field mappings
- Preview before confirmation

### 4. Dashboard
- Summary tiles (CI counts, incidents)
- CI Distribution / Incident Trends charts
- Insight cards (e.g., stale items, missing owners)

### 5. Multi-Tenant Support
- Per-tenant Cosmos DB storage
- UI + back-end tenant-aware routing

### 6. Role-Based Access Control
- Admin, Editor, Viewer roles
- Optional SSO (Google / Microsoft Entra ID)

---

## 🧱 Architecture

### ⚙️ Frontend
- Blazor Server (initial)
- MudBlazor UI framework
- Responsive layout, dark mode, themeable

### 🧠 Backend
- ASP.NET Core (.NET 8)
- Clean architecture (Domain → Application → Infra → Web)
- Background tasks (import processors, insight generation)

### ☁️ Storage
- Azure Cosmos DB (per tenant)
- Azure Key Vault for secrets
- Azure Blob Storage (optional, for files/imports)

### 🔐 Identity
- Azure AD B2C or Auth0
- JWT with claims for tenant/user role
- Third-party login support (Google, Microsoft)

### 🧠 AI Integration
- Azure OpenAI or OpenAI API
- Used for import mapping and insight enrichment

---

## 🔐 Secure Connection Handling

- Cosmos DB connection strings stored in Azure Key Vault
- Resolved dynamically by tenant on login or subdomain
- Accessed via managed identity in Azure App Service

---

## 🚀 Azure Deployment Stack

- Azure App Service or Container App
- Cosmos DB instance
- Azure Key Vault (per-tenant secret)
- App Insights / Log Analytics
- **Bicep Template** auto-deploys:
  - Cosmos DB
  - Key Vault
  - App Service + Identity

---

## 📁 Project Structure

```plaintext
Wuji.sln
├── Wuji.Web           # Blazor Server frontend
├── Wuji.Application   # Application services & interfaces
├── Wuji.Domain        # Core business models
├── Wuji.Infrastructure# Cosmos, AI, Identity access
├── Wuji.Api           # Optional REST API (future)
├── Wuji.Tests         # Unit/Integration tests
