# Module Keuangan & Persembahan - Detailed Specification

## Overview
Module ini adalah **sistem manajemen keuangan gereja yang lengkap** untuk mencatat, mengelola, dan melaporkan seluruh transaksi keuangan gereja dengan transparansi dan akuntabilitas yang tinggi.

---

## 1. Persembahan Management ⭐⭐⭐⭐⭐

### 1.1 Tipe Persembahan
```
Master Data - Tipe Persembahan:
- Persembahan Umum (General Offering)
- Persepuluhan (Tithe)
- Persembahan Syukur (Thanksgiving Offering)
- Persembahan Misi (Mission Offering)
- Persembahan Pembangunan (Building Fund)
- Persembahan Diakonia (Diaconia Fund)
- Persembahan Anak-anak (Children's Offering)
- Persembahan Natal (Christmas Offering)
- Persembahan Paskah (Easter Offering)
- Persembahan Khusus (Special Offering)
```

### 1.2 Fitur Utama

#### A. Record Persembahan per Ibadah
```
Fields:
- tanggal (date)
- ibadah_type (dropdown: Sunday, Christmas, Easter, Thanksgiving, Special)
- service_time (time: 07:00, 09:00, 17:00, etc)
- persembahan_type (dropdown dari master data)
- amount (decimal)
- payment_method (dropdown: Cash, Transfer, Check, Digital Payment)
- jemaat_id (optional: jika ada kupon/Envelope)
- envelope_number (string)
- notes (text)
- recorded_by (user_id)
- created_at (timestamp)
- updated_at (timestamp)
```

#### B. Sistem Kupon/Envelope Persembahan
```
Features:
- Generate nomor kupon unik per jemaat
- Print kupon dengan barcode/QR code
- Scan kupon untuk quick input
- Track kupon yang sudah digunakan vs belum
- Monthly envelope distribution
- Historical persembahan per kupon
```

#### C. Persembahan Tanpa Nama (Anonymous)
```
Features:
- Record persembahan cash tanpa identitas
- Kategorisasi berdasarkan waktu ibadah
- Total summary per ibadah
- Cash counting & reconciliation
```

#### D. Quick Entry Interface
```
UI Features:
- Numeric keypad untuk fast input
- Auto-calculate totals
- Split persembahan ke multiple kategori
- Batch entry (multiple amounts sekaligus)
- Voice input (optional)
```

### 1.3 Features Lanjutan

#### Persepuluhan Tracking
```
Fields:
- jemaat_id (required)
- bulan (month)
- tahun (year)
- amount (decimal)
- payment_method
- date_received
- status (pending, paid, partial)
- notes
- receipt_number
```

#### Persembahan Recurring
```
Features:
- Auto-debit untuk persembahan bulanan
- Standing instruction
- Payment gateway integration (Midtrans, Stripe, etc)
- Auto-receipt generation
- Donor portal untuk manage recurring giving
```

#### Tax Receipt / Kwitansi
```
Features:
- Generate kwitansi otomatis
- Serial number kwitansi
- Print/Email/PDF kwitansi
- Annual tax receipt summary
- Customizable receipt template
```

---

## 2. Anggaran & Budget ⭐⭐⭐⭐

### 2.1 Struktur Budget

#### A. Budget per Departemen
```
Departemen yang punya budget:
- Umum (General)
- Pendidikan (Sunday School, Teens, Youth)
- Musik & Pujian
- Diakonia
- Misi
- Pembangunan (Building)
- Operasional (Operational)
- Gaji Staff (Salaries)
- Maintenance
- Event Khusus (Events)
```

