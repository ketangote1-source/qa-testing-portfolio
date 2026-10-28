# Test Plan — InstituteSync College ERP & Hostel Portal

| Field | Detail |
|-------|--------|
| **Project** | InstituteSync — College ERP (TKIET) & Hostel Portal |
| **Document** | Master Test Plan |
| **Author** | Ketan Gote (QA / Manual Testing Engineer) |
| **Type** | Web application (cloud SaaS, multi-tenant) |
| **Test type** | Manual — Functional, Regression, Smoke, UAT, Cross-browser |

---

## 1. Objective

Validate that the College ERP and Hostel Portal meet functional requirements and perform correctly across all modules, user roles and supported browsers, with no high-severity defects at release.

## 2. Scope

### In Scope
- Authentication & role-based access control (Admin, Staff, Warden, Student)
- Admissions module (enquiry → application → admission)
- Fees module (fee structure, collection, receipts, dues, reports)
- Attendance module (marking, reports, percentage calculation)
- Examination module (marks entry, results, grade cards)
- Hostel module (room allocation, resident records, mess, hostel fees)
- Reports & dashboards (data accuracy, export)
- Form validation, cross-browser & responsive behaviour

### Out of Scope
- Load / performance / stress testing
- Penetration / security testing (handled separately)
- Third-party payment gateway internals (validated at integration level only)

## 3. Test Approach

| Phase | Activity |
|-------|----------|
| **Smoke** | Verify critical paths are up after each deployment |
| **Functional** | Execute module-wise test cases (positive, negative, boundary) |
| **Regression** | Re-run impacted suites after fixes / new builds |
| **Cross-browser** | Chrome, Firefox, Edge + mobile viewports |
| **UAT** | Acceptance scenarios with institute staff, assist sign-off |

## 4. Entry & Exit Criteria

**Entry:** Build deployed to test environment · test data ready · requirements available.
**Exit:** All planned test cases executed · no open Critical/High defects · UAT signed off.

## 5. Test Environment

- **Browsers:** Chrome (latest), Firefox (latest), Edge (latest)
- **Devices:** Desktop (1920×1080, 1366×768), Tablet, Mobile (viewport)
- **Roles:** Dedicated test accounts per role (Admin / Staff / Warden / Student)

## 6. Severity & Priority

| Severity | Meaning |
|----------|---------|
| Critical | App crash / data loss / module unusable / payment failure |
| High | Major feature broken, no workaround |
| Medium | Feature works with a workaround |
| Low | Cosmetic / minor UI issue |

| Priority | Meaning |
|----------|---------|
| P1 | Fix immediately (blocks release) |
| P2 | Fix before release |
| P3 | Fix if time permits / next release |

## 7. Deliverables

- Test plan (this document)
- Test cases per module
- Defect / bug reports
- Test execution summary & UAT sign-off

## 8. Risks

- Test data dependency across modules (admission → fees → hostel)
- Environment downtime during shared release cycles
- Last-minute requirement changes impacting regression scope
