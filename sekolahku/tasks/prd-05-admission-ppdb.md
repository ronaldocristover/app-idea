# PRD 05: Admission & PPDB (New Student Enrollment) Module

## Introduction

The Admission & PPDB (Penerimaan Peserta Didik Baru - New Student Admission) module manages the entire process of admitting new students to the school. This includes online registration forms, document submission, eligibility verification, selection processes, result announcements, and enrollment confirmation.

This module is crucial for streamlining the annual enrollment process, reducing administrative burden, ensuring fair and transparent admission decisions, and providing a positive experience for prospective students and their families.

## Goals

1. **Digitized Enrollment**: Transform the paper-based admission process into a fully digital experience
2. **Process Efficiency**: Reduce administrative time and effort in processing applications
3. **Transparency**: Provide clear, transparent admission criteria and processes
4. **Fair Selection**: Ensure objective, merit-based selection processes
5. **Parent Convenience**: Enable parents to complete enrollment from anywhere
6. **Data Quality**: Collect complete, accurate student data from the start
7. **Compliance**: Meet government regulations for student admissions

## User Stories

### Story 1: PPDB Configuration

**Description**: As a school administrator, I want to configure PPDB settings so that the enrollment process matches the school's requirements and government regulations.

**Acceptance Criteria**:
- Administrator can configure admission periods:
  - Academic year for admission
  - Registration opening date
  - Registration closing date
  - Selection period dates
  - Result announcement date
  - Enrollment confirmation deadline
- Administrator can define eligibility criteria:
  - Minimum age requirements by grade level
  - Previous education requirements
  - Residence requirements (catchment area if applicable)
  - Special program eligibility
  - Document requirements checklist
- Administrator can set capacity limits:
  - Total available seats per grade level
  - Seats per class
  - Quota categories (regular, scholarship, special needs, etc.)
- Administrator can configure selection methods:
  - First-come-first-served
  - Test-based selection
  - Lottery system
  - Points-based system (academic, distance, achievements)
  - Interview-based selection
  - Combination of methods
- Administrator can define document requirements:
  - Required documents list
  - File format specifications
  - Maximum file sizes
  - Document expiration rules
- Configuration can be copied from previous years
- System validates configuration before going live
- Settings are version-controlled with history

### Story 2: Online Registration Form

**Description**: As a prospective student/parent, I want to fill out an online registration form so that I can apply for admission without visiting the school.

**Acceptance Criteria**:
- Registration form includes:
  - **Student Information**:
    - Full name (as per birth certificate)
    - NISN (if available)
    - Place and date of birth
    - Gender
    - Religion
    - Blood type
    - Height and weight
    - Birth certificate upload
  - **Address Information**:
    - Complete address
    - Province, city, district, subdistrict
    - Postal code
    - Distance to school (auto-calculated if possible)
  - **Parent/Guardian Information**:
    - Father's name, ID number, occupation, education, phone, email
    - Mother's name, ID number, occupation, education, phone, email
    - Guardian information (if applicable)
    - Emergency contact
  - **Previous Education**:
    - Previous school name
    - School address
    - Graduation year
    - Graduation certificate/report card upload
  - **Health Information**:
    - Blood type
    - Medical conditions/allergies
    - Physical disabilities (if any)
  - **Special Information**:
    - Achievements and awards
    - Special talents
    - Extracurricular interests
- Form features:
  - Multi-step form with progress indicator
  - Save and continue later
  - Form validation (real-time)
  - File upload with progress indicators
  - Auto-save to prevent data loss
  - Preview before submission
  - Confirmation after submission
- Document uploads:
  - Birth certificate
  - Family card (Kartu Keluarga)
  - Parent ID cards (KTP)
  - Previous school report card
  - Photograph of student
  - Other required documents
- System generates:
  - Registration number
  - Application reference
  - Submission confirmation
  - Submission timestamp
- Form is mobile-responsive
- Progress can be resumed using registration number

### Story 3: Application Management

**Description**: As a school administrator, I want to manage received applications so that I can verify completeness and eligibility before the selection process.

**Acceptance Criteria**:
- Administrator can view all applications:
  - List view with key information
  - Search and filter options
  - Sort by various criteria
  - Export to spreadsheet
- Application details include:
  - All submitted information
  - Uploaded documents viewer
  - Submission date/time
  - Application status
  - Completeness check
  - Eligibility verification
- Administrator can update application status:
  - Received
  - Under review
  - Documents incomplete
  - Documents verified
  - Eligible for selection
  - Ineligible
  - Selected
  - Not selected
  - Waitlist
  - Enrolled
  - Declined
