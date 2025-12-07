# Project Charter: User Authentication & Personal Todo Lists

**Project Name**: Django Todo App - User Authentication Enhancement  
**Project Lead**: Nanmi Zimik
**Team Members**: Sairaj Martha, Rehan Mohammad Abdul ,Hari Chandra Prasad Rayapati
**Start Date**: November 25, 2025  
**Target Completion**: January 24, 2026 (9 weeks)  
**Version**: 1.0  
**Date**: November 26, 2024

---

## 1. Executive Summary

This project will enhance the Django Todo App by adding user authentication and personal todo list functionality. Currently, the application uses a single shared todo list accessible to all users. This enhancement will transform it into a secure, multi-user system where each user has their own private todo list.

---

## 2. Project Vision

To transform the Django Todo App from a simple shared list into a secure, user-friendly application that enables individuals to manage their personal tasks privately while maintaining the application's simplicity and ease of use.

---

## 3. Project Objectives

1. **Primary Objective**: Implement secure user authentication system using Django's built-in authentication framework
2. **Secondary Objective**: Enable personal todo lists where each user can only view and manage their own tasks
3. **Tertiary Objective**: Provide user profile management including password reset and account management
4. **Quality Objective**: Maintain application simplicity while ensuring data security and privacy

---

## 4. Project Scope

### 4.1 In Scope

**User Authentication**
- User registration with email and password
- Secure login/logout functionality
- Session management
- Password encryption and security

**Personal Todo Lists**
- Database schema modification to link todos with users
- User-specific todo filtering
- Data isolation between users
- Migration of existing data structure

**User Profile Management**
- Basic user profile page
- Change password functionality
- Password reset via email
- Account deletion option

**Security & Privacy**
- Secure password storage (hashing)
- Protection against unauthorized access
- CSRF protection
- Session security

### 4.2 Out of Scope

The following features are explicitly NOT included in this enhancement:

- Social login (Google, Facebook, etc.)
- Two-factor authentication (2FA)
- Todo sharing between users
- Team/collaborative workspaces
- Mobile application development
- Advanced analytics or reporting
- Email notifications for tasks
- Third-party integrations (Slack, etc.)
- API for external applications
- Todo categories or tags (can be future enhancement)

---

## 5. Stakeholders

### 5.1 Primary Stakeholders

| Stakeholder | Role | Interest | Influence |
|-------------|------|----------|-----------|
| End Users | People who use todo app | Need private, secure task management | High |
| Project Team | Development team | Deliver quality enhancement | High |
| Original Author | Shrey Shah (shreys7) | Maintain open source project | Medium |
| Course Instructor | Academic evaluator | Assess PM skills demonstrated | High |

### 5.2 Secondary Stakeholders

- Open source community contributors
- Future developers who may extend the project
- System administrators who deploy the app

---

## 6. Success Criteria

The project will be considered successful when:

### 6.1 Functional Success Criteria

1. **User Registration**: New users can create accounts with email and password
2. **Authentication**: Users can login and logout successfully
3. **Data Separation**: Each user sees only their own todos (100% isolation)
4. **Password Management**: Users can reset forgotten passwords
5. **Profile Management**: Users can update their profile and change passwords

### 6.2 Technical Success Criteria

1. **Security**: All passwords are encrypted using industry-standard hashing
2. **Performance**: Login completes within 2 seconds
3. **Reliability**: Zero unauthorized access incidents
4. **Data Integrity**: No data loss during migration
5. **Code Quality**: All tests pass with >80% coverage

### 6.3 User Experience Success Criteria

1. **Usability**: New users can register and create their first todo within 2 minutes
2. **Simplicity**: UI remains clean and intuitive
3. **Accessibility**: Mobile-friendly responsive design maintained
4. **Error Handling**: Clear, helpful error messages for all scenarios

### 6.4 Project Success Criteria

1. **Timeline**: Completed within 8-week timeline
2. **Quality**: All acceptance criteria met
3. **Documentation**: Complete user and technical documentation
4. **Testing**: All test scenarios pass

---

## 7. High-Level Requirements

### 7.1 Functional Requirements (Summary)

- FR-1: System shall allow user registration
- FR-2: System shall authenticate users
- FR-3: System shall display only user-owned todos
- FR-4: System shall allow password reset
- FR-5: System shall provide user profile management

*(Detailed requirements in separate Requirements document)*

### 7.2 Non-Functional Requirements (Summary)

