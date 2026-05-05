# xuz-ecommerce-demand-surge
# 📦 Monh Wholesale E-Commerce — Demand Surge Management & Batch Delivery System
### Product Management | E-Commerce | Supply Chain | Saudi Arabia

---

## 📌 Project Overview

Monh is a Saudi Arabia-based B2B wholesale e-commerce platform serving bulk buyers across the region. During the COVID-19 lockdown period, the platform experienced an unprecedented surge in demand — order volumes spiked beyond the platform's fulfilment capacity, causing delivery failures, inventory chaos, and customer dissatisfaction.

As the Product Manager brought in to stabilise and redesign the fulfilment operations, I led the end-to-end planning, design, and app integration of a **Batch Delivery System** that allowed Monh to manage surge demand intelligently — prioritising orders, scheduling batch deliveries, and integrating the new logic directly into the Monh app.

---

## 🎯 Problem Statement

### The Surge Situation
- COVID-19 lockdown triggered a 3–5x spike in wholesale order volumes overnight
- Existing system: first-come-first-served order processing — no batching, no prioritisation
- Delivery fleet: fixed capacity, unable to scale immediately
- Inventory: high-velocity SKUs selling out within hours with no replenishment visibility
- Customer experience: missed deliveries, no ETAs, no communication — leading to order cancellations and trust erosion

### Key Failures
1. No demand forecasting — orders accepted beyond delivery capacity
2. No geographic batching — delivery routes inefficient, same area visited multiple times per day
3. No inventory buffer logic — high-demand SKUs not protected for priority customers
4. App had no real-time order status or delivery slot visibility for buyers

---

## 💡 Solution

A Batch Delivery Management System integrated into the Monh app with four core components:

1. Demand Sensing & Order Throttling — accept orders up to daily delivery capacity only
2. *Geographic Batch Clustering* — group orders by delivery zone for route efficiency
3. *Priority Inventory Allocation* — protect stock for high-value wholesale accounts
4. *App Integration* — buyers see available delivery slots, real-time order status, and batch ETAs

---

## 🗺️ System Design

### Batch Delivery Logic

```
ORDER PLACED
     │
     ▼
┌─────────────────────────────────┐
│  CAPACITY CHECK                 │
│  Is today's delivery slot full? │
└──────┬──────────────────────────┘
       │ Yes                 │ No
       ▼                     ▼
  Offer next          Accept order →
  available slot      assign to batch
       │                     │
       └──────────┬──────────┘
                  ▼
       ┌──────────────────────┐
       │  ZONE CLUSTERING     │
       │  Assign to delivery  │
       │  zone batch (A/B/C/D)│
       └──────────┬───────────┘
                  ▼
       ┌──────────────────────┐
       │  INVENTORY CHECK     │
       │  Reserve stock for   │
       │  confirmed orders    │
       └──────────┬───────────┘
                  ▼
       ┌──────────────────────┐
       │  BUYER NOTIFICATION  │
       │  ETA + batch window  │
       │  sent via app + SMS  │
       └──────────────────────┘
```

### Geographic Zone Map (Riyadh)
```
Zone A — Central: 08:00–11:00
Zone B — North:   11:00–14:00
Zone C — East:    14:00–17:00
Zone D — West:    17:00–20:00
```

---

## 🔧 Product Features Built

### Feature 1 — Delivery Slot Booking (App)
- Buyers see available delivery slots before completing order
- Slots show capacity remaining (Full / Limited / Available)
- Slot selection mandatory before checkout
- Slots update in real-time as orders are placed

### Feature 2 — Batch Order Management (Ops Dashboard)
- Operations team sees all orders grouped by zone and time slot
- Route optimisation: orders sorted by delivery sequence within zone
- Bulk status update: mark entire batch as dispatched / delivered
- Exception flagging: failed deliveries re-scheduled to next available slot

### Feature 3 — Inventory Buffer Allocation
- High-velocity SKUs flagged for buffer protection
- 20% of stock reserved for priority wholesale accounts (>100 order history)
- Replenishment alert triggered when buffer drops below threshold
- Buyers see "Limited Stock" warning when buffer is active

### Feature 4 — Real-Time Order Tracking (App)
- Buyers track order through states: Confirmed → Batch Assigned → Out for Delivery → Delivered
- Push notification at each state transition
- Estimated delivery window shown (2-hour batch window, not exact time)
- Contact number for batch driver available 30 mins before delivery

### Feature 5 — Demand Forecasting Dashboard
- 7-day demand forecast by SKU category built from order history
- Identified top 20 high-velocity SKUs for priority restocking
- Supplier lead times mapped against forecast — flagged shortfall risks
- Operations team used daily to adjust next-day slot capacity

---

## 📊 Outcomes

| Metric | Before | After |
|--------|--------|-------|
| On-Time Delivery Rate | ~45% (surge period) | >85% |
| Delivery Route Efficiency | Unstructured | Zone-batched — 40% fewer trips |
| Order Cancellation Rate | High (capacity overload) | Reduced significantly with slot booking |
| Inventory Stockout (top SKUs) | Frequent | Buffer protection reduced stockouts |
| Buyer Satisfaction | Low — no visibility | Real-time tracking + ETAs |
| Ops Team Planning Time | Manual, reactive | Dashboard-driven, proactive |

---

## 🗂️ Repository Structure

```
├── README.md
├── docs/
│   ├── PRD.md                          # Full Product Requirements Document
│   ├── user-stories.md                 # User story backlog
│   ├── batch-delivery-logic.md         # Batch clustering and routing logic
│   └── app-feature-specs.md            # App screen-level feature specifications
├── wireframes/
│   └── delivery-slot-flow.md           # User flow for slot booking
├── metrics/
│   └── surge-management-kpis.md        # KPI tracking framework
└── retrospective/
    └── lessons-learned.md
```

---

## 👤 Role
**Product Manager** — Led end-to-end planning, design, and delivery
- Diagnosed root causes of surge failures through operational data analysis
- Designed batch delivery logic and zone clustering approach
- Wrote PRD, user stories, and app feature specifications
- Coordinated with engineering team on app integration
- Managed stakeholder communication with ops, logistics, and leadership
- Tracked KPIs and iterated on batch logic based on delivery performance data
