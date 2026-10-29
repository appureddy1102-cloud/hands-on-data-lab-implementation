# Viva preparation

1. **Why synthetic data?** It avoids personal data and makes the exercises reproducible; it does not represent real customers.
2. **Why remove duplicates?** Exact duplicates would count the same recorded transaction twice and inflate totals.
3. **Why use category medians for missing units?** They provide a simple category-specific estimate, but can reduce variability and are not true recovered values.
4. **What is gross revenue?** Units multiplied by unit price, before costs, tax, discounts or returns.
5. **Mean versus median?** Mean averages all values; median is the middle value and is less affected by extreme values.
6. **Sample versus population variance?** Sample variance divides by n−1; population variance divides by n.
7. **What is an IQR outlier?** A value below Q1−1.5×IQR or above Q3+1.5×IQR; a flag is not proof of error.
8. **Does correlation prove causation?** No. Pearson correlation describes linear association, not cause and effect.
9. **Why validate the merge?** A many-to-one check prevents duplicate lookup keys from multiplying transaction rows.
10. **Why can monthly totals differ without a trend?** Months have different lengths and category mixes; simulated random variation also matters.
