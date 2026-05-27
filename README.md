# FinFlow - AI-Powered Personal Finance Management Application

<div align="center">

![FinFlow](https://img.shields.io/badge/FinFlow-v1.0.0-blue)
![React](https://img.shields.io/badge/React-19.1.0-61DAFB?logo=react)
![Node.js](https://img.shields.io/badge/Node.js-22.11.0-339933?logo=node.js)
![MongoDB](https://img.shields.io/badge/MongoDB-7.0-13AA52?logo=mongodb)
![License](https://img.shields.io/badge/License-MIT-green)

A comprehensive, AI-powered personal finance management system built with React, Express, MongoDB, and Groq API.

[Features](#features) • [Setup](#setup) • [Running](#running) • [Project Structure](#project-structure) • [Tech Stack](#tech-stack)

</div>

---

## 📋 Overview

FinFlow is a full-stack financial management application that helps users track expenses, manage budgets, achieve savings goals, and make informed financial decisions using AI-powered insights.

### Key Highlights
- 💰 **Transaction Management** - Track income and expenses
- 📊 **Budget Planning** - Set and monitor budgets by category
- 🤖 **AI-Powered Insights** - Get personalized financial advice using Groq API
- 📈 **Analytics & Reports** - Visualize spending patterns
- 📱 **Responsive Design** - Works on desktop and mobile
- 🔐 **Secure Authentication** - JWT-based authentication

---

## ✨ Features

### Core Features
- ✅ Add, edit, and delete transactions
- ✅ Categorize expenses (Food, Transport, Shopping, Bills, etc.)
- ✅ Set monthly, weekly, or yearly budgets
- ✅ Track recurring bills and income
- ✅ Real-time balance calculations
- ✅ Budget alerts and notifications
- ✅ Global search and filtering

### AI Features
- 🤖 Expense predictions and forecasting
- 💡 Investment recommendations
- 💼 Salary and cost of living analysis
- 🎯 Savings goal optimization
- 📊 General AI insights

### Advanced Features
- 📁 Export reports to PDF
- 📋 Receipt scanning (OCR)
- 🔄 Recurring transaction management
- 📊 Advanced analytics and charts
- 🎨 Dark/Light theme support

---

## 🛠️ Tech Stack

### Frontend
- **React** 19.1.0 - UI library
- **React Router** 7.5.2 - Navigation
- **Chart.js** 4.4.9 - Data visualization
- **Axios** 1.9.0 - HTTP client
- **React Toastify** 11.0.5 - Notifications
- **Framer Motion** 12.29.0 - Animations

### Backend
- **Express.js** 4.18.2 - REST API framework
- **MongoDB** 7.0.1 - Database
- **Mongoose** 7.0.1 - ODM
- **JWT** 9.0.0 - Authentication
- **Nodemon** 2.0.21 - Development server

### AI Service
- **Groq API** - AI model (Mixtral 8x7B)
- **Tesseract.js** 7.0.0 - OCR
- **Express.js** 4.18.2

---

## 📦 Prerequisites

Before you begin, ensure you have installed:
- **Node.js** (v14.0 or higher) - [Download](https://nodejs.org/)
- **npm** (v6.0 or higher)
- **MongoDB** (local or Atlas) - [MongoDB Compass](https://www.mongodb.com/products/compass)
- **Groq API Key** - [Get here](https://console.groq.com/)

---

## 🚀 Setup Instructions

### 1. Clone the Repository
```bash
git clone https://github.com/yourusername/finflow.git
cd finflow
```

### 2. Install Dependencies
```bash
npm install
```
This will install dependencies for frontend, server, and ai-service.

### 3. Configure Environment Variables

#### Root Directory (`.env`)
```env
MONGO_URI=mongodb://localhost:27017/expensetracker
FRONTEND_URL=http://localhost:3000
PORT=5000
GROQ_API_KEY=your_groq_api_key_here
```

#### Server Directory (`server/.env`)
```env
PORT=5000
MONGO_URI=mongodb://localhost:27017/expensetracker
FRONTEND_URL=http://localhost:3000
JWT_SECRET=your_super_secret_jwt_key_12345
```

#### AI Service Directory (`ai-service/.env`)
```env
PORT=5001
MAIN_BACKEND_URL=http://localhost:5000/api
GROQ_API_KEY=your_groq_api_key_here
```

### 4. MongoDB Setup

#### Option A: Local MongoDB
```bash
mongod
```

#### Option B: MongoDB Atlas (Cloud)
1. Create account at [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)
2. Create a cluster (free tier available)
3. Copy connection string
4. Update `MONGO_URI` in `.env` files

---

## ▶️ Running the Application

### Option 1: Run All Services Together (Recommended)
From the root directory:
```bash
npm run dev
```

This starts all three services concurrently using `concurrently`:
- **Frontend:** http://localhost:3000
- **Backend:** http://localhost:5000
- **AI Service:** http://localhost:5001

### Option 2: Run Services Individually
Open 3 separate terminals:

**Terminal 1 - Backend:**
```bash
cd server
npm run dev
```

**Terminal 2 - AI Service:**
```bash
cd ai-service
npm run dev
```

**Terminal 3 - Frontend:**
```bash
cd frontend
npm start
```

### Option 3: Production Build
```bash
cd frontend
npm run build
```

---

## 📁 Project Structure

```
finflow/
├── frontend/                 # React frontend application
│   ├── public/
│   ├── src/
│   │   ├── components/      # Reusable components
│   │   ├── pages/           # Page components
│   │   ├── services/        # API services
│   │   ├── context/         # Context API
│   │   ├── App.js
│   │   └── index.js
│   ├── package.json
│   └── README.md
│
├── server/                   # Express backend
│   ├── config/              # Database config
│   ├── controllers/         # Route handlers
│   ├── middleware/          # Custom middleware
│   ├── models/              # MongoDB schemas
│   ├── routes/              # API routes
│   ├── utils/               # Utility functions
│   ├── server.js
│   ├── package.json
│   └── .env
│
├── ai-service/              # Groq AI service
│   ├── controllers/         # AI logic
│   ├── routes/              # AI endpoints
│   ├── services/            # Groq integration
│   ├── server.js
│   ├── package.json
│   └── .env
│
├── package.json             # Root package.json
├── REAL_WORLD_DIFFERENCES.md # Differences with production apps
└── README.md               # This file
```

---

## 🔌 API Endpoints

### Authentication
- `POST /api/users/register` - Register new user
- `POST /api/users/login` - Login user
- `GET /api/users/profile` - Get user profile

### Transactions
- `GET /api/transactions` - Get all transactions
- `POST /api/transactions` - Create transaction
- `PUT /api/transactions/:id` - Update transaction
- `DELETE /api/transactions/:id` - Delete transaction

### Budgets
- `GET /api/budgets` - Get all budgets
- `POST /api/budgets` - Create budget
- `PUT /api/budgets/:id` - Update budget

### AI Service
- `POST /api/ai/expense-prediction` - Predict expenses
- `POST /api/ai/investment-advice` - Get investment advice
- `POST /api/ai/salary-analysis` - Analyze salary
- `POST /api/ai/insights` - Get general insights

See [API Documentation](./API.md) for detailed endpoints.

---

## 🔐 Getting Groq API Key

1. Visit [Groq Console](https://console.groq.com/)
2. Sign up or log in
3. Navigate to API Keys section
4. Create a new API key
5. Copy the key and add to `.env` files:
   ```env
   GROQ_API_KEY=your_key_here
   ```

---

## 🧪 Testing

### Run Tests
```bash
cd frontend
npm test

cd server
npm test
```

### Lint Code
```bash
npm run lint
```

---

## 🚢 Deployment

### Frontend
```bash
npm run build
# Deploy 'build' folder to Vercel, Netlify, or similar
```

### Backend
```bash
# Deploy to Heroku, Railway, AWS, or similar
git push heroku main
```

### Docker
```bash
docker-compose up --build
```

---

## 📊 Database Schema

### User Model
```javascript
{
  _id: ObjectId,
  email: String,
  password: String (hashed),
  name: String,
  createdAt: Date,
  updatedAt: Date
}
```

### Transaction Model
```javascript
{
  _id: ObjectId,
  userId: ObjectId (ref: User),
  title: String,
  amount: Number,
  category: String,
  date: Date,
  type: String (income/expense),
  createdAt: Date
}
```

### Budget Model
```javascript
{
  _id: ObjectId,
  userId: ObjectId,
  category: String,
  limit: Number,
  frequency: String (monthly/weekly/yearly),
  createdAt: Date
}
```

---

## 🔄 Development Workflow

1. **Create Feature Branch**
   ```bash
   git checkout -b feature/your-feature
   ```

2. **Make Changes**
   - Modify code
   - Test thoroughly
   - Commit changes

3. **Create Pull Request**
   ```bash
   git push origin feature/your-feature
   ```

4. **Merge to Main**
   - Code review
   - Merge to main branch

---

## 🐛 Troubleshooting

### Port Already in Use
```bash
# Find process using port
netstat -ano | findstr :5000

# Kill process
taskkill /PID <PID> /F
```

### MongoDB Connection Error
```bash
# Check MongoDB is running
mongod

# Or use MongoDB Compass to verify connection
```

### react-scripts Not Found
```bash
cd frontend
npm install react-scripts@5.0.1
npm start
```

### JWT Secret Error
```bash
# Add JWT_SECRET to server/.env
JWT_SECRET=your_random_secret_key_here
```

---

## 📚 Documentation

- [Feature Roadmap](./FEATURE_ROADMAP.md)
- [Project Description](./PROJECT_DESCRIPTION.txt)
- [Real-World Differences](./REAL_WORLD_DIFFERENCES.md)
- [API Documentation](./API.md) (if available)

---

## 🤝 Contributing

Contributions are welcome! Here's how:

1. **Fork the repository**
2. **Create feature branch** (`git checkout -b feature/AmazingFeature`)
3. **Commit changes** (`git commit -m 'Add AmazingFeature'`)
4. **Push to branch** (`git push origin feature/AmazingFeature`)
5. **Open Pull Request**

### Code Standards
- Use ES6+ syntax
- Follow existing code style
- Add comments for complex logic
- Test your changes
- Update README if needed

---

## 📄 License

This project is licensed under the MIT License - see [LICENSE](./LICENSE) file for details.

---

## 👨‍💻 Author

**Your Name**
- GitHub: https://github.com/Gowrav19
- Email: vungowrav19@gmail.com

---

## 🙏 Acknowledgments

- **Groq API** - AI model provider
- **MongoDB** - Database
- **React** - Frontend framework
- **Express.js** - Backend framework

---

## 📞 Support

For issues and questions:
- Open an [Issue](https://github.com/Gowrav19/finflow/issues)
- Start a [Discussion](https://github.com/Gowrav19/finflow/discussions)
- Email: support@finflow.com

---

## 🗺️ Roadmap

- [ ] Mobile app (React Native)
- [ ] Bank integration
- [ ] Investment portfolio tracking
- [ ] Multi-currency support
- [ ] Social features (split expenses)
- [ ] Advanced ML models
- [ ] API marketplace

---

## 📈 Project Stats

- **Lines of Code:** 2000+
- **Components:** 20+
- **API Endpoints:** 15+
- **Database Collections:** 5+
- **AI Features:** 5+

---

<div align="center">



</div>
