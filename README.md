# Conference Expense Planner

A React + Redux app for planning and budgeting a conference. Pick a venue, add AV equipment, select meals for your attendees, and get a live running total broken down by category — built as an interactive budgeting tool rather than a personal transaction log.

> **Note:** This repo is named `Expense-Tracker`, but the app itself is a conference/event **budget calculator** ("Conference Expense Planner" / "BudgetEase Solutions"), not a personal income/expense ledger. This README documents what the app actually does.

## Features

- 🏢 **Venue selection** — choose from five room types (Conference Room, Auditorium Hall, Presentation Room, etc.), each with its own capacity and cost; quantities are adjustable with +/− controls
- 🎤 **Add-ons (AV equipment)** — add projectors, speakers, microphones, whiteboards, and signage, each with independent quantity controls
- 🍽️ **Meals** — select from Breakfast, High Tea, Lunch, and Dinner, priced per attendee based on a configurable headcount
- 🚦 **Business rule enforcement** — the Auditorium Hall is capped at 3 units; other venue items cap at 10
- 📊 **Live itemized summary** — a "Show Details" view lists every selected item with unit cost, quantity, and subtotal, plus category and grand totals
- ⚛️ **Redux Toolkit state management** — venue, AV, and meal selections each live in their own slice, combined in a single store

## Tech Stack

| Layer      | Technology                |
|------------|-----------------------------|
| Framework  | React 18 + Vite 5            |
| State      | Redux Toolkit + React Redux  |
| Linting    | ESLint                       |

## Project Structure

```
Expense-Tracker/
├── src/
│   ├── App.jsx              # Landing header + toggles the planner view
│   ├── AboutUs.jsx          # "BudgetEase Solutions" intro blurb
│   ├── ConferenceEvent.jsx  # Core planner UI: venue, add-ons, meals, navigation
│   ├── TotalCost.jsx        # Itemized summary + grand total view
│   ├── venueSlice.js        # Redux slice: venue options, quantities, business rules
│   ├── avSlice.js           # Redux slice: AV equipment options & quantities
│   ├── mealsSlice.js        # Redux slice: meal options & selection state
│   └── store.js             # Combines all slices into the Redux store
├── public/                  # Images (venue/conference art)
├── index.html
├── package.json
└── vite.config.js
```

## How It Works

1. On the landing page, clicking **Get Started** reveals the planner.
2. In **Venue**, **Add-ons**, and **Meals** sections, quantities/selections update the corresponding Redux slice via dispatched actions (`incrementQuantity`, `incrementAvQuantity`, `toggleMealSelection`, etc.).
3. For meals, the cost is multiplied by a **Number of People** field rather than a per-item quantity.
4. Clicking **Show Details** switches to the `TotalCost` view, which reads current state from all three slices, builds an itemized table, and displays category totals plus a grand total.

## Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) (v18+ recommended)

### Installation

```bash
git clone https://github.com/Hasnain-jaffer/Expense-Tracker.git
cd Expense-Tracker
npm install
```

### Running the App

```bash
npm run dev
```

Open the local URL Vite prints (typically **http://localhost:5173**).

### Building for Production

```bash
npm run build
npm run preview
```

## Roadmap

- [ ] Persist selections (currently reset on page refresh — no localStorage/backend)
- [ ] Add venue/AV/meal images (`img` fields exist in each slice but are currently empty strings)
- [ ] Export the final budget as a PDF or shareable link
- [ ] Rename the repo/app to reflect its actual purpose (conference budgeting, not general expense tracking) to avoid confusion for visitors
- [ ] Add real personal expense-tracking features if that's the direction you want to take this project

## License

This project is licensed under the Apache License 2.0. See [LICENSE](./LICENSE) for details. The license file attributes an original copyright to IBM Developer Skills Network — if this project began from an IBM Skills Network template/guided project, keep that attribution intact per the license terms.

## Author

**Hasnain Jaffer**
- GitHub: [@Hasnain-jaffer](https://github.com/Hasnain-jaffer)
