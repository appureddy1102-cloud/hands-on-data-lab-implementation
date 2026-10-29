# Dataset: synthetic retail sales

`synthetic_sales.csv` is an original, simulated dataset created for this project, not an external or real sales dataset. It may be reused under CC0 1.0 (https://creativecommons.org/publicdomain/zero/1.0/). It contains 180 generated daily transactions from 2025-01-01 through 2025-06-29, plus two exact duplicate rows (182 rows total). Four units values were deliberately made missing. The RNG seed was 42; category probabilities are 0.35 accessories, 0.40 clothing, 0.25 electronics; units are integers from 1 through 6 before missingness. Fixed category prices are $15, $30, $80.

Columns: transaction_id (identifier), date (ISO date), category (text), units (numeric, missing allowed), unit_price_usd (USD). Gross revenue is computed during analysis. A transaction per day, fixed prices, no costs, discounts, returns, customers or real-world sampling make this educational rather than representative.
