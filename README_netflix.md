# Netflix Catalog Analysis

**Question:** How has Netflix's catalog changed over the years, and what does it contain?

**Tools:** Power BI (Power Query) for cleaning, Python (pandas) in Google Colab for analysis

---

## 1. Data

- **Source:** "Netflix Movies and TV Shows" dataset (Kaggle).
- **Size:** 8,807 titles (movies and TV shows).
- **Main columns:** `type`, `title`, `director`, `cast`, `country`, `release_year`, `rating`, `duration`, `listed_in` (genres), and the date the title was added to Netflix.

## 2. Data cleaning

**In Power BI (Power Query):**
- Promoted the first row to headers and set the data types.
- Removed duplicate rows.
- Replaced blank values in text columns (`director`, `cast`, `country`) with "Unknown".
- Trimmed extra spaces in the text columns.
- Created a `Year` column with the year each title was added to Netflix, extracted from the `date_added` text.
- Split `duration` into a number and a unit (minutes for movies, seasons for TV shows).
- Removed columns that were not needed for the questions (for example `description`) and renamed columns.

**In Python:**
- Checked the size, the types and the number of blanks per column.
- Removed the one row with a blank `type`.
- Filled the remaining blanks in text columns (`title`, `listed_in`, `rating`, `unit`) with "Unknown".
- Converted `release_year` to a number (values that were not numbers became blank).
- Left blank numeric values (year added, release year, duration) as they were, since a missing year or length cannot be invented.

## 3. Questions explored

1. How many movies and TV shows are there?
2. In which years were the most titles added to Netflix?
3. What are the most common ratings?
4. How long are movies (summary statistics of the duration)?
5. How many seasons do TV shows have?
6. Which genres are the most common (overall, for movies, and for TV shows)?
7. Which countries produce the most titles?
8. Which directors and actors appear most often?
9. What are the oldest and newest release years?
10. How many years pass between a title's release and its addition to Netflix?

Columns that hold several values in one cell (`listed_in`, `country`, `director`, `cast`) were split into separate rows before counting.

## 4. Main findings

- **Movies vs. TV shows:** the catalog has 6,131 movies (about 70%) and 2,676 TV shows (about 30%), so movies outnumber shows by more than two to one.
- **Titles added over time:** 2,016 titles were added in 2019. [Add how this compares with the other years, for example whether it is the highest year and how it changed after.]
- **Countries:** the United States produces the most titles (3,688), followed by India (1,046), the United Kingdom (804) and Canada (445). About 832 titles have no country listed. [Update these numbers if they changed after cleaning the country values.]
- **Genres:** [Add the top genres overall, and say whether movies and TV shows differ.]
- **Ratings:** [Add the most common ratings and what they say about the audience.]
- **Movie length and TV seasons:** [Add the typical movie length and the most common number of seasons.]
- **Directors and actors:** [Add the most frequent names, excluding "Unknown".]
- **Time between release and addition:** [Add the typical gap in years, and say whether titles are added soon after release or years later.]

## 5. Limitations

- Some titles have missing values: for example about 13 have no year added, 6 have no duration and 2 have no release year. These were left out of the calculations that need them.
- Missing text values were labeled "Unknown", so "Unknown" can appear as a category in counts of countries, directors and cast. Those rankings should be read without it.
- A title with several countries, genres or cast members is counted once for each, so the totals are larger than the number of titles.
- The data is a snapshot of the catalog, not a full history. It shows when titles were added, not when they were removed.

## 6. Project structure

```
├── netflix_analysis.ipynb   # cleaning checks and analysis
├── netflix data.csv         # data after Power BI cleaning
└── README.md
```

## 7. How to run

1. Open the notebook in Google Colab (or Jupyter).
2. Upload `netflix data.csv` to the same environment.
3. Run all cells in order.

## Author

[RAHIK GUELDI] | [www.linkedin.com/in/rahik-gueldi | [https://github.com/rahikgueldi098-del]
