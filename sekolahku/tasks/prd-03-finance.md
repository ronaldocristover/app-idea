# PRD 03: Finance Management Module

## Introduction

The Finance Management Module handles all financial aspects of school operations, focusing primarily on School Development Fee (SPP - Sumbangan Pembinaan Pendidikan) management. This module provides comprehensive tools for configuring fee structures, managing student billing, processing payments, tracking arrears, and generating financial reports.

This module is essential for ensuring the financial sustainability of the school while providing transparency to parents about their financial obligations and payment history. It integrates with the Core School Management module to access student data and with the Communication module to send payment notifications.

## Goals

1. **Financial Transparency**: Provide clear, accurate billing information to parents
2. **Operational Efficiency**: Streamline fee collection and payment processing
3. **Financial Control**: Enable proper tracking and reconciliation of all financial transactions
4. **Automated Billing**: Reduce manual work through automated billing processes
5. **Arrears Management**: Effectively track and manage late payments
6. **Comprehensive Reporting**: Generate detailed financial reports for administration and auditing
7. **Payment Flexibility**: Support multiple payment methods and schedules

## User Stories

### Story 1: SPP Configuration

**Description**: As a school administrator, I want to configure SPP fee structures so that billing amounts can be properly calculated based on various student categories and payment schedules.

**Acceptance Criteria**:
- Administrator can create fee structures with:
  - Fee type name (e.g., "SPP Regular", "SPP New Student")
  - Description
  - Applicable academic year
  - Grade level applicability
  - Base amount per month
  - Payment periods (monthly, quarterly, semesterly, annually)
  - Discount categories (siblings, early payment, etc.)
  - Late payment penalties
  - Effective date range
- System supports multiple fee structures:
  - Different amounts per grade level
  - Special rates for new students vs. returning students
  - Scholarship categories
- Administrator can configure discounts:
  - Sibling discount (2nd child, 3rd child, etc.)
  - Early payment discount
  - Full payment discount
  - Staff/teacher children discount
  - Custom scholarships
- Administrator can configure penalties:
  - Late payment fee (fixed amount or percentage)
  - Maximum penalty cap
  - Grace period before penalty applies
- Fee structures can be copied to new academic years
- System maintains fee structure history
- Fee changes are logged with effective dates
- Administrator can preview fee calculations before applying

### Story 2: SPP Billing (Tagihan SPP)

**Description**: As a school administrator, I want to generate and manage SPP bills so that parents know exactly what they owe and when payments are due.

**Acceptance Criteria**:
- System can generate bills with:
  - Student information
  - Billing period (month/semester/year)
  - Fee components breakdown
  - Applied discounts
  - Applied penalties (if any)
  - Total amount due
  - Due date
  - Payment status
- Administrator can generate bills:
  - For individual students
  - For entire grade level
  - For all students in bulk
  - On recurring schedule (auto-generation)
- Bill generation includes:
  - Base SPP amount
  - Additional fees (lab, library, extracurricular, etc.)
  - Applied discounts (with reasons)
  - Previous balance carried forward
  - Late fees (for overdue payments)
- System assigns sequential bill/invoice numbers
- Bills are automatically saved to student records
- Administrator can review generated bills before sending
- Administrator can regenerate bills if corrections needed
- System prevents duplicate bill generation for same period
- Bill status tracking:
  - Draft
  - Sent/Notified
  - Partially Paid
  - Fully Paid
  - Overdue
  - Cancelled
- Bills can be exported to PDF for printing/emailing

### Story 3: SPP Payment Processing (Pembayaran SPP)

**Description**: As a finance staff, I want to record and process SPP payments so that accurate financial records are maintained and student accounts are updated.

**Acceptance Criteria**:
- Finance staff can record payments with:
  - Student selection
  - Bill/invoice selection
  - Payment amount
  - Payment date
  - Payment method (cash, transfer, credit card, e-wallet, check)
  - Bank/payment channel details
  - Reference number (for transfers)
  - Receipt/proof of payment upload
  - Notes
- System supports multiple payment methods:
  - Cash payments with receipt printing
  - Bank transfers with reconciliation
  - Credit/debit card payments
  - E-wallet payments (GoPay, OVO, Dana, etc.)
  - Check payments with clearing status
- System automatically:
  - Updates bill payment status
  - Calculates remaining balance
  - Applies payments to oldest bills first (configurable)
  - Generates receipt number
  - Updates payment history
- Finance staff can process:
  - Full payment of single bill
  - Partial payment of bill
  - Payment across multiple bills
- System validates payment amounts
- System prevents overpayment (or puts excess in credit balance)
- Receipt is automatically generated:
  - Printable format
  - PDF export
  - Email to parent
