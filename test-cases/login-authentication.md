# Test Cases — Login, Authentication & Role-Based Access

**Module:** Authentication & RBAC
**Application:** InstituteSync ERP / Hostel Portal
**Author:** Ketan Gote

| ID | Title | Pre-condition | Steps | Test Data | Expected Result | Type |
|----|-------|---------------|-------|-----------|-----------------|------|
| TC_AUTH_01 | Valid login | User has an active account | 1. Open login page 2. Enter valid username & password 3. Click Login | Valid credentials | User is logged in and redirected to the role-based dashboard | Positive |
| TC_AUTH_02 | Invalid password | Account exists | 1. Enter valid username 2. Enter wrong password 3. Click Login | Valid user / wrong pwd | Error message shown; user NOT logged in | Negative |
| TC_AUTH_03 | Non-existent user | — | 1. Enter unknown username & any password 2. Click Login | Unknown user | Generic "invalid credentials" error (no user-exists leak) | Negative |
| TC_AUTH_04 | Empty fields | — | 1. Leave username/password blank 2. Click Login | Blank | Inline validation: "required" messages; no submit | Negative |
| TC_AUTH_05 | Password masking | On login page | 1. Type password | any | Characters are masked by default | UI |
| TC_AUTH_06 | SQL injection attempt | — | 1. Enter `' OR '1'='1` in username 2. Submit | Malicious string | Login rejected; input sanitised; no DB error exposed | Negative/Security |
| TC_AUTH_07 | Case sensitivity of password | Account exists | 1. Enter correct username 2. Enter password in wrong case | Altered case | Login rejected | Negative |
| TC_AUTH_08 | Logout | User logged in | 1. Click Logout | — | Session ends; redirected to login; back button does not re-enter session | Positive |
| TC_AUTH_09 | Session timeout | User logged in & idle | 1. Stay idle past timeout 2. Perform action | — | User is logged out / asked to re-authenticate | Functional |
| TC_AUTH_10 | RBAC — Student access | Logged in as Student | 1. Try to open an Admin-only URL directly | Admin URL | Access denied / redirected; no admin data shown | Security/RBAC |
| TC_AUTH_11 | RBAC — Warden scope | Logged in as Warden | 1. Open hostel module 2. Attempt to open academic/exam module | — | Warden sees hostel features only; academic modules not accessible | RBAC |
| TC_AUTH_12 | Forgot password flow | Account exists | 1. Click Forgot Password 2. Enter registered email 3. Follow reset link 4. Set new password | Registered email | Reset link delivered; new password works; old one rejected | Positive |
| TC_AUTH_13 | Multiple failed attempts | Account exists | 1. Enter wrong password N times | wrong pwd ×N | Account lock / throttle / captcha as per policy | Security |
| TC_AUTH_14 | Remember me / direct URL after logout | Just logged out | 1. Paste a deep dashboard URL | — | Redirected to login (no cached private page) | Security |

**Legend:** Type = Positive / Negative / UI / Functional / Security / RBAC
