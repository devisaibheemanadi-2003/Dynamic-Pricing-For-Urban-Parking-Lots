🔍Project Architecture and Workflow Explanation

1. Data Ingestion:
Source: A CSV file that contains timestamped parking lot information including occupancy rate, vehicle type, queue length, etc.

The LastUpdatedDate and LastUpdatedTime are merged into a single Timestamp column using pandas.

2. Stream Processing (Pathway):
Data is streamed using the Pathway framework.

pw.io.python.read is used to load the cleaned dataframe into a streaming table.

pw.udf applies transformation logic to dynamically compute the price for each parking lot using Model 1, Model 2, and Model 3.

3. Pricing Models:
Model 1: Basic price calculation based on occupancy and queue length.

Model 2: Incorporates additional demand features like time of day and vehicle type.

Model 3 (Advanced):

Adds GPS coordinates (latitude, longitude) as inputs.

Incorporates competitor pricing logic (uses nearby lot prices for competitiveness).

Final output is a refined dynamic price.

4. Output Handling:
The computed price is sent to a Pathway output table.

This is used to generate:

A Bokeh line plot that shows price trends over time.

A bar plot comparing the current price of a selected lot vs nearby lots.

5. Additional Visualizations:
matplotlib is used to generate PNG snapshots of how each demand feature (e.g., occupancy rate, queue length, traffic) affects pricing across different lots.

📎 Additional Documentation
✅ Assumptions
Locations are valid within an urban boundary.

Distance threshold for competitive pricing logic is fixed (e.g., 500m radius).

The pricing model is rule-based, not ML-based (for this version).

💡 Future Scope
Replace rule-based logic with ML models (e.g., XGBoost, Random Forests).

Incorporate holiday and event-based logic.

API integration for real-time lot monitoring.

Mobile-friendly dashboard using Flask + React.

