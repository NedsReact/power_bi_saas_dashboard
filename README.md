# SaaS Power BI Dashboard (Embedded Analytics)

A production-style SaaS dashboard that embeds Power BI reports into a web app with authentication, tenant-aware access, and a backend that manages workspaces/datasets, refresh, and audit events.

**Live demo:** <ADD_DEMO_LINK>  
**Case study:** <ADD_PORTFOLIO_LINK>  
**Contact:** <ADD_LINKEDIN_OR_EMAIL>

---

## What this is
This project demonstrates how to ship **Power BI as a SaaS feature**:
- Users log in
- They see dashboards filtered to their tenant (company / client / workspace)
- The app generates **embed tokens** securely server-side
- Data model supports scalable reporting (star schema + optimized DAX)

> If you’re evaluating me for BI delivery sprints: this repo shows end-to-end delivery (modeling → DAX → embedding → refresh → security).

---

## Key features
- **Embedded Power BI** report(s) in a web UI (slicers, drill-through, tooltips)
- **Tenant-aware access** (each tenant mapped to workspace/report/dataset)
- **Row-Level Security (RLS)** support (optional; recommended for shared datasets)
- **Embed token generation** via backend (no secrets in frontend)
- **Dataset refresh orchestration** (manual + scheduled) + refresh status
- **Health & audit logs** (who viewed what / refresh events / errors)
- Optional: export, bookmarks, deep links, alerting hooks

---

## Tech stack (edit to match your repo)
- **Power BI:** semantic model (PBIX), Power Query (M), DAX measures, RLS roles  
- **Frontend:** React + TypeScript (Vite/Next.js)  
- **Backend:** .NET (ASP.NET Core Web API) or FastAPI (choose yours)  
- **Database:** PostgreSQL / SQL Server (tenants, users, embeds, logs)  
- **Auth:** Entra ID (Azure AD) / Auth0 / Clerk (choose yours)  
- **Infra:** Docker Compose for local; Azure (App Service/Container Apps) for prod

---

## Screenshots
> Add images to `docs/screenshots/` and link them here.

- Overview
- Tenant filter / permissions view
- Report page with slicers + drill-through
- Refresh status screen

Example:
![Dashboard](docs/screenshots/dashboard.png)

---

## Architecture (high level)
**Embedding flow (typical “App Owns Data” style):**
1. Frontend requests an embed config for a report
2. Backend validates user + tenant permissions
3. Backend uses service principal to call Power BI REST API
4. Backend returns: `embedUrl`, `reportId`, `accessToken` (embed token), settings
5. Frontend embeds report via Power BI JS SDK

**Security principles**
- Power BI secrets stay **server-side only**
- Tenant/report mapping is enforced in backend (not by UI)
- Prefer **RLS** if tenants share datasets

---

## Repo structure (example)

