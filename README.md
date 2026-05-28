# 🍽️ Platefolio

> Personal Investment Tracker with a Portfolio Plate UI — built with React + Vite

![Platefolio](https://img.shields.io/badge/version-2.0.0-orange) ![License](https://img.shields.io/badge/license-MIT-green) ![Vite](https://img.shields.io/badge/vite-5.x-purple) ![React](https://img.shields.io/badge/react-18.x-blue)

## ✨ Features

- 🍽️ **Portfolio Plate** — animated circular asset visualization
- 💰 **Cashflow Tracker** — dividends, coupons, rental income per asset
- 🎯 **Financial Goals** — set targets with progress bars
- 🌱 **Sprout AI** — AI-powered financial assistant (Claude API)
- 🏆 **8 Achievements** — gamification badges
- 💾 **Auto-save** — data persists via localStorage
- 🌍 **7 Languages** — ID, EN, JA, MS, ZH, ES, NL
- 💱 **7 Currencies** — IDR, USD, EUR, GBP, JPY, SGD, MYR
- 📱 **Mobile-first** — optimized for phones

---

## 🚀 Quick Start

```bash
# 1. Install dependencies
npm install

# 2. Start development server (http://localhost:3000)
npm run dev

# 3. Build for production
npm run build

# 4. Preview production build
npm run preview
```

---

## 🔑 Sprout AI Setup

Sprout AI uses the **Anthropic Claude API**. The app calls the API directly from the browser.

> ⚠️ **Important:** For production, proxy the API through your own backend to protect your API key.

### Option A — Direct (Development only)
The app currently calls `https://api.anthropic.com/v1/messages` directly. This works in development if your browser doesn't block CORS, but **is not safe for production** (exposes your key).

### Option B — Secure Backend Proxy (Recommended for production)

1. Create an `.env` file:
```env
VITE_API_URL=https://your-backend.com/api/claude
```

2. Update the fetch URL in `src/components/Platefolio.jsx`:
```js
// Replace:
const resp = await fetch("https://api.anthropic.com/v1/messages", { ... })

// With:
const resp = await fetch(import.meta.env.VITE_API_URL, { ... })
```

3. Your backend forwards the request with your `ANTHROPIC_API_KEY` in the header.

---

## 📦 Deploy to Vercel

### Method 1 — Vercel CLI
```bash
npm i -g vercel
vercel
```

### Method 2 — GitHub + Vercel Dashboard
1. Push this project to a GitHub repository
2. Go to [vercel.com](https://vercel.com) → New Project
3. Import your repo
4. Framework: **Vite** (auto-detected)
5. Build Command: `npm run build`
6. Output Directory: `dist`
7. Click **Deploy** ✅

---

## 🏗️ Project Structure

```
platefolio/
├── public/                 # Static assets
├── src/
│   ├── components/
│   │   └── Platefolio.jsx  # Main app component (all-in-one)
│   ├── App.jsx             # Root wrapper
│   ├── main.jsx            # React entry point
│   └── index.css           # Global styles & animations
├── index.html              # HTML template
├── vite.config.js          # Vite configuration
├── vercel.json             # Vercel deployment config
├── package.json
└── README.md
```

---

## 🎨 Tech Stack

| Tool | Version | Purpose |
|------|---------|---------|
| React | 18.x | UI framework |
| Vite | 5.x | Build tool & dev server |
| Canvas API | native | Portfolio plate rendering |
| Web Audio API | native | Bell & achievement sounds |
| localStorage | native | Data persistence |
| Claude API | claude-sonnet-4 | Sprout AI |

---

## 📱 Mobile PWA (Optional)

To install as a home screen app, add to `index.html`:
```html
<link rel="manifest" href="/manifest.json" />
```

Then create `public/manifest.json`:
```json
{
  "name": "Platefolio",
  "short_name": "Platefolio",
  "start_url": "/",
  "display": "standalone",
  "background_color": "#FFFAF5",
  "theme_color": "#FF7043",
  "icons": [{ "src": "/icon-192.png", "sizes": "192x192", "type": "image/png" }]
}
```

---

## 📄 License

MIT © Platefolio 2025
