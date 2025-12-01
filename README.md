# Supermarket Chips Sales Dataset - Student Guide

## Project Overview
We're analyzing chip (crisp) purchases from a large supermarket chain. This dataset helps us understand:
- What types of chips customers buy
- When and where they buy them
- Who is buying (customer demographics)
- How much different customer groups spend

## The Two Main Tables

### Table 1: `transactions` - "The Receipt Data"
Each row represents one line item from a shopping receipt.

**Example Receipt to Rows:**
A receipt from July 5, 2025 at Store 5 for Customer 1234:
- 2 × Smiths Chips Chicken 170g – $5.80
- 1 × Doritos Cheese 200g – $3.00

This becomes two rows in the transactions table.

**Key Columns:**
- `DATE`: Purchase date
- `STORE_NBR`: Store number (e.g., Store 1, Store 88)
- `LYLTY_CARD_NBR`: Customer's loyalty card number
- `TXN_ID`: Unique receipt ID (same for all items bought together)
- `PROD_NBR`: Product code
- `PROD_NAME`: Product description (brand + flavor + size)
- `PROD_QTY`: Number of packs purchased in this line
- `TOT_SALES`: Total amount paid for this line (price × quantity)

**One row means:** "On this date, at this store, this customer bought this many packs of this specific chip product and paid this amount."

### Table 2: `customer_behaviour` - "The Customer Profile"
Each row represents one customer (one loyalty card holder).

**Key Columns:**
- `LYLTY_CARD_NBR`: Loyalty card number (links to transactions)
- `LIFESTAGE`: Customer life stage group:
  - "YOUNG SINGLES/COUPLES"
  - "YOUNG FAMILIES"
  - "MIDAGE SINGLES/COUPLES"
  - "OLDER FAMILIES"
  - "RETIREES"
- `PREMIUM_CUSTOMER`: Spending category:
  - "Budget" – prefers cheaper options
  - "Mainstream" – average shopper
  - "Premium" – prefers higher-priced brands

**One row means:** "Customer with card number X is in this life stage group and shops in this spending category."

## How the Tables Connect

The two tables are linked by the `LYLTY_CARD_NBR` (loyalty card number).

```
Customer Profile → Many Transactions
(customer_behaviour)   (transactions)
      ↓                       ↓
"Who they are"        "What they bought"
```

## Real-World Analogy

Think of this as the supermarket's memory system:
1. **Transactions table** = Every line on every receipt saved in the system
2. **Customer table** = The information collected when customers signed up for their loyalty card

## Data Science Concepts

**Entities (Things in the Data):**
- Customers (in customer_behaviour)
- Transactions (shopping trips)
- Products (chip varieties)
- Stores (locations)

**Table Granularity (Level of Detail):**
- `customer_behaviour`: One row per customer
- `transactions`: One row per product per shopping trip

**Relationships:**
- One customer → Many transactions (one person shops many times)
- One transaction → Many rows (one receipt has multiple products)
- One store → Many transactions (many sales per store)
- One product → Many transaction rows (same product sold many times)

## Why This Structure Matters

This is exactly how real supermarkets organize their data. With these two tables joined together, we can answer questions like:
- Do young families buy different chips than retirees?
- Do premium customers spend more per purchase than budget customers?
- Which life stage buys the most chips in total?
- Are certain chip brands popular with specific customer types?

## How to Think About Analysis

When you work with this data, remember:
1. **Customer perspective**: "What do different types of people buy?"
2. **Product perspective**: "Who buys each type of chip?"
3. **Store perspective**: "Which stores sell the most chips?"
4. **Time perspective**: "When do people buy chips?"

This dataset gives you real-world experience with relational data, similar to what data analysts use in retail companies every day.