- NFR-1: Security - Password encryption, secure sessions
- NFR-2: Performance - Page load <2 seconds
- NFR-3: Usability - Intuitive interface, mobile-friendly
- NFR-4: Reliability - 99% uptime, zero data loss
- NFR-5: Maintainability - Clean code, well-documented

---

## 8. Constraints

### 8.1 Technical Constraints

- Must use Django framework (existing technology)
- Must maintain SQLite database (no migration to other DB)
- Must work with existing codebase structure
- Must use Django's built-in authentication (no custom auth)

### 8.2 Resource Constraints

- 4-person team
- 9-week timeline
- No budget for external services
- Development environment only (no production deployment)

### 8.3 Quality Constraints

- Must maintain code simplicity
- Must not break existing functionality
- Must pass all security audits
- Must have complete test coverage

---

## 9. Assumptions

1. **Technical Assumptions**
   - Django's authentication system is sufficient for requirements
   - SQLite can handle expected user load (<1000 users)
   - Current hosting environment supports user sessions

2. **User Assumptions**
   - Users have valid email addresses
   - Users understand basic web application concepts
   - Users want private todo lists (validated through research)

3. **Project Assumptions**
   - Team members available for full 8-week period
   - No major bugs in current codebase
   - Development environment access maintained

*(Detailed assumptions and validation in Assumptions document)*

---

## 10. Risks

### High-Priority Risks

| Risk | Impact | Probability | Mitigation |
|------|--------|-------------|------------|
| Security vulnerabilities in authentication | High | Medium | Use Django built-in auth, security audit |
| Data migration issues | High | Low | Test on copy of data, rollback plan |
| Performance degradation | Medium | Medium | Performance testing, optimization |

*(Complete risk register in Risk Management document)*

---

## 11. Project Timeline

### High-Level Milestones

| Milestone | Target Date | Deliverables |
|-----------|-------------|--------------|
| Requirements Complete | Week 2 | All requirements documented and approved |
| Architecture Complete | Week 3 | Design documents, DB schema finalized |
| Sprint 1 Complete | Week 4 | User registration and login working |
| Sprint 2 Complete | Week 6 | Personal todo lists implemented |
| Sprint 3 Complete | Week 8 | User profile features complete |
| Testing Complete | Week 9 | All tests pass, documentation complete |


---

## 12. Budget & Resources

### 12.1 Human Resources

- Project Lead: 10 hours/week
- Backend Developer: 10 hours/week
- Frontend Developer: 10 hours/week
- QA/Testing: 8 hours/week

**Total Effort**: ~300 person-hours over 9 weeks

### 12.2 Technical Resources

- Development environments (free)
- GitHub repository (free)
- Testing tools (free/open source)
- Documentation tools (free)

**Total Budget**: $0 (all free/open source tools)

---

## 13. Communication Plan

### 13.1 Team Meetings

- **Daily Standup**: 15 minutes, discuss progress/blockers
- **Sprint Planning**: 2 hours at sprint start
- **Sprint Review**: 1 hour at sprint end
- **Sprint Retrospective**: 1 hour at sprint end

### 13.2 Status Reporting

- Weekly status report to instructor/stakeholders
- GitHub issues updated daily
- Documentation updated continuously

*(Detailed communication plan in Communication document)*

---

## 14. Quality Assurance

### 14.1 Development Standards

- Code reviews required for all changes
- Unit tests required for all new code
- Documentation updated with all changes
- Security review for authentication code

### 14.2 Testing Approach

- Unit testing (80% coverage minimum)
- Integration testing for user flows
- User acceptance testing with real users
- Security testing for vulnerabilities

*(Detailed testing strategy in Testing document)*

---

## 15. Approval

### 15.1 Project Charter Approval

This project charter has been reviewed and approved by:

| Name | Role | Signature | Date |
|------|------|-----------|------|
| Nanmi Zimik | Project Lead | _________ | Nov 26, 2025 |
| Sairaj Martha | Developer | _________ | Nov 26, 2025 |
| Rehan Mohammad Abdul | Developer | _________ | Nov 26, 2025 |
| Hari Chandra Prasad Rayapati | QA/Testing | _________ | Nov 26, 2025 |

### 15.2 Change Control

Any changes to this charter must be:
1. Documented in writing
2. Reviewed by project team
3. Approved by project lead
4. Updated in version control

---

## 16. References

- Original Django Todo App: https://github.com/shreys7/django-todo
- Django Authentication Documentation: https://docs.djangoproject.com/en/stable/topics/auth/
- Project Management Course Materials
- Open Source Best Practices Guide

---

**Document Control**

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | Nov 26, 2025 | Nanmi Zimik | Initial charter creation |

---

**End of Project Charter**