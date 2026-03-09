# PRD 01: Core School Management System

## Introduction

The Core School Management module serves as the foundation of the School Management System (Sistem Manajemen Sekolah). This module establishes the fundamental data structures and management capabilities required for all other modules to function effectively. It handles the essential organizational data including school profile, academic periods, educational levels, student information, teacher/staff management, and class organization.

This module is critical as it provides the master data that will be referenced throughout the entire system, from academic operations to financial management and reporting.

## Goals

1. **Centralized Data Management**: Create a single source of truth for all core school data
2. **Data Integrity**: Ensure consistency and accuracy of master data across the system
3. **Flexibility**: Support multiple school types, grade levels, and organizational structures
4. **Ease of Administration**: Provide intuitive interfaces for school administrators to manage core data
5. **Auditability**: Track all changes to critical master data
6. **Multi-School Support**: Enable the system to potentially serve multiple schools under one organization

## User Stories

### Story 1: School Profile Management

**Description**: As a school administrator, I want to manage the school's profile information so that the system can display accurate school details across all modules and official documents.

**Acceptance Criteria**:
- Administrator can create and update school profile including:
  - School name (official and alternative names)
  - NPSN (National School Identification Number)
  - School address (street, district, city, province, postal code)
  - Contact information (phone, email, website)
  - School logo and official letterhead upload
  - School accreditation status and certificate
  - School type (SD, SMP, SMA, SMK, etc.)
  - Education level (basic, middle, high)
  - School status (public/private)
  - Principal/headmaster information
  - School establishment date
  - School vision and mission statements
  - School motto and values
- System validates required fields before saving
- School logo is automatically resized and optimized
- Profile history is maintained for audit purposes
- School information is displayed consistently across all documents and reports

### Story 2: Academic Year & Semester Management

**Description**: As a school administrator, I want to define and manage academic years and semesters so that all academic activities can be properly organized and scheduled within specific time periods.

**Acceptance Criteria**:
- Administrator can create academic years with:
  - Academic year name/format (e.g., "2024/2025", "2024-2025")
  - Start and end dates
  - Status (active, inactive, upcoming)
  - Number of semesters per academic year
- Administrator can create semesters within each academic year:
  - Semester name/number (Semester 1, Semester 2)
  - Start and end dates
  - Mid-semester break periods
  - Final examination periods
  - Status (active, inactive, upcoming)
- System prevents overlapping academic years or semesters
- System enforces chronological order of semesters within academic years
- Only one academic year/semester can be active at a time
- Administrator can view historical academic years for reference
- System automatically archives data from previous academic years
- Academic year can be marked as "current" for default selection in other modules

### Story 3: Grade Level (Tingkat) Management

**Description**: As a school administrator, I want to define and manage grade levels offered by the school so that students can be properly categorized and curricula can be appropriately structured.

**Acceptance Criteria**:
- Administrator can create grade levels with:
  - Level code (e.g., "KLS-7", "KLS-8", "KLS-X")
  - Level name (e.g., "Kelas 7", "Kelas 8", "Kelas X")
  - Level order/sequence (1, 2, 3, etc.)
  - Associated education stage (junior high, senior high, etc.)
  - Minimum and maximum age requirements
  - Promotion requirements from previous level
- Administrator can define level groups (e.g., "Junior High" contains levels 7, 8, 9)
- System maintains proper ordering of grade levels
- Grade levels cannot be deleted if they have enrolled students
- Administrator can activate/deactivate grade levels (instead of deletion)
- System displays grade levels in proper sequence across all modules
- Grade levels can be copied from previous academic year to new academic year

### Story 4: Student Data Management

**Description**: As a school administrator, I want to manage comprehensive student data so that accurate student records are maintained throughout their entire academic journey.

