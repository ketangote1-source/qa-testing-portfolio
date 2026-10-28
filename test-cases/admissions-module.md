# Test Cases — Admissions Module

**Module:** Admissions (Enquiry → Application → Admission)
**Application:** InstituteSync College ERP
**Author:** Ketan Gote

| ID | Title | Steps | Test Data | Expected Result | Type |
|----|-------|-------|-----------|-----------------|------|
| TC_ADM_01 | Create new admission enquiry | Fill enquiry form with valid data → Submit | Valid student details | Enquiry saved; unique enquiry ID generated; confirmation shown | Positive |
| TC_ADM_02 | Mandatory field validation | Submit form with required fields empty | Blank name/mobile | Inline errors; submission blocked | Negative |
| TC_ADM_03 | Mobile number validation | Enter 9-digit / 11-digit / alphabetic number | `98765`, `abcdefghij` | Rejected with "enter a valid 10-digit mobile" | Boundary/Negative |
| TC_ADM_04 | Email format validation | Enter `ketan@`, `ketan.com` | invalid emails | Rejected with format error | Negative |
| TC_ADM_05 | Duplicate application check | Submit same student (same mobile/email) twice | Duplicate data | System flags/prevents duplicate OR warns | Functional |
| TC_ADM_06 | Convert enquiry → application | Open enquiry → "Convert to Application" | existing enquiry | Application created, status updated, data carried over | Positive |
| TC_ADM_07 | Document upload | Upload photo & certificates | JPG/PDF within size limit | Files upload & attach to record | Functional |
| TC_ADM_08 | Invalid file type/size | Upload `.exe` / oversized file | invalid file | Rejected with clear error | Negative |
| TC_ADM_09 | Course/branch selection | Select course then branch | valid course | Branch list updates based on selected course (dependent dropdown) | Functional |
| TC_ADM_10 | Date of birth validation | Enter future DOB | future date | Rejected / warned | Negative |
| TC_ADM_11 | Confirm admission | Approve application → allot admission no./roll no. | approved app | Student record created; roll/admission number assigned | Positive |
| TC_ADM_12 | Admission reflects in other modules | After admission, check Fees & Attendance | admitted student | Student appears in Fees (dues generated) & Attendance roster | Integration |
| TC_ADM_13 | Search & filter applicants | Filter by course/status/date | mixed data | Correct filtered results returned | Functional |
| TC_ADM_14 | Edit applicant details | Edit a saved application → Save | updated data | Changes persist & audit reflects update | Functional |
| TC_ADM_15 | Cancel/reject application | Reject with reason | pending app | Status = Rejected; reason stored; not counted as admitted | Functional |
