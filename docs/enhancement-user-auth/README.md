# User Authentication & Personal Todo Lists Enhancement
 
## Project Information
- **Original Project**: Django Todo App by shreys7
- **Repository**: https://github.com/shreys7/django-todo
- **License**: Apache-2.0
- **Course**: SENG8091 - Software Engineering Principles
 
## Team
| Member | Role |
|--------|------|
| Nanmi Zimik | Project Lead |
| Sairaj Martha | Requirements Specialist |
| Rehan Mohammad Abdul | Architecture Specialist |
| Hari Chandra Prasad Rayapati | Testing Specialist |
 
## Enhancement Overview
This project adds user authentication and personal todo list functionality to the Django Todo App, transforming it from a shared todo list into a secure, multi-user application.
 
## Current State vs Proposed Enhancement
 
| Current State | Proposed Enhancement |
|---------------|---------------------|
| Single shared todo list | Personal todo lists per user |
| No user accounts | User registration and login |
| Anyone can edit any task | Users manage only their own tasks |
| No privacy | Complete data isolation |
| No security | Secure authentication with password hashing |
 
## Project Objectives
1. Implement secure user authentication using Django's built-in auth system
2. Modify database schema to associate todos with users
3. Ensure complete data isolation between users
4. Maintain simple, intuitive user experience
5. Follow security best practices
 
## Success Criteria
- [x] Users can register new accounts with validation
- [x] Users can login/logout securely with session management
- [x] Each user sees only their own todos
- [x] Password reset via email works
- [x] No unauthorized access to other users' data
 
## Documentation Index
 
| Section | Documents |
|---------|-----------|
| **01-Project Charter** | [charter.md](01-project-charter/charter.md) |
| **02-Requirements** | [functional-requirements.md](02-requirements/functional-requirements.md), [non-functional-requirements.md](02-requirements/non-functional-requirements.md), [user-stories.md](02-requirements/user-stories.md), [assumptions.md](02-requirements/assumptions.md), [traceability-matrix.md](02-requirements/traceability-matrix.md) |
| **03-Diagrams** | [ERD](03-diagrams/django-erd.jpg), [Use Case Diagram](03-diagrams/use-case.md), [User Flows](03-diagrams/user-flows.md) |
| **04-Architecture** | [system-architecture.md](04-architecture/system-architecture.md), [database-design.md](04-architecture/database-design.md) |

 
## Sprint Timeline
 
| Sprint | Focus | Duration | Due Date |
|--------|-------|----------|----------|
| Sprint 0 | Setup & Design | Week 1 | Dec 6, 2024 |
| Sprint 1 | User Authentication Core | Week 2 | Dec 13, 2024 |
| Sprint 2 | Personal Todo Lists | Week 3 | Dec 20, 2024 |
| Sprint 3 | User Profile & Polish | Week 4 | Dec 27, 2024 |
 
## GitHub Project Structure
 
| Type | Count | Description |
|------|-------|-------------|
| Epics | 4 | High-level feature groupings |
| User Stories | 13 | US-000 to US-012 |
| Tasks | 19 | Implementation work items |
 
## Technology Stack
- **Backend**: Django 4.x, Python 3.10+
- **Database**: SQLite (dev) / PostgreSQL (prod)
- **Authentication**: Django Built-in Auth
- **Frontend**: HTML5, CSS3, Django Templates
 
## Acknowledgments
This enhancement plan is based on the Django Todo App by Shrey Shah (shreys7) and is being developed as part of SENG8091 - Software Engineering Principles course. We acknowledge and respect the original author's work and contributions to the open-source community.