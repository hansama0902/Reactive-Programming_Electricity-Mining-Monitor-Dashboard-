# Electricity & Mining Monitor Dashboard Documentation

## Project Summary

Mining Monitor Dashboard is an interactive data visualization and analytics platform tailored for crypto mining farm operators and energy analysts. It provides real-time monitoring of mining machine statuses and electricity price dynamics, offering actionable insights for operational efficiency and energy cost management.

The dashboard integrates status filtering, device management, static IP-based regional performance analysis, and electricity price trend visualization using Plot. It also includes predictive analytics to assess potential future risks, such as emergency shutdowns triggered when electricity prices peak.

## Key Features

### Upload Your CSV Files

- **Mining Machine Table**: Upload machine status data including fields such as status, temperature, hash rate, etc.
- **Electricity Price Data**: Upload electricity price data in CSV format (Date, Time, Electricity Price ($/kWh)).

### Mining Monitor Widget

- Filter machines by status and location.
- Visualize status counts with a stacked bar chart.
- Interactive table displaying ID, temperature, hash rate, and uptime.
- Live statistics for average temperature, hash rate, and uptime.
- Expandable results with a "Show more" option.

### Electricity Price Analysis

- Interactive threshold slider to identify high-price periods.
- Summary panel showing average, minimum, and maximum electricity prices.
- Alerts for periods exceeding the defined threshold with color-coded risk levels.
- Interactive line chart visualizing price trends and threshold breaches.

### Future Price Forecast

- Predicts electricity prices for the next 5 days.
- Forecast includes two daily price points (00:00 and 12:00).
- Highlights whether predicted prices exceed the defined threshold.
- Functions abstracted into reusable utilities (`electricityPriceForecastTable` & `predictFuturePrices`).

## Component Structure

| Component Name | Description |
|----------------|-------------|
| `fileInput` | CSV upload for mining machine data |
| `uploadedMachines` | Processes CSV uploads into machine arrays |
| `MiningMonitorWidget(config)` | Reactive widget displaying machine summaries and filters |
| `filters` | Interactive status/location filter controls |
| `fileInputElectricity` | CSV upload for electricity price data |
| `parsedResult` | Asynchronous CSV parser |
| `priceThreshold` | Interactive slider to set alert thresholds |
| `dataOverview` | Card-based summary panel (average, minimum, maximum, breach rate) |
| `priceTrendChart` | Line chart visualizing price trends and threshold alerts |
| `priceAlertTable` | Table of price breaches |
| `createElectricityForecastTable()` | Generates forecast table for future prices |

## External Libraries Used

- **d3**: CSV parsing and data manipulation
- **@observablehq/plot**: Interactive trend visualizations
- **@observablehq/inputs**: Interactive sliders, selects, and checkboxes
- **@john-guerra/reactive-widgets**: Interactive reactive widget handling
- **electricityPriceForecastTable**: Styled forecast table with threshold-based alerts
- **predictFuturePrices**: Forecast generation based on historical averages and daily patterns

## Expected CSV Formats

### Electricity Price CSV

```
Date,Time,Electricity Price ($/kWh)
2025-03-01,00:00,0.20
2025-03-01,12:00,0.28
...
```
[Example Electricity Price.csv Link](https://github.com/hansama0902/Reactive-Programming_Electricity-Mining-Monitor-Dashboard-/blob/main/Example%20CSV/march_electricity_prices_sorted.csv)

### Mining Machines CSV

```
id,name,status,temperature,hashrate,uptime,location
miner-1,Mining Rig 1,Online,65,85,240,Room 1
miner-2,Mining Rig 2,Offline,52,0,0,Room 2
...
```
[Example Mining Machine.csv Link](https://github.com/hansama0902/Reactive-Programming_Electricity-Mining-Monitor-Dashboard-/blob/main/Example%20CSV/completed_mining_machine_table.csv)

## Observable Notebook

- **Electricity & Mining Monitor Dashboard**: [Observable Notebook Link](https://observablehq.com/d/17ad2f133c3f874a)
  
  This notebook provides an interactive interface for monitoring mining machine statuses and electricity-related alerts. It uses components like `MiningMonitorWidget` for real-time filtering and visualization, and `priceTrendChart` for visualizing electricity price fluctuations, allowing operators to rapidly identify abnormal behavior and respond to electricity price changes.

- **electricity-forecast-shuhan**: [Observable Notebook Link](https://observablehq.com/d/b8ad004b090ff363)

  This module abstracts forecasting logic into reusable components (`electricityPriceForecastTable` and `predictFuturePrices`), simplifying the integration of price forecasting into various Observable notebooks and dashboards.

## Project Usage

This Observable project offers an interactive dashboard for analyzing mining machine operations and electricity pricing data. Users upload relevant CSV files, apply interactive filters, and set price thresholds. The dashboard presents summary statistics, visual charts, and detailed alert tables. It incorporates predictive analytics for forecasting future electricity prices. All elements are reactive, providing real-time updates as users interact with the dashboard. The project is modular and leverages Observable’s Inputs, Plot, d3 libraries, and includes abstracted forecasting utilities reusable across various analytical tools.

## Usage of GenAI  

I utilized Claude and ChatGPT 4o throughout the development process to address various development and design challenges:  

**Electricity Price Prediction and Data Analysis**  
Use Case: Developing algorithms and visualization components for the electricity price prediction module  
Prompt: "How can I create an accurate short-term prediction model based on historical electricity price data?  

**CSV Data Processing and Formatting**  
Use Case: Implementing CSV upload and parsing functionality  
Prompt: "How to efficiently process large CSV files using d3, including data validation and transformation?"  

**Responsive Interface Development**  

Use Case: Creating responsive interfaces with @john-guerra/reactive-widgets  
Prompt: "How to design a reactive component where filter changes immediately reflect in data visualizations and statistics?"  

**Observable Platform Integration**  

Use Case: Resolving module import and publishing issues  
Prompt: "In Observable notebooks, how can I correctly export and import custom components to ensure functionality reuse between different notebooks?"  

**User Interface Optimization**  

Use Case: Enhancing interaction design and visual hierarchy  
Prompt: "How to apply design hierarchy principles to ensure the most critical monitoring information is always prominently displayed in the dashboard?"  


## License

MIT License — Free for personal and academic use.