**Acceptance Criteria**:
- Administrator can register new students with:
  - Personal information:
    - Full name (as per official documents)
    - NISN (National Student Identification Number)
    - NIS (Local Student ID - auto-generated)
    - Date and place of birth
    - Gender
    - Religion
    - Blood type
    - Photo upload
  - Contact information:
    - Address (complete with postal code)
    - Phone numbers (student, parent/guardian)
    - Email address
  - Parent/guardian information:
    - Father's name, occupation, contact
    - Mother's name, occupation, contact
    - Guardian information (if applicable)
    - Emergency contact details
  - Academic information:
    - Previous school
    - Enrollment date
    - Current grade level and class
    - Academic year of enrollment
    - Student status (active, graduated, transferred, dropped out)
- Administrator can edit student information with change tracking
- System generates unique NIS automatically based on school's format
- System prevents duplicate NISN within the same school
- Student status can be updated with effective dates and reasons
- Administrator can view student's complete academic history
- System supports bulk student import from Excel/CSV files
- System validates imported data and reports errors
- Administrator can export student data to various formats
- System maintains student enrollment history across academic years
- Deceased students can be marked with date and cause (for record-keeping)

### Story 5: Teacher & Staff Management

**Description**: As a school administrator, I want to manage teacher and staff information so that the school can properly assign responsibilities, track employment, and manage human resources.

**Acceptance Criteria**:
- Administrator can register teachers with:
  - Personal information:
    - Full name (with title)
    - NIP (Employee Identification Number) if applicable
    - NUPTK (Teacher Unique Number)
    - Date and place of birth
    - Gender
    - Religion
    - Photo upload
  - Contact information:
    - Address
    - Phone numbers
    - Email address
  - Employment information:
    - Employment type (civil servant, contract, honorary)
    - Employment status (active, on leave, resigned, retired)
    - Hire date
    - Subject specializations (can teach multiple subjects)
    - Education qualification (degree, major, institution)
    - Certifications and licenses
    - Work experience history
- Administrator can register non-teaching staff with:
  - Similar personal and contact information
  - Staff role/position (administrator, librarian, security, etc.)
  - Department/division
  - Employment type and status
  - Employment history
- System generates unique employee ID automatically
- Administrator can assign roles and permissions to teachers/staff
- Administrator can view complete employment history
- System supports bulk import of teacher/staff data
- System tracks certification expiration dates
- Teacher profiles show subjects they are qualified to teach
- Administrator can manage staff leaves and absences
- System supports assigning homeroom teacher (wali kelas) responsibilities
- Staff can be marked as inactive instead of deleted (for record retention)

### Story 6: Class Management

**Description**: As a school administrator, I want to create and manage classes so that students can be properly grouped for academic activities and administrative purposes.

**Acceptance Criteria**:
- Administrator can create classes with:
  - Class name/code (e.g., "7A", "7-B", "X-IPA-1")
  - Academic year and semester
  - Grade level
  - Homeroom teacher assignment (wali kelas)
  - Maximum capacity (optional)
  - Room/location assignment (optional)
- Administrator can add students to classes:
  - Individual student assignment
  - Bulk assignment from list of unassigned students
  - Move students between classes within same grade level
  - Remove students from classes
- System prevents exceeding maximum capacity if set
- System tracks class membership changes over time
- Administrator can view class rosters with student details
- System displays class statistics (total students, male/female count)
- Classes can be cloned/copied to new academic year
- Homeroom teacher can be changed with effective date tracking
- System maintains class history (which students were in which class, when)
- Administrator can deactivate classes (instead of deleting)
- Class information is accessible to assigned teachers and homeroom teachers
- System supports creating temporary groups/subsets within classes

### Story 7: User Account Management for Students & Teachers

**Description**: As a school administrator, I want to create and manage user accounts for students, teachers, and staff so that they can access the system with appropriate permissions.

**Acceptance Criteria**:
- Administrator can create user accounts linked to student/teacher profiles:
  - Username (can be auto-generated based on NIS/NIP)
  - Email address or phone number for login
  - Temporary password (sent via email/SMS or printed)
  - Account status (active, suspended, inactive)
  - Role-based access (student, teacher, admin, etc.)
- System enforces password requirements:
  - Minimum length
  - Complexity requirements (optional)
  - Password expiration (optional)
