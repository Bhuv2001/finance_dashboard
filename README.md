# Ledger — Finance Dashboard UI

> A clean, interactive personal finance dashboard built with vanilla JavaScript, HTML, and CSS. No frameworks. No build steps. Just open and run.

---

## 🚀 Quick Start

No installation required.

```bash
# Simply open in your browser
open finance-dashboard.html
```

Or serve it locally:

```bash
npx serve .
# Visit http://localhost:3000
```

---

## 📋 Features Overview

### 1. Dashboard Overview
- **4 Summary Cards** — Total Balance, Total Income, Total Expenses, Savings Rate
- **Balance Trend Chart** — Line chart showing monthly income vs expenses vs net (Chart.js)
- **Spending Breakdown** — Donut chart with category breakdown and color-coded legend
- **Recent Activity** — Last 5 transactions with quick link to full list

### 2. Transactions Section
- Full sortable table with Description, Category, Date, Amount, Type columns
- **Search** — Real-time text search across description and category
- **Filters** — Filter by type (income/expense), category, and month
- **Sorting** — Click any column header to sort ascending/descending
- **Pagination** — 8 records per page with page navigation
- **Empty state** — Graceful handling when no results match filters

### 3. Role-Based UI (RBAC Simulation)
Switch roles using the dropdown in the sidebar footer:

| Role | Permissions |
|------|-------------|
| **Viewer** | Read-only access. Can browse all data, filter, search, export CSV |
| **Admin** | Full access. Can add, edit, and delete transactions |

Role switching is instant with toast notification feedback.

### 4. Insights Section
- **Top Spending Category** — Bar chart breakdown of top 5 expense categories
- **Monthly Comparison** — Bar chart comparing income vs expenses by month
- **Key Observations** — Auto-generated observations based on spending patterns (savings rate health, income diversification, top spend areas)
- **Savings Rate Bar** — Visual representation of avg monthly income, expense, and savings rate

### 5. State Management
All state is managed in a single `state` object:
```js
state = {
  transactions,   // All transaction data
  role,           // 'admin' | 'viewer'
  search,         // Search query
  filterType,     // 'income' | 'expense' | ''
  filterCat,      // Category filter
  filterMonth,    // Month filter
  sortKey,        // Sort column
  sortDir,        // 'asc' | 'desc'
  page,           // Current page
  perPage         // Records per page
}
```

### 6. Data Persistence
- Transactions are saved to `localStorage` under the key `ledger_txns`
- Data persists across page reloads
- Seeded with 40 realistic transactions spanning 6 months

---

## 🎨 Design Decisions

**Aesthetic direction:** Dark fintech terminal — inspired by Bloomberg Terminal and modern fintech dashboards. Deep navy backgrounds with amber/gold accents.

**Typography:**
- `Syne` — Display headings (geometric, editorial weight)
- `DM Sans` — Body text (clean, readable)
- `DM Mono` — Data, labels, stats (precision feel)

**Color system:**
- Background: `#080c14` (near-black navy)
- Surfaces: layered `#0d1422` → `#111927` → `#162033`
- Accent: `#f0a500` (warm amber — used sparingly for active states)
- Semantic: green for income, red for expense, blue for neutral info

---

## 🔧 Technical Stack

| Concern | Approach |
|---------|----------|
| Framework | Vanilla JavaScript (no deps) |
| Styling | Custom CSS with CSS variables |
| Charts | Chart.js (CDN) |
| Fonts | Google Fonts (CDN) |
| State | Single `state` object, no external library |
| Persistence | `localStorage` |
| Data | 40 seeded mock transactions |

---

## 📁 File Structure

```
finance-dashboard.html    # Single-file application (HTML + CSS + JS)
README.md                 # This file
```

---

## ✅ Requirements Checklist

- [x] Summary cards (Balance, Income, Expenses, Savings)
- [x] Time-based visualization (monthly trend line chart)
- [x] Categorical visualization (spending donut chart)
- [x] Transaction list with date, amount, category, type
- [x] Search, filtering, sorting
- [x] Role-based UI (Viewer / Admin)
- [x] Admin: Add / Edit / Delete transactions
- [x] Insights section (top category, monthly comparison, observations)
- [x] Application state management
- [x] Responsive design (mobile sidebar drawer)
- [x] Empty state handling
- [x] Data persistence (localStorage)
- [x] Export CSV functionality
- [x] Toast notifications

---

## 💡 Assumptions Made

1. Currency is INR (₹) — can be changed by replacing `₹` globally
2. "Savings Rate" = (Income − Expenses) / Income × 100
3. Seeded data covers Jan–Jun 2024 with realistic Indian salary/expense values
4. Admin can edit any transaction; Viewer mode hides all mutation UI
5. Month filter is derived dynamically from actual transaction dates

---

## 🔄 Resetting Data

To clear all data and restore seed data, run in browser console:
```js
localStorage.removeItem('ledger_txns');
location.reload();
```
