# EdTech Unit Economics Simulator

An interactive simulator for online course unit economics. It shows how completion rate, CAC, OpEx, and repeat rate connect — and where a cohort's money actually leaks, from enrollment through to repeat purchase.

## Why this matters

In EdTech it's easy to optimize one metric in isolation: cut price to boost completion rate, and gross margin quietly collapses. Trim OpEx on mentor support, and drop-off climbs. This simulator makes those tradeoffs visible — move one parameter and watch LTV:CAC and cohort profit respond in real time.

## What's inside

**Controllable inputs:**
- Learners per cohort
- Course price
- Completion rate (share of learners who finish)
- CAC — customer acquisition cost per learner
- OpEx — delivery cost per learner (mentors, support, hosting)
- Repeat rate — share of graduates who buy the next course

**Computed metrics:**
- Drop-off (the mirror of completion rate)
- LTV per learner
- LTV : CAC — the core unit economics health check; below 3:1 is flagged as a risk zone
- Gross margin
- Net cohort profit

**Calculation model:**
```
Completers        = Learners × Completion rate
Repeat buyers      = Completers × Repeat rate
Revenue           = Learners × Price + Repeat buyers × Price
Total OpEx        = Learners × OpEx per learner
Total CAC         = Learners × CAC per learner
Cohort profit     = Revenue − Total OpEx − Total CAC
LTV               = Price + Price × Repeat rate × Completion rate
LTV : CAC         = LTV / CAC
```

The model is intentionally simplified (linear, no month-over-month retention decay or seasonality) — the goal isn't a precise P&L, it's fast intuition for product decisions.

## How to run

Open `edtech_unit_economics_simulator.html` in any browser. It runs offline — all calculations happen client-side, nothing is sent anywhere. The only external dependency is Chart.js, pulled from a CDN on first load (needs internet once).

## Stack

Vanilla HTML/CSS/JS + Chart.js for the funnel visualization. No build step, no backend — drop it into a portfolio, a Notion page, or a deck.

## Possible extensions

- Monthly retention / cohort decay for subscription-style models
- Side-by-side scenario comparison (A/B on parameters)
- Export current values to CSV/PDF for a pitch deck
- Sensitivity analysis per parameter (tornado chart)
