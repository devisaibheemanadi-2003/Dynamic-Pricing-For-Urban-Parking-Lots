## 📄 Project Overview

**Title:** Dynamic Pricing for Urban Parking Lots

**Goal:** To build a smart pricing engine that dynamically updates parking prices in urban areas based on real-time demand signals such as occupancy, queue length, traffic level, vehicle type, time, and location.

## 📋 Problem Statement

Urban parking faces imbalances in demand and pricing. Fixed pricing models result in either overutilized or underutilized lots. This project addresses this by building a real-time pricing model that adapts dynamically to changing demand factors.


## 🎯 Objectives

Your goal is to build a dynamic pricing model for each parking space such that:
• The price is realistically updated in real-time based on:
– Historical occupancy patterns
– Queue length
– Nearby traffic
– Special events
– Vehicle type
– Competitor parking prices
• It starts from a base price of $10
• The price variation is smooth and explainable, not erratic

## 📊 [Dataset](https://github.com/devisaibheemanadi-2003/Dynamic-Pricing-For-Urban-Parking-Lots/blob/main/dataset.csv)

The dataset contains 18,368 records from 14 urban parking spaces over 73 days with:
- **Location**: Latitude, Longitude
- **Capacity**: Maximum vehicles
- **Occupancy**: Current vehicles parked
- **Queue Length**: Vehicles waiting
- **Vehicle Type**: Car, bike, truck, cycle
- **Traffic Conditions**: Low, average, high
- **Special Days**: Holidays/events indicator
- **Timestamps**: Date and time information
  
## ⚙️ Tech Stack Used
**Category**	               **Tools / Libraries**

**Programming**                       Python

**Data Handling**                	pandas, numpy

**Real-time Stream Processing**	        pathway

**DateTime**	                      datetime, time

**Visualization**	                  bokeh, matplotlib

**Modeling Logic**	              Custom dynamic pricing function using rule-based logic

**Output**	                      Bokeh interactive visualizations, PNG plots

## 🧠 Architecture Diagram (Mermaid)
graph TD
    
    A[Raw Parking Data (.csv)] --> B[Data Cleaning & Timestamp Merge (pandas)]
    
    B --> C[Streaming Table (Pathway)]
    
    C --> D[Apply Pricing Logic (Model 1, 2, 3)]
    
    D --> E[Dynamic Price Calculation]
    
    E --> F[Pathway Output Table]
    
    F --> G[Real-time Bokeh Line Plot]
    
    F --> H[Bar Plot for Nearby Lot Comparison]
    
    G --> I[Dashboard / Reporting]
    
    H --> I


## 🧠 Models Implemented
### Model 1: Baseline Linear Pricing
```python
Price = Previous_Price + α × (Occupancy / Capacity)
```
- Simple linear relationship with occupancy rate
- Acts as baseline for comparison
- Parameters: α (learning rate), min/max price bounds

### Model 2: Demand-Based Pricing Function
```python
Demand = α×Occupancy_Rate + β×Queue + γ×Traffic + δ×Special_Day + ε×Vehicle_Weight
Price = Base_Price × (1 + λ×Normalized_Demand) × Vehicle_Weight
```
- Multi-factor demand calculation
- Vehicle-specific pricing weights
- Traffic condition multipliers
- Special day premiums
- Bounded using tanh normalization


## 🛠️ Implementation Features

### Real-time Processing
- **Pathway Integration**: Streaming data pipeline
- **Live Updates**: Continuous price recalculation
- **Scalable Architecture**: Handle multiple parking lots

### Interactive Visualizations
- **Bokeh Dashboard**: Real-time price monitoring
- **Comparative Analysis**: Model performance comparison
- **Demand Tracking**: Visual demand score evolution
- **Geographic Mapping**: Competitive landscape view

### Business Intelligence
- **Routing Suggestions**: Direct customers to available lots
- **Competitive Analysis**: Monitor nearby pricing
- **Demand Prediction**: Identify peak usage patterns
- **Revenue Optimization**: Maximize lot utilization
