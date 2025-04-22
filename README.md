# Data Scientist Technical Assessment

## Description

This repository contains the analysis and results for the Data Scientist Technical Assessment. We explore user behavior, trial conversions, subscription revenue, and lifetime value using a SQLite dataset and Python.

## Repository Structure

```
Data-Scientist-Technical-Assessment
/
├── papcorns.sqlite         # SQLite database with users and events tables
├── analysis_notebook.ipynb # Jupyter notebook with SQL & Python analysis workflow
├── requirements.txt        # Python dependencies
├── Task1_revenue_by_country.png
├── Task3_acquisition_channel_distribution.png
├── Task4_conversion_rate_by_source.png
├── Task5_median_duration_by_country.png
├── Task6_ltv_by_country.png
└── README.md               # Project overview and instructions
```

## Prerequisites

- Python 3.7 or higher
- Virtual environment tool (`venv` or `conda`)
- `sqlite3` installed (for database connectivity)

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/irmakerkol/Data-Scientist-Technical-Assessment
   ```
2. Create a virtual environment and activate it:
   ```bash
   python3 -m venv venv
   source venv/bin/activate    # on Windows: venv\Scripts\activate
   ```
3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## Data Schema

### `users` table

| Column             | Type    | Description                       |
|--------------------|---------|-----------------------------------|
| `id`               | INTEGER | Unique user identifier            |
| `created_at`       | TEXT    | Account creation timestamp (ISO)  |
| `attribution_source` | TEXT  | Acquisition source (`tiktok`, `instagram`, `organic`) |
| `country`          | TEXT    | User country (`US`, `TR`, `NL`)   |
| `name`             | TEXT    | User’s name                       |

### `user_events` table

| Column        | Type    | Description                                                      |
|---------------|---------|------------------------------------------------------------------|
| `id`          | INTEGER | Unique event identifier                                          |
| `created_at`  | TEXT    | Event timestamp (ISO)                                            |
| `user_id`     | INTEGER | Foreign key to `users.id`                                        |
| `event_name`  | TEXT    | One of: `app_install`, `trial_started`, `trial_cancelled`, `subscription_started`, `subscription_renewed`, `subscription_cancelled` |
| `amount_usd`  | NUMERIC | Transaction amount (for subscription events only)                |

## Analysis Tasks

1. **Total Subscription Revenue by Country**  
   - Compute total revenue from `subscription_started` and `subscription_renewed` events, grouped by country.  
   - Visualize with a bar chart.  

2. **Total Trials from Instagram Users**  
   - Count `trial_started` events for users acquired via Instagram.  

3. **Acquisition Channel Classification**  
   - Add `acquisition_channel`: `Paid` for Instagram/TikTok, `Organic` otherwise.  
   - Visualize distribution with a pie chart.  

4. **Trial-to-Subscription Conversion Rates**  
   - Calculate overall conversion (trial → subscription).  
   - Break down by attribution source.  
   - Visualize with a bar chart.  

5. **Median Subscription Duration by Country**  
   - Measure subscription length (months) between start and cancel (or present).  
   - Report median duration per country.  

6. **Average Lifetime Value (LTV) by Country**  
   - Sum subscription revenue per user.  
   - Compute country-level average LTV.  

## Key Findings

- **Revenue Leader**: US users generated the highest total subscription revenue.  
- **Instagram Trials**: 210 trials initiated by Instagram-acquired users.  
- **Acquisition Mix**: 65.7% Paid vs. 34.3% Organic users.  
- **Conversion Rates**: Overall 70.5% trial-to-subscription conversion; organic users lead at 71.6%.  
- **Subscription Duration**: Turkish users have the longest median duration (~2.83 months).  
- **Lifetime Value**: US users highest average LTV (~$25.07).  

## Visualizations

See the `*.png` files for generated charts corresponding to each analysis task.

## Usage

1. Open and run `analysis_notebook.ipynb` in Jupyter Lab or Notebook.  
2. Ensure `papcorns.sqlite` is in the same directory.  
3. Follow sections and execute cells sequentially.  


