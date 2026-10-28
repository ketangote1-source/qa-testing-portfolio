# Test Cases — Hostel Room Allocation & Management

**Module:** Hostel (Rooms → Allocation → Residents → Mess → Hostel Fees)
**Application:** InstituteSync Hostel Portal
**Author:** Ketan Gote

| ID | Title | Steps | Test Data | Expected Result | Type |
|----|-------|-------|-----------|-----------------|------|
| TC_HST_01 | Add hostel & rooms | Create hostel → add rooms with capacity | capacity = 3 | Hostel & rooms saved with correct capacity | Positive |
| TC_HST_02 | Allocate room to student | Select student → allocate available room/bed | eligible student | Student allocated; bed count decreases by 1 | Positive |
| TC_HST_03 | Capacity enforcement | Allocate more students than room capacity | 4th into cap-3 room | Allocation blocked — "room full" | Boundary/Negative |
| TC_HST_04 | Duplicate allocation | Allocate same student to a second room | already-allocated student | Blocked / warned — one active allocation only | Negative |
| TC_HST_05 | Gender/wing rules | Allocate student to wrong-gender hostel | mismatched student | Blocked per allocation rules | Functional |
| TC_HST_06 | De-allocate / vacate room | Vacate a resident | allocated student | Bed freed; count increases; history retained | Positive |
| TC_HST_07 | Room transfer | Move resident to another room | valid target room | Old bed freed, new bed occupied; counts correct both sides | Functional |
| TC_HST_08 | Occupancy report accuracy | Open occupancy dashboard | mixed data | Occupied vs vacant counts match actual allocations | Report |
| TC_HST_09 | Hostel fee generation | Allocate student → check hostel fees | allocated student | Hostel fee due generated automatically | Integration |
| TC_HST_10 | Mess registration | Register resident for mess plan | valid plan | Mess membership recorded; mess fee applied | Functional |
| TC_HST_11 | Attendance / in-out register | Mark resident in/out | timestamps | Entries logged with correct timestamp & resident | Functional |
| TC_HST_12 | Warden role access | Login as Warden → manage own hostel | warden account | Warden manages allocated hostel only, not others | RBAC |
| TC_HST_13 | Search resident | Search by name/room/admission no. | mixed query | Correct resident record returned | Functional |
| TC_HST_14 | Vacated student re-allocation | Re-allocate a previously vacated student | returning student | New allocation succeeds; history preserved | Functional |
| TC_HST_15 | Concurrent allocation to last bed | Two wardens allocate last bed at once | last available bed | Only one succeeds; no over-allocation | Edge |
