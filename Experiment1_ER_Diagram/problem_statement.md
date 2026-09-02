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

<img width="882" height="586" alt="image" src="https://github.com/user-attachments/assets/7c8b8807-9960-4f0a-91b6-dd662f8655c3" />


### Entities and Attributes
```
1.Members
   Name
   Contact number
   Address
2.Programs
   Type
   Duration
   Fees
3.Trainers
   Name
   Specialization
   Contact number
4.Payments
   Amount
   Payment Type
   Due Date
```

### Relationships and Constraints
```
1.Members — Joins → Programs
2.A member joins one or more programs.
3.Programs — Conducts → Trainers
4.Trainers conduct programs.
5.Trainers — Duty → Payments
6.Payments are associated with trainers’ duties.
```
### Assumptions
```
1.A member must be registered before borrowing books or registering for events.
2.Member contact number is unique.
3.Each loan refers to a single book and a single member.
4.Loan must have both a loan date and due date.
5.Every book belongs to exactly one category
```
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

<img width="862" height="415" alt="image" src="https://github.com/user-attachments/assets/4a366ab9-a0b5-4399-832c-f759fa933e78" />

### Entities and Attributes
```
1.MEMBER
   memb_id(PK)
   memb_name
   contact no.
   date
2.LOAN
   loan_date
   due_date
   return_date
   fine
   memb_id(FK)
   book_id(FK)
   loan_id(PK)
3.BOOK
   Title
   Author
   Category
   book_id(PK)
4.Event
   event_id(PK)
   event_name
   event_date
   room_id(FK)
5.Speaker
   speaker_id(PK)
   name
6.Room
   room_id(PK)
   room_name
   capacity
   purpose
```   
### Relationships and Constraints
```
1.Member ↔ Loan ↔ Book
   A Member can borrow many Books (M:N, resolved via Loan).
   Each Loan relates one Member to one Book.
2.Member ↔ Event
   A Member can register for many Events.
   An Event can have many Members.
   M:N → resolved via Event_Registration.
3.Room ↔ Speaker
   A Room can have multiple Speakers.
4.Event ↔ Room
   Each Event occurs in exactly one Room (1:N).
```
### Assumptions
```
1.A member must be registered before borrowing books or registering for events.
2.Member contact number is unique.
3.Each loan refers to a single book and a single member.
4.Loan must have both a loan date and due date.
5.Every book belongs to exactly one category
```
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

<img width="868" height="442" alt="image" src="https://github.com/user-attachments/assets/7fb76436-723b-467f-9f49-005eb7415c9e" />

### Entities and Attributes
```
1. Customer
* customerID(PK)
* Name
* Phone no
2. Reservation
* reservationID(PK)
* Reservation date and time
* customerID(FK)
3. Table
* tableID(PK)
* Table number
* Capacity
* categoryID(FK)
4. Category
* categoryID(PK)
* Category Name
5. Dish
* dishID(PK)
* Name
* Price
* categoryID(FK)
6. Order
* orderID(PK)
* Order time
* reservationID(FK)
* waiterID(FK)
7. Bill
* billID(PK)
* Total amount
* orderID(FK)
8. Waiter
* waiterID(PK)
* Name
* Phone no
```
### Relationships and Constraints
```
1. Customer <-> Reservation
   One customer books many reservations.
   Each reservation belongs to one customer.
   1 : N
2. Reservation <-> Table
   One reservation is assigned to one table.
   A table can be assigned to many reservations (over time).
   1 : N
3. Reservation <-> Order
   One reservation generates one or many orders.
   Each order belongs to exactly one reservation.
   1 : N
4. Waiter <-> Order
   One waiter serves many orders.
   Each order is served by exactly one waiter.
   1 : N
5. Order <-> Bill
   Each order produces one bill.
   Each bill is linked to only one order.
   1 : 1
6. Bill <-> Dish
   A bill contains many dishes.
   Each dish can appear in many bills.
   M : N
7. Dish <-> Category
   Each dish belongs to one category.
   A category can contain many dishes.
   1 : N
```
### Assumptions
```
1.A customer must register before making a reservation
2.Every reservation requires a valid and unique customerID.
3.A table may serve multiple reservations, but not simultaneously
4.Each order must be served by exactly one waiter
5.A customer can have multiple reservations
6.But no double-booking at the same date and time in the same table.
7.Contact details like phone number are assumed unique.
8.Order time is recorded
```
---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
