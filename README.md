# Clean the Netflix Dataset

A data cleaning project built with Python and Pandas, based on the
[roadmap.sh "Clean the Netflix Dataset" project](https://roadmap.sh/projects/cleaning-netflix-dataset).

## Project Description

This project loads the **Netflix Movies and TV Shows dataset** from Kaggle and cleans it using Pandas.
The raw dataset has missing values, wrong data types, and mixed-type columns — exactly the kind of mess
you find in real data.

The goal isn't just to drop nulls, but to understand *why* values are missing and make deliberate,
justified decisions about each column.

## Dataset

- Source: [Netflix Movies and TV Shows](https://www.kaggle.com/datasets/shivamb/netflix-shows) (Kaggle, by Shivam Bansal)
- Raw file: `netflix_titles.csv` (8,807 rows, 12 columns)
- Cleaned output: `netflix_titles_cleaned.csv` (8,797 rows, 16 columns, zero nulls)

## What This Project Does

- Inspects the DataFrame with `.info()`, `.describe()`, and `.head()`
- Identifies and handles missing values **column by column**, with reasoning for each decision:
  - `director` / `cast` / `country` → filled with `'Unknown'` (not guessable, too much data to drop)
  - `rating` → fixed a data-entry bug where 3 rows had a duration value shifted into the rating
    column, then filled the small number of remaining genuine gaps with the mode
  - `date_added` → dropped the 10 rows missing this value (negligible loss, no way to infer a date)
- Fixes the mixed-type `duration` column (`"90 min"` vs `"2 Seasons"`) by splitting it into a
  numeric `duration_value` and a `duration_unit`
- Parses `date_added` into a proper `datetime64` column, and derives `year_added` / `month_added`
- Exports the cleaned DataFrame to `netflix_titles_cleaned.csv`
- Includes visualizations: Movies vs TV Shows, titles added per year, top 10 countries by title
  count, movie runtime distribution, and top 10 content ratings

## Technologies Used

- Python
- Pandas
- Jupyter Notebook
- Matplotlib / Seaborn (visualizations)

## Files

| File | Description |
|---|---|
| `netflix_data_cleaning.ipynb` | Main notebook — full cleaning process, reasoning, and charts |
| `netflix_titles.csv` | Raw input dataset from Kaggle |
| `netflix_titles_cleaned.csv` | Final cleaned output |
| `viz_type_counts.png` | Movies vs TV Shows bar chart |
| `viz_titles_per_year.png` | Titles added to Netflix per year |
| `viz_top_countries.png` | Top 10 countries by number of titles |
| `viz_movie_runtime_dist.png` | Distribution of movie runtimes |
| `viz_ratings.png` | Top 10 content ratings |

## How to Run

1. Place `netflix_data_cleaning.ipynb` and `netflix_titles.csv` in the same folder.
2. Install dependencies: `pip install pandas numpy matplotlib seaborn`
3. Open the notebook in Jupyter and run all cells.

## What You'll Learn

Practice making real decisions about messy data instead of just running `.dropna()` and moving on —
and get comfortable reading a dataset thoroughly before transforming it, a habit that matters a lot
in real-world projects.

## Reference

Project brief: [https://roadmap.sh/projects/cleaning-netflix-dataset](https://roadmap.sh/projects/cleaning-netflix-dataset)
