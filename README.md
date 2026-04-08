# Modern Clinic Management System - Database Design

## 📌 Project Overview
This repository contains the Entity-Relationship (ER) diagram and database schema for a modern clinic management system. The design is structured to handle the end-to-end workflow of a clinic, seamlessly tracking patients from their initial appointment booking through consultations, diagnostic testing, reporting, and final billing. 

The schema is built to be scalable, clean, and normalized, ensuring that business logic is strictly maintained.

## 🗄️ Schema Entities
The database is divided into four main operational areas:

### 1. Core Clinic Structure
* **`Specialty`**: Catalogs the different medical departments (e.g., Cardiology, Pediatrics).
* **`Doctor`**: Stores doctor profiles, linked to their respective specialties.
* **`Patient`**: Manages patient demographics and contact details.

### 2. Appointments & Consultations
* **`Appointment`**: Acts as the scheduling intent. Links a patient to a doctor for a specific date and time.
* **`Consultation`**: Represents the actual visit. Created only when an appointment is fulfilled. Contains the doctor's notes, diagnosis, and prescription details.

### 3. Diagnostics & Reporting
* **`Test_Catalog`**: The master list of all available diagnostic tests and their standard costs.
* **`Prescribed_Test`**: A bridging record that tracks which specific tests were ordered during a consultation.
* **`Test_Report`**: The final diagnostic results linked directly to the prescribed test.

### 4. Billing & Payments
* **`Invoice`**: The financial bill generated from a consultation, aggregating consultation fees and diagnostic test costs.
* **`Payment`**: Tracks individual payment transactions against an invoice, supporting split payments or installments.

## 🔗 Key Relationships & Workflows

* **1-to-Many (`1 < *`)**:
  * One **Specialty** can have multiple **Doctors**.
  * One **Patient** can book multiple **Appointments** and have multiple **Invoices**.
  * One **Doctor** can oversee multiple **Appointments**.
  * One **Consultation** can result in multiple **Prescribed Tests**.
  * One **Invoice** can have multiple **Payments** (installments).
* **1-to-1 (`1 - 1`)**:
  * One **Appointment** leads to at most one **Consultation**.
  * One **Prescribed Test** results in exactly one **Test Report**.
  * One **Consultation** generates exactly one **Invoice**.
