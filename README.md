
Data Scientist Technical Assessment

Welcome to the Papcorns Data Scientist Technical Assessment. This repository contains analysis of user behavior and monetization metrics, using a SQLite dataset and Python.

📂 Repository Structure

├── papcorns.sqlite         # SQLite database with users and events
├── analysis_notebook.ipynb # Jupyter notebook with SQL & Python analysis
├── Task1_revenue_by_country.png
├── Task3_acquisition_channel_distribution.png
├── Task4_conversion_rate_by_source.png
├── Task5_median_duration_by_country.png
├── Task6_ltv_by_country.png
└── README.md               # This file

🗒 Dataset Description

The SQLite database papcorns.sqlite contains two tables:

users

id (integer): Unique user identifier

created_at (ISO timestamp): Account creation date

attribution_source (text): Acquisition channel (tiktok, instagram, organic)

country (text): User country (US, TR, NL)

name (text): User name

user_events

id (integer): Unique event identifier

created_at (ISO timestamp): Event timestamp

user_id (integer): Foreign key to users.id

event_name (text): One of app_install, trial_started, trial_cancelled, subscription_started, subscription_renewed, subscription_cancelled

amount_usd (numeric): Transaction amount (only for subscription events)

⚙️ Environment Setup

Clone the repository:

git clone <repo-url>
cd papcorns-data-assessment

Create and activate a Python environment:

python3 -m venv venv
source venv/bin/activate

Install requirements:

pip install -r requirements.txt

🚀 Getting Started

Open the Jupyter notebook analysis_notebook.ipynb and run the cells in order:

Imports & DB Connection: Connect to papcorns.sqlite using sqlite3.

Helper Functions:

run_query(query): Execute SQL and return a pandas DataFrame.

check_unique_years(df, date_column): Summarize the date range and unique years.

🧪 Core Analysis Tasks

Total Subscription Revenue by Country

SQL: SUM(amount_usd) for subscription_started and subscription_renewed grouped by country.

Visualization: Bar chart of revenue per country.

Total Trials from Instagram Users

SQL: Count of trial_started events where attribution_source = 'instagram'.

Acquisition Channel Classification

Create a new column acquisition_channel: 'Paid' for instagram/tiktok, 'Organic' otherwise.

Visualization: Pie chart of user counts by channel.

Trial-to-Subscription Conversion Rates

Overall: Ratio of users with both trial_started and subscription_started.

By Source: Conversion rates broken down by attribution_source.

Visualization: Bar chart of conversion rates.

Median Subscription Duration by Country

Compute time (in months) between subscription_started and subscription_cancelled (or current date if active).

Median duration per country.

Visualization: Bar chart of median durations.

Average Lifetime Value (LTV) by Country

For each user, sum all subscription_started and subscription_renewed amounts to get total revenue.

Compute average by country.

Visualization: Bar chart of average LTV.

📈 Key Findings

Revenue Leader: US users generated the highest total subscription revenue.

Instagram Trials: 210 trials were started by Instagram-acquired users.

Acquisition Mix: 65.7% of users are paid channels vs. 34.3% organic.

Conversion Rates: Overall ~70.5% of trials convert, with organic users converting slightly better (71.6%).

Subscription Duration: Turkish users stay subscribed longest (median ~2.83 months).

LTV: US users have the highest average LTV (~$25.07).

📊 Visualizations

Refer to the generated PNG files for bar charts and pie charts:

Task1_revenue_by_country.png

Task3_acquisition_channel_distribution.png

Task4_conversion_rate_by_source.png

Task5_median_duration_by_country.png

Task6_ltv_by_country.png

🤝 Collaboration

Feel free to open issues or pull requests for improvements. For questions, contact Irmak Erkol at irmakerkol00@gmail.com.
5. Send us the link to your repository back to dev+interview@papcorns.com

Good luck!
