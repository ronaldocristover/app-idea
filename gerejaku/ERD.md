# Gerejaku - Entity Relationship Diagram (Mermaid)

```mermaid
erDiagram
    %% Organisasi & Struktur Gereja
    District ||--o{ Resort : "contains"
    Resort ||--o{ Parish : "contains"
    Parish ||--o{ Church : "contains"
    Parish ||--o{ Ward : "contains"
    Church ||--o{ Ward : "has"

    District {
        int id PK
        string code UK
        string name
        text description
        boolean status
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    Resort {
        int id PK
        string code UK
        string name
        int district_id FK
        text description
        boolean status
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    Parish {
        int id PK
        string code UK
        string name
        int resort_id FK
        text description
        boolean status
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    Church {
        int id PK
        string code UK
        string name
        int district_id FK
        int resort_id FK
        int parish_id FK
        string address
        string phone
        string email
        boolean status
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    Ward {
        int id PK
        string code UK
        string name
        int parish_id FK
        int church_id FK
        text description
        boolean status
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    %% Keanggotaan
    Ward ||--o{ Family : "contains"
    Family ||--o{ Member : "has"
    Church ||--o{ Member : "registers"

    Family {
        int id PK
        string family_number UK
        string family_name
        int ward_id FK
        int church_id FK
        string address
        string phone
        string category
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    Member {
        int id PK
        string member_number UK
        int family_id FK
        int church_id FK
        int ward_id FK
        string first_name
        string last_name
        string nik
        date birth_date
        string gender
        string marital_status
        string blood_type
        string education_level
        string profession
        string emergency_contact
        string medical_conditions
        string talents_skills
        string spiritual_maturity
        date membership_date
        string membership_status
        date death_date
        string photo
        boolean status
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    Family_Member {
        int id PK
        int family_id FK
        int member_id FK
        string relationship_type
        int family_order
        boolean is_head
    }

    %% Dokumen
    Member ||--o{ Document : "has"
    Baptism ||--o{ Baptism_Document : "has"
    Marriage ||--o{ Marriage_Document : "has"

    Document {
        int id PK
        int member_id FK
        string document_type
        string title
        string file_path
        string category
        int version
        boolean is_confidential
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    %% Sakramen & Upacara
    Member ||--o{ Baptism : "receives"
    Church ||--o{ Baptism : "performs"

    Baptism {
        int id PK
        int member_id FK
        int church_id FK
        date baptism_date
        string location
        string officiant
        string baptism_type
        text notes
        boolean certificate_issued
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    Baptism_Document {
        int id PK
        int baptism_id FK
        string document_type
        string file_path
        string title
        boolean is_certificate
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    Member ||--o{ Marriage : "participates"
    Church ||--o{ Marriage : "performs"

    Marriage {
        int id PK
        int male_member_id FK
        int female_member_id FK
        int church_id FK
        date approval_date
        date wedding_date
        string location
        string officiant
        string marriage_status
        boolean certificate_issued
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    Marriage_Document {
        int id PK
        int marriage_id FK
        string document_type
        string file_path
        string title
        boolean is_certificate
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    %% Registrasi & Status
    Member ||--o{ Registration : "has"
    Member ||--o{ Membership_History : "tracks"
    Member ||--o{ Membership_Status : "has"

    Registration {
        int id PK
        int member_id FK
        date registration_date
        string registration_type
        string status
        text notes
        int approved_by
        date approval_date
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    Membership_Status {
        int id PK
        int member_id FK
        string status
        date effective_date
        string reason
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    Membership_History {
        int id PK
        int member_id FK
        string action
        text old_value
        text new_value
        string reason
        int changed_by
        timestamp created_at
    }

    %% Keuangan & Persembahan
    Member ||--o{ Offering : "gives"
    Church ||--o{ Offering : "receives"

    Offering {
        int id PK
        int member_id FK
        int church_id FK
        date offering_date
        string service_type
        string offering_category
        decimal amount
        string payment_method
        string envelope_number
        boolean is_tithe
        text notes
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    Department ||--o{ Budget : "has"

    Budget {
        int id PK
        int department_id FK
        int year
        string category
        decimal planned_amount
        decimal actual_amount
        string status
        int approved_by
        date approval_date
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    Church ||--o{ Expense : "incurs"

    Expense {
        int id PK
        int church_id FK
        int budget_id FK
        date expense_date
        string category
        string description
        decimal amount
        string status
        int approved_by
        string receipt_path
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    Member ||--o{ Donation : "contributes"

    Donation {
        int id PK
        int member_id FK
        date donation_date
        string fund_type
        decimal amount
        string donation_purpose
        boolean acknowledgment_sent
        text notes
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    %% Pelayanan & Departemen
    Church ||--o{ Department : "has"
    Member ||--o{ Department_Member : "serves_in"
    Department ||--o{ Department_Member : "has"

    Department {
        int id PK
        int church_id FK
        string name
        string code
        text description
        string leader_name
        boolean status
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    Department_Member {
        int id PK
        int department_id FK
        int member_id FK
        string role
        date start_date
        date end_date
        string status
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    Member ||--o{ Volunteer_Schedule : "serves"

    Volunteer_Schedule {
        int id PK
        int member_id FK
        int department_id FK
        date service_date
        string service_type
        string role
        string status
        text notes
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    Member ||--o{ Spiritual_Gift : "possesses"

    Spiritual_Gift {
        int id PK
        int member_id FK
        string gift_type
        string skill_level
        text assessment_notes
        date assessment_date
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    Member ||--o{ Training : "attends"

    Training {
        int id PK
        string name
        string description
        date start_date
        date end_date
        string location
        string trainer
        boolean certification
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    Member ||--o{ Training_Attendance : "participates"
    Training ||--o{ Training_Attendance : "has"

    Training_Attendance {
        int id PK
        int training_id FK
        int member_id FK
        date attendance_date
        string status
        text notes
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    %% Attendance & Kehadiran
    Member ||--o{ Attendance : "records"
    Church ||--o{ Attendance : "tracks"

    Attendance {
        int id PK
        int member_id FK
        int church_id FK
        date attendance_date
        string service_type
        time check_in_time
        time check_out_time
        string attendance_status
        boolean is_guest
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    Church ||--o{ Monthly_Statistics : "submits"

    Monthly_Statistics {
        int id PK
        int church_id FK
        int year
        int month
        int total_members
        int average_attendance
        int new_baptisms
        int new_marriages
        int deaths
        int transfers_in
        int transfers_out
        decimal total_offering
        string status
        int submitted_by
        date submission_date
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    Member ||--o{ Small_Group : "joins"

    Small_Group {
        int id PK
        int church_id FK
        string name
        string leader_name
        string meeting_day
        time meeting_time
        string location
        boolean status
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    Member ||--o{ Small_Group_Attendance : "attends"
    Small_Group ||--o{ Small_Group_Attendance : "has"

    Small_Group_Attendance {
        int id PK
        int small_group_id FK
        int member_id FK
        date meeting_date
        string attendance_status
        boolean is_visitor
        text notes
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    %% Visitasi & Pemuridan
    Member ||--o{ Pastoral_Visit : "receives"
    Member ||--o{ Pastoral_Visit : "conducts"

    Pastoral_Visit {
        int id PK
        int visitor_id FK
        int visitee_id FK
        date visit_date
        string visit_type
        string purpose
        text outcome
        text follow_up_actions
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    Member ||--o{ Counseling_Session : "attends"

    Counseling_Session {
        int id PK
        int member_id FK
        int counselor_id FK
        date session_date
        string session_type
        text notes
        boolean is_confidential
        text follow_up_actions
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    Member ||--o{ Discipleship_Group : "joins"

    Discipleship_Group {
        int id PK
        int church_id FK
        string name
        int leader_id FK
        string curriculum
        string meeting_schedule
        boolean status
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    Member ||--o{ Discipleship_Group_Member : "participates"
    Discipleship_Group ||--o{ Discipleship_Group_Member : "has"

    Discipleship_Group_Member {
        int id PK
        int group_id FK
        int member_id FK
        date join_date
        string status
        text progress_notes
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    Member ||--o{ Prayer_Request : "submits"

    Prayer_Request {
        int id PK
        int member_id FK
        date request_date
        string subject
        text description
        string privacy_level
        string status
        date answered_date
        text praise_report
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    Member ||--o{ Follow_Up : "needs"
    Member ||--o{ Follow_Up : "assigned_to"

    Follow_Up {
        int id PK
        int member_id FK
        int assigned_to FK
        string priority
        string action_type
        text description
        date due_date
        string status
        text completion_notes
        date completed_date
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    %% Komunikasi
    Church ||--o{ Announcement : "publishes"

    Announcement {
        int id PK
        int church_id FK
        string title
        string category
        text content
        string target_audience
        date publish_date
        date expiry_date
        boolean status
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    Church ||--o{ Event : "hosts"

    Event {
        int id PK
        int church_id FK
        string name
        string description
        datetime start_datetime
        datetime end_datetime
        string location
        int max_attendees
        string registration_deadline
        boolean status
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    Member ||--o{ Event_Registration : "registers_for"
    Event ||--o{ Event_Registration : "has"

    Event_Registration {
        int id PK
        int event_id FK
        int member_id FK
        date registration_date
        string status
        text notes
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    Church ||--o{ Broadcast : "sends"

    Broadcast {
        int id PK
        int church_id FK
        string broadcast_type
        string subject
        text message
        string target_group
        datetime scheduled_date
        string status
        int delivery_count
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    %% Diakonia & Kesejahteraan
    Member ||--o{ Social_Assistance : "receives"
    Church ||--o{ Social_Assistance : "provides"

    Social_Assistance {
        int id PK
        int member_id FK
        int church_id FK
        date assistance_date
        string assistance_type
        string description
        decimal amount
        string frequency
        string status
        int approved_by
        date approval_date
        text notes
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    Member ||--o{ Medical_Assistance : "receives"
    Church ||--o{ Medical_Assistance : "provides"

    Medical_Assistance {
        int id PK
        int member_id FK
        int church_id FK
        date assistance_date
        string hospital_name
        string diagnosis
        decimal amount
        string status
        int approved_by
        text follow_up_notes
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    Member ||--o{ Education_Support : "receives"
    Church ||--o{ Education_Support : "provides"

    Education_Support {
        int id PK
        int member_id FK
        int church_id FK
        string scholarship_type
        string education_level
        decimal amount
        string academic_year
        string status
        int approved_by
        text academic_progress
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    Member ||--o{ Disaster_Relief : "receives"
    Church ||--o{ Disaster_Relief : "provides"

    Disaster_Relief {
        int id PK
        int member_id FK
        int church_id FK
        date relief_date
        string disaster_type
        string description
        decimal amount
        string status
        text distribution_notes
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    %% Asset & Inventaris
    Church ||--o{ Property : "owns"

    Property {
        int id PK
        int church_id FK
        string property_type
        string name
        string address
        decimal purchase_value
        date purchase_date
        string insurance_policy
        boolean status
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    Church ||--o{ Equipment : "has"

    Equipment {
        int id PK
        int church_id FK
        string name
        string category
        string serial_number
        string brand
        string model
        date purchase_date
        decimal purchase_value
        string condition
        string location
        boolean status
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    Equipment ||--o{ Equipment_Checkout : "checked_out_from"
    Member ||--o{ Equipment_Checkout : "checks_out"

    Equipment_Checkout {
        int id PK
        int equipment_id FK
        int member_id FK
        datetime checkout_date
        datetime return_date
        string status
        text notes
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    Church ||--o{ Maintenance : "requires"
    Property ||--o{ Maintenance : "needs"
    Equipment ||--o{ Maintenance : "needs"

    Maintenance {
        int id PK
        int church_id FK
        int maintainable_id
        string maintainable_type
        string maintenance_type
        string description
        date scheduled_date
        date completed_date
        decimal cost
        string vendor
        string status
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    Church ||--o{ Facility_Booking : "books_for"
    Member ||--o{ Facility_Booking : "books"

    Facility_Booking {
        int id PK
        int church_id FK
        int member_id FK
        string facility_name
        datetime start_datetime
        datetime end_datetime
        string purpose
        string status
        int approved_by
        text notes
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    %% Kematian & Dukacita
    Member ||--o{ Death_Record : "has"
    Church ||--o{ Death_Record : "records"

    Death_Record {
        int id PK
        int member_id FK
        int church_id FK
        date death_date
        string cause_of_death
        string funeral_location
        date funeral_date
        string officiant
        text funeral_service_details
        boolean is_archived
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    Death_Record ||--o{ Bereaved_Followup : "requires"

    Bereaved_Followup {
        int id PK
        int death_record_id FK
        date contact_date
        string contact_type
        text notes
        string support_provided
        int contacted_by
        date next_followup_date
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    %% Auth & User Management
    User ||--o{ Audit_Log : "creates"
    User ||--o{ User_Role : "has"
    Role ||--o{ User_Role : "assigned_to"
    Role ||--o{ Permission : "has"

    User {
        int id PK
        string username UK
        string email UK
        string password
        string first_name
        string last_name
        string phone
        boolean status
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    Role {
        int id PK
        string name UK
        string description
        boolean status
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    User_Role {
        int id PK
        int user_id FK
        int role_id FK
        date assigned_date
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    Permission {
        int id PK
        int role_id FK
        string module
        string action
        boolean can_create
        boolean can_read
        boolean can_update
        boolean can_delete
        int created_by
        int updated_by
        timestamp created_at
        timestamp updated_at
    }

    Audit_Log {
        int id PK
        int user_id FK
        string action
        string table_name
        int record_id
        text old_values
        text new_values
        string ip_address
        string user_agent
        timestamp created_at
    }
```

