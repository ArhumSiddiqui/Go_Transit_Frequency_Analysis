# GO Transit Service Frequency & Stop Activity Dashboard

**Author:** Arham Siddiqui\
**Last Updated:** April 2025

---

## ✨ Executive Summary

This dashboard provides an in-depth analysis of GO Transit service frequency and stop-level activity using the GTFS (General Transit Feed Specification) **scheduled** data. Designed for Metrolinx planning and operations stakeholders, the goal is to uncover patterns in stop usage, service demand by time, and commonly travelled stop-to-stop pairs to support data-driven scheduling and resource allocation.

---

## 📈 Business Context

GO Transit serves a wide range of routes across the Greater Toronto and Hamilton Area (GTHA). Understanding how frequently each stop is served, when peak usage occurs, and which stop combinations experience the highest traffic is essential for:

- Planning high-frequency corridors
- Optimizing stop infrastructure investments
- Adjusting scheduling to match ridership demand
- Identifying underutilized services

This analysis is based on **scheduled services** rather than real-time or historical operational data. It provides a view into how GO Transit plans to deliver service, which can inform strategic planning and projected service delivery expectations.

---

## 🧱 Data Structure Overview

The dataset used follows the General Transit Feed Specification (GTFS) format. Key files include:

| File Name            | Description                                                          |
| -------------------- | -------------------------------------------------------------------- |
| `stop_times.txt`     | Lists the time and order of stops for each trip                      |
| `trips.txt`          | Links trips to routes and service IDs                                |
| `routes.txt`         | Describes the transit routes (e.g., Lakeshore West, Kitchener Line)  |
| `stops.txt`          | Contains location and name data for all GO Transit stops             |
| `calendar_dates.txt` | Contains the specific service dates (used instead of `calendar.txt`) |

All data was joined through common GTFS identifiers (e.g., `trip_id`, `route_id`, `stop_id`) to derive service frequency, hour-of-day trends, and stop pair flows.

---

## 🔗 Data Source

- **Feed:** GO Transit GTFS file https://www.metrolinx.com/en/about-us/open-data
- **Time Frame:** Latest available schedule data (2023–2024)
- **Format:** CSV files structured as per GTFS standard
- **Note:** This dataset represents planned service — not actual ridership or on-time performance.

---

## 🔄 Methodology

Data was preprocessed and analyzed using **Python (Pandas)** and visualized in **Power BI**. Key transformations included:

- Join and enrich GTFS files to derive hourly stop activity and stop pair frequency
- Extract day-of-week and route-level patterns using trip identifiers
- Create lookup tables for sorting (e.g., hour of day in 12-hour format)
- Aggregate and rank stop-level service frequency

---

## 🌐 Dashboard Features

### 1. **Stop Activity by Hour of Day**

- Shows the number of scheduled stop arrivals across all routes
- Includes slicers to filter by **day of week** and **route**
- Hour axis displayed in human-readable format (e.g., 7:00 AM)

### 2. **Top 10 Most Served Stops**

- Map visual with location markers sized by number of scheduled arrivals
- Provides a geospatial view of the most active GO Transit hubs

### 3. **Top 30 Most Frequently Travelled Stop Pairs**

- Horizontal bar chart of the most common sequential stop pairings based on GTFS `stop_times`
- Useful for identifying corridor-level demand

### 4. **Dynamic Slicers**

- Interactive filters allow segmentation by day (`Monday` to `Sunday`) and route (e.g., `Milton`, `Barrie`, etc.)

---

## 🔍 Key Insights

- **Peak Usage Hours:** 7:00 AM–9:00 AM and 4:00 PM–6:00 PM correspond with daily commute windows
- **High-Traffic Stops:** Union Station, Yorkdale Bus Terminal, and Square One show significantly higher scheduled service frequency
- **Common Corridors:** Richmond Hill → Union Station and Main St. W. pairings dominate route flow

---

## 💡 Recommendations

- Consider allocating more frequent service during peak commute hours
- Evaluate infrastructure capacity at top-performing stops to ensure they can accommodate projected demand
- Reassess underutilized routes or stop pairs for potential optimization

*Note: Recommendations are based on scheduled data and should be further validated with real-time and ridership datasets.*

---

## 💼 Tools Used

- **Data Wrangling:** Python (Pandas)
- **Visualization:** Power BI
- **Source Control:** GitHub

---

## 🔧 Future Improvements

- Incorporate actual ridership data to compare against the schedule
- Layer in weather or event-based variability
- Provide route-level delay and on-time performance tracking

---

> For internal use by the Metrolinx Data & Analytics team. For questions or access to the raw dataset or Python transformation scripts, please contact: [arham.siddiqui@metrolinx.ca](mailto\:arham.siddiqui@metrolinx.ca)

