# 🔌 Fintech API Testing — Postman Portfolio Project

> API test collection simulating core banking scenarios — Login, Fund Transfer, and Loan Application.
> Built with Postman · Newman · JavaScript test scripts

---

## 📌 What This Project Tests

This collection covers 3 main flows that are common in any banking or fintech API:

- **Auth** — login with valid and invalid credentials
- **Fund Transfer** — create transfer, check duplicate, test boundary amounts
- **Loan Application** — submit loan, test missing fields, test invalid data

The base URL is **reqres.in** — a free public API I used to simulate real endpoint behavior.
The test logic (status codes, response fields, negative cases) reflects what I tested professionally at Yoma Bank.

---

## 📁 Folder Structure

```
fintech-api-testing/
│
├── collections/
│   └── fintech_banking_api.json    ← import this into Postman
│
├── reports/
│   └── newman-report.html          ← generated after running Newman
│
├── .gitignore
├── requirements.txt
└── README.md
```

---

## ⚙️ How To Run

### Option 1 — Postman (manual)

1. Open Postman
2. Click **Import**
3. Choose `collections/fintech_banking_api.json`
4. Click **Run collection**

---

### Option 2 — Newman (command line)

Install Newman:
```
npm install -g newman
npm install -g newman-reporter-htmlextra
```

Run the collection:
```
newman run collections/fintech_banking_api.json -r htmlextra --reporter-htmlextra-export reports/newman-report.html
```

Then open `reports/newman-report.html` in your browser to see the full report.

---

## 🧪 Test Cases Summary

| # | Folder | Test Name | Type |
|---|--------|-----------|------|
| 1 | Auth | Login with valid credentials | Positive |
| 2 | Auth | Login with wrong password | Negative |
| 3 | Auth | Login with empty email | Negative |
| 4 | Fund Transfer | Create a successful transfer | Positive |
| 5 | Fund Transfer | Duplicate transaction check | Negative |
| 6 | Fund Transfer | Transfer amount below minimum | Boundary |
| 7 | Fund Transfer | Transfer amount above maximum | Boundary |
| 8 | Loan Application | Submit valid loan application | Positive |
| 9 | Loan Application | Submit with missing required field | Negative |
| 10 | Loan Application | Submit with invalid token | Negative |

---

## 🧠 What I Focused On

**Negative cases are the priority.**
In banking, the happy path usually works fine. What breaks things is edge cases — duplicate transactions, expired tokens, amounts that hit system limits. That's where I spent most of my testing time at Yoma Bank, and I followed the same approach here.

**Every request has test scripts.**
Not just status code checks — I also check response body fields, data types, and error messages. This is what separates a real API test from just "clicking send".

**Tests are readable.**
I wrote the test names in plain English so anyone reading the report can understand what passed and what failed without needing to dig into the code.

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| Postman | Build and run API tests |
| Newman | Run collection from command line |
| newman-reporter-htmlextra | Generate HTML report |
| reqres.in | Public mock API (simulates real endpoints) |
| JavaScript | Test scripts inside Postman |

---

## 🙋 Author

**Htuu Will Oo**
[GitHub](https://github.com/hwilltester) · [LinkedIn](https://linkedin.com/in/htuuwill)