## Entity Groups

### 1. Organisasi & Struktur Gereja
- District, Resort, Parish, Church, Ward

### 2. Keanggotaan
- Family, Member, Family_Member

### 3. Dokumen
- Document, Baptism_Document, Marriage_Document

### 4. Sakramen & Upacara
- Baptism, Marriage

### 5. Registrasi & Status
- Registration, Membership_Status, Membership_History

### 6. Keuangan & Persembahan
- Offering, Budget, Expense, Donation

### 7. Pelayanan & Departemen
- Department, Department_Member, Volunteer_Schedule, Spiritual_Gift, Training, Training_Attendance

### 8. Attendance & Kehadiran
- Attendance, Monthly_Statistics, Small_Group, Small_Group_Attendance

### 9. Visitasi & Pemuridan
- Pastoral_Visit, Counseling_Session, Discipleship_Group, Discipleship_Group_Member, Prayer_Request, Follow_Up

### 10. Komunikasi
- Announcement, Event, Event_Registration, Broadcast

### 11. Diakonia & Kesejahteraan
- Social_Assistance, Medical_Assistance, Education_Support, Disaster_Relief

### 12. Asset & Inventaris
- Property, Equipment, Equipment_Checkout, Maintenance, Facility_Booking

### 13. Kematian & Dukacita
- Death_Record, Bereaved_Followup

### 14. Auth & User Management
- User, Role, User_Role, Permission, Audit_Log

## Total Statistics
- **Total Tables**: 65+
- **Total Relationships**: 80+
- **Module Coverage**: All 19 main modules from MODULES.md

## Legend
- **||--o{** = One-to-Many relationship
- **||--|{** = One-to-One relationship
- **PK** = Primary Key
- **FK** = Foreign Key
- **UK** = Unique Key
