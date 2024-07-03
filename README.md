# MoMo User Retention Analysis and Loyalty Program Evaluation

## A. Data Source

Users' retention has always been one of the key targets that MoMo is striving to improve. A Loyalty program called "MoMo Refund", one of the projects aiming to achieve such a goal, was launched on January 1st, 2022.

The data given include their daily transaction history data during Jan 2021 - Mar 2022 (table 'Transactions'), and the Loyalty program's rules (tables 'Loyalty Points' and 'Loyalty Benefits') to measure and analyze trends.

### Given Data:

#### Transactions
| User_id | Order_id | Date       | GMV    | Service Group | Merchant_id |
|---------|----------|------------|--------|---------------|-------------|
| 123     | 234      | 01/17/2020 | 100000 | supermarket   | 12          |
| ...     | ...      | ...        | ...    | ...           | ...         |

**Schema:**
- **User_id:** Each user in MoMo will be given a unique ID.
- **Order_id:** Each transaction will be given a unique ID.
- **Date:** Date on which the transaction takes place.
- **GMV (Gross Merchandise Value):** Total amount of money that the user spends (VND).
- **Service Group:** Group services that users spend on.
- **Merchant_id:** Each merchant will be given a unique ID.

#### Loyalty Points
| Service Group | Point Mechanism           | Maximum Point Per Trans |
|---------------|---------------------------|-------------------------|
| supermarket   | 1 point / 1000 VND GMV    | 500 points              |
| data          | 10 points / 1000 VND GMV  | 1000 points             |
| ...           | ...                       | ...                     |

**Schema:**
- **Service Group:** Group services that users spend on.
- **Point Mechanism:** Each group service will be given a specific rule to calculate the accumulated points in the loyalty program.
- **Maximum Point Per Trans:** Limit of how many points a user can get for one transaction.

#### Loyalty Benefits
| Class ID | Group          | % Cashback |
|----------|----------------|------------|
| 1        | cvs            | 5%         |
| 2        | offlinebeverage| 5%         |
| 3        | ...            | ...        |

**Schema:**
- **Class ID:** Users' ranking ID according to the amount of loyalty points accumulated.
- **% Cashback:** Percentage amount of money that returns to the user's wallet after spending on a MoMo service. 
  - Example: User A spends 100,000 VND on a supermarket service. User A then receives 5,000 VND (5%) cashback to their wallet.

## B. Requirements

### Part 1: Data Processing
1. **Combine with the 'Loyalty Points' table:**
    - Add a column 'Loyalty Points' in the 'Transactions' table with the given rules.
    - Create another table named 'Loyalty Ranking' which includes columns 'Rank_name' and 'Calculated_points' to calculate the rank of each user on a daily basis.
    - At the end of Mar 2022, determine how many users achieved the rank of Gold.
    
    **Ranking rules:**
    | Class ID | Rank_name | Loyalty Points         |
    |----------|-----------|------------------------|
    | 1        | STANDARD  | 1 - 999 points         |
    | 2        | SILVER    | 1000 - 1999 points     |
    | 3        | GOLD      | 2000 - 4999 points     |
    | 4        | DIAMOND   | >= 5000 points         |
    
    **Important Notes:**
    - Points calculated for each transaction will expire after 30 days since the day the transaction is made.
    - User's rank will be reduced or increased according to the change in their accumulated loyalty points.

2. **Combine with the 'Loyalty Benefits' table and 'Loyalty Ranking' table:**
    - Add a column '%cashback' in the 'Transactions' table and calculate the total cashback cost in February 2022.
    
    **Notes:**
    - Cashback cost can be calculated by multiplying %cashback with GMV.
    - Users can only claim a maximum of 10,000 VND per transaction.

3. **Design a retention chart:**
    - Monitor since the program was launched.

### Part 2: Analyze and Comment
1. **User retention and transaction behavior:**
    - Analyze trends since the Loyalty program launched.
    - Provide advice for the Marketing department in designing promotion campaigns to increase user retention performance monthly.

2. **Optimization of cashback cost and GMV:**
    - Propose ideas to change the schemes of Loyalty benefits and Loyalty Points to alleviate the cost amount while maintaining the growth of GMV and increasing the retention rate.

### Part 3: Extended Questions
1. **Loyalty program development strategy:**
    - Provide ideas for MoMo's loyalty program development strategy.

2. **Gamification Strategy:**
    - Calculate the number of winners who maintained a 20-day or longer streak of being in the DIAMOND ranking during the last thirty days (March 01 - March 31).
    - Identify the user(s) who maintained the longest streak during that time.
