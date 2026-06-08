# WorthIt - Frontend Setup Guide

**Version**: 1.0.0
**Last Updated**: June 2026

---

## Project Structure

```
frontend/
├── app/
│   ├── (auth)/
│   │   ├── login/
│   │   ├── signup/
│   │   └── forgot-password/
│   ├── (dashboard)/
│   │   ├── dashboard/
│   │   ├── ai-coach/
│   │   ├── expenses/
│   │   ├── budgets/
│   │   ├── goals/
│   │   ├── analytics/
│   │   └── settings/
│   ├── api/
│   ├── layout.tsx
│   └── page.tsx
├── components/
│   ├── auth/
│   ├── dashboard/
│   ├── expenses/
│   ├── budgets/
│   ├── goals/
│   ├── ai-coach/
│   └── common/
├── hooks/
├── lib/
├── styles/
├── types/
├── utils/
├── public/
├── package.json
├── tsconfig.json
├── tailwind.config.js
├── next.config.js
└── .env.example
```

---

## Installation

### Step 1: Install Dependencies

```bash
cd frontend

# Install core packages
npm install next@latest react@latest react-dom@latest typescript

# Install styling
npm install -D tailwindcss postcss autoprefixer
npm install framer-motion

# Install UI components
npm install clsx class-variance-authority

# Install forms & validation
npm install react-hook-form zod @hookform/resolvers

# Install state management
npm install zustand
npm install @tanstack/react-query

# Install API & auth
npm install axios firebase firebase-admin

# Install charts & visualization
npm install recharts

# Install utilities
npm install date-fns lodash-es uuid

# Install dev tools
npm install -D @types/node @types/react eslint eslint-config-next prettier
```

---

## Core Configuration

### TypeScript Setup (`tsconfig.json`)

```json
{
  "compilerOptions": {
    "target": "ES2020",
    "useDefineForClassFields": true,
    "lib": ["ES2020", "DOM", "DOM.Iterable"],
    "module": "ESNext",
    "skipLibCheck": true,
    "esModuleInterop": true,
    "allowSyntheticDefaultImports": true,
    "strict": true,
    "noUnusedLocals": true,
    "noUnusedParameters": true,
    "noImplicitReturns": true,
    "noFallthroughCasesInSwitch": true,
    "resolveJsonModule": true,
    "jsx": "react-jsx",
    "jsxImportSource": "react",
    "moduleResolution": "bundler",
    "allowImportingTsExtensions": true,
    "paths": {
      "@/*": ["./*"]
    }
  },
  "include": ["**/*.ts", "**/*.tsx"],
  "exclude": ["node_modules"]
}
```

### Tailwind CSS Setup (`tailwind.config.js`)

```javascript
module.exports = {
  content: [
    "./app/**/*.{js,ts,jsx,tsx}",
    "./components/**/*.{js,ts,jsx,tsx}",
  ],
  theme: {
    extend: {
      colors: {
        primary: "#10B981",
        secondary: "#3B82F6",
        warning: "#F59E0B",
        danger: "#EF4444",
      },
      spacing: {
        xs: "4px",
        sm: "8px",
        md: "12px",
        lg: "16px",
        xl: "24px",
        "2xl": "32px",
        "3xl": "48px",
        "4xl": "64px",
      },
      fontFamily: {
        sans: ["Inter", "-apple-system", "BlinkMacSystemFont", "sans-serif"],
      },
    },
  },
  plugins: [],
}
```

### Next.js Config (`next.config.js`)

```javascript
module.exports = {
  reactStrictMode: true,
  swcMinify: true,
  images: {
    remotePatterns: [
      {
        protocol: "https",
        hostname: "**.firebase.com",
      },
    ],
    formats: ["image/avif", "image/webp"],
  },
  env: {
    NEXT_PUBLIC_API_URL: process.env.NEXT_PUBLIC_API_URL,
  },
}
```

---

## Environment Variables (`.env.example`)

```
# Firebase
NEXT_PUBLIC_FIREBASE_API_KEY=your_api_key
NEXT_PUBLIC_FIREBASE_AUTH_DOMAIN=your_auth_domain
NEXT_PUBLIC_FIREBASE_PROJECT_ID=worthit-prod
NEXT_PUBLIC_FIREBASE_STORAGE_BUCKET=your_storage_bucket
NEXT_PUBLIC_FIREBASE_MESSAGING_SENDER_ID=your_sender_id
NEXT_PUBLIC_FIREBASE_APP_ID=your_app_id

# API
NEXT_PUBLIC_API_URL=https://api.worthit.app/v1

# Analytics
NEXT_PUBLIC_GA_ID=your_ga_id

# Stripe
NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY=your_stripe_key

# Sentry
NEXT_PUBLIC_SENTRY_DSN=your_sentry_dsn
```

---

## Core Utilities

### Firebase Setup (`lib/firebase.ts`)

