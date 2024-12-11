## Entity-Relationship Diagram (ERD) Solution

### **ER Diagram**


### **Entities and Attributes**

#### **1. Resource**
- **Primary Key**: `Resource_ID` (Integer)
- **Attributes**:
  - `Title` (String)
  - `Author` (String)
  - `Publisher` (String)
  - `Category` (String)
  - `ISBN` (String)

#### **2. Member**
- **Primary Key**: `Member_ID` (Integer)
- **Attributes**:
  - `Name` (String)
  - `Email` (String)
  - `Phone` (String)
  - `Address` (String): Composite Attribute of street, city, state, zip
  - `Member_Type` (Enum: 'Student', 'Faculty', 'Staff')
  - `Status` (Enum: 'Active', 'Inactive')

#### **3. Loan**
- **Primary Key**: `Loan_ID` (Integer)
- **Foreign Keys**: `Member_ID` (References Member), `Resource_ID` (References Resource)
- **Attributes**:
  - `Loan_Date` (Date)
  - `Due_Date` (Date)
  - `Return_Date` (Date)
  - `Fine` (Decimal)

#### **4. Reservation**
- **Primary Key**: `Reservation_ID` (Integer)
- **Foreign Keys**: `Member_ID` (References Member), `Resource_ID` (References Resource)
- **Attributes**:
  - `Reservation_Date` (Date)
  - `Notification_Sent` (Boolean, Default: False)

#### **5. Inventory**
- **Primary Key**: `Inventory_ID` (Integer)
- **Foreign Key**: `Resource_ID` (References Resource)
- **Attributes**:
  - `Total_Stock` (Integer)
  - `Available_Stock` (Integer)
  - `Missing_Items` (Integer)
  - `Damaged_Items` (Integer)

---

### **Relationships and Cardinality**

#### **1. Resource ↔ Loan**
- **Type**: One-to-Many
- **Reason**: A resource can be loaned multiple times, but each loan refers to one resource.
- **Foreign Key**: `Resource_ID` in Loan.

#### **2. Member ↔ Loan**
- **Type**: One-to-Many
- **Reason**: A member can have multiple loans, but each loan belongs to one member.
- **Foreign Key**: `Member_ID` in Loan.

#### **3. Resource ↔ Reservation**
- **Type**: One-to-Many
- **Reason**: A resource can have multiple reservations, but each reservation refers to one resource.
- **Foreign Key**: `Resource_ID` in Reservation.

#### **4. Member ↔ Reservation**
- **Type**: One-to-Many
- **Reason**: A member can reserve multiple resources, but each reservation belongs to one member.
- **Foreign Key**: `Member_ID` in Reservation.

#### **5. Resource ↔ Inventory**
- **Type**: One-to-One
- **Reason**: Each resource has exactly one inventory entry.
- **Foreign Key**: `Resource_ID` in Inventory.

---

### Tools Used
- **ERD Creation**: [draw.io](https://app.diagrams.net/)

### Developer
<a href="https://github.com/QwertyFusion">[@QwertyFusion]</a> - Rishi Banerjee