#### B. Budget Categories
```
Master Data - Kategori Pengeluaran:
Code        | Category Name              | Type
-----------|----------------------------|-------------
GAJ         | Gaji & Honor               | Expense
LISTRIK     | Listrik & Air              | Expense
AIR         | Air Bersih                 | Expense
TELP        | Telepon & Internet         | Expense
SEWA        | Sewa Tempat                | Expense
PERAWATAN   | Perawatan Gedung           | Expense
ALAT        | Alat Tulis Kantor          | Expense
MUSIK       | Alat Musik & Sound System  | Expense
DIAKONIA    | Diakonia & Sosial          | Expense
MISI        | Misi & Evangelism          | Expense
PEMBANGUNAN | Pembangunan & Renovasi     | Expense
EVENT       | Event Khusus               | Expense
TRANSPORT   | Transportasi               | Expense
KONSUMSI    | Konsumsi                   | Expense
PUBLIKASI   | Publikasi & Media          | Expense
ASURANSI    | Asuransi                   | Expense
PAJAK       | Pajak                      | Expense
LAINNYA     | Lain-lain                  | Expense
```

### 2.2 Fitur Budget Management

#### A. Annual Budget Creation
```
Fields:
- tahun (year)
- departemen_id
- category_id
- budget_amount (decimal)
- justification (text)
- status (draft, proposed, approved, rejected)
- proposed_by (user_id)
- approved_by (user_id)
- approval_date (date)
- notes
```

#### B. Budget Approval Workflow
```
Workflow:
1. Draft → Dept Head review
2. Proposed → Finance review
3. Approved → Finalized
4. Rejected → Return with reason

Features:
- Email notification di setiap stage
- Comment & revision tracking
- Multi-level approval (jika perlu)
- Approval history
```

#### C. Budget vs Actual Tracking
```
Real-time Tracking:
- Planned budget (anggaran)
- Actual spent (realisasi)
- Variance (selisih)
- % Used (persentase terpakai)
- Remaining (sisa)

Alerts:
- Warning jika 80% terpakai
- Critical jika 90% terpakai
- Over-budget notification
```

#### D. Budget Revision
```
Features:
- Request budget increase
- Budget reallocation
- Revision approval
- Version history
- Reason tracking
```

---

## 3. Pengeluaran Management ⭐⭐⭐⭐

### 3.1 Data Structure

#### A. Expense Record
```
Fields:
- expense_id (PK)
- expense_number (auto: EXP-YYYYMM-XXXX)
- tanggal (date)
- category_id (FK)
- departemen_id (FK)
- amount (decimal)
- payment_method (dropdown: Cash, Transfer, Check)
- payee_name (string)
- payee_contact (string)
- description (text)
- justification (text)
- status (draft, pending, approved, paid, rejected)
- requested_by (user_id)
- approved_by (user_id)
- paid_by (user_id)
- approval_date (date)
- payment_date (date)
- receipt_attachment (file)
- supporting_docs (file multiple)
- notes (text)
- created_at (timestamp)
- updated_at (timestamp)
```

#### B. Bill / Invoice Tracking
```
Fields:
- bill_id (PK)
- bill_number (string)
- vendor_id (FK)
- invoice_date (date)
- due_date (date)
- amount (decimal)
- tax_amount (decimal)
- total_amount (decimal)
- status (received, reviewed, approved, paid, overdue)
- payment_term (string: Net 30, etc)
- notes
```

### 3.2 Workflow Pengeluaran

#### A. Expense Request Flow
```
1. CREATE → User buat expense request
2. REVIEW → Dept Head review
3. APPROVE → Finance approve
4. PAY → Finance process payment
5. RECORD → Payment recorded & reconciled

Features:
- Email notification setiap stage
- Auto-reminder untuk overdue approval
- Delegation (jika approver absent)
- Bulk approval untuk routine expenses
```

#### B. Payment Processing
```
Payment Methods:
- Cash (with petty cash management)
- Bank Transfer (multi-bank support)
- Check (check number tracking)
- Digital Payment (GoPay, OVO, etc)

Features:
- Payment batch processing
- Scheduled payments
- Payment confirmation upload
- Bank reconciliation
```

#### C. Petty Cash Management
```
Features:
- Petty cash fund setup
- Replenishment request
- Petty cash transactions
- Monthly reconciliation
- Custodian assignment
```

---

## 4. Laporan Keuangan ⭐⭐⭐⭐⭐

### 4.1 Standard Financial Reports

