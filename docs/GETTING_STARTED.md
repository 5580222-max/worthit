# WorthIt - Complete Getting Started Guide

**Version**: 1.0.0
**Last Updated**: June 2026

---

## 🚀 Quick Start (5 Minutes)

### 1. Clone Repository
```bash
git clone https://github.com/5580222-max/worthit.git
cd worthit
```

### 2. Setup Frontend
```bash
cd frontend
npm install
cp .env.example .env.local
npm run dev
```
Open http://localhost:3000

### 3. Setup Backend
```bash
cd ../backend/functions
npm install
firebase login
firebase deploy
```

---

## 📋 Complete Setup

### Prerequisites
- Node.js 18+
- npm/yarn
- Firebase account
- Git

### Full Installation

#### Frontend Setup
```bash
cd frontend

# Install dependencies
npm install

# Configure environment
cp .env.example .env.local

# Fill in Firebase credentials in .env.local
NEXT_PUBLIC_FIREBASE_API_KEY=your_key
NEXT_PUBLIC_FIREBASE_PROJECT_ID=worthit-dev
# ... (see .env.example for full list)

# Start development server
npm run dev
```

#### Backend Setup
```bash
cd backend/functions

# Install dependencies
npm install

# Configure environment
cp .env.example .env

# Fill in credentials
FIREBASE_PROJECT_ID=worthit-dev
GEMINI_API_KEY=your_key
# ... (see .env.example)

# Build TypeScript
npm run build

# Deploy to Firebase
firebase deploy --only functions
```

---

## 📚 Documentation Navigation

### For Different Roles

**Product Manager**
- Start with: `docs/PRD.md`
- Then: `docs/DEVELOPMENT_ROADMAP.md`
- Reference: `docs/INVESTOR_PITCH.md`

**Designer/UI Developer**
- Start with: `docs/DESIGN_SYSTEM.md`
- Then: `docs/UI_UX_SPEC.md`
- Reference: Component library in `frontend/components/`

**Frontend Developer**
- Start with: `docs/FRONTEND_SETUP.md`
- Then: `docs/API_DESIGN.md`
- Reference: `docs/TECHNICAL_ARCHITECTURE.md`

**Backend Developer**
- Start with: `docs/BACKEND_SETUP.md`
- Then: `docs/DATABASE_SCHEMA.md`
- Reference: `docs/AI_ARCHITECTURE.md`

**DevOps Engineer**
- Start with: `docs/DEPLOYMENT_GUIDE.md`
- Reference: `docs/TECHNICAL_ARCHITECTURE.md`

---

## 🎯 Key Features

### 1. "Should I Buy This?" AI Coach
- Real-time purchase decision analysis
- Multiple AI personality modes
- Emotional spending detection
- Goal impact calculation

### 2. Expense Tracking
- Quick add expenses
- Category management
- Monthly summaries
- Budget comparison

### 3. Budget Management
- Set category budgets
- Real-time tracking
- Alert notifications
- Performance analytics

### 4. Savings Goals
- Create multiple goals
- Track progress
- Milestone celebrations
- Goal recommendations

### 5. Financial Analytics
- Spending patterns
- Category breakdowns
- Trend analysis
- Comparative insights

---

## 🏗️ Project Structure

```
worthit/
├── frontend/               # Next.js application
│   ├── app/              # Pages and layouts
│   ├── components/       # React components
│   ├── hooks/            # Custom hooks
│   ├── lib/              # Utilities
│   ├── styles/           # CSS
│   ├── types/            # TypeScript types
│   ├── utils/            # Helper functions
│   └── public/           # Static files
├── backend/
│   └── functions/        # Firebase Cloud Functions
│       ├── src/
│       │   ├── services/    # Business logic
│       │   ├── controllers/ # Route handlers
│       │   ├── middlewares/ # Express middleware
│       │   ├── models/      # Data models
│       │   └── config/      # Configuration
│       └── firestore-rules/ # Security rules
├── design/               # Design system files
├── docs/                 # Complete documentation
│   ├── PRD.md           # Product requirements
│   ├── TECHNICAL_ARCHITECTURE.md
│   ├── DATABASE_SCHEMA.md
│   ├── API_DESIGN.md
│   ├── AI_ARCHITECTURE.md
│   ├── DESIGN_SYSTEM.md
│   ├── UI_UX_SPEC.md
│   ├── DEVELOPMENT_ROADMAP.md
│   ├── DEPLOYMENT_GUIDE.md
│   ├── FRONTEND_SETUP.md
│   ├── BACKEND_SETUP.md
│   ├── QUICK_START.md
│   ├── INVESTOR_PITCH.md
│   └── INDEX.md
├── scripts/              # Utility scripts
├── .github/              # GitHub workflows
├── .gitignore
├── LICENSE
├── README.md
└── CONTRIBUTING.md
```

---

## 🛠️ Available Commands

### Frontend
```bash
npm run dev              # Start dev server
npm run build            # Build for production
npm run start            # Start production server
npm run lint             # Run ESLint
npm run type-check       # TypeScript check
npm run format           # Format code with Prettier
```

