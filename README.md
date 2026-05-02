# Pandas Practice Labs

A collection of 7 hands-on Jupyter notebooks for learning **pandas** — the go-to Python library for working with tabular data. Each lab focuses on a specific skill, from basic filtering to data visualization, using real-world datasets.

---

## Contents

| # | Notebook | Focus | Dataset |
|---|---|---|---|
| 01 | `01_lab.ipynb` | Filtering, sorting, grouping | IMDB movies |
| 02 | `02_lab.ipynb` | GroupBy, aggregation, custom functions | NBA players |
| 03 | `03_lab.ipynb` | String operations, custom columns | YouTube videos |
| 04 | `04_lab.ipynb` | Merging DataFrames | Synthetic data |
| 05 | `05_lab.ipynb` | Data cleaning, normalization | Auto data |
| 06 | `06_lab.ipynb` | Visualization with matplotlib | Canada immigration |
| 07 | `07_lab.ipynb` | Regex, string extraction, merging | Movies |

---

## Requirements

```
pandas >= 2.0.0
numpy >= 1.24.0
matplotlib >= 3.6.0
openpyxl >= 3.1.0   # for reading Excel files (Lab 06)
jinja2 >= 3.1.0     # for DataFrame styling (Lab 06)
```

Install with:

```bash
pip install pandas numpy matplotlib openpyxl jinja2
```

---

## Quick Start

```bash
# Move into the project folder
cd pandas-labs

# (Optional) Create a virtual environment
python -m venv venv
source venv/bin/activate   # On Windows: venv\Scripts\activate

# Install dependencies
pip install pandas numpy matplotlib openpyxl jinja2

# Launch Jupyter
jupyter notebook
```

Open any notebook and run cells in order.

---

## Lab Summaries

### 01 — Filter, Sort, Group (IMDB)

Practice the most common pandas operations on the IMDB movie dataset.

**What you'll learn:**
- Reading CSV files with `pd.read_csv`
- Filtering rows with `query()` and boolean indexing
- Selecting columns with `loc` and `[[...]]`
- Sorting data with `sort_values`
- Combining multiple conditions with `&` and `|`
- Searching strings with `str.contains`
- Grouping and aggregating with `groupby` + `agg`
- Counting unique values with `nunique`
- **Method chaining** — writing readable multi-step pipelines

---

### 02 — GroupBy and Apply (NBA)

Dive deeper into grouping and apply custom logic to NBA player data.

**What you'll learn:**
- Aggregating numeric columns with `mean`, `sum`, etc.
- Using `numeric_only=True` to skip non-numeric columns
- Formatting values with `lambda` and f-strings
- Writing custom functions and applying them with `apply`
- Filtering rows with custom predicates

---

### 03 — String Operations (YouTube)

Work with text data and create new columns derived from existing ones.

**What you'll learn:**
- Inspecting data with `shape`, `info()`, and `describe()`
- Dropping columns with `drop(columns=...)`
- Selecting columns by position with `df.columns[-2:]`
- Splitting strings and counting parts
- Adding derived columns with `apply`
- Multi-column queries with chained methods

---

### 04 — Merging DataFrames

The pandas equivalent of SQL JOINs — combine two tables on a shared key.

**What you'll learn:**
- Building DataFrames from dictionaries
- Using `pd.merge` with `on`, `left_on`, `right_on`
- Merge types: **inner**, **left**, **right**, **outer**, **cross**
- Understanding which rows survive each merge type

---

### 05 — Data Cleaning and Normalization (Auto)

Real-world data is messy. Learn how to clean it up before analysis.

**What you'll learn:**
- Detecting missing values with `isnull().sum()`
- Replacing placeholder characters (like `?`) with `NaN`
- Filling missing values with mean, median, and mode
- Type conversion with `pd.to_numeric`
- **Data standardization** — converting between units (e.g., MPG to L/100km)
- **Data normalization** — scaling values to a 0–1 range
- Difference between `replace`, `fillna`, and `inplace=True`

---

### 06 — Visualization (Canada Immigration)

Turn numbers into insights using pandas' built-in plotting (powered by matplotlib).

