# Primeira Onda OPS

**A real-world operations management system built for a surf school.**

Primeira Onda OPS was developed to replace manual operational workflows with a centralized web application for managing students, lesson scheduling, packages, payments, instructors and day-to-day school operations.

> Production source code is private. This repository is a public case study of the project.

---

## The problem

The school's operation depended heavily on manual coordination and information distributed across conversations, memory and isolated controls.

That creates predictable problems as the operation grows:

- scheduling becomes harder to coordinate;
- student and package information is fragmented;
- credit usage can become difficult to track;
- instructor assignments and payouts require manual control;
- financial and operational information are easy to mix together;
- access to sensitive information needs to vary by team role.

The goal of Primeira Onda OPS was to turn those workflows into a single operational system designed around how the school actually works.

---

## The solution

Primeira Onda OPS centralizes the school's core workflows in a mobile-first application.

### Main features

- Student registration, search and management
- Surf lesson scheduling
- Standard and exceptional lesson times
- Multi-student and multi-instructor lessons
- Package and credit management
- Payment tracking
- Operational status and lesson completion flows
- Instructor earnings and payout control
- Role-based access for owner, administrators and instructors
- Instructor-specific schedule views
- Operational and financial summaries
- Progressive Web App (PWA) installation on supported devices

The system was designed for a real business workflow rather than as a generic CRUD application.

---

## Business rules modeled in software

Some examples of operational rules handled by the system:

- lessons normally last 90 minutes;
- one lesson may include multiple students and instructors;
- package credits are tracked per participant;
- credits cannot be consumed from unpaid packages;
- lesson completion determines credit consumption;
- instructor earnings are generated per completed lesson;
- payouts are tracked separately from earnings;
- instructor access is restricted to the information required for their own work;
- sensitive administrative and financial operations are restricted by role.

Historical purchases, prices, credit movements and financial records are preserved instead of being recalculated from current catalog values.

---

## Architecture

Primeira Onda OPS uses a lightweight full-stack architecture designed for a small business application with strong data integrity requirements.

### Frontend

- React
- TypeScript
- Vite
- Tailwind CSS
- React Router

### Backend & data

- Supabase Auth
- PostgreSQL
- Row Level Security (RLS)
- PostgreSQL functions / RPCs
- Supabase Edge Functions

### Delivery

- Cloudflare Pages
- Progressive Web App
- Responsive, mobile-first interface

The browser receives only public application configuration. Privileged operations remain server-side.

---

## Security & data integrity

A major goal of the project was to avoid relying only on frontend validation.

Business-critical rules are enforced through database and server-side mechanisms such as:

- Row Level Security
- role-based authorization
- database constraints
- transactional operations
- idempotency protections
- concurrency-aware flows
- restricted privileged functions
- audit-friendly historical records

The application is designed to prevent common problems such as duplicate actions, unauthorized role escalation, cross-user data access and partial financial operations.

---

## Testing & reliability

The project uses automated regression testing as a core part of development.

Current project checks include:

- unit and integration tests
- SQL and authorization tests
- UI behavior tests
- regression coverage
- linting
- TypeScript validation
- production build validation
- PWA validation

At the current stage, the project has reached **475 automated tests across 86 test files**, with lint, TypeScript and build checks passing in the latest recorded validation.

Critical changes are generally developed using a workflow similar to:

**RED → GREEN → REGRESSION**

Automated testing is combined with manual validation for real user flows and environment-specific behavior.

---

## Progressive Web App

Primeira Onda OPS can be installed as a PWA on supported Android and iOS devices.

The PWA layer is intentionally conservative:

- application assets can be cached;
- Supabase/Auth/business responses are not cached for offline operation;
- business modules still require connectivity;
- updates are explicitly offered to the user instead of forcing a reload during an active form.

---

## Project status

The system is in active development and has already completed its main operational modules.

The production repository remains private because it contains the real implementation and business-specific logic.

This public repository exists to document the architecture, product thinking and engineering work behind the project.

---

## Screenshots

Screenshots and interface walkthroughs will be added here as the public portfolio version is prepared.

---

## What this project demonstrates

Primeira Onda OPS represents the type of work I focus on building:

- software designed around real operational problems;
- custom internal business systems;
- automation of manual workflows;
- reliable data and permission models;
- interfaces designed for actual day-to-day use;
- rapid development without treating quality and testing as optional.

---

## Developer

**Juan Vieira**  
Software Developer

[GitHub Profile](https://github.com/juanbvdev)