### Backend
```bash
npm run build            # Build TypeScript
npm run serve            # Start emulator
npm run deploy           # Deploy to Firebase
npm run logs             # View logs
```

---

## 🔑 Environment Setup

### Firebase Console Setup
1. Go to https://console.firebase.google.com
2. Create new project: "worthit"
3. Enable these services:
   - Firestore Database
   - Cloud Functions
   - Firebase Storage
   - Firebase Authentication

### Get Credentials
1. Project Settings → Service Accounts
2. Copy config values
3. Paste into `.env.local` and `.env`

### Enable OAuth
1. Authentication → Sign-in method
2. Enable Google sign-in
3. Add authorized domains

---

## 📖 Full Documentation

All documentation is in the `docs/` folder:

| Document | Purpose |
|----------|---------|
| INDEX.md | Navigation guide |
| PRD.md | Product requirements |
| TECHNICAL_ARCHITECTURE.md | System design |
| DATABASE_SCHEMA.md | Data structure |
| API_DESIGN.md | API endpoints |
| AI_ARCHITECTURE.md | Decision engine |
| DESIGN_SYSTEM.md | Design tokens |
| UI_UX_SPEC.md | Screen specs |
| FRONTEND_SETUP.md | Frontend dev guide |
| BACKEND_SETUP.md | Backend dev guide |
| DEVELOPMENT_ROADMAP.md | Timeline |
| DEPLOYMENT_GUIDE.md | Production deployment |
| QUICK_START.md | User guide |
| INVESTOR_PITCH.md | Business pitch |

---

## 🚀 Deployment

### Vercel (Frontend)
```bash
# Login
vercel login

# Deploy
vercel --prod
```

### Firebase (Backend)
```bash
# Deploy
firebase deploy --only functions,firestore

# View status
firebase projects:describe
```

See `docs/DEPLOYMENT_GUIDE.md` for full instructions.

---

## 🧪 Testing

```bash
# Frontend tests
cd frontend
npm test

# Backend tests
cd ../backend/functions
npm test
```

---

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/your-feature`
3. Commit changes: `git commit -m "feat: your feature"`
4. Push to branch: `git push origin feature/your-feature`
5. Open Pull Request

See `CONTRIBUTING.md` for full guidelines.

---

## 📊 Project Stats

- **Documentation**: 14 comprehensive guides
- **Lines of Documentation**: 10,000+
- **API Endpoints**: 25+
- **Firestore Collections**: 8
- **UI Components**: 20+
- **Cloud Functions**: 15+

---

## 🎓 Learning Path

### Week 1: Understand the Vision
- [ ] Read PRD.md
- [ ] Read INVESTOR_PITCH.md
- [ ] Review DESIGN_SYSTEM.md

### Week 2: Technical Foundation
- [ ] Read TECHNICAL_ARCHITECTURE.md
- [ ] Read DATABASE_SCHEMA.md
- [ ] Read API_DESIGN.md

### Week 3: Development
- [ ] Setup frontend locally
- [ ] Setup backend locally
- [ ] Create first feature

### Week 4: Deployment
- [ ] Deploy to Vercel
- [ ] Deploy to Firebase
- [ ] Monitor production

---

## 💡 Key Concepts

### "Should I Buy This?" Engine
Core innovation: AI analyzes purchases BEFORE spending using:
- Financial health metrics
- Behavioral psychology
- Goal impact analysis
- Real-time recommendations

### Personality Modes
AI coach adapts to user preference:
- Friendly Mentor
- Financial Advisor
- Strict Mode
- Student Mode
- Future Self
- Reality Check

### Free for Everyone
WorthIt is completely free to use. No paywalls, no premium features. All features available to all users.

---

## 🐛 Troubleshooting

### Port Already in Use
```bash
# Use different port
npm run dev -- -p 3001

# Or kill process
lsof -i :3000
kill -9 <PID>
```

### Firebase Connection Error
- Check credentials in .env
- Verify Firebase project exists
- Check network connectivity
- Review Firestore rules

### AI API Error
- Verify API keys in .env
- Check API rate limits
- Review error logs in Sentry
- Contact API provider support

---

## 📞 Support

**Email**: hello@worthit.app
**GitHub Issues**: https://github.com/5580222-max/worthit/issues
**Documentation**: /docs folder

---

## 📈 What's Next?

### Immediate (Week 1-2)
- [ ] Setup development environment
- [ ] Read core documentation
- [ ] Run locally and test
- [ ] Understand codebase

### Short-term (Week 3-4)
- [ ] Deploy to staging
- [ ] Create first feature
- [ ] Write tests
- [ ] Submit PR

### Medium-term (Month 2+)
- [ ] Scale infrastructure
- [ ] Add mobile app
- [ ] Expand features
- [ ] Grow user base

---

## 📄 License

MIT License - See LICENSE file

---

## 🙏 Acknowledgments

Built with ❤️ for Gen Z and young adults who want to spend smarter.

---

**Welcome to WorthIt! Let's build the future of personal finance. 🚀**

**Last Updated**: June 2026
**Version**: 1.0.0
