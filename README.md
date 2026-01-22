# UPI Transactions — Power BI Dashboard

Power BI report built on a UPI transactions dataset to analyze transaction volume and value, success vs failed performance, trends over time, and breakdowns by banks, merchants, cities, devices, payment methods, and customer demographics.

> Data source: `UPI_Transactions.xlsx` (Sheet1)

---

## Project goals

- Track **overall transaction performance** (total amount, number of transactions, success rate).
- Identify **time-based patterns** (daily/weekly/monthly trends, MoM change).
- Compare **success vs failed** transactions across key dimensions (bank, city, payment mode/type).
- Explore **merchant and purpose** drivers (Top N merchants, purpose distribution).
- Provide **drillthrough detail** for investigation and export.

---

## Dataset overview

| Metric | Value |
|---|---:|
| Records | 20,000 |
| Columns | 20 |
| Date range | 2024-01-01 → 2024-12-30 |
| Total Amount (sum) | 19,872,274.03 |
| Average Amount | 993.61 |
| Success Rate (Status = Success) | 80.0% |

**Cardinality highlights (approx. unique values):**  
BankNameSent=4, BankNameReceived=4, City=4, Gender=2, TransactionType=2, Status=2, DeviceType=3, PaymentMethod=3, MerchantName=5, Purpose=5, PaymentMode=2, Currency=4.

> Note: `CustomerAccountNumber` appears unique per row in this dataset, so “returning customer” style analytics (retention/cohorts) would require a separate customer dimension or a generated customer ID logic.

---

## Data dictionary (selected fields)

- **TransactionID**: Unique transaction identifier (key).
- **TransactionDate**: Transaction date (should link to a Date dimension).
- **TransactionTime**: Time (hh:mm:ss) — can be converted to Time type and used to derive Hour/Time bands.
- **Amount**: Transaction amount (numeric/decimal).
- **Currency**: Currency code (dimension/slicer).
- **Status**: Transaction status (`Success` / `Failed`).
- **TransactionType**: Type (e.g., `Transfer` / `Payment`).
- **PaymentMode**: Mode (e.g., `Instant` / `Scheduled`).
- **PaymentMethod**: Method (e.g., `QR Code`, etc.).
- **BankNameSent / BankNameReceived**: Sending/receiving bank (bank analysis).
- **City**: City dimension.
- **Gender**: Demographic dimension.
- **CustomerAge**: Customer age (used for grouping/banding).
- **DeviceType**: Device used (e.g., Mobile/Tablet/Desktop).
- **MerchantName**: Merchant dimension (Top N analyses).
- **Purpose**: Purpose/category (e.g., Food, etc.).
- **RemainingBalance**: Post-transaction balance (useful for outlier checks).
- **CustomerAccountNumber / MerchantAccountNumber**: Sensitive identifiers (recommended masking before publishing).

---
