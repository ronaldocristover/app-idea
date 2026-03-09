# PRD 02: Academic & Learning Management System (LMS)

## Introduction

The Academic & Learning Management System (LMS) module is the educational core of the School Management System. It manages all teaching and learning activities including subject management, curriculum planning, class scheduling, teaching journals, learning materials, assignments, online examinations, student grading, and electronic report cards (e-rapor).

This module bridges the gap between administrative management and actual educational delivery, providing tools for teachers to conduct their daily teaching activities and for students to engage with learning content. It serves as a comprehensive platform for academic operations, from planning to assessment and reporting.

## Goals

1. **Streamlined Academic Operations**: Provide integrated tools for all teaching and learning activities
2. **Curriculum Alignment**: Ensure all educational content aligns with national curriculum standards
3. **Data-Driven Teaching**: Enable teachers to make informed decisions based on student performance data
4. **Parent Engagement**: Keep parents informed about their children's academic progress
5. **Efficiency**: Reduce administrative burden on teachers through automation
6. **Compliance**: Generate standardized reports that meet regulatory requirements
7. **Digital Learning**: Support modern teaching methods with digital tools and resources

## User Stories

### Story 1: Subject Management

**Description**: As an academic administrator, I want to manage the complete list of subjects taught at the school so that the curriculum can be properly structured and scheduled.

**Acceptance Criteria**:
- Administrator can create subjects with:
  - Subject code (unique identifier)
  - Subject name (full and short names)
  - Subject group (e.g., Mathematics, Sciences, Languages, Arts)
  - Subject category (core, elective, extracurricular)
  - Grade levels applicable to
  - Credit hours/lesson hours per week
  - Minimum passing grade
  - Description
  - Prerequisite subjects (if any)
- Subjects can be linked to national curriculum codes (K13, Merdeka)
- Administrator can assign subject coordinators
- Subjects can be marked as active/inactive
- System prevents deletion of subjects used in active schedules
- Subject list can be filtered by grade level and category
- Subject details include curriculum mapping and learning objectives

### Story 2: Curriculum Management

**Description**: As an academic coordinator, I want to define and manage curriculum for each subject so that teachers have clear guidance on what to teach and how to assess learning.

**Acceptance Criteria**:
- Coordinator can create curriculum documents with:
  - Subject and grade level association
  - Academic year/semester applicability
  - Core competencies (Kompetensi Inti - KI)
  - basic competencies (Kompetensi Dasar - KD)
  - Learning objectives
  - Topics/learning materials sequence
  - Suggested teaching methods
  - Assessment criteria and methods
  - Minimum completion requirements
  - Allocated time per topic
- Curriculum can follow national standards (K13 or Kurikulum Merdeka)
- Curriculum can be customized per school requirements
- System tracks curriculum version history
- Teachers can view curriculum for their assigned subjects
- Coordinator can copy curriculum from previous semester/academic year
- System supports curriculum sharing between schools
- Curriculum can be exported as PDF document

### Story 3: Class Scheduling (Jadwal Pelajaran)

**Description**: As an academic administrator, I want to create and manage class schedules so that students and teachers know when and where each class will take place.

**Acceptance Criteria**:
- Administrator can create schedules with:
  - Academic year, semester, and class association
  - Day of week and time slot
  - Subject and teacher assignment
  - Room/location assignment
  - Duration of class session
  - Schedule status (active, cancelled, substitute)
- System displays schedules in:
  - Daily timetable view
  - Weekly calendar view
  - List view by class
  - List view by teacher
- System prevents scheduling conflicts:
  - Same class at same time
  - Same teacher at same time in different locations
  - Same room at same time
- Administrator can define time slots for different grade levels
- System supports rotating schedules (week A/B patterns)
- Schedule changes trigger notifications to affected parties
- System can generate optimal schedule automatically (optional)
- Schedule can be printed or exported as PDF
- Substitute teacher assignments are supported

### Story 4: Teacher Scheduling Management

**Description**: As an academic administrator, I want to view and manage teacher workloads so that teaching assignments are distributed fairly and comply with regulations.

**Acceptance Criteria**:
- Administrator can view teacher schedules:
  - Complete weekly schedule for each teacher
  - Total teaching hours per week
  - Breakdown by grade level and subject
  - Free periods/breaks
- System calculates teacher workload:
  - Total teaching hours
  - Administrative/other duties
  - Compliance with maximum teaching hours (regulation)
