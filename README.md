# Coffee-Sales-SQL
Brief analysis of detailed coffee sales records from a vending machine with key insights and additional visualization in Google Sheets

## Summary
The dataset being observed contains detailed records of coffee sales from a vending machine. The dataset spans from March 2024 to March 2025, capturing daily transaction data.

### Input Format:
| *Colomn* | *Type* |
| ----------- | ----------- |
| date | DATE |
| datetime | TIMESTAMP |
| cash_type | STRING |
| card | STRING |
| money | FLOAT |
| coffe_name | STRING |

Where:
- **date** - date of purchasing (date format: 'yyyy-mm-dd');
- **datetime** - date and time of purchasing;
- **cash_type** - type of transaction made (with cash or card);
- **card** - anonymous card number (card format: 'ANON-0000-0000-XXXX') if transaction was made with card. If it was made with cash, the cell is empty;
- **money** - the amount of money in Ukrainian hryvnias paid for a specific type of coffee;
- **coffee_name** - a type of coffee a customer paid for (latte, americano, hot chocolate, etc).

### Input Sample Data:
<img width="1061" alt="Screenshot 2025-04-07 at 22 56 42" src="https://github.com/user-attachments/assets/1e02cf3c-5caf-4b67-8107-9b0913c44db8" />

## Data Exploration
Given this dataset, a **Google BigQuery** data warehouse and **SQL** was used for finding key metrics and generating interesting insights for further analyses. Overall, the following questions were answered:
1. How much revenue does the business generated and how many purchases were made over each month recorded?
2. What type of coffee was the most popular each month?
3. How much does the business make per day on average?
4. What percent do cash transactions constitute?
5. What is the popularity of each coffee type (by purchases) over the whole period?
6. What is the most favourite type of coffee of the best customer? (In this case, the best customer is the customer who made the most purcheses over the whole period)

## Key Techniques and Approaches
1. Data formating for easier futher aggregation (`FORMAT_DATE('%Y-%m', date)`);
2. Aggregation functions, rounding, grouping (`SUM()`,`MIN()`, `MAX()`, `COUNT()`, `ROUND()`, `GROUP BY`, etc);
3. Date difference to find total number of days (`DATE_DIFF(MAX(date), MIN(date), DAY)`);
4. Window functions (`ROW_NUMBER() OVER()`);
5. Nested queries (in `WHERE` and `FROM`);
6. Common table expressions (`WITH`).

Moreover, on the basis of the same dataset, utilizing similar approaches, a fully interactive dashboard in Google Sheets was created. The in-depth exploration of coffee sales with visualized data is available via [this link](https://docs.google.com/spreadsheets/d/1pExpI77uPN_4s_CcLldUqN2pxo6pB3kJs7eNnuEgDFs/edit?usp=sharing).
