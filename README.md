# Case Study: Library Management System

## Problem Statement

The XYZ University Library has grown considerably over the years and needs an efficient system to manage its resources, users, and various library activities. The library is responsible for managing books, journals, magazines, and other materials. Additionally, it must track the members who borrow resources, the transaction of book loans, returns, and reservations.

The current system is manual, with records stored on paper, and this has become increasingly difficult to manage as the number of materials and members has expanded. The library requires a digital solution to automate and streamline the process of book loans, returns, member management, and inventory control.

The new Library Management System (LMS) should have the following key features:

1. **Resource Management**: The system should track books, journals, magazines, and other resources. Each resource will have a unique identifier, title, author, publisher, and category.
  
2. **Member Management**: The system should manage student, faculty, and staff members. Each member will have a unique identifier, personal details, and their status (active or inactive).

3. **Loan Management**: The system should handle the borrowing of books and resources. Each loan transaction should be recorded, including the due date and any fines for late returns.

4. **Reservation System**: Members should be able to reserve resources if they are currently on loan. When the resource is returned, the system should notify the next member in line.

5. **Inventory Control**: The system should track the quantity of each resource, including the current stock and any missing or damaged items.

6. **Search and Reporting**: The system should allow the librarian and members to search for resources by title, author, category, or keyword. Reports should be generated on loan histories, overdue books, and resources with the highest demand.

---

## Task for Interns

As part of this case study, you are tasked with designing a database schema for the Library Management System. Your goal is to:

1. Identify the **entities** involved in the system.
2. Determine the **relationships** between these entities.
3. List the **attributes** of each entity.
4. Develop a basic **Entity-Relationship Diagram (ERD)**.

---

## Entity-Relationship Diagram (ERD) Solution

### **ER Diagram**
![Entity Relationship Diagram Coloured](./ER_diagram/ER_Diagram_Coloured.png)

---

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