- Administrator can see which teachers are:
  - Overloaded (exceeds maximum hours)
  - Underloaded (below minimum hours)
  - Available for additional assignments
- System highlights potential double-booking
- Schedule changes update workload calculations automatically
- Reports can be generated showing workload distribution
- Historical schedule data is retained for planning purposes

### Story 5: Teaching Journal (Jurnal Mengajar)

**Description**: As a teacher, I want to maintain a digital teaching journal so that I can record what was taught, track lesson progress, and document student attendance.

**Acceptance Criteria**:
- Teacher can create journal entries for each class session with:
  - Date, time, class, subject
  - Topics covered (linked to curriculum)
  - Teaching methods used
  - Student attendance (present, absent, permission, sick)
  - General notes and observations
  - Assignments given
  - Homework assigned
  - Next lesson plan
- Journal entries can include:
  - Photos of classroom activities
  - Attached teaching materials
  - Links to online resources
- System supports bulk attendance marking
- Absences can be marked with reasons
- Journal entries are time-stamped and cannot be modified after X days
- Homeroom teacher can review class journals
- Administrator can generate reports from journal data
- System tracks percentage of curriculum completed
- Journal data feeds into student attendance records

### Story 6: Learning Materials Management

**Description**: As a teacher, I want to upload and organize learning materials so that students can access resources anytime and review content at their own pace.

**Acceptance Criteria**:
- Teacher can upload materials with:
  - Title and description
  - Material type (document, presentation, video, audio, link, etc.)
  - Subject and topic association
  - Class/grade level targeting
  - Publication date range
  - Attachment files (PDF, PPT, video, images)
  - External links
- System supports multiple file formats:
  - Documents: PDF, DOC, DOCX, PPT, PPTX
  - Images: JPG, PNG, GIF
  - Videos: MP4, AVI, MOV (or YouTube/Vimeo links)
  - Audio: MP3, WAV
- Materials are organized by:
  - Subject and grade level
  - Topic/chapter
  - Date posted
- Students can view/download materials assigned to their classes
- System tracks download/view counts
- Materials can be marked as required or supplementary
- Teacher can update materials with version tracking
- Old materials can be archived instead of deleted
- System supports material sharing between teachers
- Materials can be scheduled for automatic publication
- File size limits are enforced
- Materials are accessible via mobile app

### Story 7: Student Assignments (Tugas Siswa)

**Description**: As a teacher, I want to create and manage student assignments so that I can assess learning progress and provide timely feedback.

**Acceptance Criteria**:
- Teacher can create assignments with:
  - Assignment title and description
  - Associated subject, class, and topic
  - Assignment type (homework, project, practice, etc.)
  - Due date and time
  - Maximum score/points
  - Instructions and requirements
  - Attachments (reference materials, templates)
  - Rubric/grading criteria
  - Individual or group assignment designation
- Students can submit assignments:
  - Upload files (documents, images, etc.)
  - Submit text responses
  - Submit links to online work
  - Submit as group (one submission per group)
- System tracks submission status:
  - Not submitted
  - Submitted on time
  - Submitted late
  - Not submitted (deadline passed)
- Teacher can grade submissions with:
  - Numeric score
  - Written feedback
  - Annotated feedback on submitted files
  - Rubric-based assessment
- Students receive notification when:
  - Assignment is posted
  - Deadline is approaching
  - Assignment is graded
- Teacher can grant extension for individual students
- Late submissions are marked with submission time
- System tracks late submission penalties (if applicable)
- Assignments can be copied/adapted for other classes
- Assignment statistics show:
  - Submission rate
  - Average score
  - Score distribution
  - Not submitted list

### Story 8: Online Examinations (Ujian Online)

**Description**: As a teacher, I want to create and conduct online examinations so that I can efficiently assess student understanding with automatic grading where possible.

**Acceptance Criteria**:
- Teacher can create exams with:
  - Exam title and instructions
  - Associated subject, class, and topics
  - Exam duration
  - Exam availability window (start and end datetime)
  - Maximum score
  - Passing grade
  - Number of attempts allowed
  - Question randomization option
  - Answer randomization option
  - Show/hide results during or after exam
- System supports multiple question types:
  - Multiple choice (single answer)
  - Multiple choice (multiple answers)
  - True/False
  - Matching
  - Fill-in-the-blank
  - Short answer
  - Essay
- Teacher can create question bank:
  - Organized by subject and topic
  - Tagged by difficulty level
  - Shared between teachers
  - Import/export questions