- Administrator can reset user passwords
- Administrator can activate/suspend accounts
- System logs all login attempts and account activities
- Users can change their own passwords
- System supports password reset via email/phone verification
- Account can be locked after multiple failed login attempts (configurable)
- Administrator can view last login information
- Student accounts are linked to parent accounts for family access
- Teacher accounts can access assigned classes and subjects only
- System maintains audit log of account changes

## Functional Requirements

### 1. School Profile
- FR-CSM-001: Create, read, update, delete school profile information
- FR-CSM-002: Upload and manage school logo and official documents
- FR-CSM-003: Display school information consistently across all system modules
- FR-CSM-004: Support multiple schools under single system (multi-tenant)
- FR-CSM-005: Maintain school profile change history

### 2. Academic Management
- FR-CSM-006: Create, read, update academic year records
- FR-CSM-007: Create, read, update semester records linked to academic years
- FR-CSM-008: Define academic year/semester status (active, inactive, upcoming)
- FR-CSM-009: Set examination periods within semesters
- FR-CSM-010: Archive academic data for previous years
- FR-CSM-011: Validate date ranges and prevent overlaps

### 3. Grade Level Management
- FR-CSM-012: Create, read, update, deactivate grade levels
- FR-CSM-013: Define grade level sequences and groupings
- FR-CSM-014: Link grade levels to education stages
- FR-CSM-015: Copy grade level structure to new academic years
- FR-CSM-016: Prevent deletion of grade levels with enrolled students

### 4. Student Management
- FR-CSM-017: Create, read, update student records with comprehensive information
- FR-CSM-018: Auto-generate unique student IDs (NIS)
- FR-CSM-019: Validate NISN uniqueness
- FR-CSM-020: Track student status changes with dates and reasons
- FR-CSM-021: Maintain student academic history across years
- FR-CSM-022: Bulk import student data from external files
- FR-CSM-023: Export student data in multiple formats
- FR-CSM-024: Link students to parents/guardians
- FR-CSM-025: Track student enrollment history
- FR-CSM-026: Manage student photos and documents

### 5. Teacher & Staff Management
- FR-CSM-027: Create, read, update teacher records with qualification details
- FR-CSM-028: Create, read, update staff records with role information
- FR-CSM-029: Auto-generate unique employee IDs
- FR-CSM-030: Track teacher subject specializations
- FR-CSM-031: Manage employment status and history
- FR-CSM-032: Assign homeroom teacher responsibilities
- FR-CSM-033: Bulk import teacher/staff data
- FR-CSM-034: Track certification and qualification expiration
- FR-CSM-035: Manage staff leaves and absences
- FR-CSM-036: Assign roles and permissions

### 6. Class Management
- FR-CSM-037: Create, read, update, deactivate class records
- FR-CSM-038: Link classes to academic year, semester, and grade level
- FR-CSM-039: Assign homeroom teachers to classes
- FR-CSM-040: Add and remove students from classes
- FR-CSM-041: Track class membership changes over time
- FR-CSM-042: Maintain maximum class capacity limits
- FR-CSM-043: Clone class structure to new academic years
- FR-CSM-044: Display class rosters and statistics
- FR-CSM-045: Manage room/location assignments

### 7. User Account Management
- FR-CSM-046: Create user accounts linked to student/teacher profiles
- FR-CSM-047: Auto-generate usernames based on institutional ID
- FR-CSM-048: Manage password policies and resets
- FR-CSM-049: Control account status and access
- FR-CSM-050: Log authentication activities
- FR-CSM-051: Implement role-based access control
- FR-CSM-052: Link student accounts to parent accounts

### 8. Data Management
- FR-CSM-053: Maintain audit trails for all data changes
- FR-CSM-054: Implement data validation rules
- FR-CSM-055: Support data backup and restore
- FR-CSM-056: Implement soft delete for critical records
- FR-CSM-057: Provide search and filter capabilities across all data

## Non-Goals

The following features are explicitly **out of scope** for this module:

- **Academic Operations**: Scheduling, attendance, grading, and curriculum management are handled by the Academic & LMS module
- **Financial Management**: Fee structures, payments, and financial reporting are handled by the Finance module
- **Communication**: Announcements, notifications, and messaging are handled by the Communication module
- **Admissions**: New student registration and selection processes are handled by the PPDB module
- **Advanced HR Features**: Payroll, benefits, and performance management are not included
- **Transportation Management**: School bus routes and logistics are not included
- **Library Management**: Library catalog and circulation are not included
- **Inventory Management**: Physical asset tracking is not included

