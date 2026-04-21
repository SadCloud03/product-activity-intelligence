## User Activity Analysis — product_activity.csv
### About
This repository contains a structured data analysis of a user activity dataset (`product_activity.csv`). The analysis covers the full pipeline from raw data ingestion, through normalization and quarantine logic, to engagement metrics and interpretation. Built with Python and pandas, this project focuses on clean data engineering practices and meaningful behavioral insights extracted from product usage data.
## This is practice of data wrangling, canonical normalization, and metric-driven analysis
### Repository structure
* /notebooks
    * `analytics.ipynb` — main analysis notebook
* /data
    * `product_activity.csv` — raw input dataset
    * `clean_product_activity.csv` — sanitized output
    * `quarantine_product_activity.csv` — rows flagged for issues
    * `metrics_summary.csv` — high-level summary metrics
* expand if needed....
### Features & Analysis Milestones
* **Data Ingestion & Inspection**: Loading raw CSV data with pandas, running `.describe()` and `.info()` to detect type mismatches and null values early.
* **Canonical Normalization**: Resolving dirty categorical columns (`plan_type`, `post_category`, `device_type`) through:
    * **String Sanitization**: Strip and lowercase to catch accidental spaces and casing inconsistencies.
    * **Value Validation**: Cross-referencing against canonical value lists to detect out-of-scope entries.
    * **Date Parsing**: Coercing `created_at` and `post_created_at` to datetime and recalculating `time_since_signup` from source.
* **Quarantine System**: Rows are not deleted — they are tagged with a `quarantine_reason` and exported separately. Reasons include unparseable dates, date mismatches (post before signup), duplicated rows, and invalid categorical values.
* **Distribution Analysis**: Breakdown of users and posts by plan type, country, post category, and device type.
* **Engagement Metrics**: Statistical description (`count`, `mean`, `std`, `min`, percentiles, `max`) of votes received per plan, country, category, and device.
* **Behavioral Averages**: Mean votes per plan, mean posts per user, and the contrast between event-level and user-level vote aggregation.
### Requirements
* **Python** (v3.9 or higher)
* **pandas** (for data manipulation)
* **Jupyter Notebook** or **JupyterLab** (to run the `.ipynb` file)
### Setup & Execution
1. **Clone the repo**
```bash
git clone <your-repo-url>
cd <your-repo-folder>
```
2. **Install dependencies**
```bash
pip install pandas jupyter
```
3. **Run the notebook**
```bash
jupyter notebook analytics.ipynb
```
4. **Check outputs**
```bash
# after running all cells, the following files will be generated:
clean_product_activity.csv
quarantine_product_activity.csv
metrics_summary.csv
```