# Student Lounge BD

A full-stack learning platform for Bangladeshi students in grades 9-12.

## Structure
- `/client` — React frontend with Tailwind CSS
- `/server` — Node.js + Express backend with MongoDB, Firebase Auth, Socket.io

## Local setup
1. Install dependencies:
   - `npm install`
2. Copy `server/.env.example` to `server/.env` and add your MongoDB and Firebase admin keys.
3. Copy `client/.env.example` to `client/.env` and add your Firebase client config.
4. Start development:
   - `npm run dev`

## Local URLs
- Frontend: `http://localhost:5173`
- Backend: `http://localhost:5000`
- Status endpoint: `http://localhost:5000/api/status`

## Deployment
### Backend on Render
This repo includes a `render.yaml` service definition for the backend.

Required Render environment variables:
- `MONGODB_URI`
- `JWT_SECRET`
- `FIREBASE_PROJECT_ID`
- `FIREBASE_CLIENT_EMAIL`
- `FIREBASE_PRIVATE_KEY`
- `FIREBASE_STORAGE_BUCKET`
- `PORT` (optional, defaults to `5000`)

After Render deploys the backend, set `VITE_API_BASE_URL` in the frontend build environment or `client/.env` to the Render service URL plus `/api`.

Example:
- `VITE_API_BASE_URL=https://student-lounge-bd-api.onrender.com/api`

### Frontend production
If the frontend is hosted separately (Firebase Hosting, Vercel, etc.), the build must know the backend base URL.
Set `VITE_API_BASE_URL` to the backend API host before building the frontend.

## Backend
- Express API routes for auth, users, notes, blogs, tutors, messages, groups
- Mongoose models for User, Note, Blog, Tutor, Message, Group
- Firebase Auth token verification and profile synchronization
- Socket.io for real-time messaging

## Notes
- The backend can start without MongoDB configured, but full data functionality requires `MONGODB_URI`.