- Payment can be reversed/cancelled with:
  - Reason for cancellation
  - Admin approval
  - Automatic bill status update
- System tracks payment status:
  - Pending confirmation
  - Confirmed
  - Cancelled
  - Reversed
- Payment history shows:
  - All transactions for student
  - Running balance
  - Payment method breakdown

### Story 4: SPP Arrears Report (Laporan Tunggakan SPP)

**Description**: As a school administrator, I want to view and manage SPP arrears so that I can identify late payers and take appropriate action to collect outstanding payments.

**Acceptance Criteria**:
- System generates arrears reports with:
  - Student list with outstanding balances
  - Arrears amount by student
  - Number of months overdue
  - Last payment date
  - Contact information
- Report filtering and sorting:
  - By grade level
  - By class
  - By arrears amount range
  - By months overdue
  - By payment status
- Report includes summary statistics:
  - Total number of students with arrears
  - Total arrears amount
  - Average arrears per student
  - Percentage of students with arrears
- System can identify:
  - Students with 1 month overdue
  - Students with 2-3 months overdue
  - Students with 3+ months overdue (critical)
- Administrator can:
  - Export arrears report to Excel/PDF
  - Generate reminder letters automatically
  - Add notes to student accounts
  - Flag critical cases for follow-up
- System tracks arrears history:
  - Payment patterns
  - Chronic late payers
  - Improvement over time
- Arrears data can be shared with:
  - Academic department (for exam eligibility)
  - Communication module (for sending reminders)
- Report can be scheduled for automatic generation
- Historical arrears reports are archived

### Story 5: Financial Reports (Laporan Keuangan)

**Description**: As a school administrator and finance manager, I want comprehensive financial reports so that I can monitor the school's financial health and make informed decisions.

**Acceptance Criteria**:
- System can generate various financial reports:
  1. **Revenue Reports**:
     - Daily/weekly/monthly/annual revenue
     - Revenue by payment method
     - Revenue by grade level
     - Revenue trends over time
     - Comparison with previous periods
  2. **Collection Reports**:
     - Collection rate by period
     - Collection effectiveness
     - Outstanding receivables aging
     - Cash flow projections
  3. **Student Financial Reports**:
     - Payment history per student
     - Transaction details
     - Outstanding balance summary
     - Payment status distribution
  4. **Administrative Reports**:
     - Total students billed vs. paid
     - Discounts and scholarships given
     - Late fees collected
     - Write-offs and adjustments
- Reports feature:
  - Date range selection
  - Multiple filter options
  - Drill-down capability
  - Export to Excel, PDF, CSV
  - Print-friendly format
  - Comparison with budget (if budgeting module added)
- Report generation:
  - On-demand
  - Scheduled (email delivery)
  - Dashboard summary with key metrics
- Report security:
  - Role-based access
  - Audit trail of report access
  - Watermark on sensitive reports
- Custom reports:
  - Save frequently used report configurations
  - Create custom report templates
  - Schedule regular report delivery

### Story 6: Payment Integration

**Description**: As a parent, I want to pay SPP online through various digital payment channels so that I don't have to come to school to make payments.

**Acceptance Criteria**:
- System supports online payment gateways:
  - Bank transfer (VA - Virtual Account)
  - Credit/debit card
  - E-wallets (GoPay, OVO, Dana, LinkAja, etc.)
  - QRIS payments
  - Retail outlets (Alfamart, Indomaret)
- Payment process:
  - Parent selects bill to pay
  - System generates payment instructions
  - Parent completes payment at chosen channel
  - System receives payment confirmation
  - Student account is automatically updated
  - Receipt is sent via email/SMS
- System handles:
  - Payment expiry time
  - Payment status checking
  - Failed payment retry
  - Partial payment handling
- Integration includes:
  - Midtrans, Xendit, or similar payment gateway
  - Bank APIs for VA confirmation
  - Callback/webhook for payment notifications
- System reconciliation:
  - Match payments to invoices automatically
  - Flag unmatched payments for manual review
  - Daily reconciliation report
- Payment notifications:
  - Confirmation to parent
  - Alert to finance team
  - Update to student account
- Transaction fees:
  - Configurable per payment method
  - Can be absorbed by school or passed to parent
  - Tracked separately from SPP amount

### Story 7: Financial Dashboard

**Description**: As a school administrator, I want a financial dashboard so that I can quickly see the current financial status and key metrics at a glance.

**Acceptance Criteria**:
- Dashboard displays key metrics:
  - Total revenue this month/term/year
  - Collection rate percentage
  - Total outstanding arrears
  - Number of students with arrears
  - Average collection time
  - Payment method breakdown
- Visual elements:
  - Revenue trend charts (line/bar)
  - Collection rate gauge/meter
  - Payment method pie chart
  - Arrears by grade level bar chart
  - Top 10 overdue list
