# 📊 Oracle SQL Billing Gap Detection

## 📌 Project Overview

This project uses **Oracle SQL** to detect missing billing periods based on a service's billing frequency (e.g., Monthly, Quarterly, Half-Yearly, Yearly). It is useful for domains like **telecom**, **utilities**, or **finance**, where consistent billing is essential.

---

## 🛠️ Tools & Technologies

- **Database:** Oracle SQL
- **SQL Concepts:** CTEs, `CONNECT BY`, `LEVEL`, Date Arithmetic
- **Use Case:** Business Intelligence, Billing Audit, Revenue Assurance

---

## 📂 Table Structure: `billing_cleaned`

| Column Name              | Description                                 |
|--------------------------|---------------------------------------------|
| `logical_id`             | Unique customer or service identifier       |
| `bill_freq`              | Billing frequency: Monthly, Quarterly, etc. |
| `bill_period_start_date`| Start of the billing period (DATE)          |
| `bill_period_end_date`  | End of the billing period (DATE)            |
| `amount` (optional)      | Amount billed for that period               |

---

## 🧠 Query Logic

### 🔹 Step 1: `base_data`
Get each logical ID’s min and max billing period based on frequency.

### 🔹 Step 2: `date_series`
Generate all expected billing period start dates using `CONNECT BY LEVEL`.

### 🔹 Step 3: `final_missing`
Find missing billing periods by comparing generated dates to existing billing data.

---

## 📈 Output Columns

| Column Name     | Description                             |
|------------------|-----------------------------------------|
| `logical_id`     | Customer/service account                |
| `bill_freq`      | Billing frequency                       |
| `expected_start` | Missing billing period start date       |
| `expected_end`   | Expected end of that billing period     |

---

## 🔄 Sample Use Case

If a customer has billing entries for Jan, Feb, and April, the query will detect **March** as missing (if the frequency is Monthly).

---

## ▶️ How to Run

1. Load your billing data into a table named `billing_cleaned`.
2. Paste and run the full SQL script in Oracle SQL Developer or any Oracle DB interface.
3. View the output sorted by logical ID and billing date.

---

## 🧪 Optional Sample Data

```sql
CREATE TABLE billing_cleaned (
    logical_id VARCHAR2(50),
    bill_freq VARCHAR2(20),
    bill_period_start_date DATE,
    bill_period_end_date DATE,
    amount NUMBER
);

INSERT INTO billing_cleaned VALUES ('A101', 'Monthly', DATE '2024-01-01', DATE '2024-01-31', 500);
INSERT INTO billing_cleaned VALUES ('A101', 'Monthly', DATE '2024-02-01', DATE '2024-02-29', 500);
INSERT INTO billing_cleaned VALUES ('A101', 'Monthly', DATE '2024-04-01', DATE '2024-04-30', 500);
```

---

## 📌 Author

**Akashh Dixit**  
BI Specialist & Data Analyst | Oracle SQL | Power BI | Excel Automation  
📩 [dixitakashh@gmail.com](mailto:dixitakashh@gmail.com)  
🔗 [LinkedIn](https://www.linkedin.com/in/akash-dixit-bbb3b5170/)


