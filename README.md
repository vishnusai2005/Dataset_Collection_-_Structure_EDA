# IPL Ball-by-Ball Data Analysis (2008-2023) cricket_game

## 📌 Project Overview

This project focuses on the **Exploratory Data Analysis (EDA)** and **Data Preprocessing** of the Indian Premier League (IPL) ball-by-ball dataset. The notebook processes raw match data from **2008 to 2023** to uncover insights regarding batting, bowling, match outcomes, and venue impacts.

The primary goal of this specific notebook (`Dataset_Collection_&_Structure.ipynb`) is to clean, standardize, and structure the raw data for downstream analysis.

## 📂 Dataset Information

The dataset contains **239,693 rows** and **34 columns**, representing individual deliveries bowled in IPL history.

**Key Features:**

* **Match Details:** `Match ID`, `Date`, `Venue`, `Winner`, `Toss`.
* **Innings Info:** `Bat First`, `Bat Second`, `Innings`, `Target Score`.
* **Delivery Details:** `Over`, `Ball`, `Batter`, `Bowler`, `Non Striker`.
* **Scoring & Dismissals:** `Batter Runs`, `Extra Runs`, `Wicket`, `Method`, `Player Out`.

## 🛠️ Data Cleaning & Preprocessing Pipeline

The raw data underwent a rigorous cleaning process to ensure accuracy and consistency. The following steps were executed:

### 1. Categorical Standardization

* **Venue Mapping:** Consolidated duplicate stadium names caused by spelling variations or renaming (e.g., *'Feroz Shah Kotla'*  *'Arun Jaitley Stadium'*, *'Sardar Patel Stadium'*  *'Narendra Modi Stadium'*).
* **Team Name Correction:** Standardized historical team names to their modern counterparts:
* *Delhi Daredevils*  **Delhi Capitals**.
* *Kings XI Punjab*  **Punjab Kings**.


* **Player Name Formatting:** Applied title casing and whitespace stripping to `Batter`, `Bowler`, and `Non Striker` names to remove formatting duplicates.

### 2. Handling Missing Values

* **Dismissal Data:** Columns like `Method` and `Player Out` contained null values for deliveries where no wicket fell. These were imputed with **"Not Out"** and **"None"** respectively.
* **Chase Data:** `Runs to Get` (relevant only for the 2nd innings) was filled with `0` for the 1st innings.
* **Dismissal Stats:** `Player Out Runs` and `Player Out Balls Faced` were filled with `0` for non-wicket deliveries.

### 3. Data Type Optimization

Converted columns to their appropriate data types for efficient analysis:

* **Date:** Converted to `datetime64` for time-series analysis.
* **Match ID:** Converted to `string` (categorical identifier).
* **Ball Rebowled:** Converted to `boolean`.
* **Numeric Conversions:** `Runs to Get`, `Player Out Runs`, and `Player Out Balls Faced` converted from float to `int64`.

## 💻 Tech Stack & Dependencies

The project uses Python 3.x and the following data analysis libraries:

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import warnings

```

## 🚀 Usage

1. Clone the repository.
2. Install dependencies:
```bash
pip install pandas numpy matplotlib seaborn

```


3. Load the dataset using the provided path in the notebook:
```python
df = pd.read_csv('/path/to/ball_by_ball_ipl.csv', index_col=0)

```


4. Run the notebook cells sequentially to reproduce the cleaning pipeline.

