💰 FinanceAI — AI-Powered Personal Finance Dashboard
A full-stack web application with React, Node.js, MongoDB, and Python ML service for intelligent personal finance management.

🚀 Quick Start
Prerequisites
Node.js v18+
Python 3.9+
MongoDB Atlas account (free)
📦 Setup Instructions
Step 1 — Clone and Install
# Install backend dependencies
cd backend
npm install

# Install frontend dependencies
cd ../frontend
npm install

# Install ML service dependencies
cd ../ml-service
pip install -r requirements.txt
Step 2 — Configure Environment
Copy the example env file:

cd backend
cp .env.example .env
Edit backend/.env and fill in:

MONGO_URI=mongodb+srv://user:pass@cluster0.xxx.mongodb.net/finance_dashboard
JWT_SECRET=make_this_very_long_random_string
JWT_REFRESH_SECRET=another_very_long_random_string
CLIENT_URL=http://localhost:3000
EMAIL_USER=your_gmail@gmail.com
EMAIL_PASS=your_gmail_app_password
Getting MongoDB URI:

Go to https://mongodb.com/atlas → Create free account
Create M0 free cluster
Database Access → Add User
Network Access → Allow from anywhere
Connect → Compass → Copy URI
Getting Gmail App Password:

Google Account → Security → 2-Step Verification (enable)
App passwords → Generate password for "Mail"
Step 3 — Run All Services
Terminal 1 — Backend:

cd backend
npm run dev
# Running on http://localhost:5000
Terminal 2 — ML Service:

cd ml-service
uvicorn main:app --reload --port 8000
# Running on http://localhost:8000
Terminal 3 — Frontend:

cd frontend
npm start
# Running on http://localhost:3000
🌐 Access the App
Open http://localhost:3000 in your browser.

Register a new account and start adding transactions!

✨ Features
Authentication — Register, login, JWT tokens, password reset via email
Transactions — Add, edit, delete, CSV import, search & filter
Dashboard — Income vs expenses charts, spending breakdown, recent activity
Budget — Set monthly limits per category with progress tracking
Goals — Savings goals with progress tracking
Analytics — AI forecasting, anomaly detection, spending insights
Settings — Profile management, currency selection
📁 Project Structure
finance-dashboard/
├── backend/              # Node.js + Express API
│   ├── config/           # Database connection
│   ├── controllers/      # Route handlers
│   ├── middleware/       # Auth & error handling
│   ├── models/           # MongoDB schemas
│   ├── routes/           # API routes
│   └── server.js
├── frontend/             # React app
│   └── src/
│       ├── components/   # Reusable UI components
│       ├── context/      # Auth context
│       ├── pages/        # All pages
│       └── services/     # API service
├── ml-service/           # Python FastAPI ML service
│   ├── routers/          # ML endpoints
│   └── main.py
└── docker-compose.yml
🔌 API Endpoints
Auth
POST /api/auth/register — Register
POST /api/auth/login — Login
POST /api/auth/logout — Logout
GET /api/auth/me — Get current user
POST /api/auth/forgot-password — Request reset
PUT /api/auth/reset-password/:token — Reset password
Transactions
GET /api/transactions — Get all (with filters & pagination)
POST /api/transactions — Add transaction
PUT /api/transactions/:id — Update
DELETE /api/transactions/:id — Delete
POST /api/transactions/upload-csv — Import CSV
GET /api/transactions/stats — Dashboard stats
Budget
GET /api/budgets — Get budgets
POST /api/budgets — Create/update budget
DELETE /api/budgets/:id — Delete budget
Goals
GET /api/goals — Get goals
POST /api/goals — Create goal
PUT /api/goals/:id — Update goal
DELETE /api/goals/:id — Delete goal
ML Service
GET /api/ml/forecast — Expense forecasting
GET /api/ml/anomalies — Anomaly detection
GET /api/ml/insights — AI insights
POST /api/ml/categorize — Categorize descriptions
🚀 Deployment
Frontend → Vercel
Push to GitHub
Connect to Vercel
Set env: REACT_APP_API_URL=https://your-backend.render.com/api
Backend → Render
New Web Service → Connect GitHub
Build: npm install, Start: node server.js
Add all environment variables
ML Service → Render
New Web Service → Python runtime
Build: pip install -r requirements.txt
Start: uvicorn main:app --host 0.0.0.0 --port 8000
