# WorthIt - AI Architecture & Decision Engine

**Version**: 1.0.0
**Last Updated**: June 2026

---

## Overview

The WorthIt AI system combines:
1. **Financial Analysis**: Hard data on affordability
2. **Behavioral Psychology**: Understanding emotional triggers
3. **Goal Alignment**: Impact on financial objectives
4. **Contextual Intelligence**: User history & patterns
5. **Natural Language**: Conversational AI coach

---

## Core AI Models

### 1. Purchase Decision Scoring

**Input Variables**:
```json
{
  "product": {
    "name": "AirPods Pro",
    "price": 249.99,
    "category": "electronics",
    "frequency_of_use": "daily"
  },
  "user_financial": {
    "monthly_income": 2000,
    "current_savings": 5000,
    "monthly_spending": 1500,
    "total_debts": 3000
  },
  "emotional_state": "stressed",
  "need_or_want": "want"
}
```

### 2. Scoring Algorithms

#### Affordability Score (0-100)
```
- Price ≤ 5% monthly income → 95/100
- Price ≤ 10% monthly income → 80/100
- Price ≤ 25% monthly income → 60/100
- Price ≤ 50% monthly income → 40/100
- Price > 50% monthly income → 20/100

Adjustments:
- Low savings cushion (< 3 months) → -20
- High savings (> 6 months) → +10
- Multiple purchases in 48h → -15
```

#### Financial Impact Score (0-100)
```
- Budget impact < 5% → 90/100
- Budget impact 5-10% → 75/100
- Budget impact 10-20% → 50/100
- Budget impact 20-50% → 20/100
- Budget impact > 50% → 0/100

Debt adjustment:
- High debt-to-income (>50%) → -25
- Moderate debt (>25%) → -10
```

#### Savings Impact (0-100)
```
Calculate daily savings rate:
- Days of savings lost < 1 day → 95/100
- Days delayed 1-7 days → 85/100
- Days delayed 7-14 days → 70/100
- Days delayed 14-30 days → 50/100
- Days delayed 30-60 days → 30/100
- Days delayed > 60 days → 10/100

Bonus: Emergency fund (6+ months) → +10
```

#### Emotional Spending Risk (0-100)
```
Base: 50/100

Negative emotions (+30):
- Stressed, Sad, Anxious, Bored, Angry

FOMO/Trend (+25):
- Social media trend
- Friend mentioned
- Limited time offer

Impulse indicator (+20):
- Unplanned purchase

Buying spree (+20):
- 2+ purchases today OR
- 5+ purchases this week

History of regrets (+15):
- High regret rate in category
```

#### Goal Interference Score (0-100)
```
For each active goal:
- Calculate days until deadline
- Calculate daily savings needed
- Determine days this purchase delays goal
- Weight by priority (1-5)

Example:
- Goal: Laptop ($2500) due in 60 days
- Current progress: $1250
- Daily needed: $20.83
- Purchase ($249.99) delays by 12 days
- Final score: weighted based on priority
```

### 3. Worth It Score (Composite)

```
Final Score = (
  Affordability × 0.25 +
  Financial Health × 0.20 +
  Savings Impact × 0.20 +
  (100 - Emotional Risk) × 0.15 +
  Goal Interference × 0.10 +
  Opportunity Cost × 0.10
)

Range: 0-100
```

### 4. Recommendation Logic

```
Score ≥ 75 → "YES, WORTH IT!" ✅
Score 55-74 → "MAYBE - Consider Waiting" ⏳
Score 40-54 → "NOT RECOMMENDED" ⚠️
Score < 40 → "SKIP IT" ❌
```

---

## AI Personality Modes

### 1. Friendly Mentor
**Tone**: Warm, encouraging, supportive

> "Hey! I see you want this $80 sweater. You could swing it, but you picked up two items yesterday. Maybe give it a week? 🎉"

### 2. Financial Advisor
**Tone**: Professional, analytical, data-driven

> "Analysis: $80 = 8% of budget. Savings: 2.4 months. Delays laptop goal by 3 days. Recommendation: Defer purchase."