- Administrator can:
  - Mark documents as verified/unverified
  - Request additional documents
  - Add notes to applications
  - Flag applications for special attention
  - Contact applicants via system
- System tracks:
  - Status change history
  - Who made changes and when
  - Communications sent
- Bulk actions:
  - Change status for multiple applications
  - Send bulk communications
  - Export selected applications

### Story 4: Selection Process

**Description**: As a school administrator, I want to manage the student selection process so that fair admission decisions can be made based on defined criteria.

**Acceptance Criteria**:
- For test-based selection:
  - Schedule entrance exams
  - Generate exam admission cards
  - Record test scores
  - Upload test results
  - Calculate composite scores
- For points-based selection:
  - Define scoring criteria:
    - Academic achievement (previous grades)
    - Distance from school
    - Siblings in school
    - Parent alumni status
    - Special achievements
  - Input scores for each criterion
  - Calculate total scores automatically
  - Rank applicants by total score
- For lottery system:
  - Random selection algorithm
  - Auditable randomness
  - Witness capability
- For interview-based selection:
  - Schedule interview slots
  - Record interview scores/notes
  - Link interviews to applications
- System supports:
  - Multiple selection rounds
  - Waitlist management
  - Quota tracking by category
  - Automatic selection based on criteria
  - Manual selection adjustments
- Selection process features:
  - Selection dashboard
  - Real-time statistics
  - Capacity tracking
  - Quota utilization
  - Selection transparency log
- Selection results can be:
  - Approved before publication
  - Exported for official documentation
  - Archived for future reference

### Story 5: Entrance Examination (if applicable)

**Description**: As a school administrator, I want to manage entrance examinations so that academic aptitude can be assessed as part of the admission process.

**Acceptance Criteria**:
- Administrator can create exam schedules:
  - Date, time, location
  - Capacity per session
  - Subject areas tested
- System generates:
  - Exam admission cards (PDF)
  - Seat assignments
  - Exam attendance sheets
- Examination management:
  - Check-in process
  - Attendance tracking
  - Special accommodations
- Grading process:
  - Score entry interface
  - Multiple grader support
  - Score moderation workflow
  - Score calculation
- Exam results:
  - Individual score reports
  - Score distribution analysis
  - Statistical summary
- Communication:
  - Exam notifications to applicants
  - Result notifications
- Security:
  - Exam content protection
  - Secure score storage
  - Audit trail

### Story 6: Result Announcement

**Description**: As a school administrator, I want to announce selection results so that applicants know whether they have been admitted.

**Acceptance Criteria**:
- System can publish results:
  - On scheduled date/time
  - After administrative approval
  - With different visibility levels
- Result display:
  - Search by registration number
  - Individual result page
  - Public announcement (names only)
  - No detailed scores shown publicly
- Result information:
  - Selection status (accepted/rejected/waitlist)
  - Next steps for accepted students
  - Appeal process (if applicable)
  - Waitlist position
- Notification:
  - Email sent to all applicants
  - SMS notification (optional)
  - In-app notification
  - Acceptance letter download (for selected)
- Accepted students receive:
  - Official acceptance letter
  - Enrollment instructions
  - Required documents for enrollment
  - Fee information
  - Important dates
- Waitlist management:
  - Waitlist position shown
  - Automatic movement if spot opens
  - Notification of movement
- Rejected applicants receive:
  - Regret letter
  - General feedback (optional)
  - Information about appeal process (if applicable)

### Story 7: Enrollment Confirmation

**Description**: As a selected student/parent, I want to confirm enrollment so that my place at the school is secured.

**Acceptance Criteria**:
- Enrollment portal for confirmed students:
  - Login with registration number
  - View enrollment checklist
  - Upload additional documents
  - Complete required forms
  - Pay enrollment fee (if applicable)
- Enrollment steps:
  1. Accept offer of admission
  2. Complete enrollment form
  3. Upload remaining documents
  4. Pay enrollment/administrative fee
  5. Receive enrollment confirmation
- Administrator can:
  - Track enrollment progress
  - Send reminders to incomplete enrollments
  - Approve completed enrollments
  - Release spots for non-confirmations
- System automatically:
  - Converts enrolled students to active student records
  - Generates student ID (NIS)
  - Assigns to class (if determined)
  - Creates parent accounts
- Confirmation documents:
  - Enrollment confirmation letter
  - Student ID card information
  - Welcome packet
  - School calendar
  - Uniform and book information
