---
type: project
status: idea
tags: [saas, product, azure]
updated: 2026-09-03
---


# AI Prompt Library

Multi-tenant SaaS: an AI prompt library with RBAC, versioning, audit logging, and compliance (SOC 2, GDPR).

## Architecture (from requirements session)
- Isolated Azure SQL database per tenant
- Auth via Microsoft Entra with Graph-based group resolution
- Three-role RBAC: Viewer / Editor / Admin
- Separate visibility dimension for sensitive collections