#### A. Cash Flow Statement (Laporan Arus Kas)
```
Period: Daily, Weekly, Monthly, Quarterly, Annual

Sections:
1. Cash Inflows:
   - Persembahan (breakdown per type)
   - Donasi khusus
   - Income lainnya
   - Total Inflows

2. Cash Outflows:
   - Pengeluaran operasional (breakdown per category)
   - Gaji & honor
   - Pengeluaran lainnya
   - Total Outflows

3. Net Cash Flow
4. Beginning Cash Balance
5. Ending Cash Balance

Features:
- Drill-down ke detail transaksi
- Compare dengan previous period
- Export Excel/PDF
- Email automation
```

#### B. Income Statement (Laporan Laba Rugi)
```
Format:

REVENUE (Pemasukan):
- Persembahan Umum: Rp XXX.XXX.XXX
- Persembahan Misi: Rp XXX.XXX.XXX
- Donasi Pembangunan: Rp XXX.XXX.XXX
- Lain-lain: Rp XXX.XXX.XXX
TOTAL REVENUE: Rp XXX.XXX.XXX

EXPENSES (Pengeluaran):
- Gaji & Honor: Rp XXX.XXX.XXX
- Operasional: Rp XXX.XXX.XXX
- Diakonia: Rp XXX.XXX.XXX
- Misi: Rp XXX.XXX.XXX
- Lain-lain: Rp XXX.XXX.XXX
TOTAL EXPENSES: Rp XXX.XXX.XXX

NET INCOME: Rp XXX.XXX.XXX

Features:
- Monthly vs YTD view
- Budget vs Actual comparison
- Variance analysis
- % of revenue breakdown
```

#### C. Balance Sheet (Neraca)
```
ASSETS (Aset):
- Current Assets:
  * Cash on Hand: Rp XXX.XXX.XXX
  * Bank Accounts: Rp XXX.XXX.XXX
  * Receivables: Rp XXX.XXX.XXX
  * Total Current Assets: Rp XXX.XXX.XXX

- Fixed Assets:
  * Tanah & Bangunan: Rp XXX.XXX.XXX
  * Peralatan: Rp XXX.XXX.XXX
  * Kendaraan: Rp XXX.XXX.XXX
  * Total Fixed Assets: Rp XXX.XXX.XXX

TOTAL ASSETS: Rp XXX.XXX.XXX

LIABILITIES (Kewajiban):
- Accounts Payable: Rp XXX.XXX.XXX
- Accrued Expenses: Rp XXX.XXX.XXX
TOTAL LIABILITIES: Rp XXX.XXX.XXX

NET ASSETS (Aset Bersih): Rp XXX.XXX.XXX

Features:
- Asset depreciation tracking
- Liability aging
- Net worth trend
```

### 4.2 Custom Reports

#### A. Departmental Reports
```
Features:
- Income & expense per departemen
- Budget utilization per departemen
- Department performance comparison
- Department-specific metrics
```

#### B. Donor Reports
```
Features:
- Total giving per donor
- Giving history
- Tax receipt summary
- Recognition levels (bronze, silver, gold)
- Annual giving statements
```

#### C. Trends & Analytics
```
Features:
- Month-over-month comparison
- Year-over-year comparison
- Giving trends (growth/decline)
- Seasonal patterns
- Forecasting
- Visual charts & graphs
```

---

## 5. Donasi Khusus ⭐⭐⭐⭐

### 5.1 Fund Management

#### A. Building Fund (Dana Pembangunan)
```
Fields:
- fund_id (PK)
- fund_name (string)
- fund_type (Building, Mission, Diaconia)
- target_amount (decimal)
- current_amount (decimal)
- start_date (date)
- end_date (date, nullable)
- description (text)
- status (active, completed, paused)

Features:
- Campaign progress tracking
- Donor wall/leaderboard
- Milestone celebrations
- Fund-specific reports
- Fund restrictions (if any)
```

#### B. Mission Fund
```
Features:
- Mission trip budgeting
- Missionary support tracking
- Fund allocation per missionary
- Mission expense tracking
- Impact reporting
```

