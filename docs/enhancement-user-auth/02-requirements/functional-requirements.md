# Functional Requirements: User Authentication & Personal Todo Lists

**Project**: Django Todo App Enhancement  
**Document Version**: 1.0  
**Date**: November 27, 2025 
**Author**: Nanmi Zimik

---

## 1. Introduction

This document defines the functional requirements for adding user authentication and personal todo list functionality to the Django Todo App. Each requirement is assigned a unique identifier for traceability.

---

## 2. User Management Requirements

### FR-1: User Registration

**Priority**: Must Have  
**Description**: The system shall allow new users to create an account.

**Requirements**:
- FR-1.1: System shall provide a registration form with fields: username, email, password, confirm password
- FR-1.2: System shall validate that username is unique
- FR-1.3: System shall validate that email is unique and in valid email format
- FR-1.4: System shall validate that password meets minimum requirements (8+ characters, at least one number)
- FR-1.5: System shall validate that password and confirm password match
- FR-1.6: System shall display clear error messages for validation failures
- FR-1.7: System shall encrypt password before storing in database
- FR-1.8: System shall create user account upon successful validation
- FR-1.9: System shall automatically log in user after successful registration
- FR-1.10: System shall send welcome email to new user (optional)

**Acceptance Criteria**:
- New user can complete registration in under 2 minutes
- All validation rules are enforced
- Passwords are never stored in plain text
- User is redirected to their personal todo list after registration

---

### FR-2: User Authentication (Login)

**Priority**: Must Have  
**Description**: The system shall allow registered users to authenticate and access their account.

**Requirements**:
- FR-2.1: System shall provide a login form with fields: username/email, password
- FR-2.2: System shall accept either username or email for login
- FR-2.3: System shall verify credentials against encrypted database values
- FR-2.4: System shall create a secure session upon successful authentication
- FR-2.5: System shall display error message for invalid credentials (generic message for security)
- FR-2.6: System shall redirect authenticated user to their todo list
- FR-2.7: System shall implement rate limiting to prevent brute force attacks (max 5 attempts per 5 minutes)
- FR-2.8: System shall provide "Remember Me" option for persistent sessions
- FR-2.9: System shall lock account after 10 failed login attempts
- FR-2.10: System shall log all authentication attempts for security audit

