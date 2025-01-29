# Open Source Mash up of COVID-19 Positivity Rate Analysis in NYC

## Project Overview
This project analyzes COVID-19 data from NYC's five boroughs (Brooklyn, Bronx, Queens, Manhattan, & Staten Island) to determine which borough had the highest positivity rate over different time periods (4 weeks, 6 months, and 1 year). The study is based on two open-source CSV datasets.

## Data Sources
- **COVID-19 Daily Counts of Cases, Hospitalizations, and Deaths** (`COVID-19_Daily_Counts_of_Cases__Hospitalizations__and_Deaths.csv`)
- **Percent of NYC Residents Tested Who Tested Positive** (`DOHMH_Covid-19_Milestone_Data__Percent_of_NYC_residents_tested_who_tested_positive.csv`)

**Data Range:**
- Start Date: February 29, 2020
- End Date: January 2024

## Hypothesis
Before analyzing the data, it was hypothesized that **Manhattan** would have the highest positivity rate, as it was where the first case in NYC was reported.

## Implementation
### Data Processing
- The project reads both CSV files using `pandas` and converts them into dictionaries.
- The datasets are merged into a single DataFrame.
- Specific columns related to testing, hospitalization, deaths, and positivity rates per borough are extracted.
- Data is analyzed over 4 weeks, 6 months, and 1 year to observe trends.

### Code Snippet:
```python
import pandas as pd

# Load datasets
covid_data = pd.read_csv('COVID-19_Daily_Counts_of_Cases__Hospitalizations__and_Deaths.csv')
vaccination_data = pd.read_csv('DOHMH_Covid-19_Milestone_Data__Percent_of_NYC_residents_tested_who_tested_positive.csv')

# Convert to dictionaries
df = pd.DataFrame.from_dict({**covid_data.to_dict(), **vaccination_data.to_dict()})

# Extract key columns
deaths_col = df['DEATH_COUNT']
queenscase_col = df['QN_CASE_COUNT']

# Compute positivity rates for different periods
print("Death Count (1 Year):", sum(deaths_col[:365]))
print("Tested Positive - Queens (1 Year):", sum(queenscase_col[:365]))
```

## Findings
### Summary of Results
| Time Period | Borough with Highest Positivity |
|------------|--------------------------------|
| 4 Weeks    | Queens                         |
| 6 Months   | Queens                         |
| 1 Year     | Queens                         |

The hypothesis was incorrect, as **Queens** consistently had the highest positivity rate in NYC across all time frames, followed by Brooklyn.

## Conclusion
The experiment demonstrated how COVID-19 impacted different boroughs over time, with Queens having the highest positivity rate. This analysis can help in understanding pandemic trends and resource allocation.

## Future Improvements
- Incorporate **vaccination data** to observe its impact on positivity rates.
- Use **visualizations** (e.g., graphs, heatmaps) for better data representation.
- Analyze data at a **zip-code level** for a more granular view.

---
📌 **Author:** Weipeng Lin  
📌 **GitHub:** [okweipeng](https://github.com/okweipeng)