#### C. Diaconia Fund
```
Features:
- Emergency fund management
- Case-based allocation
- Beneficiary tracking (privasi tinggi)
- Disbursement approval
- Impact measurement
```

### 5.2 Donor Management

#### A. Donor Database
```
Fields:
- donor_id (PK)
- member_id (FK, nullable - bisa non-member)
- name (string)
- contact_info (string)
- email (string)
- address (text)
- donor_type (individual, organization, foundation)
- donation_preference (general, mission, building, diakonia)
- status (active, inactive)

Features:
- Donor profile
- Giving history
- Communication preferences
- Acknowledgment tracking
```

#### B. Donation Campaigns
```
Features:
- Create campaign (building fund, mission trip, etc)
- Campaign goal & timeline
- Campaign page/landing
- Progress tracking
- Donor updates
- Thank you automation
```

#### C. Recurring Donations
```
Features:
- Monthly/quarterly/yearly giving
- Auto-payment setup
- Payment method management
- Donation modification/cancellation
- Recurring donor reports
```

---

## 6. Transparansi Keuangan ⭐⭐⭐⭐⭐

### 6.1 Public Financial Reports

#### A. Laporan Bulanan untuk Jemaat
```
Format Summary:
Pemasukan Bulan Ini:
- Persembahan Ibadah: Rp XX.XXX.XXX
- Donasi Khusus: Rp XX.XXX.XXX
Total: Rp XX.XXX.XXX

Pengeluaran Bulan Ini:
- Gaji & Operasional: Rp XX.XXX.XXX
- Diakonia & Misi: Rp XX.XXX.XXX
Total: Rp XX.XXX.XXX

Saldo: Rp XX.XXX.XXX

Features:
- Simplified format (non-technical)
- Auto-publish ke website/member portal
- Email distribution
- PDF generation
- Q&A section
```

#### B. Laporan Tahunan (Annual Report)
```
Sections:
1. Letter from Head of Church
2. Financial Highlights
3. Income Statement (Year)
4. Ministry Impact Stories
5. Appreciation to Donors
6. Budget Preview Next Year
7. Independent Auditor Report (jika ada)

Features:
- Professional design
- Print-ready
- Web version
- Presentation slides
- Video summary
```

### 6.2 Financial Dashboard

#### A. Real-time Metrics
```
Display:
- Total Income (Month/Year)
- Total Expense (Month/Year)
- Net Income
- Cash Balance
- Budget Utilization (%)
- Top Expense Categories
- Giving Trends (Chart)
```

#### B. Budget Health Indicators
```
Visual Indicators:
🟢 Healthy: < 70% budget used
🟡 Warning: 70-90% budget used
🔴 Critical: > 90% budget used

Features:
- Department breakdown
- Drill-down capability
- Date range selector
```

---

## 7. Database Schema (ERD Extension)

### 7.1 New Tables

