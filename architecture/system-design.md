# TalentGate – System Architecture

## High-Level Overview

TalentGate follows a standard client–server architecture with strict role separation.

```
Client (React)
↓
REST API (Express)
↓
Auth & Role Middleware
↓
MongoDB (Mongoose)

```

---

## Frontend Responsibilities
- UI rendering
- Form validation
- Auth state handling
- API consumption
- Role-based routing

---

## Backend Responsibilities
- Authentication (JWT)
- Authorization (role-based)
- Data validation
- Business logic
- API versioning

---

## Authentication Flow

1. User signs up / logs in
2. Server issues JWT
3. Client stores token securely
4. Token sent via `Authorization` header
5. Backend validates token + role

---

## Authorization Model

Roles:
- `jobseeker`
- `employer`

Middleware:
- `requireAuth` → validates identity
- `requireRole` → validates permissions

---

## Database Design (Simplified)

### User
- name
- email
- role
- passwordHash

### Job
- title
- company
- location
- type
- tags
- description
- requirements
- createdBy
- timestamps

---

## Dev vs Production

- Dev-only routes guarded by `NODE_ENV`
- No dev tooling available in production
- Secrets stored in environment variables

---

This architecture is designed to scale while remaining readable and maintainable.
