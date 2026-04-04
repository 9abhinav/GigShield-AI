🛡️ GigShield AI — Parametric Insurance for Gig Workers

**GigShield AI** is a full-stack, AI-powered parametric insurance platform that protects gig workers (Zomato, Swiggy, Zepto, etc.) from income loss caused by environmental disruptions like heavy rain, extreme heat, and high pollution — with **zero-touch, instant claim payouts**.

> Built with **React + Vite**, **Node.js + Express**, **MongoDB**, and **Socket.io** for real-time notifications.

---



## 🎯 Problem Statement

Gig workers lose **20–30% of their monthly income** due to:

- 🌧️ Heavy rain reducing delivery orders
- 🌡️ Extreme heatwaves making outdoor work unsafe
- 🌫️ High AQI / pollution advisories
- 🚫 Curfews or road restrictions

**There is currently no income protection or insurance system tailored for gig workers.**

---

## 💡 Our Solution

GigShield AI offers a **weekly micro-insurance subscription** with:

| Feature | Description |
|---|---|
| 🤖 **AI Premium Calculation** | Dynamic pricing based on real-time environmental risk factors (rain, heat, AQI) for the worker's city |
| ⚡ **Zero-Touch Claims** | No manual filing — claims are triggered **automatically** when parametric thresholds are breached |
| 💸 **Instant Payouts** | 40% of coverage amount credited instantly upon trigger via real-time Socket.io notification |
| 🕵️ **AI Fraud Detection** | Detects duplicate claims, flags suspicious users with >2 claims in 24 hours |
| 👑 **Admin Dashboard** | Real-time stats: loss ratio, flagged users, total payouts, recent triggers |
| 🎮 **Event Simulator** | Simulate weather events in any city to demo the entire claim pipeline end-to-end |

---

## ⚙️ How It Works

```
1. Worker signs up → enters city, platform (Zomato/Swiggy), weekly income
2. AI calculates personalized weekly premium based on city conditions
3. Worker purchases a 7-day micro-policy (₹500 / ₹1000 / ₹2000 coverage)
4. System continuously monitors environmental conditions
5. If disruption occurs → claim is auto-triggered (Zero-Touch)
6. Fraud detection runs → payout is credited instantly via Socket.io
```

---

## 🌦️ Parametric Triggers

Automatic claim payout happens when **any** of these thresholds are breached:

| Trigger | Threshold |
|---|---|
| 🌧️ Rainfall | > 50 mm |
| 🌡️ Temperature | > 45°C |
| 🌫️ Air Quality Index (AQI) | > 400 |
| 🚫 Curfew / Restrictions | Admin-triggered flag |

---

## 💰 AI Premium Breakdown

The premium is dynamically calculated per-user based on their city's environmental data:

| Component | Amount |
|---|---|
| Base Price | ₹30 |
| Rain Risk (if rain > 30mm) | +₹10 to ₹15 |
| Heat Risk (if temp > 35°C) | +₹5 to ₹10 |
| Pollution Risk (if AQI > 200) | +₹4 to ₹8 |
| **Typical Weekly Total** | **₹30 – ₹63** |

Risk scores are classified as **Low**, **Medium**, or **High** based on the total premium.

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| **Frontend** | React 19, Vite 8, React Router v7 |
| **Styling** | Tailwind CSS 4, Framer Motion, Glassmorphism UI |
| **Backend** | Node.js, Express 5 |
| **Database** | MongoDB Atlas (Mongoose ODM) |
| **Auth** | JWT (JSON Web Tokens), bcryptjs |
| **Real-time** | Socket.io (WebSocket push for claim notifications) |
| **Notifications** | Sonner toast notifications |
| **Icons** | Lucide React |

---

## 📂 Project Structure