- Dashboard features:
  - Date range selector
  - Comparison with previous period
  - Drill-down to detailed reports
  - Real-time data updates
  - Export dashboard as PDF
- Alerts and notifications:
  - Low collection rate warning
  - High arrears alert
  - Revenue target progress
- Customizable widgets:
  - User can arrange dashboard layout
  - Select which metrics to display
  - Set threshold alerts

## Functional Requirements

### 1. SPP Configuration
- FR-FIN-001: Create, read, update fee structures
- FR-FIN-002: Define fee amounts by grade level
- FR-FIN-003: Configure discount categories and rules
- FR-FIN-004: Configure late payment penalties
- FR-FIN-005: Copy fee structures to new academic years
- FR-FIN-006: Maintain fee structure version history

### 2. Billing
- FR-FIN-007: Generate bills for individual students
- FR-FIN-008: Generate bills in bulk
- FR-FIN-009: Schedule automatic bill generation
- FR-FIN-010: Include multiple fee components in bills
- FR-FIN-011: Apply discounts automatically
- FR-FIN-012: Apply penalties for late payment
- FR-FIN-013: Assign sequential invoice numbers
- FR-FIN-014: Track bill status throughout lifecycle
- FR-FIN-015: Export bills to PDF

### 3. Payment Processing
- FR-FIN-016: Record payments with full details
- FR-FIN-017: Support multiple payment methods
- FR-FIN-018: Update bill status automatically
- FR-FIN-019: Calculate and apply to correct bills
- FR-FIN-020: Generate payment receipts
- FR-FIN-021: Handle partial payments
- FR-FIN-022: Handle cross-bill payments
- FR-FIN-023: Process payment reversals with approval
- FR-FIN-024: Upload proof of payment
- FR-FIN-025: Email receipts to parents

### 4. Payment Gateway Integration
- FR-FIN-026: Integrate with payment gateway APIs
- FR-FIN-027: Generate payment instructions
- FR-FIN-028: Handle payment callbacks/webhooks
- FR-FIN-029: Reconcile automatic payments
- FR-FIN-030: Handle expired/failed payments
- FR-FIN-031: Track transaction fees separately
- FR-FIN-032: Send payment confirmations

### 5. Arrears Management
- FR-FIN-033: Identify students with outstanding balances
- FR-FIN-034: Categorize arrears by severity
- FR-FIN-035: Generate arrears reports
- FR-FIN-036: Track payment patterns
- FR-FIN-037: Flag chronic late payers
- FR-FIN-038: Schedule payment reminders
- FR-FIN-039: Export arrears lists

### 6. Financial Reporting
- FR-FIN-040: Generate revenue reports
- FR-FIN-041: Generate collection reports
- FR-FIN-042: Generate student financial reports
- FR-FIN-043: Generate aging receivables reports
- FR-FIN-044: Support multiple date ranges
- FR-FIN-045: Export reports to multiple formats
- FR-FIN-046: Schedule automatic report generation
- FR-FIN-047: Create custom report templates
- FR-FIN-048: Compare with budgets/forecasts

### 7. Dashboard
- FR-FIN-049: Display key financial metrics
- FR-FIN-050: Show visual charts and graphs
- FR-FIN-051: Provide drill-down capability
- FR-FIN-052: Support date range filtering
- FR-FIN-053: Enable customizable widgets
- FR-FIN-054: Set threshold-based alerts
- FR-FIN-055: Export dashboard as PDF

### 8. General
- FR-FIN-056: Audit all financial transactions
- FR-FIN-057: Implement role-based access control
- FR-FIN-058: Integrate with notification system
- FR-FIN-059: Provide data export functionality
- FR-FIN-060: Support multi-currency (if applicable)
- FR-FIN-061: Backup financial data regularly

## Non-Goals

The following features are explicitly **out of scope** for this module:

- **Full Accounting System**: General ledger, balance sheet, income statement are not included (can integrate with accounting software)
- **Payroll Management**: Teacher/staff salary payments are not included
- **Expense Management**: Non-SPP expense tracking and management are not included
- **Budgeting**: Revenue and expense budgeting tools are not included
- **Tax Management**: VAT/tax calculation and reporting are not included
- **Multi-Currency**: Complex multi-currency support is not included
- **Inventory**: Physical asset and inventory management are not included
- **Procurement**: Purchase order and vendor management are not included
- **Petty Cash**: Small cash expense tracking is not included
- **Financial Auditing Tools**: Advanced audit trails and compliance tools are not included

## Technical Considerations

### Architecture
- **Microservices**: Finance module could be isolated for security and scalability
- **Database**: Use ACID-compliant database for financial transactions
- **API**: Provide secure APIs for payment gateway integrations

