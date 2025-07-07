# Dynamic Pricing for Urban Parking Lots

## 🚗 Project Overview

This project implements an intelligent dynamic pricing system for urban parking lots as part of the Summer Analytics 2025 Capstone Project. The system uses real-time data to optimize parking prices based on demand, competition, and various environmental factors.

## 📋 Problem Statement

Urban parking spaces are a limited and highly demanded resource. Prices that remain static
throughout the day can lead to inefficiencies — either overcrowding or underutilization.
To improve utilization, dynamic pricing based on demand, competition, and real-time
conditions is crucial.
This project simulates such a system: participants will create an intelligent, data-driven
pricing engine for 14 parking spaces using real-time data streams, basic economic theory,
and ML models built from scratch, using only numpy, pandas libraries.
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

## 📊 Dataset

The dataset contains 18,368 records from 14 urban parking spaces over 73 days with:
- **Location**: Latitude, Longitude
- **Capacity**: Maximum vehicles
- **Occupancy**: Current vehicles parked
- **Queue Length**: Vehicles waiting
- **Vehicle Type**: Car, bike, truck, cycle
- **Traffic Conditions**: Low, average, high
- **Special Days**: Holidays/events indicator
- **Timestamps**: Date and time information

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