**What you'll learn:**
- Reading Excel files with `pd.read_excel` (with `skiprows`/`skipfooter`)
- Renaming columns with `rename`
- Setting and resetting indexes with `set_index`
- Transposing DataFrames for plotting
- Creating different chart types:
  - **Area charts** for time series
  - **Histograms** for distributions
  - **Pie charts** for proportions
- Customizing titles, labels, fonts, colors
- Adding legends with `bbox_to_anchor`

---

### 07 — Regex and Merging (Movies)

Use regular expressions to extract information from messy text and combine datasets.

**What you'll learn:**
- Extracting patterns with `str.extract` and capture groups
- Replacing patterns with `str.replace(regex=True)`
- Trimming whitespace with `strip()`
- Splitting and **exploding** list-like columns
- Adding multiple columns at once with `assign(**dict)`
- Removing duplicates with `drop_duplicates`
- The basics of **one-hot encoding** for categorical features

---

## Common Workflow

Most labs follow the same pattern:

```
1. Import pandas (and sometimes numpy, matplotlib)
2. Read the dataset
3. Explore with .head(), .info(), .describe()
4. Filter, transform, or aggregate
5. Display the result
```

Once you're comfortable with this, you can apply it to any dataset.

---

## Pandas Quick Reference

### Selection

| Goal | Code |
|---|---|
| First 5 rows | `df.head()` |
| Last 5 rows | `df.tail()` |
| One column | `df['col']` |
| Multiple columns | `df[['a', 'b']]` |
| Row by index position | `df.iloc[0]` |
| Row by label | `df.loc['label']` |

### Filtering

| Goal | Code |
|---|---|
| Boolean indexing | `df[df['x'] > 5]` |
| String-based query | `df.query('x > 5')` |
| Multiple conditions | `df[(df['x'] > 5) & (df['y'] < 10)]` |
| String contains | `df[df['name'].str.contains('foo', na=False)]` |

### Aggregation

| Goal | Code |
|---|---|
| Group + sum | `df.groupby('col')['x'].sum()` |
| Group + multiple aggs | `df.groupby('col').agg({'x': 'mean', 'y': 'sum'})` |
| Unique count | `df['col'].nunique()` |
| Value frequencies | `df['col'].value_counts()` |

### Combining DataFrames

| Goal | Code |
|---|---|
| Merge (SQL JOIN) | `pd.merge(df1, df2, on='key', how='inner')` |
| Stack vertically | `pd.concat([df1, df2], axis=0)` |
| Stack horizontally | `pd.concat([df1, df2], axis=1)` |

### Cleaning

| Goal | Code |
|---|---|
| Find missing values | `df.isnull().sum()` |
| Drop missing rows | `df.dropna()` |
| Fill missing values | `df['x'].fillna(value)` |
| Replace values | `df.replace(old, new)` |
| Drop columns | `df.drop(columns=['x'])` |
| Rename columns | `df.rename(columns={'old': 'new'})` |

---

## Pandas vs SQL Cheatsheet

| SQL | Pandas |
|---|---|
| `SELECT col FROM df` | `df[['col']]` |
| `WHERE x > 5` | `df.query('x > 5')` |
| `ORDER BY x DESC` | `df.sort_values('x', ascending=False)` |
| `GROUP BY x` | `df.groupby('x')` |
| `JOIN ON x` | `pd.merge(df1, df2, on='x')` |
| `COUNT(DISTINCT x)` | `df['x'].nunique()` |
| `LIMIT 10` | `df.head(10)` |

---

## Project Structure

```
pandas-labs/
├── 01_lab.ipynb
├── 02_lab.ipynb
├── 03_lab.ipynb
├── 04_lab.ipynb
├── 05_lab.ipynb
├── 06_lab.ipynb
├── 07_lab.ipynb
├── data/
│   ├── imdb.csv
│   ├── nba.csv
│   ├── youtube.csv
│   ├── clean_auto.csv
│   ├── Canada.xlsx
│   └── movies.csv
└── README.md
```

> Place your dataset files in a `data/` folder and update the file paths in each notebook to use relative paths like `data/imdb.csv` for portability.

---


## License

This project is provided for educational purposes.

---

## Acknowledgments

Built using `pandas`, `numpy`, and `matplotlib`. Datasets sourced from public collections for learning purposes.
