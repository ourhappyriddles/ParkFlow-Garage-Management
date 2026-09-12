# ParkFlow Garage Management

ParkFlow is a responsive parking garage operations prototype for tracking garage slots, vehicle check-in and checkout, parking duration, and estimated pricing.

The project currently runs as a lightweight static web application and is designed to evolve into a web, mobile, and backend platform.

## Current Features

- Garage operations dashboard
- Current occupancy and available slot counts
- Live parking slot map
- Active parking sessions table
- Vehicle license plate registration
- Vehicle type selection
- Slot assignment during check-in
- Entry time tracking
- Parking duration calculation
- Hourly price calculation
- Vehicle checkout flow
- Pending payment status for future payment-provider integration
- Responsive desktop and mobile layout
- Navigation placeholders for sessions, layout, payments, rates, and reports

## Project Files

- `index.html` - Application markup and dashboard screens
- `styles.css` - Responsive layout, visual styles, and design tokens
- `script.js` - Local parking session state and application interactions
- `PLAN.md` - Product development and deployment plan

## Run Locally

No build tools or package installation are required for the current prototype.

1. Open the project folder in Visual Studio Code.
2. Open `index.html` in a browser.
3. Select **New parking session** to check in a vehicle.
4. Enter a license plate, choose a vehicle type and available slot, then start the session.
5. Use the arrow action in the active sessions table to check out a vehicle and calculate its current price.

For a more reliable local server, run one of the following from the project folder:

```powershell
python -m http.server 8080
```

Then open <http://localhost:8080>.

If Python is unavailable and Node.js is installed, use:

```powershell
npx serve .
```

## Pricing Behavior

The prototype uses a base rate of `$4 per hour`.

- Parking time is rounded up to the next full hour.
- A minimum chargeable duration of 15 minutes is applied.
- The checkout confirmation displays the calculated amount.
- The current prototype records the payment as pending because no backend or payment provider is connected.

## Current Limitations

This is a local prototype. It does not yet include:

- Database persistence
- User authentication or role-based access
- Multi-user synchronization
- Backend API
- Production payment processing
- Payment webhooks or refunds
- Reservations
- Garage hardware or gate integration
- Production receipt storage and notifications

Refreshing the page resets the sample parking data and any sessions created during the current browser session.

## Planned Architecture

The next implementation phase can follow the architecture in `PLAN.md`:

- Next.js and TypeScript web application
- React Native with Expo mobile application
- NestJS or Next.js backend API
- PostgreSQL with Prisma
- Shared domain types and API client
- Provider-neutral payment adapter for Stripe, Razorpay, PayPal, or another provider
- Managed hosting with separate development, staging, and production environments

Payment card details should never be stored by the application. Payment processing should be handled by a PCI-compliant provider through server-side APIs and verified webhooks.

## Validation Checklist

Before deployment, verify:

- Check-in prevents assignment of occupied slots.
- Checkout calculates the expected amount for short and long sessions.
- Slot counts update after check-in and checkout.
- Layout works on desktop, tablet, and mobile widths.
- Payment failures, retries, refunds, and webhook replays are handled by the backend.
- Authentication, authorization, audit logging, backups, and monitoring are configured.

## License

This project does not currently define a production license.
