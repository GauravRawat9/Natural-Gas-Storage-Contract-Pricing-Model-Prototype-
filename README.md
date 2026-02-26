# Natural-Gas-Storage-Contract-Pricing-Model-Prototype


## 📌 Overview

This project implements a prototype pricing model for a Natural Gas Storage Contract.  
The model evaluates the value of a storage contract based on injection and withdrawal strategies, commodity prices, storage constraints, and costs.

This prototype is designed for validation and testing purposes before potential production deployment.  
Currently, it supports manual oversight for exploring contract pricing scenarios.

---

## 🧠 Problem Statement

We need to price a gas storage contract where:

- A client can inject gas on multiple dates
- A client can withdraw gas on multiple dates
- Gas is bought/sold at market prices on those dates
- Storage capacity is limited
- Injection and withdrawal rates are capped
- Storage costs apply
- No interest rates
- No transport delay
- No holiday adjustments

The goal is to compute the total contract value based on all cash flows.

---

## ⚙️ Model Assumptions

- Zero interest rates
- No transport delay
- No transaction costs (other than storage cost)
- Storage cost charged per unit per month
- Market holidays/weekends ignored
- Prices must exist for selected dates

---

## 📥 Inputs

The pricing function takes:

- `file_path` → CSV file containing price data  
- `injection_dates` → List of dates to inject gas  
- `withdrawal_dates` → List of dates to withdraw gas  
- `injection_rate` → Max gas volume injected per date  
- `withdrawal_rate` → Max gas volume withdrawn per date  
- `max_storage` → Maximum storage capacity  
- `storage_cost_per_unit_per_month` → Monthly storage cost per unit  

---

## 📤 Output

- Returns the **total contract value (cash flow)**  
- Positive → Profit  
- Negative → Loss  

---

## 🏗️ Methodology

1. Load and clean historical price data
2. Convert dates to datetime format
3. Simulate inventory changes over injection and withdrawal dates
4. Track:
   - Gas purchases (negative cash flow)
   - Gas sales (positive cash flow)
   - Inventory levels
5. Apply storage cost across inventory history
6. Return total net cash flow

---


        total_cashflow -= inv * storage_cost_per_unit_per_month
    
    return total_cashflow
