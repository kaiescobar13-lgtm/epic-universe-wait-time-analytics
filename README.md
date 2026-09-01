# Epic Universe Wait Time Analytics & Itinerary Optimization

I built this pipeline to help me prepare for my trip to Universal's Epic Universe. I had been tracking the construction of the park over the course of the year, and was eagerly anticipating the opening. I wanted to make sure that I would be able to do every ride I was looking forward to, so I built this project.

I wanted to get an idea of how traffic moved throughout the park, so I logged operational wait times throughout opening week. I turned those raw logs into a Python pipeline to find when the park has lulls, dodge peak wait times, and engineer a touring plan for my own vacation. I also wanted to learn general information about the park, so I tracked downtimes and weather delays as well as overall minutes waited. 

**Artifacts & Visual Dashboards**

* **`daily_congestion_trend.png`**: Park-wide congestion shifts and peak volume patterns across opening week.
* **`hourly_wait_heatmap.jpg`**: Comprehensive heatmap of average hourly wait times across standard operating hours (9 AM – 10 PM), with ride closures filtered out.
* **`hourly_wait_heatmap_may27_29.jpg`**: Focused heatmap targeting late-week congestion spikes.
* **`ride_reliability_ranked.png`**: Statistical ranking evaluating operational consistency, variance, and downtime frequency.
* **`optimized_breaks_itinerary.png`**: The final data-driven touring plan mapping out attraction sequencing and strategic rest intervals.

**Under the Hood (Technical Architecture)**

* **Dynamic Ingestion**: Automatically loops through multi-sheet Excel workbooks (`Epic Universe Wait Times 5_22-5_29.xlsx`), anchoring shifted header rows via string matching (`"9 A.M."`).
* **Data Sanitization**: Drops weather rows and replaces `0`-minute wait records (closures or logging gaps) with `NaN` to prevent skewing hourly means.
* **Long-Format Transformation**: Melts wide-format daily time series into a normalized pandas dataframe (`Ride Names`, `Date`, `Hour`, `WaitTime`) for advanced pivoting.
* **Publication-Grade Styling**: Renders high-resolution charts (`figure.dpi = 300`) using `seaborn` and `matplotlib` with enforced typography.

**Setup & Usage**

1. Clone the repository and ensure Python 3.8+ is installed.
2. Install dependencies: `pip install pandas matplotlib seaborn openpyxl`
3. Drop your source dataset (`Epic Universe Wait Times 5_22-5_29.xlsx`) into the working directory.
4. Run the notebook/script to execute the pipeline and generate the visualizations.