- Exam can be configured to:
  - Randomly select questions from bank
  - Present questions in random order
  - Present answers in random order
  - Allow navigation (or one question at a time)
  - Show timer
  - Auto-submit when time expires
- Student exam experience:
  - Secure browser (optional, prevents cheating)
  - Auto-save answers
  - Timer countdown
  - Question review and flagging
  - Submit before time limit
- Grading:
  - Automatic grading for objective questions
  - Manual grading interface for subjective questions
  - Partial credit support
  - Comment/feedback per question
- Exam security:
  - Access code requirement
  - IP restriction (school only)
  - Browser integrity check
  - Prevent copy/paste
- Exam results:
  - Immediate or delayed feedback
  - Detailed review of answers
  - Score breakdown by topic
  - Comparison with class average
- System generates exam statistics and analytics
- Exam can be published as practice test

### Story 9: Student Grading (Nilai Siswa)

**Description**: As a teacher, I want to record and manage student grades so that academic progress can be tracked and reported accurately.

**Acceptance Criteria**:
- Teacher can record grades for:
  - Assignments
  - Exams/Quizzes
  - Projects
  - Class participation
  - Practical work
  - Other assessments
- Grade entry interface supports:
  - List view by class and subject
  - Individual student grade detail
  - Bulk grade entry
  - Import from spreadsheet
- Grading scales are configurable:
  - Letter grades (A, B, C, D, E)
  - Numeric scales (0-100)
  - Descriptive scales (Excellent, Good, Fair, Poor)
  - Custom scales per school
- System calculates:
  - Assignment averages
  - Formative assessment scores
  - Summative assessment scores
  - Final grades using configurable weighting
  - Class rank (optional)
- Teacher can add:
  - Grade comments
  - Notes for improvement
  - Behavioral observations
- System tracks grade changes with audit trail
- Missing/incomplete grades are highlighted
- Grades can be exported to spreadsheet
- Grade calculations follow school's grading policy
- System supports grade moderation/approval workflow
- Historical grades are retained for transcript purposes

### Story 10: Electronic Report Cards (E-Rapor)

**Description**: As a teacher and administrator, I want to generate electronic report cards so that students and parents receive comprehensive, standardized academic reports.

**Acceptance Criteria**:
- System generates e-rapor with:
  - Student information and photo
  - Academic year and semester
  - Class and homeroom teacher
  - Grades for all subjects
  - Grade breakdown (assignments, exams, participation)
  - Attendance summary
  - Class ranking (if enabled)
  - Teacher comments for each subject
  - Homeroom teacher general comments
  - School achievements and extracurricular activities
  - Signature area (principal, homeroom teacher)
- E-rapor formats:
  - PDF download
  - Online view
  - Printable version
- Report cards can be generated:
  - Per student
  - Per class (bulk)
  - For specific grading period
- Report cards include:
  - Grade legends/explanations
  - School information and logo
  - Next grade level placement
  - Promotion/retention status
- System tracks:
  - Report card generation date
  - Report card download history
- Parents receive notification when report card is available
- Report cards are archived permanently
- System supports custom report card templates
- Report card can be signed digitally (optional)
- Report cards can be shared via parent portal
- System generates statistical reports:
  - Class average comparison
  - Subject distribution
  - Grade trends

## Functional Requirements

### 1. Subject Management
- FR-LMS-001: Create, read, update, deactivate subjects
- FR-LMS-002: Link subjects to grade levels and curriculum
- FR-LMS-003: Assign subject coordinators
- FR-LMS-004: Define subject groups and categories
- FR-LMS-005: Set minimum passing grades per subject
- FR-LMS-006: Define prerequisite subject relationships

### 2. Curriculum Management
- FR-LMS-007: Create curriculum documents per subject and grade
- FR-LMS-008: Define competencies and learning objectives
- FR-LMS-009: Map topics to time allocation
- FR-LMS-010: Version control for curriculum documents
- FR-LMS-011: Copy curriculum between academic periods
- FR-LMS-012: Export curriculum as PDF
- FR-LMS-013: Track curriculum completion percentage

### 3. Scheduling
- FR-LMS-014: Create class schedules with day/time/room
- FR-LMS-015: Assign subjects and teachers to schedule slots
- FR-LMS-016: Prevent scheduling conflicts
- FR-LMS-017: Define configurable time slots
- FR-LMS-018: Support rotating schedule patterns
- FR-LMS-019: Display schedules in multiple views
- FR-LMS-020: Print/export schedule as PDF
- FR-LMS-021: Support substitute teacher assignments
- FR-LMS-022: Calculate teacher workload from schedule

