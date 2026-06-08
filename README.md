# WorthIt - AI-Powered Spending Decision Assistant

> **The world's smartest AI financial coach for Gen Z and young adults**

WorthIt is a production-ready SaaS web platform (with future mobile apps) that helps students and young professionals make better financial decisions **before** spending money. It's not an expense tracker or budgeting app—it's an AI financial coach that feels like a responsible older sibling, mentor, and trusted advisor.

## 🎯 Mission

Help users spend intentionally instead of emotionally. Prevent regret purchases and encourage smarter financial decisions.

## 🔥 Core Differentiator

Most finance apps track what happened.  
**WorthIt predicts whether a purchase should happen.**

The main question users ask: **"Should I buy this?"**  
The AI must answer this question better than any existing product on the market.

---

## 📋 Repository Structure

```
worthit/
├── docs/                          # Complete documentation
│   ├── PRD.md                     # Product Requirements Document
│   ├── AI_ARCHITECTURE.md         # AI system design
│   ├── TECHNICAL_ARCHITECTURE.md  # Tech stack & infrastructure
│   ├── DATABASE_SCHEMA.md         # Firestore schema design
│   ├── API_DESIGN.md              # RESTful API specifications
│   ├── UI_UX_SPEC.md              # Complete UI/UX specifications
│   ├── DESIGN_SYSTEM.md           # Design language & components
│   ├── PROMPT_ENGINEERING.md      # AI prompts & behaviors
│   ├── GROWTH_STRATEGY.md         # Marketing & user acquisition
│   ├── MONETIZATION.md            # Pricing & retention
│   ├── DEVELOPMENT_ROADMAP.md     # 30-day MVP + phases
│   ├── DEPLOYMENT_GUIDE.md        # Production deployment
│   ├── INVESTOR_PITCH.md          # Pitch summary
│   └── LANDING_PAGE_COPY.md       # Website copywriting
│
├── frontend/                      # Next.js frontend application
│   ├── app/                       # Next.js App Router
│   ├── components/                # React components
│   ├── hooks/                     # Custom React hooks
│   ├── styles/                    # Tailwind CSS
│   ├── types/                     # TypeScript types
│   ├── utils/                     # Utility functions
│   ├── public/                    # Static assets
│   ├── .env.example               # Environment variables template
│   ├── package.json               # Dependencies
│   ├── tsconfig.json              # TypeScript config
│   └── tailwind.config.js         # Tailwind configuration
│
├── backend/                       # Backend services
│   ├── functions/                 # Firebase Cloud Functions
│   ├── firestore-rules/           # Firestore security rules
│   ├── config/                    # Configuration
│   ├── services/                  # Business logic services
│   │   ├── ai-service/            # AI integration service
│   │   ├── auth-service/          # Authentication service
│   │   └── analytics-service/     # Analytics service
│   ├── .env.example               # Environment variables template
│   └── README.md                  # Backend setup guide
│
├── design/                        # Design system & assets
│   ├── figma-export/              # Exported components
│   ├── typography/                # Font files
│   ├── icons/                     # SVG icons
│   ├── colors/                    # Color palette
│   └── DESIGN_TOKENS.json         # Design token definitions
│
├── scripts/                       # Utility scripts
│   ├── setup.sh                   # Development environment setup
│   ├── deploy.sh                  # Deployment script
│   └── seed-data.js               # Database seeding
│
├── .github/                       # GitHub configuration
│   ├── workflows/                 # CI/CD pipelines
│   └── ISSUE_TEMPLATE/            # Issue templates
│
├── .gitignore                     # Git ignore rules
├── LICENSE                        # MIT License
└── CONTRIBUTING.md                # Contribution guidelines
```

---

## 🚀 Quick Start

### Prerequisites
- Node.js 18+
- npm or yarn
- Firebase CLI
- Git

### Setup

```bash
# Clone repository
git clone https://github.com/5580222-max/worthit.git
cd worthit

# Run setup script
chmod +x scripts/setup.sh
./scripts/setup.sh

# Install dependencies
npm install

# Configure environment
cp frontend/.env.example frontend/.env.local
cp backend/.env.example backend/.env

# Start development server
npm run dev
```

---

## 📚 Documentation

All comprehensive documentation is in the `/docs` folder:

| Document | Purpose |
|----------|----------|
| **PRD.md** | Complete product requirements & feature specifications |
| **AI_ARCHITECTURE.md** | AI system design, models, and decision engines |
| **TECHNICAL_ARCHITECTURE.md** | Tech stack, infrastructure, and system design |
| **DATABASE_SCHEMA.md** | Firestore collections, documents, and relationships |
| **API_DESIGN.md** | REST API endpoints, payloads, and responses |
| **UI_UX_SPEC.md** | Screen-by-screen UI specifications and flows |
| **DESIGN_SYSTEM.md** | Colors, typography, components, animations |
| **PROMPT_ENGINEERING.md** | AI personality modes and prompt templates |
| **GROWTH_STRATEGY.md** | Marketing, user acquisition, viral mechanics |
| **MONETIZATION.md** | Pricing tiers, retention, and revenue models |
| **DEVELOPMENT_ROADMAP.md** | 30-day MVP and future phases |
| **DEPLOYMENT_GUIDE.md** | Production deployment and scaling |
| **INVESTOR_PITCH.md** | Executive summary and pitch materials |

---

## 🎨 Tech Stack

### Frontend
- **Framework**: Next.js 14+ (TypeScript)
- **Styling**: Tailwind CSS + Framer Motion
- **State Management**: TanStack Query + Zustand
- **UI Components**: Shadcn/ui + custom components

### Backend
- **Database**: Firebase Firestore
- **Authentication**: Firebase Auth + Google OAuth
- **Functions**: Firebase Cloud Functions (Node.js)
- **Storage**: Firebase Storage

### AI & Analytics
- **AI Models**: Gemini API + OpenAI API
- **Analytics**: Google Analytics 4
- **Monitoring**: Sentry

---

## 💰 Pricing Tiers

| Plan | Price | Users | Features |
|------|-------|-------|----------|
| **Free** | $0 | Students | 3 AI decisions/month |
| **Student** | $4.99/mo | College Students | Unlimited decisions, goal tracking |
| **Premium** | $9.99/mo | Young Professionals | Advanced analytics, multiple goals |
| **Family** | $19.99/mo | Families | Up to 5 members, shared goals |

---

## 🎮 Key Features

### MVP (30-day launch)
- ✅ Authentication (Google + Email)
- ✅ Financial profile setup
- ✅ "Should I Buy This?" calculator
- ✅ AI spending decision analysis
- ✅ Expense tracking
- ✅ Basic dashboard

### Phase 2 (Months 2-3)
- 📊 Advanced analytics
- 🎯 Savings goals with AI tracking
- 💬 AI chat companion
- 🏆 Gamification (XP, streaks, achievements)
- 📱 Mobile app alpha

### Phase 3 (Months 4-6)
- 🤖 Multiple AI personalities
- 👥 Social features & leaderboards
- 📈 Predictive financial health
- 🔄 Subscription management
- 📱 iOS & Android apps (full release)

---

## 📊 Target Users

**Primary Audience**
- College students (18-24)
- University graduates (22-28)
- Young professionals (23-32)
- First-time earners
- People on allowances
- Impulse spenders

**Common Pain Points**
- Emotional spending
- Impulse buying
- Overspending on food delivery
- Unnecessary shopping
- Poor saving habits
- No financial awareness
- FOMO purchases

---

## 🤖 AI Personality Modes

WorthIt's AI coach can adapt to different user preferences:

1. **Friendly Mentor** - Warm, supportive, encouraging
2. **Financial Advisor** - Professional, analytical, data-driven
3. **Strict Mode** - Prioritizes savings, direct feedback
4. **Student Mode** - Relatable comparisons ("18 college lunches")
5. **Future Self Mode** - Speaks from future perspective
6. **Reality Check Mode** - Brutally honest about purchases

---

## 📈 Development Status

- **Current Phase**: MVP Development
- **Target Launch**: 30 days
- **Status**: 🟡 In Progress

---

## 🤝 Contributing

We welcome contributions! Please read [CONTRIBUTING.md](./CONTRIBUTING.md) for guidelines.

---

## 📄 License

MIT License - see [LICENSE](./LICENSE) file

---

## 👨‍💼 Team

- **Founder & Product**: 5580222-max
- **Engineering Lead**: TBD
- **AI/ML Lead**: TBD
- **Design Lead**: TBD

---

## 📞 Contact & Support

- **Website**: worthit.app (coming soon)
- **Email**: hello@worthit.app
- **Twitter**: @worthit_app
- **Discord**: [Community Server]

---

## 🙏 Acknowledgments

Built with ❤️ for Gen Z and young adults who want to spend smarter.

---

**Last Updated**: June 2026  
**Version**: 1.0.0-alpha