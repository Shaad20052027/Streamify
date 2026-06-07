# Streamify 🎥💬

> Full-stack real-time video calling and chat application

**Live App:** [streamify-three-rouge.vercel.app](https://streamify-three-rouge.vercel.app) &nbsp;|&nbsp; **API:** [streamify-backend-8kp5.onrender.com](https://streamify-backend-8kp5.onrender.com)

---

## What is Streamify?

Streamify is a full-stack real-time communication app where users can send friend requests, chat one-on-one, and start live video calls — all in a single platform. Built with the MERN stack and powered by the Stream API for low-latency video and chat infrastructure.

---

## Features

- **One-on-one video calling** — real-time video calls powered by Stream Video SDK
- **Live chat** — instant messaging with Stream Chat SDK
- **Friend request system** — send, accept, and manage friend requests
- **JWT authentication** — secure register/login with protected routes
- **Global state management** — Zustand for lightweight, fast client state
- **Server state management** — TanStack Query for caching, refetching, and API sync
- **Responsive UI** — built with DaisyUI + Tailwind CSS

---

## Tech Stack

### Frontend
- React 18 + Vite
- Tailwind CSS + DaisyUI
- Zustand (global state)
- TanStack Query (server state + caching)
- Stream Chat React SDK
- Stream Video React SDK
- React Router v6
- Axios

### Backend
- Node.js + Express
- MongoDB Atlas + Mongoose
- JSON Web Tokens (JWT)
- bcryptjs
- Stream API (server-side token generation)

### Deployment
- Frontend → Vercel
- Backend → Render
- Database → MongoDB Atlas

---

## Screenshots

> Add screenshots here after uploading to `/screenshots` folder

---

## Getting Started Locally

### Prerequisites
- Node.js 18+
- MongoDB Atlas account (free)
- Stream account — [getstream.io](https://getstream.io) (free tier)

### 1. Clone the repo
```bash
git clone https://github.com/Shaad20052027/Streamify.git
cd Streamify
```

### 2. Backend setup
```bash
cd backend
cp .env.example .env
npm install
npm run dev
```

Fill in `backend/.env`:
```env
MONGO_URI=your_mongodb_atlas_connection_string
JWT_SECRET=your_jwt_secret_key
STREAM_API_KEY=your_stream_api_key
STREAM_API_SECRET=your_stream_api_secret
CLIENT_URL=http://localhost:5173
PORT=5000
```

### 3. Frontend setup
```bash
cd frontend
cp .env.example .env
npm install
npm run dev
```

Fill in `frontend/.env`:
```env
VITE_API_URL=http://localhost:5000/api
VITE_STREAM_API_KEY=your_stream_api_key
```

Open `http://localhost:5173`

---

## API Endpoints

| Method | Endpoint | Description | Auth |
|--------|----------|-------------|------|
| POST | `/api/auth/register` | Register new user | ❌ |
| POST | `/api/auth/login` | Login user | ❌ |
| GET | `/api/auth/me` | Get current user | ✅ |
| GET | `/api/users` | Get all users | ✅ |
| POST | `/api/friends/request/:id` | Send friend request | ✅ |
| PUT | `/api/friends/accept/:id` | Accept friend request | ✅ |
| GET | `/api/friends` | Get friends list | ✅ |
| GET | `/api/stream/token` | Get Stream chat/video token | ✅ |

---

## How It Works

```
User logs in → JWT issued → Stream token generated server-side
        ↓
User connects to Stream Chat + Stream Video with token
        ↓
Friend request sent → accepted → chat channel created
        ↓
One-on-one chat via Stream Chat SDK (real-time, persistent)
One-on-one video call via Stream Video SDK (WebRTC)
        ↓
TanStack Query syncs friend list + requests in background
Zustand manages auth state + UI state globally
```

---

## Project Structure

```
Streamify/
├── frontend/
│   ├── src/
│   │   ├── pages/
│   │   │   ├── HomePage.jsx
│   │   │   ├── LoginPage.jsx
│   │   │   ├── SignUpPage.jsx
│   │   │   ├── ChatPage.jsx
│   │   │   └── CallPage.jsx
│   │   ├── components/
│   │   ├── store/           ← Zustand store
│   │   ├── hooks/           ← TanStack Query hooks
│   │   └── lib/
│   │       └── api.js       ← Axios instance
│   └── package.json
│
└── backend/
    ├── models/
    │   └── User.js
    ├── routes/
    │   ├── auth.js
    │   ├── users.js
    │   ├── friends.js
    │   └── stream.js
    ├── middleware/
    │   └── authMiddleware.js
    └── server.js
```

---

## Author

**Mohd Shaad Siddiqui**
- GitHub: [@Shaad20052027](https://github.com/Shaad20052027)
- LinkedIn: [mohd-shaad-siddiqui](https://www.linkedin.com/in/mohd-shaad-siddiqui-797a9a329/)

---

## License

MIT