### 4. Teaching Journals
- FR-LMS-023: Create journal entries per class session
- FR-LMS-024: Record student attendance in journal
- FR-LMS-025: Link journal entries to curriculum topics
- FR-LMS-026: Attach materials to journal entries
- FR-LMS-027: Prevent modification after deadline
- FR-LMS-028: Generate reports from journal data
- FR-LMS-029: Track curriculum completion progress

### 5. Learning Materials
- FR-LMS-030: Upload and organize learning materials
- FR-LMS-031: Support multiple file formats
- FR-LMS-032: Organize materials by subject, grade, topic
- FR-LMS-033: Control material visibility by class
- FR-LMS-034: Schedule material publication
- FR-LMS-035: Track material access statistics
- FR-LMS-036: Archive outdated materials
- FR-LMS-037: Share materials between teachers

### 6. Assignments
- FR-LMS-038: Create assignments with configurable parameters
- FR-LMS-039: Accept various submission formats
- FR-LMS-040: Track submission status and timing
- FR-LMS-041: Grade submissions with feedback
- FR-LMS-042: Apply late submission penalties
- FR-LMS-043: Grant individual extensions
- FR-LMS-044: Send assignment notifications
- FR-LMS-045: Generate assignment statistics

### 7. Online Examinations
- FR-LMS-046: Create exams with various configurations
- FR-LMS-047: Build and manage question banks
- FR-LMS-048: Support multiple question types
- FR-LMS-049: Configure exam security settings
- FR-LMS-050: Randomize questions and answers
- FR-LMS-051: Auto-grade objective questions
- FR-LMS-052: Provide manual grading interface
- FR-LMS-053: Control result display timing
- FR-LMS-054: Generate exam analytics

### 8. Grading
- FR-LMS-055: Record grades for various assessment types
- FR-LMS-056: Support multiple grading scales
- FR-LMS-057: Calculate weighted averages
- FR-LMS-058: Track grade changes with audit trail
- FR-LMS-059: Import/export grade data
- FR-LMS-060: Generate grade statistics
- FR-LMS-061: Implement grade approval workflow

### 9. E-Rapor
- FR-LMS-062: Generate report cards per student
- FR-LMS-063: Bulk generate report cards per class
- FR-LMS-064: Customize report card templates
- FR-LMS-065: Include comprehensive academic information
- FR-LMS-066: Archive report cards permanently
- FR-LMS-067: Notify parents of available reports
- FR-LMS-068: Support digital signatures
- FR-LMS-069: Generate statistical reports

### 10. General
- FR-LMS-070: Integrate with notification system
- FR-LMS-071: Provide role-based access to academic data
- FR-LMS-072: Audit all academic activity
- FR-LMS-073: Support mobile app access
- FR-LMS-074: Provide APIs for third-party integrations

## Non-Goals

The following features are explicitly **out of scope** for this module:

- **Advanced Learning Analytics**: Predictive analytics and AI-driven learning insights are not included in initial version
- **Video Conferencing**: Built-in video conferencing for online classes is not included (can integrate third-party)
- **Plagiarism Detection**: Automatic plagiarism checking for submissions is not included
- **Social Learning Features**: Discussion forums, peer collaboration tools are not included
- **Gamification**: Badges, leaderboards, and learning games are not included
- **Adaptive Learning**: Personalized learning paths based on performance are not included
- **Parent-Teacher Conference Scheduling**: Meeting scheduling is handled by Communication module
- **Library Integration**: Book catalog and reading lists are not included
- **Special Education Tools**: IEP (Individualized Education Program) management is not included
- **Teacher Evaluation Tools**: Performance appraisal for teachers is not included

## Technical Considerations

### Architecture
- **Microservices Consideration**: LMS module could be separated into its own service for scalability
- **Database**: Use document database or hybrid approach for flexible curriculum and question data
- **Storage**: Use cloud storage for large files (videos, documents)
- **Caching**: Cache frequently accessed content like materials and exams

### Performance
- **Content Delivery**: Use CDN for static learning materials
- **Database Optimization**: Index frequently queried fields (student grades, submissions)
- **Load Balancing**: Prepare for high traffic during exam periods
- **Background Jobs**: Use queue for grade calculations and report generation
- **Lazy Loading**: Implement pagination for large class lists and grade books