**Acceptance Criteria**:
- Users can login with username or email
- Invalid credentials show generic error (don't reveal if username exists)
- Session persists across browser tabs
- Rate limiting prevents brute force attacks

---

### FR-3: User Logout

**Priority**: Must Have  
**Description**: The system shall allow authenticated users to log out and end their session.

**Requirements**:
- FR-3.1: System shall provide logout button/link visible on all authenticated pages
- FR-3.2: System shall terminate user session upon logout
- FR-3.3: System shall clear all session cookies
- FR-3.4: System shall redirect user to login page after logout
- FR-3.5: System shall prevent access to authenticated pages after logout
- FR-3.6: System shall display confirmation message after successful logout

**Acceptance Criteria**:
- Logout button is easily accessible from any page
- Session is completely terminated
- User cannot access protected pages after logout
- Back button doesn't expose previous session data

---

### FR-4: Password Reset

**Priority**: Must Have  
**Description**: The system shall allow users to reset their password if forgotten.

**Requirements**:
- FR-4.1: System shall provide "Forgot Password" link on login page
- FR-4.2: System shall prompt user for their email address
- FR-4.3: System shall generate unique, time-limited password reset token (valid for 1 hour)
- FR-4.4: System shall send password reset email with secure link
- FR-4.5: System shall validate reset token before allowing password change
- FR-4.6: System shall reject expired or invalid tokens
- FR-4.7: System shall allow user to enter new password (with confirmation)
- FR-4.8: System shall enforce password requirements on new password
- FR-4.9: System shall invalidate reset token after successful password change
- FR-4.10: System shall send confirmation email after password change
- FR-4.11: System shall automatically log out all other sessions after password change

**Acceptance Criteria**:
- Users can reset password without contacting admin
- Reset link expires after 1 hour
- One reset token can only be used once
- All sessions are terminated after password change for security

---

## 3. Personal Todo List Requirements

### FR-5: User-Specific Todo Display

**Priority**: Must Have  
**Description**: The system shall display only todos belonging to the authenticated user.

**Requirements**:
- FR-5.1: System shall filter todos by authenticated user's ID
- FR-5.2: System shall display message "No todos yet" if user has no todos
- FR-5.3: System shall order todos by creation date (newest first) by default
- FR-5.4: System shall display todo count for current user
- FR-5.5: System shall hide other users' todos completely (no visibility)
- FR-5.6: System shall prevent URL manipulation to access other users' todos
- FR-5.7: System shall redirect unauthenticated users to login page

**Acceptance Criteria**:
- Each user sees only their own todos
- No way to view or access other users' data
- Clean, intuitive interface showing personal todos
- Performance is not degraded with user filtering

---

### FR-6: Create Personal Todo

**Priority**: Must Have  
**Description**: The system shall allow authenticated users to create todos in their personal list.

**Requirements**:
- FR-6.1: System shall provide todo creation form on main page
- FR-6.2: System shall automatically associate new todo with authenticated user
- FR-6.3: System shall validate that todo text is not empty
- FR-6.4: System shall limit todo text to 200 characters
- FR-6.5: System shall save todo with current timestamp
- FR-6.6: System shall display newly created todo immediately
- FR-6.7: System shall mark new todos as "incomplete" by default
- FR-6.8: System shall clear input form after successful creation

**Acceptance Criteria**:
- Authenticated users can add todos easily
- Todos are immediately visible in user's list
- Todo is linked to correct user ID
- Validation prevents empty or overly long todos

---

### FR-7: Update Personal Todo

**Priority**: Must Have  
**Description**: The system shall allow users to update their own todos only.

**Requirements**:
- FR-7.1: System shall allow users to mark todos as complete/incomplete
- FR-7.2: System shall allow users to edit todo text
- FR-7.3: System shall verify todo ownership before allowing updates
- FR-7.4: System shall display error if user attempts to update another user's todo
- FR-7.5: System shall update timestamp when todo is modified
- FR-7.6: System shall maintain complete/incomplete status separately
- FR-7.7: System shall provide clear UI indication of complete vs incomplete todos

**Acceptance Criteria**:
- Users can only modify their own todos
- Changes are reflected immediately
- Ownership verification prevents unauthorized updates
- UI clearly shows todo status

---

### FR-8: Delete Personal Todo

**Priority**: Must Have  
**Description**: The system shall allow users to delete their own todos only.

**Requirements**:
- FR-8.1: System shall provide delete button/option for each todo
- FR-8.2: System shall verify todo ownership before deletion
- FR-8.3: System shall display error if user attempts to delete another user's todo
- FR-8.4: System shall ask for confirmation before deletion
- FR-8.5: System shall permanently remove todo from database upon confirmation
- FR-8.6: System shall update display immediately after deletion
- FR-8.7: System shall display success message after deletion

**Acceptance Criteria**:
- Users can only delete their own todos
- Confirmation prevents accidental deletion
- Ownership verification prevents unauthorized deletion
- Todo is completely removed from database

---

## 4. User Profile Requirements

### FR-9: View User Profile

**Priority**: Should Have  
**Description**: The system shall allow users to view their profile information.

**Requirements**:
- FR-9.1: System shall provide link to user profile from main navigation
- FR-9.2: System shall display user's username, email, and join date
- FR-9.3: System shall display todo statistics (total, completed, incomplete)
- FR-9.4: System shall display account creation date
- FR-9.5: System shall display last login date/time

**Acceptance Criteria**:
- Profile page is easily accessible
- All user information is displayed correctly
- Statistics are accurate and up-to-date

---

### FR-10: Change Password

**Priority**: Should Have  
**Description**: The system shall allow users to change their password while logged in.

**Requirements**:
- FR-10.1: System shall provide "Change Password" option in profile
- FR-10.2: System shall require current password verification
- FR-10.3: System shall prompt for new password and confirmation
- FR-10.4: System shall enforce password requirements on new password
- FR-10.5: System shall validate that new password is different from current
- FR-10.6: System shall update password in database upon successful validation
- FR-10.7: System shall display success message after password change
- FR-10.8: System shall send confirmation email to user
- FR-10.9: System shall maintain current session (don't log user out)

**Acceptance Criteria**:
- Users can change password without logging out
- Current password verification prevents unauthorized changes
- Password requirements are enforced
- User receives confirmation

---

### FR-11: Update Profile Information

**Priority**: Could Have  
**Description**: The system shall allow users to update their profile information.

**Requirements**:
- FR-11.1: System shall allow users to change their email address
- FR-11.2: System shall validate new email format and uniqueness
- FR-11.3: System shall send verification email to new address
- FR-11.4: System shall require email verification before changing primary email
- FR-11.5: System shall allow users to update display name (if added)
- FR-11.6: System shall display success message after profile update

**Acceptance Criteria**:
- Users can update email with proper verification
- Email uniqueness is enforced
- Changes require verification for security

---

### FR-12: Delete Account

**Priority**: Could Have  
**Description**: The system shall allow users to permanently delete their account.

**Requirements**:
- FR-12.1: System shall provide "Delete Account" option in profile settings
- FR-12.2: System shall display clear warning about permanent deletion
- FR-12.3: System shall require password confirmation for deletion
- FR-12.4: System shall require user to type "DELETE" to confirm
- FR-12.5: System shall delete all user todos upon account deletion
- FR-12.6: System shall delete user profile information
- FR-12.7: System shall log user out after successful deletion
- FR-12.8: System shall send confirmation email to deleted account email
- FR-12.9: System shall prevent account recovery after deletion

**Acceptance Criteria**:
- Account deletion requires multiple confirmations
- All user data is permanently removed
- No recovery option after deletion
- Process is irreversible

---

## 5. Security Requirements

### FR-13: Access Control

**Priority**: Must Have  
**Description**: The system shall enforce proper access control for all operations.

**Requirements**:
- FR-13.1: System shall require authentication for all todo operations
- FR-13.2: System shall verify user ownership before any data modification
- FR-13.3: System shall prevent unauthorized access via direct URLs
- FR-13.4: System shall prevent unauthorized access via API calls
- FR-13.5: System shall implement CSRF protection on all forms
- FR-13.6: System shall sanitize all user inputs to prevent XSS attacks
- FR-13.7: System shall use parameterized queries to prevent SQL injection
- FR-13.8: System shall enforce HTTPS for all authenticated pages (production)

**Acceptance Criteria**:
- No unauthorized access to any user data
- All forms are CSRF protected
- No XSS or SQL injection vulnerabilities
- Security best practices are followed

---

## 6. Data Migration Requirements

### FR-14: Existing Data Handling

**Priority**: Must Have  
**Description**: The system shall handle existing todos during migration to multi-user system.

**Requirements**:
- FR-14.1: System shall create a default "admin" or "system" user
- FR-14.2: System shall assign all existing todos to default user
- FR-14.3: System shall preserve all existing todo data (text, status, dates)
- FR-14.4: System shall backup existing data before migration
- FR-14.5: System shall verify data integrity after migration
- FR-14.6: System shall provide rollback option if migration fails
- FR-14.7: System shall log all migration activities

**Acceptance Criteria**:
- No data loss during migration
- All existing todos remain accessible
- Migration can be rolled back if needed
- Clear migration log for verification

---

## 7. Requirements Summary

### Must Have Requirements (13)
FR-1 through FR-8, FR-13, FR-14

### Should Have Requirements (2)
FR-9, FR-10

### Could Have Requirements (2)
FR-11, FR-12

---

## 8. Traceability Matrix

*(See separate Traceability Matrix document for mapping requirements to user stories and tasks)*

---

## 9. Requirements Validation

Each requirement will be validated through:
- **Code Review**: All code implements requirements correctly
- **Unit Tests**: Automated tests verify requirement behavior
- **Integration Tests**: End-to-end tests validate requirement workflows
- **UAT**: Real users confirm requirements meet their needs

---

**Document Control**

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | November 27, 2025 | Nanmi Zimik | Initial functional requirements |

---

**End of Functional Requirements Document**