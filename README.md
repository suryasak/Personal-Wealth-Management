## Personal-Wealth-Management
This database schema is designed is to create personal wealth management by tracking income, expenditures, Investments, and goals for individuals. By tracking the goals and financials, we will be able to recommend adjustments when necessary and to provide the net worth of the customers. A personal wealth management system will also help in producing solutions if the individual is going through a personal or monetary crisis that leaves them with a lot of debt and in the way of savings.

**Database Schema**

* **`user_account_type_t`:** Defines different types of user accounts (e.g., Primary, Self, Joint, Family).
* **`employment_category_t`:** Categorizes different employment types (e.g., Salaried, Business, Agriculture, Vendor).
* **`users_t`:** Stores user information (e.g., name, gender, date of birth, SSN, address, contact information).
* **`user_bank_account_t`:** Stores details of user bank accounts (e.g., bank name, account type, account number, routing number, available balance).
* **`expense_category_t`:** Categorizes different types of expenses (e.g., ATM/Cash, Entertainment, Electricity, Food, etc.).
* **`expenses_t`:** Records user expenses (e.g., transaction ID, user ID, transaction time, expense category, transaction location, amount).
* **`income_t`:** Stores user income information (e.g., account ID, income date, income source, salary, employment category, bonus included).
* **`family_member_t`:** Stores information about user's family members (e.g., member ID, user ID, name, gender, date of birth, income, relationship, member type).
* **`liabilities_categories_t`:** Categorizes different types of liabilities (e.g., Credit Card, Personal Loan, Home Loan, etc.).
* **`liabilities_t`:** Records user liabilities (e.g., loan ID, user ID, liability category, sanctioned amount, interest rate, loan tenure, date of loan sanction, outstanding amount, EMI).
* **`investment_categories_t`:** Categorizes different types of investments (e.g., Shares/Stocks, Real Estate, Gold, Deposits/Fixed interest, Bonds, Cash).
* **`investments_t`:** Records user investments (e.g., user ID, investment ID, investment category, date of investment, investment type, amount).

**Views and Procedures**

* **Views:**
  - `salary_v`: Calculates total salary for each user.
  - `liability_v`: Calculates total outstanding amount for each user.
  - `invest_v`: Calculates total investments for each user.
  - `expense_v`: Calculates total expenses for each user.
  - `networth`: Calculates net worth for each user based on salary, investments, liabilities, and expenses.

* **Procedures:**
  - `expense_level`: Estimates the expense level of a user based on their total expenses.
  - `check_liabilities`: Checks if a user's liabilities are greater than their investments.
  - `avg_monthly_investments`: Calculates average monthly investments for each user.
  - `total_monthly_expenses`: Calculates total monthly expenses for essential categories for each user.

**Functions**

- `simple_interest`: Calculates simple interest.
- `compound_interest`: Calculates compound interest.
- `is_over_draft`: Checks if a bank account has a positive balance.

**Triggers**

- `Check_age`: Checks if the user's age is at least 18 before inserting a new user.
- `Backup`: Creates a backup of the `liabilities_t` table before deleting a row.
- `after_income_update`: Tracks changes in income.
- `track_address_change`: Tracks changes in user addresses.
