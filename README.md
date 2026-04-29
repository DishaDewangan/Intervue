# 🤖 Intervue — AI-Powered Interview Agent

![MongoDB](https://img.shields.io/badge/MongoDB-Database-47A248?style=flat&logo=mongodb)
![Express](https://img.shields.io/badge/Express.js-Backend-000000?style=flat&logo=express)
![React](https://img.shields.io/badge/React.js-Frontend-61DAFB?style=flat&logo=react)
![Node](https://img.shields.io/badge/Node.js-Runtime-339933?style=flat&logo=node.js)
![Redux](https://img.shields.io/badge/Redux-Toolkit-764ABC?style=flat&logo=redux)
![Firebase](https://img.shields.io/badge/Firebase-Google%20Auth-FFCA28?style=flat&logo=firebase)
![Razorpay](https://img.shields.io/badge/Razorpay-Payments-02042B?style=flat&logo=razorpay)
![Framer](https://img.shields.io/badge/Framer-Motion-0055FF?style=flat&logo=framer)
![Render](https://img.shields.io/badge/Deployed-Render-46E3B7?style=flat&logo=render)

> A production-ready, SaaS-style AI Interview Agent that analyzes your resume, generates personalized interview questions, conducts Technical & HR rounds, and delivers intelligent feedback — all powered by AI. Built with the **MERN Stack**.

🚀 **Live Demo:** _Coming Soon_
🐙 **GitHub:** _Coming Soon_

---

## 📌 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Project Pipeline](#project-pipeline)
- [API Endpoints](#api-endpoints)
- [Setup & Installation](#setup--installation)
- [Deployment](#deployment)
- [Key Implementations](#key-implementations)

---

## 📖 Overview

**Intervue** is a next-generation AI Interview Agent built from scratch using the MERN stack. It goes far beyond a basic CRUD app — users upload their resume (PDF), and the AI analyzes it to generate tailored interview questions for both Technical and HR rounds. A credit-based monetization system powered by Razorpay allows users to purchase access, making it a fully functional SaaS product ready for real-world deployment.

---

## ✨ Features

### 👤 For Users
- Upload resume in **PDF format** for AI analysis
- Receive **AI-generated interview questions** tailored to your resume
- Practice both **Technical and HR interview rounds**
- Get **intelligent AI feedback** after each session
- View complete **interview history and reports**
- Purchase **credits via Razorpay** to unlock sessions

### 🤖 AI Capabilities
- **Resume analysis** using OpenRouter AI integration
- **Context-aware question generation** based on resume content
- **Smart feedback** on user responses during practice sessions
- Supports multi-step interview flow (Setup → Interview → Report)

### 💳 Credit-Based System
- Users start with a limited number of free credits
- Additional credits purchasable via **Razorpay payment gateway**
- Each interview session consumes credits, enabling SaaS monetization

### 🔐 Authentication & Security
- One-click **Firebase Google Authentication**
- JWT-based middleware for protected API routes
- Role-based access control
- Secure session management

### 🎨 UI / UX
- Smooth, production-grade animations with **Framer Motion**
- Clean and modern responsive design with **Tailwind CSS**
- Multi-step interview flow with intuitive UX
- Mobile-friendly across all screen sizes

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|------------|
| **Frontend** | React.js (Vite), Redux Toolkit, React Router, Tailwind CSS, Framer Motion, Axios |
| **Backend** | Node.js, Express.js, Mongoose, JWT, Multer |
| **Database** | MongoDB |
| **Auth** | Firebase (Google OAuth) |
| **AI** | OpenRouter API (Resume Analysis + Question Generation) |
| **Payments** | Razorpay (Credit Purchase) |
| **Deployment** | Render |

---

## 📂 Project Structure

```
Intervue/
│
├── server/
│   ├── controllers/       # Route logic (user, interview, payment)
│   ├── middleware/        # isAuth guard, Multer file upload
│   ├── models/            # Mongoose schemas (User, Interview, Session)
│   ├── routes/            # API route definitions
│   ├── utils/             # OpenRouter config, helpers
│   └── index.js           # Server entry point
│
├── client/
│   ├── src/
│   │   ├── components/    # Reusable UI (Navbar, Footer, StepCards)
│   │   ├── redux/         # Redux store & slices (auth, interview)
│   │   ├── pages/         # Route-level pages (Home, Interview, Pricing, History)
│   │   └── App.jsx
│   └── package.json
│
└── README.md
```

---

## 🔄 Project Pipeline

```
User visits Intervue
       ↓
Firebase Google Sign-In (JWT issued)
       ↓
Credit Check (Free / Purchased via Razorpay)
       ↓
┌──────────────────────────────────────────────┐
│  Step 1: Setup                               │
│  Upload Resume (PDF) → AI Analyzes Resume    │
│                ↓                             │
│  Step 2: Interview                           │
│  AI Generates Questions → User Answers       │
│                ↓                             │
│  Step 3: Report                              │
│  AI Feedback + Score + History Saved         │
└──────────────────────────────────────────────┘
       ↓
Redux State persisted across all pages
       ↓
MongoDB ← REST API → React UI
       ↓
OpenRouter (AI) + Razorpay (Credits) + Firebase (Auth)
```

---

## 🔌 API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/v1/user/google-auth` | Firebase Google sign-in |
| GET | `/api/v1/user/me` | Get current authenticated user |
| POST | `/api/v1/interview/analyze` | Upload resume & get AI analysis |
| POST | `/api/v1/interview/create` | Create new interview session |
| POST | `/api/v1/interview/feedback` | Get AI feedback on answers |
| GET | `/api/v1/interview/history` | Get user's interview history |
| GET | `/api/v1/interview/report/:id` | Get detailed interview report |
| POST | `/api/v1/payment/order` | Create Razorpay credit order |
| POST | `/api/v1/payment/verify` | Verify payment & add credits |
| GET | `/api/v1/payment/credits` | Get user's current credit balance |

> 10+ REST API endpoints total across User, Interview, and Payment routes.

---

## ⚙️ Setup & Installation

**1. Clone the repository**
```bash
git clone https://github.com/DishaDewangan/Intervue.git
cd Intervue
```

**2. Backend Setup**
```bash
cd server
npm install
```

Create a `.env` file in the `server/` directory:
```env
PORT=8000
MONGO_URI=your_mongodb_connection_string
SECRET_KEY=your_jwt_secret_key
OPENROUTER_API_KEY=your_openrouter_api_key
RAZORPAY_KEY_ID=your_razorpay_key_id
RAZORPAY_KEY_SECRET=your_razorpay_key_secret
FIREBASE_PROJECT_ID=your_firebase_project_id
FIREBASE_PRIVATE_KEY=your_firebase_private_key
FIREBASE_CLIENT_EMAIL=your_firebase_client_email
```

Start the backend:
```bash
npm run dev
```

**3. Frontend Setup**
```bash
cd client
npm install
```

Create a `.env` file in the `client/` directory:
```env
VITE_API_URL=http://localhost:8000/api/v1
VITE_RAZORPAY_KEY_ID=your_razorpay_key_id
VITE_FIREBASE_API_KEY=your_firebase_api_key
VITE_FIREBASE_AUTH_DOMAIN=your_firebase_auth_domain
VITE_FIREBASE_PROJECT_ID=your_firebase_project_id
```

Start the frontend:
```bash
npm run dev
```

---

## 🚀 Deployment

The application is deployed on **Render** (both frontend and backend).

To deploy your own instance:
1. Create a [Render](https://render.com) account
2. Connect your GitHub repository
3. Configure all environment variables in the Render dashboard
4. Deploy `server/` and `client/` as separate services
5. Update `VITE_API_URL` in the frontend `.env` to point to your live backend URL

---

## ✅ Key Implementations

| Feature | Status |
|---------|--------|
| Firebase Google Authentication | ✅ |
| JWT middleware-protected routes | ✅ |
| Resume upload via Multer (PDF) | ✅ |
| AI resume analysis (OpenRouter) | ✅ |
| AI interview question generation | ✅ |
| AI feedback on user answers | ✅ |
| Multi-step interview flow | ✅ |
| Interview history & report page | ✅ |
| Credit-based access system | ✅ |
| Razorpay payment integration | ✅ |
| Redux state management | ✅ |
| Framer Motion animations | ✅ |
| Protected routes | ✅ |
| Responsive design | ✅ |
| Production deployment on Render | ✅ |

---

## 👩‍💻 Author

**Disha Dewangan**
[![GitHub](https://img.shields.io/badge/GitHub-DishaDewangan-black?style=flat&logo=github)](https://github.com/DishaDewangan)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Disha%20Dewangan-blue?style=flat&logo=linkedin)](https://www.linkedin.com/in/disha-dewangan-9a0071291/)
[![LeetCode](https://img.shields.io/badge/LeetCode-DishaDewangan-orange?style=flat&logo=leetcode)](https://leetcode.com/DishaDewangan/)

---

If this project helped you, consider giving it a ⭐!
