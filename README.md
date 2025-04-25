# PaisaTrack – Smart Indian Expense Tracker 📱💸

> Simple, smart, and secure way to automatically track your daily expenses from SMS, UPI, and bank alerts.

---
## Live Demos
- **Live Web Demo** - <a href="https://paisatrackweb.netlify.app" target="_blank" rel="noopener noreferrer">https://paisatrackweb.netlify.app</a>
- **Android App Demo** - Coming very soon

---

## ✅ Problem Statement

In India, people commonly use UPI, bank transfers, wallets, and debit cards for transactions. However:

- Manual expense tracking is rare.
- People often forget where their money went.
- Budgeting seems too complicated.
- Most don't use finance apps unless they're extremely simple and automatic.

---

## 💡 Solution

**PaisaTrack** is a mobile app that **automatically reads transaction SMSes, UPI messages, and bank alerts** to:

- 📆 Track daily/monthly expenses
- 🗂️ Categorize spends (Food, Travel, Recharge, Shopping, etc.)
- 📈 Show insights, pie charts, and trends
- 🔔 Remind users of bills and subscriptions
- 💡 Provide personalized savings tips

---

## 🔧 Features Breakdown

### 🔍 1. Automatic SMS Parsing

- Reads incoming SMSes with user permission
- Filters bank/UPI messages using regex & keywords (e.g., "debited", "₹", "Rs.")
- Extracts:
  - 💰 Amount
  - 🏪 Merchant name
  - 🔗 UPI ID
  - 🕒 Date & time

---

### 🪙 2. UPI Spend Analysis

- Detects UPI transactions (Google Pay, PhonePe, Paytm, etc.)
- Categorizes spends using AI or user feedback
- Visual split: UPI vs Cash vs Bank spends

---

### 📊 3. Dashboard & Reports

- View expenses via:
  - Daily/Weekly/Monthly graphs
  - Category-wise breakdown
- Highlights:
  - Highest spending day/month
  - Monthly savings vs spends comparison

---

### 💼 4. Bank Balance & Statement View

- Displays current balance from latest SMS
- Generates mini statements using SMS history
- (Optional) Integrate account sync via APIs like **Salt**, **Finbox**, or **Setu**

---

### 🔔 5. Reminders & Insights

- Smart reminders for recurring bills (based on SMS patterns)
- Contextual savings tips (e.g., _“You spent ₹1,200 on Swiggy — try home-cooked meals 🍳”_)

---

### 🔐 6. Privacy & Security

- Data stored **locally** or with **end-to-end encryption**
- SMS permission is optional (but recommended for best experience)
- No bank login required unless the user opts in

---

## 🛠️ Tech Stack

### Android App (Java/Kotlin)
- `SMS BroadcastReceiver`
- `Room DB` or `SQLite`
- `MPAndroidChart` for visual reports
- `Retrofit` for optional backend sync
- (Optional) `Firebase` for backup & sync

## 💻 Android App (Java) Structure
```java
📁 app/
├── 📁 activities/
│   ├── MainActivity.java
│   ├── PermissionsActivity.java
│   ├── TransactionDetailActivity.java
│   ├── ReportsActivity.java
│   └── SettingsActivity.java
│
├── 📁 adapters/
│   ├── TransactionAdapter.java
│   └── CategoryAdapter.java
│
├── 📁 models/
│   ├── Transaction.java
│   ├── Category.java
│   └── User.java
│
├── 📁 utils/
│   ├── SmsParser.java
│   ├── PermissionUtils.java
│   └── NetworkUtils.java
│
├── 📁 services/
│   └── SmsReceiver.java (BroadcastReceiver for SMS)
│
├── 📁 database/
│   ├── DBHelper.java
│   └── TransactionDAO.java
│
├── 📁 network/
│   ├── ApiClient.java
│   ├── ApiService.java
│   └── ApiResponse.java
│
├── 📁 charts/
│   └── ExpenseChartManager.java
│
├── 📁 res/
│   ├── layout/
│   ├── drawable/
│   ├── values/
│   └── xml/
│
└── AndroidManifest.xml
```

### Backend (Optional)
- `Node.js` or `PHP` + `MySQL`
- For cloud sync, analytics, and secure backup

## 🌐 Backend (PHP + MySQL) Structure
```php
📁 finance_tracker_api/
├── 📁 config/
│   └── database.php (MySQL DB connection)
│
├── 📁 models/
│   ├── User.php
│   ├── Transaction.php
│   └── Category.php
│
├── 📁 controllers/
│   ├── register.php
│   ├── login.php
│   ├── add_transaction.php
│   ├── get_transactions.php
│   ├── get_report.php
│   └── sync_data.php
│
├── 📁 helpers/
│   └── auth.php (JWT or token verification)
│
├── 📁 utils/
│   └── sanitizer.php
│
├── 📁 uploads/
│   └── (if users export reports)
│
├── .htaccess
└── index.php
```
---
## 🗃️ MySQL Database Structure

