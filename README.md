# Student Mental Health

This project, developed for the **IE6700 Data Management for Analytics** course, aims to address the pressing issue of student mental health through data management and analytics. The solution is designed as a web application capable of storing and analyzing student data to provide actionable insights and support mental health initiatives.

---

## Table of Contents
1. [Project Overview](#project-overview)
2. [Goals](#goals)
3. [Data Models](#data-models)
4. [Implementation](#implementation)
5. [SQL Queries](#sql-queries)
6. [Authors](#authors)
7. [License](#license)

---

## Project Overview
In many regions of the world, student mental health is a growing concern. Issues such as depression, anxiety, and stress are prevalent among students, impacting their well-being and academic performance. This project provides a platform to analyze and address these issues through effective data management and collaboration among stakeholders like mental health professionals, educators, and support staff.

---

## Goals
The project aims to:
1. Provide insights into student mental health to reduce stigma and encourage treatment-seeking behavior.
2. Prevent escalation of mental health issues by identifying at-risk individuals early.
3. Facilitate collaboration between stakeholders to deliver personalized care and promote well-being.

The web application stores critical data points such as:
- Personal and academic information (e.g., GPA, credit load)
- Mental health metrics (e.g., anxiety, stress, depression levels)
- Lifestyle factors (e.g., sleep and diet cycles, physical activities)
- Counseling and therapy details.

---

## Data Models
### Conceptual Data Model
The data model includes entities like students, schools, workouts, doctors, appointments, therapy sessions, and payments. Relationships are designed to capture the interaction between these entities, providing a comprehensive view of student mental health data.

### Relational Model
The database schema, implemented using MySQL, contains 11 normalized tables:
- **STUDENT**: Stores student demographic and academic details.
- **SCHOOL**: Contains school information.
- **WORKOUT**: Tracks types of physical activities.
- **LOGIN**: Manages user credentials.
- **PAYMENTS**: Records financial transactions.
- **DOCTORS**: Details about doctors.
- **APPOINTMENTS**: Tracks appointments and sessions.
- **THERAPY_SESSIONS**: Details of therapy sessions.

---

## Implementation
The relational model is implemented in MySQL under the schema `Student_Mental_Health`. The schema ensures normalized data storage to optimize queries and maintain data integrity.

---

## SQL Queries
Sample queries include:
1. **Calculate Total Payments per Student**:
   ```sql
   SELECT StudentID_FK, SUM(Amount) AS TotalPaid
   FROM PAYMENTS
   GROUP BY StudentID_FK
   ORDER BY TotalPaid DESC;
