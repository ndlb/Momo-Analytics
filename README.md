# MoMo User Retention Analysis and Loyalty Program Evaluation

## A. Overview

This project involves analyzing MoMo’s user retention and evaluating the effectiveness of the "MoMo Refund" loyalty program, which was launched on January 1st, 2022. The analysis aims to optimize cashback costs while maintaining or improving user retention. The file **Momo Analytics.pdf** is a presentation detailing the methods, data processing steps, and findings related to this project.

## B. Data Source

The data for this project includes daily transaction history from January 2021 to March 2022 and the loyalty program's rules, provided in two tables:

- **Transactions Table**: Contains information on user transactions.
- **Loyalty Points and Benefits Tables**: Define how users earn points and receive cashback.

### Transactions Table Schema:
| Column        | Data Type | Description                                                  |
|---------------|-----------|--------------------------------------------------------------|
| User_id       | int       | Unique identifier for each user.                             |
| Order_id      | int       | Unique identifier for each transaction.                      |
| Date          | date      | Date of the transaction.                                     |
| GMV           | int       | Gross Merchandise Value (amount spent in VND).               |
| Service Group | str       | Group of services where the user spent money.                |
| Merchant_id   | int       | Unique identifier for the merchant involved in the transaction. |

### Loyalty Points Table Schema:
| Column         | Data Type | Description                                                   |
|----------------|-----------|---------------------------------------------------------------|
| Service Group  | str       | Group of services where users earn loyalty points.             |
| Point Mechanism| int       | Points earned per 1000 VND spent.                              |
| Max Points     | int       | Maximum points that can be earned in a single transaction.     |

### Loyalty Benefits Table Schema:
| Column         | Data Type | Description                                                   |
|----------------|-----------|---------------------------------------------------------------|
| Class ID       | int       | User rank ID based on loyalty points (Standard, Silver, etc.). |
| % Cashback     | int       | Percentage of cashback for transactions in each service group. |

## C. Requirements

### Part 1: Data Processing
1. Combine the 'Transactions' table with the 'Loyalty Points' table.
2. Create a table 'Loyalty Ranking' to calculate user ranks based on loyalty points.
3. Determine how many users achieved the rank of Gold by the end of March 2022.

### Part 2: Analyze and Comment
1. Analyze user retention trends since the loyalty program launched.
2. Propose strategies to optimize cashback costs while maintaining GMV growth and retention.

### Part 3: Extended Questions
1. Provide ideas for developing MoMo's loyalty program.
2. Implement a gamification strategy by calculating streaks of DIAMOND rank users.
