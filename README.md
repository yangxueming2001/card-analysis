# Wise Card Program Analysis

## Overview
This project analyzes transaction-level data from a card program to understand profitability, customer lifetime value (LTV), and market performance.

The goal is to identify key drivers of revenue and cost, evaluate unit economics across transaction types, and recommend strategies to improve profitability.

---

## Problem Statement
The analysis focuses on three main questions:

1. What is the average profit for each transaction type?
2. What is the estimated 12-month lifetime value (LTV) of customers?
3. How are different markets performing, and where are the growth opportunities?

---

## Methodology

### Data Preparation
- Filtered to successful transactions only
- Joined multiple tables:
  - Transactions
  - Cards
  - Cost structure
  - FX rates

### Profit Calculation
Profit per transaction is defined as:


- Interchange revenue converted to GBP using FX rates
- Conversion revenue calculated when billing currency differs from transaction currency
- Fixed and variable costs mapped using transaction type and region

### LTV Estimation
- Aggregated profit per user over observed time window
- Annualised profit to estimate 12-month LTV:

  
- Inactive users (no transactions) treated as £0

---

## Key Findings

### 1. Transaction-Level Profitability
- **ECOM purchases** are the most profitable (high interchange, favourable cost structure)
- **POS purchases** are marginally profitable but high volume
- **ATM withdrawals** are significantly loss-making due to:
  - negative interchange
  - high variable costs

### 2. Customer Lifetime Value
- The card program is overall loss-making on a per-user basis
- Active users generate negative LTV due to ATM costs
- ~65% of cards show no activity, masking true performance

### 3. Market Performance
- Profitability varies significantly across markets
- Driven primarily by:
  - FX usage
  - average spend
  - transaction scale

- Some markets are profitable (e.g. Spain)
- Others are loss-making at scale (e.g. UK)

---

## Recommendations

- Reduce ATM usage (largest cost driver)
- Increase digital transaction share (ECOM, POS)
- Target high-value users with low FX usage
- Expand in markets with strong unit economics

---

## Tools Used
- SQL (SQLite) — data extraction and transformation
- Python (pandas, matplotlib) — analysis and visualisation

---

## Files
- `wise_card_analysis.ipynb` — full analysis workflow
- `slides.pdf` — presentation of findings

---

## Notes
This project is based on a case study dataset and is intended for analytical demonstration purposes.
