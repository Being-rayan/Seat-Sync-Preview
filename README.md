# SeatSync

SeatSync is a full-stack train seat exchange platform where verified passengers on the same train and coach can inspect a live coach map, view exchange preferences, send swap requests, and complete a seat exchange only after both passengers give final consent.

**Live Demo:** https://seatsync-nine.vercel.app/  
**Source Code:** Private  
**Preview Repository:** Documentation and project showcase only

---

# Project Overview

SeatSync solves a practical passenger problem where travelers often want to exchange berths inside the same train coach but lack a proper digital workflow for verification, request handling, and mutual approval.

The platform provides a controlled seat-exchange environment where passengers can:

- Verify journey details
- Access a coach-specific live seat map
- Inspect verified passenger seats
- Send exchange requests
- Accept or reject incoming requests
- Complete swaps after two-sided final confirmation

The system focuses on trust, fairness, and real-time interaction between passengers.

---

# Key Features

- Passenger signup and login system
- JWT-based authentication
- Password hashing using `bcrypt`
- Journey verification using seeded records
- Protected passenger-only routes
- Live coach seat map
- Sleeper, 3AC, 2AC, and 1AC coach layouts
- Seat state visualization system
- Passenger exchange preference support
- Complete swap request lifecycle management
- Duplicate active request prevention
- Mutual final confirmation before reassignment
- In-app notification updates
- Profile and exchange history tracking
- Polling-based real-time refresh
- Vercel deployment support

---

# Seat Exchange Workflow

```text
Passenger creates account
        |
Passenger logs in
        |
Passenger verifies journey
        |
SeatSync unlocks coach seat map
        |
Passenger selects another seat
        |
Swap request is created
        |
Receiver accepts or rejects
        |
Both passengers final confirm
        |
SeatSync completes the swap
        |
Seat assignments and history update
```

---

# Demo Credentials

All demo accounts use:

```text
Password: Travel@123
```

| Passenger | Email | Coach Seat |
|---|---|---|
| Aarav Sharma | `aarav@seatsync.dev` | S1, 41 Lower |
| Diya Menon | `diya@seatsync.dev` | S1, 42 Middle |
| Vihaan Kapoor | `vihaan@seatsync.dev` | S1, 43 Upper |
| Tara Iyer | `tara@seatsync.dev` | S1, 47 Side Lower |
| Omar Khan | `omar@seatsync.dev` | S1, 48 Side Upper |

---

# Demo Testing Flow

1. Open the live demo
2. Login using `aarav@seatsync.dev`
3. Open the live seat map
4. Select another passenger seat
5. Send a swap request
6. Open another browser or incognito window
7. Login using another demo account
8. Accept the incoming request
9. Final confirm from both accounts
10. SeatSync completes the seat exchange workflow

---

# Journey Verification Samples

New users can verify seeded journey records using the following examples:

| Reference | Passenger | Date | Train | Coach | Seat | From | To |
|---|---|---|---|---|---|---|---|
| `PNR-900111` | Ishaan Kapoor | `2026-05-18` | 12901 Rajdhani Express | S1 | 5 | New Delhi | Bhopal |
| `PNR-900211` | Ananya Roy | `2026-05-19` | 12627 Karnataka Express | B1 | 35 | Bengaluru City | New Delhi |
| `PNR-900311` | Rahul Verma | `2026-05-20` | 12951 Mumbai Rajdhani | A1 | 17 | Mumbai Central | New Delhi |
| `PNR-900411` | Neha Arora | `2026-05-21` | 12301 Howrah Rajdhani | H1 | 7 | Howrah | New Delhi |

---

# Tech Stack

## Frontend

- React
- Vite
- React Router
- Axios
- JavaScript
- CSS

## Backend

- Node.js
- Express.js
- JWT Authentication
- bcrypt Password Hashing
- Helmet
- CORS
- PostgreSQL-ready repository layer
- In-memory demo runtime

## Deployment

- Vercel
- Static Vite frontend
- Express API exposed through `/api`
- Serverless API wrapper configuration

---

# Backend API Surface

| Area | Endpoints |
|---|---|
| Auth | `POST /api/auth/register`, `POST /api/auth/login`, `GET /api/auth/me` |
| Journey | `POST /api/journey/verify`, `GET /api/journey/current`, `PATCH /api/journey/preference` |
| Seats | `GET /api/journeys/:journeyId/seats` |
| Swaps | `POST /api/swaps`, `GET /api/swaps/incoming`, `GET /api/swaps/outgoing`, `GET /api/swaps/:id` |
| Swap Actions | `PATCH /api/swaps/:id/accept`, `PATCH /api/swaps/:id/reject`, `PATCH /api/swaps/:id/cancel`, `PATCH /api/swaps/:id/final-confirm` |
| Notifications | `GET /api/notifications`, `PATCH /api/notifications/:id/read` |
| Health | `GET /api/health` |

---

# Database Design

The backend architecture is structured around these core entities:

- `users`
- `journeys`
- `passenger_journeys`
- `seats`
- `swap_requests`
- `notifications`
- `audit_logs`

The schema supports:

- Verified passenger journeys
- Assigned seat tracking
- Original seat preservation
- Swap request lifecycle management
- Notification storage
- Audit logging

---

# Validation And Testing

Verified checks include:

- Production frontend deployment validation
- API health endpoint verification
- Protected route authentication checks
- Demo login verification
- Journey verification workflow testing
- Seat map rendering validation
- Swap creation workflow testing
- Duplicate request prevention testing
- Mutual confirmation workflow testing
- Frontend production build validation

---

# Current Limitations

- Journey verification uses seeded demo records
- No live railway API integration
- Polling-based updates instead of WebSockets
- Public deployment uses in-memory demo data
- Source code remains private

This repository exists only for project showcase, workflow explanation, and recruiter preview.

---

# What This Project Demonstrates

- Full-stack application architecture
- Authentication and authorization workflows
- Real-world business rule implementation
- Dynamic train coach seat-map rendering
- Backend validation and service-layer logic
- API-driven frontend state management
- Production deployment using Vercel
- Multi-user mutual-confirmation workflows

---

# Author

Rayan Qamar