```sql
-- Tipe Persembahan
CREATE TABLE offering_types (
    id INT PRIMARY KEY AUTO_INCREMENT,
    code VARCHAR(20) UNIQUE NOT NULL,
    name VARCHAR(100) NOT NULL,
    description TEXT,
    is_active BOOLEAN DEFAULT TRUE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    created_by VARCHAR(50),
    updated_by VARCHAR(50)
);

-- Persembahan
CREATE TABLE offerings (
    id INT PRIMARY KEY AUTO_INCREMENT,
    offering_number VARCHAR(50) UNIQUE NOT NULL,
    date DATE NOT NULL,
    service_type ENUM('Sunday', 'Christmas', 'Easter', 'Thanksgiving', 'Special') NOT NULL,
    service_time TIME,
    offering_type_id INT NOT NULL,
    amount DECIMAL(15,2) NOT NULL,
    payment_method ENUM('Cash', 'Transfer', 'Check', 'Digital') NOT NULL,
    member_id INT NULL,
    envelope_number VARCHAR(50),
    is_anonymous BOOLEAN DEFAULT FALSE,
    notes TEXT,
    recorded_by VARCHAR(50) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    created_by VARCHAR(50),
    updated_by VARCHAR(50),
    FOREIGN KEY (offering_type_id) REFERENCES offering_types(id),
    FOREIGN KEY (member_id) REFERENCES members(id)
);

-- Budget
CREATE TABLE budgets (
    id INT PRIMARY KEY AUTO_INCREMENT,
    year INT NOT NULL,
    department_id INT NOT NULL,
    category_id INT NOT NULL,
    budget_amount DECIMAL(15,2) NOT NULL,
    justification TEXT,
    status ENUM('draft', 'proposed', 'approved', 'rejected') DEFAULT 'draft',
    proposed_by VARCHAR(50),
    approved_by VARCHAR(50),
    approval_date DATE,
    notes TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    created_by VARCHAR(50),
    updated_by VARCHAR(50),
    UNIQUE KEY unique_budget (year, department_id, category_id)
);

-- Pengeluaran Categories
CREATE TABLE expense_categories (
    id INT PRIMARY KEY AUTO_INCREMENT,
    code VARCHAR(20) UNIQUE NOT NULL,
    name VARCHAR(100) NOT NULL,
    description TEXT,
    is_active BOOLEAN DEFAULT TRUE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    created_by VARCHAR(50),
    updated_by VARCHAR(50)
);

-- Pengeluaran
CREATE TABLE expenses (
    id INT PRIMARY KEY AUTO_INCREMENT,
    expense_number VARCHAR(50) UNIQUE NOT NULL,
    expense_date DATE NOT NULL,
    category_id INT NOT NULL,
    department_id INT NOT NULL,
    amount DECIMAL(15,2) NOT NULL,
    payment_method ENUM('Cash', 'Transfer', 'Check') NOT NULL,
    payee_name VARCHAR(200) NOT NULL,
    payee_contact VARCHAR(100),
    description TEXT NOT NULL,
    justification TEXT,
    status ENUM('draft', 'pending', 'approved', 'paid', 'rejected') DEFAULT 'draft',
    requested_by VARCHAR(50) NOT NULL,
    approved_by VARCHAR(50),
    approval_date DATE,
    paid_by VARCHAR(50),
    payment_date DATE,
    receipt_path VARCHAR(255),
    notes TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    created_by VARCHAR(50),
    updated_by VARCHAR(50),
    FOREIGN KEY (category_id) REFERENCES expense_categories(id),
    FOREIGN KEY (department_id) REFERENCES departments(id)
);

-- Donasi Khusus Funds
CREATE TABLE funds (
    id INT PRIMARY KEY AUTO_INCREMENT,
    fund_code VARCHAR(20) UNIQUE NOT NULL,
    fund_name VARCHAR(100) NOT NULL,
    fund_type ENUM('Building', 'Mission', 'Diaconia', 'Other') NOT NULL,
    target_amount DECIMAL(15,2),
    current_amount DECIMAL(15,2) DEFAULT 0,
    start_date DATE NOT NULL,
    end_date DATE NULL,
    description TEXT,
    status ENUM('active', 'completed', 'paused') DEFAULT 'active',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    created_by VARCHAR(50),
    updated_by VARCHAR(50)
);

-- Donasi
CREATE TABLE donations (
    id INT PRIMARY KEY AUTO_INCREMENT,
    donation_number VARCHAR(50) UNIQUE NOT NULL,
    donation_date DATE NOT NULL,
    fund_id INT NOT NULL,
    donor_id INT NULL,
    amount DECIMAL(15,2) NOT NULL,
    payment_method ENUM('Cash', 'Transfer', 'Check', 'Digital') NOT NULL,
    is_anonymous BOOLEAN DEFAULT FALSE,
    notes TEXT,
    recorded_by VARCHAR(50) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    created_by VARCHAR(50),
    updated_by VARCHAR(50),
    FOREIGN KEY (fund_id) REFERENCES funds(id),
    FOREIGN KEY (donor_id) REFERENCES donors(id)
);

-- Donors
CREATE TABLE donors (
    id INT PRIMARY KEY AUTO_INCREMENT,
    donor_number VARCHAR(20) UNIQUE NOT NULL,
    member_id INT NULL,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100),
    phone VARCHAR(20),
    address TEXT,
    donor_type ENUM('individual', 'organization', 'foundation') DEFAULT 'individual',
    donation_preference VARCHAR(50),
    is_active BOOLEAN DEFAULT TRUE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    created_by VARCHAR(50),
    updated_by VARCHAR(50),
    FOREIGN KEY (member_id) REFERENCES members(id)
);

-- Rekening Bank
CREATE TABLE bank_accounts (
    id INT PRIMARY KEY AUTO_INCREMENT,
    account_name VARCHAR(100) NOT NULL,
    bank_name VARCHAR(50) NOT NULL,
    account_number VARCHAR(50) UNIQUE NOT NULL,
    account_type ENUM('Checking', 'Savings', 'Credit') NOT NULL,
    branch VARCHAR(100),
    currency VARCHAR(3) DEFAULT 'IDR',
    balance DECIMAL(15,2) DEFAULT 0,
    is_active BOOLEAN DEFAULT TRUE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    created_by VARCHAR(50),
    updated_by VARCHAR(50)
);
```