## Technical Considerations

### Database Design
- Use normalized database schema with proper referential integrity
- Implement soft delete pattern for auditability
- Use appropriate indexes for frequently queried fields
- Consider partitioning for large historical datasets
- Store documents and images in secure storage with CDN delivery

### Performance
- Implement caching for frequently accessed reference data
- Use database connection pooling
- Optimize queries for class rosters and student lists
- Consider read replicas for reporting queries
- Implement pagination for large data sets

### Security
- Implement role-based access control (RBAC)
- Encrypt sensitive data (PII) at rest
- Use secure password hashing (bcrypt/argon2)
- Implement audit logging for all data changes
- Validate and sanitize all user inputs
- Use HTTPS for all communications
- Implement rate limiting for API endpoints

### Scalability
- Design for multi-school deployment (multi-tenancy)
- Use horizontal scaling architecture
- Implement database sharding if needed for large deployments
- Design API to support mobile app integration
- Consider implementing microservices architecture

### Integration
- Provide RESTful APIs for all CRUD operations
- Support webhook notifications for data changes
- Implement data export/import in standard formats (CSV, Excel, JSON)
- Design for integration with government education systems (Dapodik)
- Support single sign-on (SSO) integration

### Data Quality
- Implement data validation at multiple layers
- Use database constraints for data integrity
- Provide data deduplication utilities
- Implement data quality reports
- Support data migration tools

## Success Metrics

### Adoption Metrics
- **Data Completeness**: 95% of students, teachers, and classes have complete profile information within 3 months of deployment
- **User Registration**: 100% of active students and teachers have system accounts within first semester
- **Data Accuracy**: Less than 2% data errors identified in quarterly audits

### Operational Metrics
- **System Availability**: 99.5% uptime during business hours
- **Response Time**: Page loads within 2 seconds for 95% of requests
- **Data Load Time**: Class roster loads within 3 seconds for classes up to 40 students
- **Import Success Rate**: 98% success rate for bulk data imports

### User Satisfaction
- **User Satisfaction Score**: 4.0+ out of 5.0 in semi-annual surveys
- **Support Tickets**: Less than 5 tickets per 100 users per month related to data management
- **Training Completion**: 90% of administrators complete training within first month

### Data Quality Metrics
- **Duplicate Records**: Less than 0.5% duplicate student/teacher records
- **Inactive Account Cleanup**: 100% of inactive accounts identified within 30 days
- **Data Currency**: 95% of student status updates processed within 2 business days

## Open Questions

1. **Multi-School Support**: Should the system support multiple independent schools with completely separate data, or schools under one organization with shared reference data?

2. **Historical Data Retention**: How many years of historical student and academic data should be retained by default? Should there be an archive policy?

3. **Government Integration**: What are the specific integration requirements with Dapodik (Indonesian Education Basic Data) system? Are there API specifications available?

4. **Bulk Import Format**: What should be the standard format for bulk imports? Should the system provide templates?

5. **Photo Storage**: What are the size limits and format requirements for student/teacher photos? Should they be stored locally or in cloud storage?

6. **Class Capacity Limits**: Should class capacity be enforced strictly or just used for guidance? What happens when capacity is exceeded?

7. **Student ID Format**: Should the NIS generation format be configurable per school, or should there be a standard format?

8. **Parent Account Linking**: How many parent/guardian accounts should be linked per student? Should there be a primary vs. secondary designation?

9. **Data Export Privacy**: Should exported student data include all fields, or should sensitive fields be filtered based on user permissions?

10. **Soft Delete Retention**: How long should soft-deleted records be retained before permanent deletion?

11. **Academic Year Transition**: How should the system handle the transition between academic years? Should data be automatically copied or manually initiated?

12. **Duplicate Student Detection**: Should the system implement automatic duplicate detection based on name, date of birth, or NISN? If so, what should the merge process be?
