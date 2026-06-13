https://santiagojleons.github.io/lease-tracker/

# 🚗 Lease Mileage Tracker

A mobile-first, single-file web app to track your car lease mileage in real time — no backend, no install, no account needed. Built with vanilla JavaScript and stores all data locally on your device using `localStorage`.

> **Live demo:** Deploy instantly on [GitHub Pages](https://pages.github.com/) by uploading `index.html`.

---

## 📱 Screenshots

| Setup Screen | Dashboard | Weekly View |
|---|---|---|
| Enter your lease details once | See daily & weekly budgets at a glance | Track pace vs. actual on a live chart |

---

## ✨ Features

- **Zero setup friction** — fill out 5 fields once, never again
- **Any-day logging** — log your odometer on any day, not just Sundays; date is stamped automatically
- **Sunday week boundaries** — weeks reset on Sunday with automatic prorating for your first partial week
- **Three daily budget cards:**
  - 📊 *Lease Base Rate* — what your contract allows per day (no cushion)
  - ✅ *Your Daily Budget* — recommended target with your mileage cushion spread over the full lease
  - ⚡ *Max/Day This Week* — how hard you can drive if you want to use your full weekly budget before Sunday
- **Live progress bars** — weekly usage and overall lease progress at a glance
- **Cushion tracking** — see exactly how many miles you are ahead of or behind ideal pace
- **Chart.js line chart** — target pace vs. your actual miles plotted from lease start through 90 days ahead
- **Full log history** — every entry shows date, odometer, and miles added, with a delete button for mistakes
- **100% offline** — all data lives in your browser's `localStorage`, nothing is sent to any server
- **GitHub Pages ready** — rename to `index.html` and deploy in under 60 seconds

---

## 🧮 Math & Logic

### Core Formulas

```
Total Miles Allowed   = Annual Allowance × (Lease Months ÷ 12)
Base Daily Rate       = Total Miles Allowed ÷ Total Lease Days
Miles Remaining       = Total Miles Allowed − Miles Driven
Daily Budget          = Miles Remaining ÷ Days Remaining
```

> `Daily Budget` is always slightly **above** the base rate when you have a cushion, because fewer remaining miles are spread over fewer remaining days — the cushion is automatically baked in.

### Cushion

```
Ideal Miles By Today  = Days Elapsed × Base Daily Rate
Cushion               = Ideal Miles By Today − Miles Driven
```

- **Positive cushion** → you have driven *less* than the ideal pace → you can afford to drive more
- **Negative cushion** → you have driven *more* than the ideal pace → ease up to stay on track

### Weekly Budget

```
Week End              = Next Sunday (or today if today is Sunday)
Days Left This Week   = Days until (and including) Sunday
Weekly Remaining      = Daily Budget × Days Left This Week
Max Daily This Week   = (Daily Budget × 7) ÷ Days Left This Week
```

Weeks always end on **Sunday**. If your lease started mid-week, the first week is automatically prorated from your start date to the first Sunday.

---

## 🚀 Getting Started

### Option 1 — GitHub Pages (recommended)

1. Fork or clone this repo
2. Rename `lease_mileage_tracker.html` → `index.html`
3. Go to **Settings → Pages → Source: main branch / root**
4. Your app is live at `https://yourusername.github.io/lease-tracker`

### Option 2 — Local

1. Download `lease_mileage_tracker.html`
2. Open it in any browser (Safari, Chrome, Firefox)
3. That's it — no server, no install

---

## 🛠️ Tech Stack

| Library | Version | Purpose |
|---|---|---|
| [Tailwind CSS](https://tailwindcss.com) | v4 (Play CDN) | Utility-first styling |
| [Lucide Icons](https://lucide.dev) | Latest (unpkg CDN) | SVG icon set |
| [Chart.js](https://chartjs.org) | 4.4.9 (jsDelivr CDN) | Line chart rendering |
| Vanilla JS (ES5) | — | All app logic |
| `localStorage` | Browser API | Persistent data storage |

No build step. No npm. No bundler. One file.

---

## 📂 Project Structure

```
lease-tracker/
└── index.html          # The entire app — HTML + CSS + JavaScript
└── README.md           # This file
```

---

## ⚙️ Setup Fields

| Field | Description |
|---|---|
| **Miles Allowed Per Year** | Your lease contract's annual mileage cap (e.g. 12,000) |
| **Car's Odometer at Lease Start** | Miles on the car the day you picked it up (enter `0` if brand new) |
| **Miles Driven Since Lease Start** | Total personal miles you've put on the car up to today |
| **Lease Start Date** | The date you drove the car off the lot |
| **Lease Length** | 24, 36, or 48 months |

---

## 📊 Dashboard Metrics

| Metric | What It Means |
|---|---|
| **Lease Base Rate** | The raw daily rate from your contract (e.g. 32.9 mi/day for 12k/yr over 365 days) |
| **Your Daily Budget** | Recommended daily target — slightly above base rate when you have a cushion |
| **Max/Day This Week** | If you want to spend your entire week's budget before Sunday |
| **Miles Left This Week** | Daily budget × days remaining until Sunday |
| **Miles Cushion** | How many miles ahead of (or behind) the ideal pace you currently are |
| **Ideal Miles By Today** | How many miles you *should* have driven if perfectly on pace since day one |

---

## 🔒 Privacy

All data is stored exclusively in your browser's `localStorage`. No data is ever transmitted to any server. Clearing your browser data or clicking **Reset All Data** will permanently delete all stored information.

---

## 📄 License

MIT — free to use, modify, and distribute.

---

## 🙌 Contributing

Pull requests welcome. If you find a bug or want a new feature, open an issue.

1. Fork the repo
2. Create your branch: `git checkout -b feature/your-feature`
3. Commit your changes: `git commit -m 'Add your feature'`
4. Push to the branch: `git push origin feature/your-feature`
5. Open a pull request