---

## 8. User Roles & Permissions

### 8.1 Role Definitions

```
Finance Admin:
- Full access to all financial features
- Approve/reject expenses
- Manage budget
- Generate all reports
- Configure system settings

Finance Staff:
- Record offerings & expenses
- View basic reports
- Process payments
- Data entry

Department Head:
- View department budget
- Create expense requests
- View department reports
- Cannot see other departments

Reviewer:
- Review expense requests
- Approve/reject within limit
- View assigned reports

Auditor:
- Read-only access
- View all financial data
- Generate audit reports
- Cannot modify data

Church Board (Majelis):
- View summary reports
- Approve major budgets
- Financial dashboard
- Monthly reports

Congregation (Jemaat):
- Public reports only
- No access to detailed data
```

### 8.2 Permission Matrix

```
Feature                   | Finance Admin | Finance Staff | Dept Head | Reviewer | Auditor | Board | Jemaat
--------------------------|---------------|---------------|-----------|----------|---------|-------|--------
Record Offering           | ✓             | ✓             | ✓*        | ✗        | ✗       | ✗     | ✗
Record Expense            | ✓             | ✓             | ✓         | ✗        | ✗       | ✗     | ✗
Approve Expense           | ✓             | ✗             | ✗         | ✓        | ✗       | ✓     | ✗
Manage Budget             | ✓             | ✗             | View Only | ✗        | ✗       | ✓     | ✗
View All Reports          | ✓             | Basic         | Dept Only | Basic    | ✓       | ✓     | Public
Export Data               | ✓             | ✓             | ✓         | ✓        | ✓       | ✓     | ✗
Configure System          | ✓             | ✗             | ✗         | ✗        | ✗       | ✗     | ✗
```

*Hanya untuk department-nya sendiri

---

## 9. Integration Points

### 9.1 External Systems

```
Payment Gateway:
- Midtrans (Indonesia)
- Stripe (International)
- PayPal
- GoPay, OVO, Dana (e-wallets)

Banking API:
- Bank Statement Import
- Auto-reconciliation
- Payment confirmation

Accounting Software:
- Export to Jurnal, Accurate, QuickBooks
- Sync invoices
- Tax reporting
```

### 9.2 Internal Modules

```
Member Module:
- Donor profile linked to member
- Persembahan history in member profile
- Tax receipt per member

Document Module:
- Receipt storage
- Invoice storage
- Financial report archive

Notification Module:
- Budget alerts
- Approval notifications
- Payment reminders

Dashboard Module:
- Financial widgets
- Giving trends
- Budget health indicators
```

---

## 10. Development Priority & Phases

### Phase 1: Foundation (Week 1-2)
- [ ] Database setup (tables, relationships)
- [ ] Basic offering entry
- [ ] Basic expense entry
- [ ] Simple categories management
- [ ] User roles & permissions

