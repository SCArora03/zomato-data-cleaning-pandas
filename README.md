# zomato-data-cleaning-pandas
Cleaned a 51K-row Zomato dataset using Pandas — removed duplicates, nulls, and irrelevant columns
# Zomato Dataset Cleaning (Pandas)

## Overview
Cleaned a raw Zomato restaurant dataset using Python and Pandas in Jupyter Notebook, reducing it from 51,717 to 8,250 high-quality entries by removing duplicate records, irrelevant columns, and rows with missing data.

## Objective
Prepare a messy, real-world restaurant dataset for downstream analysis (e.g. rating and pricing trends, online ordering behavior) by resolving data quality issues across pricing, ratings, and categorical fields.

## Tools Used
- Python, Pandas, Jupyter Notebook

## Original Columns (17)
`url, address, name, online_order, book_table, rate, votes, phone, location, rest_type, dish_liked, cuisines, approx_cost(for two people), reviews_list, menu_item, listed_in(type), listed_in(city)`

## Final Columns (6)
`Name, Online_order, Book_table, Rate, Dish_liked, Approx_cost(for two people)`

## Cleaning Steps
1. **Dropped 11 irrelevant columns** not needed for the intended analysis — `url`, `address`, `votes`, `phone`, `location`, `cuisines`, `rest_type`, `reviews_list`, `menu_item`, `listed_in(type)`, `listed_in(city)`
2. **Renamed remaining columns** to a consistent capitalized format (e.g. `name` -> `Name`)
3. **Removed duplicate rows** -- 32,808 duplicate entries dropped
4. **Removed rows with missing values** in `Rate` (2,418 missing), `Dish_liked` (10,587 missing), and `Approx_cost(for two people)` (140 missing)
5. **Reset the index** after row removal to keep it continuous
6. **Cleaned the `Rate` column** -- stripped extra whitespace and reformatted values from `"4.1/5"` style to a more readable `"4.1 out of 5"` format
7. **Converted `Online_order`** from Yes/No text to binary (1/0) for easier downstream analysis

## Result
| Metric | Before | After |
|---|---|---|
| Rows | 51,717 | 8,250 |
| Columns | 17 | 6 |

**Why the drop:** ~63% of the removed rows were exact duplicates; the remaining drop came from rows missing values in key fields (`Rate`, `Dish_liked`, `Approx_cost`).

## How to Use
1. Open `Zomato.ipynb` in Jupyter Notebook
2. Update the file path in the first `pd.read_csv(...)` cell to point to your local copy of `zomato.csv`
3. Run all cells top to bottom
4. Cleaned output is saved as `Cleaned Data.csv`

## Possible Next Steps
- Convert `Rate` into a numeric column (e.g. extract just `4.1` as a float) to enable rating-based analysis and visualization
- Convert `Book_table` to binary (1/0), matching the `Online_order` treatment
## Dataset Source
Raw dataset sourced from Kaggle: [Zomato Dataset](https://www.kaggle.com/datasets/rishikeshkonapure/zomato)

Raw file not included in this repo due to size — download it from the link 
above and place it in the same folder as `Zomato.ipynb` to reproduce the cleaning.
