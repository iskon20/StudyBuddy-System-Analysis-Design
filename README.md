# StudyBuddy - Smart Student Collaboration Platform

**Academic Year:** 2026  
**Course:** System Analysis and Design  
**Team Name:** Metric  

---

## 👥 Team Members

| Name | Student ID | Group | Role | Contact |
|------|------------|--------|------|---------|
| Dadabaev Iskandar | 202490094 | I24D | Project Developer | [Telegram](https://t.me/IDnoksi) |
| Muratov Shaxrux | 202490201 | I24D | Team Leader & Process Analyst | [Telegram](https://t.me/dothdc) |
| Fayzullayev Shokhruh | 202490117 | I24D | System Designer | [Telegram](https://t.me/Shokhruh23) |
| Babaev Akmal | 202490071 | I24C | Database Designer | [Telegram](https://t.me/lixali) |
| Kenesbaeva Gulsevar | 202490164 | I24D | UI/UX Designer | [Telegram](https://t.me/gulsevarkr) |

---

## 📝 Project Overview

**StudyBuddy** is an online platform aimed at helping students find study partners, organize collaborative study sessions, and enhance learning efficiency.  
Students can create, search, and join study sessions, categorized by subjects, while mentors and admins manage the system and provide guidance.  
The platform ensures a structured approach to collaborative learning, streamlines session management, and tracks participation and feedback.

---

## 🎯 Project Objectives

- Collect and analyze functional and non-functional requirements for a student collaboration platform.  
- Model key business processes with BPMN diagrams.  
- Design system workflows using UML (Use Case, Sequence, Activity diagrams).  
- Create a relational database design (ERD, DBML) suitable for future implementation.  
- Develop a simple, intuitive UI/UX prototype for session navigation and management.

---

## 🔍 System Scope

- **User Roles:** Student, Mentor, Admin  
- **Sessions:** Create, join, leave, manage study sessions  
- **Subjects:** Categorize sessions for targeted learning  
- **Participants:** Track users joining sessions  
- **Feedback:** Collect ratings and comments on sessions  

---

## 🛠 Tech Stack & Tools

- **Database & ERD:** MySQL, dbdiagram.io  
- **Diagrams:** Lucidchart, Visual Paradigm, Draw.io  
- **UI/UX:** Figma  
- **Version Control:** Git & GitHub  
- **Documentation:** Markdown  

---

## 🗂 Database Architecture

### Tables

- **Users** — store student, mentor, and admin profiles  
- **Subjects** — subjects for study sessions  
- **Sessions** — details of each study session  
- **SessionParticipants** — track users joining sessions  
- **Reviews** — store ratings and comments  

### Relationships

- Users → Sessions (creator of session)  
- Users → SessionParticipants  
- Users → Reviews  
- Subjects → Sessions  
- Sessions → SessionParticipants, Reviews  

### DBML Structure

<pre>
Table users {
  user_id integer [primary key]
  name varchar
  email varchar
  password varchar
  role varchar
  created_at timestamp
}

Table subjects {
  subject_id integer [primary key]
  name varchar
  description text
}

Table sessions {
  session_id integer [primary key]
  subject_id integer [not null]
  creator_id integer [not null]
  session_date timestamp
  location varchar
  max_participants integer
  description text
  created_at timestamp
}

Table session_participants {
  participant_id integer [primary key]
  session_id integer [not null]
  user_id integer [not null]
  status varchar
  joined_at timestamp
}

Table reviews {
  review_id integer [primary key]
  session_id integer [not null]
  reviewer_id integer [not null]
  rating integer
  comment text
  review_date timestamp
}

// Relationships
Ref: sessions.creator_id > users.user_id
Ref: sessions.subject_id > subjects.subject_id
Ref: session_participants.session_id > sessions.session_id
Ref: session_participants.user_id > users.user_id
Ref: reviews.session_id > sessions.session_id
Ref: reviews.reviewer_id > users.user_id
</pre>

---

## Structural Diagrams

### **Entity-Relationship Diagram (ERD)**
**Visual:** ![ERD](https://github.com/iskon20/StudyBuddy-System-Analysis-Design/blob/main/diagrams/dbml.png)

* **Description**: This diagram illustrates the complete database schema. It details core entities such as `Users`, `StudySessions`, `Subjects`, and `Enrollments`, along with their specific attributes and constraints.
* **Key Relationships**: Defines how data points connect, including **One-to-Many** (e.g., one Mentor to many Sessions) and **Many-to-Many** (e.g., Students to Sessions) relationships.
* **Technical Purpose**: Acts as the technical blueprint for backend development, ensuring data integrity and efficient query performance.

### **Use Case Diagram**
**Visual:** ![Use Case](https://github.com/iskon20/StudyBuddy-System-Analysis-Design/blob/main/diagrams/use_case_diagram.png)

* **Description**: Visualizes the interactions between the system's primary actors and their specific goals.
* **Roles & Actions**:
    * **Student**: Search for sessions, register for classes, and download materials.
    * **Mentor**: Create session schedules, manage participant lists, and upload resources.
    * **Admin**: Moderate content, manage user accounts, and access system analytics.
* **Functional Purpose**: Defines the functional scope of the project and clarifies "who" can perform "which" actions within the system.

---

## 2. Behavioral & Process Diagrams

### **BPMN Diagram (Business Process Model and Notation)**
**Visual:** ![BPMN](https://github.com/iskon20/StudyBuddy-System-Analysis-Design/blob/main/diagrams/bpmn_diagram.png)

* **Workflow**: *“Join Study Session”*
* **Description**: Illustrates the end-to-end user journey from selecting a session and passing validation checks (like seat availability) to receiving a final confirmation and calendar invite.
* **Business Purpose**: Provides a high-level view of the business logic, including decision gateways and error handling (e.g., handling "Session Full" scenarios).

### **Sequence Diagram**
**Visual:** ![Sequence Diagram](https://github.com/iskon20/StudyBuddy-System-Analysis-Design/blob/main/diagrams/sequence_diagram.png)

* **Interaction Flow**: `Student` → `System` → `Sessions` → `SessionParticipants`
* **Description**: A detailed technical breakdown of the chronological interactions between system components and the database.
* **Implementation Purpose**: Shows exactly how objects communicate via API calls and database queries in real-time. It serves as a roadmap for developers to implement the specific order of operations required to complete a transaction.

---

## ⏳ 5-Week Roadmap

The project development is divided into five key phases, moving from initial analysis to a complete technical blueprint.

| Week | Phase | Deliverables |
|:---:|:---|:---|
| **1** | **Requirement Analysis** | Functional & Non-functional requirements, User Personas. |
| **2** | **BPMN Modeling** | BPMN diagrams for "Joining" and "Creating" study sessions. |
| **3** | **System Design** | UML Use Case, Sequence, and Activity diagrams. |
| **4** | **Data Architecture** | ERD, DBML, Data Dictionary, and UI/UX mockups. |
| **5** | **Finalization** | Comprehensive project documentation, final report, and presentation. |

---

## ✅ Expected Outcomes

Upon completion of the design phase, the following assets will be delivered:

* **Full System Requirements Specification (SRS):** Detailed documentation of all system constraints and capabilities.
* **Complete UML Diagrams Suite:** Visual models of system behavior and object interactions.
* **ERD & Relational Database Blueprint:** A structured data model ready for SQL implementation.
* **Interactive UI/UX Prototype:** High-fidelity wireframes showing the user journey.
* **Software Design Plan:** A production-ready roadmap for the development team.

---

## 🧾 Conclusion

**StudyBuddy** facilitates structured collaborative learning, improves efficiency, and simplifies session tracking. 

By combining a solid database foundation, detailed process modeling, and intuitive UI/UX design, the platform provides a robust framework ready for immediate software development and future scalability.