### Phase 2: Core Features (Week 3-4)
- [ ] Offering management (all types)
- [ ] Expense management with workflow
- [ ] Bank account management
- [ ] Basic reports (cash flow)
- [ ] Envelope/kupon system

### Phase 3: Budget & Planning (Week 5-6)
- [ ] Budget creation & approval
- [ ] Budget vs actual tracking
- [ ] Departmental budgets
- [ ] Budget revision workflow
- [ ] Budget reports

### Phase 4: Advanced Features (Week 7-8)
- [ ] Donor management
- [ ] Fund management (building, mission, diakonia)
- [ ] Recurring donations
- [ ] Tax receipts
- [ ] Advanced reports (Income Statement, Balance Sheet)

### Phase 5: Transparency & Reporting (Week 9-10)
- [ ] Public financial reports
- [ ] Annual report generator
- [ ] Financial dashboard
- [ ] Analytics & trends
- [ ] Export & automation

### Phase 6: Integration & Polish (Week 11-12)
- [ ] Payment gateway integration
- [ ] Bank integration (if available)
- [ ] Email notifications
- [ ] SMS notifications (for approvals)
- [ ] UI/UX improvements
- [ ] Testing & bug fixes

---

## 11. Key Metrics & Success Criteria

### 11.1 User Adoption
```
Success Metrics:
- 95% of offerings recorded within 24 hours
- 90% of expenses follow proper workflow
- Zero data entry errors (validation)
- Monthly reports generated on time
```

### 11.2 Financial Health
```
Tracking Metrics:
- Budget utilization (keep under 90%)
- Cash flow positivity
- Emergency fund adequacy (3-6 months expenses)
- Giving trends (growth year-over-year)
```

### 11.3 Transparency
```
Success Indicators:
- Monthly reports published consistently
- Jemaat satisfaction with financial transparency
- Auditor approval (clean audit reports)
- Zero financial discrepancies
```

---

## 12. Compliance & Best Practices

### 12.1 Accounting Standards
```
Following:
- Indonesian Accounting Standards (PSAK)
- Non-profit accounting principles
- Double-entry bookkeeping (optional, for advanced use)
- Accrual vs cash basis (configurable)
```

### 12.2 Tax Compliance
```
Requirements:
- Tax receipt issuance
- Donor tax statements
- Withholding tax (if applicable)
- Annual tax reporting
```

### 12.3 Internal Controls
```
Best Practices:
- Segregation of duties (recorder ≠ approver)
- Approval limits (amount-based)
- Mandatory receipts for expenses
- Regular bank reconciliation
- Annual external audit
- Audit trail for all transactions
```

---

## 13. Training & Documentation

### 13.1 User Guides Needed
```
- Finance Admin Manual
- Finance Staff Manual
- Department Head Manual
- Church Board Financial Dashboard Guide
- FAQ for common issues
```

### 13.2 Training Schedule
```
Pre-launch:
- Finance team: 2 days intensive training
- Department heads: 1 day budget training
- Church board: 1/2 day dashboard training

Post-launch:
- Refresher training monthly
- New features training as released
```

---

## Summary

**Total Features:** 50+ features across 7 main components
**Development Time:** 12 weeks (3 months)
**Team Size Needed:**
- 1 Senior Backend Developer
- 1 Frontend Developer
- 1 UI/UX Designer
- 1 QA Tester
- 1 Finance/Accounting SME (Subject Matter Expert)

**Critical Success Factors:**
1. Input from finance team/accountant
2. Proper user training
3. Clean data migration (if existing system)
4. Ongoing support & maintenance
5. Regular feedback from users
6. Compliance with regulations
7. Strong security & access controls

---

## Questions for Stakeholders

Before implementation, clarify:
1. Apakah gereja sudah punya sistem keuangan sebelumnya? Apa itu?
2. Berapa banyak transaksi per bulan (offering & expenses)?
3. Apakah perlu integrasi dengan payment gateway?
4. Apakah perlu integrasi dengan accounting software?
5. Berapa banyak user untuk setiap role?
6. Apa budget constraint untuk development?
7. Timeline yang diharapkan?
8. Apa pain points utama dengan sistem sekarang?
