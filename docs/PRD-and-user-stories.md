# PRD — Monh Batch Delivery Management System
**Version:** 1.0 | **Status:** Shipped | **PM:** Asma Siddiqi

---

## 1. Problem Statement
COVID-19 lockdown triggered 3–5x order volume spike on Monh wholesale platform. Existing first-come-first-served system had no capacity management, no geographic batching, and no buyer visibility — resulting in 55%+ missed deliveries, stockouts, and cancellations.

## 2. Goals
1. Restore on-time delivery rate to >85% within 4 weeks
2. Reduce delivery route inefficiency through geographic zone batching
3. Protect high-velocity SKU inventory for priority accounts
4. Give buyers real-time visibility into order and delivery status

## 3. Success Metrics
| KPI | Target |
|-----|--------|
| On-Time Delivery Rate | >85% |
| Order Cancellation Rate | <10% |
| Delivery Trip Efficiency | -40% trips via zone batching |
| Inventory Stockout (top 20 SKUs) | <5% occurrence |
| Buyer App Engagement | >70% track orders via app |

## 4. Scope
**In scope:** Slot booking, zone batch clustering, inventory buffer, real-time tracking, ops dashboard
**Out of scope:** Automated route optimisation (manual zone approach for MVP), third-party logistics integration, payment changes

## 5. Risks
| Risk | Mitigation |
|------|-----------|
| Buyers reject slot booking | Offer incentive (priority delivery) for early slot selection |
| Zone clustering increases wait time for some areas | Communicate batch windows clearly upfront |
| Engineering capacity limited during lockdown | Phased delivery — slot booking first, tracking second |

---

# User Stories — Monh Batch Delivery System

## EPIC 1: Delivery Slot Booking

### US-001
**As a** wholesale buyer on Monh,
**I want** to see available delivery slots before placing my order,
**So that** I know when my order will arrive before committing to purchase.

**Acceptance Criteria:**
- Delivery slot selector shown at checkout before payment
- Slots display zone, date, time window, and availability status
- Full slots shown as unavailable — buyer redirected to next available
- Slot confirmed in order confirmation screen and email

---

### US-002
**As a** wholesale buyer,
**I want** to receive a push notification when my delivery slot is confirmed,
**So that** I can plan my receiving operations accordingly.

**Acceptance Criteria:**
- Push notification sent within 60 seconds of order confirmation
- Notification includes: order ID, delivery date, time window, zone
- SMS fallback if push notification not enabled

---

## EPIC 2: Real-Time Order Tracking

### US-003
**As a** wholesale buyer,
**I want** to track my order status in real-time on the Monh app,
**So that** I know exactly where my order is and when to expect it.

**Acceptance Criteria:**
- Order status visible in app: Confirmed → Batch Assigned → Out for Delivery → Delivered
- Push notification triggered at each state change
- Estimated delivery window shown (2-hour window)
- Driver contact number visible 30 minutes before delivery

---

## EPIC 3: Ops Batch Management Dashboard

### US-004
**As an** operations manager,
**I want** to see all orders grouped by delivery zone and time slot,
**So that** I can dispatch drivers efficiently and track batch completion.

**Acceptance Criteria:**
- Dashboard shows orders grouped by Zone A/B/C/D and time slot
- Each order shows: buyer name, address, items, order value, status
- Bulk action: mark entire batch as dispatched / delivered
- Failed delivery flag: re-schedule to next slot with one click

---

### US-005
**As an** operations manager,
**I want** capacity controls that prevent accepting more orders than we can deliver,
**So that** we never overcommit on delivery promises.

**Acceptance Criteria:**
- Each delivery slot has a maximum order cap (configurable by ops admin)
- When cap reached, slot shows as Full — buyers offered next available
- Ops admin can adjust slot capacity in real-time from dashboard
- Alert triggered when slot reaches 80% capacity

---

## EPIC 4: Inventory Buffer Management

### US-006
**As an** inventory manager,
**I want** buffer protection on high-velocity SKUs,
**So that** priority wholesale accounts always have stock available even during surge.

**Acceptance Criteria:**
- Top 20 high-velocity SKUs flagged for buffer protection
- 20% of stock reserved for accounts with 100+ order history
- "Limited Stock" warning shown to non-priority buyers when buffer active
- Replenishment alert triggered when buffer drops below 10%

---

## EPIC 5: Demand Forecasting

### US-007
**As an** operations manager,
**I want** a 7-day demand forecast by SKU category,
**So that** I can proactively adjust slot capacity and trigger supplier restocking.

**Acceptance Criteria:**
- Forecast built from last 90 days order history, adjusted for surge multiplier
- Top 20 high-velocity SKUs highlighted with restock recommendations
- Supplier lead times mapped against forecast — shortfall risk flagged in red
- Dashboard refreshed daily at 06:00 before ops team start
