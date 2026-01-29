# SaaS Power BI Dashboard (Embedded Analytics)

A production-style SaaS dashboard that embeds Power BI reports into a web app with authentication, tenant-aware access, and a backend that manages workspaces/datasets, refresh, and audit events.

---

## Tech stack 
- **Power BI:** semantic model (PBIX), Power Query (M), DAX measures, RLS roles
  
---

## Screenshots
> Add images to `docs/screenshots/` and link them here.

- Overview
- Tenant filter / permissions view
- Report page with slicers + drill-through
- Refresh status screen

Example:
<img width="3840" height="2063" alt="image" src="https://github.com/user-attachments/assets/b3189c8a-6caf-4e32-a136-0a094d01638d" />


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

## Power BI setup (quick)

- Open PBIP from /pbip/pbip

---

