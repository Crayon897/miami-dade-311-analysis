# Which Miami-Dade ZIP Codes Wait Longest for Pothole Repairs?

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Crayon897/miami-dade-311-analysis/blob/main/311_analysis.ipynb)

An analysis of 2023 Miami-Dade County 311 service requests in Python, measuring how long the county takes to close pothole reports in each ZIP code.

## Key findings
- Miami-Dade's goal is to fix potholes within **3 days**, but only **43%** of the 5,030 pothole requests analyzed were closed within it. The countywide median was **4.3 days**.
- In ZIP **33167**, the median was **8.0 days**, nearly double the countywide median. ZIPs **33183** and **33142**, with over 120 requests each, took more than 6 days.
- **Busier ZIP codes weren't slower.** The correlation between request volume and median days was -0.19, a weak relationship.

## Charts
![Most potholes miss the county's 3-day goal](chart%201.png)
![The slowest and fastest ZIP codes](chart%202.png)
![Busier ZIP codes don't wait longer](chart%203.png)

## Data
- Source: [Miami-Dade County Open Data – 311 Service Requests 2023](https://opendata.miamidade.gov/datasets/311-service-requests-miami-dade-county-2023)
- 343,851 requests in the raw file, 307,275 after cleaning, and 5,030 pothole requests analyzed
- The raw CSV isn't in this repo because of its size. Download it from the link above.

## Method
1. Calculated response time as the closed date minus the created date, in days.
2. Removed 11,081 requests with a missing date or ZIP code, 4,109 that were closed before they were opened, and 21,386 that weren't truly closed (canceled, duplicate, locked, or another non-closed status).
3. Focused on potholes because they're common, handled by the county, and not scheduled by appointment. Of the three request types compared, potholes covered the most ZIP codes (70).
4. Compared the median response time and the share closed within the 3-day goal for the 36 ZIP codes with at least 30 pothole requests. Medians were used because a few very slow tickets (up to 514 days in the full dataset) pull averages up.
5. Checked the calculated response times against the county's own `actual_completed_days` column. They match after rounding.

## Limitations
- 3,109 closed pothole tickets (38%) were closed before they were opened and were removed. They may be repairs that crews logged after fixing them.
- Smaller ZIP codes show more extreme medians, so their exact rankings are less certain.
- ZIP 33034 (median 0.6 days) is far faster than every other ZIP and needs further investigation.
- The dataset mostly covers county-handled requests, not cities like the City of Miami or Coral Gables.
- "Closed" may not always mean the pothole was physically repaired.

## How to run
1. Open the notebook with the **Open in Colab** button above.
2. Download the data and upload it to your Google Drive as `311_2023.csv`.
3. Click **Runtime → Run all**.

## Tools
Python, pandas, matplotlib, Google Colab

## Author
Rayyan Awan · Data Science & AI, Florida International University
