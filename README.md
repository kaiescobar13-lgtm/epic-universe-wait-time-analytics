# Epic Universe Wait Time Analytics & Itinerary Optimization

**Overview**
This repository houses a comprehensive data science pipeline designed to analyze, visualize, and optimize theme park attraction wait times using operational logs collected from Epic Universe Opening Week (May 22–29, 2025). The framework dynamically processes multi-sheet Excel workbooks, cleans operational anomalies, and generates high-resolution visual dashboards for strategic park navigation.

**Repository Artifacts & Visualizations**

* **`daily_congestion_trend.png`**: Displays daily park-wide congestion shifts and peak volume patterns across the analyzed week.
* **`hourly_wait_heatmap.jpg`**: Comprehensive heatmap illustrating average hourly wait times by attraction across standard operating hours (9 AM – 10 PM), with closed-ride anomalies filtered out.


* **`hourly_wait_heatmap_may27_29.jpg`**: Focused hourly heatmap highlighting late-week peak congestion windows from May 27 to May 29.
* **`ride_reliability_ranked.png`**: Statistical ranking of attractions evaluating operational consistency, variance, and downtime frequency.
* **`optimized_breaks_itinerary.png`**: Data-driven touring plan mapping out optimal attraction sequencing and strategic rest intervals to minimize queue exposure.

**Data Pipeline & Technical Architecture**

* **Dynamic Sheet Ingestion**: Automatically loops through daily numerical sheet tabs in `Epic Universe Wait Times 5_22-5_29.xlsx`, anchoring shifted header rows dynamically via string matching (`"9 A.M."`).


* **Data Sanitization**: Drops generalized weather rows and replaces `0`-minute wait records (representing ride closures or logging gaps) with `NaN` to protect hourly mean calculations from downward skew.


* **Long-Format Transformation**: Melts wide-format daily time series into a normalized pandas dataframe (`Ride Names`, `Date`, `Hour`, `WaitTime`) for advanced aggregation and pivoting.


* **High-Resolution Styling**: Utilizes `seaborn` and `matplotlib` with enforced `DejaVu Sans` typography and a high-density export configuration (`figure.dpi = 300`) for publication-grade chart rendering.



**Setup & Usage**

1. Ensure Python 3.8+ is installed alongside required packages: `pip install pandas matplotlib seaborn openpyxl`.
2. Place the source dataset (`Epic Universe Wait Times 5_22-5_29.xlsx`) into the working directory.


3. Run the processing script to execute data munging, handle aggregations, and export updated visual artifacts.
