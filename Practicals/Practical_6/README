
# Domain Model 

This document outlines the domain objects and their relationships within a banking system.

---

## Bounded Contexts

- **Customer Management Context**
- **Account Management Context**
- **Card Management Context**
- **Branch Management Context**

---

## Aggregates and Entities

Each aggregate root is the entry point to consistency boundaries in a context.

### A. Customer (Aggregate Root – Customer Management Context)
- **Attributes:**
  - `ID: CustomerID`
  - `Name: String`
  - `accountNumbers: List<AccountNumber>`
- **Associations:**
  - 1 Customer ↔ 1 Address
  - 1 Customer ↔ 1 EmploymentDetails
  - 1 Customer ↔ 0..* AccountNumber
  - 1 Customer ↔ 0..1 ATMCard

### B. Account (Aggregate Root – Account Management Context)
- **Attributes:**
  - `accountNumber: AccountNumber`
  - `accountType: String`
  - `holderID: CustomerID`
  - `jointHolderID: CustomerID`
  - `branchName: BranchName`
  - `balance: Balance`
- **Associations:**
  - 1 Account ↔ 1 Balance
  - 0..1 SavingAccount ↔ 0..* CurrentAccount
  - 1 Account ↔ 1 Branch (via `branchName`)

### C. ATMCARD (Entity – Card Management Context)
- **Attributes:**
  - `ID`
  - `customerID`
  - `dateOfIssue: Date`
- **Associations:**
  - Identified by ATMCardID
  - 0..1 ATMCard ↔ 1 Customer

### D. Branch (Aggregate Root – Branch Management Context)
- **Attributes:**
  - `branchName: BranchName`
- **Associations:**
  - 1 Branch ↔ 1 BranchAddress

---

## Value Objects

Value objects are immutable and identified only by their attributes.

### A. Address (Customer Management Context)
- `Street: String`
- `City: String`
- `State: String`
- `PostalCode: String`

### B. EmploymentDetails (Customer Management Context)
- `CompanyName: String`
- `TelephoneNo: String`
- `AnnualSalaryRange: String`
- `Occupation: String`
- `Designation: String`

### C. CustomerID (Customer Management Context)
- `id: String`

### D. AccountNumber (Customer Management Context / Account Management Context)
- `number: String`

### E. ATMCardID (Card Management Context)
- `id: String`

### F. BranchName (Account Management Context)
- `name: String`

### G. Balance (Account Management Context)
- `amount: Decimal`
- `currency: String`

### H. BranchAddress (Branch Management Context)
- `Street: String`
- `City: String`
- `State: String`
- `PostalCode: String`

---

## Relationships / Associations 

### Between Contexts:
- **Customer Management Context ↔ Card Management Context**
  - A Customer can have 0..1 ATMCard.

- **Customer Management Context ↔ Account Management Context**
  - A Customer can hold 0..* Accounts (identified by AccountNumber).

- **Account Management Context ↔ Branch Management Context**
  - An Account belongs to a Branch (via BranchName).

### Internal Associations:
- **Customer → Address** (1:1)
- **Customer → EmploymentDetails** (1:1)
- **Account → Balance** (1:1)
- **Branch → BranchAddress** (1:1)
- **SavingAccount ↔ CurrentAccount** (0..1 : 0..*)

---

