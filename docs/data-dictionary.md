# Data Dictionary

## dim_customer

| Column        | Description                    |
|---------------|--------------------------------|
| customer_key  | Surrogate key (PK)             |
| customer_id   | Source customer ID             |
| full_name     | Customer's full name           |
| address       | Customer address               |
| gender        | Gender (e.g., M / F / Other)   |
| phone_number  | Customer phone number          |
| email_id      | Customer email address         |
| birthdate     | Date of birth                  |
| create_date   | Customer record creation date  |

---

## dim_account

| Column         | Description                                      |
|----------------|--------------------------------------------------|
| account_key    | Surrogate key (PK)                               |
| account_number | Source account number                            |
| customer_id    | Source customer ID                               |
| account_type   | Account type (savings, current, etc.)            |
| open_date      | Account open date                                |
| close_date     | Account close date (nullable if open)            |
| branch_id      | Branch identifier (business key)                 |
| branch_name    | Branch name                                      |
| zone           | Branch zone / region                             |

---

## dim_date

| Column        | Description                                  |
|---------------|-----------------------------------------------|
| full_date     | Full date (DD-MM-YYYY) (PK)                  |
| year          | Calendar year                                |
| quarter       | Calendar quarter (Q1, Q2, etc.)              |
| month         | Month number (1-12)                          |
| month_name    | Month name (Jan, Feb, etc.)                  |
| week_of_year  | ISO week number                              |
| day           | Day of month                                 |
| day_name      | Day name (Mon, Tue, etc.)                    |
| is_month_end  | Boolean flag; true if date is month end       |

---

## dim_transaction_code

| Column            | Description                                         |
|-------------------|-----------------------------------------------------|
| transaction_code  | Source transaction code ID (PK)                     |
| transaction_type  | High-level type (Debit / Credit / Other)            |
| subtype           | Subtype or category (Cash, POS, Transfer, etc.)     |
| channel           | Transaction channel (branch, mobile, internet, ATM) |
| description       | Human-readable description of the code              |

---

## fact_transaction

| Column            | Description                                         |
|-------------------|-----------------------------------------------------|
| transaction_id    | Transaction unique ID (PK)                          |
| transaction_time  | Timestamp of transaction (datetime)                 |
| transaction_date  | FK to `dim_date.full_date` (date of txn)            |
| customer_key      | FK to `dim_customer.customer_key`                   |
| account_key       | FK to `dim_account.account_key`                     |
| transaction_key   | FK to `dim_transaction_code.transaction_code`       |
| amount            | Transaction amount |
| account_balance   | Account balance after transaction                   |

---
