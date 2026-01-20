# Nished — Learning Platform with AI Proctoring

Nished is a full-stack learning and assessment platform built to host coding content, projects, and online exams.  
It includes an **AI-based Proctoring System** to monitor users during exams and store session-level proctoring data securely.

PROJECT LINK: https://nish-educates.netlify.app/
---

## 🚀 Features

- 📚 Coding courses & pattern-based learning content
- 🧑‍💻 User authentication & profiles
- 📝 Assessments (MCQs + coding exams)
- 🔒 AI Proctoring system for online exams
- 📊 Exam session tracking & admin review
- ☁️ Cloud-based user & session storage (MongoDB Atlas)

---

## 🧱 Tech Stack

### Frontend
- React
- React Router
- Axios
- CSS / Tailwind (if applicable)

### Backend
- Node.js
- Express.js
- JWT Authentication
- Mongoose

### Database
- **MongoDB Atlas (Cloud)**
  - User details
  - Exam sessions
  - Proctoring data

### Storage
- **Local filesystem**
  - Course content
  - Static assets
  - Proctoring evidence (small images / thumbnails)

---

## 📂 Project Architecture

```

NISHED
│
├── client/                 # React frontend
│
├── server/                 # Node.js backend
│   ├── controllers/
│   ├── routes/
│   ├── models/
│   ├── middleware/
│   └── uploads/             # Local evidence storage
│
├── content/                 # Local course/lesson content
│
└── README.md

````

---

## 🧠 AI Proctoring System (By Nish)

The AI Proctoring system monitors candidates during online exams and records behavior-based signals to ensure exam integrity.

### What is monitored
- Camera access (face presence)
- Tab switching / window focus changes
- Session duration & activity timeline
- Proctoring flags (stored per session)

> Note: All proctoring data is stored **per session in MongoDB Cloud**.  
> No external cloud storage or queues are used at this stage.

---

## 🔄 Proctoring Flow

1. User starts a proctored exam
2. Exam session is created in MongoDB
3. Browser permissions (camera, tab focus) are tracked
4. Proctoring events are attached to the exam session
5. Session summary is generated for review

---

## 🗃️ Database Design (Simplified)

### `users`
```json
{
  "name": "User Name",
  "email": "user@email.com",
  "passwordHash": "...",
  "role": "student"
}
````

### `exam_sessions`

```json
{
  "userId": "ObjectId",
  "examId": "exam_123",
  "status": "in_progress",
  "startedAt": "ISODate",
  "endedAt": "ISODate",
  "proctorSummary": {
    "riskScore": 10,
    "flags": ["tab_switch", "face_absent"]
  }
}
```

---

## 🔌 API Overview

### Auth

* `POST /api/auth/register`
* `POST /api/auth/login`

### Exams

* `POST /api/exams/:id/start`
* `POST /api/exams/:id/submit`

### Proctoring

* `POST /api/proctor/event`
* `GET /api/admin/session/:id`

---

## ⚠️ Current Limitations

* Course content stored locally (not CMS-based yet)
* Proctoring logic is rule-based (ML expansion planned)
* No cloud object storage (S3 not used currently)

---

## 🔮 Future Enhancements

* ML-based face & gaze detection
* Cloud storage for large evidence files
* Redis-based real-time session handling
* Live human proctor option
* Exam playback timeline for admins

---

## 🧑‍💻 Author

**Nishtha Singh**
Full Stack Developer
Project: **Nished**



