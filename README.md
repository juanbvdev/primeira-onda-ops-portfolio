# Primeira Onda OPS

**English** | [Português](README.pt-BR.md)

**A surf school's day-to-day operations, organized in one place.**

A production application connecting scheduling, students, instructors, packages and financial tracking with a mobile-first Student Portal. Built around a real school's workflows, with business rules and permissions enforced on the backend.

> A public case study of a real product. Source code and operational documentation remain private.

[Features](#features) · [Product walkthrough](#product-walkthrough) · [Architecture](#architecture) · [Engineering and quality](#engineering-and-quality)

## The problem OPS solves

Bookings, credits and payments spread across messages and separate records make it difficult to see the whole operation. The school needs to know who is attending, who is teaching, which credits are available and what has been received — while giving each person access only to the information they need.

OPS brings that work into an application accessible from a phone, with dedicated experiences for management, instructors and students.

## Features

| Area | What the system delivers |
|---|---|
| **Scheduling and lessons** | Booking, rescheduling, cancellation and completion; standard and exceptional times; multiple students and instructors per lesson. |
| **Students and credits** | Student registration and search, packages and one-off lessons, tracking of available, reserved and used credits. |
| **Student Portal** | Lessons, packages and profile details; booking, rescheduling and cancellation requests, with approval and counterproposals. |
| **Team** | Role-based access, instructors' own schedules, earnings, payouts and history. |
| **Financial tracking** | Recorded sales and receipts, pending payments, instructor earnings and payouts, with operational and financial summaries. |
| **Communication** | Web Push operational alerts with access to the relevant notification context. |
| **PWA experience** | Installation on supported devices, mandatory updates when a new version is ready and release notes tailored to each role. |
| **Technical maintenance** | Temporary backend restrictions on operational writes and a maintenance screen, managed independently of the application. |

Portal requests are reviewed by management; a proposed change of date or time requires the student's explicit acceptance. Financial features record and track school operations; **student online checkout is not included**.

## Product walkthrough

All screenshots use **fictional data created for demonstration**.

### Student Portal — designed for mobile

The next lesson, booking requests and credit information in navigation built for students.

| Home | Booking request | Packages and one-off lessons |
|:---:|:---:|:---:|
| <img src="assets/screenshots/portaldoaluno-home.jpg" alt="Student Portal showing the next lesson and main shortcuts" width="230"> | <img src="assets/screenshots/portaldoaluno-agendamento.jpg" alt="Lesson request with date, time and notes" width="230"> | <img src="assets/screenshots/portaldoaluno-pacotes.jpg" alt="Package credits and payment status" width="230"> |

Lesson history and profile editing complete the student experience.

| Lessons | Profile |
|:---:|:---:|
| <img src="assets/screenshots/portaldoaluno-minhas-aulas.jpg" alt="Student Portal lesson history" width="230"> | <img src="assets/screenshots/portaldoaluno-perfil.jpg" alt="Editing personal and contact details in the Student Portal" width="230"> |

### Management — scheduling and lessons

Organize time slots, lessons, students and instructors in a clear view of the school schedule.

<img src="assets/screenshots/agenda.png" alt="Schedule with lessons, students and instructors" width="680">

<details>
<summary>Explore financial tracking, students, packages and instructors</summary>

Sales, receipts, instructor earnings and payouts have distinct meanings and are presented separately.

| Financial overview | Students | Packages and one-off lessons |
|:---:|:---:|:---:|
| <img src="assets/screenshots/financeiro-owner-admin.png" alt="Financial dashboard with period indicators and overall balances" width="230"> | <img src="assets/screenshots/alunos.png" alt="Student search and management using demonstration data" width="230"> | <img src="assets/screenshots/pacotes-e-avulsa.png" alt="Package, one-off lesson and payment management" width="230"> |

| Instructors | Instructor balance and history |
|:---:|:---:|
| <img src="assets/screenshots/instrutores.png" alt="Instructor overview and balances" width="230"> | <img src="assets/screenshots/saldo-instrutor.png" alt="Instructor earnings, payments and history" width="230"> |

</details>

The screenshots illustrate the product interface. This case study does not provide access to production accounts or data.

## Mobile-first PWA experience

- **Installation on supported devices:** app-like access, with a responsive layout on desktop too.
- **Safe updates:** a ready new version requires an update; drafts and pending or uncertain operations block the transition until it is safe to proceed, with coordination across tabs.
- **Protected Push navigation:** the destination opens directly when permitted. During editing or a pending operation, the activity is preserved and the user chooses when to open the notification.
- **Relevant release notes:** optional access to notes and history filtered for management, instructors or students, tied to the installed version.
- **Real maintenance controls:** server-side protection during technical interventions, with clear messaging for users.

The PWA caches static assets; authentication responses and operational data are not cached for offline use. The system requires connectivity for business operations.

## Architecture

| Layer | Technologies and responsibilities |
|---|---|
| **Interface** | React, TypeScript, Vite, Tailwind CSS and React Router. |
| **Identity and data** | Supabase Auth and PostgreSQL, with Row Level Security, constraints, functions and transactional operations. |
| **Backend services** | Supabase Edge Functions for privileged operations and notification processing. |
| **Notifications** | Web Push with VAPID, a PostgreSQL event outbox and delivery tracking; processing through pg_cron and pg_net. |
| **Delivery** | Cloudflare Pages, PWA and a Service Worker for static assets and controlled updates. |
| **Quality** | Vitest, Testing Library, SQL tests, ESLint, TypeScript and build/PWA validation. |

The browser receives only public configuration. Privileged credentials and authorization for sensitive operations stay on the backend.

## Engineering and quality

### Engineering challenges addressed

| Challenge | Approach |
|---|---|
| **Keeping credits and financial records consistent** | Credit reservation and consumption, transactions and idempotency; sales, receipts and payouts handled separately. |
| **Restricting access by responsibility** | Server-side authorization and RLS, with dedicated views for management, instructors and students. |
| **Updating without interrupting a protected activity** | Cross-tab update admission, document and Service Worker identity checks, and protection for forms and operations. |
| **Opening notifications safely** | Session and permission revalidation before navigation, respecting edits, maintenance and updates. |
| **Preserving business history** | Recorded purchases, prices and movements retain their historical terms. |

### Quality as part of delivery

The recorded local validation includes **983 automated tests across 141 test files**, with lint, TypeScript, build and PWA checks passing.

Practices include unit and integration tests, UI behavior, authorization, regression coverage and concurrency scenarios in local PostgreSQL. Critical changes are checked through **RED → GREEN → REGRESSION**.

Delivery combines separate environments, identified artifacts and integrity verification to make each publication traceable.

## Skills demonstrated

- Full-stack development grounded in real operations.
- Data modeling, business rules and access control.
- Mobile-first experiences for users with different needs.
- Integration of PWA, notifications and backend services.
- Regression testing and a controlled delivery process.

## Developer

**Juan Vieira** · Software Developer

[GitHub Profile](https://github.com/juanbvdev)
