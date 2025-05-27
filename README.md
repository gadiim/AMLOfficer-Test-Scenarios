# AMLOfficer-Test-Scenarios

**Task:** Your task is to test the Business Account setup flow starting from the moment the user opens the "Add Business Account" pop-up in the web interface. Go through each step: accepting terms and conditions, entering a valid email, verifying it with the code, creating a password, entering company and owner names, and inviting team members. Verify that all validations work correctly (e.g. email format, code match, password strength, valid teammate emails). 

In your response, please include: 
1. Write test scenarios that cover both positive and negative cases based on the flow described above.
2. Identify and document 6-8 issues found during testing in the form of bug reports.
3. Prepare a short test summary describing the results of your testing.
4. Suggest any improvements related to usability or the user experience (optional but welcome).


[FLOW](https://drive.google.com/file/d/1rSLSdITvoYT0TzmVW4qn2rHftp9FprgM/view)


## Table of Contents
- [Test Scenarios](#test-scenarios)
- [Bug Reports](#bug-reports)
- [Test Summary](#test-summary)

## Test Scenarios
  - [Step 1: The user agrees to the terms](#step-1-the-user-agrees-to-the-terms)
  - [Step 2: The user enters e-mail](#step-2-the-user-enters-e-mail)
  - [Step 3: The user enters the code from the e-mail](#step-3-the-user-enters-the-code-from-the-e-mail)
  - [Step 4: The user enters the password](#step-4-the-user-enters-the-password)
  - [Step 5: The user enters the company name and own name](#step-5-the-user-enters-the-company-name-and-own-name)
  - [Step 6: The user invites someone to the team](#step-6-the-user-invites-someone-to-the-team)
  - [Step 7: The user sends invitations](#step-7-the-user-sends-invitations)

### Step 1: The user agrees to the terms
**Test Scenario**  
**Objective:** Ensure the user cannot proceed to the next step without accepting the terms of use.  
**Precondition:** The user is on Step 1.  
**Steps:**
1. Read the Terms and Conditions text.
2. Check the "I accept the terms" checkbox.
3. Click the "Continue Setup" button.
**Expected Result:** Proceeding to Step 2 is only possible after accepting the terms.

| Test Case ID | Type      | Preconditions                  | Steps                                                                 | Expected Result                                      | Actual Result               |
|--------------|-----------|--------------------------------|------------------------------------------------------------------------|-----------------------------------------------------|----------------------------|
| TC1-P1       | Positive  | User is on Step 1              | 1. User sees Terms and Conditions text                                 | Terms text is fully visible                         | ✅ As expected              |
| TC1-P2       | Positive  | User is on Step 1              | 1. User checks “I accept the terms” checkbox                          | “Continue Setup” button becomes enabled             | ✅ Button activates         |
| TC1-P3       | Positive  | Checkbox is checked            | 1. User clicks “Continue Setup”                                       | Proceeds to Step 2                                  | ✅ Navigates forward        |
| TC1-N1       | Negative  | User is on Step 1              | 1. User does not check checkbox                                       | “Continue Setup” button remains disabled            | ✅ Button disabled          |
| TC1-N2       | Negative  | User is on Step 1              | 1. Clicks “Continue Setup” without checking checkbox                  | Nothing happens; no feedback shown (potential bug)  | ❌ No error/feedback        |

### Step 2: The user enters e-mail
**Test Scenario**  
**Objective:** Verify email input validation and correct UI behavior.  
**Steps:**
1. Enter an email address.
2. Click the "Continue Setup" button.
**Expected Result:** Proceeding to the next step is only allowed with a valid email address.

| Test Case ID | Type      | Preconditions                                | Steps                                                                 | Expected Result                                     | Actual Result                  |
|--------------|-----------|----------------------------------------------|------------------------------------------------------------------------|----------------------------------------------|-------------------------------|
| TC2-P1       | Positive  | On Step 2                                    | 1. Enter valid email (test@example.com)                          | “Continue Setup” button becomes active             | ✅ As expected                 |
| TC2-N1       | Negative  | On Step 2                                    | 1. Leave input empty                                                   | Button stays disabled                        | ✅ As expected                 |
| TC2-N2       | Negative  | On Step 2                                    | 1. Enter invalid email (test@.com)                               | Error shown, button remains inactive               | ✅ Validation blocks progress |
| TC2-N3       | Negative  | On Step 2                                    | 1. Enter spaces or unsupported characters                              | Error message shown                          | ✅ As expected                 |

### Step 3: The user enters the code from the e-mail
**Test Scenario**  
**Objective:** Ensure the system correctly handles both valid and invalid verification codes.  
**Steps:**
1. Enter the code received via email.
2. Click the "Continue Setup" button.  
**Expected Result:** The user can proceed with a valid code; an error is shown for an invalid one.

| Test Case ID | Type      | Preconditions                                | Steps                                                 | Expected Result                        | Actual Result                  |
|--------------|-----------|----------------------------------------------|--------------------------------------------------------|-----------------------------------------|-------------------------------|
| TC3-P1       | Positive  | Code received in email                        | 1. Enter correct code                                  | Navigation to next step                 | ✅ Proceeds to Step 4         |
| TC3-N1       | Negative  | Code not entered                              | 1. Leave input empty                                   | Button disabled                         | ✅ As expected                 |
| TC3-N2       | Negative  | Incorrect code                                | 1. Enter wrong code                                    | Error message displayed                 | ✅ “Wrong code” error shown   |

### Step 4: The user enters the password
**Test Scenario**  
**Objective:** Confirm that the password meets security requirements.  
**Steps:**
1. Enter a password.
2. Observe the UI response.
**Expected Result:** Validation works correctly; weak passwords prevent further progress.

| Test Case ID | Type      | Preconditions                                | Steps                                                     | Expected Result                                  | Actual Result                 |
|--------------|-----------|----------------------------------------------|------------------------------------------------------------|---------------------------------------------------|------------------------------|
| TC4-P1       | Positive  | On Step 4                                     | 1. Enter strong password (Xyz@123456)                | “Continue Setup” button enabled                  | ✅ As expected                |
| TC4-N1       | Negative  | On Step 4                                     | 1. Enter weak password (12345)                       | Error or password strength warning                | ✅ Password warning shown     |
| TC4-N2       | Negative  | On Step 4                                     | 1. Leave input empty                                       | Button remains disabled                          | ✅ As expected                |

### Step 5: The user enters the company name and own name
**Test Scenario**  
**Objective:** Ensure both fields are mandatory for progress.  
**Steps:**
1. Enter the company name.
2. Enter the first and last name.
**Expected Result:** User can proceed only if all fields are filled in.

| Test Case ID | Type      | Preconditions                                | Steps                                                    | Expected Result                                    | Actual Result                 |
|--------------|-----------|----------------------------------------------|-----------------------------------------------------------|-----------------------------------------------------|------------------------------|
| TC5-P1       | Positive  | On Step 5                                     | 1. Enter company name <br> 2. Enter first & last name      | Fields accept input and allow progress              | ✅ As expected                |
| TC5-N1       | Negative  | On Step 5                                     | 1. Leave fields empty                                     | Error or button disabled                            | ✅ Blocked from proceeding   |

### Step 6: The user invites someone to the team
**Test Scenario**  
**Objective:** Verify the team member invitation functionality.  
**Steps:**
1. Enter a valid teammate email.
2. Select a role from the dropdown.
3. Click the "Add" button.
**Expected Result:** The teammate is added successfully only with a valid email and selected role.

| Test Case ID | Type      | Preconditions                                | Steps                                                                                     | Expected Result                                      | Actual Result                  |
|--------------|-----------|----------------------|--------------------------------------------------------------------------------------------|-------------------------------|------------------------|
| TC6-P1       | Positive  | On Step 6                                     | 1. Enter valid teammate email <br> 2. Select a role from dropdown <br> 3. Click “Add” | Teammate added to list                               | ✅ Added with role visible    |
| TC6-N1       | Negative  | On Step 6                                     | 1. Enter invalid email (john@.com) <br> 2. Click “Add”                     | Error shown or blocked                               | ✅ Email validation works     |
| TC6-N2       | Negative  | On Step 6                                     | 1. Select no role <br> 2. Click “Add”                                             | Prompt to select role                                | ❌ No role = silent failure   |

### Step 7: The user sends invitations
**Test Scenario**  
**Objective:** Ensure invitations can only be sent after adding at least one team member.  
**Steps:**
1. Click the "Send Invitations" button.
**Expected Result:** If no team members are added, an error message is displayed.

| Test Case ID | Type      | Preconditions                                | Steps                                         | Expected Result                                   | Actual Result                  |
|--------------|-----------|----------------------------------------------|------------------------------------------------|----------------------------------------------------|-------------------------------|
| TC7-P1       | Positive  | Teammate(s) added                             | 1. Click “Send Invitations”                   | Invitation sent, confirmation shown               | ✅ As expected                |
| TC7-N1       | Negative  | No teammate added                             | 1. Click “Send Invitations”                   | Error or warning to add at least one teammate     | ✅ Blocked from sending       |


## Bug Reports

No critical or blocking bugs detected during testing.

- **TC1-N2:** Clicking “Continue Setup” without checking the terms checkbox does not provide user feedback or error message. (Minor UX improvement recommended.)
- **TC6-N2:** When adding a team member without selecting a role, there is no prompt or error message. (UX improvement needed to avoid silent failure.)


## Test Summary

The overall business account setup flow works as expected, with all validation and UI controls functioning correctly.

**Recommendation:**  
Add the ability for users to navigate back to previous steps during the setup process. This will improve user experience by allowing corrections without restarting the entire process.

