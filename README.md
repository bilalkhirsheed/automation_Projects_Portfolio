# Stripe Manual Approval Booking System (Make.com Automation)

## Purpose

This project implements an automated booking and payment system where Stripe payments are **authorized first and captured only after manual approval**.

The entire solution is built using **Make.com**, leveraging **Stripe PaymentIntents with manual capture**, email-based approval workflows, and persistent data storage to ensure secure and controlled payment handling.

---

## Use Case

This system is designed for businesses that:

- Sell time-based services (e.g. advertising slots, promotions, campaigns)
- Require **manual review and approval** before charging customers
- Want to avoid accidental or unauthorized payments
- Need a clear audit trail for bookings and approvals

Typical use cases include:
- Advertising bookings (1-day / 3-day campaigns)
- Media placements
- Influencer or promotional campaigns
- High-value service reservations

---

## Key Features

- Stripe PaymentIntent with **manual capture**
- Email-based approval flow (Approve / Reject)
- Secure booking identification using UUIDs
- Persistent storage with Make Data Store
- Modular and scalable scenario architecture
- 100% Stripe test mode (safe for development)
- Extendable for calendar blocking and invoicing

---

## Architecture Overview

The automation is structured into three independent Make.com scenarios:

1. **Scenario 01 – Booking & Stripe Authorization**
   - Receives booking requests via webhook
   - Creates a Stripe PaymentIntent (authorization only)
   - Stores booking data in Make Data Store
   - Sends approval email to the administrator

2. **Scenario 02 – Manual Approval (Approve / Reject)**
   - Receives approval decision via webhook
   - Captures or cancels the Stripe PaymentIntent
   - Updates booking status accordingly

3. **Scenario 03 – Post-Capture Processing (Extendable)**
   - Calendar availability blocking
   - Invoice creation (e.g. Lexoffice)
   - Customer confirmation emails

---

## Approval Flow

1. Customer submits a booking request
2. Stripe PaymentIntent is created with manual capture
3. Administrator receives an approval email
4. Administrator approves or rejects the booking
5. Stripe payment is captured or canceled
6. Booking status is updated and stored

---

## Automation Flow Diagram

![Automation Flow](assets/automation-flow.png)

*(Place the PNG diagram inside the `/assets` folder in this repository.)*

---

## Test Mode Notice

This project is configured to run **entirely in Stripe test mode**.

- No live Stripe keys
- No real payments
- Safe for development, testing, and demonstration purposes

---

## Tech Stack

- Make.com
- Stripe API (PaymentIntents – Manual Capture)
- Gmail / SMTP for email approvals
- Make Data Store

---

## License

This project is provided as a reference implementation and portfolio example.