### `users` table

| Column      | Type        | Description         |
|-------------|-------------|---------------------|
| id          | INT (PK)    | User ID             |
| name        | VARCHAR     | Full name           |
| email       | VARCHAR     | Email address       |
| password    | VARCHAR     | Hashed password     |
| phone       | VARCHAR     | Mobile number       |
| created_at  | TIMESTAMP   | Account creation    |

### `transactions` table

| Column     | Type       | Description                       |
|------------|------------|-----------------------------------|
| id         | INT (PK)   | Transaction ID                    |
| user_id    | INT (FK)   | Linked to `users.id`              |
| amount     | DECIMAL    | Transaction amount                |
| category   | VARCHAR    | Spending category                 |
| merchant   | VARCHAR    | Merchant or payee name            |
| upi_id     | VARCHAR    | UPI ID (if available)             |
| type       | VARCHAR    | Debit/Credit                      |
| date       | DATETIME   | Transaction date                  |
| notes      | TEXT       | Optional user notes               |

### `categories` table

| Column     | Type       | Description                                |
|------------|------------|--------------------------------------------|
| id         | INT (PK)   | Category ID                                |
| name       | VARCHAR    | Category name (e.g., Food, Travel)         |
| icon       | VARCHAR    | Icon or emoji name                         |
| user_id    | INT (nullable) | Null for default, user ID for custom |

---

## 🔄 API Endpoints (Sample)

| Endpoint              | Method | Description                              |
|-----------------------|--------|------------------------------------------|
| `/register.php`       | POST   | Register a new user                      |
| `/login.php`          | POST   | Login and receive auth token             |
| `/add_transaction.php`| POST   | Add a new transaction                    |
| `/get_transactions.php`| GET   | Get all transactions for a user          |
| `/get_report.php`     | GET    | Fetch weekly/monthly spend stats         |
| `/sync_data.php`      | POST   | Sync offline transactions to server      |

---

## 🔐 Security

- 🔑 Use **token-based authentication** (JWT or session tokens)
- 🛡️ Validate all input on the **server-side**
- 🔒 Always use **HTTPS** for API communications
- 🧹 Sanitize user input to avoid SQL injection/XSS attacks
- 🔐 Store passwords using hashing algorithms like **bcrypt**

---

## 🎯 Target Audience

- 🎓 College students
- 👨‍💼 Working professionals
- 🧾 Small business owners
- 👩‍🍳 Homemakers managing household budgets

---

## 💸 Monetization Ideas

- **Freemium Model**: Free basic features, Pro version for ₹49/month
- **Non-intrusive Ads** via Google AdMob
- **Affiliate Links**: Credit cards, loans, savings plans
- **Subscription Perks**: Advanced analytics, Excel export, cloud sync, smart insights

---

## 🧠 Bonus Ideas

- 🤝 Split bills with friends
- 📤 Export expense reports for tax filing
- 🧠 Smart suggestions (recharge offers, budget tweaks)
- 🌐 Multi-language support: Hindi, Bengali, Tamil, more

---

## 📱 Coming Soon

- iOS version
- Voice assistant for expense queries
- Dark mode UI
- OCR-based receipt tracking

---

## 👨‍💻 Contributing

Got an idea or want to contribute? Fork this repo and raise a pull request or open an issue!

---

## 📬 Contact

For partnerships, suggestions, or feedback, reach out at:  
📧 **hello@skwasimakram.com**

---

## ⭐ Show Your Support

If you like this project, give it a ⭐ on GitHub and share it with your friends and family!

---

## License
This project is licensed under the MIT License.

---

## Author
**Develope By** - [Sk Wasim Akram](https://github.com/skwasimakram13)

- 👨‍💻 All of my projects are available at [https://skwasimakram.com](https://skwasimakram.com)

- 📝 I regularly write articles on [https://blog.skwasimakram.com](https://blog.skwasimakram.com)

- 📫 How to reach me **hello@skwasimakram.com**

- 🧑‍💻 Google Developer Profile [https://g.dev/skwasimakram](https://g.dev/skwasimakram)

- 📲 LinkedIn [https://www.linkedin.com/in/sk-wasim-akram](https://www.linkedin.com/in/sk-wasim-akram)

---

> _“Take control of your paisa, with PaisaTrack!”_
