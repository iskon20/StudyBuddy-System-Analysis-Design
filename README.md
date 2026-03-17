# 🏫 StudyBuddy - Smart Student Collaboration Platform

**Academic Year:** 2026  
**Course:** System Analysis and Design  
**Team Name:** Metric  

---

## 👥 Team Members & Roles

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

### ERD Diagram



