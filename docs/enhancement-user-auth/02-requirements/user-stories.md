# User Stories: User Authentication & Personal Todo Lists

**Project**: Django Todo App Enhancement  
**Document Version**: 1.0  
**Date**: November 29, 2025
**Author**: Nanmi Zimik

---

## 1. Introduction

This document contains all user stories for the User Authentication & Personal Todo Lists enhancement. Each story follows the standard format: "As a [user type], I want to [goal], so that [benefit]."

Stories are organized by epic and include:
- Story ID
- Priority (Must Have, Should Have, Could Have)
- Story Points (Fibonacci: 1, 2, 3, 5, 8, 13)
- Acceptance Criteria
- Dependencies

---

## 2. Epic 1: User Authentication

### US-001: Create New Account

**Priority**: Must Have  
**Story Points**: 5  
**Sprint**: Sprint 1

**User Story**:  
As a **new user**  
I want to **create an account with username, email, and password**  
So that **I can have my own private todo list**

**Acceptance Criteria**:
- [ ] Registration form is accessible from homepage
- [ ] Form has fields for username, email, password, and confirm password
- [ ] Username must be unique (show error if taken)
- [ ] Email must be valid format and unique (show error if taken)
- [ ] Password must be at least 8 characters with at least one number
- [ ] Password and confirm password must match
- [ ] Clear, specific error messages shown for validation failures
- [ ] Account is created in database upon successful submission
- [ ] Password is encrypted before storing (never plain text)
- [ ] User is automatically logged in after successful registration
- [ ] User is redirected to empty todo list after registration
- [ ] Registration completes in under 2 minutes

**Dependencies**: None

**Related Requirements**: FR-1

**Testing Notes**:
- Test with various invalid inputs (short passwords, invalid emails, etc.)
- Verify password encryption in database
- Test duplicate username/email scenarios

---

### US-002: Login to My Account

**Priority**: Must Have  
**Story Points**: 3  
**Sprint**: Sprint 1

**User Story**:  
As a **registered user**  
I want to **log in with my credentials**  
So that **I can access my personal todo list**

**Acceptance Criteria**:
- [ ] Login form is accessible from homepage
- [ ] Form accepts either username or email as identifier
- [ ] Form has password field with masked input
- [ ] Correct credentials grant access to personal todo list
- [ ] Incorrect credentials show generic error message (e.g., "Invalid credentials")
- [ ] Error message doesn't reveal if username/email exists (security)
- [ ] "Remember Me" checkbox option is available
- [ ] Remember Me keeps user logged in across sessions
- [ ] User is redirected to their todo list after successful login
- [ ] Login completes within 2 seconds
- [ ] Failed login attempts are logged for security
- [ ] Rate limiting prevents brute force (max 5 attempts per 5 minutes)

**Dependencies**: US-001

**Related Requirements**: FR-2

**Testing Notes**:
- Test with valid and invalid credentials
- Verify rate limiting functionality
- Test "Remember Me" persistence

---

### US-003: Logout of My Account

**Priority**: Must Have  
**Story Points**: 2  
**Sprint**: Sprint 1

**User Story**:  
As a **logged-in user**  
I want to **log out of my account**  
So that **I can secure my data when finished**

**Acceptance Criteria**:
- [ ] Logout button/link is visible on all authenticated pages
- [ ] Clicking logout terminates session immediately
- [ ] All session cookies are cleared
- [ ] User is redirected to login page after logout
- [ ] Attempting to access authenticated pages after logout redirects to login
- [ ] Browser back button doesn't expose previous session data
- [ ] Confirmation message shows "Successfully logged out"
- [ ] Logout completes within 1 second

**Dependencies**: US-002

**Related Requirements**: FR-3

**Testing Notes**:
- Verify complete session termination
- Test back button security
- Verify cookie clearance

---

### US-004: Reset Forgotten Password

**Priority**: Must Have  
**Story Points**: 5  
**Sprint**: Sprint 1

**User Story**:  
As a **user who forgot my password**  
I want to **reset my password via email**  
So that **I can regain access to my account**

**Acceptance Criteria**:
- [ ] "Forgot Password" link is visible on login page
- [ ] Link leads to password reset request page
- [ ] User enters their email address
- [ ] System sends password reset email with secure link
- [ ] Reset link is unique and time-limited (expires in 1 hour)
- [ ] Reset link leads to password change form
- [ ] User enters new password and confirmation
- [ ] New password must meet all password requirements
- [ ] Invalid or expired links show appropriate error message
- [ ] Password is successfully changed in database
- [ ] All other sessions are logged out after password change (security)
- [ ] Confirmation email is sent after successful password change
- [ ] Reset token can only be used once
- [ ] User can login with new password immediately