### 3. Strict Mode
**Tone**: Direct, savings-focused

> "$80 you don't need. That's 3 lunches = 1/30th of your laptop fund. Skip it."

### 4. Student Mode
**Tone**: Relatable, peer-to-peer

> "Real talk: $80 = 16 coffees = 5 delivery meals. Which makes you happier?"

### 5. Future Self Mode
**Tone**: Introspective, perspective-shifting

> "Three months from now, you'll either remember wearing this once, or you'll appreciate the extra savings. What does future you want? 💭"

### 6. Reality Check Mode
**Tone**: Honest, no-sugarcoating

> "You're not buying a sweater. You're buying a feeling that lasts 2 weeks. Your savings goal matters. Choose wisely."

---

## Emotional Spending Detection

### Trigger Analysis

```json
{
  "stress_spending": {
    "indicators": ["stressed", "anxious", "overwhelmed"],
    "categories": ["food", "entertainment", "shopping"],
    "intervention": "Take 30 min break, then reconsider",
    "empathy": "HIGH"
  },
  "sadness_spending": {
    "indicators": ["sad", "lonely", "depressed"],
    "categories": ["fashion", "tech", "experiences"],
    "intervention": "Talk to someone, journal, then decide",
    "empathy": "VERY_HIGH"
  },
  "boredom_spending": {
    "indicators": ["bored", "restless"],
    "categories": ["entertainment", "food"],
    "intervention": "Do something free first",
    "empathy": "MEDIUM"
  },
  "fomo_spending": {
    "indicators": ["social_media", "friend_mentioned", "limited_time"],
    "categories": ["fashion", "tech", "experiences"],
    "intervention": "Wait 48 hours - it'll still be available",
    "empathy": "UNDERSTANDING"
  }
}
```

### Impulse Risk Score

```
Factors:
- Time since planning
  < 1 hour: 0.8
  1-24 hours: 0.5
  1-7 days: 0.2
  > 7 days: 0.05

- Emotional state
  Negative: 1.5x multiplier
  Neutral: 1.0x multiplier
  Positive: 1.2x multiplier

- Purchase frequency today
  1st: 1.0x
  2-3: 1.3x
  4+: 1.8x

- Time of day
  Late night: 1.4x (higher risk)
  After stress: 1.5x
```

---

## LLM Integration

### Primary: Google Gemini API

**Uses**:
1. Generating personalized explanations
2. Creating impact summaries
3. Conversational AI chat
4. Emotional tone matching
5. Alternative suggestions

### Fallback: OpenAI GPT-4

**Uses**:
1. Enhanced reasoning
2. Complex analysis
3. Premium features

---

## Response Time Targets

- Cached user data: < 2 seconds
- Fresh analysis: < 5 seconds
- Complex analysis: < 10 seconds

---

## Confidence Scoring

```
- Missing critical data → 0.5 confidence
- Has all data → 0.95 confidence
- Some data → 0.75 confidence

Adjustments:
- Low prediction uncertainty → × 1.1
- High uncertainty (> 0.5) → × 0.8

Final range: 0.3 - 0.95
```

---

## Data Flow

```
User Input
    ↓
Validation & Normalization
    ↓
Financial Analysis
    ↓
Behavioral Psychology Analysis
    ↓
Goal Impact Analysis
    ↓
Scoring Algorithms
    ↓
Worth It Score Calculation
    ↓
Recommendation Logic
    ↓
LLM-Enhanced Explanation
    ↓
Personality Formatting
    ↓
User Response
```

---

## Model Training & Improvement

### Feedback Loop
1. User receives recommendation
2. User makes decision (buy/skip/wait)
3. User provides feedback
4. System learns outcome
5. Model weights adjust

### Continuous Learning
- Daily accuracy tracking
- Monthly retraining
- A/B testing weights
- User cohort analysis
- Feedback sentiment analysis

---

## Privacy & Security

✅ Financial data encrypted
✅ No model training on personal data
✅ GDPR compliant
✅ User can delete history
✅ No third-party data sharing

---

**Document Version**: 1.0.0
**Last Updated**: June 2026
