# Data Dictionary

## gold.dim_customer

| Column        | Description                    |
|---------------|-------------------------------|
| customer_key  | Surrogate key (PK)            |
| customer_id   | Source customer ID            |
| full_name     | Customer's full name          |
| address       | Customer address              |
| gender        | Gender (M/F/O)                |
| phone_number  | Phone number                  |
| email_id      | Email address                 |
| birthdate     | Date of birth                 |
| create_date   | Customer creation date        |

## gold.dim_account

| Column         | Description                   |
|----------------|------------------------------|
| account_key    | Surrogate key (PK)           |
| account_number | Source account number        |
| customer_id    | Related customer_id (attr)   |
| account_type   | Type (savings, current, etc) |
| open_date      | Account open date            |
| close_date     | Account close date           |
| branch_id      | Branch identifier            |
| branch_name    | Branch name                  |
| zone           | Branch zone                  |

## gold.fact_transaction

| Column               | Description                           |
|----------------------|---------------------------------------|
| transaction_id       | Transaction unique ID                 |
| transaction_date     | Date of transaction                   |
| customer_key         | FK to dim_customer                    |
| account_key          | FK to dim_account                     |
| transaction_type     | Debit/Credit/Other                    |
| transaction_code     | Transaction code                      |
| transaction_subtype  | Subtype (NEFT, RTGS, etc)             |
| transaction_channel  | Channel (branch, online, ATM, etc)    |
| amount               | Transaction amount                    |
| account_balance      | Balance after transaction             |