```
GigShield-AI/
├── README.md
├── LICENSE
├── .gitignore
│
├── backend/
│   ├── server.js                  # Express + Socket.io server entry
│   ├── package.json
│   ├── controllers/
│   │   ├── authController.js      # Register, Login, JWT
│   │   ├── policyController.js    # Premium calc, policy purchase
│   │   ├── simulatorController.js # Event trigger + fraud detection
│   │   └── adminController.js     # Dashboard stats, loss ratio
│   ├── models/
│   │   ├── User.js                # Worker/Admin schema with fraud flags
│   │   ├── Policy.js              # Coverage, premium breakdown
│   │   └── Claim.js               # Trigger event, payout, status
│   ├── routes/
│   │   ├── authRoutes.js
│   │   ├── policyRoutes.js
│   │   ├── simulatorRoutes.js
│   │   └── adminRoutes.js
│   ├── middlewares/
│   │   └── authMiddleware.js      # JWT verification
│   └── utils/
│       └── globalState.js         # In-memory city environment state
│
├── frontend/
│   ├── index.html
│   ├── package.json
│   ├── vite.config.js
│   └── src/
│       ├── main.jsx               # App entry point
│       ├── App.jsx                # Router + Protected routes
│       ├── index.css              # Tailwind + custom styles
│       ├── components/
│       │   ├── Sidebar.jsx        # Navigation sidebar
│       │   └── ui/                # Reusable UI primitives
│       └── pages/
│           ├── Login.jsx          # Auth (Login + Register)
│           ├── Dashboard.jsx      # Worker dashboard + stats
│           ├── BuyPolicy.jsx      # Premium calculator + purchase
│           ├── Claims.jsx         # Claims history
│           ├── SimulatorPanel.jsx  # Event trigger simulator
│           └── AdminDashboard.jsx # Admin analytics + fraud flags
```

---

## 🚀 Getting Started

### Prerequisites

- **Node.js** v18+
- **MongoDB Atlas** account (or local MongoDB)
- **npm** or **yarn**

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/GigShield-AI.git
cd GigShield-AI
```

### 2. Setup Backend

```bash
cd backend
npm install
```

Create a `.env` file in `backend/`:

```env
PORT=5000
MONGO_URI=mongodb+srv://<username>:<password>@cluster.mongodb.net/gigshield_db
JWT_SECRET=your_jwt_secret_here
```

Start the backend server:

```bash
npm run dev
```

> Backend runs on `http://localhost:5000`

### 3. Setup Frontend

```bash
cd frontend
npm install
npm run dev
```

> Frontend runs on `http://localhost:5173`

---

## 🔌 API Endpoints

### Auth
| Method | Endpoint | Description |
|---|---|---|
| `POST` | `/api/auth/register` | Register a new worker/admin |
| `POST` | `/api/auth/login` | Login and receive JWT |
| `GET` | `/api/auth/me` | Get current user profile |

### Policy
| Method | Endpoint | Description |
|---|---|---|
| `POST` | `/api/policy/calculate-premium` | AI-calculated premium for user's city |
| `POST` | `/api/policy/purchase` | Purchase a 7-day micro-policy |
| `GET` | `/api/policy/my-policy` | Get active policy |
| `GET` | `/api/policy/my-claims` | Get claim history |

### Simulator
| Method | Endpoint | Description |
|---|---|---|
| `POST` | `/api/simulator/trigger` | Trigger a weather event in a city |

### Admin
| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/api/admin/dashboard` | Get platform-wide analytics |

---

## 🕵️ Fraud Detection System

The platform includes built-in AI fraud detection:

1. **Duplicate Claim Prevention** — If the same trigger event was already filed for a policy within the last 24 hours, the claim is silently skipped.
2. **Suspicious Activity Flagging** — If a user files more than 2 claims within 24 hours, they are automatically flagged as `Suspicious` and visible on the Admin Dashboard.
3. **User Flagging** — Flagged users have their `flags.suspicious` field set to `true` with a reason, viewable by admins.

---

## 🧠 AI / Intelligence Features

- **Dynamic Premium Pricing** — Premiums are not flat-rate; they adjust based on real-time environmental risk factors for the worker's specific city.
- **Risk Score Classification** — Each user gets a Low / Medium / High risk label based on their city's conditions.
- **Automated Claim Pipeline** — From trigger detection to payout, the entire process is zero-touch with no manual intervention.

---

## 🎮 Simulator Mode

The **Simulator Panel** allows you to demo the full claim pipeline:

1. Select a city (e.g., Mumbai, Delhi, Bangalore)
2. Choose an event type (Heavy Rain, Heatwave, High Pollution, Curfew)
3. Click **Trigger** — the backend processes all active policies in that city
4. Claims are auto-created with fraud checks
5. Real-time Socket.io notifications pushed to affected workers

---

## 👥 User Roles

| Role | Access |
|---|---|
| **Worker** | Dashboard, Buy Policy, Claims, Simulator |
| **Admin** | Admin Dashboard (stats, flagged users, loss ratio, recent triggers) |

---

## 📄 License

This project is **proprietary**. See [LICENSE](./LICENSE) for details.

---

<p align="center">
  Built with ❤️ for India's 15M+ gig workers
</p>
]]>
