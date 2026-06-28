# ⚡ Structra — Intelligent Construction Cost Platform

> India's most feature-rich construction cost estimator.  
> Built by **Adarsh** · DPGU University, Pune · CSE 2025–26

---

## 🌟 Features

| Feature | Description |
|---|---|
| **Reality Layer** | Soil type, urban/rural, road access — affects actual cost |
| **Structra Score™** | 0–100 optimization score for your configuration |
| **Material Quantities** | Cement bags, steel tonnes, bricks, sand — CPWD norms |
| **Construction Timeline** | Phase-by-phase breakdown with months |
| **Monthly Payment Plan** | Cash flow planning by construction phase |
| **Scenario Comparison** | Basic vs Standard vs Premium cost table |
| **Smart Optimization** | Rule-based suggestions with exact savings amounts |
| **Budget Planner** | Reverse calc: budget → max area, floors, quality |
| **Contractor Matching** | City-specific verified contractors with WhatsApp link |
| **Export Report** | Download full analysis as text report |
| **15+ Cities** | City-specific rates with tier multipliers |
| **Dark / Light Mode** | Full theme toggle |
| **Offline Fallback** | Works without backend (calculations run in browser) |

---

## 🏗️ Project Structure

```
structra/
├── frontend/
│   └── index.html          ← Complete standalone website (open in browser)
│
├── backend/
│   ├── server.js            ← Express entry point
│   ├── package.json
│   ├── .env.example         ← Copy to .env and fill in values
│   │
│   ├── config/
│   │   ├── db.js            ← MongoDB connection
│   │   └── seed.js          ← Seed contractors + cities (run once)
│   │
│   ├── models/
│   │   ├── Estimate.js      ← Saved estimates schema
│   │   ├── Contractor.js    ← Contractor profiles schema
│   │   └── City.js          ← City rates schema
│   │
│   ├── routes/
│   │   ├── estimate.js      ← POST /api/estimate
│   │   ├── contractors.js   ← GET  /api/contractors
│   │   ├── budget.js        ← POST /api/budget
│   │   └── cities.js        ← GET  /api/cities
│   │
│   ├── controllers/
│   │   ├── estimateController.js
│   │   ├── contractorController.js
│   │   ├── budgetController.js
│   │   └── cityController.js
│   │
│   └── services/
│       └── calculationService.js  ← ENTIRE calculation engine
│
└── README.md
```

---

## 🚀 How to Run Locally

### Option A — Frontend Only (No install needed)
```
Just open  frontend/index.html  in your browser.
Everything works offline — calculations run in the browser.
```

### Option B — Full Stack (Frontend + Backend + MongoDB)

**Step 1 — Install Node.js**
- Download from https://nodejs.org (LTS version)
- Verify: `node -v` and `npm -v`

**Step 2 — Install MongoDB**
- Local: https://www.mongodb.com/try/download/community
- OR use MongoDB Atlas (free cloud): https://mongodb.com/atlas

**Step 3 — Set up backend**
```bash
cd structra/backend
npm install
cp .env.example .env
```

**Step 4 — Edit .env**
```
# Open backend/.env and set:
MONGODB_URI=mongodb://localhost:27017/structra
PORT=5000
FRONTEND_URL=http://localhost:5500
```

**Step 5 — Seed database**
```bash
node config/seed.js
# Should print: ✅ Seeded 17 contractors  ✅ Seeded 15 cities
```

**Step 6 — Start backend**
```bash
npm run dev        # development (auto-restart)
# OR
npm start          # production
```

**Step 7 — Open frontend**
- Install VS Code extension: **Live Server** (by Ritwick Dey)
- Right-click `frontend/index.html` → **Open with Live Server**
- Or just open `frontend/index.html` in your browser

**Step 8 — Test the API**
```
Open browser: http://localhost:5000/api/health
Should show: { "status": "Structra API is running ⚡" }
```

---

## 🔌 API Reference

### POST /api/estimate
```json
{
  "plotSize": 1500,
  "plotUnit": "sqft",
  "builtupPercentage": 75,
  "floors": 2,
  "city": "nagpur",
  "buildingType": "residential",
  "quality": "standard",
  "brickType": "flyash",
  "soilType": "normal",
  "locationType": "urban",
  "roadAccess": "good",
  "customPrices": {
    "cementPerBag": 400,
    "steelPerKg": 70,
    "labourPerDay": 800
  }
}
```

### GET /api/contractors?city=nagpur&limit=5

### POST /api/budget
```json
{ "budget": 5000000, "plotSize": 1500, "city": "nagpur", "quality": "standard" }
```

### GET /api/cities

### GET /api/estimate/stats

---

## 📤 How to Upload to GitHub

See the **GITHUB_UPLOAD_GUIDE.md** file for full step-by-step instructions.

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Frontend | HTML5, CSS3 (custom), Vanilla JS, Chart.js |
| Backend | Node.js, Express.js |
| Database | MongoDB + Mongoose |
| Security | Helmet, express-rate-limit, CORS |

---

## 📋 API Values Reference

**buildingType:** `residential` · `commercial` · `warehouse`  
**quality:** `basic` · `standard` · `premium`  
**brickType:** `red` · `flyash` · `aac`  
**soilType:** `normal` · `rocky` · `loose` · `expansive`  
**locationType:** `urban` · `suburban` · `rural`  
**roadAccess:** `good` · `moderate` · `poor`  
**cities:** `nagpur` `pune` `mumbai` `delhi` `bangalore` `hyderabad` `chennai` `ahmedabad` `kolkata` `jaipur` `lucknow` `surat` `bhopal` `coimbatore` `indore`

---

*© 2025 Structra · Built by Adarsh · DPGU University Pune*
