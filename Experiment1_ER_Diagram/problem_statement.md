# ER Diagram Workshop – Submission Template

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Scenario A: City Fitness Club Management

**Business Context:**  
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

**Requirements:**  
- Members register with name, membership type, and start date.  
- Each member can join multiple programs (Yoga, Zumba, Weight Training).  
- Trainers assigned to programs; a program may have multiple trainers.  
- Members may book personal training sessions with trainers.  
- Attendance recorded for each session.  
- Payments tracked for memberships and sessions.

### ER Diagram:
<img width="752" height="422" alt="image" src="https://github.com/user-attachments/assets/76df9b22-c260-43b3-9585-26e0ea2d04da" />


### Entities and Attributes

| Entity   |                    Attributes (PK, FK)                     |           Notes                    |
|--------  |------------------------------------------------------------|------------------------------------|
|Member    |Member_ID (PK), Name, Membership_Type, Start_Date           |Tracks all gym members              | 
|Program   |Program_ID (PK), Program_Name, Type                         |Yoga, Zumba, Weight Training        |
|Trainer   |Trainer_ID (PK), Name, Specialization                       |A trainer may take multiple programs|
|Session   |Session_ID (PK), Member_ID (FK), Trainer_ID (FK), Date, Time|For personal training sessions      |
|Attendance|Attendance_ID (PK), Session_ID (FK), Status (Present/Absent)|Records session attendance          |

### Relationships and Constraints

|      Relationship        | Cardinality | Participation |               Notes                    |
|--------------------------|-------------|---------------|----------------------------------------|
|Member–Program (Joins)    |M:N          |Partial        |A member can join many programs         |
|Program–Trainer (Assigned)|M:N          |Total          |Programs can have multiple trainers     |
|Session–Attendance        |1:M          |Partial        |Each session must have attendance record|

### Assumptions
 1.Membership type determines allowed programs but not restricted in ER model. -Personal training sessions are optional. -Payments cover both membership fees and session fees.
---

# Scenario B: City Library Event & Book Lending System

**Business Context:**  
The Central Library wants to manage book lending and cultural events.

**Requirements:**  
- Members borrow books, with loan and return dates tracked.  
- Each book has title, author, and category.  
- Library organizes events; members can register.  
- Each event has one or more speakers/authors.  
- Rooms are booked for events and study.  
- Overdue fines apply for late returns.

### ER Diagram:
<img width="752" height="432" alt="image" src="https://github.com/user-attachments/assets/4ebb7a3e-485e-4777-8a76-5480c8bfc91f" />


### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|Member|Member_ID (PK), Name, Email, Phone|Library members|
|Book|Book_ID (PK), Title, Author, Category|Each book has category (Fiction, etc.)|
|Loan|Loan_ID (PK), Book_ID (FK), Member_ID (FK), Loan_Date, Return_Date|Tracks borrowing details|
|Event|Event_ID (PK), Title, Date, Time|Cultural events organized by library|
|Speaker|Speaker_ID (PK), Name, Expertise|Authors or guest speakers|  

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|Member–Loan (Borrows)|1:M|Total|Each member can borrow many books|
|Book–Loan|1:M|Total|A book can appear in many loan records|
|Member–Event (Registers)|M:N|Partial|Members can register for events|
|Event–Speaker|M:N|Total|Each event must have at least one speaker|


### Assumptions
- Each event must take place in one room.

-Multiple speakers can be assigned to one event.

-Fine is applied only if return date > due date.

---

# Scenario C: Restaurant Table Reservation & Ordering

**Business Context:**  
A popular restaurant wants to manage reservations, orders, and billing.

**Requirements:**  
- Customers can reserve tables or walk in.  
- Each reservation includes date, time, and number of guests.  
- Customers place food orders linked to reservations.  
- Each order contains multiple dishes; dishes belong to categories (starter, main, dessert).  
- Bills generated per reservation, including food and service charges.  
- Waiters assigned to serve reservations.

### ER Diagram:
<img width="1467" height="742" alt="image" src="https://github.com/user-attachments/assets/d7b877e8-6fd4-4ace-85c7-28274d1ec2d2" />


### Entities and Attributes

|   Entity  |                Attributes (PK, FK)                      |         Notes            |
|-----------|---------------------------------------------------------|--------------------------|
|Customer   |Customer_ID (PK), Name, Phone, Email                     |Guests visiting restaurant|
|Reservation|Reservation_ID (PK), Customer_ID (FK), Date, Time, Guests|Reservation details       |
|Table      |Table_ID (PK), Capacity                                  |Reserved for customers    |
|Order      |Order_ID (PK), Reservation_ID (FK), Order_Time           |Orders placed             | 
|Dish       |Dish_ID (PK), Dish_Name, Price                           |Menu items                |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|Customer–Reservation (Makes)|1:M|Partial|A customer can make multiple reservations|
|Reservation–Table(Assigned)|M:1|Total|Each reservation must have one table|
|Reservation–Order|1:M|Partial|Orders are linked to reservations|
|Order–Dish (Contains)|M:N|Total	Orders contain multiple dishes| 

### Assumptions
- Walk-in customers are entered as new records in the system.

-Each reservation must be linked to exactly one table.

-One bill per reservation (no bill-splitting considered). 

---

## Instructions for StudentsF

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
