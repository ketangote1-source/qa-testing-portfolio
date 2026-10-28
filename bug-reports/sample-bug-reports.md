# Sample Bug Reports

Representative defects logged during testing of the InstituteSync ERP & Hostel Portal.
Each follows a standard template: **Summary · Environment · Steps to Reproduce · Expected · Actual · Severity · Priority · Status**.

> Data is illustrative/anonymised. Screenshots would be attached in `../screenshots/`.

---

## BUG-101 — Hostel room allocated beyond capacity

| Field | Detail |
|-------|--------|
| **Module** | Hostel → Room Allocation |
| **Environment** | Chrome 118, Staging, Warden role |
| **Severity** | Critical |
| **Priority** | P1 |
| **Status** | Closed (Fixed & Verified) |

**Steps to Reproduce**
1. Open a room with capacity = 3 that already has 3 residents.
2. Select a 4th student and click "Allocate".

**Expected:** System blocks allocation with "Room is full".
**Actual:** 4th student was allocated; occupancy showed 4/3.
**Notes:** Capacity check missing on server side (only client-side). Verified fixed in build 2.4.1.

---

## BUG-102 — Fee total mismatch when concession applied

| Field | Detail |
|-------|--------|
| **Module** | Fees → Collection |
| **Environment** | Firefox 119, Staging, Staff role |
| **Severity** | High |
| **Priority** | P1 |
| **Status** | Closed (Fixed & Verified) |

**Steps to Reproduce**
1. Open a student with total due ₹50,000.
2. Apply a concession of ₹5,000.
3. Observe the balance due.

**Expected:** Balance due = ₹45,000.
**Actual:** Balance due still showed ₹50,000 until page refresh; receipt printed the wrong amount.
**Notes:** Front-end total not recalculated after concession. Regression added to fee suite.

---

## BUG-103 — Student can open Admin-only report via direct URL

| Field | Detail |
|-------|--------|
| **Module** | Reports / RBAC |
| **Environment** | Chrome 118, Production-like, Student role |
| **Severity** | High |
| **Priority** | P1 |
| **Status** | Open |

**Steps to Reproduce**
1. Log in as a Student.
2. Paste an Admin report URL (e.g. `/reports/collection-summary`) in the address bar.

**Expected:** Access denied / redirect to dashboard.
**Actual:** Report loaded with other students' fee data.
**Notes:** Authorisation enforced in UI menu only, not at route level. Security-sensitive.

---

## BUG-104 — Mobile number field accepts letters

| Field | Detail |
|-------|--------|
| **Module** | Admissions → Enquiry Form |
| **Environment** | Chrome 118, Staging |
| **Severity** | Medium |
| **Priority** | P2 |
| **Status** | Closed (Fixed & Verified) |

**Steps to Reproduce**
1. Open admission enquiry form.
2. Enter `98abc45xyz` in the Mobile field and submit.

**Expected:** Validation error "enter a valid 10-digit mobile number".
**Actual:** Form submitted and saved the invalid value.

---

## BUG-105 — Attendance percentage rounds incorrectly

| Field | Detail |
|-------|--------|
| **Module** | Attendance → Report |
| **Environment** | Edge 118, Staging |
| **Severity** | Medium |
| **Priority** | P2 |
| **Status** | Closed (Fixed & Verified) |

**Steps to Reproduce**
1. Student attended 7 of 9 sessions.
2. View attendance % in report.

**Expected:** 77.78% (or 78% rounded).
**Actual:** Displayed 70%.
**Notes:** Calculation used integer division. Added to regression checklist.

---

## BUG-106 — Session not invalidated after logout

| Field | Detail |
|-------|--------|
| **Module** | Authentication |
| **Environment** | Chrome 118, Staging |
| **Severity** | High |
| **Priority** | P2 |
| **Status** | Open |

**Steps to Reproduce**
1. Log in and open the dashboard.
2. Click Logout.
3. Press the browser Back button.

**Expected:** Redirect to login; no private data shown.
**Actual:** Cached dashboard page remained visible with data.

---

## BUG-107 — Duplicate receipt number on concurrent payment

| Field | Detail |
|-------|--------|
| **Module** | Fees → Receipt |
| **Environment** | Chrome 118, Staging, 2 Staff accounts |
| **Severity** | High |
| **Priority** | P1 |
| **Status** | Closed (Fixed & Verified) |

**Steps to Reproduce**
1. Two staff collect fees for different students at the same instant.

**Expected:** Each receipt gets a unique sequential number.
**Actual:** Both receipts shared the same number.
**Notes:** Race condition in receipt-number generation; fixed with DB-level sequence.

---

### 📊 Defect summary (sample cycle)

| Severity | Count | Fixed | Open |
|----------|-------|-------|------|
| Critical | 1 | 1 | 0 |
| High | 4 | 2 | 2 |
| Medium | 2 | 2 | 0 |
| **Total** | **7** | **5** | **2** |