```typescript
import { initializeApp } from "firebase/app";
import { getAuth } from "firebase/auth";
import { getFirestore } from "firebase/firestore";
import { getStorage } from "firebase/storage";

const firebaseConfig = {
  apiKey: process.env.NEXT_PUBLIC_FIREBASE_API_KEY,
  authDomain: process.env.NEXT_PUBLIC_FIREBASE_AUTH_DOMAIN,
  projectId: process.env.NEXT_PUBLIC_FIREBASE_PROJECT_ID,
  storageBucket: process.env.NEXT_PUBLIC_FIREBASE_STORAGE_BUCKET,
  messagingSenderId: process.env.NEXT_PUBLIC_FIREBASE_MESSAGING_SENDER_ID,
  appId: process.env.NEXT_PUBLIC_FIREBASE_APP_ID,
};

export const app = initializeApp(firebaseConfig);
export const auth = getAuth(app);
export const db = getFirestore(app);
export const storage = getStorage(app);
```

### API Client (`lib/api-client.ts`)

```typescript
import axios from "axios";

const API_URL = process.env.NEXT_PUBLIC_API_URL;

export const apiClient = axios.create({
  baseURL: API_URL,
  headers: {
    "Content-Type": "application/json",
  },
});

// Add token to requests
apiClient.interceptors.request.use((config) => {
  const token = localStorage.getItem("authToken");
  if (token) {
    config.headers.Authorization = `Bearer ${token}`;
  }
  return config;
});

// Handle errors
apiClient.interceptors.response.use(
  (response) => response,
  (error) => {
    if (error.response?.status === 401) {
      localStorage.removeItem("authToken");
      window.location.href = "/login";
    }
    return Promise.reject(error);
  }
);
```

---

## Custom Hooks

### useAuth Hook (`hooks/useAuth.ts`)

```typescript
import { useEffect, useState } from "react";
import { auth } from "@/lib/firebase";
import { onAuthStateChanged, User } from "firebase/auth";

export function useAuth() {
  const [user, setUser] = useState<User | null>(null);
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    const unsubscribe = onAuthStateChanged(auth, (user) => {
      setUser(user);
      setLoading(false);
    });

    return unsubscribe;
  }, []);

  return { user, loading };
}
```

### useExpenses Hook (`hooks/useExpenses.ts`)

```typescript
import { useQuery, useMutation } from "@tanstack/react-query";
import { apiClient } from "@/lib/api-client";

export function useExpenses(month: string) {
  return useQuery({
    queryKey: ["expenses", month],
    queryFn: async () => {
      const { data } = await apiClient.get("/expenses", {
        params: { month },
      });
      return data;
    },
  });
}

export function useCreateExpense() {
  return useMutation({
    mutationFn: async (expense) => {
      const { data } = await apiClient.post("/expenses", expense);
      return data;
    },
  });
}
```

---

## Component Library

### Button Component (`components/common/Button.tsx`)

```typescript
import React from "react";
import clsx from "clsx";

interface ButtonProps
  extends React.ButtonHTMLAttributes<HTMLButtonElement> {
  variant?: "primary" | "secondary" | "danger" | "ghost";
  size?: "sm" | "md" | "lg";
  loading?: boolean;
}

export function Button({
  variant = "primary",
  size = "md",
  loading = false,
  children,
  ...props
}: ButtonProps) {
  const baseStyles =
    "font-medium rounded-lg transition-all duration-200 disabled:opacity-50";

  const variants = {
    primary: "bg-primary hover:bg-primary/90 text-white",
    secondary: "bg-secondary hover:bg-secondary/90 text-white",
    danger: "bg-danger hover:bg-danger/90 text-white",
    ghost: "border border-gray-300 hover:bg-gray-50 text-gray-700",
  };

  const sizes = {
    sm: "px-3 py-1.5 text-sm",
    md: "px-4 py-2 text-base",
    lg: "px-6 py-3 text-lg",
  };

  return (
    <button
      className={clsx(baseStyles, variants[variant], sizes[size])}
      disabled={loading}
      {...props}
    >
      {loading ? "Loading..." : children}
    </button>
  );
}
```

### Card Component (`components/common/Card.tsx`)

```typescript
import React from "react";

interface CardProps {
  children: React.ReactNode;
  className?: string;
}

export function Card({ children, className = "" }: CardProps) {
  return (
    <div className={`bg-white rounded-lg shadow-md p-6 ${className}`}>
      {children}
    </div>
  );
}
```

---

## Package.json Scripts

```json
{
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start",
    "lint": "eslint . --ext .ts,.tsx",
    "type-check": "tsc --noEmit",
    "format": "prettier --write .",
    "test": "jest",
    "test:watch": "jest --watch"
  }
}
```

---

## Running the Project

```bash
# Development
npm run dev
# Open http://localhost:3000

# Build
npm run build

# Production
npm run start

# Type check
npm run type-check

# Linting
npm run lint

# Format code
npm run format
```

---

**Document Version**: 1.0.0
**Last Updated**: June 2026