- Timeline management:
  - Enrollment deadline
  - Automatic offer withdrawal if deadline passed
  - Waitlist promotion

### Story 8: PPDB Analytics & Reporting

**Description**: As a school administrator, I want analytics and reports on the PPDB process so that I can evaluate the admission process and make improvements.

**Acceptance Criteria**:
- Dashboard with real-time statistics:
  - Total registrations received
  - Registration progress over time
  - Applications by gender
  - Applications by catchment area
  - Capacity utilization
- Reports include:
  - Registration statistics by period
  - Applicant demographics
  - Previous school analysis
  - Selection outcome statistics
  - Enrollment yield rate
  - Drop-off analysis (where applicants abandon process)
- Export capabilities:
  - Raw data export
  - PDF reports
  - Presentation-ready summaries
- Comparison reports:
  - Year-over-year comparison
  - Target vs. actual
  - Category performance
- Communication analytics:
  - Email open rates
  - Notification delivery rates
  - Response times
- Process efficiency metrics:
  - Average processing time
  - Bottleneck identification
  - Staff workload distribution

## Functional Requirements

### 1. PPDB Configuration
- FR-PPDB-001: Configure admission periods and deadlines
- FR-PPDB-002: Define eligibility criteria
- FR-PPDB-003: Set capacity limits and quotas
- FR-PPDB-004: Configure selection methods
- FR-PPDB-005: Define required documents
- FR-PPDB-006: Copy configuration from previous years
- FR-PPDB-007: Validate configuration before activation

### 2. Registration
- FR-PPDB-008: Provide online registration form
- FR-PPDB-009: Support multi-step form with save
- FR-PPDB-010: Validate form inputs in real-time
- FR-PPDB-011: Handle file uploads securely
- FR-PPDB-012: Generate unique registration numbers
- FR-PPDB-013: Send registration confirmation
- FR-PPDB-014: Support mobile-responsive forms
- FR-PPDB-015: Enable partial form completion

### 3. Application Management
- FR-PPDB-016: View all applications with search/filter
- FR-PPDB-017: Update application status
- FR-PPDB-018: Verify uploaded documents
- FR-PPDB-019: Request additional documents
- FR-PPDB-020: Add notes to applications
- FR-PPDB-021: Track status change history
- FR-PPDB-022: Perform bulk status updates
- FR-PPDB-023: Export application data

### 4. Selection Process
- FR-PPDB-024: Implement various selection methods
- FR-PPDB-025: Calculate scores automatically
- FR-PPDB-026: Rank applicants by criteria
- FR-PPDB-027: Manage waitlist
- FR-PPDB-028: Track quota utilization
- FR-PPDB-029: Support selection rounds
- FR-PPDB-030: Audit selection decisions
- FR-PPDB-031: Generate selection reports

### 5. Entrance Examination
- FR-PPDB-032: Schedule exam sessions
- FR-PPDB-033: Generate exam admission cards
- FR-PPDB-034: Track exam attendance
- FR-PPDB-035: Record exam scores
- FR-PPDB-036: Calculate exam results
- FR-PPDB-037: Publish exam results

### 6. Results & Enrollment
- FR-PPDB-038: Publish selection results
- FR-PPDB-039: Send result notifications
- FR-PPDB-040: Generate acceptance letters
- FR-PPDB-041: Manage enrollment confirmation
- FR-PPDB-042: Convert enrolled to active students
- FR-PPDB-043: Generate student IDs
- FR-PPDB-044: Manage waitlist promotions

### 7. Analytics & Reporting
- FR-PPDB-045: Display real-time statistics
- FR-PPDB-046: Generate demographic reports
- FR-PPDB-047: Analyze process efficiency
- FR-PPDB-048: Compare year-over-year data
- FR-PPDB-049: Export data and reports
- FR-PPDB-050: Track communication metrics

### 8. Communication
- FR-PPDB-051: Send registration confirmation
- FR-PPDB-052: Send exam notifications
- FR-PPDB-053: Send result announcements
- FR-PPDB-054: Send enrollment reminders
- FR-PPDB-055: Support multiple communication channels
- FR-PPDB-056: Track message delivery

## Non-Goals

The following features are explicitly **out of scope** for this module:

- **Scholarship Management**: Detailed scholarship application and disbursement processes are not included
- **Advanced Testing**: Online entrance examination with AI proctoring is not included
- **Interview Scheduling**: Complex interview scheduling with video conferencing is not included
- **Document Verification**: Integration with government databases for document verification is not included
- **Payment Gateway**: Integration for enrollment fee payment is covered in Finance module
- **Alumni Management**: Tracking admitted students after graduation is not included
- **Marketing**: Lead generation and marketing automation features are not included
- **Campus Tours**: Scheduling and managing campus visits are not included

