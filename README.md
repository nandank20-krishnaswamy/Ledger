Ledger — Personal Finance Tracker
A single-file, no-build personal finance tracker with a ledger-book aesthetic. Log income and expenses, watch your balance update live, and see spending broken down by category — all in plain HTML, CSS, and JavaScript.
Features
Add transactions — description, amount, category, and income/expense type
Live balance — running net balance updates instantly, color-coded positive/negative
Edit in place — click the pencil icon on any row to load it back into the form and update it
Delete entries — remove any transaction with one click
Category breakdown — animated bar chart of expenses grouped by category
Persistent storage — entries are saved to localStorage and survive page reloads
Responsive layout — works on mobile and desktop
Zero dependencies — no build step, no npm install, no framework
Getting started

No installation required.

Clone or download this repo
Open ledger.html directly in any modern browser
bash
git clone https://github.com/<your-username>/<your-repo>.git
cd <your-repo>
open ledger.html   # macOS
# or just double-click the file
How it works
State: transactions are held in a single in-memory array of { id, desc, amount, category, type } objects.
Rendering: one render() function is the source of truth — it rebuilds the transaction table, recalculates the balance, and redraws the category bars every time the data changes. No virtual DOM, no framework.
Persistence: saveToStorage() / loadFromStorage() read and write a single JSON blob to localStorage under the key ledger.transactions.v1, wrapped in try/catch so the app still works (in-memory only) in environments where localStorage is unavailable.
Category chart: bar widths are just percentages of the largest category total — no charting library needed.
Project structure
.
├── ledger.html          # the entire app — markup, styles, and logic
├── ledger-screenshot.png
└── README.md
Customizing
Categories — edit the <select id="category"> options in ledger.html
Colors / fonts — tweak the CSS custom properties at the top of the <style> block (--ink, --gold, --income, --expense, etc.)
Currency — update the fmt() function in the <script> block
License

MIT — use it, fork it, adapt it.
