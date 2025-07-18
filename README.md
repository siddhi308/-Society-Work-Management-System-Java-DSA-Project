# -Society-Work-Management-System-Java-DSA-Project
 We have created a management system for society work where this is accessible for 4  types of persons: Admin (Secretary) , Society Members , Other than Society Member  ,Helper .
 
# 🏡 Society Management System - Java DSA Project

## 📌 Overview

This is a **Java-based console application** that manages daily tasks of a residential society. The application is built using **core Java concepts and data structures** like Binary Search Trees and Linked Lists. It covers management of society members, maintenance fees, helper staff, and hall booking system.

---

## 🧰 Modules & Features

### 1. 📅 Society Member Management (Binary Search Tree)

* Add, Update, Delete, and Search member records
* Fields include: Name, Flat Number, Flat Status (Owner/Tenant), Life Status (Family/Bachelor), Phone Number, Maintenance Due
* Flat numbers are stored in a **BST** to ensure fast search and ordering

### 2. 📞 Phone Directory & Sorting

* Display all member phone numbers
* Search member by flat number or phone number
* Sort members by:

  * Phone number
  * Name (alphabetically)

### 3. 🧱 Maintenance Fee Tracker

* Every flat pays ₹2500 every 6 months
* System tracks payments, dues, or overpayments
* Output displayed in readable format (Paid / Due)

### 4. 🏢 Hall Booking System (Doubly Linked List)

* Book society hall (2 halls available: 100 and 400 capacity)
* Validate and prevent duplicate bookings on the same date
* Store and display bookings using **doubly linked list**

### 5. 💼 Helper Staff Management (BST)

* Manage data for helpers: Watchman, Housekeeper, Gardner, etc.
* Store helper name, ID, area of work, phone number, and attendance status
* Mark attendance ("present") by helper login

### 6. 🔐 Role-Based Access System

| Role           | Password    | Permissions                                       |
| -------------- | ----------- | ------------------------------------------------- |
| Admin          | `ssva`      | Full access to member, helper, hall & maintenance |
| Society Member | `dream@123` | Can view, search, pay maintenance, book halls     |
| Helper         | `vssa`      | Can mark themselves present                       |
| Visitor        | None        | Can book and view hall bookings                   |

---

## 🔧 Technologies Used

* Java (Core)
* OOP: Classes, Objects, Encapsulation
* Data Structures: Binary Search Tree, Linked List, Stack
* Console Input via Scanner

---

## 📊 Sample Execution Flow

```bash
1) Admin Login
2) Add Member: Sakshi Manoj Deshmukh, Flat #7
3) Pay Maintenance: ₹2500
4) Book Hall #1 for 12/1/2023
5) Add Helper: Vishal (Housekeeper, ID: 1)
6) Display Members & Bookings
```

---

## 📁 Project Structure

* `SocietyWork.java` - Main driver class
* `BinarySearchTree.java` - Member management logic
* `BookHall1.java` - Hall booking module
* `BST.java` - Helper staff management
* `Node.java`, `Node1.java`, `Hall1.java` - Data entity models

---

## 🚀 How to Run

1. Compile:

```bash
javac SocietyWork.java
```

2. Run:

```bash
java SocietyWork
```

---

## 📝 Author

* Developed as part of a Java DSA academic project to demonstrate real-world application of data structures and object-oriented programming.


  
