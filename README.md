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

### Implementation of Python and SQL
- Connected SQL Workbench with Python using root credentials.
- Retrieved student data from the database and converted it into a data frame for visualization in Jupyter Notebook.

### Visualizations:
- **Gender Distribution**: Illustrated diverse gender representation among students (Male, Female, Non-Binary).
- **Correlation Heat Map**: Showed the relationship between Age, CreditLoad, and GPA using Seaborn.
- **Time Distribution**: Bar chart of student activity across different times of the day.
- **GPA vs. Course**: Scatter plot showing variation of GPA across different courses.

### Implementation of NoSQL and SQL
- Created a cluster on MongoDB to mirror all MySQL tables.
- Performed queries on the student_mental_health database using MongoDB.

### NoSQL Queries:
- **Find Male Students**: Retrieve all male students.
- **Find Students Above Age 20**: List students whose age is greater than 20.
- **Find Students with GPA > 3.5**: Retrieve students with GPA greater than 3.5.
- **Count Students by Gender**: Count the number of students by gender.
- Find Students Whose Name Starts with 'A'.

---

## SQL Queries
Sample queries include:
1. **Calculate Total Payments per Student**:
   ```sql
   SELECT StudentID_FK, SUM(Amount) AS TotalPaid
   FROM PAYMENTS
   GROUP BY StudentID_FK
   ORDER BY TotalPaid DESC;
2. **Students and Their Workouts**:
   ```sql
   SELECT S.Name AS StudentName, W.WorkoutName 
   FROM STUDENT S 
   JOIN STUDENT_WORKOUTS SW ON S.StudentID = SW.StudentID_FK 
   JOIN WORKOUT W ON SW.WorkoutID_FK = W.WorkoutID 
   ORDER BY S.Name;
3. **Find Students Above the Average GPA of Their School**:
   ```sql
   SELECT StudentID_FK, SUM(Amount) AS TotalPaid
   FROM PAYMENTS
   GROUP BY StudentID_FK
   ORDER BY TotalPaid DESC;
4. **Find Workouts Attended by at Least One Student**:
   ```sql
   SELECT W.WorkoutName
   FROM WORKOUT W
   WHERE EXISTS (
       SELECT StudentID
       FROM STUDENT_WORKOUTS SW
       WHERE SW.WorkoutID_FK = W.WorkoutID
   );
5. **List Students, Doctors, and Therapy Details**:
   ```sql
   SELECT ST.Name AS StudentName, D.DoctorName, A.Date, A.Time, TS.SessionType
   FROM STUDENT ST
   JOIN STUDENT_DOCTOR SD ON ST.StudentID = SD.StudentID_FK
   JOIN DOCTORS D ON SD.DoctorID_FK = D.DoctorID
   JOIN APPOINTMENTS A ON SD.StudentID_FK = A.StudentDoctorID_FK
   JOIN THERAPY_SESSIONS TS ON A.AppointmentID = TS.AppointmentID_FK
   WHERE TS.SessionType = 'Physical'
   ORDER BY A.Date, A.Time;

---

## Authors
Vinyas Naidu Karri.
Sri Sai Tarun Vemu

---

## License

This project is licensed under the MIT License. For more details, see the [LICENSE.md](LICENSE.md) file.