**Dependencies**: US-002

**Related Requirements**: FR-4

**Testing Notes**:
- Test token expiration (after 1 hour)
- Verify one-time use of reset tokens
- Test all sessions logout after change

---

## 3. Epic 2: Personal Todo Lists

### US-005: View Only My Todos

**Priority**: Must Have  
**Story Points**: 3  
**Sprint**: Sprint 2

**User Story**:  
As a **logged-in user**  
I want to **see only my todos (not other users' todos)**  
So that **my todo list is private and not cluttered with others' tasks**

**Acceptance Criteria**:
- [ ] After login, user sees only their own todos
- [ ] No other users' todos are visible or accessible
- [ ] Empty list shows friendly message: "No todos yet! Add your first task."
- [ ] Todo count shows correct number for current user
- [ ] Todos are ordered by creation date (newest first)
- [ ] Direct URL access to other users' todos returns error
- [ ] API requests filter by authenticated user ID
- [ ] Page loads within 2 seconds regardless of total todos in system
- [ ] Unauthenticated access redirects to login

**Dependencies**: US-002

**Related Requirements**: FR-5

**Testing Notes**:
- Create multiple users and verify data separation
- Test URL manipulation attempts
- Verify performance with large datasets

---

### US-006: Add Todo to My List

**Priority**: Must Have  
**Story Points**: 3  
**Sprint**: Sprint 2

**User Story**:  
As a **logged-in user**  
I want to **add a new todo to my list**  
So that **I can track tasks I need to complete**

**Acceptance Criteria**:
- [ ] Todo input form is prominently displayed on main page
- [ ] User can type todo text (up to 200 characters)
- [ ] Pressing Enter or clicking "Add" button creates the todo
- [ ] New todo appears immediately in user's list
- [ ] New todo is marked as "incomplete" by default
- [ ] Todo is automatically associated with logged-in user
- [ ] Empty todos cannot be submitted (validation)
- [ ] Todo text over 200 characters is truncated or rejected
- [ ] Input field clears after successful addition
- [ ] Success feedback is provided (visual or message)
- [ ] Character counter shows remaining characters (optional)

**Dependencies**: US-005

**Related Requirements**: FR-6

**Testing Notes**:
- Test empty submission (should fail)
- Test character limit enforcement
- Verify correct user association

---

### US-007: Mark My Todo as Complete

**Priority**: Must Have  
**Story Points**: 2  
**Sprint**: Sprint 2

**[TODO: TEAMMATE-1] - Complete this user story following the format above**

**User Story**:  
As a **logged-in user**  
I want to **mark my todos as complete or incomplete**  
So that **I can track my progress**

**Acceptance Criteria** (add at least 8-10 criteria):
- [ ] Each todo has a checkbox or toggle for completion status
- [ ] Clicking checkbox marks todo as complete
- [ ] [ADD MORE CRITERIA]

**Dependencies**: US-006

**Related Requirements**: FR-7

---

### US-008: Edit My Todo Text

**Priority**: Should Have  
**Story Points**: 3  
**Sprint**: Sprint 2

**[TODO: TEAMMATE-1] - Complete this user story**

**User Story**:  
As a **logged-in user**  
I want to **edit the text of my existing todos**  
So that **I can correct mistakes or update task details**

**Acceptance Criteria** (add at least 8-10 criteria):
- [ ] Each todo has an "Edit" button or icon
- [ ] [ADD MORE CRITERIA]

**Dependencies**: US-006

**Related Requirements**: FR-7

---

### US-009: Delete My Todo

**Priority**: Must Have  
**Story Points**: 2  
**Sprint**: Sprint 2

**[TODO: TEAMMATE-1] - Complete this user story**

**User Story**:  
As a **logged-in user**  
I want to **delete todos I no longer need**  
So that **my list stays clean and relevant**

**Acceptance Criteria** (add at least 8-10 criteria):
- [ ] Each todo has a "Delete" button or icon
- [ ] [ADD MORE CRITERIA]

**Dependencies**: US-006

**Related Requirements**: FR-8

---

## 4. Epic 3: User Profile Management

### US-010: View My Profile

**Priority**: Should Have  
**Story Points**: 2  
**Sprint**: Sprint 3

**[TODO: TEAMMATE-1] - Complete this user story**

**User Story**:  
As a **logged-in user**  
I want to **view my profile information**  
So that **I can see my account details and statistics**

**Acceptance Criteria** (add at least 6-8 criteria):
- [ ] Profile link is accessible from navigation menu
- [ ] [ADD MORE CRITERIA]

**Dependencies**: US-002

**Related Requirements**: FR-9

---

### US-011: Change My Password

**Priority**: Should Have  
**Story Points**: 3  
**Sprint**: Sprint 3

**[TODO: TEAMMATE-1] - Complete this user story**

**User Story**:  
As a **logged-in user**  
I want to **change my password from my profile**  
So that **I can update my security credentials**

**Acceptance Criteria** (add at least 8-10 criteria):
- [ ] "Change Password" option is available in profile
- [ ] [ADD MORE CRITERIA]

**Dependencies**: US-010

**Related Requirements**: FR-10

---

### US-012: Update My Email

**Priority**: Could Have  
**Story Points**: 3  
**Sprint**: Sprint 3

**[TODO: TEAMMATE-1] - Complete this user story**

**User Story**:  
As a **logged-in user**  
I want to **update my email address**  
So that **I can keep my contact information current**

**Acceptance Criteria** (add at least 6-8 criteria):
- [ ] Email update option is available in profile
- [ ] [ADD MORE CRITERIA]

**Dependencies**: US-010

**Related Requirements**: FR-11

---

## 5. Story Points Summary

### By Epic

| Epic | Stories | Total Points |
|------|---------|--------------|
| Epic 1: Authentication | 4 stories | 15 points |
| Epic 2: Personal Todos | 5 stories | 13 points (estimated) |
| Epic 3: User Profile | 3 stories | 8 points (estimated) |
| **Total** | **12 stories** | **~36 points** |

### By Sprint

| Sprint | Stories | Total Points |
|--------|---------|--------------|
| Sprint 1 | US-001 to US-004 | 15 points |
| Sprint 2 | US-005 to US-009 | 13 points |
| Sprint 3 | US-010 to US-012 | 8 points |
| **Total** | **12 stories** | **~36 points** |

### By Priority

| Priority | Count | Points |
|----------|-------|--------|
| Must Have | 8 | 25 points |
| Should Have | 3 | 8 points |
| Could Have | 1 | 3 points |

---

## 6. Story Dependencies

```
US-001 (Register)
  └─> US-002 (Login)
        ├─> US-003 (Logout)
        ├─> US-004 (Password Reset)
        └─> US-005 (View My Todos)
              ├─> US-006 (Add Todo)
              │     ├─> US-007 (Mark Complete)
              │     ├─> US-008 (Edit Todo)
              │     └─> US-009 (Delete Todo)
              └─> US-010 (View Profile)
                    ├─> US-011 (Change Password)
                    └─> US-012 (Update Email)
```

---

## 7. Velocity Planning

Assuming team velocity of 12 story points per 2-week sprint:

- **Sprint 1** (15 points): Slightly over capacity, prioritize US-001, US-002 as critical
- **Sprint 2** (13 points): Good fit, focus on personal todo functionality
- **Sprint 3** (8 points): Under capacity, good buffer for polish and testing

---

## 8. Definition of Done

For a user story to be considered "Done":
- [ ] All acceptance criteria are met
- [ ] Code is reviewed and approved
- [ ] Unit tests written and passing
- [ ] Integration tests written and passing
- [ ] Manual UAT completed successfully
- [ ] Documentation updated
- [ ] No critical or high-priority bugs
- [ ] Code is merged to main branch

---

**Instructions for Teammate-1**:

Please complete user stories US-007 through US-012 by:
1. Writing the full user story in "As a... I want... So that..." format
2. Adding 6-10 detailed acceptance criteria for each story
3. Ensuring acceptance criteria are testable and specific
4. Following the format and level of detail in US-001 through US-006

**Commit these changes as**:
```bash
git commit -m "docs: Complete user stories US-007 to US-009 for todo management"
git commit -m "docs: Add user stories US-010 to US-012 for profile management"
```

---

**Document Control**

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | Nov 27, 2025 | Nanmi Zimik | Initial user stories US-001 to US-006 |
| 1.1 | Nov 28, 2025 | Sairaj Martha | Complete US-007 to US-012 |

---

**End of User Stories Document**