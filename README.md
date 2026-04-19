<div align="center">

# 🎓 AlumniConnect
### College Alumni Networking & Mentorship Platform

*Bridging the gap between students and alumni — one mentorship at a time.*

[![JavaScript](https://img.shields.io/badge/JavaScript-98.5%25-F7DF1E?style=flat-square&logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![React](https://img.shields.io/badge/React-Frontend-61DAFB?style=flat-square&logo=react&logoColor=black)](https://reactjs.org/)
[![Node.js](https://img.shields.io/badge/Node.js-Backend-339933?style=flat-square&logo=node.js&logoColor=white)](https://nodejs.org/)
[![MongoDB](https://img.shields.io/badge/MongoDB-Database-47A248?style=flat-square&logo=mongodb&logoColor=white)](https://mongodb.com/)
[![Express](https://img.shields.io/badge/Express.js-API-000000?style=flat-square&logo=express&logoColor=white)](https://expressjs.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](LICENSE)

[Report a Bug](../../issues) · [Request a Feature](../../issues)

</div>

---

## 📖 Table of Contents

- [About the Project](#-about-the-project)
- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Architecture](#-architecture)
- [Getting Started](#-getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Environment Variables](#environment-variables)
  - [Running the App](#running-the-app)
- [User Roles](#-user-roles)
- [API Reference](#-api-reference)
- [Database Schema](#-database-schema)
- [Project Structure](#-project-structure)
- [Contributing](#-contributing)
- [License](#-license)

---

## 🌟 About the Project

**AlumniConnect** is a full-stack web platform designed to bridge the gap between college students and alumni. Students can discover mentors, send mentorship requests, explore job and internship opportunities, and communicate directly — all within a single, structured environment.

The platform eliminates the problem of scattered, unorganized alumni networks on social media by providing a centralized, role-based system built for professional growth.

### 💡 Problem It Solves

| Problem | Solution |
|---|---|
| No structured way for students to reach alumni | Role-based mentorship request system |
| Alumni networks scattered across social media | Centralized searchable alumni directory |
| Limited access to career opportunities | Dedicated job & internship board |
| No real-time communication channel | Built-in messaging between connected users |
| No platform oversight | Admin dashboard for moderation |

---

## ✨ Features

### 🔐 Authentication
- Secure signup and login with **JWT authentication**
- Role-based access control — Student, Alumni, Administrator
- Password hashing with **bcrypt**
- Auto session expiry with graceful logout

### 👤 Profiles
- Detailed professional profiles with skills, industry, experience, and bio
- Skill tags, company, graduation year, and profile photo
- Public alumni profile pages for student discovery

### 🔍 Alumni Discovery
- Browse and search alumni by name, industry, and skills
- Filter combinations with real-time results
- Paginated card grid with clean, modern UI

### 🤝 Mentorship System
- Students send mentorship requests with a personal message
- Alumni accept or reject requests
- Full status tracking — Pending / Accepted / Rejected
- Mentorship history for both parties

### 💬 Messaging
- In-platform messaging between connected (accepted mentorship) users
- Conversation list + chat window interface
- Auto-refreshing with message polling

### 💼 Opportunity Board
- Alumni post job and internship opportunities
- Students browse and filter by type (Job / Internship)
- Direct link to posting alumni's profile

### 🛠️ Admin Dashboard
- Platform-wide analytics (users, requests, opportunities)
- User management with role filtering
- Delete users with cascading data cleanup

---

## 🛠 Tech Stack

### Frontend
| Technology | Purpose |
|---|---|
| React.js | UI framework |
| Chakra UI | Component library & theming |
| React Router | Client-side routing |
| Axios | HTTP client with interceptors |
| React Context API | Global auth state management |

### Backend
| Technology | Purpose |
|---|---|
| Node.js | Runtime environment |
| Express.js | REST API framework |
| JSON Web Tokens (JWT) | Authentication |
| Bcrypt | Password hashing |
| Mongoose | MongoDB ODM |

### Database & Tools
| Technology | Purpose |
|---|---|
| MongoDB | NoSQL database |
| Git & GitHub | Version control |
| Postman | API testing |
| VS Code | Development environment |

---

## 🏗 Architecture

```
┌────────────────────────────────────────────┐
│              React Frontend                │
│   (Chakra UI · React Router · Axios)       │
└──────────────────┬─────────────────────────┘
                   │ REST API (HTTP)
┌──────────────────▼─────────────────────────┐
│           Express.js API Server            │
│   Auth Middleware · Role Guard · Routes    │
└──────────────────┬─────────────────────────┘
                   │ Mongoose ODM
┌──────────────────▼─────────────────────────┐
│               MongoDB Atlas                │
│  users · mentorshipRequests · messages     │
│  opportunities                             │
└────────────────────────────────────────────┘
```

**Service layers:** Profile Access · Mentorship Services · Messaging · Opportunity Services · Networking Services

---

## 🚀 Getting Started

### Prerequisites

Make sure you have the following installed:

- **Node.js** v18+ → [Download](https://nodejs.org/)
- **npm** v9+ (bundled with Node.js)
- **MongoDB** — local or a free [MongoDB Atlas](https://www.mongodb.com/atlas) cluster
- **Git** → [Download](https://git-scm.com/)

---

### Installation

**1. Clone the repository**
```bash
git clone https://github.com/Aman-Thewhiz/College-Alumni-Networking-Mentorship-Platform.git
cd College-Alumni-Networking-Mentorship-Platform
```

**2. Install Backend dependencies**
```bash
cd backend
npm install
```

**3. Install Frontend dependencies**
```bash
cd ../frontend
npm install
```

---

### Environment Variables

**Backend** — create a `.env` file inside the `/backend` folder:

```env
# Server
PORT=5000

# MongoDB
MONGO_URI=your_mongodb_connection_string_here

# JWT
JWT_SECRET=your_super_secret_jwt_key_here
JWT_EXPIRES_IN=7d

# Environment
NODE_ENV=development
```

**Frontend** — create a `.env` file inside the `/frontend` folder:

```env
VITE_API_BASE_URL=http://localhost:5000/api
```

> ⚠️ Never commit your `.env` files. They are already listed in `.gitignore`. Use `.env.example` as the reference template.

---

### Running the App

**Start the Backend**
```bash
cd backend
npm run dev
```
> Runs on `http://localhost:5000`

**Start the Frontend** *(in a new terminal)*
```bash
cd frontend
npm run dev
```
> Runs on `http://localhost:5173`

---

### Creating an Admin Account

Admin accounts must be set manually in the database. After registering a user normally, open MongoDB Compass or Atlas and update their `role` field:

```json
{ "email": "admin@example.com", "role": "Admin" }
```

---

## 👥 User Roles

| Role | Capabilities |
|---|---|
| **Student** | Browse alumni, send mentorship requests, view opportunities, message mentors |
| **Alumni** | Accept/reject mentorship requests, post opportunities, message students |
| **Admin** | View all users, manage accounts, view platform analytics |

---

## 📡 API Reference

### Auth Routes
| Method | Endpoint | Access | Description |
|---|---|---|---|
| `POST` | `/api/auth/register` | Public | Register a new user |
| `POST` | `/api/auth/login` | Public | Login and receive JWT |
| `GET` | `/api/auth/me` | Protected | Get logged-in user |

### User Routes
| Method | Endpoint | Access | Description |
|---|---|---|---|
| `GET` | `/api/users` | Public | Get alumni list (filterable) |
| `GET` | `/api/users/:id` | Public | Get a user's public profile |
| `PUT` | `/api/users/:id` | Protected | Update own profile |

### Mentorship Routes
| Method | Endpoint | Access | Description |
|---|---|---|---|
| `POST` | `/api/mentorship` | Student | Send a mentorship request |
| `GET` | `/api/mentorship/sent` | Student | Get sent requests |
| `GET` | `/api/mentorship/received` | Alumni | Get incoming requests |
| `PUT` | `/api/mentorship/:id` | Alumni | Accept or reject a request |

### Opportunity Routes
| Method | Endpoint | Access | Description |
|---|---|---|---|
| `GET` | `/api/opportunities` | Public | Browse all opportunities |
| `POST` | `/api/opportunities` | Alumni | Post a new opportunity |
| `DELETE` | `/api/opportunities/:id` | Alumni / Admin | Delete an opportunity |

### Message Routes
| Method | Endpoint | Access | Description |
|---|---|---|---|
| `GET` | `/api/messages/:userId` | Protected | Get conversation with a user |
| `POST` | `/api/messages` | Protected | Send a message |

### Admin Routes
| Method | Endpoint | Access | Description |
|---|---|---|---|
| `GET` | `/api/admin/users` | Admin | Get all users |
| `DELETE` | `/api/admin/users/:id` | Admin | Delete a user |
| `GET` | `/api/admin/stats` | Admin | Get platform statistics |

---

## 🗃️ Database Schema

### Users
```js
{
  name: String, email: String (unique), password: String (hashed),
  role: "Student" | "Alumni" | "Admin",
  bio: String, skills: [String], industry: String,
  graduationYear: Number, company: String,
  experience: String, profilePhoto: String, createdAt: Date
}
```

### MentorshipRequests
```js
{
  studentId: ObjectId (ref: User), alumniId: ObjectId (ref: User),
  message: String, status: "pending" | "accepted" | "rejected",
  requestedAt: Date
}
```

### Opportunities
```js
{
  title: String, description: String, company: String,
  type: "job" | "internship",
  postedBy: ObjectId (ref: User), createdAt: Date
}
```

### Messages
```js
{
  senderId: ObjectId (ref: User), receiverId: ObjectId (ref: User),
  content: String, sentAt: Date
}
```

---

## 📁 Project Structure

```
College-Alumni-Networking-Mentorship-Platform/
│
├── backend/
│   ├── config/          # Database connection
│   ├── controllers/     # Route handler logic
│   ├── middleware/      # Auth & role guards
│   ├── models/          # Mongoose schemas
│   ├── routes/          # Express route definitions
│   ├── .env             # Environment variables (not committed)
│   └── server.js        # Entry point
│
├── frontend/
│   ├── public/          # Static assets
│   └── src/
│       ├── api/         # Axios instance & API calls
│       ├── components/  # Reusable UI components
│       ├── context/     # Auth context provider
│       ├── pages/       # Route-level page components
│       ├── theme/       # Chakra UI custom theme
│       └── main.jsx     # App entry point
│
├── .env.example         # Environment variable template
├── .gitignore
└── README.md
```

---

## 🤝 Contributing

Contributions are welcome!

1. **Fork** the repository
2. **Create** your branch: `git checkout -b feature/your-feature-name`
3. **Commit** your changes: `git commit -m 'Add some feature'`
4. **Push** to your branch: `git push origin feature/your-feature-name`
5. **Open** a Pull Request

---

## 📄 License

Distributed under the MIT License. See `LICENSE` for more information.

---

<div align="center">

Made with ❤️ by [Aman Kumar](https://github.com/Aman-Thewhiz)

⭐ **Star this repo if you found it useful!**

</div>
