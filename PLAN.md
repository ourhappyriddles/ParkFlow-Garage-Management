## Plan: ParkFlow Garage Management

Build a responsive web and mobile parking platform for managing garage slots, vehicle entry/exit times, pricing, receipts, and future online payments.

### Application Name
**ParkFlow Garage Management**

### Problem Statement
Manual parking records cause inaccurate slot availability, slow entry and exit processing, pricing mistakes, and poor payment tracking. ParkFlow centralizes parking slots, sessions, pricing, payments, and reports.

### Target Users
- Garage administrators
- Entry and exit attendants
- Drivers/customers
- Finance and operations staff

### Main Features
- User authentication and role-based access
- Garage, floor, zone, and slot management
- Live slot availability map
- Vehicle registration by license plate
- Check-in and check-out management
- Entry time, exit time, duration, and ticket number
- Configurable hourly, daily, overnight, tax, discount, and grace-period rates
- Automatic price calculation
- Manual/cash payment recording
- Future payment-provider integration through a provider-neutral payment interface
- Receipts and payment history
- Occupancy, revenue, and utilization reports
- Search, filtering, audit logs, and maintenance status
- Reservation support as a later phase

### Pages/Screens Required
- Login and password reset
- Operations dashboard
- Live parking slot map
- Vehicle check-in
- Active parking sessions
- Vehicle check-out and payment
- Receipt view
- Garage and floor configuration
- Slot management
- Pricing configuration
- Payments and refunds
- Reports and exports
- Users, roles, and audit logs
- Mobile driver/attendant home screen
- Mobile active parking session
- Mobile checkout and receipt
- Mobile parking history

### Technology Stack
- Web: Next.js, TypeScript, responsive CSS or Tailwind CSS
- Mobile: React Native with Expo
- Backend: NestJS or Next.js API routes
- Database: PostgreSQL with Prisma
- Authentication: Auth.js, Supabase Auth, or Clerk
- Realtime updates: WebSockets, Server-Sent Events, or Supabase Realtime
- Validation: Zod
- Testing: Vitest/Jest, Playwright, and Expo tests
- Deployment: Vercel/Azure Static Web Apps, Azure Container Apps, managed PostgreSQL
- Payments: provider adapter supporting Stripe, Razorpay, PayPal, or another provider later

### Project Folder Structure
- `apps/web/` — web dashboard and parking operations
- `apps/mobile/` — Expo mobile application
- `apps/api/` — backend API and business logic
- `packages/domain/` — shared types, validation, and state transitions
- `packages/api-client/` — shared typed API client
- `packages/ui/` — shared UI components and design tokens
- `prisma/` — database schema, migrations, and seed data
- `tests/e2e/` — end-to-end tests
- `docs/` — architecture and deployment documentation
- `PLAN.md` — product and development plan

### Data to Store
- Garage, floor, zone, and slot information
- Slot status: available, occupied, reserved, blocked, maintenance
- Users, roles, and permissions
- Customer and vehicle details
- Parking sessions
- Check-in and check-out timestamps
- Ticket or QR identifiers
- Rate plans and pricing rules
- Calculated price snapshots
- Payments, refunds, provider references, and statuses
- Receipts
- Reservations
- Audit events
- Notifications and reports

Payment card details must not be stored by the application.

### Development Steps
1. Confirm garage rules, rates, taxes, grace periods, roles, and payment methods.
2. Replace the current static registration prototype with a structured application foundation.
3. Define database entities, API contracts, and parking/payment state transitions.
4. Create PostgreSQL schema, migrations, indexes, and sample garage data.
5. Implement authentication, roles, authorization, and audit logging.
6. Implement garage, floor, zone, and slot management.
7. Implement vehicle check-in and slot assignment.
8. Implement active session tracking and check-out.
9. Build and test the pricing engine.
10. Add manual payments, receipts, and provider-neutral payment interfaces.
11. Build web dashboard and operations screens.
12. Build mobile driver and attendant workflows.
13. Add reports, notifications, exports, backups, and monitoring.
14. Test concurrency, pricing, payment failures, webhook retries, accessibility, and responsive layouts.
15. Pilot the system with one garage before expanding.

### Deployment Approach
- Use separate development, staging, and production environments.
- Deploy the web application through Vercel or Azure Static Web Apps.
- Deploy the API through Azure Container Apps or an equivalent container platform.
- Use managed PostgreSQL with automated backups and point-in-time recovery.
- Store secrets in a managed secret store.
- Use HTTPS, protected APIs, webhook verification, and idempotency keys.
- Deploy mobile builds through Expo EAS for internal testing and app-store releases.
- Begin with manual payments, then enable external payment providers through feature flags.
- Release in stages: prototype, staging, single-garage pilot, and production.