## Technical Considerations

### Architecture
- **High Availability**: System must handle high traffic during registration periods
- **Scalability**: Design for simultaneous registrations (hundreds per minute)
- **Microservices**: PPDB could be isolated service for independent scaling

### Performance
- **Load Testing**: Test for peak registration traffic
- **Database Optimization**: Optimize queries for application searches
- **CDN**: Use CDN for static assets and document storage
- **Caching**: Cache reference data and configuration
- **Background Jobs**: Use queue for document processing and notifications

### Security
- **Data Privacy**: Protect sensitive applicant information
- **Document Security**: Secure storage of uploaded documents
- **Access Control**: Role-based access to applicant data
- **Fraud Prevention**: Detect duplicate registrations
- **Audit Trail**: Complete audit of selection process
- **GDPR/Privacy**: Comply with data protection regulations

### User Experience
- **Mobile-First**: Optimize for mobile devices
- **Progressive Enhancement**: Works on slow connections
- **Form Usability**: Clear instructions and error messages
- **Auto-Save**: Prevent data loss
- **Accessibility**: WCAG 2.1 AA compliance

### Integration
- **Payment Gateway**: Integration for enrollment fees
- **SMS/Email**: Communication channels
- **Government Systems**: Potential integration with national PPDB system
- **Document Verification**: Possible integration with Dukcapil for ID verification

### Data Management
- **Backup**: Regular backups of applicant data
- **Archive**: Archive previous PPDB cycles
- **Export**: Data export for reporting
- **Retention**: Define data retention policy for rejected applicants

## Success Metrics

### Process Metrics
- **Registration Completion**: 85%+ of started registrations are completed
- **Document Submission**: 90%+ of applicants submit all required documents
- **Selection Time**: Selection completed within 1 week of closing
- **Enrollment Yield**: 90%+ of selected students confirm enrollment
- **Process Duration**: Average time from registration to enrollment < 4 weeks

### User Satisfaction
- **Parent Satisfaction**: 4.0+ out of 5.0 for registration process
- **Administrator Efficiency**: 50% reduction in time spent on PPDB
- **Support Requests**: Less than 5 support requests per 100 applicants
- **System Uptime**: 99.9% availability during registration period

### Quality Metrics
- **Data Accuracy**: 95%+ of applications have complete, accurate data
- **Document Quality**: 90%+ of uploaded documents are readable and valid
- **Registration Errors**: Less than 2% error rate in form submissions
- **Duplicate Detection**: 100% of duplicate registrations identified

### Operational Metrics
- **Capacity Utilization**: 100% of available seats filled
- **Waitlist Usage**: Minimal waitlist movement (indicates good yield)
- **Cost Savings**: 60% reduction in printing costs
- **Processing Time**: Application processing time reduced by 70%

## Open Questions

1. **Selection Method**: What selection method will be used? Is it purely first-come-first-served or merit-based?

2. **Government Integration**: Is there integration required with the national PPDB system (PPDB Online)?

3. **Document Verification**: Should there be integration with government databases (Dukcapil) for document verification?

4. **Testing Requirement**: Will entrance exams be conducted? If so, online or offline?

5. **Lottery System**: If lottery is used, how can we ensure and prove fairness?

6. **Appeals Process**: Is there an appeal process for rejected applicants? How should it work?

7. **Enrollment Fee**: Is there an enrollment/administrative fee? How is it collected?

8. **Special Needs**: How should the system handle applications from students with special needs?

9. **Catchment Area**: Is there a catchment area requirement? How is distance calculated?

10. **Sibling Priority**: Do siblings of current students get priority? How is this verified?

11. **Interview Requirement**: Are interviews part of the selection process?

12. **Age Calculation**: How is age calculated for eligibility? Based on what date?

13. **Data Retention**: How long should data from rejected applicants be retained?

14. **Multi-School**: If one organization runs multiple schools, can one application apply to multiple schools?

15. **Foreign Students**: How does the application process differ for foreign students?

16. **Transfer Students**: Is there a separate process for transfer students mid-year?

17. **Proof of Residence**: What documents are accepted as proof of residence?

18. **Registration Limits**: Should there be daily/hourly registration limits to manage server load?

19. **Public Statistics**: What statistics should be publicly displayed during PPDB?

20. **Result Publishing**: Should results be published all at once or in batches?
