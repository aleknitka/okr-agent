# Company OKRs & Business Context — E-commerce Platform

## Strategic Context

We run a marketplace platform connecting independent retailers with consumers across the UK and Ireland. In Q1 2026 we are focused on improving seller retention (sellers leaving for competitors is the top growth threat), preparing the platform for peak summer trading, and reducing the cost of our logistics operations which have grown unsustainably with volume.

## Company Objectives

### CO-1: Improve seller retention by making the platform the most valuable sales channel for independent retailers

**Objective**: Make it demonstrably easier and more profitable for sellers to grow their business on our platform than anywhere else, so that churn drops and active seller count grows.

**Key Results**
1. Reduce monthly seller churn rate from 8.5% to 5% by end of Q1
2. Increase average monthly GMV per active seller from £3,200 to £4,100
3. Achieve a seller NPS of ≥45 (up from current 31) by end of Q1

---

### CO-2: Make the platform reliable and scalable for peak summer trading

**Objective**: Ensure the platform can handle 3× our current peak load without degradation so that the summer trading season does not cause the outages we experienced last year.

**Key Results**
1. Platform sustains 3× peak load in load tests with p99 response time under 800ms by end of March
2. Reduce mean time to recovery from incidents from 47 minutes to under 15 minutes
3. On-call alert volume (actionable pages) reduced by 40% through improved observability and auto-remediation

---

### CO-3: Reduce logistics cost per shipment by 20%

**Objective**: Bring logistics unit economics under control by renegotiating carrier contracts, improving routing efficiency, and reducing failed delivery rates.

**Key Results**
1. Reduce average cost per shipment from £4.80 to £3.84 by end of Q1
2. Reduce failed first-delivery attempts from 14% to 8% of shipments
3. Carrier contract renegotiations complete for at least 3 of our top 5 carriers by end of February

---

## Business Context Notes

- Q1 is typically slower for consumer sales — this is the right time to invest in platform reliability and tooling before the summer peak
- The Seller Experience team owns CO-1; other teams should flag any cross-team dependencies early as the team has limited capacity for unplanned work
- Logistics cost reduction (CO-3) requires data from the Fulfilment team's new warehouse system, which goes live in week 3 — do not plan work that depends on this data before week 4
- There is a platform-wide feature freeze from 15 March to 1 April to allow stabilisation before the spring trading period