### Security
- **Data Encryption**: Encrypt all financial data at rest and in transit
- **Access Control**: Strict role-based access with two-factor authentication
- **Audit Trail**: Comprehensive logging of all financial activities
- **Payment Security**: PCI DSS compliance for card payments
- **Fraud Detection**: Implement checks for unusual payment patterns
- **Backup**: Encrypted backups with secure retention policy

### Performance
- **High Availability**: 99.9% uptime during peak payment periods
- **Scalability**: Handle payment spikes during registration and monthly deadlines
- **Response Time**: Payment confirmation within 5 seconds
- **Batch Processing**: Efficient bulk billing generation
- **Database Optimization**: Index frequently queried financial data

### Integration
- **Payment Gateway**: Integration with major Indonesian payment providers (Midtrans, Xendit, etc.)
- **Bank APIs**: Direct integration with major banks for VA confirmation
- **SMS Gateway**: For payment confirmations and reminders
- **Email Service**: For sending bills and receipts
- **Accounting Software**: Integration with Jurnal, Accurate, etc.

### User Experience
- **Mobile-Friendly**: Parents can view and pay via mobile
- **Payment Flow**: Simple, intuitive payment process
- **Receipt Design**: Professional, branded receipts
- **Error Handling**: Clear error messages and recovery options
- **Offline Support**: Finance staff can work offline and sync later

### Compliance
- **Data Privacy**: Compliance with Indonesian data protection laws
- **Financial Regulations**: Alignment with education finance regulations
- **Tax Compliance**: Support for tax calculation and reporting
- **Audit Requirements**: Maintain records for required retention period

## Success Metrics

### Operational Metrics
- **Billing Efficiency**: 100% of bills generated automatically on schedule
- **Payment Processing**: 95% of payments processed within 1 business day
- **Collection Rate**: Target collection rate of 95% by month 3 of implementation
- **Online Payment Adoption**: 60% of parents using online payment within 6 months
- **Reconciliation Accuracy**: 99% of payments automatically matched to invoices

### User Satisfaction
- **Parent Satisfaction**: 4.0+ out of 5.0 for ease of payment
- **Admin Efficiency**: 50% reduction in time spent on billing and collection
- **Support Tickets**: Less than 2 tickets per 100 users per month
- **Payment Success Rate**: 98% successful payment completion rate

### Financial Metrics
- **Arrears Reduction**: 20% reduction in outstanding arrears within 6 months
- **Late Payment Reduction**: 30% reduction in late payments with reminders
- **Revenue Visibility**: Real-time visibility into financial status
- **Cost Savings**: 40% reduction in administrative costs related to billing

### System Performance
- **Uptime**: 99.9% availability during business hours
- **Response Time**: Page loads within 2 seconds
- **Payment Confirmation**: 90% of online payments confirmed within 2 minutes
- **Report Generation**: Financial reports generated within 30 seconds

## Open Questions

1. **Payment Gateway Selection**: Which payment gateways should be integrated? Consider coverage, fees, and technical requirements.

2. **Fee Structure Complexity**: How complex should the fee structure be? Should we support unlimited customization or keep it simple?

3. **Late Payment Policy**: What is the school's policy on late payments? Is there a maximum penalty cap?

4. **Scholarship Management**: How are scholarships managed? Is there an approval workflow needed?

5. **Arrears Actions**: What actions should be taken for chronic late payers? Hold exam results? Withhold report cards?

6. **Accounting Integration**: Should the system integrate with external accounting software? Which platforms?

7. **Refund Policy**: Are refunds ever given? If so, what's the process and approval workflow?

8. **Multi-School Finance**: If multiple schools are supported, should finances be completely separate or consolidated?

9. **Currency Handling**: Is multi-currency support needed for international students?

10. **Payment Plans**: Should the system support custom payment plans for families with financial difficulties?

11. **Bill Delivery**: Should bills be sent via email, SMS, or both? Is there additional cost?

12. **Receipt Customization**: How customizable should receipts be? Can schools add their own branding?

13. **Financial Year**: Does the financial year align with academic year, or follow calendar year?

14. **Fee Changes Mid-Year**: Can fees be changed during an academic year? How are existing bills affected?

15. **Payment Reconciliation**: How much manual intervention is expected in payment reconciliation?

16. **Data Retention**: How long must financial records be retained? What are the compliance requirements?

17. **Audit Trail**: What level of audit trail detail is required? Who should have access to audit logs?

18. **Transaction Limits**: Are there limits on transaction amounts? Who can approve large payments?

19. **Offline Payment Recording**: If internet is unavailable, how should finance staff record payments?

20. **Parent Access**: Should parents be able to view their complete payment history and download receipts?
