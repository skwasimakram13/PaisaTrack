# PaisaTrack – Smart Indian Expense Tracker
 Smart Indian Expense Tracker

✅ Problem Statement
In India, people use UPI, bank transfers, wallets, and debit cards for most payments. However:

They don’t manually track expenses.

They forget where their money went.

Budgeting seems complicated.

Most don’t use finance apps unless it's really simple and automatic.

💡 Solution
A mobile app that automatically reads transaction SMSes, UPI messages, and bank alerts to:

Track daily/monthly expenses.

Categorize spends (Food, Travel, Recharge, Shopping, etc.).

Show insights, pie charts, and spending trends.

Remind users of bills or subscriptions.

Provide savings tips.

🔧 Features Breakdown
🔍 1. Automatic SMS Parsing
App reads incoming SMSes (with user permission).

Filters bank/UPI messages using regex & keywords (e.g. "debited", "₹", "Rs.").

Extracts:

Amount

Merchant name

UPI ID

Date/time

🪙 2. UPI Spend Analysis
Detects UPI transactions (Google Pay, PhonePe, Paytm, etc.).

Links each transaction with category using AI or user feedback.

Shows UPI vs cash vs bank spend split.

📊 3. Dashboard & Reports
Daily/weekly/monthly spending graphs.

Category-wise breakdown (Food, Recharge, Groceries, etc.).

Highest spending day/month.

Compare monthly savings/spends.

💼 4. Bank Balance & Statement View
Shows current balance from last SMS or manual sync.

Shows mini statement using SMS history.

(Optional) Add account sync via APIs like Salt, Finbox, or Setu (for future).

🔔 5. Reminders & Insights
Auto-reminders for recurring bills (based on SMS).

Tips to save based on spending habits (e.g., “You spent ₹1,200 on Swiggy this month — consider cooking more 🍳”).

🔐 6. Privacy & Security
All data stored locally or end-to-end encrypted.

SMS permission is optional but recommended.

No bank login required (unless user opts for it).

🛠️ Tech Stack
Android App (Java/Kotlin):
SMS BroadcastReceiver

Room DB or SQLite

MPAndroidChart for graphs

Retrofit (if syncing with backend)

Optional Firebase for backup

Backend (optional):
Node.js or PHP + MySQL

For cloud sync, insights, and backup

🎯 Target Audience
College students

Working professionals

Small business owners (who pay via UPI/cash)

Homemakers managing household budgets

💸 Monetization Ideas
Freemium: Basic features free, Pro features paid

Ads (Google AdMob, non-intrusive)

Affiliate links: Credit cards, loan offers

Subscription model: ₹49/month for advanced insights, cloud sync, export to Excel, etc.

🧠 Bonus Ideas
Split bills with friends

Export expense reports for tax

“Smart Suggestions” (e.g., recharge offers, better budget plans)

Multi-language support (Hindi, Bengali, Tamil, etc.)