### Security
- **Exam Security**: Implement browser integrity checks, prevent tab switching
- **Content Protection**: Prevent unauthorized downloading of copyrighted materials
- **Access Control**: Fine-grained permissions for viewing grades and reports
- **Data Privacy**: Encrypt sensitive student performance data
- **Audit Logging**: Track all grade changes and access to student data

### User Experience
- **Mobile Responsiveness**: Ensure all features work on mobile devices
- **Offline Support**: Allow viewing downloaded materials offline
- **Progressive Web App**: Consider PWA for mobile app alternative
- **Accessibility**: Ensure WCAG 2.1 AA compliance for accessibility

### Integration
- **Single Sign-On**: Integrate with school SSO system
- **Calendar Integration**: Sync exam schedules with external calendars
- **Notification Channels**: Support email, SMS, and in-app notifications
- **Third-Party Tools**: Consider LTI (Learning Tools Interoperability) for external tool integration

### Data Management
- **Backup**: Automated backups of all academic data
- **Archive**: Move old academic data to cold storage
- **Export**: Standard formats for data portability
- **Import**: Tools for migrating from other LMS platforms
- **Data Retention**: Configurable retention policies for submissions and materials

## Success Metrics

### Engagement Metrics
- **Teacher Adoption**: 90% of teachers use teaching journals weekly
- **Material Usage**: Average of 3 materials viewed per student per week
- **Assignment Completion**: 85% average assignment submission rate
- **Exam Participation**: 95% of eligible students complete online exams

### Learning Outcomes
- **Grade Tracking**: 100% of grades recorded within 1 week of assessment
- **Report Card Generation**: 100% of report cards generated within 2 weeks of semester end
- **Parent Access**: 80% of parents access report cards within first month of availability
- **Attendance Accuracy**: 98% accuracy in attendance tracking

### System Performance
- **Exam Stability**: 99.5% uptime during scheduled exams
- **Content Delivery**: 95% of materials load within 3 seconds
- **Grading Efficiency**: 50% reduction in grading time for objective questions
- **Mobile Usage**: 60% of material views via mobile app

### User Satisfaction
- **Teacher Satisfaction**: 4.0+ out of 5.0 in semi-annual surveys
- **Student Satisfaction**: 4.0+ out of 5.0 for ease of use
- **Parent Satisfaction**: 4.0+ out of 5.0 for report card accessibility
- **Support Tickets**: Less than 3 tickets per 100 users per month

## Open Questions

1. **Offline Assessment**: How should the system handle offline exams? Should there be a separate workflow for paper-based exams?

2. **Grade Scaling**: Should the system support automatic grade scaling (curving) to ensure grade distribution meets school policies?

3. **Third-Party Content**: Should teachers be able to embed content from external platforms (YouTube, Khan Academy, etc.) directly in the LMS?

4. **Plagiarism Detection**: Is integration with plagiarism detection services (Turnitin, etc.) required? What budget is available?

5. **Exam Proctoring**: What level of online proctoring is needed for remote exams? Webcam monitoring? Browser lockdown?

6. **Multiple Intelligences**: Should the system support different assessment methods for different learning styles?

7. **Parent Grade Access**: Should parents have real-time access to grades throughout the term, or only see final report cards?

8. **Question Bank Sharing**: Should question banks be shared across schools in the organization, or kept private per school?

9. **Learning Analytics**: What level of learning analytics is needed? Should we track time spent on materials, login frequency, etc.?

10. **Curriculum Flexibility**: How much curriculum customization is needed per class? Should all classes follow same curriculum or can teachers customize?

11. **Group Work Assessment**: What features are needed for group assignments? Individual grades within groups? Peer evaluation?

12. **Special Accommodations**: How should the system handle students with special needs or learning disabilities in assessments?

13. **Grade Appeals**: Is there a formal process for grade appeals? How should this be managed in the system?

14. **Cross-Curricular Projects**: Should the system support projects that span multiple subjects? How would grading work?

15. **Data Retention**: How long should student work (submissions, exam responses) be retained? Can students access past work?

16. **Export Formats**: What formats are required for official grade submissions to education authorities?

17. **Language Support**: Is multi-language support needed for the LMS interface and content?

18. **Mobile Exam Taking**: Should students be able to take exams on mobile devices, or restrict to desktop/laptop only?

19. **Collaborative Learning**: Are discussion forums, peer review, or collaborative annotation features needed?

20. **AI Integration**: Should AI features like automatic grading of essays or personalized recommendations be considered?
