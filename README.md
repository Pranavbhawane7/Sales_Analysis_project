# Sales Analysis Project

## 📌 Overview

This project explores the Rossmann Store Sales dataset using Python and Jupyter Notebook. It examines daily sales, customer counts, store opening status, promotions, holidays, and store characteristics. The notebook focuses on data inspection, exploratory analysis, and preparation of the data for further study.

## 📂 Project Structure

```text
Sales_Analysis_project/
├── Sales_Analysis_project_visualization/
├── train.csv
├── store.csv
├── Sales_Analysis_project.ipynb
└── README.md
```

## 📊 Dataset

This project uses the [Rossmann Store Sales dataset](https://www.kaggle.com/c/rossmann-store-sales/data), provided as two CSV files.

### `train.csv`

Contains **1,017,209 daily records** for Rossmann stores, with these fields:

- `Store`: Store identifier.
- `DayOfWeek`: Day of the week, encoded from 1 to 7.
- `Date`: Date of the observation.
- `Sales`: Daily sales amount and competition target variable.
- `Customers`: Number of customers recorded that day.
- `Open`: Whether the store was open (`1`) or closed (`0`).
- `Promo`: Whether a promotion was active (`1`/`0`).
- `StateHoliday`: Holiday category (`a` = public holiday, `b` = Easter, `c` = Christmas, `0` = no holiday).
- `SchoolHoliday`: Whether public schools were closed (`1`/`0`).

### `store.csv`

Contains store metadata for **1,115 stores**:

- `Store`: Store identifier used to associate metadata with daily sales.
- `StoreType`: Store type category.
- `Assortment`: Assortment category.
- `CompetitionDistance`: Distance to the nearest competitor.
- `CompetitionOpenSinceMonth`, `CompetitionOpenSinceYear`: Month and year the nearest competitor opened, when available.
- `Promo2`: Whether the store participates in the continuing promotion (`1`/`0`).
- `Promo2SinceWeek`, `Promo2SinceYear`: Start week and year of Promo2, when available.
- `PromoInterval`: Months in which Promo2 runs, when available.

## 🚀 Installation

### 1️⃣ Prepare the project files

Keep the notebook and both CSV files in the same directory. The notebook reads the files using the relative paths `train.csv` and `store.csv`.

### 2️⃣ Install dependencies

The notebook imports the following Python packages:

- `pandas`
- `numpy`
- `matplotlib`
- `seaborn`

Install the packages and Jupyter with pip:

```bash
python -m pip install pandas numpy matplotlib seaborn jupyter
```

### 3️⃣ Open the notebook

From the project directory, run:

```bash
jupyter notebook
```

You can also run `jupyter lab`, then open `Sales_Analysis_project.ipynb` and execute the cells from top to bottom.

## 🔍 Methodology

### 1. Data loading and inspection

- Load the daily sales and store metadata CSV files with pandas.
- Preview the records and inspect column types, row counts, and descriptive statistics.
- Check daily sales data for missing values and visualize numeric field distributions.

### 2. Open-store analysis

- Count open and closed store-day records. The notebook finds **844,392 open** records and **172,817 closed** records.
- Filter the daily data to records where `Open` is `1`.
- Remove the `Open` column from the filtered data because it has the same value in every remaining row.
- Summarize sales and customer counts for open-store days. The notebook reports mean daily sales of approximately **6,955** and mean customers of approximately **763**.

### 3. Store metadata and missing values

- Inspect missing values in the store metadata.
- The notebook identifies 3 missing `CompetitionDistance` entries, 354 missing competition opening month/year entries, and 544 missing Promo2 schedule entries.
- It attempts to fill selected missing competition opening and Promo2 schedule fields with zero. Review this assumption before using the resulting values in further analysis: missing can mean unknown or not applicable rather than a literal zero.

## 📈 Visualizations

The notebook includes a missing-value heatmap for the daily sales data and histograms of numeric fields. The project also includes a `Sales_Analysis_project_visualization/` directory containing image files associated with the analysis.

## 🛠️ Technologies Used

- Python
- Jupyter Notebook
- Pandas
- NumPy
- Matplotlib
- Seaborn

## 📌 Scope and Future Improvements

The current notebook documents exploratory data analysis and basic data preparation. It does not show a completed forecasting model or model evaluation. Possible next steps include:

- Join daily sales and store metadata using `Store` and analyze store-level factors alongside sales.
- Parse `Date` as a datetime and explore sales patterns over time, by weekday, holiday, promotion, and store type.
- Investigate missing-value treatment and data quality, including zero-sales records on open days.
- Build and evaluate a sales forecasting model using a time-aware validation strategy.
- Compare predictions with suitable regression metrics such as MAE and RMSE.
