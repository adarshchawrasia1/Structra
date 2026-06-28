# Structra
Structra is a full-stack web application that helps users estimate the cost of building residential, commercial, or warehouse structures based on plot size, materials, labour, and location. It provides detailed cost breakdowns, smart optimization suggestions, and budget planning tools to support real-world construction decisions.


structra/
├── frontend/index.html          ← Full website (open directly in browser)
├── backend/
│   ├── server.js                ← Express server
│   ├── package.json
│   ├── .env.example             ← Copy → rename to .env
│   ├── config/db.js             ← MongoDB connection
│   ├── config/seed.js           ← Seeds contractor + city data
│   ├── models/                  ← Estimate, Contractor, City schemas
│   ├── routes/                  ← /api/estimate, /contractors, /budget, /cities
│   ├── controllers/             ← Business logic per route
│   └── services/calculationService.js  ← Entire calculation engine
├── README.md
├── GITHUB_UPLOAD_GUIDE.md       ← Full GitHub instructions
└── .gitignore
