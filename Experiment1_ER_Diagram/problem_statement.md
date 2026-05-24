# **Experiment 1: Entity-Relationship (ER) Diagram**

## **🎯 Objective:**

To understand and apply the concepts of ER modeling by creating an ER diagram for a real-world application.

## **📚 Purpose:**

The purpose of this workshop is to gain hands-on experience in designing ER diagrams that visually represent the structure of a database including entities, relationships, attributes, and constraints.

---

# **🧪 Scenario Chosen: Hospital Database**

Design a database for patient management, appointments, medical records, and billing.

---

# **📝 User Requirements**

* Patient details including contact and insurance.
* Doctors and their departments, contact info, specialization.
* Appointments with reason, time, patient-doctor link.
* Medical records with treatments, diagnosis, test results.
* Billing and payment details for each appointment.

---

# **ER Diagram**
<img width="1287" height="774" alt="image" src="https://github.com/user-attachments/assets/44a1d9cf-35ed-4de4-8898-4aac6ae18c75" />

---

# **Entities and Attributes**

## **Patient**

* **PatientID (PK)**
* **FullName**
* **DOB**
* **Gender**
* **Address**
* **Phone**
* **Email**
* **InsuranceDetails**

---

## **Doctor**

* **DoctorID (PK)**
* **FullName**
* **Specialization**
* **Phone**
* **Email**
* **ScheduleDetails**

---

## **Department**

* **DepartmentID (PK)**
* **DepartmentName**
* **DepartmentHead**

---

## **Appointment**

* **AppointmentID (PK)**
* **AppointmentDateTime**
* **Reason**
* **Notes**
* **PatientID (FK)**
* **DoctorID (FK)**

---

## **MedicalRecord**

* **MedicalRecordID (PK)**
* **Diagnosis**
* **Medications**
* **Treatments**
* **TestResults**
* **VisitDate**
* **PatientID (FK)**
* **DoctorID (FK)**

---

## **Billing**

* **BillingID (PK)**
* **AppointmentID (FK)**
* **TotalAmount**
* **Status (Paid/Unpaid)**
* **BillingDate**

---

## **Payment**

* **PaymentID (PK)**
* **BillingID (FK)**
* **PaymentMode (Cash/Card/Online)**
* **PaymentDate**
* **AmountPaid**

---

# **Relationships and Constraints**

## **Relationships**

* **Department → Doctor : 1 to Many**
* **Doctor ↔ Patient : Many to Many (via Appointment)**
* **Patient ↔ Doctor : Many to Many (via MedicalRecord)**
* **Appointment → Billing : 1 to 1**
* **Billing → Payment : 1 to Many**

---

## **Cardinality & Participation Constraints**

* Every **Appointment** is between **1 Doctor** and **1 Patient**.
* A **Billing** record is created for each appointment.
* A **Payment** may be split into multiple records.
* One **Department** can contain many doctors.
* One **Doctor** belongs to only one department.

---

# **Extension: Billing and Payment**

## **Bill Entity**

### **Attributes**

* **BillID (PK)**
* **DateIssued**
* **TotalAmount**
* **Status (Paid/Unpaid)**
* **PaymentMethod**

### **Relationship**

* **Appointment → Bill : 1 to 1**

One appointment generates one bill.

---

## **Optional Extension: Payment Entity**

### **Attributes**

* **PaymentID**
* **AmountPaid**
* **DatePaid**
* **PaymentMethod**

### **Relationship**

* **Bill → Payment : 1 to Many**

This supports:

* Partial payments
* Installments
* Insurance co-payments

---

# **Design Justification**

## **Why These Entities Were Chosen**

### **Patient**

Chosen to represent individuals receiving healthcare services.
Attributes such as **PatientID**, **Name**, **DOB**, and **InsuranceDetails** are necessary for identification, communication, and billing.

---

### **Doctor**

Represents healthcare professionals.
Attributes like **DoctorID**, **Specialization**, and **ScheduleDetails** help manage consultations and appointments.

---

### **Department**

Provides organizational structure such as:

* Cardiology
* Neurology
* Orthopedics

It helps group doctors under specific medical specialties.

---

### **Appointment**

Used to capture interactions between patients and doctors.
This resolves the many-to-many relationship between patients and doctors.

Includes:

* Appointment date
* Time
* Reason for visit
* Notes

---

### **MedicalRecord**

Stores clinical information including:

* Diagnosis
* Treatments
* Medications
* Test results

Linked with both patient and doctor to maintain medical history and accountability.

---

### **Billing**

Introduced to manage financial details separately from appointments.

Tracks:

* Total charges
* Billing status
* Billing date

---

### **Payment**

Represents transactions made against a bill.

Supports:

* Multiple payments
* Installments
* Partial payments

---

# **Relationship Choices and Assumptions**

## **Patient – Appointment – Doctor**

Modeled using the **Appointment** entity because:

* A patient can consult many doctors.
* A doctor can treat many patients.

This creates a **many-to-many** relationship.

---

## **Doctor – Department**

* One department can have many doctors (**1:N**).
* Each doctor belongs to one department.

---

## **MedicalRecord – Patient & Doctor**

Medical records are created for each patient visit and linked to:

* One patient
* One doctor

This helps maintain visit-based records.

---

## **Appointment – Billing**

Each appointment generates exactly one billing record.

Relationship:

* **1:1**

---

## **Billing – Payment**

One bill can contain multiple payment records.

Relationship:

* **1:N**

This supports real-world billing systems.

---

# **Key Assumptions**

* Every patient visit must have an appointment.
* Every appointment generates a bill.
* Medical records are visit-based.
* Multiple payments can be made for a single bill.

---

# **## RESULT**

Successfully designed an **ER diagram for the Hospital Database** with:

* Entities
* Attributes
* Relationships
* Cardinality constraints
* Billing and payment extensions

The design effectively supports real-world healthcare management operations.
